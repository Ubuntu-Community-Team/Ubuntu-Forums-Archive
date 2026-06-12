---
title: "i have no idea what happened"
date: 2009-04-08
forum: General Help
---

### Post by dec7m2 on 2009-04-08
how do i fix this "Could not open location 'file:///home/chris/Documents'"

---

### Post by WRDN on 2009-04-08
Providing the location exists, this sounds like a folder permissions issue. Press Alt + F2, then enter:

```
gksudo nautilus
```

Now, navigate to the folder. If you wish, you can change the permissions by right clicking on the folder, select Properties, then the Permissions tab.

---

### Post by Lunx on 2009-04-08
> **dec7m2 said:**
> how do i fix this "Could not open location 'file:///home/chris/Documents'"

All those forward slashes look a little odd. 

In the terminal you can type ```
home/chris/Documents
``` 

As you can see this tells you it's a directory (so you now know it does exist :) )

To move to the Documents directory you use the change directory command *cd*

```
cd Documents
```

once in the directory you can use the list command *ls* to show you what's in that directory

```
ls
```

Any time you are moving around the file system and get a bit lost, the print working directory command will show you where you are

```
pwd
```

And when you really get lost, the cd command used on its own will return you to the desktop so you can start again.

I see from you post count you are new to the forums (welcome BTW) and so I'm guessing you are probably new to Ubuntu. If you want some really good info on Ubuntu, I suggest reading the [COLOR="Blue"]_[pocket guide]("http://www.ubuntupocketguide.com/")_[/COLOR] as this is brilliant for new users (I was pretty lost myself only a few months back when I was completely new to Linux and Ubuntu until I read this). There's some very easy to understand info on the file system and command line basics in there.

Also plenty of really good stuff for beginners to advanced users available for free 

[http://www.linuxlinks.com/article/20...oks-Part1.html](http://www.linuxlinks.com/article/20...oks-Part1.html)

Enjoy the journey ;)

---

### Post by kryptikos on 2009-04-08
> All those forward slashes look a little odd. 

The three / are fine. The first two are the protocol separators just like you would see in http:// or [ftp://.](ftp://.) The file tells the browser to look locally on the box and the third '/' is indicating directory. If you entered file:/// you would see your root directory structure pop up in the browser. 

Either the Documents folder has been deleted, moved, or renamed. Can you list the contents of your /home directory? 

Open up a terminal (Applications -> accessories -> Terminal) and run the command:

**ls -al**

and print the output here.

---

### Post by dec7m2 on 2009-04-09
chris@chris-desktop:~$ gksudo nautilus

(gksudo:5722): GVFS-RemoteVolumeMonitor-WARNING **: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory

and when i

