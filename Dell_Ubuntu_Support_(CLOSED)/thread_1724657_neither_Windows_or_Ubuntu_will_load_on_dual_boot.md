---
title: "neither Windows or Ubuntu will load on dual boot"
date: 2011-04-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Heidi_ on 2011-04-08
I installed Ubuntu on a Dell Vostro 3400 laptop earlier this week. Everything was working fine in both operating systems for a couple days. Now neither will start up except in safe (Windows)/recovery (Ubuntu) mode. 

When I choose an operating system from Grub, the initial loading screen pops up, that says the name of the operating system, but it never gets to the log-in screen. For Windows 7, it hangs on a black screen. For Unbuntu, it hangs on the purple texture screen that is the default background.

After waiting several minutes, I hold the power button down to force off and try again. This is how I am able to access Windows safe mode - forcing it off allowed me access. I tried restarting several times, but since I don't know what to look for in the recovery mode, I make no progress.

I tried searching for other threads on this, but if there are any, I haven't hit the right search terms.

---

### Post by garvinrick4 on 2011-04-08
Put in Ubuntu install cd and choose try ubuntu and open a terminal and download this
script to your DESKTOP and then run code in a terminal will put a text file on Desktop
that says Results.txt open it and copy and paste to this thread. Highlight whole thing
once pasted to your message box and Hit # sign in upper right corner of Message box.
and submit. Will give a lot of users capabilities of fixing your boot in a flash. Now download
and run code in terminal:
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
 sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by Heidi_ on 2011-04-08
Thank you for your advice. In following it, I realized that there was a graphics problem, and then I realized that after the first failed boot, I plugged in the power supply and absent-mindedly also plugged in the monitor it is usually hooked up to. So the hanging problem actually only happened twice, the rest of the time the log-in screen was being sent to a monitored that wasn't turned on.

I am sorry for posting in an unnecessary panic.

---

