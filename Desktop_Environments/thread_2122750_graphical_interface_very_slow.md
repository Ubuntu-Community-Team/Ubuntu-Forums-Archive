---
title: "graphical interface very slow"
date: 2013-03-06
forum: Desktop Environments
---

### Post by gvr2600 on 2013-03-06
Hello Guys,

I wanted to ask you if you can help in regards to my issue. I have a Lenovo g580 core i3 with intel vga and nvidia gt630M with CUDA tech.

I have tested this laptop on: Fedora/Ubuntu 12.10/12.04LTS/Linux Mint/xubuntu and ubuntu server+xfce installed. Graphical Desktop manager only unity/gnome and xfce.

After some tests, I said that it is not worth trying anymore to make the nvidia work. So I decided to keep using only the intel vga. It seems that also this is to much to ask for.

My issue:

-fresh install every time
-update/upgrade packages with latest updates, nothing else
-when moving windows from left to right, I can see the lines from the windows decomposing, looks like poor rendering. - what I see is like you are filming a crt monitor with your camera
                  * slow youtube in full hd - same as the mentioned behavior 
                  * avi/mkv/mpeg video same as the mentioned behavior
                  * functionality is normal, no unusual slow behavior, except gui rendering.

The only distro working correctly in gui was Ubuntu 12.10 Unity. After I installed everything, I did reboot after each software installation to verify if there are problems. It worked very nice, smooth, no issues. And the next day it started to work like crap after doing the security updates from the packed manager.

I am not at the end of my nerves and power and force :)) I think this is a driver issue for the intel adapter

Currently I have xubuntu 12.10 with same behavior. 

I just want to move my last device running windows to linux. 

Thank you in advance.

---

### Post by black veils on 2013-03-06
have you tried the previous kernel version(s)? as you say it is a security update which changed it to bad behaviour, which means it was a kernel update, and that contains drivers.

so when booting the computer, press and hold the Shift key to show the grub bootloader menu. the newest kernel will be at the top, boot into a lower one and see how it is.

if you find an appropriately working kernel, you can use grub customizer to choose it as default for every boot.

---

### Post by gvr2600 on 2013-03-06
> have you tried the previous kernel version(s)? as you say it is a security update which changed it to bad behavior, which means it was a kernel update, and that contains drivers.

Yes, before I did the upgrade :))) and it worked nice. But that issue, I decided to try more disctros in order to find one suitable for me, because I was a little unsure about ubuntu at that time. I had my doubts about what will happen on the next update :) 

Now I am running the same kernel as I was then, but xfce instead of unity. on the first installation of xubuntu I had the same kernel as before and it was not working as ubuntu 12.10 with unity.

I found a nice blog post that's referring to the intel driver installation:

 [http://sagark.org/optimal-ubuntu-graphics-setup-for-thinkpads/](http://sagark.org/optimal-ubuntu-graphics-setup-for-thinkpads/)

I will try this after I will get home. I will let you know how it goes .

If somebody had the same issues with the intel vga, please reply and I will test it with pleasure.

---

