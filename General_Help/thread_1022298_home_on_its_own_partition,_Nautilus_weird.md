---
title: "/home on its own partition, Nautilus weird"
date: 2008-12-26
forum: General Help
---

### Post by mikeman141 on 2008-12-26
Hey all,

I just reinstalled Ibex on my Dell XPS 1530 after deciding I wanted to dual boot.  

This time, I put my home directory in its own parition so that my documents and stuff could be more easily shared between windows and linux.  

The partitions are as follows:

Windows partition 50 gigs
/home ext3 100 gigs
swap 10 gigs
/ ext3 100 gigs

Everything seems to be ok except for a weird thing that nautilus is doing.

If i click on places and go to "mike" (my home directory" the folder opens up in nautilus but has nothing inside it (except for some lnk called examples).

If I go to the home directory via the command line its populated with the usual...Videos, Documents...etc

If I go straight to one of those folders from the "places" menu (i.e. click directly on Videos) it opens up with all of the videos that I have placed there.

If nautilus is already open, I can click on the "mike" directory on the left side, and the same behaviour is repeated.

Is this some kind of weirdness associated with the seperate /home/ partition?

thanks

---

### Post by ibuclaw on 2008-12-26
If you haven't done so already, go into **Edit -> Preferences** in Nautilus and click on the behaviour tab and enable the "**Always open in browser windows**" checkbox, then close and open Nautilus to your home directory.

Above the side pane, you should see a Pencil and Notepad icon, click it to switch from the button-based location bar to the text-based entry bar.

Does it say /home/mike ? (Or whatever your username is).

Regards
Iain

---

### Post by LowSky on 2008-12-26
are you sure you created a seperate /home partition? check gparted to make sure

Also No reason root needs 100 GB of space... 15-20GB TOPS and that if you go installing everything you can humanly think of form synaptic.
Swap should only be double your RAM, don't wast space if you don't need to.

---

### Post by mikeman141 on 2008-12-26
Thanks for the quick response,

Yea, it reads /home/mike

here's 2 screenshots, one of my home directory selected with no content inside, and the other with a directory in the home folder selected.

[IMG]http://kadin.portfolio.googlepages.com/home.png[/IMG]


[IMG]http://kadin.portfolio.googlepages.com/docs.png[/IMG]

---

### Post by mikeman141 on 2008-12-26
Oh,  I checked gparted, and I forgot about 1 detail,

I did definitely mount /home/ on a seperate partition, but it is ext2 not ext3, because I read somewhere it was easier to mount ext2 on windoze.

Could this be the problem somehow?

---

### Post by ibuclaw on 2008-12-26
For argumental purposes, I'm going to say: No, using ext2 does not effect this issue.

In Nautilus (in your /home/mike directory) Press **F5**, maybe the folders need refreshing...

Regards
Iain

---

### Post by ibuclaw on 2008-12-26
Aha...

In the terminal, type in:
```
gedit ~/.hidden
```

Is there a list of file/directory names in that file?

If so, close the file and remove it:
```
rm ~/.hidden
```

Regards
Iain

---

### Post by mikeman141 on 2008-12-26
nope...nothing in there.


I tried the view menu - show hidden files and a few other things show up:

.gnome2 (directory)
.bash_logout
.bashrc
.profile

and that's it, no videos, documents,etc


Weird eh?

---

### Post by ibuclaw on 2008-12-26
What are the permissions of the folders/directories?

```
ls -l ~
```
I fail to see why, but maybe you don't have full permissions to everything
```
sudo chown mike:mike ~ -R
```
Regards
Iain

---

### Post by mikeman141 on 2008-12-26
Here's the output of ls

drwxrwxrwx  3 mike mike 4096 2008-12-26 16:52 Desktop
drwxrwxrwx  6 mike mike 4096 2008-12-26 15:36 Documents
drwxrwxrwx  2 mike mike 4096 2008-12-26 15:15 drivers-software-extras
lrwxrwxrwx  1 mike mike   26 2008-12-26 07:23 Examples -> /usr/share/example-content
drwxrwxrwx  3 mike mike 4096 2008-12-26 15:41 Music
drwxrwxrwx 26 mike mike 4096 2008-12-26 16:16 Pictures
drwxrwxrwx  5 mike mike 4096 2008-12-26 15:51 Videos


the chown command did some funky stuff and failed because of permissions, which is strange, because I used sudo.

mike@mike-ubuntu:~$ sudo chown mike:mike ~ -R
chown: changing ownership of `/home/mike/.gnome2/gnome-power-manager/profile-DELL_XT8168-57720-589-discharging.csv': Stale NFS file handle
chown: changing ownership of `/home/mike/.Xauthority': Stale NFS file handle
chown: changing ownership of `/home/mike/.xsession-errors': Stale NFS file handle
chown: changing ownership of `/home/mike/.dmrc': Stale NFS file handle
chown: changing ownership of `/home/mike/.gconf/desktop/gnome/applications/window_manager/%gconf.xml': Stale NFS file handle
chown: changing ownership of `/home/mike/.nautilus/metafiles/x-nautilus-desktop:%2F%2F%2F.xml': Stale NFS file handle
chown: cannot access `/home/mike/.gvfs': Permission denied



Then I tried,

mike@mike-ubuntu:~$ sudo chown mike /home/mike/.gvfs
chown: cannot access `/home/mike/.gvfs': Permission denied

very strange, do you think this may have something to do with files leftover from my previous installation?

Thanks for all your help man.

---

### Post by ibuclaw on 2008-12-26
Don't worry about the .gvfs folder, that is supposed to be non-readable.

As for the "Stale NFS file handle" message, you may need to run fsck on your /home partition.

run:
```
df -h | grep home
```
and take note of the /dev/sd* location

Now its probably best to save and close all running applications at this point and run:
```
sudo shutdown now
```
in the terminal to drop to runlevel 1, or reboot into recovery mode.

Select "Root Shell" in the options menu, and type in:
```
umount /dev/sd**a1**

fsck -y /dev/sd**a1**

mount /dev/sd**a1**

```
Replace "**a1**" with the /dev/sd* location of your home folder.

Once it has finished, type in:
```
exit
```
and then "Continue with Normal Boot"

Let us know how it goes.

Regards
Iain

[EDIT]
Also, after having a second review of what you previously posted, I thought I might like to make you aware that it is a security risk to have your directories and files writeable by all users.
```
sudo find /home/mike -type d -exec chmod 755 "{}" \;
```

---

### Post by mikeman141 on 2008-12-26
IT WORKED.

thanks, man, I much appreciate it.

---

