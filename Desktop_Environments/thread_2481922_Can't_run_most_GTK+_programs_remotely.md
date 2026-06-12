---
title: "Can't run most GTK+ programs remotely"
date: 2022-12-13
forum: Desktop Environments
---

### Post by Alex_Filonov on 2022-12-13
I had 22.04 installed on Lenovo Thinkserver M82, had balsa as a mail agent, and was able to run it remotely from other 22.04 computer (connecting ssh -Y). My Nvidia drivers got all messed up, and I had to reinstall (full install on existing partition, with nouveau drivers this time). Now I can't run most GTK+ programs remotely. Balsa doesn't run, gnome-terminal either. At the same time, non-GTK+ stuff runs: xclock, a bunch of other stuff. What's wrong here? Is it a common thing or I messed something up in a new install?

---

### Post by TheFu on 2022-12-13
X/Windows on both sides or is there any Wayland involved?  If just X/Windows, then you probably screwed something up, but the Gnome guys have been moving to Wayland pretty fast and breaking X/Windows stuff along the way.  

I haven't seen problems recently, since I don't/can't use Wayland. It breaks many workflows that I use.  I do use libreoffice remotely, however. Sometimes it gets stuck.

You can try using 'ssh -X user@remote xterm -sb &'   then run the program. It will inherit the ssh DISPLAY forwarding and the program output can be seen in the terminal even if the program doesn't show up on your desktop.

---

### Post by Alex_Filonov on 2022-12-13
Well, I didn't dig that deep. It's a stock 22.04.1 LTS install (on both computers), so probably it's Wayland.
As for running through xterm, getting the same result: just hangs, no output, no nothing.

---

### Post by Alex_Filonov on 2022-12-14
OK, I checked out, it's Wayland. On both machines. I have a suspicion that it wasn't Wayland when I had Nvidia drivers, that might be the reason balsa worked remotely. Oh well, back to old fashioned mutt.
I don't know the reason why they are so eager to break Gnome all the time? I remember 1.2 18 years ago, it worked great for me.

---

### Post by TheFu on 2022-12-14
Why not just prevent Wayland from being used?  Google should find the 2-steps needed to make that happen.  I'm guessing it is 2-steps.

---

### Post by Alex_Filonov on 2022-12-15
Why Wayland developers decide what I need and what I don't need? ssh -X functionality was INTENTIONALLY not implemented in Wayland. That's an outrage! I don't care about games, I don't care about purity of concepts. I worked with ssh -X for 20 years, it's the best remote GUI access for me. Don't want to run remote desktop. Don't want to run VNC.

---

### Post by TheFu on 2022-12-15
> **Alex_Filonov said:**
> Why Wayland developers decide what I need and what I don't need? ssh -X functionality was INTENTIONALLY not implemented in Wayland. That's an outrage! I don't care about games, I don't care about purity of concepts. I worked with ssh -X for 20 years, it's the best remote GUI access for me. Don't want to run remote desktop. Don't want to run VNC.

It isn't the Wayland team.  They didn't do anything except to work long and hard on something they hoped lots of users would like.  They didn't force anything onto you system either.  BTW, Xwayland should work for situations like this, at least that's my understanding. It is Canonical that has decided ... and they've tried since at least 2017 to make Wayland default.  Each time, there have been failures.  Seems that lots of people don't care, because they don't know what they've lost.  Gnome team isn't helping much either, as they push Wayland stuff too.
[https://bugs.launchpad.net/ubuntu/+bug/1992155](https://bugs.launchpad.net/ubuntu/+bug/1992155)

X11 is still installed on all Ubuntu flavor desktops, so you just need to enable it, then see if that solves the issue.  

It is a little early to be mad.  X11 is still there and available.  X11 has some serious security problems that Wayland has closed. The time to become mad is when there aren't any work-arounds.  X11 is still being developed. Seems the team has learned they can't just abandon it, as planned and that getting Wayland to be stable will take 10 more years.

---

### Post by SeijiSensei on 2022-12-15
Just tested "ssh -X" now with the Konsole application on Kubuntu 22.04 to a server running CentOS 6. Connected and opened xterm on the server. It displayed locally as expected. I then successfully ran LibreOffice on the server which I'm pretty sure uses GTK+.

I don't think KDE uses Wayland, but I'm not too familiar with what's running under the hood.

---

