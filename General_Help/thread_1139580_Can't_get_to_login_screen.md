---
title: "Can't get to login screen"
date: 2009-04-27
forum: General Help
---

### Post by Colinho on 2009-04-27
Hi, I'm having a little trouble. I was getting undefined video mode upon booting into Ubuntu 9.04 so I searched for some help and I found that running an aticonfig command (I can't remember it exactly) might help so I tried that. It said I needed to get an ati fglrx driver, and I remembered a message that I got upon installing 9.04 a week or two ago about removing the fglrx package on the upgrade. So I confirmed it and it downloaded and installed the package. I restarted and I got grub and the loading screen, but after that I got some graphical corruption (is that the term? - coloured distorted lines) and could not do anything. I decided to leave this for today, and today I tried choosing a video mode from the list and seeing if that would work. Now I do not get the distorted lines - but the screen is completely black.

With my limited knowledge of Linux, I am thinking that doing a non graphical boot and then uninstalling the fglrx package might have something to do with the solution, but as I said my knowledge is very limited :confused:

I am pretty sure that the problem has to do with the ati fglrx driver or the aticonfig command.

My Graphics Card is an ATI Radeon X1650, if that helps.

Any help would be GREATLY appreciated. I do have a 8.04 CD and I have a separate / partition, but I want this to be a last resort. I wouldn't lose any important data but to be honest it would be a pain to upgrade back to 9.04.

Thanks in advance for any replies.

---

### Post by Legace on 2009-04-27
The new FLGRX driver is not compatible with your graphics card. You need to use the opensource radeon driver instead.. To remove the FGLRX driver:

> **gocek said:**
> Reboot PC and select "recovery mode" in boot-manager (GRUB) and then go for "root shell" option. 
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```


then type
```
exit
```

and select "resume normal boot"

This should get you back to your Ubuntu desktop, but running on default drivers.

---

### Post by Colinho on 2009-04-28
Sorry for the late reply, just got back from school.

Thanks a bunch - to you and the original poster! I was thinking something like that would be the solution but I thought that experimentation was kinda what caused the problem so I shouldn't use experimentation as the solution. It's pretty much back to normal now, I reconfigured xorg.conf, and then restored a backup later.

So the ati --initial (I think thats what it was now >.<) was how NOT to solve the problem, do you (or anyone else) have any advice?

When I boot I get this message:

```
Undefined Video Mode number:318

Press <Enter> to see video modes available, <Space> to continue or wait 30 seconds
```

None of the available video modes are my resolution (1440x900).

Thanks again :)

---

