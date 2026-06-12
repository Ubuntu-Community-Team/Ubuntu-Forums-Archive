---
title: "Keeping Java app running 24/7"
date: 2005-02-03
forum: Desktop Environments
---

### Post by Wardhog on 2005-02-03
I'm pretty sure I've got the right forum to ask this question, forgive me if I haven't.

I'm running Ubuntu on a head/kbd/mouseless box that's on 24/7, I use Reflection X on a Windows box to access my Ubuntu box.

I want to run Azureus full time on this Ubuntu box.  I don't want to leave my Windows box up and running 24/7 as well. 

I have Azureus up and running with no problems, my problem is that I cannot keep it running - when I exit out of Reflection X on the Windows box, I'm basically killing the X server the Azureus process is a child of, and as such, it shuts down.

I've also tried using VNC to connect to the Ubuntu box in the hope that when I disconnect the VNC viewer (without logging out), the Azureus process will remain running, and I can reattach to the VNC server later and find things as I left them.  This has had success for a short time span only, something seems to happen to my non-root user's session when away from it for any length of time > 5 minutes.  As an aside, can someone explain what's going on there?

I'm seeking advice as to the best way to achieve this always-on Azureus, and these forums appear to be the right place to ask.  Would starting Azureus up in rc5.d be the way to go (su -c non-root-user-running-Azureus or not?)?  If so, how do I reattach to the GUI of that process?

I keep hearing about FreeNX, is using that the way to go?  Can a VNC viewer attach to a FreeNX server?

Thanks in advance for your assistance.

---

