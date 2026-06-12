---
title: "switch to text when booting up.. swapfile?"
date: 2009-04-17
forum: General Help
---

### Post by iochinome on 2009-04-17
hey guys, so i recently installed ubuntu 8.10 on my acer aspire one laptop, dual booting with windows. for some reason, it takes a really long time to boot up- it goes to the black and orange screen w/ the ubuntu logo and loading bar, but then about 1/3rd of the way through, it always stalls out, then reverts to a command-line like text screen where it lists a bunch of operations (Thats what i assume they are) and it is stopped at 'swapfile.' all of them have an 
[ok]
accross the screen from them. how can i speed this up? thanks!

---

### Post by codeseer on 2009-04-17
> **iochinome said:**
> hey guys, so i recently installed ubuntu 8.10 on my acer aspire one laptop, dual booting with windows. for some reason, it takes a really long time to boot up- it goes to the black and orange screen w/ the ubuntu logo and loading bar, but then about 1/3rd of the way through, it always stalls out, then reverts to a command-line like text screen where it lists a bunch of operations (Thats what i assume they are) and it is stopped at 'swapfile.' all of them have an 
[ok]
accross the screen from them. how can i speed this up? thanks!

I'm not understanding you fully. Does it boot all the way into the Desktop environment eventually or does it stop and fail?

---

### Post by Cybie257 on 2009-04-17
Did you install it with the autoinstall or did you manually specify partitions? I'm wondering if you don't have a Swap partition. ???

-Cybie

---

### Post by iochinome on 2009-04-17
just for extra info, the line it stops on says :
activating swapfile swap...                               [ok]

thanks!

---

### Post by iochinome on 2009-04-17
no, it does boot into the desktop environment, just slowly. i think i had wubi install it, actually, if that helps. 
thanks!

---

### Post by codeseer on 2009-04-17
Well I think wubi will be slower than a real dual-boot setup.

Edit:

Yeah, from what I'm reading wubi essentially creates a virtual disk, sort of like a virtual machine would; so, I could imagine that wubi is a bit slower, but maybe not as slow as a virtual machine would be. I'm reading posts that say it is about half the speed of a real installation or dual-boot setup.

Might I alternatively suggest resizing your windows partition to make enough room for an Ubuntu install?

---

### Post by iochinome on 2009-04-17
hmm... well, when i tried to install ubuntu via a usb stick (thing is i have an acer aspire one, which does not have a cd drive) it gave me some error, not allowing me to even boot into it via that... created off of the live cd... so i just went with wubi. should i re-install it, do you think?

thanks

---

### Post by Daisuke_Aramaki on 2009-04-17
> **iochinome said:**
> hmm... well, when i tried to install ubuntu via a usb stick (thing is i have an acer aspire one, which does not have a cd drive) it gave me some error, not allowing me to even boot into it via that... created off of the live cd... so i just went with wubi. should i re-install it, do you think?

thanks

how did you prepare your usb stick may i ask?

---

### Post by codeseer on 2009-04-17
> **iochinome said:**
> hmm... well, when i tried to install ubuntu via a usb stick (thing is i have an acer aspire one, which does not have a cd drive) it gave me some error, not allowing me to even boot into it via that... created off of the live cd... so i just went with wubi. should i re-install it, do you think?

thanks

