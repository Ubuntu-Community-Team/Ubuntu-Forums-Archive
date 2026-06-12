---
title: "Stuttering Firefox scrolling using Beryl...FIX?!"
date: 2007-05-29
forum: Desktop Effects &amp; Customization
---

### Post by antifaithstl on 2007-05-29
First, the nitty:
HP 6205us Vista laptop (minus Windows ME II...er...Vista of course), with a Intel 945gm video card.  512 DDR2 RAM, Dual 1.6Ghz Intel P4.  
Now the gritty:
I installed Beryl a few days ago using the guide found on the Beryl Wiki [here,]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL") & it runs pretty good on this low-end Vista basic laptop.  The flames Rawk.  
The ONLY drawback was that Firefox scrolled a page like Jerry's kids walk. 
The guide had me create a separate log-in session to use Beryl (xgl), which of course I used when I ran Beryl.  But the Firefox scrolling was still bad.
I went about 3 days searching for a fix w/ no luck.
Then I tried starting the Beryl manager in the normal Gnome log-in session.  Not only did Beryl load w/ all the features working as good as they did logging in using the special "XGL" session, but **the FireFox stutter was GONE!  **
Why is this?  Is this a fix?  Why create a separate XGL log-in session if I can just start it up using plain old Gnome?  Is my laptop gonna blow the F up if I don't log in w/ XGL???

---

### Post by FuturePilot on 2007-05-30
You don't need XGL anymore with Xorg 7.1 or later. XGL is an old hacked up xserver. When you create an extra XGL session what happens is XGL gets loaded as a layer on top of xserver which uses up a lot of RAM. So with more RAM being used, Firefox ran slower. Now without XGL you have a little more RAM and things will run a bit faster.

---

