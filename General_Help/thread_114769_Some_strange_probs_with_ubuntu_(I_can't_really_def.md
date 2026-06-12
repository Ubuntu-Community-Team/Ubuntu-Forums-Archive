---
title: "Some strange probs with ubuntu (I can't really define it)"
date: 2006-01-09
forum: General Help
---

### Post by Snooz on 2006-01-09
**The story**

A few months ago I started with ubuntu, I had some troubles then, but I managed to get it all working. Sadly enough, I had to do a full format early this week. I tought, well, I know what I have to do, it can't be that hard then it was the first time.

So I downloaded the latest version of ubuntu, installed it (all went fine). Until I logged on in Gnome. To my surprise, my network card didn't see all the access points it needed to see (only that on from my neighbors, it's an IEE802.11b, all the other are IEEE802.11BG). There were also numerous problems with the dns (that I fixed eventually, but they shouldn't have been there :s).

So now I always have to connect manually to my access point (iwconfig eth 0 mode .......). No problem you think, but as SOON as I log on to the Internet, the start up time of some applications take as long as 5 min or so. The apps I'm talking about are:

1. System-->preferences-->Users and groups (it takes 5 min untill i can see    
    the screen)
2. Sudo gedit (in terminal): This just never comes up (I CAN use it when I'm 
    not connected to the internet)
3. Installing something with synaptic (it takes FOREVER to install the j2r 
    packages)
4. Altering network connections

I can see a pattern in these "errors": All those things need sudo (or promt for a root password).

The system I use is:
Acer Travelmate 8106 and it has a intel pro wireless card (2195BG or something like that).

Can you please help me, I don't know what to do anymore :(.

grtz

---

### Post by BathroomNinja on 2006-01-09
Just to satisfy my crazy mind, can you boot up with the 5.10 Live CD and see if you get the same issues after you have connected to the internet?

EDIT- Also, if you have installed Automatix, can you try CTRL-ALT-DEL to see what program is taking up all your resources after you try to use one of those programs?

---

### Post by Snooz on 2006-01-09
I'll need to download the live cd. I'll check if my problem goes away then.

I do not have Automatix installede, but I can look ak top to see wich program is causing the problemen.

The probleme is that everyting is normal.
When I try "sudo gedit"
gedit pops up at 10% and then dissapears again :(.
When I try "gedit" it stays at 10 %.

I wonder if there's something wrong with the sudo :s.

---

### Post by earobinson on 2006-01-09
looks like an sudo problem, you coulded enable the root account and use su see if that helps... see MY FAQ in my sig question 1

---

### Post by braynyac on 2006-01-16
I'm having similar problems - except I have others...Azureus takes about 10 minutes to load, then eats ALL processor performance.  I use Citrix for work, and my connection to our published Outlook takes about 10 minutes to load after authentication as well.  

I searched the forums to no avail...I'm going to try reinstalling sudo, see if that helps.  Anyone have any ideas?  Thanks!

~braynyac

---

### Post by RAOF on 2006-01-16
My guess is that IPv6 support is being crazy again.  If your AP doesn't support IPv6, Ubuntu will still try it when resolving domains & stuff (and sudo needs to resolve the *localhost* domain).  Then, because the AP doesn't support IPv6, the request times out eventually & Ubuntu tries (the normal, everyday) IPv4, which does work.

You could try following [these instructions]("http://www.ubuntuforums.org/showthread.php?t=87798") to disable IPv6 support, then try again?

Oh, and @braynyac - have you installed a Java runtime environment?  Because if you haven't, you'll be using the gnu classpath opensource Java (almost) runtime.  As you've noticed, it doesn't run Azureus particularly well :)

---

