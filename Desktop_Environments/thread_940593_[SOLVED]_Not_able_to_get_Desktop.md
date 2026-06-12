---
title: "[SOLVED] Not able to get Desktop"
date: 2008-10-07
forum: Desktop Environments
---

### Post by techie_india on 2008-10-07
Hi all,

I have got very wierd problem not able to solve it.

it is like this :
I have make a folder in the user dir as data. 
By mistake I put all the file and folders ( including Desktop and Document Folder)
When I restarted the system , the Desktop link it takes as ~/data/Desktop.
When I moved all the Desktop again to the ~/Desktop , 
It is taking the user directory as Desktop.
So all the Folders in the User directory is shown as Desktop icon
I m not able to restore the default value.

Please anybody can help me to restore the Default

Thanks and Regards
Anshuman Srivastava

---

### Post by phidia on 2008-10-07
Create a test user > sudo adduser test login to test and copy the files from the test Desktop to your regular user. 
You may need to do more editing and sorting but the method of having a good test user system to compare to should make things right again.

---

### Post by techie_india on 2008-10-08
Thanks for help.

There is a file ---- > ~/.config/user-dirs.dir 
in this file  there is a parameter as
XDG_DESKTOP_DIR
XDG_DOWNLOAD_DIR

it has to be provided with right path . 
Then the Destop path will be restored.

Thanks and Regards

---

