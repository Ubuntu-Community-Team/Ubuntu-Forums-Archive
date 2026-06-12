---
title: "Jaunty 9.04 - Missing Splash Screen on Shutdown/Restart"
date: 2009-05-08
forum: General Help
---

### Post by fermulator on 2009-05-08
Hey there all,

When we shutdown or restart the system with any previous version of Ubuntu (intrepid, hardy, heron, edgy, etc.), I'm used to seeing the **"splash"** screen **"unload"**, then the system shuts down (or restarts).

**_Problem_**:
When I shutdown or restart in Jaunty 9.04, there is no splash screen present, just a black screen.  I can hear/see the hard disk working on the shutdown procedure, so 'stuff' is happening at least, and then it shuts down or restarts.  The process of shutting down and restarting is quite quick, so it's not a huge deal, but I'm still curious as to why I don't see the 'pretty' splash screen.

NOTE: The splash screen on startup is fully functional and works great!

Does anyone else have this problem with Ubuntu Januty 9.04?
or
Any idea how to troubleshoot such a problem?

EDIT:  Sometimes the system will never shutdown/restart.  With a blank screen, I'm not sure where the system is getting stuck during the shutdown sequence ...

Thanks

---

### Post by iain123 on 2009-05-18
Yea,  I have the same problem.  Only it's with Kubuntu 9.04.   

Real Pain.  Cannot get the tty consoles either.  System Got screwed after trying to install drivers to improve Intel Graphics using Compiz.  Screen was all over the place and often scrambled.  After a few minor tweaks in the Xorg.conf file Compiz works normally now but now I have another several problems to deal with.  

Problem 1
When you edit file from command using: sudo kate /etc/file.  
I get a little message - Xmessage box appear on screen saying: "could not start ksm server Check your installation" and when you click OK the whole KDM session bombs out and brings me back to login.  

Problem 2
Black screen on console when I switch using Ctrl & Alt & F1.  

Problem 3
No kubuntu splash screen on shutdown.  

Somehow I think they all maybe related somewhere along the way.

Using Tosh Laptop with Intel 855GM integrated graphics.  

I am highly tempted to downgrade back to Hardy.  At least these issues did not rear there ugly heads.  I have not been impressed with Jaunty one bit.  Had to upgarde my VMware console as a result.  

That's my rant

Iain

---

### Post by fermulator on 2009-06-12
Well, I know it's not a Jaunty specific problem.  I mean to say, I've installed Jaunty on other systems and they have no problem with a missing splash screen on shutdown.

It's only for my main desktop PC.  It's most likely a configuration problem or something.  Problem is, I don't really want to reinstall the OS just to fix such a minor problem.

Hoping for some help troubleshooting to dig deeper.

---

