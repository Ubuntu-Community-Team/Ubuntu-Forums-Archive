---
title: "system freeze, no SysRq"
date: 2009-03-10
forum: General Help
---

### Post by dogbert55 on 2009-03-10
Well, I'm running xubuntu 8.10 on a dell mini 9 and the system froze right after I logged in.  I tried ctrl + alt + backspace and ctrl + alt + delete, but neither helped.  Printscreen is accessed through Fn + 7 because of the small keyboard and I couldn't get any combination of Fn, 7, and alt to work as SysRq.  I hit the power button to shut it down. 

When I restarted it had me run **fsck** manually.  When that finished I got a message saying something about the xserver or xorg file being broken.  I ran ** sudo dpkg-reconfigure xserver-xorg** ;another post recommended that. It froze at the first window that came up.  I somehow got to a point where could enter reboot  and it seemed to work fine.

I guess my question has three parts.  First and foremost, is there a way to get the SysRq key to work or a safe way to shut down when the computer freezes.  Is there an easy way to find if I broke anything? Is there an easy way to find what caused the crash? (Sorry this is long, I'm new to linux and don't really know what's important)

---

