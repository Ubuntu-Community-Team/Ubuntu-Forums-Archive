---
title: "NVIDIA-module won't load"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Mastodront on 2005-10-13
I've just finished installing Breezy and I just love it :)

But I've bumped into some problems :( I've installed the nvidia-glx with Synaptic and run "sudo nvidia-glx-config enable" as usual but when I made a reboot it "failed to load nvidia-module" or something. I the ran "sudo dpkg-reconfigure xserver-xorg" and made all the changes but the problem remained :(

I have a 6600GT and it worked just fine in Hoary. My brother who also have a 6600GT  seems to experiencing a similar problem ...

Anyone who have a solution

---

### Post by SeanCallan on 2005-10-13
I'm interested in seeing the replies to this, I can't get my resolution any larger on my  Nvidia..

---

### Post by KingBahamut on 2005-10-13
can you modprobe as root for the nvidia driver?

---

### Post by Mastodront on 2005-10-13
No, this is the result :(

FATAL: Module nvidia not found.

---

### Post by belboz on 2005-10-13
Ditto for me.

On Hoary I would just install the nvidia packages and then do a 

sudo nvidia-glx-config enable

On Breezy after installing the nvidia packages, and running the above command I get no output from the command.  On Hoary I would get a message letting me know I had to restart the xserver.

---

### Post by rjwood on 2005-10-13
I had to make sure all the repositories were checked before nvidia-glx with settings would work properly. I hope this helps

---

### Post by SeanCallan on 2005-10-13
I went ahead and got the module for 7667 installed and I enabled it AND restarted my X server.  However, I still don't have any resolutions over 1024.

In Fedora and Windows I used to 1280.

Any ideas?

---

### Post by Mastodront on 2005-10-13
Thanks but that's already done. All of the repositories have been uncommented except the backports which gave me many errors when i ran "sudo apt-get update" a couple of times ...

Edit: this was a reply on rjwoods message

---

### Post by rjwood on 2005-10-13
[quote=Mastodront]Thanks but that's already done. All of the repositories have been uncommented except the backports which gave me many errors when i ran &quot;sudo apt-get update&quot; a couple of times ...

Edit: this was a reply on rjwoods message[/quote]You may want to see the new guide in system>help

---

### Post by darkmatter on 2005-10-13
Sean, you need to
```
sudo dpkg-reconfugure xserver-xorg
```

To get the resolutions you need.

Curing the configuration, you just need to make sure that the resolutions you desire are selected, and that the horizontal and vertical refresh rates are correct. when you restart X (Ctrl+Alt+Backspace), every thing should be the way you want it.

---

### Post by somuchfortheafter on 2005-10-13
install the k7 or the 686 kernel with all the generic packages, headers, etc then remove the 386 kernel and all other 386 kernel packages as well as the nvidia stuff.
reboot reinstall nvidia, edit your xorg.conf file then ctrl-alt-backspace and you should be set.

---

### Post by Mastodront on 2005-10-13
Aah, it seems it wasn't such a big mystery after all :)

I had installed the k7-SMP-kernel (I have a x2 AMD64) but I didn't install the restricted modules for it. Now it works even better than hoary (smp didn't work with the 2.6.10-5-kernel for me).

Anyway, thanks for your time :)

---

### Post by belboz on 2005-10-13
According to apt-get I have the latest nvidia-glx and nvidia-settings installed.

When I do an "sudo nvidia-glx-config enable" I get no messages.

In regards to having repositories all on.  I use the synaptic manager from the admin menu.

When I go into the repositories section of it.

I get the CD restricted repo, ubuntu 5.10 binary and souce (restricted), 5.10 updates binary and source(restricted), 5.10 security binary and source (restricted) and 5.10 binary (universal).

When I search for NVIDIA in the advanced portion of synaptic I see the following installed.

linux-restricted-modules 2.6.12.4-11 (386)

nvidia-glx 1.0.7667-0ubuntu25

nvidia-settings 1.0-3ubuntu6

nvidia-kernel-common 1.0.7667+1

xserver-xorg-driver-nv 6.8.1-77

This worked so well in Hoary.  Any thoughts?

---

### Post by Drakx on 2005-10-13
Im having the same problems too this box has a geforce 2 :S

---

### Post by somuchfortheafter on 2005-10-13
honestly if you are going to use the 386 kernel because you have too i wouldnt worry with the nvidia drivers, trust me they work with the 686 and k7 kernels as im using it now.

---

### Post by Drakx on 2005-10-13
OK, so i just install the 686 kernel ? then reinstall nvidia-glx ?

---

### Post by SeanCallan on 2005-10-13
Aweosme guys, I got mine working!  Thanks

---

### Post by Drakx on 2005-10-13
How ???

---

### Post by Drakx on 2005-10-13
OK,

Any one having problems with the 386 kernel install nvidia-glx-legacy drivers then sudo nvidia-glx-config enable you'll see the message you use to get for 5.04 (hoary) Ctrl+Alt+backspace see nvidia logo jobs done!

---

### Post by belboz on 2005-10-13
Hmmm.  No luck for me.

I tried installing the 686 kernel, removing the NVIDIA drivers, and reinstalling them with any 686 options if available... No go.

I tried installing the legacy option, it wants the 386 kernel, so I didn't go that route.

The system I am using is a Celeron 366 with a TNT card.  Worked great in Hoary with the nvidia drivers loaded.

Sigh.....

Oh well, I gues I will give Slackware 10.2 a try.  It shouldn't be this hard to get the nvidia drivers loaded.

---

### Post by Drakx on 2005-10-13
try installing the 386 kernel it does work!

---

### Post by belboz on 2005-10-13
I fixed it and was able to stick with the 686 kernel!!!

From what I found on here reading about the nvidia drivers the latest ones don't work with older nvidia cards.

My card in my Linux box is an older TNT card (Riva).  So I removed all the nvidia stuff and installed the nvidia legacy drivers.  Rebooted and ran the nvidia-glx-config enable and everything is working now.

Thanks everyone.

---

### Post by spockrock on 2005-10-19
I was having the same problem but, I updated to the 686 kernal, then rebooted, then installed the nvidia-glx-legacy drives, and then reboot, and then used the nvidia-glx-config enable, and it works like magic

btw I am running a riva 2 tnt card..........

---

### Post by RAOF on 2005-10-20
[QUOTE=belboz]...
From what I found on here reading about the nvidia drivers the latest ones don't work with older nvidia cards....
[/QUOTE]
Yes indeed!  The nvidia-glx drivers **no longer support TNT cards**.  I'm not sure where the cutoff is, but if you've got something older than a geforce, the drivers you want are nvidia-glx-legacy.

---

