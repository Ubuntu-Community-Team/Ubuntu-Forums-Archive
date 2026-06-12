---
title: "wine Internet Explorer problem"
date: 2006-07-17
forum: Desktop Environments
---

### Post by Kurt_Alan on 2006-07-17
****

Internet Explorer is installed and on my desktop.  When I open it, the wine website requires a Mozilla Active X control.  After that is installed automatically, the IE icon, when I try to open it, flashes open for a split second, then closes. 

So, no IE. Any ideas?

---

### Post by aysiu on 2006-07-17
IEs4Linux

---

### Post by Torched-Geek on 2006-07-17
Change to Mozzilla Firefox ? I know it rocks in Windows XP, havent had the pleasure of using it in Ubuntu yet however. (Mouse isnt working)

---

### Post by aysiu on 2006-07-17
> **Torched-Geek said:**
> Change to Mozzilla Firefox ? I know it rocks in Windows XP, havent had the pleasure of using it in Ubuntu yet however. (Mouse isnt working)
Some people have Internet Explorer installed because they're web designers and want to see how their websites look in the browser most people use.

Other people keep IE around for those few sites that won't work with Firefox (yes, even with the User Agent Switcher extension installed).

---

### Post by Kurt_Alan on 2006-07-19
****

Thanks, Aisyu, for your recommendation of IEs4Linux.  This was my first experience assembling a packgage from the console.  It was interesting and I am up and running in my new IE browser.  Next, for practice, I'm doing my first compile from source using Dillo.

Here's a question.  The only evidence I have of my IE app is one little icon.  It does not appear in Applications.  Can I drag the icon there?  Windows, as you know, as a lot of redundancy in its programs: desktop, program menu, taskbar, quick launch, etc.

It seems that Linux has too little redundancy.  Am I missing something? What happens if I lose my IE icon?  How do I find and/or locate the program?

---

### Post by aysiu on 2006-07-19
I believe the actual program launcher is in /home/kurtalan/bin/ie6

I would move it somewhere more useful: ```
sudo mv ~/bin/ie6 /usr/local/bin/ie6
```

---

### Post by XPuntu on 2006-07-20
> **aysiu said:**
> IEs4Linux

Aysiu:KS , I appreciate all the help you do for all the new users, but how does this response address the question?

**Just a little peeved because this just happened to me. And I want to know wha'happened?

---

### Post by aysiu on 2006-07-20
> **XPuntu said:**
> Aysiu:KS , I appreciate all the help you do for all the new users, but how does this response address the question?

**Just a little peeved because this just happened to me. And I want to know wha'happened?
It helps because IE is a tricky program to install in Linux, and IEs4Linux is a script that does it all for you.

---

### Post by harryhoudini66 on 2006-07-20
Aysui: Thank you so much for the advice. It worked great for me. I had been trying to install it using winetools for days. This did it in seconds and all is good.

---

### Post by XPuntu on 2006-07-21
Aysui, what you say is true. But as the original post asked "Why"? 

I followed a tutorial on how to set up wine and install the font packs, etc and IE worked splendidly. Then two days ago, I was asked to install the active X controls and wound up with the problem Kurt_Alan posted about. I'll never learn anything if the solution is just "load a different program".

I've installed IEs4Linux btw. Will I have a similar problem in the near future? 

PS. Not angry, just trying to understand...

---

### Post by aysiu on 2006-07-21
I don't know. IE--not being a native application--is subject to periodic weirdness. I can't predict what sort of errors may appear in the future, whether you're using vanilla Wine or IEs4Linux.

I just suggested IEs4Linux because I know it works. It sounded as if the OP was trying to install IE through Wine manually and not having much success.

---

### Post by XPuntu on 2006-08-01
As an update, I've ditched WINE and now use VMWare server. I'm happy with the result since I don't play a lot of graphic intensive apps. I do a lot of video editing and transcoding and Win in Virtual machine seems to work like a charm

Cheers :-D

---

### Post by josys36 on 2006-08-01
For me Firefox runs great under Wine, and is the only way I can get AOL Radio to work using Ubuntu. But hey, it works and I have had no problems.

Jason

---