chris@chris-desktop:~$ ls -al
total 212
drwxr-xr-x 36 chris chris 4096 2009-04-09 10:47 .
drwxr-xr-x  6 root  root  4096 2009-03-25 12:04 ..
drwx------  3 chris chris 4096 2009-03-25 11:49 .adobe
-rw-------  1 chris chris  178 2009-03-20 09:21 .bash_history
-rw-r--r--  1 chris chris  220 2009-03-19 11:48 .bash_logout
-rw-r--r--  1 chris chris 3115 2009-03-19 11:48 .bashrc
drwxr-xr-x  3 chris chris 4096 2009-03-19 12:27 .cache
drwxr-xr-x  6 chris chris 4096 2009-04-09 10:47 .config
drwx------  3 chris chris 4096 2009-03-19 12:26 .dbus
drwxr-xr-x  2 chris chris 4096 2009-04-06 09:40 Desktop
-rw-------  1 chris admin   28 2009-04-09 10:47 .dmrc
drwxr-xr-x  2 chris chris 4096 2009-03-19 12:26 Documents
-rw-------  1 chris chris   16 2009-03-19 12:26 .esd_auth
drwxr-xr-x  7 chris chris 4096 2009-03-20 08:41 .evolution
lrwxrwxrwx  1 chris chris   26 2009-03-19 11:48 Examples -> /usr/share/example-content
drwxr-xr-x  2 chris chris 4096 2009-04-08 09:59 .fontconfig
drwx------  4 chris chris 4096 2009-04-09 10:47 .gconf
drwx------  2 chris chris 4096 2009-04-09 10:52 .gconfd
-rw-r-----  1 chris chris    0 2009-04-09 10:51 .gksu.lock
drwx------ 10 chris chris 4096 2009-04-09 10:41 .gnome2
drwx------  2 chris chris 4096 2009-03-19 12:27 .gnome2_private
drwx------  2 chris chris 4096 2009-03-19 12:26 .gnupg
drwxr-xr-x  2 chris chris 4096 2009-04-07 11:17 .gstreamer-0.10
-rw-r--r--  1 chris admin  108 2009-04-09 10:47 .gtk-bookmarks
dr-x------  2 chris admin    0 2009-04-09 10:47 .gvfs
-rw-------  1 chris admin 4331 2009-04-09 10:47 .ICEauthority
drwxr-xr-x  2 chris chris 4096 2009-03-19 14:32 .icons
drwxr-xr-x  3 chris admin 4096 2009-04-08 10:02 .java
drwx------  3 chris chris 4096 2009-03-19 12:27 .local
drwx------  3 chris chris 4096 2009-03-25 11:49 .macromedia
drwx------  4 chris chris 4096 2009-03-19 14:25 .mozilla
drwxr-xr-x  2 chris chris 4096 2009-03-19 12:26 Music
drwxr-xr-x  3 chris chris 4096 2009-04-07 11:12 .nautilus
-rw-r--r--  1 chris chris  334 2009-03-25 11:18 .nvidia-settings-rc
drwx------  3 chris chris 4096 2009-03-25 11:45 .openoffice.org2
drwxr-xr-x  2 chris chris 4096 2009-03-19 12:26 Pictures
-rw-r--r--  1 chris chris  675 2009-03-19 11:48 .profile
drwxr-xr-x  2 chris chris 4096 2009-03-19 12:26 Public
drwxr-xr-x  2 chris chris 4096 2009-03-19 12:27 .pulse
-rw-------  1 chris chris  256 2009-03-19 12:26 .pulse-cookie
-rw-------  1 chris chris 1804 2009-03-25 11:47 .recently-used
-rw-------  1 chris admin 5066 2009-04-09 10:42 .recently-used.xbel
-rw-r--r--  1 chris chris    0 2009-03-19 14:10 .sudo_as_admin_successful
drwxr-xr-x  2 chris chris 4096 2009-03-19 12:26 Templates
drwxr-xr-x  2 chris chris 4096 2009-03-19 14:32 .themes
drwx------  4 chris chris 4096 2009-03-24 14:52 .thumbnails
drwxr-xr-x  4 chris chris 4096 2009-03-20 09:09 .tomboy
-rw-r--r--  1 chris chris 6491 2009-03-20 09:09 .tomboy.log
drwxr-xr-x  2 chris chris 4096 2009-03-19 14:08 .update-manager-core
drwx------  2 chris chris 4096 2009-03-19 12:27 .update-notifier
drwxr-xr-x  2 chris chris 4096 2009-03-19 12:26 Videos
drwxr-xr-x  2 chris chris 4096 2009-03-20 09:09 .wapi
-rw-------  1 chris admin  124 2009-04-09 10:47 .Xauthority
-rw-r--r--  1 chris admin 3014 2009-04-09 10:52 .xsession-errors

---

### Post by dec7m2 on 2009-04-13
it did not work

---

### Post by askreet on 2009-04-13
You really should use a better subject in your post to attract more help, maybe that error message.

Also, you never say *what you do* to see the error, or what it looks like, how often it happens, etc.  Detail is important.

Thanks,
askreet

---

### Post by dec7m2 on 2009-04-13
Could not open location 'file:///home/chris'
No application is registered as handling this file

---

### Post by 3rdalbum on 2009-04-13
Can you please tell us what you are doing that triggers the error message, and if possible tell us what program is displaying the error message? For instance, does it appear when you double-click a folder icon? Does it appear when you drag a file from K3B to Nautilus? What exactly are you doing when the message appears?

---

### Post by dec7m2 on 2009-04-13
when i try to access a folder or try to save a picture with with the screenshot function and this appears 
Could not open location 'file:///home/chris'
No application is registered as handling this file

---

