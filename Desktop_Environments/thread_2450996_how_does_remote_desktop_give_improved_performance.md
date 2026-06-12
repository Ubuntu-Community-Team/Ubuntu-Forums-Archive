---
title: "how does remote desktop give improved performance?"
date: 2020-09-24
forum: Desktop Environments
---

### Post by abe404 on 2020-09-24
Hello,

I recently switched from logging into my ubuntu (20.04.1 LTS) computer directly to using it via a remote desktop connection from windows.

To my surprise everything is faster and more responsive. I'm wondering if some settings are automatically changed when logging in via remote desktop that are designed to make the user experience faster and more responsive?

Is it possible to alter these settings manually to get this improved user experience without using a remote desktop connection?

Thanks!
Abraham

---

### Post by TheFu on 2020-09-24
Is the Windows GPU better?
Which DE does your Ubuntu use?
Which remote desktop method is being used?  x2go can fly over the internet with good connections provided Gnome3 isn't used.

The performance improvement is almost all from not having the GUI running.

---

### Post by abe404 on 2020-09-25
Thanks TheFu,

[I]> Is the Windows GPU better?
[/I]
The windows GPU is worse. But sometimes the linux GPU is busy with other tasks.

* > Which DE does your Ubuntu use?*

Based on this answer:
[https://askubuntu.com/a/281554](https://askubuntu.com/a/281554) 

I concluded I have GNOME

*> Which remote desktop method is being used?*

From checking top, looks like xrdp is running on linux. On windows it's the default remote desktop application for windows 10.

*> x2go can fly over the internet with good connections provided Gnome3 isn't used.*

It's a local network, rather than the internet so that helps a lot.

[I] > The performance improvement is almost all from not having the GUI running. 				

[/I]I'm still using a GUI on linux, but it seems to have been altered somehow to make it run faster (perhaps less animations?)

I'd like to understand specifically what is happening so I can set it as a default but I'm not sure how to find out.

---

### Post by TheFu on 2020-09-25
I don't use Gnome3, but there might be a way to turn down the graphics it uses.  I think this is setting automatic for all "gnome approved" remote desktops and only recently in Gnome3 systems. Don't know if there is any way to turn GPU requirements down other than using the approved, gnome, remote desktop tool. [https://wiki.gnome.org/Projects/Mutter/RemoteDesktop](https://wiki.gnome.org/Projects/Mutter/RemoteDesktop)

If it were me, I'd be using the SPICE remote desktop protocol with QXL GPU drivers from a virtual machine. Those are crazy fast for any remote desktop on the LAN or on the same physical machine. I only use virt-viewer for kvm virtual machines where it is built-in. For some reason, I thought spice had been ported to non-VM uses as well. 
There are Spice clients for every platform I have, including android, though I haven't tried Windows in a few years.  The Linux client is crazy fast.  

Over the internet, I'd use x2go, period.  Some things just work too well, with security, to bother looking at anything else.

[https://en.wikipedia.org/wiki/Simple_Protocol_for_Independent_Computing_Environments](https://en.wikipedia.org/wiki/Simple_Protocol_for_Independent_Computing_Environments) has been around about 10 yrs. The goal is to provide native performance, with audio+video, for local and networked GUIs. In the last year, it has really become great. 

If you don't use virtual machines, SPICE probably isn't helpful. Sorry.

---

### Post by abe404 on 2020-09-25
Thanks TheFu,

Thanks for the extra tips. I will look into those solution if I have remote desktop setup decisions to make in the future.

I will try just disabling animations to see if that does the trick in terms of speed up next time I am using ubuntu without remote desktop.

---

### Post by TheFu on 2020-09-25
"Fallback" might be a useful keyword when searching. as in fallback mode.  
[https://people.gnome.org/~lferrett/gnome-help_it/fallback-mode.html](https://people.gnome.org/~lferrett/gnome-help_it/fallback-mode.html)

---

### Post by ActionParsnip on 2020-09-26
Could even use a super lightweight desktop like LXDE. It'll make the remote session super light and fast

---

### Post by TheFu on 2020-09-26
> **ActionParsnip said:**
> Could even use a super lightweight desktop like LXDE. It'll make the remote session super light and fast

LXDE is dead, isn't it?  They switched to LXQt.  A DE is 100% optional. Can just run a window manager, WM.  Openbox is minimal, but behaves in a way Windows users won't hate.  Or make the jump to i3 or fvwm for a "Unixy" WM.  

For people seeking truly light, there is dwm from the suckless group. [https://dwm.suckless.org/](https://dwm.suckless.org/)  It requires recompiling to change options because reading config files adds bloat.  That's extreme, even for me. ;)

---

