---
title: "Graphics card to run DirectX 11?"
date: 2014-11-08
forum: Gaming &amp; Leisure
---

### Post by Panawe on 2014-11-08
I've just been given, as a gift, the game Alien Isolation. When I asked for it I didn't read the small print and now the game won't run under Window$ 7 because the graphics card I have doesn't support DirectX 11.

It is an easy matter to buy a card that does, but I want to anticipate problems with Ubuntu and choose a graphics card that will let me run the game when I'm in Window$ but not give me trouble when I'm using Linux (which I do most of the time).

TIA

---

### Post by oldrocker99 on 2014-11-08
Any nVidia card from the 400 series on supports DirectX 11, and you're beter off using Linux if you go nVidia. The card I have is a 750ti, which you can get for $150 or less if you shop around, and uses less power than the PCI-Express slot offers, which is 75 watts. This means it doesn't get as hot as earlier models, and it doesn't need a separate power input.

---

### Post by Panawe on 2014-11-08
Thanksoldrocker - I'm looking at a 750ti on ebay.

---

### Post by oldrocker99 on 2014-11-08
Glad to hear it. Make sure you install the latest nVidia driver!

---

### Post by Panawe on 2014-11-09
Okay, I've ordered a Palit NVIDIA GeForce GTX 750 Ti 2GB Boost Graphics Card (hope that's right?).

When I install it what is the best way to go about installing drivers or will ubuntu do that automatically? My current card is nVidia so I hope I don't get a black screen!

---

### Post by oldrocker99 on 2014-11-09
When you boot, you will not see a black screen. If you select **Additional Drivers**, you'll see more than one nVidia driver. Select the highest-numbered one, let it install, and then reboot (one of the few times you have to reboot in Linux; the other times are when a new kernel is installed, and when certain programs, like ureadahead, which have to run on startup, are installed), and you should be all set. Use nvidia-settings to select your desired resolution, etc.

---

### Post by Panawe on 2014-11-09
Cheers.

How do I find "Additional Drivers"?

Edit

Found that. I discover I'm not using nVidia drivers at all but "X.org.X.server - Nouveau display driver"! Does this matter? Several nVidia drivers are listed.

---

### Post by mastablasta on 2014-11-10
yes, it matters. nouveau are opensource drivers. they are good but nearly not as good as the ones packed by nVidia.

---

### Post by Panawe on 2014-11-10
So when I install the 750ti it will work from the off?

---

### Post by dannyboy79 on 2014-11-11
it will work immediately yes, whether noevou will support it or it will fallback onto vesa you'll have a graphical desktop at least until you can choose the additional drivers. 1 million dollar question though: did you first ensure your pc has a PCIe slot?

---

### Post by Panawe on 2014-11-11
Had me panicking there for a moment...

*2 PCI-E 2.0 x16 interface for ultimate graphics performance*

Should be okay?

---

### Post by dannyboy79 on 2014-11-11
if that's what your motherboard says than you'll be good to go. just seemed weird your current video card doesn't support directX11 AND is PCIe already. anyway, you should be good.

---

### Post by Panawe on 2014-11-14
Card installed and all seems to be functioning well.

One little mystery (to me) - when I look at System Settings and Additional Drivers, there's nothing in the box! No Nvidia, no Nouveau, nothing!

I'll mark this as solved later today.

---

### Post by oldrocker99 on 2014-11-14
Here's how to get the latest nVidia drivers. Open a terminal:
```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-graphics-drivers-343 dkms
sudo shutdown -r now
```
The first line adds a repository with the latest drivers.
The second line refreshes your list to include the repository on the first line.
The third line installs the latest driver, and dkms, which will hook the driver to a new kernel if it installed, so you don't need to install the driver again.
The fourth line reboots your system, which needs to be done to make sure the driver will load.

Good luck, and post if you have any problems.

---

### Post by Panawe on 2014-11-16
Thanks for all your help, Oldrocker, but I'm going to leave the situation as it is.
I don't use Ubuntu for gaming so my graphics requirements aren't too high end and I'm pleased with the way it's working at the moment.
Maybe in the future :)

Thanks again.

---

