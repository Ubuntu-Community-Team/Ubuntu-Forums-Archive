---
title: "Problem with Eclipse 3.1"
date: 2005-12-13
forum: Desktop Environments
---

### Post by fabriciobraga on 2005-12-13
Hi all,

I have a big trouble while trying to use Ubuntu + Eclipse 3.1.  Let me show you what I did:

1 - Donwload Eclipse 3.1 from [www.eclipse.org](www.eclipse.org) ...
2 - extract Eclipse files from the gz file...
3 - start Eclipse IDE running "eclipse" file.

After this, I got the Eclipse starting, but then it was empty!

Yes, when Eclipse finished the load, it was empty, with most of menus disabled, and no perspective to choose.  While loading, Eclipse gaves me some error messages, somethig about permissions.

So I thought the permitions was the problem, right?  Then I changed the owner and the group of entire Eclipse's folder, sub-folders and files.  But it just didn't work!

After this, I thought the problem could be jdk or jre version.  then I got the jdk 1.5 at [www.java.sun.com](www.java.sun.com), run the installation, and tried to start using this:
$ eclipse <jdk1.5_installation_dir_here>

But still got the same error.   :o(

Anyone can help me?

Regards,
Fabricio Braga

---

### Post by gborbolla on 2005-12-13
Could you post eclipse's log files?

---

### Post by usprinter on 2005-12-13
I had the same problem and solved by doing:

--> install and run galternatives to set the default jvm to J2SDK :)

Good luck

---

### Post by fabriciobraga on 2005-12-13
Ok,  here goes the error messages, appended to a file under the eclipse/configuration directory:

!MESSAGE Error reading configuration: /home/fabricio/install/eclipse/eclipse/./configuration/org.eclipse.osgi/.manager/.fileTableLock (Permission denied)
!STACK 0
java.io.FileNotFoundException: /home/fabricio/install/eclipse/eclipse/./configuration/org.eclipse.osgi/.manager/.fileTableLock (Permission denied)
   at ._ZN4java4lang11VMThrowable16fillInStackTraceEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9Throwable16fillInStackTraceEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ExceptionC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java2io11IOExceptionC1EPNS_4lang6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java2io21FileNotFoundExceptionC1EPNS_4lang6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN3gnu4java3nio8channels15FileChannelImpl4openEPN4java4lang6StringEi (/usr/lib/libgcj.so.6.0.0)

As I told before, seems to be something about permissions...

Regards,
Fabricio Braga

---

### Post by gborbolla on 2005-12-13
Have you run eclipse with a user diferent than yours, for example run eclipse using sudo?

Try running eclipse directly from your home directory (type the complete path to the eclipse command) this will create a new workspace for you.

---

### Post by fabriciobraga on 2005-12-13
Ok, I did it, but nothing has change...    

1 - I tried to unpack eclipse.tar and run "./eclipse" using my user ("fabricio") but got the same error.

2 - Then, I tried to unpack eclipse.tar and run "./eclipse" using "root" user but still got  the same error!

I just can't believe that simply unpack and run an  application could be so hard.  Even considering that I'm using Linux (where thing can be a little bit harder), but I don't know if my enforce will gave some advantage.  

I don't know what to do.  I really want, I swear, I really want to use Linux+Eclipse to develop my Java applications, but I just don't know what to do anymore.

I will change back to my Win XP, where I can run Eclipse without problems...

Regards,
Fabricio Braga

---

### Post by gborbolla on 2005-12-13
Try running the following commands and let me know if anything changes:

```
cd
```

```
/home/fabricio/install/eclipse/eclipse/eclipse
```

Supposing that you uncompressed eclipse in /home/fabricio/install/eclipse, if not simply change it to the path where you uncompressed eclipse.

If this doesn't works, please change to the directory where eclipse was uncompressed and post the exit of the following command

```
ls -la
```

Greeting

---

### Post by fabriciobraga on 2005-12-13
Ok, to make things a little bit easy, I did remove the previous "eclipse" directory created.

Let's start from beginning...

First step I have oppened a terminal window.

