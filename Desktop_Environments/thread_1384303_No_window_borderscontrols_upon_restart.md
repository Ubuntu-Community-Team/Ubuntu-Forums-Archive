---
title: "No window borders/controls upon restart"
date: 2010-01-18
forum: Desktop Environments
---

### Post by Lord Stig on 2010-01-18
Hi. I'm using XFCE and have problems with Compiz or Emerald which involve bizarre screen corruption at random but frequent intervals on parts of the screen. The corruption appears either as lines or as large letters or numbers appearing on the offending area. My solution at first was to roll up and then roll down the window, but now I've decided to just disable Compiz altogether.
I actually have Mint 7 XFCE and am going to post there but hope it's ok to post here as well to increase the likelihood of resolving this (I understand Mint 7 is Jaunty underneath). Apologies if this is bad form.

I have disabled Compiz by going to XFCE Display Settings at the bottom of the System menu. There are two options: one to disable now (no problem, it reverts to the XFCE window borders), the other to disable Compiz at login.

In-built video is Intel 82855 GME. I haven't installed any other video drivers - it's as it came when I installed Mint.

I've chosen to disable Compiz at login, so I don't have to switch every time I log in, but this results in me having no window outlines at all. No borders, no minimise, maximise, roll up/down, close etc. and obviously can't move or resize the windows.

1) How can I tell the OS to use the XFCE window borders on startup? (I suspect it is leaving it to Emerald, which presumably is disabled as part of disabling Compiz).

2) If I uninstalled Compiz and Emerald would I mess stuff up?

3) Can the bizarre display problem with Compiz be solved

4) Thanks for reading this.

---

### Post by XubuRoxMySox on 2010-01-18
I fixed a similar problem in a Crunchbang/Xfce experiment by *completely* removing Compiz (not just uninstall, but *completely remove*, using Synaptic). I can't say how it will work in Mint Xfce, but since both are Ubuntu-based, it might. And you can always re-install it if it doesn't work.

-Robin

---

### Post by Lord Stig on 2010-01-18
Ok, thanks for replying. Did a complete uninstall of all the Compiz elements listed in Synaptic.
I still have the same problem when I start Mint, though - no windows borders at all. I left the Mint tweak that allows you to turn on/off Compiz (the one in my first post) and trying to turn it on reinstated those window borders. But how can I get them to just appear on login, like they should?

Can anyone help with this?

---

### Post by Lord Stig on 2010-01-19
Anybody? :-(

---

### Post by Lord Stig on 2010-01-20
After doing a bit of research I will add a button to my bottom panel that runs the command "xfwm4". Hopefully this will reinstate the window borders.

I'll post back if this work to help anyone else who encounters a similar problem.

Still open to suggestions from anyone on this (particularly if I find my idea doesn't work).

---

### Post by Lord Stig on 2010-01-20
Yep, that works: usr/bin/xfwm4
Made it run automatically at startup by adding it in Settings, Session & Startup

---

