---
title: "Can't get 6.06.2 Xorg to run on PowerEdge 2950"
date: 2008-02-07
forum: Dell  Ubuntu Support
---

### Post by danfluidmind on 2008-02-07
I installed from the 6.06.2 Server CD and everything installed fine on a PowerEdge 2950. Then, after installing SSH, I did "apt-get install ubuntu-desktop". After it finished installing I rebooted. Once it finishes booting the screen went blank and the keyboard locked up. I can't even hit CTRL-ALT-F1 to get to a virtual terminal. Can't do a think at the console. Then I SSHed into the machine and ran top. xorg was taking up to 98% processor time, and I was unable to kill it, even with "kill -KILL". So I removed gdm from the runlevel and rebooted. Now it is running fine, but I can't boot into gdm.

So I started from scratch and completely reinstalled, thinking maybe something just went wrong. I got exactly the same result. I've looked through the logs and can't find anything in them. I had hoped that xorg was writing something to its log while it was taking 98% of the CPU time, but there wasn't anything there.

Has anyone been able to get 6.06 with Xorg running on a PowerEdge 2950?

Thanks
--Dan

---

### Post by faulkes on 2008-02-07
If I recall correctly there are known issues with X on the 2950 and the supplied video card.

I believe dell offers some binary rpms of the display drivers (and you would likely have to configure xorg.conf manually.

Faulkes

---

### Post by sr20ve on 2008-02-07
You might want to try setting RenderAccel to true in your xorg.conf.

Option "RenderAccel" "TRUE" 


What video driver is your xorg.conf using?

---

### Post by danfluidmind on 2008-02-07
Section "Device"
        Identifier      "ATI Technologies, Inc. ES1000 (RN50)"
        Driver          "ati"
        BusID           "PCI:16:13:0"
EndSection


Here's something odd: for some reason there are three sections in xord.conf for a Wacom tablet, which, of course, this server does not have.

---

### Post by danfluidmind on 2008-02-08
Thanks for the suggestions guys. The RenderAccel didn't have any effect. And I tried installing the drivers from Dell and they didn't change anything either.

---

