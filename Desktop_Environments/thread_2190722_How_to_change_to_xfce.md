---
title: "How to change to xfce"
date: 2013-11-28
forum: Desktop Environments
---

### Post by jcoles on 2013-11-28
I've installed ubuntu server. Then I installed ubuntu-desktop for a GUI. It's Unity. I'd hold my nose and use Unity, but it doesn't work over RDP. No taskbar is visible. I can't do anything. I thought I could just install xubuntu-desktop and try that instead. I installed and rebooted, but Unity is still there and there's no access to any settings to choose a xubuntu session instead. Surely I should be given the choice at logon?

Is there some command-line magic to do this? Unity gives so little access to my machine that I can't find a way out of this.

---

### Post by steeldriver on 2013-11-28
There should be a little 'button' (Ubuntu logo) next to your name on the lightdm login screen - if you press that there should be a list of available sessions - or are you not seeing that?

---

### Post by jcoles on 2013-11-28
Thanks. I just found that! (Controls that don't look like controls. How smart is that?) But when you log in through RDP, you don't get that login screen and can't make a choice. Should my choice locally on the machine affect which session I get via RDP? I still see only the background via RDP. Right-clicking on the desktop brings up the same menu it does locally. 

Of course, it's always possible that the problem is xrdp and not Unity...

---

### Post by steeldriver on 2013-11-28
Oops sorry I missed the bit about RDP - I *think* that the xrdp session ini runs /etc/X11/Xsession which in turn looks for a user's ~/.xsession if it exists and runs the session indicated there - it *may* be possible to set the session for RDP independently using something like an ~/.xrdp/.xsession (like the VNC equivalent ~/.vnc/xstartup)

TBH I've never found RDP to be very satisfactory - unless you absolutely need to use RDP on the client side I'd suggest taking a look at doing it with VNC

---