Now I did (as user "fabricio"):
1 - Unpack eclipse-SDK-3.1.1-linux-gtk.tar into /home/fabricio directory

2 - tar -xvf eclipse-SDK-3.1.1-linux-gtk.tar

3 - ok, now I have a new directory: /home/fabricio/eclipse

4 - now I changed to directory /home/fabricio/eclipse

5 - start eclipse using "./eclipse" command

6 - At first time, eclipse ask me about location of my workspace, and suggests "/home/fabricio/workspace",  that I've accepted

7 - Now the Eclipse starts, without error messages, but.... all is empty!  as I told before, it haves the most of menus disabled, and I can't do anything.  

Here goes the output of "ls -la" from /home/fabricio directory:

total 114996
drwxr-xr-x  24 fabricio fabricio      4096 2005-12-13 21:19 .
drwxr-xr-x   5 root     root          4096 2005-12-09 19:38 ..
-rw-------   1 fabricio fabricio      7794 2005-12-13 21:32 .bash_history
-rw-r--r--   1 fabricio fabricio       414 2005-12-08 16:58 .bash_profile
-rw-r--r--   1 fabricio fabricio      2227 2005-12-08 16:58 .bashrc
-rw-r--r--   1 fabricio fabricio       718 2005-12-12 21:43 comandos
-rw-r--r--   1 fabricio fabricio       450 2005-12-08 20:29 comandos~
drwxr-xr-x   2 fabricio fabricio      4096 2005-12-12 22:04 Desktop
-rw-------   1 fabricio fabricio        47 2005-12-08 19:10 .dmrc
drwxr-xr-x   7 fabricio fabricio      4096 2005-12-13 21:48 eclipse
-rw-r--r--   1 fabricio fabricio 117288960 2005-12-13 20:58 eclipse-SDK-3.1.1-linux-gtk.tar
-rw-------   1 fabricio fabricio        16 2005-12-08 19:10 .esd_auth
drwxr-xr-x   6 fabricio fabricio      4096 2005-12-08 22:26 .evolution
drwx------   4 fabricio fabricio      4096 2005-12-13 19:51 .gconf
drwx------   2 fabricio fabricio      4096 2005-12-13 21:39 .gconfd
-rw-r-----   1 fabricio fabricio         0 2005-12-13 20:11 .gksu.lock
drwx------   9 fabricio fabricio      4096 2005-12-12 22:26 .gnome2
drwx------   2 fabricio fabricio      4096 2005-12-08 19:10 .gnome2_private
srwxr-xr-x   1 fabricio fabricio         0 2005-12-12 20:41 .gnome-system-monitor.fabricio
drwxr-xr-x   2 fabricio fabricio      4096 2005-12-08 19:10 .gstreamer-0.8
-rw-r--r--   1 fabricio fabricio        32 2005-12-08 21:54 .gtk-bookmarks
-rw-r--r--   1 fabricio fabricio        90 2005-12-08 19:10 .gtkrc-1.2-gnome2
-rw-------   1 fabricio fabricio       161 2005-12-13 19:51 .ICEauthority
drwxr-xr-x   2 fabricio fabricio      4096 2005-12-09 20:22 .icons
drwxr-xr-x   4 root     root          4096 2005-12-13 21:17 install
-rw-r--r--   1 root     root           115 2005-12-09 20:05 .mailcap
drwx------   3 fabricio fabricio      4096 2005-12-08 19:10 .metacity
-rw-r--r--   1 root     root           230 2005-12-09 20:05 .mime.types
drwx------   4 fabricio fabricio      4096 2005-12-08 22:21 .mozilla
drwxr-xr-x   3 fabricio fabricio      4096 2005-12-08 19:10 .nautilus
drwx------   3 fabricio fabricio      4096 2005-12-08 19:16 .openoffice.org2
drwxr-xr-x   4 fabricio fabricio      4096 2005-12-12 22:10 projects
-rw-------   1 fabricio fabricio      1785 2005-12-13 21:35 .recently-used
drwxr-xr-x   2 fabricio fabricio      4096 2005-12-08 22:19 .themes
drwx------   4 fabricio fabricio      4096 2005-12-08 20:47 .thumbnails
drwx------   4 fabricio fabricio      4096 2005-12-13 21:02 .Trash
drwx------   2 fabricio fabricio      4096 2005-12-08 19:10 .update-notifier
drwxr-xr-x   2 fabricio fabricio      4096 2005-12-08 22:09 wallpaper
drwxr-xr-x   3 fabricio fabricio      4096 2005-12-13 21:19 workspace
-rw-------   1 fabricio fabricio       119 2005-12-13 19:51 .Xauthority
drwxr-xr-x   4 fabricio fabricio      4096 2005-12-08 21:06 .xmms
-rw-r--r--   1 fabricio fabricio     11162 2005-12-08 22:18 .xscreensaver
-rw-r--r--   1 fabricio fabricio    169114 2005-12-13 21:50 .xsession-errors

