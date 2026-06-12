---
title: "How to safely remove an USB pen drive?"
date: 2009-04-25
forum: General Help
---

### Post by juanbretti on 2009-04-25
Hello,
I have Ubuntu 9.04.

I would like to know how to safely remove an USB pen drive or HHD from Ubuntu.

I'm looking for something like the Windows "Safely remove".

Something that shut the power off of the USB port.

I've found this soft: [https://launchpad.net/ejecter](https://launchpad.net/ejecter)
Is it good? Is it necesary? Or just UNMOUNT do the job?

Also, I've found this comments: [http://ubuntuforums.org/showpost.php?p=1606778&postcount=4](http://ubuntuforums.org/showpost.php?p=1606778&postcount=4)
Is this correct? Is not unsafe to remove with the power on?

Thanks for your comments and help.

Saludos,
pepemosca

---

### Post by bodhi.zazen on 2009-04-25
1. Close all files using the device.

2. In the file manager, right click the usb device and select eject or remove.

3. Or, from the command line, umount the device.

---

### Post by juanbretti on 2009-04-25
That's it?

Because I've just kill an USB pendrive... And I think it's because the "unmount" was not enought.

Am I wrong?

---

### Post by HermanAB on 2009-04-25
$ sudo umount -l /dev/sdb

---

### Post by TR1X on 2009-04-25
it should be enough, ive never had any misfortune with unmounting

---

### Post by bodhi.zazen on 2009-04-25
> **pepemosca said:**
> That's it?

Because I've just kill an USB pendrive... And I think it's because the "unmount" was not enought.

Am I wrong?

That' it. 

Removing a drive without unmounting it should not kill a drive as you say, it would result in data loss.

---

### Post by Peasantoid on 2009-04-25
1) Make sure nothing is accessing the drive or you'll get all manner of I/O errors.
2) Pull it out.
3) There is no #3.

This works fine for me, but your mileage may vary.

---

### Post by |{urse on 2009-04-25
uh no dont just yank it out.. issue this command before you remove any drive 

> sync

the sync command will finish up any job the drive may or may not have finished up.

then yes u can pull it lol

---

### Post by Peasantoid on 2009-04-25
> **|{urse said:**
> the sync command will finish up any job the drive may or may not have finished up.

then yes u can pull it lol
:shock:
Crap, I've been doing it wrong for ages.

Edit: But I thought I read somewhere that "sync" is unnecessary...?

---

### Post by |{urse on 2009-04-25
Oh? It's quite necessary if you want your transferred data to be complete despite delayed writes.
lmao noone uses that command and i dont know why...

---

### Post by juanbretti on 2009-04-26
Question: If is it so necessary, why is not associated with the UNMOUNT command?

I mean, when I do an UNMOUNT Ubuntu could also do -internally- the SYNC.

Just for safety.

So I should use this: [https://launchpad.net/ejecter](https://launchpad.net/ejecter) for a GUI of the "SYNC" command?

---

### Post by juanbretti on 2009-04-26
And, any way to shut off the power of the USB port?

---

### Post by mcduck on 2009-04-26
> **pepemosca said:**
> And, any way to shut off the power of the USB port?

I don't think there is. By standard, USB ports should provide 5V/100mA always when the computer is powered.

---

### Post by Seventh Reign on 2009-04-26
Nautilus and Dolphin have an Eject button.  Just click the icon and wait for the icon to vanish.  Pull out the Pendrive.

Your're Done.

---

### Post by mcduck on 2009-04-26
> **pepemosca said:**
> Question: If is it so necessary, why is not associated with the UNMOUNT command?

I mean, when I do an UNMOUNT Ubuntu could also do -internally- the SYNC.

Just for safety.

So I should use this: [https://launchpad.net/ejecter](https://launchpad.net/ejecter) for a GUI of the "SYNC" command?

umount does sync the drive. It's just that syncing might take a while (depending on the amount of data waiting to be written to the drive) so it's still possible to unplug the drive too soon after running umount.

Just use the umount command (no need for sync) but make sure your drive's light stops blinking before you unplug it.

At least in Gnome, if there's much data to write to the drive, you will get a progress window showing the sync progress after ejecting the drive.

---

