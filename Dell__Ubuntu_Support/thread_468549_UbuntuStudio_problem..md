---
title: "UbuntuStudio problem."
date: 2007-06-09
forum: Dell  Ubuntu Support
---

### Post by dwink1217 on 2007-06-09
Okay guys. heres the deal. I've been running feisty fawn for a few weeks on my Dell Dimension 8300.

Everything was going nicely, until i see ubuntu studio.

being an active musician, i use [http://anakjakarta.wordpress.com/2007/05/25/my-feisty-fawn-upgraded-to-ubuntu-studio/](http://anakjakarta.wordpress.com/2007/05/25/my-feisty-fawn-upgraded-to-ubuntu-studio/) this guide to update my computer.

BUT. when i reboot the computer, the "loading" screen shows up, but right before it goes to the screeen i actually type in my username and password i get a "Ubuntu Studio failed to start the x server" error. I've tried to "reconfigure" it with no luck. Maybe i am doing something wrong?

I'm running a Dell Dimension 8300 as stated above, it has Nvidia Geforce some number graphics cards, and feisty fawn works perfectly. right now im running this from the feisty fawn boot disk.

any ideas/help would be greatly appreciated. I'm pretty new to linux though so please explain how to do certain things.

id like to get this problem solved as quickly as possible as this computer is shared by the family, and at the moment nobody can use it.

---

### Post by dwink1217 on 2007-06-09
looking a little further, it has a nvidia geforce fx 5200. i got something looking somewhat like this...

FATAL: Error running install command for nvidia.
Failed to load the nvidia kernal module
Screen(s) found, but none hasve a useable configuration

---

### Post by ZipoTe on 2007-06-09
post your xorg.conf

---

### Post by shen-an-doah on 2007-06-09
Were you using the binary nVidia driver on your old Feisty install? If so, you'll need to install it for the new low-latency kernel.

You should still have your old Feisty kernel ("generic" rather than "low-latency") in your GRUB menu. Try booting into that and see if it works. If so, you'll need to go to synaptic and install "linux-restricted-modules-low-latency".

---

### Post by dwink1217 on 2007-06-09
> **ZipoTe said:**
> post your xorg.conf

well, im kind of running up and down stairs between computers. i dont really have a way to get that here.

---

### Post by dwink1217 on 2007-06-09
> **shen-an-doah said:**
> Were you using the binary nVidia driver on your old Feisty install? If so, you'll need to install it for the new low-latency kernel.

You should still have your old Feisty kernel ("generic" rather than "low-latency") in your GRUB menu. Try booting into that and see if it works. If so, you'll need to go to synaptic and install "linux-restricted-modules-low-latency".

i think i crapped something up trying to reconfigure xserver for studio, because now THATS not booting either. but it used to.

---

### Post by dwink1217 on 2007-06-09
actually i take that back. theres TWO other "generic" kernals on the grub menu. The very bottom one worked. and im trying what you said right now.

---

### Post by tk471 on 2007-06-09
I discovered something similar, only in reverse (on my Inspiron 8100, I tried to boot to the 'generic' kernel, and it didn't want to start X for probably a similar reason).    I originally had Feisty Fawn standard installed, and I did a clean install of Ubuntu Studio.   I'm pretty sure, that even if you couldn't get to the GUI with the 'generic' kernel, you could do something like this from command line when you try to boot to the 'low-latency' kernel:

#sudo apt-get install linux-restricted-modules-lowlatency
(it will then install the needed bits)
#sudo reboot

Good Luck!  -Pete
(also in a band, shameless plug .. [http://myspace.com/amayonnaisegraveyard]("http://myspace.com/amayonnaisegraveyard")

oh, looks like you already are on your way thru the 'generic' kernel, I was a little slow on my response :)

oh, and another link with info you may or may not need:
[http://ubuntuforums.org/archive/index.php/t-448003.html]("http://ubuntuforums.org/archive/index.php/t-448003.html")

---

### Post by shen-an-doah on 2007-06-09
> **tk471 said:**
> (also in a band, shameless plug .. [http://myspace.com/amayonnaisegraveyard]("http://myspace.com/amayonnaisegraveyard")

If we're doing shameless plugs, there's a couple of links in my sig ;)

---

### Post by dwink1217 on 2007-06-09
okay, downloading the low latency module fixed it. thanks a bunch.

---

### Post by shen-an-doah on 2007-06-09
> **dwink1217 said:**
> okay, downloading the low latency module fixed it. thanks a bunch.

No probs. It's what we're here for :D

---

