---
title: "notepad permissions correction"
date: 2008-12-07
forum: General Help
---

### Post by sandman3838 on 2008-12-07
HELLO ):P

I HAVE AN ISSUE WITH NOTEPAD OR GEDIT IN UBUNTU 810 IN MY HOME FOLDER! 

ALL THE NOTEPAD OR WHAT I USE TO CALL TXT FILES ARE SET TO OPEN TO "PLAIN TEST DOCUMENT" USING "TEXT EDITOR".  THE ONES THE WORK HAVE "ALLOW EXECUTING FILE AS PROGRAM" UNCHECKED UNDER PERMISSIONS WHEN YOU DO "PROPERTIES" ON THE FILE.  THE RESULT IS MOSTLY FILS WITH PERMISSIONS -R W - R W - R W.

HOWEVER SOME FILES FAIL!

WHEN YOU CLICK ON THE FILE YOU ARE ASKED IF YOU WISH TO "RUN TERMINAL" "DISPLAY" "CANCEL" "RAN".  WITH THESE "ALLOW FILE AS PROGRAM" IS CHECKED UNDER PERMISSIONS WHEN YOU DO "PROPERTIES" ON THE FILE.  THE RESULT IS MOSTLY FILS WITH PERMISSIONS -R W X - R W X - R W X.

ONCE I UNCHECK "ALLOW FILE AS PROGRAM" THE  FILES RESPOND AS EXPECTED AND THE PERMISSIONS CHANGED TO -R W - R W - R W.  FROM THERE NOTEPAD/GEDIT OPENS THE FILE RIGHT UP WITH NO MESSAGE.

I WOULD HATE TO SIT HERE AND MANUALY EDIT EACH OF THESE "PLAIN TEXT DOCUMENTS" HERE IN MY HOME FOLDER.  IS THERE A SAFE COMMAND THAT I CAN EXECUTE IN TERMANNIAL TO CORRECT THIS?


THANK YOU ALL! :p

---

### Post by taurus on 2008-12-07
Assuming you want to change all the files in the same directory to read/write only, you can do something like

```
chmod 644 *
ls -la
```

p.s.  And turn off your cap.

---

### Post by sandman3838 on 2008-12-07
Great!
That wasn't is.
I think that command changed more than just my notepad permissions!

My wallpaper folder is empty now.
Awn is no longer at the bottom of the screen.

Quit a few of the folders are now empty?

If there is not a way to get the permissions all back to their default i think i'm headed for another reinstal?  Nuts.

](*,)](*,)

---

### Post by taurus on 2008-12-07
Did you run that command from your $HOME?

---

### Post by sandman3838 on 2008-12-07
IN MY HOME FOLDER I OPENED THESE VISIBLE FOLDERS, EACH HAD NOTEPAD FILES.
I NEVER DID CTRL+H
I JUST OPENED EACH FOLDER AND RAN

chmod 644 *
ls -la

FOLDERS:
1A_UBUNTU
DOCUMENTS
EMERALD THEMES
PICTURES
POWERCERT
THEME PACKAGES
VIDEOS
WEB LINKS

ALL HAVE PERMISSIONS OF
DR WR RW XR WR
DR WX R- XR -X

NOTE I DO HAVE A BACKUP OF ALL THESE FOLDERS ON ANOTHER DRIVE BUT IT WON'T LET ME COPY THEM IN.

---

### Post by taurus on 2008-12-07
Just do

```
chmod 755 *
```
this time and for the love of humanity, turn off the **cap**!

---

### Post by sandman3838 on 2008-12-07
I RAN THAT LAST SUGGESTION ONCE DIRECTLY FROM THE HOME DIRECTORY.

chmod 755 *

FOR A QUICK TEST I TRIED TO COPY ONE PICTURE FILE ON ANOTHER HD TO THE PICTURE FOLDER IN THE HOME DIRECTORY WHAT I GOT WAS:

Error opening file '/home/kevin/Pictures/X_PLANETS/1198163283.jpg': Permission denied

---

### Post by vanadium on 2008-12-07
Don't SHOUT or people might not be willing to help anymore.

Do not wildly change permissions: it will break your system.

You can selectively remove the execute bit from text files only using the following terminal command:

chmod -x *.txt

This is much safer than globally changing all permissions of files.

It is strange, though, that your files automatically have an execute bit. Perhaps this is because they are being copied from an ntfs disk. What does the command "umask" tell you (will probably be OK, "0022".

---

### Post by sandman3838 on 2008-12-07
Thanks
For the reply.
Sorry, I didn't mean to shout.
I just like to type with the CAPS on?  :)

I'll try as you suggested.

---

