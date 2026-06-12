---
title: "Radeon 9250 card problems!"
date: 2006-01-08
forum: General Help
---

### Post by franklee on 2006-01-08
Hey folks, I recently upgraded my graphics card in an older machine and installed Breezy, however the Gui wouldnt load and I was thrown out to a terminal. Im guessing the auto installer didnt detect my card and instead installed the onboard video as I have no probs when I connect my modem to onboard...

I want to use the radeon as the video memory is so much greater, 128meg instead of 16meg.

Any suggestions as to how I alter my xorg conf, or similar?

---

### Post by Nrvnqsr on 2006-01-08
well, my Desktop's radeon 9250 is recognized with Ubuntu out of the box, so try this in the terminal

> 
sudo dpkg-reconfigure xserver-xorg


---

### Post by Imexius on 2006-01-08
If that doesn't work try this:

sudo apt-get install xorg-driver-fglrx

Then:
> 
sudo pico /etc/X11/xorg.conf

Then
> 
Section "Device"
	Identifier	"Your Ati graphics card"
	Driver		"ati"
	BusID		"PCI:1:0:0"

Edit the ati part to fglrx then hit ctrl o, enter, then ctrl x

now type
> 
startx

If all else fails (do this only if you dont need to run things requiring 3dacceleration)
> 
sudo pico /etc/X11/xorg.conf


> 
Section "Device"
	Identifier	"Your Ati graphics card"
	Driver		"ati"
	BusID		"PCI:1:0:0"

Add Option "noaccel" below BusID

---

### Post by franklee on 2006-01-09
Thanks folks, Ill give that a go and get back to you!

---

