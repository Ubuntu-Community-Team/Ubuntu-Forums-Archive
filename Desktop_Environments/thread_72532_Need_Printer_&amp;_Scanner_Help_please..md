---
title: "Need Printer &amp; Scanner Help please."
date: 2005-10-06
forum: Desktop Environments
---

### Post by YeshuJah on 2005-10-06
I recently installed Breezy Badger 5.10 on my home computer and I love it! (Still dual booting Win XP though).This is the only alternative to Windows I've used that didn't keep me up nights.  I even like it better than Steve Job's OS; and I tried that too! (I'm telling everybody I know about you guys:smile: )

But I gotta a problem- well, two in fact. I want to install Ubuntu on all the machines in my house (I have 5 on a LAN), including my 5 yr old's machine (She loves the games!) but I cannot get my Pixma IP1500 printer which is networked through a D-Link Model DP-300U (printer connect is USB)to work! :confused: 

I cannot convince the wife to switch:rolleyes:  if I cannot get this printer working, and my son (15 yrs old) will also need it to print his school work.  Can someone help me?  

Less important to the family, but important to me is that I also cannot get my Epson Perfection 1250 Scanner to work under Ubuntu.  I'd appreciate some help here too. Thanks.

P.S. if this is not the place for this post please re-direct. I am new to these surroundings.

---

### Post by aysiu on 2005-10-09
I'm thinking you're right--Ubuntu Backports probably isn't the place to put this. I'm moving the thread to a more appropriate spot. Congratulations on getting Ubuntu to work. Hopefully we can get all this peripheral stuff worked out, too.

---

### Post by aysiu on 2005-10-09
By the way, can we assume you've already done these two Google searches?

[http://www.google.com/search?hl=en&q=%22Pixma+IP1500%22+linux&btnG=Google+Search](http://www.google.com/search?hl=en&q=%22Pixma+IP1500%22+linux&btnG=Google+Search)
[http://www.google.com/search?hl=en&q=%22Epson+Perfection+1250+Scanner%22+linux&btnG=Google+Search](http://www.google.com/search?hl=en&q=%22Epson+Perfection+1250+Scanner%22+linux&btnG=Google+Search)

---

### Post by YeshuJah on 2005-10-10
Thank you. I will look at the Google searches you provided. Can you direct me to where this post was moved?

---

### Post by robins_web on 2005-10-10
The best place to look for general and specific printer support is at
[http://www.linuxprinting.org/](http://www.linuxprinting.org/)

What I discovered during my adventures with Kubuntu and a Canon S300 printer (which I ultimately replaced with an HP) is this:
Canon + Linux = not good
HP + Linux = Good

I found an HP psc1315 printer/scanner/copier all-in-one at Sam's Club for under $65. Worked perfectly the first time.

---

### Post by rplantz on 2005-10-13
YeshuJah,

I described what I did to get my usb printer (Epson CX6400) to work in Breezy here:

[http://www.ubuntuforums.org/showthread.php?t=74289](http://www.ubuntuforums.org/showthread.php?t=74289)

My post is #5 in the thread.

Please let me know if it works for you.

Bob

---

### Post by throntax on 2005-10-19
Hi
I recently upgraded to breezy from hoary, and found that my Epson Perfection 1260 photo under xsane was producing errors like
Scanner busy and occasionally I/O error, 

which was confusing because everything worked fine with hoary..

after some diggin' around I found that removing 
libsane-extras and libsane-extras-devel provided the trick and everything went back to normal. 
Perhaps this could help with your epson scanner? I hope so...

btw I Ubuntu is really, really rad, and this problem took me only 1/2 and hour to find a solution to, rather than the usual couple'o'days, so yay more scan and coffee time :D

---

### Post by MorayJ on 2006-07-02
[QUOTE=throntax]

after some diggin' around I found that removing 
libsane-extras and libsane-extras-devel provided the trick and everything went back to normal. 
Perhaps this could help with your epson scanner? I hope so...
[/QUOTE]

Just joined this forum to say that you are a star! Removing libsane-extras kick started my Epson Perfection 1260 immediately (I didn't have libsane-extras-devel installed).

Was just beginning to fume, having bought it as I had read that it was Linux compatible.

Thanks for posting this solution

MorayJ

---

