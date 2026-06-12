---
title: "Frostwire again"
date: 2006-09-19
forum: Desktop Environments
---

### Post by DougieFresh4U on 2006-09-19
Can some one help me to get frostwire  w/Edgy? I download but when I go to open it nothing happens and I have all the java as frostwire worked w/dapper. Also the same w/gaim. I enabled it but when I go to open , nothing happens.

---

### Post by croak77 on 2006-09-20
What message do get when you run frostwire from a terminal?

---

### Post by DougieFresh4U on 2006-09-20
Silly me, but how to do that please?

---

### Post by odinfromvalhalla on 2006-09-20
to open a terminal use Alt+F2 to open the run window and type xterm (for ubuntu) or konsole (kubuntu).

this will open a console where you can type frostwire to start the app and it will also provide some output.

hope this helps

---

### Post by DougieFresh4U on 2006-09-20
what I got was                             syntac error unexpected (expected)              I did notice a little some thing odd                        during download. The little download window that shows progress of download from internet, the little % bar was not sliding across as the download was comming in, if this helps any.

---

### Post by DougieFresh4U on 2006-09-20
dougie@DougiesToyBox:~$ sudo apt-get frostwire
Password:
E: Invalid operation frostwire
dougie@DougiesToyBox:~$ sudo apt-get install frostwire
Reading package lists... Done
Building dependency tree       
Reading state information... Done
frostwire is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.17-7 linux-headers-2.6.17-7-386 fastjar
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dougie@DougiesToyBox:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.17-7 linux-headers-2.6.17-7-386 fastjar
The following packages will be REMOVED:
  fastjar linux-headers-2.6.17-7 linux-headers-2.6.17-7-386
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 84.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 117997 files and directories currently installed.)
Removing fastjar ...
Removing linux-headers-2.6.17-7-386 ...
Removing linux-headers-2.6.17-7 ...
dougie@DougiesToyBox:~$ 
trying to get frostwire in Edgy. java's are all installed. Just will not open

---

### Post by sharperguy on 2006-10-19
I have been told in the #ubuntu+1 irc channel that there is a scripting bug meaning Frostwire's file must be run in bash, but sh defaults to dash as of edgy.

To fix you have to edit /usr/bin/frostwire to run it in bash

ie:
```
sudo nano /etc/bin/frostwire
```

Edit the line that says:
```
sh runFrost.sh
```

And change it to:
```
bash runFrost.sh
```

Then ctrl+o to save and ctrl+x to exit nano.

Obviously you dont have to use nano.

Now frostwire should work

---

