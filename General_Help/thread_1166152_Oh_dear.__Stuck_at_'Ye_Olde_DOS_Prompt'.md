---
title: "Oh dear.  Stuck at 'Ye Olde DOS Prompt'"
date: 2009-05-21
forum: General Help
---

### Post by nogoodreason on 2009-05-21
Hmm.  I've been following [this guide]("http://www.ubuntugeek.com/dual-monitors-with-nvidia.html") to set up dual-monitors on Ubuntu.    I did everything the instructions said, but wasn't sure whether I was successfully 'reloading X' as nothing seemed to happen when I pressed ctrl+alt+backspace.

I rebooted to see if the configuration had worked, and I've obviously killed the X thing completely as it will now only boot into a DOS/Terminal prompt.  What on earth should I type??

And can anyone offer me some more indepth advice about how to set up dual monitors?  As that approach clearly didn't work. :(

---

### Post by baseface on 2009-05-21
do you know what dos is?

---

### Post by clhsharky on 2009-05-21
What video card do you have

---

### Post by spcwingo on 2009-05-21
Try this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

followed by:

```
sudo /etc/init.d/gdm restart
```

That should at least get X back.

---

### Post by nogoodreason on 2009-05-21
> **baseface said:**
> do you know what dos is?

Well, okay... the thing that looks like DOS. :p  i.e. a slight shortage of cursors and windows.

I have an Nvidia 8800GTS 512mb.

Will try those commands now and report back - hopefully from within Ubuntu.

---

### Post by nogoodreason on 2009-05-21
> **spcwingo said:**
> Try this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

followed by:

```
sudo /etc/init.d/gdm restart
```

That should at least get X back.

No luck, I'm afraid. :(

The first command brought up the message "**/usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed**"

The second command seemed to work, but wasn't able to bring back Ubuntu.

---

### Post by spcwingo on 2009-05-21
Try:

```
sudo apt-get install --reinstall xserver-xorg
```

followed by:

```
sudo reboot
```

Let us know if that gets it sorted.

---

### Post by nogoodreason on 2009-05-21
spcwingo:

That command definitely installed something, but even after the reboot it brings me to the same old 'DOS prompt' thing. :(

It it worth mentioning that I changed the timer on GRUB bootloader to 0 seconds?  I'm just wondering if it's behaving like Windows and hovering over a 'boot in safe mode' equivalent, but the boot screen's disappearing before I have a chance to move it back to the normal selection.

---

### Post by spcwingo on 2009-05-21
:-k  Hmmm...try rebooting and while it's doing that constantly press esc at the grub screen.  If it lets you in select "recovery mode" and boot it.  When it finishes booting you will be at a screen that should give the option to fix x, among other things.  Select fix x and when it's done select continue normal boot.  If that doesn't get you to your desktop the only other thing that I can think of to try is:

```
sudo apt-get install --reinstall ubuntu-desktop
```

But, try "recovery mode" first to see if that works...if not, then try the above listed command.  If neither one fixes it, I am at a loss as what to try next.  Let us know either way.

---

### Post by bacardiandwatermelon on 2009-05-21
```
sudo apt-get install dontzap
sudo dontzap --disable
```Restart and then Ctrl+Alt+Backspace will work again

---

### Post by nogoodreason on 2009-05-21
Grrrrrrrrrr

The reinstall Ubuntu-desktop command worked, but it's still booting into this 'DOS screen'.  :S :S :S :S :S

This is making me think that, rather than doing anything drastic, I may just need to find a command line access GRUB or something.

I tried the only one I know (**gksudo gedit /boot/grub/menu.lst**) but it said it couldn't display the list.  But surely there must be others...

---

### Post by spcwingo on 2009-05-21
To edit the menu.lst from the terminal enter:

```
sudo nano /boot/grub/menu.lst
```

Change whatever you need to change and it's "CTRL + O"(that's a capital "O") to save then "CTRL + X" to exit.

---

### Post by nogoodreason on 2009-05-21
spcwingo:

All your suggestions have worked perfectly.  I got into Grub's equivalent of 'safe mode', repaired X, made sure everything was hunky dory, saved successfully and reboot.


