---
title: "Need help getting Ubuntu Desktop and tightvncserver to work on EC2"
date: 2022-08-29
forum: Desktop Environments
---

### Post by broiledsmurf on 2022-08-29
I'm hosting Ubuntu Desktop on an EC2 instance and trying to connect to it from my Mac.  To do this, I followed the instructions detailed in [this tutorial]("https://ubuntu.com/tutorials/ubuntu-desktop-aws#1-overview") for how to run Ubuntu Desktop on an EC2 instance.  I was able to get it up and running, but when I connect, I don't see the usual Ubuntu Desktop.  Instead, what I see is grey and buggy and weird and nothing really works right.  For example, when I hit the "Desktop" button, I get an error.  And my mouse leaves weird trails all over the screen.  I tried both the Mac's built in VNC client as well as RealVNC, and got the same results.  The Ubuntu version I'm using is 22.04.1 LTS.

I took a couple of screenshots. [This]("https://i.stack.imgur.com/2o46u.png") is what it looks like when I connect, and [this]("https://i.stack.imgur.com/EwI6A.png") is what it looks like when I hit the "Desktop" button.

Thank you for taking a look!

---

### Post by TheFu on 2022-08-30
Try right-clicking on the desktop - the gray area.  Does a menu appear?

If not, I suspect you didn't tell VNC which window manager to run.  BTW, Gnome doesn't work over remote desktops, so you really need to use a different, light, DE. Something like XFCE or LXQt or Mate.  KDE probably won't work either, since it is tightly coupled with plasma now.

Of course, the better, easier, answer is to use x2go instead.  The same lite DE issue exists, but it has a pretty client for most OSes and built-in ssh so the traffic is all secured, as is the login to the remote system.  It doesn't hurt that x2go is 2-3x faster than VNC or RDP either. [https://wiki.x2go.org/doku.php/doc:newtox2go](https://wiki.x2go.org/doku.php/doc:newtox2go)
I've used x2go and other NX-based remote desktops from 5 continents.  x2go is by far the best option.

---

### Post by broiledsmurf on 2022-08-31
Thank you for the response, @TheFu!  When I right click on the file manager, it does give me a context menu (New Folder, Add to Bookmarks, Paste, Select All, Open in Terminal, Properties).  However, when I right click on the grey background (the desktop) I get no context menu.  So I'm guessing you've diagnosed my problem.  Interestingly, in the tutorial I linked to, [it does appear that they got the normal Ubuntu desktop to show up]("https://ubuntu.com/tutorials/ubuntu-desktop-aws#5-connecting-to-ubuntu-desktop").  However, [it appears]("https://ubuntu.com/tutorials/ubuntu-desktop-aws#1-overview") the tutorial was using Ubuntu 16.04 — would an earlier version have let me use the normal Ubuntu desktop?  If not, any idea what they may have done to get it to work?

I guess I was kinda jazzed about using the normal Ubuntu desktop, since it has such wide community support, and I could apply the knowledge contained in so many Stack Overflow and Ubuntu Forum posts..  I have used Mate a bit, but it seemed to have little community support, and I'm afraid that not as many things would work on it.  Is Mate as bad as it seems?

(also, apologies, I'm a bit new to this world — haven't used desktop Linux in a number of years)

---

### Post by TheFu on 2022-08-31
In 16.04, the default Ubuntu desktop was Unity.
In 18.04 and later, that changed to be Gnome 3 or Gnome 4.

Remote desktops have limitations.  DEs that require direct access to GPU hardware are one of those limitations.  Gnome3+ and KDE-Plasma want that direct hardware access.  So, pick any other DE (almost) and it should work.

I used Mate for a bit and found it one of the least obnoxious DEs, but it was too bloated for my needs. I have this thing about bloat when it isn't necessary and DEs are bloat. A few years ago, I switched back to using the WM I ran in the mid-1990s, fvwm.  That's probably too much effort for someone new.

If you dump VNC and switch to using x2go, you'll be happy and you'll definitely be more secure.  Promise.

---

### Post by ActionParsnip on 2022-08-31
What are you doing on the remote system that needs the full desktop session? There may be a sleeker solution to what you are trying to achieve.

---

### Post by broiledsmurf on 2022-08-31
I'm basically wanting to use it as my main dev/work box for working remotely.  The goal is to have the box reside in AWS, and then I can VNC in and operate the machine from anywhere.

  Some desktop apps I want to use : pycharm, slack, chrome, and zoom.  This is in addition to the usual suite of command line tools.  

Amazon Workspaces offers a fairly decent solution for this (using Mate), but they don't let you initiate on-demand backups of the system drive, which is a problem for me.  So I'm kinda trying to DIY this using VNC.  Any other ideas would be welcome!

---

### Post by TheFu on 2022-08-31
You won't be using zoom.  Video applications will never work the way you hope.  Make other plans.

For years, I use x2go to remote into my main Linux desktop. Usually it was from the same LAN, but when I was traveling, it would be from remote locations.  VNC isn't secure enough for this.

---

### Post by Skaperen on 2022-08-31
is *x2go* FOSS?

---

### Post by broiledsmurf on 2022-08-31
> **TheFu said:**
> VNC isn't secure enough for this.

When I was testing this out, I did VNC through an SSH tunnel and it seemed to work fine.  Isn't that a sufficient amount of security?

---

### Post by ActionParsnip on 2022-09-01
Could always use xdp
[https://docs.microsoft.com/en-us/azure/virtual-machines/linux/use-remote-desktop?tabs=azure-cli](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/use-remote-desktop?tabs=azure-cli)

---

### Post by TheFu on 2022-09-01
> **broiledsmurf said:**
> When I was testing this out, I did VNC through an SSH tunnel and it seemed to work fine.  Isn't that a sufficient amount of security?

Yes, assuming vnc is setup to only allow localhost connections.  There is an option for this, but NX (the protocol) has ssh built in and does dynamic compression with manual controls, so why use the inferior VNC?

I've pushed x2go, which is F/LOSS, enough.  "You can take a horse to the water, but you can't make him drink."

---

### Post by broiledsmurf on 2022-09-01
Thanks for the tip!  I'll check out x2go.

---

