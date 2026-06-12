---
title: "Laptop keyboard stopped working"
date: 2009-01-15
forum: General Help
---

### Post by HyperHacker on 2009-01-15
Yesterday I was browsing the web on my laptop (Gateway MX7515 running Xubuntu 8.04), and the keyboard and touchpad just stopped working halfway through reading a page. I could move the cursor and use the Fn key to adjust brightness, toggle power LED, etc but nothing else would respond; mouse buttons, Caps Lock, Ctrl+Alt+Backspace, etc did nothing. I had to hit the power button, and then it hung during the shutdown process, saying something about networking. I was able to hit Ctrl+Alt+F1 at that point to switch to a TTY, but then the whole keyboard froze up again and I had to do a hard shutdown.
It worked again once I turned it back on. Any ideas what would cause that?

---

### Post by HyperHacker on 2009-01-17
OK, now my desktop just did the same thing. Out of nowhere the entire system just locked up except for Amarok playing in the background and the mouse cursor (could move it but not click). No response from the keyboard at all. What's going on here?

---

### Post by HyperHacker on 2009-01-19
The laptop froze up again (twice actually), at the desktop this time, and I noticed something strange. At first I could left-click to open or close a menu but not select anything in it. After a few seconds the keyboard and mouse buttons stopped responding.
The odd part was the display would keep updating, but only if I had my finger on the touchpad. If I held it there, the clocks (in Conky and the panel) kept ticking and the CPU graph in the panel would run normally. As soon as I removed my finger, it'd freeze. If I waited a few seconds and then tapped it, it would run for one second and then freeze again. The clocks displayed the correct time (i.e. if I waited 5 seconds and tapped it, they'd have counted 5 seconds), but the CPU graph would only update once per tap.
This suggests to me some sort of interrupt problem, where the timer interrupt suddenly gets connected to the touchpad, and the keyboard to nothing. It's always shown a message at startup, something like "MP-BIOS bug, APIC timer not connected to somethingorother" but it's never been an issue until the other day.
Again I found even the power button wouldn't respond unless I was touching the pad, and it only managed to actually shut down when I tapped it.

Also, it's actually running 8.04 as I haven't found time to back it up and update it. (It's accumulated a lot of junk so I want to just copy any files I need and format it. Could be hard to do though if it keeps locking up every 5 minutes! Network dies too, just before the keyboard, so I can't even do it through SSH or FTP.)

---

### Post by HyperHacker on 2009-01-23
Got the syslog this time. I've been watching in the terminal (while true; tail /var/log/syslog; sleep 5; done) and saw a crapton of crash messages scroll by just before it stopped working. Even while the system is just sitting there doing nothing, it will randomly crash like this. Usually the crash message only appears once, I'm not sure why it got spammed so many times here. The symptoms are different every time; sometimes the clock stops, sometimes the keyboard locks up, etc.

(Why is the size limit for text files so low? <_<)

I'm going to try formatting and reinstalling with 8.10 (I'd been meaning to do that for a while anyway), so I'll see if the live CD and/or new installation has the same problems.

---

### Post by swiftarrow on 2009-02-08
Hi I have the same problem...  My xubuntu 8.10 laptop kbd stopped working, along with the trackpad, when I turned it on.  It was working fine before than...  Is there any solution?  or do I have to re-install the entire system?  How can this happen?
I really need a solution...
the keyboard and trackpad work in another OS, but that's completely not a solution.  I need to use xubuntu for work.  There is no way around it!  Aauaaaaaaaaaaauuuuggggggghhhh!!!

---

### Post by HyperHacker on 2009-02-09
I ended up reinstalling and it's been working since then. The desktop only did it that one time; I suspect it was just a brownout or something. (Seems to be some wiring problems in this house...)

---

### Post by dik23 on 2009-06-04
Did you ever find a fix for this ?

Re-installation isn't really a fix

---

### Post by HyperHacker on 2009-06-04
It hasn't happened since. Some file must have been corrupted to cause it? Though I can't see how that happened.

---

### Post by dik23 on 2009-06-04
I have recently developed this in Hardy on a Dell laptop

Than thing that I find odd is the fact that fn+ any fn related key still works but nothing else. The touch pad seems to work without problem.

And no errors are shown in any log files....

---

### Post by HyperHacker on 2009-06-04
The Fn keys typically work independent of the OS, so it's no surprise they still work. IIRC mine did as well.

---

### Post by dik23 on 2009-06-05
> **HyperHacker said:**
> It hasn't happened since. Some file must have been corrupted to cause it? Though I can't see how that happened.

My machine has two accounts on it.

When the keyboard locks up on one I can use the mouse to log out / switch to the other account which will work fine.

However - both account have the "ability" to have this problem.

Sometimes it happens half way through typing and sometimes when resuming from RAM. When resuming it won't let me enter the password, but I can switch user - whilst on the login screen the keyboard works fine - and log back into the same account where the keyboard doesn't work. As I said before if I log into a different account the keyboard works fine.

This really confuses me, to say the least, as it rules out a hardware problem and I don't see how a corrupt file would be the problem

All I can think of is some kind of clash or interrupt issue.

Someone out there must have a clue to this...

---

### Post by HyperHacker on 2009-06-05
I suspect a corrupt file only because it started happening on an install that I had accidentally corrupted a few files on (though this started happening months after that incident), and it hasn't happened since I reinstalled. Perhaps some per-user settings file?
I wonder if two different users run the same program, is it loaded to memory twice? If so then potentially an executable file could be corrupt as well.

---

### Post by dik23 on 2009-06-11
Doesn't anyone else have any input for this one ?

I'm finding this particularly strange because I'm not getting any errors in the log files

---

