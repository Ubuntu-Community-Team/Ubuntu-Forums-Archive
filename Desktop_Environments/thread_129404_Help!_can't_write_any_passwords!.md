---
title: "Help! can't write any passwords!"
date: 2006-02-13
forum: Desktop Environments
---

### Post by h0mer on 2006-02-13
Hi everybody. I've been using Ubuntu breezy on my gateway 7422gx laptop for over 4 months now. I've managed to sort out every issue reading these forums, but now I find myself in a situation that I can't figure out.

Long story short: wanted to give more HD space to ubuntu since I've rarely used winXP the past months. my winxp ntfs partition was 50GB and had around 20GB free, so I defraged, and used partition magic to resize it to 30GB, freed 20GB. Still in partition magic, I created a new ext2 filling these 20GB. No trouble there.

Reboot: Grub Error 17. So I used the breezy livecd to reinstall grub, and asign the new ext2 partition a mounting point (/home/jose/media). Great!

Reboot: Grub loaded ok. Chose Ubuntu as usual... and as usual, after a while of console messages under the Ubuntu logo, the gdm login screen came up, as beatiful as ever. Typed my username 'jose'... no problem. Began to type my password... but as soon as I type one character, the whole display disappears, crashing back to console. A second later, the login screen is automatically reloaded. Same thing: type my name... ok. Type one character (whichever) into the password box, and crash/reload. What??!!??

Switched to another console (ctrl+alt+f6 or something). entered as jose. startx. Error: display is already running. su root, killed gdm. su jose... startx... victory! I bypassed the login screen and was starting session as usual. 

But as soon as I was there, I knew something was fishy. It seems ok, but whenever I try to do anything that requires admin permissions, the usual password input box comes up, but as soon as type any character, it shuts itself!! What could possibly be going on??

BTW, the new partition is there... some permission restrictions I should update on fstab, but no big deal. But what's up with password thing?

Rebooted, and the same situation occurs everytime. Can't type any password!! Well, I can if in a terminal console... but not directly through gnome's interface. And only half the apps seem to work, or load. 

PLEASE does anyone have a clue about what to do or what might be going on??

---

### Post by Robgould on 2006-02-13
Sounds like time to re-install Ubuntu to me.  You may be able to sort our your issues, but I bet it takes way longer than to just re-install.

---

### Post by h0mer on 2006-02-13
eek!

is there a way to reinstall without losing my profile? I mean, my gnome customization... my evolution emails, my home files, my working ndiswrapper, my working ATI 3D... these last two really worry me...

---

### Post by Robgould on 2006-02-13
I am sure there is.   I just don't know what it is.  If you look in your home directory and see hidden files there are lots of configuration files.  I know your gnome configs are there.  I don't know about evolution, but I am sure there is a way to save your e-mails.  I'm even less sure about the others.  If you are very worried, then you could resolve yourself to taking the time to sort out your new problems.  I hope you figure something out.

---

### Post by shamrock_uk on 2006-02-13
Is your /home folder on a separate partition? If not, this is why it should be - it will allow you to reinstall linux in a snap and simply pick up where you left off without having to worry about deleting any of your personal files or preferences. 

Assuming all your folders are on the same partition, then I would suggest that you install Ubuntu on your newly freed-up 20GB partition - that would safeguard all your /home folder on the old partition. I would use ext3 rather than ext2 however...

Ndiswrapper is a relatively simple install with the correct method, but unfortunately the ATI drivers are hit and miss at the best of times. Both of these would need to be reinstalled if you reinstalled Breezy.


So, to try and head towards a fix instead:

I take it that (without X running) you can log in and give a root password without any problems?

What happens when you run startx as root?

---

### Post by h0mer on 2006-02-13
progress!

same situation... login screen comes up, and can't type passwords. But, I switched to another console, and as root tried to see the gdm process running, so I could kill it. Used

```
ps -e | grep gdm
```

And five instances of gdm were running!! :???: hmmm... did a kill -9 XXXX to all of them, kill Xorg, startx... and voila! my old gnome desktop, completely normal and functional! was able to enter admin sections giving the password and all! even gdesklets was there!

What could this be? too many gdm's interfering and failing? how can I keep them from loading at boot?

---

### Post by h0mer on 2006-02-13
discovered another thing: before, when I shut and reopened my laptop, it asked for my password before resuming. now, after getting it to work again by killing all those gdm's, it doesn't; just resumes where it was before closing the lid. Sooo, I figure out, whatever daemon or process in charge of showing this password prompt on lid reopen, is the one to blame.

Can anyone pinpoint to me which damon/process/whatever is this? how can disable/configure it?

---

### Post by Oxygene on 2006-02-13
I'm no expert, but i think that it has to do with the gdm processes you killed. Now you are the one who directly started "startx" with you profile running implicitly.
what happens if you kill everything including the x-server and then run
/etc/init.d/gdm start

btw: In my ubuntu running now "ps aux|grep gdm" yields
```
root      8243  0.0  0.1  11076  1176 ?        Ss   Feb13   0:00 /usr/sbin/gdm
root      8246  0.0  0.1  11404  1956 ?        S    Feb13   0:00 /usr/sbin/gdm
root      8280  7.1 17.0 235268 176260 ?       S    Feb13  53:44 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
```
Just in case you want to compare how it looks if everything is okay.

---

### Post by h0mer on 2006-02-14
Ok Ubuntu experts, there is progress here that i'd like some insight about.

When I boot the machine and receive the login screen, instead of entering username and trying to type a password (which will fail), I open a new console (ctrl+alt+f5), log as root and type ```
ps -e | grep gdm
``` I get three results: two gdm processes and a gdmgreeter:

XXXX gdm
YYYY gdm
ZZZZ gdmgreeter

where XXXX < YYYY < ZZZZ

I discovered that everytime I try to type a password on the login screen, when the login crashes and reloads itself, the first gdm (XXXX) remains while the second was replaced (YYYY), which I conclude is the one crashing. 

If, in the second console (f5) I try to kill the second gdm first, I get the same result! the login screen crashes and is auto-reloaded. So I discovered that in order to get rid of these processes, I have to kill them in order; kill XXXX then kill YYYY. ZZZZ last. If at this point I try /etc/init.d/gdm start, the loop error starts over again, and I'm faced with other instances of gdm. 

The only solution is to bypass gdm altogether: kill the processes in the specific order, and then startx, which brings me to a fully functional gnome ubuntu.

Sooo, I guess my gdm is gone bad!! Does this make sense? how can I reinstall it? does it make sense to try to replace only gnome, which will keep my wireless and ati configuration, which since its working (and got me a while to get there) I really don't feel like retrying? Do I *need* gdm? can I disable it altogether? or better trying to reinstall it? how?

THANKS for reading... I know it's not a common issue but I've gotten far! maybe others might benefit from this! please help!

---

