---
title: "recovery iso file"
date: 2008-02-05
forum: Dell  Ubuntu Support
---

### Post by gamelord12 on 2008-02-05
So I was tired of having that recovery iso file on my desktop every time I booted up and deleted it.  Now, I know the recovery image is its own partition as well.  I have a question or two.

1) Since Ubuntu's free and easily downloaded anyhow, would it be safe to delete the recovery partition and just rely on a disc for a re-install?  Synaptic would be able to find the drivers for my laptop hardware and stuff, right?

2) If I do hold on to my recovery partition, is it safe to empty my trash can of the iso file (that looked more like a shortcut than a file in and of itself anyway) that I deleted?

---

### Post by notwen on 2008-02-06
Dell offers custom isos of Gutsy including the additional drivers needed for the hardware not originally supported in the Gutsy install.  Check out the [Dell Linux Wiki]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10") for these DVD images.  I wiped mine and carry the cd around in my laptops bag in case I should ever need to re-install on the road.  Hope this helps.  =]

---

### Post by gamelord12 on 2008-02-07
But what about that disc image on my desktop after a fresh install.  It says it's 5 GB.  Is it safe to delete with that partition on my HDD?

---

### Post by notwen on 2008-02-11
> **gamelord12 said:**
> But what about that disc image on my desktop after a fresh install.  It says it's 5 GB.  Is it safe to delete with that partition on my HDD?

During the install you will reach a Partition Select stage.  Here you would choose to wipe your HDD and install, install using what free space is available and a couple of others.  It is safe to delete this partition **_IF_** you do not mind losing the restore option in GRUB.  I simply carry a LiveCD around w/ me in case I do need to re-install.  Best of luck. =]

---

### Post by gamelord12 on 2008-02-16
I'm asking specifically about the file that appears on the desktop when it's brand new though.  Does the recovery partition rely on that file?  Can I delete the file and rely on the partition?

---

### Post by notwen on 2008-02-17
If you're referring to the restore partition that may be showing up on your desktop.  Do not delete it as it is a mounted partition and you would be physically deleting it's contents, making your restore option inoperable.  Search the forums, I'm pretty sure there's a way to specify which partitions Ubuntu will auto mount at startup.

---

### Post by gamelord12 on 2008-02-18
It's not the partition that's showing up on my desktop.  That would have a hard drive icon.  This is a .iso file, but it's roughly the size of the partition itself.  It looks like it's just a link, yet it's about 5 GB.

---

### Post by wyth on 2008-04-13
I don't believe the reinstall iso you're talking about is linked to that partition.  There's nothing in the properties to suggest it's anything other than a regular .iso file.  

[This is on the Direct2Dell page]("http://direct2dell.com/one2one/archive/2007/12/19/38924.aspx") about the 7.10 machines:
[INDENT]> We are now placing a DVD restore [ISO image]("http://en.wikipedia.org/wiki/ISO_image") on the user's desktop. By burning this ISO to a disc and then booting to it, customers can restore their operating system to the exact state in which they received it. This now gives customers a second option to restore their OS, in addition to the reinstallation partition already located on the hard drive.[/INDENT]So it looks like that .iso is what notwen is talking about -- it's the same thing as what's in the restore partition, just in another place/format.  Burn that to a dvd and delete as you wish.  I just tucked mine into a folder off the desktop.

---

