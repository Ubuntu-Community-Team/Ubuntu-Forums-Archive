---
title: "shutdown/reboot icons in kubuntu gutsy 7.10 with XGL and COMPIZ on a ATI card"
date: 2007-11-04
forum: Desktop Effects &amp; Customization
---

### Post by giobik on 2007-11-04
Hello everybody!
 this is my first question in this forum, in the past I managed to fix my problems following some howtos...
 I ask sorry for my English, I'm Italian... I'll try to write the best I can!

So, this is my problem:

 I freshly installed Kubuntu Gutsy 7.10 on my laptop some days ago... I installed the restricted drivers for my ATI card and I wanted to try Compiz Fusion. 
So I installed xserver-xgl, compiz-kde, ccsm an many other packages as I read in many howtos...
Everything worked perfectly! This is very cool!

[SIZE="3"] [COLOR="Red"]Now, when I try to shutdown the pc by pressing the K MENU -> "End Session" the SHUTDOWN/RESTART icons doesn't appear! It appears only the log off button, so to turn off the pc I must LOGOFF from kde and use the buttons in KDM![/COLOR][/SIZE]

Does anybody have the same problem??? Please tell me I'm not the only one!

Thank you for your help!

Bye!

giorgioB

---

### Post by jeroenvdw on 2007-11-07
you're not the only one... i'm searching for a solution for about a week now, still not found anything that works...

somebody help?

---

### Post by Caffeine_Junky on 2007-11-07
Hey there...

Have a look at this link and see if it helps sort things out for you, It suggests to un-install the 'xgl-xserver' package: 

[http://kubuntuforums.net/forums/index.php?topic=3088244.0](http://kubuntuforums.net/forums/index.php?topic=3088244.0)

Also have a look through the search results here:
[http://ubuntuforums.org/search.php?searchid=30783330](http://ubuntuforums.org/search.php?searchid=30783330)

---

### Post by Caffeine_Junky on 2007-11-07
oops!    Deleted!  (I made a double post) :o

---

### Post by fikiman69 on 2008-02-21
Remove XGL and install Emerald:)
Saved me a lot of time.

---

### Post by shadecc3 on 2008-02-21
I had the same problem until I had reinstalled ubuntu and somehow the buttons came back again.   But during that time, I ended up using the terminal to shutdown.

shutdown is "sudo shutdown -h now"
restart is "sudo shutdown -r now"

---

### Post by giobik on 2008-02-21
> **fikiman69 said:**
> Remove XGL and install Emerald:)
Saved me a lot of time.

I cannot remove XGL because my ATI X700 doesn't work with the open source drivers!

I will try some new drivers from ATI but I've read that the last drivers have some problems with Firefox and video playback...

Bye!

---