And here goes the output of "ls -la" at /home/fabricio/eclipse directory:

total 332
drwxr-xr-x   7 fabricio fabricio   4096 2005-12-13 21:48 .
drwxr-xr-x  24 fabricio fabricio   4096 2005-12-13 21:19 ..
drwxr-xr-x   2 fabricio fabricio   4096 2005-09-29 10:06 about_files
-rw-r--r--   1 fabricio fabricio    585 2005-09-29 10:06 about.html
drwxr-xr-x   6 fabricio fabricio   4096 2005-12-13 21:19 configuration
-rwxr-xr-x   1 fabricio fabricio  22161 2005-09-29 10:06 eclipse
-rw-r--r--   1 fabricio fabricio     25 2005-09-29 10:06 eclipse.ini
-rw-r--r--   1 fabricio fabricio     59 2005-09-29 10:06 .eclipseproduct
-rw-r--r--   1 fabricio fabricio  16536 2005-09-29 10:06 epl-v10.html
drwxr-xr-x  11 fabricio fabricio   4096 2005-09-29 10:05 features
-rw-r--r--   1 fabricio fabricio   9022 2005-09-29 10:06 icon.xpm
-rwxr-xr-x   1 fabricio fabricio 194964 2005-09-29 10:06 libcairo.so.1
-rw-r--r--   1 fabricio fabricio   6506 2005-09-29 10:06 notice.html
drwxr-xr-x  27 fabricio fabricio   4096 2005-09-29 10:06 plugins
drwxr-xr-x   2 fabricio fabricio   4096 2005-09-29 10:06 readme
-rw-r--r--   1 fabricio fabricio  32567 2005-09-29 10:06 startup.jar

I wolud like to thank you very much for your atemption dear friend.  Thanks a lot!

Regards,
Fabricio Braga

---

### Post by Knitter on 2005-12-13
Hello!
I and most, if not all, of my friends that use ubuntu and eclipse have had similar problems with breezy. All was solved installing the sun's java virtual machine and puting the system to run on it.
Is the java virtual machine you have the default one? If so try to install the one from sun.
After I installed jdk1.5 update 04 all worked well.
I followed this thread: [http://ubuntuforums.org/showthread.php?t=76754&highlight=install+jdk](http://ubuntuforums.org/showthread.php?t=76754&highlight=install+jdk)

Hope it helps

---

### Post by Knitter on 2005-12-13
forget what i just wrote! I wasn't paying attention to the question :rolleyes: 

See ya.

---

### Post by fabriciobraga on 2005-12-18
Before few days without think about this problem, I came back to face it...

The solution was not so hard, at last.  I just need to start Eclipse using argument option about where java vm is.  Something like this:

./eclipse -vm <the-path-of-my-jdk>

And that bastard starts, correctly!  I don't know why, but seems that gij (GNU libgcj) is not compatible with Eclipse 3.1.

I still don't know how to make my downloaded JDK as default VM of Ubuntu Linux (don't forget, I'm still a newbie).  But I don't think to that type the vm parameter on every Eclipse initialization is the end of the world, isn't it?

I would like to thank the guys that have spent their time trying to help me, specially "gborbolla".  

Regards,
Fabricio Braga

---

