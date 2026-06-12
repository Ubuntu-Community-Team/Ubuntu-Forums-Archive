---
title: "gnome-panel crashing?"
date: 2006-12-29
forum: Desktop Environments
---

### Post by scudellari on 2006-12-29
Hi all,
My gnome-panel is crashing repeatedly and I don't know what to do.  The Bug Reporting tool pops up and gives me a lot of cryptic messages.  I've attached the output to this post for review.

The last thing I did was right click on an ISO file and selected "Extract here".  This seems COMPLETELY unrelated to me, but I'm far from a linux guru, so who knows.

Anyway, I've tried Ctrl-Alt-Backspace to restart window server.  When that didn't work I restarted the whole machine.  Somehow gnome-panel STILL keeps on crashing.  It crashes, and the Ubuntu debug reporting tool pops up notifying me.  I click close.  It tries to start gnome-panel again and the whole process starts all over.

Obviously, this make the machine completely useless from Desktop perspective, but everything else seems to work fine.  I have been connecting via ssh to try to resolve the issue.

I ran ```
apt-get --reinstall install gnome-panel
``` but it didn't help.

I really don't know where to go from here.  Any suggestions would be greatly appreciated!

Thanks,
Ryan

---

### Post by scudellari on 2006-12-29
Update:  I just tried logging in as a different user, and it works fine.  Somehow I messed up my gnome-panel config?  I don't get it...

Any ideas on how I can restore my user's gnome-panel settings?

Thanks,
Ryan

---

### Post by ariogenki on 2006-12-29
I have the same issue !Help!!   And last thing I did was install an application...

---

### Post by H.H on 2006-12-30
I have the same problem,  no problem to log in as a different user.  This happened when i tried to extract a .ISO file.

---

### Post by H.H on 2006-12-30
Solved it,

I logged in to failsafe console and did this
rm .recently-used.xbel

rm -rf ~/.gnome* && rf -rf .gconf*

rm -rf ~/.gtkrc*

This restored my gnome desktop to default.

---

### Post by scudellari on 2007-01-02
Do you have any idea how extracting an ISO did this?  I find this very bizzare.

---

### Post by mts-fi on 2007-01-09
> **H.H said:**
> I have the same problem,  no problem to log in as a different user.  This happened when i tried to extract a .ISO file.

I had the same problem...

Here is another solution:
delete (or rename) the
.recently-used.xbel (It's hidden, press Ctrl+h to see it)
file found in your home directory

I found it from:
[http://ubuntuforums.org/showthread.php?t=316356](http://ubuntuforums.org/showthread.php?t=316356)

See also:
[http://bugzilla.gnome.org/show_bug.cgi?id=358044](http://bugzilla.gnome.org/show_bug.cgi?id=358044)

---

### Post by RSX311 on 2007-01-18
wow, I too tried running a .iso file and gnome-panel kept crashing.

deleting .recently-used.xbel worked!

Thanks!

weird bug

---

### Post by uncleducati on 2007-03-15
Thanks for the tip, it worked, but a couple things I found might help newbies that are attempting this:

Don't worry, this looks daunting, but nothing permanent and evil has happened, relax :) 

1. To get into the GRUB menu, you wait just a couple seconds after your computer turns on and then you'll see some gibberish about GRUB, so then hit <Escape> within a couple seconds and it will give you another menu
2. You should see a few different options, the one you want will probably be the second one down, should say something about 
  Ubuntu, kernel 2.6.17-generic (recovery mode), that's the one you want
3. You'll see a bunch of junk scroll past, but eventually it will ask you for a password, this is your root password, so hopefully you already set one up, enter that.
4. Then you'll get a command prompt, (#) and then you need to find the user's home directory, because you're root and so the files you need to change are in a different place, then once you get to your home directory you have to delete a couple files and folders, so go:
  cd /home/whatever_your_username_is
  rm .recently-used.xbel
  rm -rf ~/.gnome* && rm -rf .gconf* (there was a typo on the earlier post, the second one should've been rm, it was rf, no worries)
  rm -rf ~/.gtkrc*
5. So now you have the evil files deleted, don't worry, it won't kill your computer, so now you have to reboot, so just type
  reboot
6. Your computer should come back to your desktop and be happy.


HTH,
Cameron 
San Diego

---

