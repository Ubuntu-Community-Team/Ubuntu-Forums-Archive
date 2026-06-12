---
title: "Suddenly can't launch apps in Xubuntu Xfce?"
date: 2007-04-08
forum: Desktop Environments
---

### Post by SubGothius on 2007-04-08
[I just installed Xubuntu 6.10 Edgy](http://ubuntuforums.org/showthread.php?t=395441), booted up and logged into my new system successfully, immediately installed all available Updates for the OS and initial suite of packages, and then lightly customized some Xfce Panels and basic windowing options to my liking.  Now I can't seem to launch any programs from the Xfce Applications menu panel. Whenever I try, my drive chatters briefly like it's going to do something, but then nothing happens. Only Xfce utilities like the Settings Manager and Process Manager will open from the Panel's Apps menu, and the Process Manager doesn't list any new processes whenever I try to launch an app.  Whaa... :confused:

Also FWIW, after installation, my new Xubuntu boots into a 800x600 resolution that's shrunken and squeezed off the left side of the screen, appearing the same as when I select 800x600 in my other OS (obviously not a well-supported vmode for this monitor+card!), and I can't select anything but 800x600 and 640x480 in the Xfce Display settings panel (even tho' I specified 1024x768 in the Installer as the only valid rez for X), so I think it's defaulting to a generic video driver and resolution instead of the imsttfb driver. I am specifying the kernel argument "video=imsttfb:vmode:17,cmode:32" (also tried substituting "vmode:16", "cmode:24", or adding ",mclk:75" to the end) in my bootloader, to no avail; perhaps this is not the right karg, or maybe I need to edit my xorg.conf ... ([Please respond to this secondary issue in its own dedicated thread - click here](http://ubuntuforums.org/showthread.php?t=404204).)

---

### Post by kerry_s on 2007-04-08
Please do not post more than 1 thread with the exact same thing.

---

### Post by SubGothius on 2007-04-08
My apologies if I offended forum sensibilities.  I just wanted to avoid perpetrating the dreaded "thread about everything" and its cousin, the "thread in the wrong category", so I only intended to branch two unrelated tangents off my original installation-problem thread, by posting two different threads in two different categories appropriate to each distinct post-install issue, and as an afterthought decided to add cross-links between those two issues/threads.  Sorry if it looked like I was posting the same thing twice; that was not my intent, tho' I admit it kinda turned out looking that way.

Back to the primary intended subject of *this* thread, FWIW I have already tried rebooting (both hard and soft), and tried logging into a brand-new Xfce Session, neither of which helped matters any.  It seems as if, somehow, perhaps the Application menu icons no longer point to their actual applications, so clicking on them is like a dead link?

Also, some of the various Install/Update apps (Synaptic, Update, Add/Remove) seem to at least open their window and start trying to synch up the system state vs. d/l repositories, but then spontaneously quit before showing any sign of actually making progress (e.g. finding any packages to update or getting a list of pkgs to remove/install).

---

### Post by kerry_s on 2007-04-08
what about if you press alt+F2 does that bring up the run dialog?

if it does type> xterm
then
mv ~/.config ~/##.config  <- this is to reset all your settings to bone stock
rm -rf ~/.cache <- deletes cache
then
ctrl + alt + backspace <- this will restart X

If it's still screwed up after returning everything back to stock, i would say your install is borked.

---

### Post by RedSquirrel on 2007-04-08
> **kerry_s said:**
> what about if you press alt+F2 does that bring up the run dialog?

if it does type> xterm
then
[COLOR=Red] mv -rf ~/.config ~/##.config [/COLOR] <- this is to reset all your settings to bone stock
rm -rf ~/.cache <- deletes cache
then
ctrl + alt + backspace <- this will restart X


Minor correction:

"r" (recursive) in not an option for the mv (move) command.

```
 mv ~/.config ~/##.config
```[COLOR=Black]would do the trick.
[/COLOR]

---

### Post by kerry_s on 2007-04-08
> **RedSquirrel said:**
> Minor correction:

"r" (recursive) in not an option for the mv (move) command.

```
 mv ~/.config ~/##.config
```[COLOR=Black]would do the trick.
[/COLOR]


Sorry, i was ready to hit the sack. I first had "rm", but changed it to "mv" just in case he might need to put it back. Thanks for the correction.

---

### Post by kerry_s on 2007-04-08
Okay, i came across a post about gnome having problems with composite, which got me thinking you might be having the same problem in xubuntu.

Try this:
Press ctrl+alt+F1 this get you to tt1
type> nano /etc/X11/xorg.conf
put this at the bottom->

```
Section "Extensions"
    Option         "Composite" "False"
EndSection

```

Press> ctrl and x and y and enter to save

---

### Post by SubGothius on 2007-04-09
Well, I managed to login to a new Session and was about to run your commands in xterm re: .config and .cache, but on a lark I decided to try loading the Software Update utility again... and it launched!  Strangely, still listing the same 86 or so available updates as last time, so I decided to try reapplying all available updates again.  Updating finished with the following errors:

E: /var/cache/apt/archives/linux-headers-2.6.17-11_2.6.17.1-11.35_powerpc.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/linux-image-2.6.17-10-powerpc_2.6.17.1-10.34_powerpc.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/mozilla-thunderbird_1.5.0.10-0ubuntu0.6.10_powerpc.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/update-manager_0.45.2_all.deb: subprocess new post-removal script returned error exit status 134

Plus in the terminal pane of the update progress dialog (alas, could not copy-paste this output -- is it logged somewhere?), I kept seeing something about it trying to run update-initramfs to rebuild a new initrd.img, which would fail with a "segmentation fault (core dumped)" error, and also how xorg.conf would not be updated due to a possibly-custom xorg.conf (I hadn't messed with it yet), and how Xserver updates would not take effect until all X sessions were ended.

So I did the Ctl-Alt-Backspace to restart X, but it wouldn't restart.  Tried rebooting and only got a terminal login, no X.  Tried renaming my ~/.config and deleting my ~/.cache, still no joy on attempting to "startxfce4".  This is when I ran dpkg-reconfigure xserver-xorg to build a new xorg.conf (see other thread re: video issues), still no worky.

Thinking I might try redoing the updates via aptitude, I ran "aptitude update" and that also quit with a "segmentation fault (core dumped)" error after hitting 53% on the building dependency tree stage.

Is my system now well and truly borked, or can I yet recover from all this?

---

