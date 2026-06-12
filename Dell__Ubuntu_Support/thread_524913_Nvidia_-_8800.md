---
title: "Nvidia - 8800"
date: 2007-08-13
forum: Dell  Ubuntu Support
---

### Post by newttyy on 2007-08-13
Hello there,

I'm new around here ... I'm actually a new user of Ubuntu 7.
I was quite exited about trying it out, but unfortunately it looks like we had a bad start ...

I'm using a Dell XPS 710 with a NVIDIA GeForce 8800 GTX at 768MB and a PhysX by Ageia.

I guess that says pretty much eh :)!? I've been looking around this forum, before posting this thread and did tried two of the solutions, but none actually worked (one with changing the nv to nvidia from xorg.conf ... and the other one by doing the "sudo dpkg-reconfigure xserver-xorg"). I do not have the links for those solutions anymore.

Is a royal pain ... I'm using a 1920x1200 widescreen monitor and my maximum resolution si 1024x768 ... :( ...

I was wondering if this is something specific to my machine and if anyone of you have a solution for it? That actually works :).?

I really like Ubuntu and I could very easily fall in love with it if I could just found a solution to this problem ... or at least when Ubuntu might have an update for this driver? Anything ... 

I'm not really a Linux user, so if anyone care to explain, please go a little bit in more detail ... it would be appreciate it.

Thanks to all that will try and help me out!!!

---

### Post by erimar77 on 2007-08-14
Can you click 

System - Administration - Restricted Drivers Manager

Then check the box for Nvidia accelerated graphics driver.. give that a shot.  Reboot probably

---

### Post by newttyy on 2007-08-16
Hi erimar77,

I did that the first time and X didn't start anymore. And at that point I tried the two tutorials I was talking about, but nothing ... 

I had to re-install Ubuntu just for that. As a weird thing, it wasn't even let me restore the old xorg.conf (for whatever reasons).

Anything else that might help me?

I have downloaded the NVIDIA-FreeBSD-x86-1.0-9755 from nvidia site - the drivers for linux version they said ... but I honestly don't know if it will help me out and most worst (for me), is that i have no ideea how to install drivers on Ubuntu :confused: :(...

---

### Post by sc3252 on 2007-08-16
lol, reinstalled because x wasnt starting?  What you should have done was post here before wasting more of your time.  Another thing, dont use ubuntu's restricted drivers, they suck. Also you downloaded the wrong drivers off of the nvidia site, you want the linux drivers.
download [http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html) to your desktop

What you should do next is install the build essential
```

sudo apt-get install build-essential

```
also I cant remember if build-essential installs the header files you need to build the nvidia drivers.  check synaptic package manager for kernel header, after that you will see a list of different kernel headers.  if you dont know what kernel you have installed open another command terminal and type in uname -r, it will tell you the kernel.

after that we are going to need to kill x to install the drivers.  to kill x you first press control+alt+F1  to bring up command line, type in your user name and password and type this
```

sudo killlall gdm

```
You have now killed x.

now you are going to have to install the drivers.  
```

cd Desktop
ls

```
after you type in ls you should see NVIDIA-Linux-x86-1.0-9755-pkg1.run(I have older drivers, so dont worry if it says 1004 or something)

now type in this

```

sudo sh NVIDIA(then press the tab button, it will fill in the rest)

```
after that it will start the install proccess, it will install everything and ask you to change xorg.conf file.  click yes and continue.  now type in 

```

sudo gdm

```
x should start up and you should have your native rez

if things go wrong, and x doesnt start do this.

```

sudo nano /etc/X11/xorg.conf

```

look for

```

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GT]"
    Driver         **"nvidia"**
EndSection

```

change the bold to vesa, make sure the quotes stay in place, so it should look like this 

Driver       "vesa"
after that type in control+x and save.

make sure to post the error message you have if it doesnt work.  I hope what I posted helps you in some way, and dont get to discouraged in how long this is, just print it out and follow it and everything should work.

note:  there could be a misspelling on one of my commands, if anyone see's any please correct it, thanks.:guitar:

---

### Post by newttyy on 2007-08-17
Hi sc3252,

[-X Don't laugh at me man :lol:. I said I am not a Linux person :(.

thanks for the tips. I will try everything you just said in there and I'll let you know if it worked. I just hope you wrote the commands right :tongue:.

To be continued ...

---

### Post by meowsqueak on 2007-08-18
I also have an nvidia 8800 GTX and it appears to me that the nvidia restricted driver in Feisty does not recognise this card. The driver loads but when X tries to start it throws up a bunch of 'unrecognised hardware' errors. X no go.

Works OK with the 'nv' driver however.

EDIT: another post I just read suggests installing the nvidia-glx-new package for Nvidia 8000 series cards.

---

### Post by cooldudejz on 2007-08-18
hey newttyy try doing a search for the nvidia envy script. it is a script that will download the right drivers for your video card and install them for you. here is the link to the script [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by BadTimmy on 2007-09-03
**Bravo sc3252!**

Your guidance worked perfectly where others missed completely.  Thank you for your help and thank you for making it easy for us noobs to understand.

---

### Post by saru411 on 2007-09-03
newbies should try envy....[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

this will do all the work for you

---

### Post by ircarrascal on 2007-09-04
Yes, try Envy; it worked great for me on a XPS410, Nvidia GeForce 6700. I tried to edit the xorg.config and tons of other tricks I found online but none worked. Envy did. Give it a try!

---