Maybe you should try this for setting up your USB stick:
[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

---

### Post by iochinome on 2009-04-17
i created the usb stick with the application that comes installed on ubuntu... from the dropdown bar. it says 'create a ubuntu disc' or something of the sort. so should i go to the website above and try to reinstall ubuntu from there? i would like to keep windows...

thanks for all the help!

---

### Post by codeseer on 2009-04-17
> **iochinome said:**
> i created the usb stick with the application that comes installed on ubuntu... from the dropdown bar. it says 'create a ubuntu disc' or something of the sort. so should i go to the website above and try to reinstall ubuntu from there? i would like to keep windows...

thanks for all the help!

The one from the "dropdown bar" is for a 'startup disk', not an installation disk. Yeah, the site in my post above will guide you on creating a real installation disc on the USB stick.

If you have one big Windows partition, you'll need to resize it though to make room to install Ubuntu.

---

### Post by Daisuke_Aramaki on 2009-04-17
> **iochinome said:**
> i created the usb stick with the application that comes installed on ubuntu... from the dropdown bar. it says 'create a ubuntu disc' or something of the sort. so should i go to the website above and try to reinstall ubuntu from there? i would like to keep windows...

thanks for all the help!

use unetbootin, its pretty good.

---

### Post by codeseer on 2009-04-17
I recommend defragmenting your Windows installation using this:
[http://www.iobit.com/iobitsmartdefrag.html]("http://www.iobit.com/iobitsmartdefrag.html")

Then resizing your disk, using either Windows Vista's (if you have Vista) drive utilities or GParted.

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/")
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by iochinome on 2009-04-18
well, i have xp actually but ill give it a try and let you all know how it goes. thanks!

---

### Post by iochinome on 2009-04-18
so i went into 'partition editor' to see if i did in fact have a partition set up, and heres what it had:
/dev/sda1                   fat32             PQSERVICE    4.88 GiB  
/dev/sda2(picture of keys)  ntfs  /boot,/host 144.17 Gib

then the second one's flag is 'boot.' i do not know what any of this means, but is it screwed up? i am dual booting ubuntu 8.10 live and windows xp. 

thanks!

---

### Post by codeseer on 2009-04-18
/dev/sda1 is your acer restoration partition for windows
/dev/sda2 is your windows installed partition

If you've already defragmented, you can just fire up GParted and resize /dev/sda2 to accommodate a Ubuntu install. You have 144 GB on the partition; I'd say resize it down to about 114, giving yourself 30 GB for Ubuntu (If you have that and then some on your free space of the windows install). That should give you enough play room to determine if you want to keep Ubuntu and ditch windows, go back to windows or whatever.

Once you resize and restart with Ubuntu in the USB stick, booting from the USB stick, Ubuntu will see 30 GB of free space. I'd allocate enough space that it equals your RAM size to a swap partition; then give the rest to / with ext3.

---

### Post by iochinome on 2009-04-19
hmm...
so i installed smart defrag, and when i tell it to defrag the ntfs file system, it just mysteriously stops about two seconds after it starts... same with the 'analyze' thing. under 'status' for the C:\, it says first 'idle' then 'stopping.' never anything between. how do i get this to defragment? because i cant resize without it...
thanks!

---

### Post by codeseer on 2009-04-19
What did it say your fragmentation percentage was?

Oh wait. *slaps forehead*

Do you have a SSD?

---

### Post by iochinome on 2009-04-19
most likely not... because i have never heard of it. wikipedia tells me it is a solid state drive. so yes, yes i do have a solid state drive. this is all on an acer aspire one, which has a 140-some gb solid state drive. is this a problem?

---

### Post by codeseer on 2009-04-19
> **iochinome said:**
> most likely not... because i have never heard of it. wikipedia tells me it is a solid state drive. so yes, yes i do have a solid state drive. this is all on an acer aspire one, which has a 140-some gb solid state drive. is this a problem?

Well, it doesn't need defragmenting. That's why Smart Defrag is behaving like that.

Humm... :-?

I'm not sure how GParted would behave with the resizing of an SSD. I'll see if I can find something on it.

---

### Post by iochinome on 2009-04-19
well, when i fired it up, it just wouldnt allow it. (the buttons for 'resize' when i had the partition hilighted did not appear.)

thanks!

---

### Post by codeseer on 2009-04-19
Yeah, it may be so dangerous that it isn't implemented in GParted, considering the way SSDs write; at least not yet. That's a bummer.

You don't have any other drives to store windows on temporarily?

---

### Post by iochinome on 2009-04-19
well, i have a 4gb usb flash drive, and my brother has a portable hard drive too that i could use for an afternoon or so. would that work? what do i have to do?

---

### Post by codeseer on 2009-04-19
I'd give Clonezilla a go and see how big of an image it creates from the SSD.

Here's the USB stick creation instructions: [http://clonezilla.org/clonezilla-live/liveusb.php]("http://clonezilla.org/clonezilla-live/liveusb.php")
Here's the step by step imaging guide: [http://clonezilla.org/clonezilla-live/doc/]("http://clonezilla.org/clonezilla-live/doc/")

---

### Post by iochinome on 2009-04-19
so i am curious as to how this is supposed to work out...
i originally installed ubuntu 8.10 from wubi on my laptop with a solid-state drive with all standard settings, sharing the space with windows. how is it usually done? does this happen to everyone? the only reason that i did it that way is that i do not have an actual cd drive in that laptop. this has to be a pretty common occurance, since it is a pretty common laptop.

so what are you having me do? put windows onto a flash drive?

thanks

---

### Post by codeseer on 2009-04-19
Wubi creates an image file, single file, that is comparable to those created by virtual machines; thus the slow performance. Basically image windows onto an external drive. If you didn't care about windows, I'd say format the drive and install Ubuntu from the USB stick you created.

The idea is to image windows off onto an external disk, then reformat the ssd to the size desired for windows, leaving enough room for Ubuntu to install. Then reimage the image from the external drive back onto the drive in the laptop to the new windows partition, then install Ubuntu to the free space.

---

