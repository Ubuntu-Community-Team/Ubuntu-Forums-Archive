---
title: "Can't log in (Yellow screen with white square)"
date: 2009-04-01
forum: General Help
---

### Post by Ouia on 2009-04-01
Hi there.

Today I wanted to log in to my Ubuntu, but it doesn't work anymore.

Everything is fine up to the point where I log in. My user-name and password work fine, but after that my screen goes 'ubuntu-yellow' and after a while a small white square appears in the left-side upper-corner.

I have been fiddeling with relatime and noatime few days ago. Could that be a problem? I managed to log in between the fiddeling and today btw.


I also have another partition with ubuntustudio and that works fine.
Right now I'm logged in with the livecd.

Besides the relatime thing I have no idea what it could be. I'm also pretty new to linux, so any help would be greatly appreciated.

---

### Post by cptr13 on 2009-04-01
Just dawned on me....April Fools....doh

And I switched from Konq to firefox because I thought it was a browser issue.

---

### Post by Ouia on 2009-04-01
I wish it was an aprils fool joke, but it has nothing to do with my browser. I can't get to my desktop. It just stalls after I login, with a yellow background and a white square in the corner.

---

### Post by markharding557 on 2009-04-01
load up a live cd and then undo the changes you made.
this will be menu.ist in /boot/grub,you need to remove the noatime part and then run sudo update-grub

---

### Post by lisati on 2009-04-01
Scroll down the forum screen, and change CleanV2af to cleanv2

---

### Post by Chemical Imbalance on 2009-04-01
> **Ouia said:**
> Hi there.

Today I wanted to log in to my Ubuntu, but it doesn't work anymore.

Everything is fine up to the point where I log in. My user-name and password work fine, but after that my screen goes 'ubuntu-yellow' and after a while a small white square appears in the left-side upper-corner.

I have been fiddeling with relatime and noatime few days ago. Could that be a problem? I managed to log in between the fiddeling and today btw.


I also have another partition with ubuntustudio and that works fine.
Right now I'm logged in with the livecd.

Besides the relatime thing I have no idea what it could be. I'm also pretty new to linux, so any help would be greatly appreciated.

relatime and noatime  have nothing to do with it.

Have you recently installed graphics drivers?

---

### Post by lisati on 2009-04-01
[http://ubuntuforums.org/showthread.php?t=1113365](http://ubuntuforums.org/showthread.php?t=1113365)

---

### Post by Chemical Imbalance on 2009-04-01
> **lisati said:**
> [http://ubuntuforums.org/showthread.php?t=1113365](http://ubuntuforums.org/showthread.php?t=1113365)

The OP has already stated that he/she is talking about logging in to his/her computer, not the forums.

> I wish it was an aprils fool joke, but it has nothing to do with my browser. I can't get to my desktop. It just stalls after I login, with a yellow background and a white square in the corner.

---

### Post by lisati on 2009-04-01
> **Chemical Imbalance said:**
> The OP has already stated that he/she is talking about logging in to his/her computer, not the forums.

Sorry, my bad.

---

### Post by Ouia on 2009-04-02
I remember last thing I did was install program to change themes. I don't remember which one exactly and I can't look it up since I can't log in :?.

If I remember correctly, I found searching for 'theme' in 'add/remove programs' and it was for gtk.2. Maybe someone knows what I'm talking about.


I tried to use the liveCD to log in, but that won't let me look into the files of my original OS. I can just access the files and programs from the liveCD.

I used recovery mode, but repairing packages and the x-server doesn't do anything.
Going in terminal mode works, but I don't know how to go from there on.
I tried reinstalling the nvidia driver package, but it says I'm in "mode 1" and I should be in "mode 3" for safety reasons.

I'll look up what mode exactly is. (-edit- It's telinit 3)

Ubuntustudio has small issues too now, but not to much to stall the system. But I haven't set up Compiz and usplah for that.

---

### Post by Ouia on 2009-04-02
Does anybody have any idea about what program it could possibly be? 

this is screenshot I found.

[http://xs.to/xs.php?h=xs231&d=08391&f=gtk-chtheme-aud-default-820.jpg](http://xs.to/xs.php?h=xs231&d=08391&f=gtk-chtheme-aud-default-820.jpg)

---

### Post by Ouia on 2009-04-02
I narrowed it down to 

GTK+ 2.0 theme manager

or

Gtk+ 2.0 Change Theme

The first on is on my system (found it after I search for GTK+, only entry as a matter of fact)-. The second one, I looked up on the web. 
Assuming it's the same thing, how do I uninstall/remove it?

BTW, I have reinstalled the drivers, but to no avail.

---

