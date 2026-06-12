---
title: "automating a mount"
date: 2005-12-31
forum: Desktop Environments
---

### Post by welshgasman on 2005-12-31
Hi,
I am trying to use the live CD of Ubuntu as an intro to Linux, being a windows user.

From a thread in these forums [http://ubuntuforums.org/archive/index.php/t-75539.html](http://ubuntuforums.org/archive/index.php/t-75539.html)

I found out why I could not see my hard disk on my XP laptop.

Entering the commands recommended sort that out.

Having written plenty of batch programs over the years I tried to write a simple file to automate the process as I will be bound to forget the syntax next time.

The file contains
 
#!/bin/sh
if [! -d "/media/windows]";then
    sudo mkdir "/media/windows"
fi
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

Cutting and pasting the commands individually works fine.
When I try and run the file I get 
'mount: mount point /media/windows/ does not exist'

yet it creates a 'windows?' directory in /media

What am I doing wrong??

TIA

---

### Post by zoiks on 2005-12-31
2 things.

The ending quote is on the wrong side of the closing bracket in your if... command.

Maybe something about sudo and stdin/stdout.  Try making the script only executable by root (chown root.root myscript; chmod u+x myscript; chmod go-x myscript) and kill off the sudo's.  Then just use sudo to run the command.

---

### Post by welshgasman on 2005-12-31
Cheers Zoiks.

I originally started without quotes, but was prepared to try anything.

File is now
#!/bin/sh
if [! -d "/media/windows"];then
    mkdir "/media/windows"
fi
mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

I entered
ubuntu@ubuntu:/media$ chown root.root UDISK25X/unixmount
ubuntu@ubuntu:/media$ chmod u+x UDISK25X/unixmount
ubuntu@ubuntu:/media$ chmod go-x UDISK25X/unixmount

UDISK25X is a USB pendrive where I wish the command to be kept and run if possible.

I then got
ubuntu@ubuntu:/media$ ls -l UDISK25X
total 12226
-rwx------  1 ubuntu ubuntu 12425080 2005-08-20 14:26 dklite.exe
drwx------  3 ubuntu ubuntu     2048 2005-11-18 19:35 Joss Stone
drwx------  2 ubuntu ubuntu     2048 2005-11-12 14:48 OBO
-rwx------  1 ubuntu ubuntu    81408 2004-03-05 12:27 OPENDVD.EXE
-rwx------  1 ubuntu ubuntu      135 2005-12-31 23:51 unixmount
-rwx------  1 ubuntu ubuntu      145 2005-12-31 22:55 unixmount~
-rwx------  1 ubuntu ubuntu      106 2005-12-31 21:55 unixmount.txt~
-rwx------  1 ubuntu ubuntu     1158 2005-06-11 07:19 wpa.dbl
ubuntu@ubuntu:/media$ sudo UDISK25X/unixmount
sudo: unable to execute UDISK25X/unixmount: Permission denied
ubuntu@ubuntu:/media$ UDISK25X/unixmount
bash: UDISK25X/unixmount: /bin/sh: bad interpreter: Permission denied
ubuntu@ubuntu:/media$

when trying to run the command both with and without sudo.

Thanks for your help.

---

### Post by zoiks on 2005-12-31
OK I suggest:

1) put a space after the open bracket ([) before the "!".  (as well, put a space after the directory name.  bash needs these, and this is a bash script)
2) this shouldn't make a difference, but since this is definitely a bash script, but /bin/bash on the shebang line.  Likely /bin/sh points to bash anyway.
3) Just create the directory in /media and forget about the mkdir part.

Oh, also be careful if you are editing the file in windows.  MS does carriage returns differently than everyone else on the planet, so if you save it from windows unix may complain about the extra line feed characters.  Try editing it in linux using sudo gedit or some other editor.  (I noticed because of your unixmount.txt file.)

(Another thing to try is just put an entry in fstab that way it mounts every time the system starts.)

---

### Post by welshgasman on 2005-12-31
1) I did have spaces, but took those out. I got that phrase from a RH8 book.
2) Will do.
3) Will do also. I know I will remember that much from dos commands :-)

I did initially create the file in windows on my desktop and put it onto the pen drive to port to the laptop, but since then I have edited all he time in Ubuntu with gpedit you mentioned.

As I *thought* I understood it fstab would be on the CD and non editable. Could I edit the iso somehow and recreate the CD?.

Have a good New Year and thanks again for your help.

I'll let you know my progress.

---

### Post by zoiks on 2005-12-31
Oh, I forgot you are working from a live CD.  Yeah, in general you can remaster the CDs, if you find the right instructions.  If you are making this for general use, be aware some people's windows file systems might not be hda1 (e.g. lots of systems have "hidden" hda1 for diagnostics and such), and they might be vfat instead of ntfs.

You are on the right track.  What you have should work.  Just something's wrong with the syntax or something.

---

### Post by zoiks on 2005-12-31
I should have thought of this earlier.  Another solutions is to just run "mkdir" without the if statement.  If the directory already exists it will simply fail to make it, no sweat.

---

### Post by welshgasman on 2006-01-01
Thanks,

I originally had that but it came back with 'Directory exists' and I thought it was aborting at that point.

I'm going back to basics now. I'm going to put the commands in my Psion 3a and I will always have them when I need them.

I will also cut and paste from the file to execute the commands.

5 minutes later........

Went back to basics and created the mkdir and mount with sudo accessin a new file.
Copied that to /usr/bin and sudo'd that and it works...??

Thanks again.

---

