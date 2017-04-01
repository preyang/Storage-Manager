________________

Storage Manager
________________

Team Members
_____________

Preyang Shah (Leader) - A20385823 - pshah115@hawk.iit.edu
Riten Chhatrala - A20385102 - rchhatrala@hawk.iit.edu
Meet Patel - A20379333 - mpatel104@hawk.iit.edu
Niket Patel - A20384264 - npatel102@hawk.iit.edu
__________

File List
__________

README.txt
dberror.c
dberror.h
storage_mgr.c
storage_mgr.h
test_assign1_1.c
test_helper.h
Makefile

_________________________

Installation Instruction
_________________________

1) Go to the path where the extracted files are present. 2) Run the below command: make 3) Run the below command for testing test_assign1.c: make run 4) To remove object files, run following command: make clean 5) We have provided additional testcases in file "test_assign1_2.c To run those testcases use the below command: ./test_assign1_2
_______________________

Functions Descriptions
_______________________

initStorageManager()
This method initializes the storage manager
_______________________

File Related Functions
_______________________

createPageFile()
This method creates a new file and initializes with '\0' i.e 4096
 
openPageFile()
In this method, the file will open if it exists.Otherwise, will return an error.This function assigns all the file information to an existing file handle used to maintain the file information.

closePageFile()
This method closes a file if it is opened or else throws an error.

destroyPageFile()
This function destroy or removes the existing file if it exists or else throws an appropriate error.

_______________________

Read Related Functions
_______________________

readBlock()
This method reads a particular block in the file and stores its content into memory. If the given page number to be read is more than total pages then it throws an error. 

getBlockPos()
This method returns the current page position if the file exists or else returns error.

readFirstBlock()
This method gives the page number which is to be read as an input to readBlock() function and then reads that block.

readPreviousBlock()
This function gives the page number to be read by getting current block position using getBlockPos() function and decrementing it by 1 as an input to readBlock() function. It then reads that block.

readCurrentBlock()
This function gives the page number to be read by getting current block position using getBlockPos() function as an input to readBlock() function. It then reads that block.

readNextBlock()
This function gives the page number to be read by getting current block position using getBlockPos() function and incrementing it by 1 as an input to readBlock() function. It then reads that block.

readLastBlock()
This function gives the page number to be read by getting total number of  pages using the fileHandle structure and decrementing it by 1 as an input to readBlock() function. It then reads that block.
________________________

Write Related Functions
________________________

writeBlock()
This method is used to write a given block or page by providing its page number. It check whethers the file handle is initialized or not, then it checks if the given page number lies within the total number of pages, then it writes the content from the memory to the file and updates the file stats using the UpdateFileStats() function that we created additionally. In case of any errors, appropriate errors are returned.


writeCurrentBlock
This function is used to write the current block with the content stored in memory (memPage). It makes use of writeBlock() function to write the current block by passing the current position, the file handle structure and the content to be written. In case of any errors, appropriate errors are returned.

appendEmptyBlock()
In this method, it increases the number of pages in the file by one and the last new page gets filled with zero bytes.
 
ensureCapacity()
In this method if the file has less than numberOfPages pages then it increases the size to numberOfPages.

_____________

Extra Credit
_____________

We have implemented an extra test case that is available in the file named "test_assign1_2.c". The description of that test case can be found in the Test Cases section below.
_________________

Additional Files
_________________

test_assign1_2.c
This file contains additional test cases for testing.
___________

Test Cases
___________

testCreateOpenClose()
This test case is used to test the functions that creates a file, opens a file, destroys a file and close the file. It should return an error if a file that has already been destroyed is tried to be opened.

testSinglePageContent()
This test case is used to test the functions that are used to read first block and write a block. Firstly, a file is created and then opened. The first block is read and is expected to be empty since it is full of NULLs. Then a block is written in the file and it is read again. At last, the file is destroyed.

Additional Test Case Sequence:

readFirstBlock:Read first block run fine
writeBlock: 
writeCurrentBlock
writeBlock
writeCurrentBlock:
curPagePos = 1000;

After setting page to 1000 below will not run
readPreviousBlock
readCurrentBlock

But below function will run perfect 
readLastBlock
ensureCapacity
destroyPageFile

readFirstBlock
