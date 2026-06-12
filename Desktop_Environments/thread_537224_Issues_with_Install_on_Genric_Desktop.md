---
title: "Issues with Install on Genric Desktop"
date: 2007-08-28
forum: Desktop Environments
---

### Post by lodogg on 2007-08-28
Currently I have and older custom built PC.

[I]1.8 amd xp processor
2 gig of ram (333)
200 gig western digital
Generic cd rom
GeForce FX 5500 128MB[/I]

I booted on the CD and choose all the defaults for the install.  It seemed sluggish but finished after reboot I signed in and it hangs on the orange colored back ground?  Could it be the way the drive is partitioned?  I’m sure it can handle 200 Gig.

I did successfully install it on my dell d-600 laptop and it works great except for the 3d rendering I just can’t get it working.:(

Thanks,
lo

---

### Post by lodogg on 2007-08-28
On boot I do get the following error "ACPI: unable to load the system description tables".

Could this be my graphics card causing all of the issues?

-lo

---

### Post by merlinus on 2007-08-28
Perhaps video card problems.  Try this:

boot into recovery mode, login...then enter:

(or Ctrl-Alt-F1 to get to prompt)

```

sudo dpkg-reconfigure xserver-xorg

```
You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```
or reboot.

This should at least get you to a GUI, then you can search how to install the correct video drivers for your card.

-merlin

---

### Post by lodogg on 2007-08-28
It seems like a graphic card issue at this time..:confused:

I ran ```

sudo dpkg-reconfigure xserver-xorg

```

and killed my boot screen all together.  I tried “versa” and a few others and I still can't get startx to work.  Any more idea's would be appreciated..

-lo

GeForce FX 5200 4.34.20.18.00:mad:

---

### Post by merlinus on 2007-08-28
You might try the Alternate Desktop install cd. It is text-based, but quite straightforward.  And it will not be prey to video card problems.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

-merlin

---

### Post by lodogg on 2007-08-29
I will give the text based install a chance then apt-get the necessary drivers for my card.  Will see..

thanks
-lo

---

