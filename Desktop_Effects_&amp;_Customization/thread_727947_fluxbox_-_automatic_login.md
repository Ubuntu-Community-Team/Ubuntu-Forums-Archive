---
title: "fluxbox - automatic login"
date: 2008-03-18
forum: Desktop Effects &amp; Customization
---

### Post by marcosramos on 2008-03-18
I use slim as display manager and fluxbox for window manager - fluxbuntu 7.10 TC

Is there any way to set up automatic login to fluxbox?

I've set up, in /etc/slim.conf the default_user <username>
there is no such variable as default_pass ...

Any ideas?


thank you so much

---

### Post by zolodon on 2008-03-20
I've been searching for this answer too...with no luck yet.

In my case, I want to boot a kiosk workstation all the way to a logged in desktop without user intervention or logins required.

---

### Post by kerry_s on 2008-03-20
**sudo apt-get install rungetty**

(when using xedit click the save 2x to save)
**sudo xedit /etc/event.d/tty1**
comment out
**respawn /sbin/getty 38400 tty1**
put
**exec respawn /sbin/rungetty tty1 --autologin user**

replace "user" with your login name

**xedit ~/.bash_profile**
put 
**startx**
at the bottom, don't forget to leave 1 blank line at the bottom.

**reboot**

last remove slim
**sudo apt-get remove --purge slim**

you can substitute "xedit" with your editor of choice

---

### Post by littlebattler on 2008-03-21
> **kerry_s said:**
> **sudo apt-get install rungetty**

(when using xedit click the save 2x to save)
**sudo xedit /etc/event.d/tty1**
comment out
**respawn /sbin/getty 38400 tty1**
put
**respawn /sbin/rungetty tty1 --autologin user**

replace "user" with your login name

**xedit ~/.bash_profile**
put 
**startx**
at the bottom, don't forget to leave 1 blank line at the bottom.

last remove slim
**sudo apt-get remove --purge slim**

you can substitute "xedit" with your editor of choice

I just joined to say DONT follow this advice. It has broken my system completely and i am having trouble restoring it to good working order. Again avoid this advice completely.

If you are unlucky enough to have tried out and are now faced with a broken apt, try reading [http://ubuntuforums.org/archive/index.php/t-637322.html](http://ubuntuforums.org/archive/index.php/t-637322.html) 

good luck

update. system is well and truly hosed. to make matters worse freevo no longer works. thanks for the advice, you've just cost me a re-install and then i'll have to painstakingly recreate my freevo install which has taken me several days of experimentation, to make matters worse i have no wireless anymore so i cannot backup my files and recreate them later.

---

### Post by kerry_s on 2008-03-21
> **littlebattler said:**
> I just joined to say DONT follow this advice. It has broken my system completely and i am having trouble restoring it to good working order. Again avoid this advice completely.

If you are unlucky enough to have tried out and are now faced with a broken apt, try reading [http://ubuntuforums.org/archive/index.php/t-637322.html](http://ubuntuforums.org/archive/index.php/t-637322.html) 

good luck

update. system is well and truly hosed. to make matters worse freevo no longer works. thanks for the advice, you've just cost me a re-install and then i'll have to painstakingly recreate my freevo install which has taken me several days of experimentation, to make matters worse i have no wireless anymore so i cannot backup my files and recreate them later.

none of those commands can break your system and no way can it break apt, wireless or any other program. on top of that they are all reversible.

there's something else you did that your not owning up to.

---

### Post by littlebattler on 2008-03-22
> **kerry_s said:**
> none of those commands can break your system and no way can it break apt, wireless or any other program. on top of that they are all reversible.

there's something else you did that your not owning up to.

I did reverse my tt1, restore my .bashrc but there was nothing i could do about the broken apt due to the apt-get remove --purge which left my system unusable. I did NOTHING else at that point except your instructions. It was fully working, to wit, i could have installed rungetty without ANY problems. Obviously my system and apt was FINE before your instructions. Consider that before calling me a liar. 

I was told by the guys in #fluxbuntu that fluxbuntu-defaults shouldnt be messed with, but it seems that is what the apt-get remove slim --purge did, because it affected fluxbuntu-defaults. I tried to reverse it using the instructions in the link i posted earlier but it made things only worse. Upon rebooting I could no longer use my wireless connection to even backup my config files somewhere, so i could sue them after a reinstall.

EDIT. oh and btw your instructions didnt even work because fluxuntu will drop you to a login shell asking you to login and it will not automatically log you in. a bigger man would apologise at this point but you've resorted to calling the victim a liar.shame on you.

---

### Post by kerry_s on 2008-03-22
> **littlebattler said:**
> I did reverse my tt1, restore my .bashrc but there was nothing i could do about the broken apt due to the apt-get remove --purge which left my system unusable. I did NOTHING else at that point except your instructions. It was fully working, to wit, i could have installed rungetty without ANY problems. Obviously my system and apt was FINE before your instructions. Consider that before calling me a liar. 

I was told by the guys in #fluxbuntu that fluxbuntu-defaults shouldnt be messed with, but it seems that is what the apt-get remove slim --purge did, because it affected fluxbuntu-defaults. I tried to reverse it using the instructions in the link i posted earlier but it made things only worse. Upon rebooting I could no longer use my wireless connection to even backup my config files somewhere, so i could sue them after a reinstall.

EDIT. oh and btw your instructions didnt even work because fluxuntu will drop you to a login shell asking you to login and it will not automatically log you in. a bigger man would apologise at this point but you've resorted to calling the victim a liar.shame on you.

:lolflag: SORRY!
i did not call you a liar, i said those commands won't screw up your system. your suppose to be at command line, it's a command line log in instructions with out a log in manager(slim) it goes strait from boot to the desktop. here's what it would look like.
[http://video.google.com/videoplay?docid=-3617653703708436505&hl=en](http://video.google.com/videoplay?docid=-3617653703708436505&hl=en)

modified the instructions, added "exec" which i believe was needed from feisty on, put to reboot before removing slim, so it's not in use at the removal time.

---