### Post by sandman3838 on 2008-12-07
Here is the information:

username@Larry-Ubuntu:~$ chmod -x *.txt
chmod: cannot access `*.txt': No such file or directory

username@Larry-Ubuntu:~$ umask
0022

---

### Post by vanadium on 2008-12-07
This means there are no files with extention .txt in your current directory. Replace *.txt by the names of the files you need to change. It is simply unsafe to globally change permissions.

Your umask is obviuosly normal and what I expected. New files have as default permissions 644 (rw-r--r--) and directories 755 (rwxr-xr-x).

Try to describe or to find out exactly which files after what action have the weird behaviour. Then we might find out what the reason is.

---

### Post by sandman3838 on 2008-12-07
Thanks for your help!
But I have had some other issues as well.

I just posted this in the Forum but at another location.
I'm just going to do a reinstall! 

******* OTHER POSTING  ******** 

Hello

About a week ago I wiped out my UBUNTU 804 HD and re-installed UBUNTU 810 but, not before I saved my entire HOME folder (including the hidden material) to a folder on my WINXP HD.

C:\SAVED UBUNTU HOME FOLDER\

I'm getting ready to Re-install UBUNTU-810 again. I have done some things unintentionally and it's not worth playing around with so soon after a new install. I might as well re-install again and do it right.

I suspect that some of the issues that I have experienced may have been from user rights with the original Ubuntu 804 home folder.

About the only thing hidden that needs restoring from UBUNTU 804, that I can think of at the moment, is my .Evolution Email material?

All the rest of the UBUNTU 804 HOME folder material are just the default standard folders and some additional files and folders that I added!

Could this (user rights) have been an issue?

Any suggestions on how to safely and easily recover that material (FOLDERS, FILES, EVOLUTION) back over?

Thanks for all your help.

**************************  
I'll let you know how it turns out.

---

### Post by sandman3838 on 2008-12-07
I'm back with some update info!  ):P

REMEMBER!  I have my original Ubuntu HOME folder (including it's hidden folders) saved over on my WINXP HD!

1.  I just did a re-install of Ubuntu.
2.  I configured/installed drivers for sound, video, and network.
3.  I let the system do an upgrade.
4.  I made two text files using TEXT EDITOR and saved them in my new HOME folder.

	File name=notepad test   	Group=john  Owner=john - John Smith  Permissions= -rw-r--r--
	File name=notepad test2.txt   	Group=john  Owner=john - John Smith  Permissions= -rw-r--r--

These open with no issue.

5.  Next, I went over to C:\SAVED UBUNTU HOME FOLDER  or  (/media/WIN_XP/SAVED UBUNTU HOME FOLDER)
The TXT files here are as follows:

	File name=code notes.txt	Group=root  Owner=root   Permissions= -rwxrwxrwx

These files open up asking for:
	Do you want to run "code notes.txt" or display its content?
	<Run Terminal>  <Display>  <Cancel>  <Run>

Also, I just did some more looking around in my HOME backup folder (/media/WIN_XP/SAVED UBUNTU HOME FOLDER)
even my wallpaper is messed up.  It probably all is?

	File name=Lights.jpg	Group=root  Owner=root   Permissions= -rwxrwxrwx

Is it possible to change or correct everything in my HOME backup folder (/media/WIN_XP/SAVED UBUNTU HOME FOLDER)
ONLY!  Just targetting my Backup Home Folder on the XP HD and still leave my new current HOME folder or everything on my UBUNTU HD alone.

As for anything hidden that's over in that backup folder?  All I can think of getting is .ICONS, .THEMES, and my EVOLUTION EMail folders?  

As usual I can just bet that the real headache here is going to get that Email folders back over?

Anyway, .......  Any suggestions!  :)

---

### Post by vanadium on 2008-12-08
Your "/media/WIN_XP/SAVED UBUNTU HOME FOLDER" resides on an ntfs partition. The ntfs file system does not support permissions. In order to allow anyone to read/write/navigate the partition, permissions are set to 777. Files copied from that ntfs volume to an ext3 partition therefore keep the 777 permissions they had on the ntfs volume.

I do not have an ntfs volume to test, but my fat32 USB has permissions rxw------ When I copy a text file from the USB to the hard drive, it inherits these permissions also in the destination directory, and I eventually have to change them.

It is how it works.

---

### Post by sandman3838 on 2008-12-10
Sorry for not replying sooner.  I have been busy.
I went through and found about 20 files I really really needed to keep.  I,m just going to open them up and save them to my homes folder changing the name slightly.

As for the mail folders......
Nuts to them!  It just means my Email will be running faster than usual.

Thanks for your help.

---

