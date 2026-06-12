---
title: "How do I make my own custom LiveDVD of Ubuntu???"
date: 2009-01-12
forum: General Help
---

### Post by grndslm on 2009-01-12
OK... so the title should be mostly self-explanatory.

I'm trying to create my own custom LiveDVD of Ubuntu 8.04-1 or maybe even gOS Space 2.9.  I would like it to have today's current base packages along with current additional packages that I use.  I'd also like many defaults for all newly created users, specifically my favorite Firefox extensions & my Compiz settings.  That way, I can tell all my friends... "Hey you can have everything I use, customized the way I like, all on this one DVD.  The only thing you need to do is pick a username/password and configure your graphics card."

What programs should I use?  Have you guys used any of them yourselves? Somebody in the #ubuntu channel suggested UCK and it's mostly what I'm looking for, but on [what I think was] the last step, the program just stopped at 76% repackaging the ISO.  What's the problem, or what else should I use?

Any other heads up I should be aware about??  I really need to know how to make my personal Compiz & Firefox settings the default system-wide settings for all newly created users.  That's almost more important to me than having the updated and extra packages already on the DVD.  Thoughts??

---

### Post by adam.ec on 2009-01-12
I'd go with UCK and minibuntu. Not sure what happened with your UCK but I've never had problems with it. I know it takes a long time to build the ISO but it's worth it for customizing your LiveDVD's.

Also, are you wanting them to just be able to install from the DVD or are you going to be running their systems all the time from live disk? If it's the latter you might want to reconsider the distro you use because using things like Compiz and Ubuntu as a live system is going to make your systems crawl.

---

### Post by grndslm on 2009-01-12
> **adam.ec said:**
> I'd go with UCK and minibuntu. Not sure what happened with your UCK but I've never had problems with it.Dunno what happened either... it just froze and the progress bar didn't change from 76% for nearly an hour.  

> **adam.ec said:**
> Also, are you wanting them to just be able to install from the DVD or are you going to be running their systems all the time from live disk?Either/or really... just like the "real deal" Ubuntu.  I was going to configure Compiz the way I find it most useful (i.e. - no wobbly windows for starters), but I was still going to leave metacity as default WM for the LiveDVD.  If they want Compiz, I'll instruct them on how to change from metacity after they've got their graphics driver installed.

Test with...
compiz --replace

Make default with...
nano (or gedit) ~/.gnomerc
ADD:   export WINDOW_MANAGER=/usr/bin/compiz
SAVE

---

### Post by grndslm on 2009-01-14
Anybody else trying to make their own distro??  What are *you* using?

Wondering if there's any better way for me to go about my real goals (Saving my Firefox & Compiz prefs as system-wide defaults for all users)... or in other words, what are these programs like uck & reconstructor really doing?  Or how do the pros do this stuff??

---

