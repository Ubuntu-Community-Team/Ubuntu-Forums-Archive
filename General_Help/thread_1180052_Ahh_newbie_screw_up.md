---
title: "Ahh newbie screw up"
date: 2009-06-06
forum: General Help
---

### Post by cougs_83 on 2009-06-06
So My who issue started with installing A ATI radeon 4650.  The hardware driver was detected downloaded and installed fine.  

The only problem was that I had hooked my system up to my 1080P 42" LCD and 9.04 was still detecting the old monitor.  (an old philips crt) So I could not set a very high resolution.

I jumped on the forum and started doing some research and someone talked about going to grub then recovery mode then redetecting the hardware.  

Well that is where everything really got screwed up.  I didn't notice a redetect hardware menu.  But I did see the xfix which is what I assumed he was talking about.  

I ran xfix and now as soon as Ubuntu loads I get a couple of weird lines or color splotches on the screen and its locked up.  I installed the old CRT through the second DVI to see if it is an issue with the HDTV.  But both monitors display the same thing.  

Someone please help!  is there anything I can do?  Please remember I am a complete novice.  I can still access GRUB but I wouldn't have any idea of how to go about fixing the xconfig or whatever it is that controls the video

---

### Post by cougs_83 on 2009-06-06
Also when I run the fix broken packages option is says that following maybe this will mean something to someone.

rm: cannot remove `/var/lib/apt/lists/partial/*': No such file or directory

rm: cannot remove `/var/cache/apt/archives/partial/*': No such file or directory


Then is says that 6 packages are going to be upgrades.  When I type yN to continue it runs, but says that everything failed.

---

### Post by blueridgedog on 2009-06-06
Boot the system normally, then give it time to come all the way up.  

Press Ctrl+Alt+F2 to get to a command prompt and log in using your normal account.

Then enter:
```

	sudo /etc/init.d/gdm stop
	sudo dpkg-reconfigure xserver-xorg
	sudo /etc/init.d/gdm start
```

This should be with the big monitor only connected and on.

---

### Post by cougs_83 on 2009-06-06
So I have only my LCD TV hooked up.  Ran a regular boot.  As soon as the bar scrolls all the way saying that Ubuntu is loading it goes to a screen that looks as though it just has a static line wait a full 2 minutes to make sure that it would have had time to fully load.  But when I type the command I don't see a command line come up.  Nothing changes at all.  It looks like I can bring up a command line in recovery mode.  Can I use the commands there?

Thanks for the help.  This will teach me to screw with things.

---

### Post by cougs_83 on 2009-06-06
Also I should mention that it makes no difference whether I use the onboard video or the video card.  All images are fine until Ubuntu is loaded then nothing but a little static on the screen.

---

### Post by blueridgedog on 2009-06-06
Do you get the boot sound?

Disable the onboard card in the Bios...

---

### Post by cougs_83 on 2009-06-06
I went in and made sure that the port was set to PCIE.  It looks as though I can disable every onboard device besides the video.  I must have other issues besides the video though because if the caps/num locks are on or off when Ubuntu is loaded I can't change them.  If they are on they stay on.  If they are off they stay off.  Any ideas from here?

---

### Post by cougs_83 on 2009-06-06
I know its a long shot but is there any way to do a reinstall of Ubuntu without wiping the HDD.  That would probably help me out with the OS not detecting the monitor correctly anyway.

---

### Post by blueridgedog on 2009-06-06
If you let it boot, what happens if you press "ctrl + alt + backspace".  This should kill the xserver.

You can do an install without formating, but I bet we can salvage what you have.

---

### Post by cougs_83 on 2009-06-06
Nothing... Keyboard no longer functions as soon as Ubuntu loads All devices seem to work fine.  But as soon as the OS boots, or freezes during the process (although the progress bar shows that it has been fully loaded) every locks up.

---

### Post by blueridgedog on 2009-06-06
OK, let's see what is happening.

At the grub menu screen, press 'e' to get into edit mode, and remove the word "quiet" and change "splash" to "nosplash" on the kernel line.

Then you can see the boot messages scroll by...if it hangs, perhaps we can see why it is getting stuck.

---

### Post by cougs_83 on 2009-06-06
Not positive that I am doing it right.  

E to edit the kernal line at no to splash hit enter.

E to edit remove the word quiet.  

b to boot after these changes have been made.   

Please let me know if I am missing anything.  It doesn't seem like anything changes as the system boots and it ends up in the same place.  

hopefully this link works.  I took this before the changes above this is what is happening on start up after the screen at the end is reached it does not change and everything is locked up.
<embed width="448" height="361" type="application/x-shockwave-flash" wmode="transparent" src="http://i624.photobucket.com/player.swf?file=http://vid624.photobucket.com/albums/tt324/Townandcountrylanes/VID00090.flv">

---

### Post by blueridgedog on 2009-06-06
I saw the film.  

You can try editing the boot line that looks something like:

```
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hde4 ro quiet splash

to be:

kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hde4 ro
```

What we are after is to not have the progress bar, so you can see what is happening.

---

### Post by cougs_83 on 2009-06-07
That got rid of the progress bar.  But the script never hangs up.  It says that everything finishes.  But I am still ending up with the same issue.  This time instead of the greenish status bar I got the MSI motherboard graphic with screwed up colors 4 times in the same bar across the top of the screen.

---

### Post by kn100 on 2009-06-07
correct me if im wrong, but you can boot up in a liveCD correctly, correct?

---

### Post by blueridgedog on 2009-06-07
So, in the text part of the boot, you see no errors, and then it attempts to start x the screen messes up.  You can't do ctrl + ALT + f2 to get to a command prompt and you can't do ctrl + ALT + backspace to kill the server.

Let's see if you can boot to run level 1 (single user, no x windows system) and then we can reconfigure the server.

1. At the graphical boot screen, press e (for edit), scroll down to select the kernel you edited before (might as well remove quite and splash again), and press e again.
2. Press the spacebar, type single or 1, and press Enter.

3. Finally, press b to boot, and you’ll boot into runlevel 1 instead of the default runlevel
listed in /etc/inittab.

IF...that works, they you can log in and try:

```
sudo dpkg-reconfigure xserver-xorg
```

Then reboot and hope that it did something.  You might as well just stick to the CRT for testing at this point.

---

### Post by cougs_83 on 2009-06-07
Level 1 sends me to the grub recovery menu.

---

