---
title: "mount: unknown filesystem type 'vfat'"
date: 2009-03-25
forum: General Help
---

### Post by sdlynx on 2009-03-25
I can't mount any of my FAT32 flash drives because apparently vfat/fat32 is an unknown filesystem type on Ubuntu now.  It worked before and I didn't change anything.  Does anybody know why and how to fix this? Thanks in advance.

P.S. Also sometimes I plugged in a flash drive and Ubuntu wouldn't read it and I'd have it to plug it in and out a few times for it to mount it (otherwise it wouldn't mount at all)

---

### Post by coffeecat on 2009-03-25
> **sdlynx said:**
> I can't mount any of my FAT32 flash drives because apparently vfat/fat32 is an unknown filesystem type on Ubuntu now.

That's news to me - and I should imagine it's news to the Ubuntu devs. Flash drive formatted VFAT mounting nicely in Ubuntu 8.10 even as I type.

What error messages are you getting, if any?

**Edit:** just a moment. You said flash drive and FAT32. Flash drives are usually formatted FAT16. Whatever, a FAT16 flash drive and a FAT32 USB drive have both just automounted cleanly for me in Ubuntu 8.10.

---

### Post by sdlynx on 2009-04-09
> **coffeecat said:**
> That's news to me - and I should imagine it's news to the Ubuntu devs. Flash drive formatted VFAT mounting nicely in Ubuntu 8.10 even as I type.

Its true, I could easily mount my flash drives one day and then the next day all of a sudden vfat was no longer supported.

> **coffeecat said:**
> What error messages are you getting, if any?

I get as follows:

**Failed to mount "SDLYNX-5".**
mount: unknown filesystem type 'vfat'.

> **coffeecat said:**
> **Edit:** just a moment. You said flash drive and FAT32. Flash drives are usually formatted FAT16. Whatever, a FAT16 flash drive and a FAT32 USB drive have both just automounted cleanly for me in Ubuntu 8.10.

My flash drive is a 4GB and I formatted it to FAT32.  Also, my iPod comes formatted to FAT32.  Basically they used to mount fine but not anymore.

---

### Post by SuperSonic4 on 2009-04-09
Have you tried resetting HAL ```
sudo /etc/init.d/hal restart
``` (hal deals with hardware you plug in etc). Does mounting through the terminal work? ```
sudo mount -t vfat /dev/sdXX /media/<place>
```

---

### Post by sdlynx on 2009-04-09
hal didn't work but what do I use for the <PLACE> part?  If I just use say the name of the drive it tells me that mount point doesn't exist, like:
```
mount: mount point /media/USB does not exist
```

EDIT: I just made a folder under root at /media/USB and now it tells me that vfat is unsupported.

---

### Post by cariboo on 2009-04-09
Vfat file system support is built in to the kernel. Did you build yourself a custom kernel?

I would also suggest you check the partition using gparted. If you don't have it installed, you can use Add/Remove Programs or Synaptic Package Manager to install it.

Jim

---

### Post by sdlynx on 2009-04-09
nope I have been using the default kernel that came with Ubuntu.

yes I checked the partitions with GParted and they are fine (and visible).

---

### Post by sdlynx on 2009-04-17
bumpp

---

### Post by danwood76 on 2009-04-17
Is your system all the way up to date?

If you have an older kernel version you could try booting from that to see if vfat support is in there.
Maybe you have a corrupt (heaven forbid) vfat driver.

---

### Post by sdlynx on 2009-04-17
Oh well yes my system is up to date and I only have one kernel...
Can my vfat driver actually be corrupt? how can I check or fix that?

---

### Post by danwood76 on 2009-04-17
I seriously doubt it, but it is possible for you disk to have an odd error.

You could try seeing if the driver is actually there, run this:
```

modinfo vfat

```
if that gives you information try loading it:
```

sudo modprobe vfat

```
that might give you errors out and point you in the direction of the problem.

---

### Post by sdlynx on 2009-04-17
ok I ran sudo modprobe vfat and there was obviously a problem because:

```
WARNING: Could not open '/lib/modules/2.6.24-19-generic/kernel/fs/fat/fat.ko': No such file or directory
FATAL: Error inserting vfat (/lib/modules/2.6.24-19-generic/kernel/fs/vfat/vfat.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

Thanks so much for pointing me in the direction of what's wrong.  Now I just need to know what to do to fix it...

---

### Post by coffeecat on 2009-04-17
Try booting into an older kernel and seeing if the vfat mounting issue is there or not. If you can mount vfat filesystems OK with the older kernel, uninstall the 2.6.24-19 kernel and all 2.6.24-19 packages. Then reinstall them. You'll probably be prompted to do this by the update manager anyway.

---

### Post by danwood76 on 2009-04-17
Well considering you only have one kernel installed that will not work.

What you can do is reinstall the kenrel through synaptic.
Search in synaptic for your kernel version, the one you are looking for is probably:
```

linux-image-2.6.24-19-generic

```

---

### Post by coffeecat on 2009-04-17
> **danwood76 said:**
> Well considering you only have one kernel installed that will not work.

Yes, you're quite right. I missed this:

> **sdlynx said:**
> Oh well yes my system is up to date and I only have one kernel...
Can my vfat driver actually be corrupt? how can I check or fix that?

However, the OP's system is not up to date. The 2.6.24 kernel is the kernel release used in Hardy, and there have been 2.6.24-21 and -23 versions issued for Hardy since the -19 version.

**sdlynx**, I'm puzzled. Your user profile says Ubuntu 8.10, but you seem to be using the 8.04 kernel. Can you clarify this? And if you are using 8.04, updating the system should bring in the -23 kernel, which might fix the issue for you.

---

### Post by danwood76 on 2009-04-17
Thats true, I'm using jaunty so I'm unsure of kernel minor versions that old :)

---

### Post by coffeecat on 2009-04-17
> **danwood76 said:**
> Thats true, I'm using jaunty so I'm unsure of kernel minor versions that old :)

Well, I'm using my Mac Mini at the moment, and I had to start VirtualBox up in order to boot virtual Hardy just so that I could check kernel version numbers. The things I do. :p

---

### Post by sdlynx on 2009-04-17
> **coffeecat said:**
> 
**sdlynx**, I'm puzzled. Your user profile says Ubuntu 8.10, but you seem to be using the 8.04 kernel. Can you clarify this? And if you are using 8.04, updating the system should bring in the -23 kernel, which might fix the issue for you.

Ohhh you're right I thought I had updated but I just checked and apparently not.. this could be the problem.  Wow I feel like an idiot for not noticing that lol...  Well I guess I'll upgrade and check and see if it works after.

EDIT: After upgrading to 8.10 it works fine. Thanks for the help.

---

