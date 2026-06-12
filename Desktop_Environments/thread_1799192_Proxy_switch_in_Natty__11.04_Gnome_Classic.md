---
title: "Proxy switch in Natty / 11.04 Gnome Classic"
date: 2011-07-07
forum: Desktop Environments
---

### Post by kngharv on 2011-07-07
Dear all:

Ever since I upgraded to Natty / 11.04, the quality of my desktop experience has dropped sharply.  

One thing that effect me greatly is that I can no longer conveniently switch my network proxy on or off system-wide with single click.

Back in Maverick / 10.10, I could launch gnome-network-properties and switch it back and forth depends rather I am at work or at home.

I have found a similar application, "gnome-control-center network,"  on the surface of it, it seems to replace "gnome-network-properties" in Maverick.   Except that this application doesn't seems do ANYTHING.

As result, I am having the hardest time switching my proxy settings, as I have to do so per application basis  (gpodder, pidgin, aptitude, thunderbird / firefox, etc). 

has anyone figure out how to switch proxy on and off at the OS level, like the good old days?


Thanks in advance


Harv
ps.  I am using Gnome "classic"  but Gnome 3 suffers the same issue

---

### Post by mErchamion on 2011-07-11
Well, if you are using a gnome-panel based desktop, you can install gnome proxy applet by this guy:
[http://www.andreafabrizi.it/?proxyapplet](http://www.andreafabrizi.it/?proxyapplet)

I am not using unity nor gnome-shell, but, I have once tried it out in unity, you still have the proxy settings for gnome: just do Alt+f2 (or watever to get that awfull application panel) and type "Proxy", you will find the gnome-network-properties and in 2 or 3 clicks you will have the proxy set systemwide. 

Now, for gnome-shell, it is quite hidden, but I remember to have seen it in the  system configuration took: look for network configuration an in one of the 2 (?) option available you have some tag for proxy setting.

Hope this help You. By the way, I am looking for something like proxy applet but for awn, Any ideas?

---

### Post by mErchamion on 2011-07-11
You should also take a look at proxindicator:
[http://www.ubuntuupdates.org/packages/show/361026](http://www.ubuntuupdates.org/packages/show/361026)

in launchpad for ppa:
[https://launchpad.net/~domurb/+archive/domurb-projects](https://launchpad.net/~domurb/+archive/domurb-projects)

just add the ppa, update and isntall proxindicator. It works for me with awn, hope it works in unity and gnome-shell.

---

### Post by held7over on 2011-07-12
Thanks SteveDee!

I didn't know I could also change it in Menu/Preferences/Openbox Configuration Manager/Desktops  I had a misconception of what Openbox was and had left it alone...

That worked great! 

I am betting your suggested file edit would have worked also. I have no idea why the direct approach via panel preferences didn't work.

Sorry it took so long for me try this....I was otherwise occupied elsewhere and we are having terrific electrical storms in the evenings here. Quite beautiful if you like lots of bright explosions in the sky like atomic bombs going off....I tend to shut down and unplug EVERYTHING COMPUTER RELATED in those things...

Thanks again! And thanks to everyone that interacted with me on this! :D

---

