---
title: "System beep during boot and azureus"
date: 2005-11-04
forum: Desktop Environments
---

### Post by Antimatter3009 on 2005-11-04
Two entirely unrelated questions.

First of all, I can't find azureus in any of the repositories (I have universe and multiverse in the list). Am I missing something, or does this have to be installed manually?

Second, I'm having some unwanted system beeps. I currently have breezy kubuntu installed on my laptop and ubuntu on my desktop. On both of them when I boot, I get a system beep just before X loads, and also while the system is shutting down. On my desktop this isn't too much of an issue, but on my laptop it's ridculously annoying as I carry it around in public areas and it beeps every time I try to boot it. This has almost singlehandedly forced me to use Windows on my laptop unless I'm at my desk. So my question is, is there any way to stop this from happening besides taking apart my laptop and removing the speakers? Also, my desktop is beeping every time I try to use tab completion for file names in a terminal. This, again, is just really annoying. Can I shut this off easily? Thanks.

Edit: One more issue I forgot to mention. On my desktop I have a nVidia 6600GT video card. I downloaded the nvidia driver package just fine and everything, and it still runs fine as long as I leave the xorg.conf file set to nv. If I change that line to nvidia (like I'm supposed to to use the drivers) I just get a blank screen when I reload X (the light on my monitor goes to orange and everything). However, I can use ctrl+alt+Fx to get to a console and change it back, then restart X and it works fine again. Can anyone help with this? Thanks.

---

### Post by Kyral on 2005-11-04
Azureus depends on SunJava, whose license conflicts with the GPL, so you can't install it from the Repos, thus Azureus isn't in the repos.

As for Beeping...I know what you mean, but since I use my desktop I don't mind it.

And for X....try a sudo dpkg-reconfigure xserver-xorg and pick the NVidia Module manually from the list

---

### Post by poptones on 2005-11-04
My thinkpad has a control key to adjust volume and mute the sound. You press the blue "system control" function key and then press ESC and it mutes sound. I use this  (also because I don't even have it configured for sound as it is a lowly 400MHz system).

Does your laptop not have a BIOS setting or a system function key to mute sound exclusive of operating system software?

---

### Post by Antimatter3009 on 2005-11-04
Thanks for the info on Azureus. As for the system beeps...I have a Dell 600m. While it does have volume control keys, they don't seem to do anything about the system beeps.

---

### Post by Antimatter3009 on 2005-11-04
So I tried the dpkg-reconfigure you suggested and it just ended up breaking everything. After that, I got garbled error messages about things being messed up. Anyways, I replaced the xorg.conf file with the one that was backed up and now I'm back to where I was. Stuck with nv and any change to nvidia causes it to stick...

---

### Post by Antimatter3009 on 2005-11-11
Does anyone have any more ideas? I'm losing hope...

---

### Post by akniss on 2005-11-18
I also have a Dell 600m, and get a double beep when I boot or come back from hibernation just before the gui starts.  Sometimes I can briefly see an error message just before the gui starts and asks me for my password.  I will have to try a few more times to get the whole message, but the end of the message is "error -71".  I don't know if this will shed any light on the problem for you folks who know what you're doing.  (I'm still pretty new to  Linux, and VERY new to ubuntu.)

---

