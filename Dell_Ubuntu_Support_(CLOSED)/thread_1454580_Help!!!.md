---
title: "Help!!!"
date: 2010-04-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Sentoguy on 2010-04-14
Hey folks,

I'm really in a bind and hope that someone can help me out. 

I just got back from vacation, in which time my cousin and two of my friends had access to my almost brand new Dell computer. I have Ubuntu 9.10 installed along side Windows 7 and left directions for them on how to operate it.

However, after several unsuccessful attempts I cannot get my ubuntu kernel to boot. A message keeps coming up when I try to boot the kernel which says 

"Mount of File System Failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
root@keegan-desktop:~#"

I called my cousin and asked him if he had trouble starting up the computer and he said that he didn't know what he was doing and hit some keys (basically trying to exit the screen where you can choose between booting ubuntu or Windows), then some other screens popped up, he hit some buttons, then a message popped up asking if he wanted to save changes and he selected yes! I don't know why on earth he would have done that, but apparently he did.

The problem is that I have no idea what he did, and now I can't even get the computer to run the live CD (which did work before I left), and that's even after I went back to the menu and selected CD rom as the primary boot source. It's like whatever he did is causing the computer to bypass the CD rom or not be able to run the CD.

Please, if any one can help I am really frustrated right now and have no idea where to even start. Is there a command that I can type into either the command line, or the the message that I'm getting when trying to boot to force ubuntu to return to default settings or undo whatever my cousin did?

Thanks for any help anyone can give.

---

### Post by gbrainin on 2010-04-14
I'm guessing he got into the BIOS setup screen, and switched between RAID and IDE mode.  Try switching back.

---

### Post by Sentoguy on 2010-04-14
> **gbrainin said:**
> I'm guessing he got into the BIOS setup screen, and switched between RAID and IDE mode.  Try switching back.

OK, cool. So, how exactly do I do that? I know how to get to the setup screen, but don't know which drop down menu to go into to find the option of switching between those two options.

BTW, I've got a dell Zino HD if that helps.

Thanks for the help.

---

### Post by gbrainin on 2010-04-15
Unfortunately, there is quite a bit of variance between BIOS menus.  However, the RAID/IDE setting (which may have a somewhat different name, depending) is a setting for the hard drive controller, if that helps.  If you post the exact model of your computer, I may be able to look it up.

Note that Windows can only handle one of these, so switching to the other will make Windows not boot properly.  This is easily fixed by switching back.

---

### Post by Sentoguy on 2010-04-15
> **gbrainin said:**
> Unfortunately, there is quite a bit of variance between BIOS menus.  However, the RAID/IDE setting (which may have a somewhat different name, depending) is a setting for the hard drive controller, if that helps.  If you post the exact model of your computer, I may be able to look it up.

Note that Windows can only handle one of these, so switching to the other will make Windows not boot properly.  This is easily fixed by switching back.

Thanks.

Windows boots just fine actually, it's just ubuntu that doesn't.

The exact model is the Dell Zino HD.

---

### Post by reiki on 2010-04-15
> **Sentoguy said:**
> Thanks.

Windows boots just fine actually, it's just ubuntu that doesn't.

The exact model is the Dell Zino HD.

I have a Zino HD.

Assuming you're using Grub to multi-boot
I have a separate root and home partition for Ubuntu. When I say "find your ubuntu partition" I mean the one where /boot resides.
 
Boot a 9.10 live CD and see if your Ubuntu partition is still there. It should show up in Places.

If you can see your Ubuntu partition, click on it in Places to mount it. REMEMBER the NAME. Let's pretend it's called ubuntu

You can reinstall grub by doing:
sudo grub-install --root-directory=/media/ubuntu /dev/sda
(remember you're going to substitute the REAL name of your ubuntu partition)

Then you update grub
sudo update-grub

It should find your windows loader and your ubuntu partition. If it doesn't find ubuntu, then you have a different problem.

disclaimer: I think I have all of the instructions right. I'm doing this from memory at work without access to my machine. But I've had to repair my grub like 5 times in 3 days because I was screwing around with an external eSATA installation.

---

### Post by gbrainin on 2010-04-15
> **Sentoguy said:**
> Thanks.

Windows boots just fine actually, it's just ubuntu that doesn't.

The exact model is the Dell Zino HD.

Sorry, I wasn't familiar with that model, and assumed you were talking about your hard drive. :-)

Reinstalling GRUB is a good idea.  If you can see the hard drive when booting off of a live CD, then my guess as to the problem was wrong, and the problem is most likely somewhere in the GRUB setup.

---

### Post by reiki on 2010-04-16
> **gbrainin said:**
> Sorry, I wasn't familiar with that model, and assumed you were talking about your hard drive. :-)

Reinstalling GRUB is a good idea.  If you can see the hard drive when booting off of a live CD, then my guess as to the problem was wrong, and the problem is most likely somewhere in the GRUB setup.

If windows is booting from the grub menu, but ubuntu isn't, then my guess is the ubuntu entry in grub is messed up. If it's booting straight to windows without grub, then windows may have "repaired" the MBR, in which case a grub reinstall would likely take care of this.

---

### Post by Sentoguy on 2010-04-18
> **reiki said:**
> I have a Zino HD.

Assuming you're using Grub to multi-boot
I have a separate root and home partition for Ubuntu. When I say "find your ubuntu partition" I mean the one where /boot resides.
 
Boot a 9.10 live CD and see if your Ubuntu partition is still there. It should show up in Places.

If you can see your Ubuntu partition, click on it in Places to mount it. REMEMBER the NAME. Let's pretend it's called ubuntu

You can reinstall grub by doing:
sudo grub-install root-directory=/media/ubuntu /dev/sda
(remember you're going to substitute the REAL name of your ubuntu partition)

Then you update grub
sudo update-grub

It should find your windows loader and your ubuntu partition. If it doesn't find ubuntu, then you have a different problem.

disclaimer: I think I have all of the instructions right. I'm doing this from memory at work without access to my machine. But I've had to repair my grub like 5 times in 3 days because I was screwing around with an external eSATA installation.

NICE!!!

Thanks so much Reiki, this actually worked and now I've got Ubuntu up and running again.

---

