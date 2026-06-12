---
title: "Urgent help needed - booting problems"
date: 2009-01-02
forum: General Help
---

### Post by miocene on 2009-01-02
OK, first my setup:
I have a vista installation on a Raid array of 2 160GB hds.
I also have a separate 80GB hd onto which I just installed Ubuntu using the live cd installer.
To install onto this I selected it in the partition tool during installation under "guided".

Now I have serious issue - I cant boot into anything.
When I turn on my pc it detects the drives and then says "GRUB loading stage 1.5"
then "GRUB loading"
the "error"
and a cursor just sits there and blinks.

I have tried disconnecting the 80gb but no difference. I also tried booting from the RAID array.

How can I get my vista back - or anything at all for that matter? PLease say it isn't lost forever.

---

### Post by phinullfermata on 2009-01-02
Good news is, your VIsta drive probably isn't gone.  When you installed on the external HD, did you take out the internal one?  It sounds like you've written over your boot sector.  You'll need to recover that.  I know in XP there is a fixmbr command in the recovery prompt.  I would suggest trying to look into recovering your boot sector, because that's most likely the problem.

If you want ubuntu to work with your setup you need to install grub on the external drive.  When I did this I took out my internal drive completely to make sure Grub couldn't be loaded anywhere else.

The page that helped me out a lot with installing on an external drive [here]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent").
look at the instructions for Method 1.

---

### Post by miocene on 2009-01-02
Thanks for the reply.
OK, I (rather stupidly) did not unplug my RAID (vista) drives before installing Ubuntu. They are plugged into SATA 1 and 2.
The 80gb drive is internal also and plugged into SATA 4. (DVD is SATA 3).

I'm hoping all is not still lost though. How do I recover my boot sector? Do I need a vista cd to get a recovery prompt?

Edit: it is still not a problem to unplug my SATA drives if needed.

---

### Post by phinullfermata on 2009-01-02
I found [this]("http://support.microsoft.com/kb/927392") - it should help.  You will need your Vista CD.
EDIT:
You will probably need the fixmbr option.  Good luck.O:)

---

### Post by miocene on 2009-01-02
Thankyou so much that has fixed it! Phew thought I was done for.
I think I'll try a reinstall of Ubuntu now but unplug my Vista drives first.

Is there a good guide to help me through this? I would like to boot to Vista by default but have the option to boot to ubuntu also.

---

### Post by phinullfermata on 2009-01-02
No problem, I made the same mistake I first installed.  The link I gave you before is what I went off of.  The only thing I did differently from that process was editing my /boot/grub/menu.lst file to use the right drive.  The drive you want will be one of either /dev/sda1 or /dev/sdb1 .
[This]("http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/") is also a good guide, but doesn't mention the /boot/grub/menu.lst edits.

This is what I did to fix the boot menu, I changed the section that looked like this:
```
title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic[COLOR=Red] **root=/dev/sdb1**[/COLOR] ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet
```You will need to change the stuff highlighted in bold red to whatever hard drive your usb drive is, which might take some trial and error if ubuntu won't work correctly right after the install.  To change this file you'll need to boot into ubuntu using the live cd, and change the file on the external drive.

---

