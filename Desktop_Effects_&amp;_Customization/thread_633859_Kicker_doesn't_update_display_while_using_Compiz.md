---
title: "Kicker doesn't update display while using Compiz"
date: 2007-12-07
forum: Desktop Effects &amp; Customization
---

### Post by kprateek88 on 2007-12-07
I'm using compiz (from the repos) on Kubuntu 7.10 on a laptop with an Intel 915GM graphics card. Compiz itself works fine, but the kicker has a strange problem. Kicker's display is frozen at what it was when compiz was started (the time on the clock is frozen, new windows don't show up in the taskbar, K button doesn't look pressed when it should, etc). Clicking (on the K menu, clock, network manager, etc) does what is expected. "Behind the scenes" kicker seems to be working fine, however the actual image on the screen is frozen. If I switch to kwin, kicker works fine. When I switch back to compiz, kicker goes back to this behaviour. I'm using emerald with compiz. Any ideas?

This is quite urgent as I won't be having proper internet access for a few weeks starting tomorrow. 
Thanks.

---

### Post by kprateek88 on 2007-12-07
I restarted the system. This time it looked like kicker is working fine, but there was a much more serious problem: the keyboard stopped responding completely (no Ctrl+Alt+Backspace, no Caps Lock light), and mouse clicking had no effect. The mouse pointer moved, though. The display was being updated (eg, the clock was ticking). I have had similar problems earlier (on a different system), the only difference being that the display was frozen too. Thankfully I could ssh to this laptop from another system. Oddly enough, ps aux | grep Xorg didn't show Xorg running. I did sudo reboot, and now all is fine, including kicker and compiz. I'm a bit uneasy... if this happens again in the next few weeks ssh is ruled out as I will have neither a network connection nor another system to ssh from, and I'll just have to hard reset... (which reminds me of Windows 98 days :-( )

Note: During the first reboot mentioned above, I had booted Windows and shut it down (as opposed to hibernate, which was being used earlier). So Kubuntu mounted the Windows NTFS partition this time, while it wasn't doing so earlier since it was not cleanly shut down from Windows. I don't know if this is relevant to the problem, but I'm mentioning it anyway.

---

