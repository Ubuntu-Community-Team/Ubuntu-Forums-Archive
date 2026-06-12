---
title: "Loading GRUB, please wait - error 21"
date: 2009-04-05
forum: General Help
---

### Post by ccpha on 2009-04-05
I recently formated my D: drive(secondary, consisted of fedora) with partition magic, after which I installed Ubuntu onto it via wubi. Now, the problem is that whenever I try to start my box it says the following:

"Loading GRUB, please wait.

Error 21"

I even tried taking away the second harddrive from my box completley, but it didnt do ****.
I cant get anywhere, not even to windows(vista, i know i know).

As you might've guessed, I dont have the ubuntu live cd, and neither do I have a vista install CD, since the box was delivered with vista installed and a "hidden" HD that would auto-recover it, but since it cant get past the GRUB-error, I cant access it.

Any ideas on what I can do to at least get to Windows?
Help much appriciated, thanks.

---

### Post by callie510 on 2009-04-05
I can't tell you how many times I've had to fix grub when installing or reinstalling Ubuntu or Windows. 

I think you really need a Live CD ... do you have a friend with a computer whose CD burner you can use, or access to a computer with a CD burner at all? I guess you can order one from the website if you really don't know anyone whose CD burner you can borrow for a second. One time I had an emergency, grabbed some CDs from the local pharmacy, and used the computers in the local library to burn an Ubuntu Live CD :)

Once you've got one, you can fix grub with the following commands (make sure you mount your drives first):

sudo grub
find /boot/grub/stage2
** this will tell you where your grub is. mine is (hd0,5); yours will almost certainly be different.. replace numbers needed**
root (hd0,5)
setup (hd0)

In my experience grub is very intelligent and will put the windows bootloader in the list so you can boot windows too. I've never had to edit the menu list, although this is possible.

The much-less-free method is to somehow get ahold of a Windows CD (borrow a friends?) and boot into recovery mode and use fixboot - this will restore the Windows bootloader. Of course, you will only be able to boot into Windows this way. 

You should really have a Windows disc and an Ubuntu disc for precisely this reason - if something ever happens to make your computer unbootable, you need them! :) Usually your computer manufacturer will let you order the recovery discs for your computer, if you've lost them, for some small fee.

---

### Post by ccpha on 2009-04-05
> **callie510 said:**
> I can't tell you how many times I've had to fix grub when installing or reinstalling Ubuntu or Windows. 

I think you really need a Live CD ... do you have a friend with a computer whose CD burner you can use, or access to a computer with a CD burner at all? I guess you can order one from the website if you really don't know anyone whose CD burner you can borrow for a second. One time I had an emergency, grabbed some CDs from the local pharmacy, and used the computers in the local library to burn an Ubuntu Live CD :)

Once you've got one, you can fix grub with the following commands (make sure you mount your drives first):

sudo grub
find /boot/grub/stage2
** this will tell you where your grub is. mine is (hd0,5); yours will almost certainly be different.. replace numbers needed**
root (hd0,5)
setup (hd0)

In my experience grub is very intelligent and will put the windows bootloader in the list so you can boot windows too. I've never had to edit the menu list, although this is possible.

The much-less-free method is to somehow get ahold of a Windows CD (borrow a friends?) and boot into recovery mode and use fixboot - this will restore the Windows bootloader. Of course, you will only be able to boot into Windows this way. 

You should really have a Windows disc and an Ubuntu disc for precisely this reason - if something ever happens to make your computer unbootable, you need them! :) Usually your computer manufacturer will let you order the recovery discs for your computer, if you've lost them, for some small fee.

I do have a windows XP(not vista) install CD laying around, dont know what the password is for the recovery console though, and that's how far I get with that, is there a default password or something?

---

### Post by callie510 on 2009-04-05
It should be the Administrator password. I believe the default one is just blank, try just pressing enter? If it was installed on your system when it came, your manufacturer might have a different default admin password. I've seen that before and it's a pain.

I don't know if you can fix a vista boot using a windows XP cd.... it's not something I'd want to try on a system where I don't have everything backed up. 

