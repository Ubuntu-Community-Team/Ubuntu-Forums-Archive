---
title: "[SOLVED] ubuntu will not display video with restricted video drivers enabled(but it u"
date: 2008-12-30
forum: General Help
---

### Post by Miles_Prower on 2008-12-30
problem has been solved, see last post for a recap. Thanks to SonnHalter and stderr for the assistance.


being heavily into gaming, I recently installed wine and started trying to install and run a couple of games. At one point my screen resolution was set such that parts of the desktop were not viewable. I figured I would change the resolution to something different, then change back to 1440x900 and ubuntu would work out where the edges of the screen were, just like it did the first time I changed the resolution to 1440x900. 

As it turns out, the resolution I picked is not one that my monitor is capable of displaying. Furthermore, I couldn't switch back to the sane resolution, as I couldn't see anything. Once I realized that I was effectively cut off from the internet without a gui and could not research common fixes for this problem, I curled up in the fetal position and cried for about 8 days, then I managed to get a terminal up with ctrl+alt+f1, ran ```
apt-get remove ubuntu-desktop
``` and then ```
apt-get install ubuntu-desktop
```. That didn't fix anything, so I got into the grub menu and ran from the debug kernel, then chose the "fix x server" option, or whatever it's called. This put this back the the monitors preferred resolution (1440x900) and made the gui visible. The only problem is that it also disabled the restricted nvidia drivers, which are necessary for that cool paper airplane thing compiz does, and also probably necessary to run starcraft (or games in general.) Enabling the restricted nvidia drivers brings me back to the same problem, after restarting, the computer will not display anything, the monitor displays an "analog out of range" error message, and the only way to get back to the GUI is to run "fix x server" from the debug kernel. 


To recap:
1. magic happened, and the screen resolution got changed to one that my monitor cannot display (and It's the only monitor I have.)

2. This can be fixed by choosing the "fix x server" option from the debug kernel, started from the grub menu (press esc during boot).

3. This fix disables the restricted video drivers, which I would prefer to keep enabled

4. enabling the restricted drivers brings us back to point 1.


Am I right in assuming that the restricted nvidia drivers are dictating a screen resolution to the OS when said drivers are enabled? If so, how can I hack in and dictate a reasonable resolution to the nvidia drivers?

---

### Post by SonnHalter on 2008-12-30
try another kernel

---

### Post by Miles_Prower on 2008-12-30
I'll try that as soon as the starcraft disc images finish copying from my fileserver. Nice sig, btw. I can't help but to think that vista was a paid open-beta of windows 7....

---

### Post by SonnHalter on 2008-12-30
.............tousche'

---

### Post by stderr on 2008-12-30
You've probably already tried these hints or they disable your nvidia driver anyway, but I'll list them anyway in case:

If there are resolutions in your /etc/X11/xorg.conf, you could edit those.

Failing that, you could give this a go (it should ask you a series of configuration questions; hopefully they will involve a resolution question):

```
dpkg-reconfigure xserver-xorg
```

Although they probably won't help. 

You could also try **purging** the restricted nvidia drivers (removing config files too) e.g. 

```
sudo apt-get purge nvidia-glx*
```

(I think that would do it... currently running with ATi so can't verify). Then re-install them, and hopefully no config remnants remain...

Failing all that, I'd try downloading an NVIDIA driver directly from their website, compiling if necessary, and installing - although this really isn't ideal. It won't get updated automatically, etc.

---

### Post by Miles_Prower on 2008-12-31
no good. some crappy resolution is stuck way down in there. s&%* . um... eh.... well.... i guess i can just back up all my porn and reinstall the OS. For future users, though, is there a way for ubuntu to know what resolutions the connected monitor is capable of and offer resolution options accordingly? I feel like I got screwed (pretty hard) here because the OS offered resolution options not supported by the monitor, and would like to prevent other people from encountering the same s*&% if possible.

(please pardon the language (and grammar, probably). I don't like OS reinstalls, they feel like failure.)

---

### Post by SonnHalter on 2008-12-31
well did you try the kernel thing? 

I used to have messed up resolution on my monitor until i found out i had a vga port on my monitor (i was usin dvi) and now my screen is perfect.

---

### Post by Miles_Prower on 2008-12-31
I tried all the available kernels in the grub menu, no good. is there another, more dependable kernel that I could try? I can get a list of the four kernels I have availble (two of them are debug variants of the other two) if you'd like.

---

### Post by SonnHalter on 2008-12-31
no thats fine....do you have another display connection you could try? vga?

---

### Post by Miles_Prower on 2008-12-31
I've got nothing *but* vga. I'm trying to mess around with this [http://ubuntuforums.org/showthread.php?p=1541970](http://ubuntuforums.org/showthread.php?p=1541970) but it seems like that edits the resolution of everything except the gui.

---

### Post by Miles_Prower on 2008-12-31
nope. pure failure everywhere i turn. it's really hard not to just abandon all pretenses of being level-headed and rant and rave about how this os reinstall could have been prevented if... w/e. I can't implement OS changes. I'll keep to myself. Thanks for all your help, guys.

---

### Post by Miles_Prower on 2008-12-31
but wait, there's hope yet!

after getting frustrated and running all the terminal commands in my recent memory that i thought might be destructive to x or compiz and booting to every kernel I had, I managed to get everything working relatively smoothly. The GUI loads well now, and compiz is enabled. The only problem is that the when the computer tries to load the default kernel: 8.10 kernel 2.6.27-9-generic , an error is returned : grub error 15, file not found. Dunno which file, but w/e. booting from 2.6.27-7 works just fine, and compiz is enabled. can I just reinstall grub without disturbing the fragile, fragile remains of my ubuntu?

---

### Post by Miles_Prower on 2008-12-31
yes! the system is back to normal. All i had to do to specify the default kernel was edit the /boot/grub/boot.lst file and put the preferred kernel on top of the list. So, to recap:

1. magic happened, and the ubuntu was set to a screen resolution that my monitor was not capable of supporting

2. I booted to the recovery kernel (included with every install) and chose "xfix" from the list of actions the kernel gave me.

3. I opened synaptic and uninstalled everything that said "compiz" in the title.

4 I purged the system of the proprietary graphics drivers:
```
sudo apt-get purge nvidia-glx*
```

5 after rebooting, I found that one of the kernels in the grub list will not boot (error 15, file not found), so I now boot to an older kernel. I've edited the grub list as described at the top of the post to make the functional kernel the default one.



My baby... she's hurt, but I'm glad she's alive

---

### Post by stderr on 2008-12-31
> **Miles_Prower said:**
> My baby... she's hurt, but I'm glad she's alive

I was just about to suggest posting the output of xrandr, but looks like you've managed to sort it out.

I find a good **purge** often helps ;)

---

