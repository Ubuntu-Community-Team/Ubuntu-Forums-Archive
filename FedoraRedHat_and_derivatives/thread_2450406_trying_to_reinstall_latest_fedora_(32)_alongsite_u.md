---
title: "trying to reinstall latest fedora (32) alongsite ubuntu but the live USB isn't"
date: 2020-09-13
forum: Fedora/RedHat and derivatives
---

### Post by ronjjjg8885 on 2020-09-13
loading anymore.

the reason why i want to reinstall is because i've not entered my  password correctly when i set it for the first time and i forgot what  i've entered.
bottom line: can't loging fedora.

when i load the usb i get these errors {SCREENSHOT ADDED}
what should solve it?

[ATTACH=CONFIG]286949[/ATTACH]

thanks in advance!

---

### Post by guiverc on 2020-09-13
Is the USB the same architecture (i686) as the installed system is (which is i686 given the Fedora-WS-Live-32-1-6)?  You can (I believe, sorry I'm rusty with Fedora) see those messages when you boot a different architecture (amd64) to the prior install.

If this is on a VM, is the architecture the same & hasn't been changed to the initial install?

*I'm no expert in Fedora, I've got an install here but it's mostly used for comparison testing, to confirm bugs aren't Ubuntu specific*

---

### Post by ronjjjg8885 on 2020-09-13
thank you!
do you mean to ask if the usb with the fedora installation the same as i used for installing it? if this is what you mean, the answer is yes..
if you meant to ask about my system. my computer is 64bit. and i don't know what is i686 architecture.

i'm not very good with linux so i'm not sure what exactly you mean.

i need fedora for learnig from a book about using linux.

should i perhaps reprepare the usb live fedora and try again then?
{i created it with the fedora tool on windows on another computer}

---

### Post by guiverc on 2020-09-13
If the 'usb' is the same one your originally installed Fedora with, and it's not had a different image written to it, my guess will be wrong I now believe.  (I'd did a quick search online and it came with that as a possible cause there too).

-- FYI only
[I]x86 or 32-bit is called i386 in Debian (intel created the 80386 & the class of cpu became i386). Debian & Ubuntu refer to all x86 (32-bit) as i386, where as later x86 advanced to i486, i586 and the final 32-bit was i686. Fedora (& the Linux kernel) call it i686, as it's the type of 32-bit intel cpu required; or correctly the **architecture**.

The most common alternative is amd64 (64-bit or x86_64). It's called AMD64 as AMD created the x86 that was backwards compatible with x86 (32-bit). Intel's attempt failed in the marketplace (IA64) so even intel made cpus are amd64.  All companies call it amd64 (intel, amd, apple, microsoft..)[/I]
-- END FYI

Your issue maybe just the forgotten password, and Fedora is just not letting you re-install until you prove you have access rights via entry of the correct password. If you've forgotten the password, or it was mis-entered, you may need to clean install the system, or replace the forgotten password with a known one (the same as you can do with forgotten windows passwords, replace the hashed password with a known hashed password; assuming you don't have encryption).

I can't explain the Warning messages though, and it would take me too long to explore a Fedora-Workstation-32 ISO (*my own is called Fedora-Workstation-Live-x86_64-32-1.6 where yours is missing the amd64, which I suspect is significant but aren't sure sorry*).

Sorry I can't really advice any further, as I'm largely a Debian and Ubuntu user.

---

