---
title: "Assorted Problems"
date: 2005-12-15
forum: General Help
---

### Post by Progressive on 2005-12-15
I just downloaded Kubuntu 5.10 for my Sony VAIO FS Laptop. I dual booted it with Windows XP Home. Nobody has even viewed my post there, so I am posting here.

I am getting some video problems. Everything turns like static (as in television static) among other similar weird problems until I refresh the desktop, but then starts turning to static again.

Is that a driver problem? I am thinking it might be a booting/partitioning problem because I noticed somewhere in the static that the words "Windows Saving System Settings" were clearly visible.

A side problem is that I havent been able to figure out how to set Windows back as the default in the boot loader or change the amount of time before it bypasses the selection process. I didnt have these problems with the Mandriva boot loader, plus it looked prettier. Maybe I should revert to the old boot loader?

A third problem is that when I set it to shutdown or restart, it gets almost all the way to shutting off or restarting, but does not actually do it.

Another thing you should be aware of is that I previously had Mandriva 2005 installed on the partition. It is possible that I did not format the partition correctly. Would all these be symptoms of if I wrote Kubuntu on top of the Mandriva partion without formatting first?

---

### Post by tabinin on 2005-12-15
> **Progressive]I just downloaded Kubuntu 5.10 for my Sony VAIO FS Laptop. I dual booted it with Windows XP Home. Nobody has even viewed my post there, so I am posting here.[/QUOTE]

Let's see if we can give this a start.  We will need some help from some other forum members  said:**
> I am getting some video problems. Everything turns like static (as in television static) among other similar weird problems until I refresh the desktop, but then starts turning to static again.

Is that while you start Kubuntu or Windows?

> Is that a driver problem? I am thinking it might be a booting/partitioning problem because I noticed somewhere in the static that the words "Windows Saving System Settings" were clearly visible.

I think you have a ghost...  The exorcism requires you to delete the Windows install and only run Kubuntu.  Just kidding, but this is weird.

> A side problem is that I havent been able to figure out how to set Windows back as the default in the boot loader or change the amount of time before it bypasses the selection process. I didnt have these problems with the Mandriva boot loader, plus it looked prettier. Maybe I should revert to the old boot loader?

The easiest way I have seen to do this is to use Webmin (with the webmin-grub module).  Of course, you need to ge Webmin installed and search the forum for how to get a root login to it.


> A third problem is that when I set it to shutdown or restart, it gets almost all the way to shutting off or restarting, but does not actually do it.

I believe this is know bug in Kubuntu/Ubuntu.  Upgrade to KDE 3.5 and the problem will go away as far as I have experienced.

> Another thing you should be aware of is that I previously had Mandriva 2005 installed on the partition. It is possible that I did not format the partition correctly. Would all these be symptoms of if I wrote Kubuntu on top of the Mandriva partion without formatting first?

Sounds like a re-install might be in order.  Blow that Mandriva partition away and start from scratch.  I am a former Mandrake/driva user and it is a great distro, but the (K/X/U)buntu line-up is the cat's meow.  This forum has provided all the answers I couldn't get with Mandriva.  It's free and it's *hot*.

---

### Post by RAOF on 2005-12-15
I'd suspect that the graphics corruption is due to display drivers.  It sounds like the same problem as another person had today.  Since they haven't got back, I 'll ask you instead:   What sort of graphics hardware does the VIAO have?  It will almost certainly be one of these three:  nvidia, ati, intel.  What we do next depends on what the hardware is.  

Or, actually, you could try running "sudo dpkg-reconfigure xserver-xorg" and selecting the "vesa" graphics driver when asked (all the other questions can be left on the defaults, unless you know better).  This will select the vesa X driver - slow but almost guaranteed to work.

As for changing the boot options, the file you need to edit is /boot/grub/menu.lst.  Or, you could alternatively install bum (the Boot Up Manager).  Just search for "bum" in synaptic, and you should be able to change those options with it.

---

### Post by Progressive on 2005-12-16
I have a Nvidia graphics card....

also the display problems are with Kubuntu, not XP. Sorry for the confusion

---

### Post by RAOF on 2005-12-16
Since it's an nvidia card, you'll currently be using the default open-source nv drivers.  I've had (the same sort of) problems with these.  Try the nvidia drivers, by typing the following commands into a terminal window (like Konsole):

```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```

Now restart X (log out, and press Ctrl-Alt-Backspace).  You should
1) Get an "nvidia" splashscreen
2) Not have any more graphics corruption ;)

---

### Post by Progressive on 2005-12-16
thx for the help... I am working on it. Just so you know, I completely reinstalled and reformatted since my first post and I am having the same problems. In fact I can see the windows logo now. Craziness

---

### Post by Progressive on 2005-12-16
It worked! I am not having the problems anymore. I will still need to update my kde to get rid of the shutdown problem, but other than that I am good to go

thank you very much

---

### Post by RAOF on 2005-12-16
Another problem solved by the awesome might of the **nVidia Graphics Drivers**!

Seriously, maybe I should put that in my sig :)

---

