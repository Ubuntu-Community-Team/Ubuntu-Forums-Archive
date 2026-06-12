---
title: "How to save customization as global defaults in Remastersys ISO ?"
date: 2009-04-24
forum: General Help
---

### Post by Jags_FL on 2009-04-24
Using Remastersys > Dist option, I just built an ISO and though ISO did include the theme (Solairs' Nimbus) I installed, it was not selected as default. Also ISO didn't have any Desktop, Firefox etc. customization I had made.

I'm trying to build an ISO with following customization: 

1, Nimbus theme as default
2, Customized desktop look : Removed bottom panel, Main Menu (instead of Menu bar), added app icons on top panel etc...
3, .gtkrc-2.0 saved with "gtk-menu-popup-delay = 0" to make GNOME menu faster 
4, Firefox nightly (3.6a1pre) with changed preferences & some extensions installed already
5, Activated Firehol with it settings saved as default

Now going thru Remastersys forums I did find [this post in which its developer says]("http://geekconnection.org/remastersys/forums/index.php?topic=111.msg864#msg864") "the global system defaults are what they were before and this is what the ubuntu casper scripts use to setup the live user.  You need to change these and I don't help with these"

So how can I make changes/customization as **global defaults** instead of user specific. Many thanks in advance, any help is highly appreciated. - Jags

---

### Post by Jags_FL on 2009-04-24
anyone on Remastersys ?? Thanks.

---

### Post by inthevidual on 2009-09-21
I suppose this has already been resolved, but the easiest way to 'globalize' user-specific settings in my experience, has been to copy the home folder of the user that has all the customizations, to /etc/skel. /etc/skel holds the 'default configuration' that is copied into every new user's home folder.

---

### Post by Jags_FL on 2009-09-22
@ inthevidual

Thanks alott. I didn't know about this. Next time I'm gonna give it a try.

---