I think you should try some other kind of CD - a Live CD, a Vista CD, or some other kind of recovery CD. I don't have any other suggestions.... let me know if you do try to fix the boot using the Windows XP cd and it works, though; I'm curious.

edit: [http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654) .... you will want to use fixboot and/or fixmbr. Uhh, I still don't think this is a great idea though.

edit2: this ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)) may also help you, although this also involves burning a CD and if you're going to do that, you can probably make things work with an Ubuntu Live CD.

---

### Post by ccpha on 2009-04-05
> **callie510 said:**
> It should be the Administrator password. I believe the default one is just blank, try just pressing enter? If it was installed on your system when it came, your manufacturer might have a different default admin password. I've seen that before and it's a pain.

I don't know if you can fix a vista boot using a windows XP cd.... it's not something I'd want to try on a system where I don't have everything backed up. 

I think you should try some other kind of CD - a Live CD, a Vista CD, or some other kind of recovery CD. I don't have any other suggestions.... let me know if you do try to fix the boot using the Windows XP cd and it works, though; I'm curious.

edit: [http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654) .... you will want to use fixboot and/or fixmbr. Uhh, I still don't think this is a great idea though.

edit2: this ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)) may also help you, although this also involves burning a CD and if you're going to do that, you can probably make things work with an Ubuntu Live CD.
I got my hands on a live cd, so if I get this right, start PC with disk, chose "try ubuntu without modifying your pc" and type in what you stated earlier in the terminal?
Sorry, but I normally install via wubi, and I've never hit a problem.

And thanks for the quick replies.

---

### Post by callie510 on 2009-04-05
yes indeed. However, make sure you mount your drives first (I do it the graphical way; go to Places and click each drive and then they show up on the desktop)

Go to terminal, type sudo grub, and the rest. Make sure you replace my (hd0,5) with the location of your grub (thats why the find command comes first).

This will fix your problem if it's just a bootloader problem, which it sounds like it is.

---

### Post by ccpha on 2009-04-05
> **callie510 said:**
> yes indeed. However, make sure you mount your drives first (I do it the graphical way; go to Places and click each drive and then they show up on the desktop)

Go to terminal, type sudo grub, and the rest. Make sure you replace my (hd0,5) with the location of your grub (thats why the find command comes first).

This will fix your problem if it's just a bootloader problem, which it sounds like it is.

Alright, tried that command and it says "Error 15 - file not found" :-s

---

### Post by Ben Crisford on 2009-04-05
> **ccpha said:**
> Alright, tried that command and it says "Error 15 - file not found" :-s

I'm not sure but presumably that means Grub isn't installed properly. (if at all)

So try getting the grub files and sticking them on a USB if you can...

I don't know, sorry :S, but it might be worth a shot.

---

### Post by callie510 on 2009-04-05
Post the output of sudo fdisk -l?

Since you just formatted that second partition anyways, one good option would be to use the Live CD to just install Ubuntu on that ... definitely a safer/better option than using wubi, which is meant to install within Windows and not to another partition (iirc). This will make Ubuntu work and will also ensure grub works & is installed... should fix your booting problems.

edit2: seems that grub is in a different place if you use wubi. Try this: "find /wubi/boot/grub/stage2"

---

### Post by callie510 on 2009-04-05
I keep finding more things so I made another post. Sounds like this from the wubi wiki may help too:

> How can I access my Wubi install and repair my install if it won't boot?

Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:

sudo mkdir /win
sudo mount /dev/sda1 /win

Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

Now the content of the virtual disk will be visible under /vdisk. 
To check the filesystem you can use:

sudo fsck /win/ubuntu/disks/root.disk 

---

### Post by ccpha on 2009-04-05
I'm afraid the whole **** collapsed in the end(monitor stopped answering etc) - so I dropped it off @ the manufacturer and they said they'll take a look and replace any broken hardware etc.

Thank you in any case, once everything is fixed I will do as you said, install via the live CD instead.
Again, thank you for your trouble, even if it didn't work out like it was supposed to.

Have a cookie! :D

---

### Post by callie510 on 2009-04-05
Awww - I hope it wasn't anything that happened with the ubuntu CD. Yeah, try the live cd next time - it's definitely the way to go when you're installing to a separate partition. 
Good luck! Hope the comp is OK!

---

