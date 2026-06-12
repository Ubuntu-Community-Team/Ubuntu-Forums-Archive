---
title: "Dimension E521 AMD 64 X&quot; + 5000"
date: 2007-07-01
forum: Dell  Ubuntu Support
---

### Post by Jinge on 2007-07-01
I have some problems with my Dimension E521. I have AMD 64 Ahtlon X2 + 5000 and the only Ubuntu i can install is the 32-bit version. 

The 64-bit version never com further than the place where i chose to install..

Any tips?

---

### Post by khedron on 2007-07-01
Is that the part where you are choosing your partition layout?

(As an aside, I would recommend you stick with Ubuntu 32-bit, unless you specifically want to try 64-bit out. There are some third-party applications (and possibly drivers) that just don't work with 64-bit. For example, Flash is only released in a 32-bit flavour. This means that if you want the Flash plugin for Firefox, the whole of Firefox must* also be 32-bit. This could apply to Open Source projects, as well as commercial - 32-bit is much better currently in terms of compatibility.

Obviously, you can decide on your own whether you want 64-bit or not, but with some of your applications having to be 32-bit, I would wonder whether there is any point having a 64-bit OS.

* I believe that this might not technically be necessary, but it is certainly much harder to mix 64-bit Firefox with 32-bit plugins.)

EDIT: Sorry that the aside turned into a rant larger than the actual question. :) Could you give me some more detail on where the error happens, and I'll try to help.

---

### Post by capitol on 2007-10-04
Hi

The installer freezes right after the splash screen where you can choose "Start or install Ubuntu" or "Memory Test" and so on.

---

### Post by khedron on 2007-10-05
I'll try to help, but I'm afraid I don't have access to my Ubuntu now (3 month holiday! Yay!) so I can't test anything to see what works.
 
When you get to that splash screen, press F6. (It should be marked as "Other Options".)
 
You will be presented with a line of text that says something like 
```
Boot Options casper initrd=/casper/initrd.gz quiet splash --
```
[IMG]http://bourlas.yooblog.gr/files/2007/06/ubuntu02.jpg[/IMG]
 
What you need to do is delete "quiet" and "splash" from that line, so you get 
```
casper initrd=/casper/initrd.gz --
```
Then press Enter.
 
This puts Ubuntu into text mode (no splash) and makes it say everything it is doing (not quiet). Text will start scrolling off the screen quickly as Ubuntu boots up. 
 
Could you tell me the last 5 or so lines before the freeze happens? You don't have to give the number in brackets at the beginning of each line, and if any of the lines are too long, just skip any numbers/codey looking things out and replace the with a [...] or something when you write me the lines.
 
This should help me figure out what the problem is.
 
Cheers,
Khedron

---

