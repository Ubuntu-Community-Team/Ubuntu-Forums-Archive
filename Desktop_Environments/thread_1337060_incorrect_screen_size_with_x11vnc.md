---
title: "incorrect screen size with x11vnc"
date: 2009-11-25
forum: Desktop Environments
---

### Post by jdrugo on 2009-11-25
Hi all,

I am using Kubuntu Keramic and am tunneling a VNC session (connecting to the currently logged in session) over SSH/VPN, running x11vnc on the server side with the following command:

```
x11vnc -safer -localhost -nopw -once -ncache 10 -noxdamage -display :0
```

I can then connect with KRDC (same result with other VNC viewers) to the remote desktop. The only problem is that the VNC server seems to overestimate the remote desktop size: The width in the VNC client corresponds to the remote desktop width. The height, on the other hand, is about 10x the height of the remote desktop. The 'correct' remote desktop itself is at the top of the remote desktop that the VNC client shows. All the rest below that is black. If I move the mouse over the black part, the occasional window of the 'correct' remote desktop appears at various locations.

Has anyone experience this problem and knows a workaround? I have tried various different x11vnc comment line options, but wasn't successful. Searching the web and the forums didn't reveal a solution either.

Thankful for any advice,
Jan

---

### Post by krunge on 2009-11-25
> **jdrugo said:**
> 
```
x11vnc -safer -localhost -nopw -once -ncache 10 -noxdamage -display :0
```

I can then connect with KRDC (same result with other VNC viewers) to the remote desktop. The only problem is that the VNC server seems to overestimate the remote desktop size: The width in the VNC client corresponds to the remote desktop width. The height, on the other hand, is about 10x the height of the remote desktop.

This is how '-ncache 10' works: it makes a desktop 10X taller than the normal height and uses the extra framebuffer for caching windows and their saveunders.  If you can't get KRDC to not show you that region (e.g. by resizing its window) then you can't use KRDC with x11vnc -ncache.

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching](http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching)[/INDENT]

---

### Post by Zorael on 2009-11-25
(off topic)
krunge, why isn't there a more recent version of x11vnc in the repos? :3 I see that even the Lucid repos have 0.9.3.

I love it, by the way. Though the GUI (from -gui) is pretty horrid. ;)


(on topic)
TightVNC on Windows shows it as one very tall desktop too, so I imagine client support isn't very wide (yet).
edit: Because the client *is* supposed to hide the extra space from view and just treat it as an internal cache, right?

---

### Post by krunge on 2009-11-25
> (off topic)
krunge, why isn't there a more recent version of x11vnc in the repos? :3 I see that even the Lucid repos have 0.9.3.

0.9.8 is in squeeze/sid since August.  Someone at debian kindly picked it up after it had been orphaned for years.
> 
I love it, by the way. Though the GUI (from -gui) is pretty horrid. ;)

Yes, that aspect of the gui is intentional and by careful design.  Glad to hear I'm succeeding in that. :-)

> 
(on topic)
TightVNC on Windows shows it as one very tall desktop too, so I imagine client support isn't very wide (yet).
edit: Because the client *is* supposed to hide the extra space from view and just treat it as an internal cache, right?
Yes, ideally the client will autodetect it or the user can indicate to hide it.  It's not clear to me clients besides my own ssvnc viewer will ever support x11vnc's "-ncache" hack, even though it is probably just a simple change for most.

The -ncache mode was done out of frustration that after 10+ years the VNC protocol still had no client-side caching (which all other remote desktop systems had from day 1.)  And 3 years after -ncache VNC still doesn't have client-side caching...  If that ever happens, I will add support for it to x11vnc and ssvnc (assuming I'm still alive.)

So for now the only -ncache "support" is for a viewer to be able to have a scrollbar and to be able to disable auto-scrolling.  Or on unix/macosx use ssvnc (another horrid gui of mine!)

---

### Post by jdrugo on 2009-11-26
> **krunge said:**
> This is how '-ncache 10' works: it makes a desktop 10X taller than the normal height and uses the extra framebuffer for caching windows and their saveunders.  If you can't get KRDC to not show you that region (e.g. by resizing its window) then you can't use KRDC with x11vnc -ncache.

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching](http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching)[/INDENT]

Thanks! That's exactly what I've been looking for. I used the '-ncache 10' because of the recommendations that x11vnc writes to the output when you start it, but didn't read through the (vast amount of) documentation about what all the possible arguments to x11vnc do in detail.

With my connection there doesn't seem to be much of a difference between -noncache and -ncache, so I'll be using -noncache for now.

Thanks again for your help,
Jan

---

### Post by krunge on 2009-11-26
> **jdrugo said:**
> 
With my connection there doesn't seem to be much of a difference between -noncache and -ncache, so I'll be using -noncache for now.
Yes, it needs to be a medium-to-slow link to notice the improvement. I use it daily to a desktop 3000 miles away and it works very nicely.

---

