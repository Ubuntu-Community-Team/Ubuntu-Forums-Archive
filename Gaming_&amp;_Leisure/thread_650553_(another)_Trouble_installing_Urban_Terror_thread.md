---
title: "(another) Trouble installing Urban Terror thread"
date: 2007-12-26
forum: Gaming &amp; Leisure
---

### Post by Sweet Spot on 2007-12-26
I tried using the installer via both methods mentioned on the forum installer page (not this forum, the one from where the installer is from). 

The first method promises to get and install both packages if followed correctly, which I did, but the final message was "WGET failed downloading"

I also have both packages (zipped) and put them in a folder named urbanterror on my desktop, and then cd'd to that location, and tried again. Also, got the same message about not being able to download:

```
cd /home/********/Desktop/urbanterror
********@********-desktop:~/Desktop/urbanterror$ chmod +x urt40-linux-installer.sh
********@********-desktop:~/Desktop/urbanterror$ ./urt40-linux-installer.sh _   _     _             _____                      _ _   __  
| | | |_ _| |__  __ _ _ |_   _|__ _ _ _ _ ___ _ _  | | | /  \ 
| |_| | '_| '_ \/ _` | ' \| |/ -_) '_| '_/ _ \ '_| |_  _| () |
 \___/|_| |_.__/\__,_|_||_|_|\___|_| |_| \___/_|     |_(_)__/ 
                                                    installer

 This program will help install UrbanTerror 4 on your system.

 Press enter key to continue or control-c now to abort

Downloading ioUrbanterror binaries ...
--14:10:55--  ftp://ftp.snt.utwente.nl/pub/games/urbanterror/iourbanterror/ioUrbanTerror_Installer_1.0.zip
           => `ioUrbanTerror_Installer_1.0.zip'
Resolving ftp.snt.utwente.nl... 130.89.175.1
Connecting to ftp.snt.utwente.nl|130.89.175.1|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/games/urbanterror/iourbanterror ... done.
==> SIZE ioUrbanTerror_Installer_1.0.zip ... done.
==> PASV ... done.    ==> REST 6624298 ... done.    
==> RETR ioUrbanTerror_Installer_1.0.zip ... 
No such file `ioUrbanTerror_Installer_1.0.zip'.

ERROR: WGET failed downloading.
********@********-desktop:~/Desktop/urbanterror$ 

```it says there's no such file, but of course there is. Do I have to unpack it perhaps ?

I'd really love to play this again, so any help would be appreciated. Thanks a bunch.

doug

---

### Post by TidusBlade on 2007-12-26
Seems like it needs to download something? I didnt need to download anything, but maybe cause Im using the ioUrbanTerror? Anyways, maybe try running the .sh file with "bash urt40-linux-installer.sh" ?

---

### Post by Sweet Spot on 2007-12-27
Perhaps you can tell me what you did from step one ? I do have the iourbanterror file along with the full installer as well as the script in a folder on my desktop.

---