### Post by vidtek on 2020-09-13
If you have an installed Ubuntu system, why are you loading the USB from Windows?  Just use mkusb to install the fedora system to your stick in Ubuntu.
Fill out you signature with details of your base system, that will help you get properly targeted replies.  At least we know you are in the covid capital of Aus.  (I'm ex Perth btw).

2 things for you to check:
As guiverc says, check which architecture you are downloading and burning, make sure the burned stick is the same and it has the same boot structure, the old bios or the newer UEFI type.   

Cheers Tony.

---

### Post by ronjjjg8885 on 2020-09-13
> -- FYI only
[I]x86 or 32-bit is called i386 in Debian (intel created the 80386 &  the class of cpu became i386). Debian & Ubuntu refer to all x86  (32-bit) as i386, where as later x86 advanced to i486, i586 and the  final 32-bit was i686. Fedora (& the Linux kernel) call it i686, as  it's the type of 32-bit intel cpu required; or correctly the **architecture**.

The most common alternative is amd64 (64-bit or x86_64). It's called AMD  as AMD created the x86 that was backwards compatible with x86 (32-bit).  Intel's attempt failed in the marketplace (IA64) so even intel made  cpus are amd64.  All companies call it amd64 (intel, amd, apple,  microsoft..)[/I]
-- END FYI

a bit confusing to comprehend, but still interesting!

> assuming you don't have encryption
no, no encryption

anyhow, thanks,
what i did is to install it on my desktop computer and now i'm happy with it.

i want to erase fedora from the laptop because if the password problem.

can you tell me which guide/article explain it  the best? my laptop's ubuntu is working. the os to delete from the laptop is the fedora...
how to remove fedora relatively easily from dual book system?

thank you for the readiness to assist and thanks for explaning

---

### Post by ronjjjg8885 on 2020-09-13
> If you have an installed Ubuntu system, why are you loading the USB from  Windows?  Just use mkusb to install the fedora system to your stick in  Ubuntu.

i've tried to find explanation for how to make a bootable live usb stick in ubuntu but the articles suggested apps like etcher which i prefer not to install as it is not from the software center.
i just wanted to do it quickly so i went to windows 10 and downloaded fedora's tool.

> Fill out you signature with details of your base system
good idea.
i created one. can you see it? should i be able to see my own signature?

TNX!!

---

### Post by guiverc on 2020-09-13
> **ronjjjg8885 said:**
> 
i want to erase fedora from the laptop because if the password problem.

can you tell me which guide/article explain it  the best? my laptop's ubuntu is working. the os to delete from the laptop is the fedora...
how to remove fedora relatively easily from dual book system?


My current system is dual boot, the two OSes are Ubuntu *groovy* (*the development release*) and Ubuntu 18.04 LTS (*a fallback should I have issues*)

If I wanted to remove one, I'd boot the other one, erase the partitions of the OS I didn't want (mine contain two partitions used by each, one for / & one for /home).  This erases the other system, **but** may leave a broken system if the *now* erased system owned the MBR (first sector of the OS that contains a pointer used by `grub`). To ensure the current OS owned the boot process, I'd enter the command

```
sudo grub-install /dev/sda
```

I'd then reboot & test.

--
Another example of the same thing.  If I was to boot a system to my left, which contains 3 OSes being include Lubuntu 20.04, Fedora 32 & OpenSUSE tumbleweed. If I wanted to erase Fedora, I'd boot an OS (Lubuntu 20.04 in my case), load it's *KDE Partition Manager *and remove the Fedora partition(s)  (both / and /home) then again to ensure the system booted and didn't end up in *grub rescue* (*because of a dangling pointer*) enter the same `sudo grub-install /dev/sda` command. 

On that box I know Lubuntu owns the grub, so the `grub-install` command is not necessary, but re-running again will do no harm so I'd likely do it anyway, just to be sure.

**NOTE**:  /dev/sda is my boot device on both my example boxes; it maybe something different on your boxes.  `blkid` may provide some clues.

--
If I wanted to use the now free disk space for something else, I'd not do that in this erasure step. After everything was tested & I knew it was good, I'd boot a *live* system and makes those changes later.  Partition changes like re-sizing can be risky, so backup first.

---

### Post by vidtek on 2020-09-14
No, signature not visible yet.

---

### Post by C.S.Cameron on 2020-09-15
> **ronjjjg8885 said:**
> the articles suggested apps like etcher which i prefer not to install as it is not from the software center.

Gnome-Disks will do everything Etcher will do.

- Select the Disk you want Ubuntu Live on.

- Select the icon with three lines upper right.

- Select Restore Disk Image.

- Click Image to Restore.

- Find the image and click Open.

- Click Start Restoring.

---

### Post by ronjjjg8885 on 2020-09-16
C.S.Cameron
ok i see

guiverc
thanks again.
i will have to be able to determine which partition needed to be erased first because the name of the partition isn't fedora

i will try to check why the signature not visible

---

