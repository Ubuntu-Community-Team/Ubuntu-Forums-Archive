---
title: "Vncserver using Unity"
date: 2012-05-07
forum: Desktop Environments
---

### Post by ttr77 on 2012-05-07
Hi,

I just installed Ubuntu 12.04 and I can't get the vnc4server to work with Unity.
Been using vnc4server with Ubuntu 10.04 and gnome for about 2 years with success.

The Problem is that when connection to Vncserver with vnc client it will only show the desktop.. no bars or applications to access.
I tested by installing gnomer-core and got it working that way but.. but it messed the unity login screen and became a bit slower so I don't want to go there.

Any idea how to get vncserver to work with Unity successfully. 

Regards,

Toby

---

### Post by ttr77 on 2012-05-07
Anyone?

---

### Post by ttr77 on 2012-05-08
Are there any ohter remotedesktop application that you would recommend other than Vnc4server

---

### Post by GordonF on 2012-05-09
Same problem. Regretting upgrading to 12.04 right now because I can't use my desktop remotely from my iPAD so paying for  a cloud server that isn't working :(
Any help/suggestions would really be appreciated and save me a load of traveling and I really enjoy unity but would prefer to enjoy it everywhere.

---

### Post by GordonF on 2012-05-09
:lolflag: Search for 'remote' in your dash search. Its dog slow though even over high speed connections 10mb+

---

### Post by QIII on 2012-05-09
A recommended solution might be to get away entirely from the slow and insecure vnc technology entirely and go to nx.

Nomachines produces results on par with Windows RDP, but it requires ssh and is not trivial to set up.  And don't use version 4 yet.  It's sub Alpha and I found it to be a basket case while I was testing it.

One thing about your Ubuntu host is that you will need to be running gdm instead of lightdm.

I am really happy with it, except that audio is difficult to get working because Nomachine expects ESP, which no modern distro uses any more.

---

### Post by Perryg on 2012-05-09
x11vnc works well.  You need to manually configure it but once you have it worked out it is really fast. Unity 3D is of course slower over remote no matter what you use because of the heavy compiz.  Unity 2D is as fast and any other remote connection I have used.

---

### Post by QIII on 2012-05-09
How fast or slow the remote performance is is a function of the VNC software, not of the DE.  VNC is slow because it compresses bitmaps and transmits them.  You might say that it takes a rapid series of screenshots of pixels that change and sends them.  In a 3D DE, there are lots of changes.

Using VNC with a Windows host would fare no better.  

VNC is terribly inefficient and produces an inordinate amount of traffic.

---

### Post by Perryg on 2012-05-09
Well that's according to you.  As I said 2D is as fast as anything I have seen.  Add 3D with compiz it is slower. What I see is from actuall use so take it for what it is worth. Use it or don't. I use it almost everyday at least 5 days a week.

---

### Post by QIII on 2012-05-09
No, not according to me.  It's a function of the VNC technology.

The performance you are seeing is substantially inferior and less efficient than nx or RDP.

---

### Post by Perryg on 2012-05-09
Oh and I believe you ment pixmap not bitmaps. But either way I am very happy with the results myself.  Not for the casual user but it is very powerful.

---

### Post by QIII on 2012-05-09
No.  I believe I meant bitmap compression.

At least that's Olivetti and Oracle Research Lab think it is.

---

### Post by gmoore777 on 2012-05-16
I'm having similar issue as the original poster.

My VNC client (RemoteDesktopViewer) is on a laptop running PrecisePangolin 32-bit.

I have a machine running PrecisePangolin 64-bit and I am running vnc4server as the VNC Server.
(this machine happens to be a virtual machine running under (or on top of)
Xen 4.1.x.)

When I vnc to the machine, I am missing the Unity launcher and
the top menu bar. I only have the background image showing.

On a different remote machine where I do see a correct Unity launcher and
top menu bar, I also noticed that if I choose "Log out" when 
connected to the machine, that the resulting screen is just the 
background image. No Unity launcher nor top menu bar.

Not sure if that information is helpful.

So either the Unity launcher and top menu bar has crashed
(is there a separate process devoted to these 2 things?)
or we are seeing the "logout" screen (or the login screen).

FYI: I can successfully connect to vnc4server running on a 64-bit
LucidLynx machine.

---

### Post by gmoore777 on 2012-05-22
I opened a bug against "compiz" for this problem:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1003179](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1003179)

---

### Post by SirKingChase on 2012-07-04
I love Vncserver, over LAN it is super fast, asid from video acceleration it is literally just a fast as using it regularly.

I have gotten it to work by installing gnome-shell, but I am missing the exit and enlarge buttons.  I am also not able to move some applications.  Needless to say it is broken.  I am in the process of completely removing Unity and installing gnome.

---

### Post by Linfreak on 2012-07-16
> **QIII said:**
> A recommended solution might be to get away entirely from the slow and insecure vnc technology entirely and go to nx.

I am really happy with it, except that audio is difficult to get working because Nomachine expects ESP, which no modern distro uses any more.

Hi QIII. Could you let me know the steps using NX3.5.0 please? My setup is from Windows to a ubuntu 12.04 machine though. And does NX work with both Unity 3D and Gnome-shell as well?

Thanks in advance!

---

### Post by Linfreak on 2012-07-16
> **SirKingChase said:**
> I love Vncserver, over LAN it is super fast, asid from video acceleration it is literally just a fast as using it regularly.

I have gotten it to work by installing gnome-shell, but I am missing the exit and enlarge buttons.  I am also not able to move some applications.  Needless to say it is broken.  I am in the process of completely removing Unity and installing gnome.

SirKingChase... Eagerly awaiting your how-to for running Gnome-shell over VNC! :)

---

