---
title: "Unable to save settings on Kubuntu live usb"
date: 2009-04-10
forum: General Help
---

### Post by Admiral Yi on 2009-04-10
Hello,
I have created a live USB of Kubuntu 8.10 using a program called Unetbootin. I used a standard Kubutnu live cd iso downloaded from the ubuntu website. 

My main reason for creating the live usb is to carry my files and my favorite operating system around with me. I would like to be able to change a few things, for example downloading firefox as a web browser. However, the live usb appears to be acting like a live cd. When I shut down, all changes are lost. Is this because I used a live cd image, is there a special one just for live usb? I know I can use a program in ubuntu to create a live usb, but I don't want to do this.

I have created a live usb before, of puppy linux. When I shut down in this one I get an option to save changes to the OS. Is there any way to get this on Kubuntu?

---

### Post by Admiral Yi on 2009-04-10
Bump

---

### Post by tea for one on 2009-04-10
There is a utility within Ubuntu (Administration > Create USB Startup Disk) which allows the inclusion of a "persistent" area on your USB stick to store settings and data.

I assume that there is a similar feature in Kubuntu.

Failing that, create an Ubuntu live USB and add KDE.

---

### Post by tea for one on 2009-04-10
I have just had another idea.

Boot up your live system
Add the utility "USB Creator" via Synaptic
Then use the utility to create a "live" Kubuntu with a persistent area.

You will, of course, need another USB stick to store your newly created OS.

I hope that this will work.

---

