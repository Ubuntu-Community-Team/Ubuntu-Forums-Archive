---
title: "Dead/Dying Hard Drive"
date: 2009-05-30
forum: General Help
---

### Post by lockettowl on 2009-05-30
I'm not sure if what I'm asking is possible.
My hard drive is shot - I can't even re-install Ubuntu on it. Right now, I'm using a Live CD until I have enough save up to get a new computer. However, this is very frustrating because it limits what I can do, especially when it comes to saving files. I'm wondering if there is a way for me to still use my hard-drive through the Live CD. I know this is probably not a good idea, but I need something to hold me over until I can get a new system. What are my options?

---

### Post by quixote on 2009-05-30
When a hard drive starts failing, it's usually not long for this world.  The more you use it, the quicker it fails.  And, cosmic law being what it is, the data you lose when it acts up will be the data you absolutely need.  I'd say: get what data you can off that drive, and don't use it.

You don't say how limited your budget is, but if it runs to a USB memory stick, some of the small capacity ones are only a few dollars.  After you boot from your liveCD, you can mount the thumbdrive, and save your files to that.  (If it's a small one, maybe not video files or photo collections :-) . )

You can also use the LiveCD to make a bootable thumbdrive (assuming your computer has booting from a USB device as an option in the boot order).  There's information on the wiki ([https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)) and also here: [http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/)  (for instance for intrepid).  The main site [http://www.pendrivelinux.com](http://www.pendrivelinux.com) has a long list of specific howtos for putting ubuntu versions and other distros on USB drives.

---

### Post by lindsay7 on 2009-05-30
Why not just buy a new hard drive.  I just bought a 500 gig drive from Newegg for $49. You can find all kinds of used drives on ebay for just a few dollars.

---

### Post by Volt9000 on 2009-05-30
> **quixote said:**
> When a hard drive starts failing, it's usually not long for this world.  The more you use it, the quicker it fails.  And, cosmic law being what it is, the data you lose when it acts up will be the data you absolutely need.  I'd say: get what data you can off that drive, and don't use it.

+1 :D

Definitely, boot the LiveCD, mount the hard drive, and copy whatever you can to a USB stick or other removable media.

You're fortunate that you've noticed your hard drive dying. The last hard drive to die on me did so in about 5 seconds flat, from fully healthy to completely unreadable. Didn't have a snowball's chance in hell of saving ANYTHING. :(

---

### Post by lockettowl on 2009-05-30
Thanks for all the advice. Thankfully, I was able to get all (well, most) of my important files of a while ago.

Getting a new hard drive is something that I've thought about, but I'm using a laptop and wouldn't really know how to replace it. Is this something easy to do? If I got an external drive, would I be able to use it like a regular one?

---

### Post by lindsay7 on 2009-05-31
Most computers are easy to work on and changing out a hard drive is easy. Plug and play for the most part. Older machines have IDE or Pata drives which use a flat cable. Newer machines use SATA type drives which use a small cable.  There is lots of instructions on the net for doing this. Basically you unplug the computer open the computer case, disconnect the drice, unscrew the drive, put the new one in and reconnect. Then you partition and format the drive and add the OS.

You can get by with an external drive but it will be very slow compared to an internal one.

---

### Post by quixote on 2009-05-31
Sometimes it's easy.  Sometimes, not so much.  I have a Sharp MP30 -- which I love -- but replacing the HD on that required taking the whole damn jewelry-sized laptop apart.  I did [a post]("http://www.molvray.com/acid-test/2008/12/replacing-a-sharp-mp30-laptop-hard-drive/") on the process if you want to see how that was just for fun.

Dells are usually very simple to work on.  You don't say what kind of laptop you have, but search for the exact model number of your laptop, and find out whether it takes PATA or SATA.  They're not at all interchangeable.

If you use an external HD, then it would probably be USB?  Depending how old your laptop is, it may or may not be set up to boot via USB-connected devices.  When you start bootup, press whatever function key it tells you to enter Setup (usually F2?).  Then you get a whole series of menus to change BIOS options.  One of the tabs toward the end is Boot.  I think the arrow keys will get you there.  And then see if "USB" is one of the options in the boot order.  Move it up ahead of the internal hard drive, if you decide to use that option.

---

