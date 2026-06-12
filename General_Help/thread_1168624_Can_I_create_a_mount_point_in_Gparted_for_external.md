---
title: "Can I create a mount point in Gparted for external HD."
date: 2009-05-24
forum: General Help
---

### Post by cptrohn on 2009-05-24
Hi,  I am trying (again) to reformat an external HD to ext 3...  I am using gparted to reformat the HD into ext 3... SO after I reformat the HD do I then go to manage flags in gparted to be able to set up a mountpoint for the HD in ext 3?

I tried to do this once before, but couldn't get it mount properly after formatting to ext 3, so I took it back to ntsf and it mounted up no problems (by just plugging it into the USB, this is what I am wanting with ext 3)

So can this be done fairly easily with the manage flags operation in gparted?  I've done a google search, but I am still kind of a newcomer and learning about computers and how and why things do and don't work...So alot of what I am finding is just a little too technical for me at this moment.

So any help is greatly appreciated..

---

### Post by Bartender on 2009-05-24
Are you using the stand-alone GParted LiveCD (GPLCD)?

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Or the GParted on the Ubuntu install CD?  

I prefer GPLCD.  It's the same installer as you find on the Ubuntu install CD, but it's more complete and I think it just works better.

I've done this sort of thing several times, and never had to screw around with the flags.  I think the flags are only for setting the drive as "boot".  Not sure about that.

Anyway, download GPLCD, burn to a CD (same idea as installer CD, it's an .iso file) and boot from the CD with the external drive plugged in.  GPLCD should see the external.  Wipe it, format as ext3 or 4, then get out of GPLCD and let the PC boot normally.

There are some weird things to know about permissions and such that you won't be familiar with if you're coming from the Windows world.  The drive should show up under "Places" but you'll have to do some screwing around with permissions.  Here's a thread where I asked about that and got some help.

[http://ubuntuforums.org/showthread.php?t=1016710](http://ubuntuforums.org/showthread.php?t=1016710)

---

### Post by drs305 on 2009-05-24
cptrohn,

Once you have the partition formatted to ext3 in gparted. I find labels very convenient, so you might want to add a label. Other than that, there should be no need to do anything else from within gparted. 

Unmount the device ("sudo umount -a" will work although you will get "busy" messages) and then cycle the external's power. It should mount under /media/yourlabel (example: /media/mydata or whatever you labeled it).

Run the following to make you the owner of all the files on the device (substitute your username and label, of course):
```

sudo chown -R *yourusername*: /media/*yourlabelname*
# Example: sudo chown -R john: /media/mydata

```

The next time you boot or the device is connected it should automatically mount on /media/yourlabelname with all the files owned by you.

---

### Post by cptrohn on 2009-05-24
OK thank you to both of you..


I've got the drive reformatted into ext 3.... But there seems to be a lost and found folder on the drive that I can't access for some reason... (I also can't seem to delete this file as well.. )  I get a permissions error everytime I try to access this lost and found folder and it says I can't get into it......


I read on another linux where somebody had recommended using DBAN to completely wipe the external and then reformat it....


WOuld the gparted liveCD do the same thing?  Because yes I had been using gparted from the add/remove in ubuntu...


Is this something that is being left over from the windows filesystem when I reformated it the first time? 


I seem to be able to mount the drive, but then I can't use it after it is mounted..

---

### Post by cptrohn on 2009-05-24
Ok.. I get it now...


I have to basically give myself permission to the file in a terminal then!!


That seems to be what my problem is...

Thanks guys for the help, I think this is my solution!

---

### Post by cptrohn on 2009-05-24
Works perfectly now, Thank you very much for the help... Made my day.):P

---

