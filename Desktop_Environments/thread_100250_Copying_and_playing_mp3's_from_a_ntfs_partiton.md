---
title: "Copying and playing mp3's from a ntfs partiton"
date: 2005-12-07
forum: Desktop Environments
---

### Post by tominator333 on 2005-12-07
Hi all
I have just installed ubuntu 5.10 on my pc, and i really like it (im a first time linux user).  The install has gone smoothly, but i seem to have a problem when trying to copy files from my ntfs partition to the ubunto partition. I copy and paste the files, and when i try to play the mp3's totem says that i need to install specific codecs. The other player that comes bundled with ubuntu (sorry, dont remeber the name) just starts up and doesnt play anything. Even when i try to play the files by browsing them with the system app 'disk drives', which i use to mount the ntfs partition, i am unable to play them. Also when i try to browse a directory that has been copied onto the linux partition, by going to places, files system, i get an error saying i dont have permissions to browse this directory. i am only using the account i set up when i first installed ubuntu.

What am i doing wrong???

---

### Post by phanboy_iv on 2005-12-07
You're not doing anything wrong, don't worry.

This is actually 2 problems.

First we'll deal with the mp3's:

Go to System->Administration->Synaptic Package Manager

Once you've opend synaptic, click the search button and search for a package called "gstreamer0.8-mad" and install it. This will install the codec's Ubuntu needs to play mp3's. It's not included by default because it's not open-source, but it's perfectly legal.

As to the write access errors, at this time linux doensn't have the ability to write to NTFS partitions safely without data corruption, so by default you don't have write access, just read access. If you need to edit a file on an NTFS disk, first copy it to a linux partition and change the permissions via the right-click Properties menu and give yourself the permissions.

Also, if you're getting "cannot open folder" messages, try mounting the NTFS partition in a folder you have write-access to, like one in your home folder.

---

### Post by Gray. on 2005-12-07
Use [EasyBreezy]("http://dev.realistanew.com/easybreezy/easybreezy0.33-alpha.tar.gz") to install Multimedia codecs along with other useful things.
In case you have no idea what to do with the file, I'll give you the steps.
Open the terminal:
Applications > Accessories > Terminal
Change to the directory where the file is:
```
cd /path/to/file
```
(If you downloaded this in Firefox, it defaults to saving them to the Desktop, in which case you'd type:
```
cd ~/Desktop
```
then do:
```
tar -xvzf easybreezy0.33-alpha.tar.gz && cd easybreezy-install
```
then:
```
./install
```
After that it should be installed and can be accessed by going to:
Applications > System Tools > Easy Breezy

---

### Post by Limulus on 2005-12-07
For legal reasons, Ubuntu doesn't ship with MP3 support.  But this is easy to fix.  You would probably do best to install the XMMS player; you can find it under "Add Applications" (Sound & Video -> More programs)

---

### Post by tominator333 on 2005-12-07
thanks alot for the quick replies guys!
ok, i have installed the gstreamer + breezy codecs, without a hitch.
but i still cant get them to play, either thru the browser system>admin>disk directly off the mounted hdd or by copying them to the linux partition. I have also changed the permissions on the folders. i keep getting told i dont have write permissions even tho i have changed them....

thanks again!!

---

### Post by Limulus on 2005-12-07
Did you change the permissions of the files in the directories too? (e.g. right-click one of them, select properties, click the Permissions tab)

Also, I'd still recommend XMMS; it does a good job of handling MP3s ;)

---

### Post by tominator333 on 2005-12-08
ok, ive worked out what was wrong, thanks for the help guys, xmms works flawlessly!

just one more question, when i change the permissions on a directory, the files within the directory permission remain unchanged, is there a way to change the permissions of a folder and change them on all the files and folders beneath it?

---

### Post by phanboy_iv on 2005-12-08
Yeah. Just run these commands in a terminal

>  sudo chown -R yourusername /path/to/the/folder/  
to make sure you're the owner of the files (substitiuting your actual username, of course) and then run:

>  chmod -R 755 /path/to/the/folder  

to give yourself read/write/execute permissions to all the files in that folder.

Happy Ubuntu-ing

---

