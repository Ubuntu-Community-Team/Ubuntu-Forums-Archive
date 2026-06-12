---
title: "Home folder not opening - nautilus? UID?"
date: 2010-11-29
forum: Desktop Environments
---

### Post by candtalan on 2010-11-29
I am helping a friend with his ubuntu PC, and I reinstalled to go from 8.04 to 10.10. In the process I had reconfigured his home directory to be a separate partition, it all worked ok. 
Although I did have to do the new install as a new username etc as I think is usual in such cases. I am not *convinced* I sorted all ownerships and permissions out. after the  new install, I did change ownership of /home/oldusername contents using chown, which seemed to work ok. 

I do note that for the old username in the original 8.04 installation the uid was 1000, but the same username in the new installation is 1001

the problem is that nautilus does not start from
 Places > Home folder
all that is seen is a waiting circle, which soon stops.

But nautilus *does* start from a user terminal with just   
nautilus

What to do, and why, please?
tia

---

### Post by tom4everitt on 2010-11-29
You did use the -R flag when chown? Otherwise do
```

sudo chown -R /home/username

```
to make sure all folders and subfolders get the right owner. 

What I usually do with Gnome problems is to reset all Gnome settings. Simply delete the following folders in the home directory:

.config
.gconfd
.gnome2
.gnome2_private
.thumbnails

---

### Post by candtalan on 2010-11-29
> **tom4everitt said:**
> You did use the -R flag when chown? Otherwise do
```

sudo chown -R /home/username

```
to make sure all folders and subfolders get the right owner. 

What I usually do with Gnome problems is to reset all Gnome settings. Simply delete the following folders in the home directory:

.config
.gconfd
.gnome2
.gnome2_private
.thumbnails

Thanks!
Yes, I did use the -R 

About deleting the gnome stuff - should I be at the time logged in as user, or not? Or maybe logged in as another user maybe, or live CD?
I deleted them one by one and no errors appeared, but replacements have re-appeared. Should I log out and in or re-boot or something?

---

### Post by tom4everitt on 2010-11-29
It usually works fine being logged in as that user; but it doesn't hurt being another user. 

Yes, they will be replaced by new ones pretty quickly if you're logged in as that user. Otherwise new ones will be created upon login. The new ones will contain the default settings, so the end result is that all Gnome settings are reset to their defaults.

---

### Post by candtalan on 2010-11-29
Still not working. Strange. I can create other users, and the 
Places>Home folder 
works ok for them(!) I can see nothing wrong with the 
usr/share/applications desktop config file for home
in fact it is the same one used by the other (test) users, so it must be ok in itself.

Something is screwed which is associated with the oldusername. I did some file-by-file comparisons with a (working) newuser and saw that olduser had missing .gconf.apps/nautilus/desktop-metadata and copied one across and changed owner and permissions to suit, but that was not it. Worth a try I suppose.

From what the friend says, this has not been working even in Ubuntu 8.04.4, and he has been getting to his documents by opening a folder on the desktop, and then using (nautilus) what he can navigate to.

Any comments appreciated!

---

### Post by tom4everitt on 2010-11-29
Hmm, I wonder what command is executed when clicking on one of the Places entries. For the home folder, I would expect it to be either:
```

nautilus /home/username &, or
nautilus $HOME &

```
They both do the same thing as clicking on the entry is supposed to do, and I can't really think of anything else reasonable... (Perhaps there is even a way to find out?)

In the first case, nautilus /home/username, obviously much could go wrong if one for example changed the name of ones home folder. 

In the second case, nautilus $HOME, messing with home folder name should be fine, but problem might arise if the $HOME is incorrectly set. 

Personally, I feel that the second option is more likely. Is it only the home folder malfunctioning, or are all entries malfunctioning? what about old vs newly added entries? Does the $HOME variable seem correct? I'm really just speculating, as you can surely tell :)

---

### Post by candtalan on 2010-11-29
> **tom4everitt said:**
> Hmm, I wonder what command is executed when clicking on one of the Places entries. For the home folder, I would expect it to be either:
```

nautilus /home/username &, or
nautilus $HOME &

```
They both do the same thing as clicking on the entry is supposed to do, and I can't really think of anything else reasonable... (Perhaps there is even a way to find out?)

In the first case, nautilus /home/username, obviously much could go wrong if one for example changed the name of ones home folder. 

In the second case, nautilus $HOME, messing with home folder name should be fine, but problem might arise if the $HOME is incorrectly set. 

Personally, I feel that the second option is more likely. Is it only the home folder malfunctioning, or are all entries malfunctioning? what about old vs newly added entries? Does the $HOME variable seem correct? I'm really just speculating, as you can surely tell :)

The problem PC is remote and I have been using teamviewer (non commercial) to work on it, and it is not available now for a while. However, the  item Home Folder in Places > Home Folder is, I believe, (in ubuntu 10.10) a desktop configuration file which is found in usr/share/applications/Home Folder
and its properties say  its command is
nautilus --no-desktop
So when this link is clicked by baduser, something goes wrong. When gooduser clicks th elink on their desktop, it works ok.

If baduser opens a terminal and types simply 
nautilus
again nautilus opens and runs ok.

??

tia

---

### Post by dkjMusic on 2010-11-30
Pardon me if I am way off-base but...

Has "baduser" configured some other application than Nautilus, even inadvertently, to open folders? I know once I right-clicked my Music folder, selected "Open With Other Application..." and chose Rhythmbox without realising that the "Remember this application" box at the bottom being checked (by default) would then make Rhythmbox try to open ALL folders, even those in the Places menu.

I've seen several "Places folders won't open properly" problems due to this.

Again, it's just a guess w/o reading all the details of your post (sorry).

---

