---
title: "Exec line in .desktop entry will not execute"
date: 2021-01-11
forum: Desktop Environments
---

### Post by mark bower on 2021-01-11
I have two PCs with Ubuntu MATE 20.4, different motherboards.  On the 1st PC, MATE was install by other than DVD(burned .iso image), on the 2nd PC MATE was installed via DVD.  On the 1st PC, the SHUTDOWN.desktop works as expected.  BUT on the 2nd PC, the SHUTDOWN.desktop displays the image, but the Exec line does not execute and displays the error message "There was an error launching the application".  On both PCs, the .desktop file is stored out of Geany.  

On the 2nd PC the shutdown.sh script, which is used in SHUTDOWN.desktop, works.  Note: Conky is not used, just in directory names.  Any ideas or what might need to be tweaked to get the .desktop file to work on the 2nd PC?

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false

Exec=/home/mark/ToTheDesktop/Shutdown_w_Icon/shutdown.sh
Name=SHUTDOWN
Comment=save as SHUTDOWN.desktop on the Desktop
Icon=/home/mark/ToTheDesktop/Images/Focus400.JPG

```

```
#!/bin/bash
#file:  shutdown.sh

shutdown -P now
```

---

### Post by sisco311 on 2021-01-11
You can validate/verify your .desktop file with the `desktop-file-validate' command:
```
desktop-file-validate <your desktop file>
```

---

### Post by mark bower on 2021-01-11
I ran the validate code runs and shows no errors.  If I place the shutdown.sh on the Desktop, and change the Exec path to point to that location, the .desktop performs as expected:

```
Exec=/home/mark/Desktop/shutdown.sh                      works
```          

However, if i substitute just one directory for Desktop, and place shutdown.sh in that directory, the code will not execute with the error msg presented:

```
Exec=/home/mark/a/shutdown.sh                            does not work
```

---

### Post by ActionParsnip on 2021-01-12
What is the output of:
```

ls -la /home/mark/zConky_plusDesktopScripts/Shutdown_w_Desktop_Icon/shutdown.sh

```
please?

---

### Post by mark bower on 2021-01-12
@ ActionParship - you made the good call - thanks

I abbreviated directories to make appearance simpler, so the .desktop code is now:

```

Exec=/home/mark/ToTheDesktop/Shutdown_w_Icon/shutdown.sh
Name=SHUTDOWN
Comment=save as SHUTDOWN.desktop on the Desktop
Icon=/home/mark/ToTheDesktop/Images/Focus400.JPG
```

I then ran the code line:  
```
mark@senior:~$ ls -la /home/mark/ToTheDesktop/Shutdown_w_Icon
total 36
drwxr-xr-x 3 mark mark  4096 Jan 12 11:38  .
drwxr-xr-x 4 mark mark  4096 Jan 12 11:38  ..
-rw-r--r-- 1 mark mark 12792 Jan 12 11:38  aReadme.odt
-rw-r--r-- 1 mark mark  1363 Jan 12 11:38  SHUTDOWN
-rw-r--r-- 1 mark mark   908 Jan 12 11:38  shutdown.sh
drwxr-xr-x 2 mark mark  4096 Jan 12 11:38 'Utility Scripts-not Desktop'
mark@senior:~$ 
```

I then ran the ls -la command on the PC where the .desktop works, and voila, shutdown.sh is marked as executable:

```
mark@mark:~$ ls -la /home/mark/ToTheDesktop/Shutdown_w_Icon
total 36
drwxrwxr-x 3 mark mark  4096 Jan 12 11:29  .
drwxr-xr-x 4 mark mark  4096 Jan 12 10:41  ..
-rw-rw-r-- 1 mark mark 12792 Jan 11 07:07  aReadme.odt
-rw-rw-r-- 1 mark mark  1363 Jan 12 11:29  SHUTDOWN
-rwxr-xr-x 1 mark mark   908 Jan 10 20:33  shutdown.sh
drwxr-xr-x 2 mark mark  4096 Jan  9 07:37 'Utility Scripts-not Desktop'
mark@mark:~$ 
```

So on the PC (senior) where the code was not working, I opened shutdown.sh in its directory "/home/mark/ToTheDesktop/Shutdown_w_Icon/shutdown.sh" and changed it to executable via rt-click-Properties, and **BINGO**, the .desktop works.  I guess what I learned from this is in copying the .desktop files from one computer to another, that shutdown.sh lost its execution authority.  And I was fooled whereby I dragged the non-executable shutdown.sh to the Desktop, made it executable, then changed the path in the .desktop to Exec=/home/mark/Desktop/shutdown.sh

I am going to mark this post as solved, because it is!

---

### Post by ActionParsnip on 2021-01-13
Glad you got the gold :)

---

