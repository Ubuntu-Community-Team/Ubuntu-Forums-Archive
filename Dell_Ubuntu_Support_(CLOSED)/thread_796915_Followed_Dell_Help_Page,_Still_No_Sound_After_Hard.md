---
title: "Followed Dell Help Page, Still No Sound After Hardy Upgrade"
date: 2008-05-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Unstuck on 2008-05-16
I just installed Hardy on my friend's Dell Inspiron 1420n, and like many, was sad to find out the laptop was left without sound or wifi.  I followed the Dell [**instructions**]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade") to correct the sound problem, but things went wrong after entering the fourth command: it could not find the file I asked it to remove.  I called Dell afterwards and was told that I would have to back up the home directory and restore factory settings...that was right before they told me they don't really know anything about the OS.  

Is there a better solution than the one they offered?

---

### Post by cheetaux on 2008-05-17
Did you did a fresh install or an upgrade.  I did a fresh install of Hardy on my 1420n (with the Intel 3100 vido card) and have had absolutely no problem.  The sound worked OK from the beginning.

---

### Post by hagmist on 2008-05-17
> **Unstuck said:**
> I just installed Hardy on my friend's Dell Inspiron 1420n, and like many, was sad to find out the laptop was left without sound or wifi.  I followed the Dell [**instructions**]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade") to correct the sound problem, but things went wrong after entering the fourth command: it could not find the file I asked it to remove.  I called Dell afterwards and was told that I would have to back up the home directory and restore factory settings...that was right before they told me they don't really know anything about the OS.  

Is there a better solution than the one they offered?

I followed the instructions from your link above and they worked for me .... after I had undone my previous fixes and then reboot and then changed devices back and forth. Not sure the reboot helped but the changing devices seemed to trigger something.... Anyway works fine now.

The volume control stated working after the instructions -> but no sound -> right click on volume control -> open sound control -> file -> change device. After 1 change it worked (softly) -> changed back to choice 0 (ALSA) and it worked fine from then on.
g.

---

### Post by Unstuck on 2008-05-20
This is the output when I try to enter the third set of commands
> xxx@dell:/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda$ sudo mv snd-hda-intel.ko.REPLACEDBYhsfmodem snd-hda-intel.ko
mv: cannot stat `snd-hda-intel.ko.REPLACEDBYhsfmodem': No such file or directory


I'm not sure where to go from here so I can fix this...

---

### Post by notwen on 2008-05-20
Try using the find or locate commands in a term to see if this file is even present on your friend's machine.

```
locate snd-hda-intel.ko.REPLACEDBYhsfmodem
```

```
find snd-hda-intel.ko.REPLACEDBYhsfmodem
```

---

### Post by Unstuck on 2008-05-20
Thanks, notwen.

It seems that the file is only located in 2.6.20 kernel.

> xxx@dell:~$ locate snd-hda-intel.ko.REPLACEDBYhsfmodem
/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko.REPLACEDBYhsfmodem


---

### Post by notwen on 2008-05-20
Np, were you able to get your sound back?

---

### Post by Unstuck on 2008-05-20
I'm not sure what to do next.  It made sense to me...because I'm an ignorant noob...to substitute the location of the file in the kernel where the file was found, but that didn't seem to work
> @dell:~$ cd /lib/modules/2.6.20-16-generic/ubuntu/sound/alsa-driver/pci/hda
bash: cd: /lib/modules/2.6.20-16-generic/ubuntu/sound/alsa-driver/pci/hda: No such file or directory


---

### Post by notwen on 2008-05-20
If you're going by the page you linked in your initial post, just copy and paste each command into a terminal, one command at a time.  Try not to copy and paste multiple commands; the step you're hung up on should be entered like so:

```
cd /lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda
```

then

```
sudo mv snd-hda-intel.ko.REPLACEDBYhsfmodem snd-hda-intel.ko
```

Then proceed with the rest of the commands.  Post back if you're still having issues and I'll do my best to get your sound back up & running.  =]

---

### Post by Unstuck on 2008-05-20
I can change directories without a problem, but moving the file seems to be the issue.  I copied and pasted the command you provided and got the following reply
> mv: cannot stat `snd-hda-intel.ko.REPLACEDBYhsfmodem': No such file or directory


---

### Post by notwen on 2008-05-21
Since you said earlier you're still using an older kernel, let's try checking the directory you found the file using find.

```
cd /lib/modules/2.6.20-16-generic/kernel/sound/pci/hda
```

Just curious, have you updated this machine after installing Hardy?  I don't see how an older kernel is installed w/ Hardy.  Hardy installs kernel 2.6.24-16.30 by default.  =\

---

### Post by Unstuck on 2008-05-21
I'm fairly certain I have updated since upgrading to Hardy.  I don't know why the older kernel is hanging around.

Here are the results from the most recent code you posted:
> $ cd /lib/modules/2.6.20-16-generic/kernel/sound/pci/hda
xxx@dell:/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda$ sudo mv snd-hda-intel.ko.REPLACEDBYhsfmodem snd-hda-intel.ko
xxx@dell:/lib/modules/2.6.20-16-generic/updates$ sudo rm snd-hda-intel.ko
rm: cannot remove `snd-hda-intel.ko': No such file or directory


---

### Post by notwen on 2008-05-22
Do you view GRUB when starting your machine?  You can boot the different kernels available and I'm wondering if GRUB did not pick up the new kernel or if it's just defaulting to your old one?  Another option would be to search synaptic for "linux image".  The results should let you know which kernels are currently installed on your system.  You're obviously wanting the newer one that is involved w/ this sound fix.

---

### Post by Unstuck on 2008-05-22
I don't usually look at GRUB before the computer fully boots, but your suggestion made me think I should.  Kernel 2.6.24-16.30 isn't listed in GRUB, but it is listed in Synaptic as an installed "linux image".

---

### Post by monomakh on 2008-05-26
The Dell instructions aren't working since the new kernel is -17 instead of -16.  Replace the path in the instructions with the newer kernel and everything works again.

---

### Post by Unstuck on 2008-05-26
I did a clean reinstall and problems disappeared.  

Thank you to everyone who offered advice.

---

