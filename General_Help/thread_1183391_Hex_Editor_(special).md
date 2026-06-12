---
title: "Hex Editor (special)"
date: 2009-06-10
forum: General Help
---

### Post by brodeur235 on 2009-06-10
I'm looking for a hex editor for Ubuntu that is capable of writing directly to disks such as floppies and flash drives. GHex allows this in the windows version, but unfortunately the ubuntu version lacks this feature... All suggestions are appreciated,

Brodeur235

---

### Post by ryanhaigh on 2009-06-10
I've never done this before and would be interested to know the reason for doing so but how are your trying to open the disks? You should be able to open /dev/fd0 (or whatever floppy devices are called) but you will probably need to run ghex as root to do so.

There seem to be a [number of alternatives you might want to try as well]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=all&keywords=hex+editor").

---

### Post by jyaan on 2009-06-10
You could make a floppy image from the disk and edit that, and then just write the image over the floppy later.

---

### Post by brodeur235 on 2009-06-10
I can't make an image from the floppy as the floppy does not mount... Since I just learned that you guys are awesome with response time and I work until my problems are solved, I think you could help a lot if you knew my entire situation... Here goes:

I have just written my first OS. I want to be able to further develop this OS without having to boo/reboot over and over. So, I installed VirtualBox and ghex on BOTH ubuntu (9.04) and windows xp (both apps on both os's).

While in windows everything went fine - breaking with the norm from my experience with that OS. From windows I was able to use GHex to write my 512 byte binary (.bin) boot code / kernel (boot code is the entire OS) to the first sector of a floppy. Then I opened up VirtualBox, made a new virtual machine and booted from drive A. As expected, my first and very minimal OS displayed a string, waited for 1 character input, and then shut down.

While in Ubuntu however, I couldn't find a way to write directly to a floppy's memory, even using GHex because the feature is apparently unsupported in Ubuntu. Additionaly, once I wrote my OS to the first sector of my floppy (using windows to do that part), ubuntu would no longer mount my floppy. I'm guessing that might be because the floppy was no longer formatted with any recognizable file system format. At this point, I don't really mind because I open VirtualBox (in ubuntu), and it recosnizes that there is a floppy drive and allows me to set it to the boot device. However, when I try to start the virtual machine my floppy drive is quite (unlike in windows, at which point it hummed immediately) and I get an error, the gist of which says that VBox could not read understand the boot partition... This seems illogical as the exact same boot code worked perfectly in the windows version of virtual box...

Why do I care if things don't work in Ubuntu when they work in Windows? Up until now I have always been much more comfortable working in Ubuntu... On anything. It's my goto OS and now it seems to be the source of my problems...

All help is appreciated (in finding a solution to ANY of these problems),

Brodeur235

---

### Post by ryanhaigh on 2009-06-10
How were you trying to write to the floppy?

Virtualbox might not be able to access the drive because of a permissions problem depending on how it is trying to access the drive. 

It's pretty cool that you are writing an OS and I'm glad to see Ubuntu is your preferred platform. Have you considered moving away from using actual floppies and just using image files instead? The [info here]("http://untitledfinale.wordpress.com/2007/10/09/create-mount-and-copy-floppy-disks-images-under-linux/") might be useful to you and might eliminate some of your issues.

---

### Post by jyaan on 2009-06-10
Have you tried using dd? You might be able to access it that way by writing/reading directly at /dev/fd0 (or whatever the device is called on your system).

If that works, you can extract an image with ```
dd bs=2x80x18b if=/dev/fd0 of=/tmp/floppy.image 
```

This will put floppy.image on /tmp for a floppy drive with 2 sides, 80x for the cylinders and 18b for the sectors (1474560 bytes). Copying to the floppy is basically the reverse.

---

### Post by brodeur235 on 2009-06-10
> 
How were you trying to write to the floppy?

In windows, the GHex GUI has a menu called "extras", in which you can select "open drive" and choose a disk to write to. It works for disk partitions, usb flash drives, and floppies. The ubuntu version of GHex does not have this menu/option as far as I can tell.

> 
Virtualbox might not be able to access the drive because of a permissions problem depending on how it is trying to access the drive.

Sounds very interesting. This is a possibility that I hadn't even considered.

> 
Have you considered moving away from using actual floppies and just using image files instead? The [info here]("http://untitledfinale.wordpress.com/2007/10/09/create-mount-and-copy-floppy-disks-images-under-linux/") might be useful to you and might eliminate some of your issues. 	

The opposite. I bought my floppy drive from best buy today for this purpose beause neither my BIOS nor VBox supports booting from a USB, a device which I am willing to risk testing my OS on. I am not willing to make a partition to test my OS and risk messing up my drive. The reason I don't use images is because they boot a very different way than usbs/floppies/disk drives. I am just beggining to write OS's and I'm farmiliar with the latter and wish to use that until I become more adept at dealing with the low level mechanics of a computer. So, after eliminating booting from a USB (because I cant), a disk partition (because I won't), and Image files(because I don't want to confuse myself), I'm left with booting from a floppy (and in a virtual machine). Not only is this my preference for now, but others much better at doing what I'm doing have told me that this is a very good - very common - setup. The uncommon ingredient in my case is Ubuntu...

Again, ANY/ALL help is appreciated,

Brodeur235

---

### Post by jyaan on 2009-06-10
I believe a floppy image would be exactly the same as using a real floppy. When you go into VirtualBox settings, just have it load the floppy image instead of from your drive.

---

### Post by ryanhaigh on 2009-06-10
Have you tried just opening the device file for the floppy as per my first post.

Because you are using virtualbox I don't see any advantage in using a real floppy disk (apart from the slower speed and noise ;)) as the virtual machine will see that img file as a real floppy. The dd command does a raw low level copy so it doesn't care about filesystems etc just the bits on the disk. [http://en.wikipedia.org/wiki/Dd_(Unix](http://en.wikipedia.org/wiki/Dd_(Unix))

---

### Post by brodeur235 on 2009-06-10
> 
Have you tried just opening the device file for the floppy as per my first post.

Sorry man, I did not see that link, but I dl'ed the top one (hex curse), located the floppy's file (/dev/sdb) and edited it successfully, changing the startup string from "Welcome to Nick's First OS!!!!" to "Qelcom to Nick's first OS!!!". Some might not consider this progress, but it is. Boom, point for Ubuntu, put it up. Thank you ryanhaigh.

Will update on VBox problem progess as soon as I try the suggested approaches posted...

Brodeur235

---

### Post by brodeur235 on 2009-06-10
I'm a complete dumbass. ALL I had to do was change the extension of the .bin generated by my assembler to .img . WOW. 24 hours of wasted grief, and over complicated workarounds. Oh, and I didn't realize this on my own... Nope, it was jyaan. I used the command he posted to get a .img from the floppy. I opened the new img in hex curse and saw that the contents were EXACTLY the same as those in the original bin. What an end to the day... Finding out it was wasted lol... At least all my problems have been fixed and I can begin full scale OS development in my favorite OS :). Thanks for all your help, you guys are awesome. I'll be using these forums much more often. All help appreciated,

Brodeur235

---

### Post by jyaan on 2009-06-10
One of my favourite things about Linux is that you get all those great command-line utilities right out of the box.

Your idea sounds really interesting, and I think I might take some time out to learn about boot loaders and kernels that way. I'd like to do some on the Linux kernel some day. :) Good luck with your project.

---

