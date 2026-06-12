---
title: "White Screen of Death again?"
date: 2009-10-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nmrcy on 2009-10-10
i have installed 9.10 karmic beta on my studio 1535 and i couldnt even use it becouse of the white screen of death in 9.04 there is no problem i hope it will be solved. Any1 have this problem too?

---

### Post by mrBallistic on 2009-10-11
i've run  into the same issue. i'm going to wipe the drive and do a clean install of 9.10 and see if that fixes anything. i'm hoping that there's some setting in compiz that is breaking things.

also, my trackpad isn't working, but that's the least of my issues right now. 

(it would be a bad bad thing to release 9.10 with this bug intact, as it'll render many a dell useless)

---

### Post by sthacher on 2009-10-11
I had to boot with vga=792 its the same problem that dells have always had with Linux. they use cheap screen controllers and it pushes the wrong resolution. But of course I cant figure how to do this after install, this new grub is kind of weird.....I haven't installed ubuntu in a little while.

turns out that its just the installer that I an boot to with vga command but with the new kernel seems that gfxpayload=1024x768 has taken the place of the vga command. This option will not work from my screen. I can hear it boot all the way up I just cant get the correct configuration its a dell studio 1535 with intel video card I will keep trying today and post my results if any.

---

### Post by hasagar on 2009-10-31
Hi,


I also have the same problem. When I log in in the new kernel, i can hear the sound of starting. But it is a white screen. I can see nothing. Same thing happened for recovery mode.

If I login using the previous kernel, I can see everything but mouse does not work.

Please help me. I dont want to install it again.

Thanks.


--Him

---

### Post by nmrcy on 2009-11-11
Any solutions?

---

### Post by AklBlue on 2009-11-18
I'm having similar issues .. anyone with a solution?

Symptoms for me are:
- Cold boot (sometimes but not always) directly into white screen after GRUB.
- Leaving computer idle for around 30 minutes .. like when going into powersave mode will go white screen.

Computer is an Acer Aspire with Intel X3100 graphics.

Thanks in advance.

---

### Post by teward on 2009-11-18
I don't have a solution for you, but you'll just have to wait for someone to come along who does.  Don't keep posting asking if there are solutions, if there are, someone will come and post one.

---

