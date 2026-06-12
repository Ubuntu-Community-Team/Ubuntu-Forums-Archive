---
title: "rdesktop doesn't work"
date: 2008-03-15
forum: Desktop Environments
---

### Post by Ampi on 2008-03-15
A couple of days ago I logged into a computer with windows (XP I think) and it worked perfectly.
Now I am trying to log into a Windows Vista computer and it just doesn't work.
I get

Autoselected Keyboard us-en

And that's it. It's the same message I got with the working computer, but the second time it just opened a windows-window. 

I just downloaded rdesktop again but this time a more recent version. 1.5 or something and it still doesn't work.
The Vista computer has allowed remote control and has no firewall...

Also I installed tsclient. When I plug in the IP address the window of tsclient dissapears and nothing else comes in return...

What am I missing?

---

### Post by richbl on 2008-03-28
I ran into the same problem with rdesktop. The solution for me was to disable Vista Windows Firewall. 

Actually, in my particular case, I had to permit terminal services to run on port 3389 while the firewall was running.

Good luck.

---

