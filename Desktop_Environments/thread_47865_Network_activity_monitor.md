---
title: "Network activity monitor"
date: 2005-07-10
forum: Desktop Environments
---

### Post by Raeth on 2005-07-10
Greetings,

On Gnome, I enjoyed the applets that notified me of ingoing and outgoing network activity, by either the flashing double-monitor icon or the minature system graph.

I would love to have an applet for my Kicker panel that showed me network activity. There isn't one in the "Add to panel" menu, so I'm wondering if anyone had links or names of such applets.

Thanks!
Raeth

---

### Post by SGC on 2005-07-10
Try [knemo](http://kde-apps.org/content/show.php?content=12956)  (universe repository):
sudo apt-get install knemo

After installing it, go to the control -> KDE components -> service manager , then choose knemo and hit start, and then go to control center -> Internet  & network -> Network monitor, to configure it.

You will see a flashing monitor or what ever icon you choose on kde's system tray.

---

### Post by dc2447 on 2005-07-10
You need: knetworkled

---

### Post by N8MAN1068 on 2005-07-15
[QUOTE=dc2447]You need: knetworkled[/QUOTE]
I wasn't able to find that in Synaptic.

When trying to install knemo, I recvd an error referencing knetworkconf being in use..

I searched Synaptic for knet and find knetload, which installed ok. it at least lets me see whats going on, although at a glance i can barely see the chart/graph and would prefer the 2 monitors blinking at me a al wind0ws

---

### Post by N8MAN1068 on 2005-07-15
I take that back.
I was able to install Knemo after a few minutes, but I had to reboot, then upon launching back into KDE it prompted me for setup, but didn't find my interface.  :-|, uninstalled


I found:
bubblefishymon--no idea where this went...
slurm---installed, but no icons on the 'start' bar...searched for it, couldn't get it to start...uninstalled...
tleds---installed, but no icons on the 'start' bar...searched for it, couldn't get it to start...uninstalled...

maybe someone more knowledgeable will have better luck?

---

### Post by GeneralZod on 2005-07-15
I wrote a little system tray app called knetpersec ages ago (my first KDE app!).  I'll be happy to e-mail you the source/ executable if it sounds like something you'll want.  The same executable has worked for me across Mandrake 10, Gentoo, and Kubuntu.

[img]http://etotheipiplusone.com/knetpersec.png[/img]

The app itself is the little black square in the bottom right of the screen; the yellow pop-up is what appears if you hover over it.  A line graph scrolls from right to left, showing how your download rate has varied over time.  It was inspired by netpersec, a Windows utility that I missed when I made the switch :)

Edit:

Alternatively, ksysguard might do the trick - I've just added Net monitoring to mine to show what it looks like.  Up and down rates are superimposed on the same graph (unlike the "split view" with knetpersec) :

[img]http://etotheipiplusone.com/ksysguard.png[/img]

---

### Post by elsewhere on 2005-07-15
If you don't mind compiling your own applications, there's an app called kbandwidth on kde-apps.org, the link is [here.](http://www.kde-apps.org/content/show.php?content=18939) 

It gives you an "led-style" bargraph for bandwidth in/out, similar to zonealarm on Windows if you've ever used it.  It's configurable for colors so you can match it to your color scheme. Works pretty well, I used it for a while although I mainly use a superkaramba add-on for monitoring network activity now.

Compiled fine for me on kubuntu, once installed it becomes an option to add into your system tray under applets.

Anyways, just throwing out another option...

Cheers,
KV

---

### Post by Raeth on 2005-07-16
> **GeneralZod]I wrote a little system tray app called knetpersec ages ago (my first KDE app!).  I'll be happy to e-mail you the source/ executable if it sounds like something you'll want.  The same executable has worked for me across Mandrake 10, Gentoo, and Kubuntu.

[img]http://etotheipiplusone.com/knetpersec.png[/img]

The app itself is the little black square in the bottom right of the screen said:**
> http://etotheipiplusone.com/ksysguard.png[/img]

Thank you for the info! I tried the Ksysguard applet, but when I drag the desired network modules into it, nothing displays. The CPU info shows fine.

---

### Post by GeneralZod on 2005-07-17
[QUOTE=Raeth]Thank you for the info! I tried the Ksysguard applet, but when I drag the desired network modules into it, nothing displays. The CPU info shows fine.[/QUOTE]


That's odd - try dragging Network-Interfaces-<interface name e.g. eth0,etc>-Receiver-Data and the same for Transmitter and see if that works.

---

### Post by runesvend on 2007-08-11
> **elsewhere said:**
> If you don't mind compiling your own applications, there's an app called kbandwidth on kde-apps.org, the link is [here.](http://www.kde-apps.org/content/show.php?content=18939) 

It gives you an "led-style" bargraph for bandwidth in/out, similar to zonealarm on Windows if you've ever used it.  It's configurable for colors so you can match it to your color scheme. Works pretty well, I used it for a while although I mainly use a superkaramba add-on for monitoring network activity now.

Compiled fine for me on kubuntu, once installed it becomes an option to add into your system tray under applets.

Anyways, just throwing out another option...

Cheers,
KV
Could you give a short guide to compiling this program? It looks really nice from the screenshots.

---