And IT'S STILL IN DOS MODE!!!!!!!!!!!! :'(


Am I just destined to use Windows for the rest of my life? :(

---

### Post by spcwingo on 2009-05-21
Of course not.  I had a couple of machines that gave me problems.  Well, back to the matter at hand.  What release are you using?

```
lsb_release -a
```

Paste the output here.  The reason I ask is Hardy (8.04, the release I'm on) is much more stable and uses a different version of xserver than the later releases.  If you want, you could give Hardy a shot if we can't get this thing sorted.

---

### Post by nogoodreason on 2009-05-21
> **spcwingo said:**
> Of course not.  I had a couple of machines that gave me problems.  Well, back to the matter at hand.  What release are you using?

```
lsb_release -a
```

Paste the output here.  The reason I ask is Hardy (8.04, the release I'm on) is much more stable and uses a different version of xserver than the later releases.  If you want, you could give Hardy a shot if we can't get this thing sorted.

I can tell you for a fact it's the latest - Jaunty.

Erg.  I may wait a couple of days before attempting a new OS install - it took me enough attempts to get this dual-boot working with easyBCD. ;)  But I will definitely keep that in mind.  (Wouldn't the auto-updater try and automatically update me to Jaunty as soon as I got online, though?)

---

### Post by spcwingo on 2009-05-21
> **nogoodreason said:**
> Wouldn't the auto-updater try and automatically update me to Jaunty as soon as I got online, though?

No, because by default on LTS (Long Term Support) releases like Hardy, auto update defaults to only update to other LTS releases.

---

### Post by googlegot on 2009-05-21
What video card are you using?

This is what I use when X just doesnt like me:

sudo apt-get remove ubuntu-desktop

followed by 

sudo apt-get autoremove

followed by

sudo apt-get install ubuntu-desktop

followed by

sudo apt-get -f install

the --reinstall command never did any good for me to be honest.

---

### Post by nogoodreason on 2009-05-21
I'm using an Nvidia 8800GTS 512mb.  The driver itself seemed okay; it was only when I started playing around (see link in my OP) to get dual monitors that this problem happened.

---

### Post by googlegot on 2009-05-21
did you try what I had posted previously?

If you were playing around with dual moniters, you could try restoring a backed up xorg.conf.

Type

ls /etc/X11/

And tell me what the output of this command is

---

### Post by nogoodreason on 2009-05-21
> **googlegot said:**
> ls /etc/X11/

And tell me what the output of this command is


Tried what you said in your first post, but still getting this evil "DOS" screen.

View my attachment to see the output from the command.

Possible thing: When this "DOS" thingy loads up, next to my username and station name it says **tty1**.  I've no idea what tty1 is or whether it has any significance.

---

### Post by asmoore82 on 2009-05-21
I would say try to start up with no xorg config file at all and see if it "Just Works" again ...

Rename your existing xorg config to a backup location:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.$(date +%F)
```

Then, restart:
```
sudo reboot
```

---

### Post by asmoore82 on 2009-05-22
The slight hostility you may have sensed from other replies is because Linux, in general,
and especially in its Command Line interface, attempts to stay as true as possible to its UNIX roots.

UNIX version 1, released in 1971, easily predates the development of CP/M in 1973.
DOS was based entirely on CP/M and didn't exist in any form until 1980.
Readily admitting its roots as a cheaper rewrite of CP/M,
DOS actually stands for "Dirty Operating System" - [http://en.wikipedia.org/wiki/86-DOS](http://en.wikipedia.org/wiki/86-DOS)

No one among us who stops and takes a breath first will blame You for it,
But it is a darn shame that UNIX based code is everywhere all around us everday
(Linux, DVR's, HD-DVD/BluRay Players, PlayStation 3's, Mac OS X, Android, iPhones);
However, when the vast majority of folks come face to face with the true visage
of these mythical and legendary OS design principles, all they can see is "DOS."

----------------
It says a lot about what forces have been driving the computing industry for far too long.
Gary Kildall designed and built CP/M; Tim Patterson wrote QDOS which Micro$oft would later buy
and build up as MS-DOS. CP/M and MS-DOS actually "competed" directly to be the OS for IBM PC's;
and the rest, as they say, is History. How was Gary Kildall to compete with *his very own* OS design
turned against him at a cut-rate price? I'm pretty sure if the original OS designer had gotten
to play a more active role in the course of PC history it would be quite a different world today.

This is often spun as Gary Kildall not being a great businessman. He went on, by the way,
to die a multi-millionaire even after having the PC OS Industry stolen out from under him.
Some have went so far as to say that Gary just wasn't enough of a visionary to truly understand
the revolution he had started. This is just romantic and shameful nonsense!

Gary knew exactly how explosively the PC Industry would grow,
but early on he had made a decision of great and humble conscience: he once asserted that
no company should ever "compete" in both the Operating System and Applications space
at the same time; the temptation to abuse this position would be far too great.

Oh man!! how right was he?? As you can see, He was quite a visionary indeed.
The proof of this non-mainstream and true history of Gary Kildall is here:
[http://www.archive.org/details/GaryKild](http://www.archive.org/details/GaryKild)
----------------

Sorry, I had to write all of this out for posterity, but
I definitely didn't want to mix it in with my attempt at a "helpful" post :lol:.

---

### Post by Yellow Pasque on 2009-05-22
If you're stuck at a DOS prompt:
```

C:\DOS
C:\DOS\RUN
RUN\DOS\RUN
```

---

### Post by nogoodreason on 2009-05-22
Heheh.  Thanks for the lesson. :)

So what term should I use when describing the 'black and white screen with a command line' that's currently appearing instead of my GUI operating system?

---

### Post by bacardiandwatermelon on 2009-05-22
tty1 etc are actually called virtual consoles.. I think :-D

---

### Post by Fzang on 2009-05-22
I'd call it CLI (command line interface)

---

### Post by Kareeser on 2009-05-22
**What is everyone even DOING?!**

First of all, ubuntu-desktop is a meta-package. Uninstalling, purging, and reinstalling the package won't do a thing because it's just a set of programs and helper applications on top of the linux kernel!

Nobody here has asked *SPECIFICALLY* what steps or guide the OP took to try and get dual monitors.

So I'll start.

**nogoodreason**, please provide us with the exact steps you took way back in the beginning to try and get dual-monitors. Once we know that, we can take the appropriate steps to reverse what you did, to get you back to where you were at the beginning.

After that, I'd advise you [install the nvidia drivers directly from the nvidia website](http://ubuntu.kareeser.com/?p=44).

---

### Post by nogoodreason on 2009-05-22
> **asmoore82 said:**
> I would say try to start up with no xorg config file at all and see if it "Just Works" again ...

Rename your existing xorg config to a backup location:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.$(date +%F)
```

Then, restart:
```
sudo reboot
```

Result: Cannot stat '/etc/X11/xorg.conf': no such file or directory

---

### Post by nogoodreason on 2009-05-22
> **Kareeser said:**
> **What is everyone even DOING?!**

First of all, ubuntu-desktop is a meta-package. Uninstalling, purging, and reinstalling the package won't do a thing because it's just a set of programs and helper applications on top of the linux kernel!

Nobody here has asked *SPECIFICALLY* what steps or guide the OP took to try and get dual monitors.

So I'll start.

**nogoodreason**, please provide us with the exact steps you took way back in the beginning to try and get dual-monitors. Once we know that, we can take the appropriate steps to reverse what you did, to get you back to where you were at the beginning.

After that, I'd advise you [install the nvidia drivers directly from the nvidia website](http://ubuntu.kareeser.com/?p=44).

Thanks for the post, Kareeser.

I'm new to Ubuntu and couldn't figure out how to get the drivers from nvidia.com installed, but was told that going to Synaptics Package Manager and searching for Nvidia would yield the same result.  I found the corresponding drivers, installed, and then followed this guide: [http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html)

When I rebooted I got an "Ubuntu is running in safe graphics mode" warning and some message about (sorry for the complete vagueness) it moving the xserver from 0 to 1 because it couldn't find it?

Anyway, I figured this clearly hadn't worked so I went back to Synaptics Package Manager and unchecked all the nvidia things, so that it would uninstall all the drivers.  I rebooted, opened Synaptics and installed some slightly different drivers (there were a few variations available) and tried the guide again to see if I'd have more luck.

After rebooting, I got to this command screen and haven't been able to get out of it since.

---

### Post by quinnten83 on 2009-05-22
If this were to actually work, I would pee my pants laughing.
Try pressing ctrl-alt-F8 or is it F7?
you might be in the wrong virtual terminal.
Althoug I think you would be starting up in the right one after rebooting.
I don't have an nvidia card and I shy away from playing with my X-server, so I am not of much help....

---

### Post by NCLI on 2009-05-22
> **nogoodreason said:**
> Thanks for the post, Kareeser.

I'm new to Ubuntu and couldn't figure out how to get the drivers from nvidia.com installed, but was told that going to Synaptics Package Manager and searching for Nvidia would yield the same result.  I found the corresponding drivers, installed, and then followed this guide: [http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html)

When I rebooted I got an "Ubuntu is running in safe graphics mode" warning and some message about (sorry for the complete vagueness) it moving the xserver from 0 to 1 because it couldn't find it?

Anyway, I figured this clearly hadn't worked so I went back to Synaptics Package Manager and unchecked all the nvidia things, so that it would uninstall all the drivers.  I rebooted, opened Synaptics and installed some slightly different drivers (there were a few variations available) and tried the guide again to see if I'd have more luck.

After rebooting, I got to this command screen and haven't been able to get out of it since.

Sounds like you installed some incompatible drivers. You should always use the ones found in "System/Administration/Hardware Drivers" ;)

---

### Post by Kareeser on 2009-05-22
NCLI's post hit the mark. nvidia-glx is most likely incompatible with your graphics card. The blog post was from 2007, so it's quite old, and to be honest, I've never heard of the package "nvidia-glx" before.

Can you follow the instructions listed on the website I posted? I've laid out the exact procedure to get the new drivers installed.

You can skip the command "sudo /etc/init.d/gdm stop", since you don't have any graphical overlay.

---

### Post by nogoodreason on 2009-05-22
Thanks Kareeser, that link to the blog was really helpful.

I managed to install the latest nvidia drivers from the terminal, although I'm still not booting into a GUI. :(

I'll have a crack at trying the console command to UNinstall the drivers, and then will reboot and reinstall them again in case that makes any difference.

I'll also try Ctrl+Alt+Fkey just incase that solves it. ;)

---

