---
title: "ATI Radeon x1900x Dual Monitor Configuration"
date: 2007-06-10
forum: Desktop Effects &amp; Customization
---

### Post by videocheez on 2007-06-10
I have  an ATI Radeon x1900x 512MB PCIe graphics card that has two monitors attached to it. In Windows, I have it set up so that my desk top is extended to  the second monitor so that i can drag things im not working on to the other side.  Can I do this with ubuntu and if so hwat approach do I take.  I tried right clicking the desktop but nothing happened.
Any help or guidance will be appreciated.

Thanks in advance,

VC

---

### Post by videocheez on 2007-06-10
Should this question be posted in another forum?

---

### Post by jorgepedret on 2007-06-13
I have the exact same question, the only difference is that I'm using an ATI Radeon XPRESS 200M 5955. Is it easy to set? or is at least 'setable'?

Thanks

---

### Post by kpolice on 2007-06-13
Idon't know which version of the ati drivers are you using but you can do it in the ATI Catalyst Control Center. 

If you don't have a shortcut type in the console **amdcccle**.

[ATTACH]35241[/ATTACH]

---

### Post by jorgepedret on 2007-06-13
I've been playing with aticonfig for a while, trying different configurations but All I got is cloning my two displays. (I'm working on a laptop, my laptop's monitor and an 19" LCD )

kpolice: Can you post a link where I can download that control panel, I did some research, and it says it's just available for Windows. And when I type amdcccle in my console It says command not found.

Thanks.

---

### Post by jorgepedret on 2007-06-13
Done!!

I made it with this package fglrx-control
Just type in your console:

# get-apt install fglrx-control

That will install the control panel for your ATI Video Card.
After it install it, you run the command 

# fireglcontrol

That will bring a window with different labels where you can graphically set what you want!

There was something else I did, but im not sure if it was that:
I added to the xorg.conf file the next line under the section "Default Layout"
Option "Clone" "off"

Try it out and let me know!

---

