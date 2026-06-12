---
title: "Ubuntu freezes at the blank and orange splash screen"
date: 2009-02-27
forum: General Help
---

### Post by lemurh on 2009-02-27
Hi, new to Ubuntu and am very interested in getting it running properly. I have it installed on my hard drive along with Windows XP Home Service Pack 3. But, when I boot into Ubuntu, it takes me to the Ubuntu splash screen with the orange loading bar. It will load for no more than a minute, and then it will just freeze, forcing a restart. If any information is needed, I will supply it.

Typo in the thread title, meant black.

---

### Post by Peter09 on 2009-02-27
Are you dual booting or using WUBI?

---

### Post by lemurh on 2009-02-27
Correction; WUBI. (If you're talking about the Ubuntu Installer, which I believe you are.) Sorry, New to these terms.

---

### Post by Peter09 on 2009-02-27
Having read your post again I suspect you are dual booting.

There are a couple of things to try. First, immediately you see the grub prompt hit the escape key. Using the down arrows select recovery mode and hit enter. When the menu arrives select fix the x server and see what happens from there.

---

### Post by Peter09 on 2009-02-27
Not sure the above will apply when using WUBI as I have never tried it.

---

### Post by Peter09 on 2009-02-27
Note using WUBI means that you boot Ubuntu from inside XP, rather than at normal boot time.

---

### Post by lemurh on 2009-02-27
Well maybe this will clear up my ignorance, I boot up Ubuntu during normal boot time. So I take it I AM dual-booting.

---

### Post by Peter09 on 2009-02-27
Yes, thats right so you should be able to do what I suggested above.

If that does not work do the same again, but do not move down the Grub Menu.

Press the e (for edit) key and you will see the boot command lines. Remove the references in the first line to splash and quiet (arrow keys to move, delete key to delete). Press B to boot and watch what happens.

This is a temporary thing and all will be normal on your next boot.

---

### Post by lemurh on 2009-02-27
I can't find a single thing in relation to splash and quiet, I'm afraid. So it might help by telling you how I go through this.

System boots up, I'm prompted to select between XP and Ubuntu. Then  message appears saying "Press Esc to enter menu" and if I don't after a few seconds, it takes me directly to the splash screen which results in imminent lock-up. After I press Esc, I'm taken to the GRUB menu, and nothing in here gives me what you suggest. I may need some more detailed directions as I am very, very new to Unbuntu.

---

### Post by Peter09 on 2009-02-27
OK, leave the top option on the GRub Screen selected and press the **e** (for edit) key. This should then show a few lines which are your boot parameters. Quiet and Splash are in the top line near the end.

---

### Post by jwbrase on 2009-02-27
> **Peter09 said:**
> Note using WUBI means that you boot Ubuntu from inside XP, rather than at normal boot time.

No it doesn't. I installed my copy of Ubuntu via Wubi and then migrated.

Wubi *installs* from within Windows and sets up a virtual hard disk within Window's NTFS partition. But it is a full dual boot and loads at boot time. It is not an emulated or virtualized copy of Ubuntu within Windows.

With regards to doing anything when Grub comes up: As I recall, when I did my install, the Windows side of the installer ran, then told me to reboot when it was done. I rebooted and got a grub menu. Then the Ubuntu side of the installer finished the installation. After that, I never saw the Grub menu again on startup until I installed startup manager (the choice between Windows and Ubuntu was set up in boot.ini rather than Grub). So my guess is that after the first boot during the install, the installer sets the timeout for the grub menu to zero, which means the menu doesn't display. If lemurh got it to boot the first time during the install, but has subsequently had problems, he might not really be seeing anything of Grub.

@lemurh: If you ran the installer from within Windows you're using Wubi. In that case the first thing to try is going back into Windows and running the uninstall program, and then trying to install it again. If it works, probably something happened during the first install that messed something up. If it doesn't, you have a more serious problem. Also, did you get it to boot at first, and for some reason it's not working anymore, or did it freeze the first time you tried to boot it (immediately after the Windows side of the installer told you to reboot)?

---

### Post by Peter09 on 2009-02-27
jwbrase, thanks for the clarification - I've never used WUBI so I didn't realise that there was no XP interaction after install.

---

### Post by jwbrase on 2009-02-27
> **lemurh said:**
> I can't find a single thing in relation to splash and quiet, I'm afraid. So it might help by telling you how I go through this.

System boots up, I'm prompted to select between XP and Ubuntu. Then  message appears saying "Press Esc to enter menu" and if I don't after a few seconds, it takes me directly to the splash screen which results in imminent lock-up. After I press Esc, I'm taken to the GRUB menu, and nothing in here gives me what you suggest. I may need some more detailed directions as I am very, very new to Unbuntu.

OK, so you are getting Grub. I was thinking you might not. (Actually, thinking back, I think I did get the "Press Esc to enter menu" message with my Wubi install. That's probably why I didn't see the grub menu itself.)

---

### Post by lemurh on 2009-02-27
jwbrase - No, I have not gotten it to load successfully at all. Reinstalling it now.

---

### Post by lemurh on 2009-02-27
By the way, I did manage to find splash and quiet and did as suggested. The screen loaded with a ton of commands which seemed normal until it denied something like sh/bin 255 or whatever, fuzz memory. If I recreate this, I'll write those few lines down.

---

### Post by lemurh on 2009-02-27
Segmentation Fault
/etc/init.d/rc: 372: sh: Permission denied
inti: unable to execute "/bin/sh" for rc-default
init: rc-default main process (5347) Termination status 255

I'm no genius, but it sounds like it's trying to access a certain directory it can't find.

---

### Post by Peter09 on 2009-02-27
I think this suggests that the install process failed somewhere along the line. As you have no real data in Ubuntu I would try to install again. If you are using a CD make a new one and burn it at as slow a rate as you can to make sure its valid.

---

### Post by lemurh on 2009-02-27
Yes sir, doing so now.

---

### Post by lemurh on 2009-02-27
Windows based UBuntu Installer has encountered a problem and needs to close.  We are sorry for the inconvenience.

When attempting to install via new CD, just my luck, eh? Going for another disc attempt.

---

### Post by lemurh on 2009-02-27
Come to the conclusion that my download of Ubuntu may be bad/incomplete. Will work on it more tomorrow.

---

### Post by lemurh on 2009-02-27
Ok, downloaded from a different ubuntu mirror, wrote the .iso to DVD using ISO Recorder V3, and wrote it at the lowest possible speed. Installing now.

Update - WUBI hasn't crashed on me like the two attempts before this one.

---

### Post by lemurh on 2009-02-27
Freezes at splash screen, again.

---

### Post by lemurh on 2009-02-27
Tried booting and installing from the CD drive, disk integrity showed no errors. Then I attempted to install. Went to the splash screen and it froze at the same exact spot. Am I just not meant for this?... :(

---

### Post by lemurh on 2009-02-27
If anyone can suggest a solution, I'll be here.

---

### Post by cmosguy on 2009-04-30
I'm having the same problem.  Of course, it could be for a different reason.

I tried not using Wubi, taking the step to a full installation.  This time, it froze with a black screen and a cursor.

8.04 had installed with no problems, so I went back to that.  I'll try upgrading to 9.04 via the package manager, maybe that will help.

---

