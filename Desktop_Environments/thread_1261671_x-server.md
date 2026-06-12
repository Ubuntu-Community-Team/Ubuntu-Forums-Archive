---
title: "x-server"
date: 2009-09-09
forum: Desktop Environments
---

### Post by jwxie on 2009-09-09
This sounds stupid but I just realized how dumb I was lmao.

OKay, so I have 9.04 and I want to know something. Is Ubuntu desktop = X-Windows? 

And the X-windows in the aspect of Ubuntu Command-line default Server system, the X-windows is the GUI Windows, am I correct?

So if this is the statement
> Launching application through X-window is slow through Internet.
I am running my ssh command via terminal (desktop 9.04), I am actually doing this via X-WINDOWS?


Lol thanks for the help....

---

### Post by DaithiF on 2009-09-09
> **jwxie said:**
> 
OKay, so I have 9.04 and I want to know something. Is Ubuntu desktop = X-Windows? 

Ubuntu (and pretty much every other distro too), uses X-windows as a part of its GUI infrastructure.  Think of X as a low-level graphical layer, that desktop environments like Gnome and KDE use in displaying their graphical elements.

> 
I am running my ssh command via terminal (desktop 9.04), I am actually doing this via X-WINDOWS?


is it a graphical application that you are running -- does it have a window, menu, toolbar etc, and are you running ssh with a -X or a -Y parameter?  If yes to both then yes you are using X-windows remotely.  But if its a text-based console application, or a shell command/shell script then no, X isn't involved.

---

### Post by 3rdalbum on 2009-09-09
> Launching application through X-window is slow through Internet.

With SSH, you can actually run graphical (GUI) programs across an SSH session. The program runs on the remote computer, and it communicates with the X server running on your local computer. Your local computer recieves the window, and sends your keypresses and mouse clicks to the remote computer.

That's what is meant by that quote: Running GUI programs on SSH across the Internet is slow. Through a LAN, it's reasonably fast, and running text programs across the Internet is also reasonably fast.

---

