---
title: "remix interface not very responsive"
date: 2009-04-27
forum: Desktop Environments
---

### Post by leandromartinez98 on 2009-04-27
I've installed the Remix 9.04 in a Asus eee 4G Surf. I was pleased
to see that everything was recognized, and working. The only problem
is that the remix interface is very slow, that is, it is very irresponsive, the mouse moves jumping, for example. At first I thought that the problem
was the speed of the netbook, but when I open any application, the interfacing with the application is perfect. Furthermore, if I change to the normal ubuntu interface, it becomes perfectly responsive. Therefore, the problem is indeed that the remix interface is slow.

I would be ok in changing to the normal interface, but then I get many issues, one of them being that the gnome panel is not automatically launch on boot (although if I boot into the remix interface and change to the normal one, it works fine). 

Therefore, my questions are two:

1 - Is it possible to tune the remix interface to make it more responsive (for instance, I don't care the icons to increase or rotate when the mouse approach them).

2 - If not, are there good chances that a normal ubuntu instalation works better (in terms correctly loading the gnome-panel, with the correct resolution) than the remix version? That is, is there any reason for the remix version being interfering negativelly in the normal interface, such that a normal instalation would behave better?

Thanks,
Leandro.

---

### Post by leandromartinez98 on 2009-04-27
Any idea?

---

### Post by PacSci on 2009-04-27
I have zero experience with the netbook remix, so I can't help you as far as tuning. However, the standard Ubuntu setup should work fine - a netbook is still a computer, after all, and I have read other threads about people using standard Ubuntu on their netbooks.

---

### Post by Aearenda on 2009-04-27
Make sure you have not turned visual effects on (in preferences->appearance) since this gives the slowness you are describing when using the netbook-launcher. 

Also, if you have turned Metacity compositing on, turn it off (you will know what this is if you have, so ignore it otherwise!).

---

### Post by leandromartinez98 on 2009-04-27
Thanks guys. I found the issue, it is a reported bug, and it
has a solution:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/349314](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/349314)

The patched kernel solved my problem.
Leandro.

---

### Post by kasimyro on 2009-04-29
Sorry, I am a beginner...
How do I apply patch to solve it?

---

### Post by leandromartinez98 on 2009-04-29
> **kasimyro said:**
> Sorry, I am a beginner...
How do I apply patch to solve it?


In simple terms:

1 - Open a terminal.

2 - Download the patched kernel:

wget [http://people.ubuntu.com/~apw/lp349314-jaunty/linux-image-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb](http://people.ubuntu.com/~apw/lp349314-jaunty/linux-image-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb)

3 - Install the patched kernel 

sudo dpkg -i linux-image-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb

4 - reboot

Done.

My netbook is a Asus eeePC 701 4G Surf. I cannot guarantee that it will work on other models.

Leandro.

(Ps. In my case, I'm not sure why, the package manager complained about
unresolved dependencies on installed packages, which are solved using:

sudo apt-get -f install

But this should have nothing to do with this problem.)

---

### Post by leandromartinez98 on 2009-04-29
> **kasimyro said:**
> Sorry, I am a beginner...
How do I apply patch to solve it?


In simple terms:

1 - Open a terminal.

2 - Download the patched kernel:

wget [http://people.ubuntu.com/~apw/lp349314-jaunty/linux-image-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb](http://people.ubuntu.com/~apw/lp349314-jaunty/linux-image-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb)

3 - Install the patched kernel 

sudo dpkg -i linux-image-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb

4 - reboot

Done.

My netbook is a Asus eeePC 701 4G Surf. I cannot guarantee that it will work on other models.

Leandro.

(Ps. In my case, I'm not sure why, the package manager complained about
unresolved dependencies on installed packages, which are solved using:

sudo apt-get -f install

But this should have nothing to do with this problem.)

---

