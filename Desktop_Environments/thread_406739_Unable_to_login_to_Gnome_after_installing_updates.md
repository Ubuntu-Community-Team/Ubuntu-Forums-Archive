---
title: "Unable to login to Gnome after installing updates"
date: 2007-04-11
forum: Desktop Environments
---

### Post by vik.vaughn on 2007-04-11
I installed several automatic updates about a week ago and have since been unable to login to gnome. the nvidia video driver loads up fine, and I am able to issue the login credentials at the graphical login prompt, but once the OS tries to bring up my user environment, it flakes out and kicks me back out to the login prompt again.

I have beryl installed if that could be an issue. Any ideas what could have caused this problem? Thanks in advance for any help.

---

### Post by Moosey on 2007-04-11
EXACT same problem here (also using Beryl). My guess is that, as I remember seeing updates for the X server included in the last set of updates I did, updating the X server must have broken Beryl/GNOME. I imagine fiddling round with xorg.conf will probably play an important role in getting the problem fixed but I have not found a solution myself. I personally plan to re-install my entire Ubuntu anyway, as the amount of tinkering I've done, without really knowing what I was doing, was sure to have broken something that will undoubtedly come back to haunt me in the future.

Sorry that I could not be any actual help,

Moosey

---

### Post by cyph33r on 2007-04-11
I'm had the same problem after updating. I also have Beryl running. 
GDM would restart after I logged in.

How I managed to solve this was to reinstall the NVIDIA driver and all was working again.
You can also try this: [Envy]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by tachyon462 on 2007-04-11
I just took care of the exact same problem about 10 minutes ago.
I logged into a terminal session and was able to remove beryl manager with
"sudo apt-get remove beryl"
but now I can't get it back on.....I tried envy but I've already got the latest drivers.
any ideas?

---

### Post by vik.vaughn on 2007-04-11
I was able to solve my problem by removing beryl. I haven't reinstalled it yet to see if it would work when it's installed AFTER the updates, but I imagine it will probably work fine.

tachyon have you tried removing beryl, then uninstalling the Nvidia driver and reinstalling it?

---

### Post by quixote on 2007-04-12
I have the same problem in Kubuntu, Edgy, and NOT using Beryl.  So it's the same problem in KDE.  I ran the automatic updates, and also noticed some for xorg & a few other X items.  Then I have the same situation as the first commenter: I get my graphical login, and then it just goes to a black screen and stays there.  It doesn't matter which of the start-up options I try by right-clicking the "choices" icon to the left of the form fields for login.

If I boot up in recovery mode, I'm "root" with no gui, although if I type "startx" it comes right up.  That implies there's nothing actually wrong with xorg.conf.  (Or does it?)  

Anybody have any answers?

---

### Post by igknighted on 2007-04-12
run df -h in the terminal to see if you are out of disk space.  Also, are using a separate /home partition?  If so, you might have gotten the update that renames hard drives to SATA and now you home partition isn't being mounted, so your setting cannot load.

---

### Post by quixote on 2007-04-12
No, I have, like, 3GB or so free.  That shouldn't be a problem.

I've never heard of the SATA thing.  Anything I can do about it?

---

### Post by quixote on 2007-04-12
PS.  My /home is not in a separate partition from the system files etc.  It's all on the ext3 formatted partition of a dual boot system with WinXp.

---

### Post by quixote on 2007-04-13
This is embarrassing.  I checked, and root (/) is on different logical partition than /home (dev/hda6  and dev/hda7).  I guess that means it could be doing something to the /home partition that wouldn't affect "root".  

But what is it doing?  And what can I do to fix it?

---