### Post by adam.ec on 2009-01-14
Ahhh, now, this is something a little different. If you are wanting to create entirely your own distro there are a few approaches to choose from. Linux From Scratch will help you start off on something that is completely your own work, but it is reall from _scratch_. If you need something that is a bit more set up from the beginning but still want your 'own' distro then try downloading a minimal version of Debian, Slackware (first 2 CD's only) or Fedora. Initially only install the minimum needed packages and work from there. At least this will give you the support of some kind of packaging system. Finally, If you really can't be bothered with this stuff and you really just wanted a normal distro with custom packages and environment try something like the minibuntu and UCK options. There is also something like UCK for Fedora but I can't remember what it's called.

Apps like UCK basically take a bog standard distro like Ubuntu and create configuration and startup scripts with an easy to use GUI so you can make your own live disks or preconfigured versions of said distro.

Mostly a personal opinion more than anything else but if you're going to make a live distro I'd use one that has already been 'created' like Damn Small, Puppy, Slax or Knoppix. This is mainly because these distros have already been optimized to run live and will work much more smoothly direct from CD or DVD.

---

### Post by grndslm on 2009-01-14
I'm really trying to stick with Ubuntu for reasons that should be obvious to most people on this forum.

I tried UCK one more time today, and it froze at 77% again.  Here's the output...

```
ISO customization script finished
Updating files lists...
Packing SquashFS image...
Parallel mksquashfs: Using 4 processors
Creating little endian 3.1 filesystem on /home/grndslm/tmp/remaster-iso/casper/filesystem.squashfs, block size 131072.
TIOCGWINZ ioctl failed, defaulting to 80 columns
[============================================              ] 114185/147657  77%
```

I've only done these things so far (not even touching the Firefox & Compiz customizations that will have to be done thru command line only, I believe)...

(1) added repositories
(2) aptitude update; aptitude upgrade -y
(3) aptitude install [~150 packages w/ their deps]
(4) wget frostwire.deb; dpkg -i frostwire.deb; rm frostwire.deb
(5) ln /usr/bin/gnome-terminal /usr/bin/gterm; chmod 755 /usr/bin/gterm
(6) fc-cache -fv
(7) xmodmap -e "keycode 77 = " (disables numlock key)
(8 ) added this to the empty xorg.conf file (this could be the problem??)

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "ctrl:nocaps"
EndSection

---

### Post by spcwingo on 2009-01-14
Have you tried remastersys?  I have used it with success in the past.

---

### Post by grndslm on 2009-01-14
UPDATE:

Tried running UCK on my laptop, and it froze at 76%.  Geez, I wish I could get to 78%.  I guess I'm gonna have to do this 10 times, adding only one step at a time until I find out what the problem is... prolly the xorg config??

---

### Post by grndslm on 2009-01-14
OK... So I figured out that the biggest culprit of freezing UCK was me installing the extra 100+ packages & dependencies.  Bummer.

I guess I'm gonna try installing my 8.04.2 disc, installing the extra packages, and then using remastersys.

---

### Post by thomasr on 2009-01-14
Remastersys has worked well for me. I consider it a real gem.

---

### Post by grndslm on 2009-01-15
remastersys was just the ticket...

I now have all the upgraded base packages installed & all the ~460 extra packages/libraries I wanted installed (also added google desktop this time, since beagle and tracker don't "do it for me").

Now I need to find out how I can make the settings in these personal folders (.compiz, .gconf, .gconfd, .gnome2, .mozilla/firefox, .nautilus) the default settings for all newly created users on that liveDVD.

I'm thinking about just copying those hidden folders to a directory like /usr/share/settings before I make the liveDVD iso, so that way I can at least easily copy them to a new user's home folder.  But I'd still prefer some way to do this automatically, like copy those files to the home dir as soon as the adduser command creates a new home dir.  Or does gconf really have all the default settings for Compiz?  I really doubt gconf could handle the Firefox extensions, so that leaves me with copying over the personal configs to each individual home dir.

Now for some random questions...

(1)  UCK question --  It kept asking me if I wanted to delete the win32 files.  What win32 files??  ntfs-3g?
(2)  remastersys question -- Will a backup still bootup into a liveCD/DVD session? (will try this out tomorrow)
(3)  remastersys question -- What's the difference between isolinux and grub?
(4)  xmodmap -e "keycode 77 = " -- Anybody know where to put this command so it will start at every boot up?

EDIT:
(5)  and a general liveDVD question -- If the installed system is 4.3GB... do I even need to compress the fs with casper??  If I have ~4GB of uncompressed files, shouldn't I just leave them uncompressed?  I suppose I couldn't keep using remastersys for this, tho.

---

### Post by ajcham on 2009-01-15
> **grndslm said:**
> Now I need to find out how I can make the settings in these personal folders (.compiz, .gconf, .gconfd, .gnome2, .mozilla/firefox, .nautilus) the default settings for all newly created users on that liveDVD.

I'm not sure, but is that not what the **/etc/skel** directory is for?

---

### Post by grndslm on 2009-01-15
:-o :-o  OMG... I dunno why I thought that feature wouldn't be built into Linux.  I just had no idea!!  I've been wasting so much time configuring stuff for family & friends one by one...

Never again.  Thanks ajcham!!


Anybody know about the other questions...

(1) UCK question -- It kept asking me if I wanted to delete the win32 files. What win32 files?? ntfs-3g?

(4) xmodmap -e "keycode 77 = " -- Anybody know where to put this command so it will start at every boot up?

(5) and a general liveDVD question -- If the installed system is 4.3GB... do I even need to compress the fs with casper?? If I have ~4GB of uncompressed files, shouldn't I just leave them uncompressed? I suppose I couldn't keep using remastersys for this, tho.

Thanks again.

---

### Post by grndslm on 2009-01-16
Bump didilly ump.

---

### Post by ridgeland on 2009-06-26
Hi grndslm,
> (4) xmodmap -e "keycode 77 = " -- Anybody know where to put this command so it will start at every boot up?

I remap my CapsLock to be a second Tab key.

/etc/gdm/PostLogin/Default contains:
```
#!/bin/sh
xmodmap /UserHome/Bash/Xmodmap.CAPSLOCK
```

/UserHome/Bash/Xmodmap.CAPSLOCK contains:
```
remove Lock = Caps_Lock
keysym Caps_Lock = Tab
```

That might point you in the right direction.  Hopefully you solved this issue long ago (like in January) :)

---

