---
title: "[SOLVED] compiz raise on click problem"
date: 2008-01-13
forum: Desktop Effects &amp; Customization
---

### Post by zenkaon on 2008-01-13
Hello,

I am running kubuntu 7.10 with compiz fusion. I have emerald set up and a nice theme. All works fine.

I was hoping somebody could help me with a setting. I cannot turn on the general options -> focus & raise -> raise on click. When I tick the box, it promptly unticks itself. This has a very annoying effect that unselected windows are left in the foreground.

Any hints?

---

### Post by SnakeSkin on 2008-01-14
Hi..... You are not alone......I had the same problem. Just found a fix! :-)

Look at [http://ubuntuforums.org/showthread.php?t=503145&page=2](http://ubuntuforums.org/showthread.php?t=503145&page=2)

Easy fix. I spend maybe total of 20 hours, 10 re-installs.......

I am SO happy it is not fixed!

---

### Post by Forlong on 2008-01-14
> **zenkaon said:**
> I was hoping somebody could help me with a setting. I cannot turn on the general options -> focus & raise -> raise on click. When I tick the box, it promptly unticks itself. This has a very annoying effect that unselected windows are left in the foreground.
Go to *Preferences* (in ccsm) and disable **Enable integration into the desktop environment**

---

### Post by zenkaon on 2008-01-15
Fixed it. Thanks to AlienPlanet for the fix.

Here's how I got it to work:

   1. Opened K->System Settings->Window behavior (Look & Feel section)
   2. Selected Window Behavior (first icon on the left side), clicked "Focus" tab.
   3. Under Focus Policy (dropdown), selected Focus follows mouse (this is what I like)
   4. Checked the "Click to raise window" checkbox and hit Apply button.
   5. Then I quit compiz config settings and KDE window behavior system settings.
   6. Final step: Reloaded compiz to see the new changes (typed "compiz --replace" without the quotes in "run command" window (ALT F2))


Thanks AlienPlanet

---

### Post by phishinphree on 2008-02-04
thanks.  The last post does indeed fix the problem. :-)

---

