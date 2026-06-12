---
title: "Up and Down Splash Screen"
date: 2007-10-29
forum: Desktop Environments
---

### Post by mrfelker on 2007-10-29
I think this might be the right forum for this post.

I installed Ubuntu from the Ubuntu CD - the default desktop is of course Gnome

Then I wanted access to the the kubuntu desktop and KDE programs so installed the kubuntu desktop using Synaptic.  Perhaps I should have used apt-get or aptitude but the result should have been the same.

During the install it asked the question whether I wanted gdm or kdm as the logon manager.  I chose gdm - however at this point I use auto login but will change that to timed after this post.

Now when I shutdown Ubuntu the downsplash screen is the blue Kubuntu splash image.  But when I boot Ubuntu the the upsplash screen is the brown Ubuntu splash image.

This has happened in earlier versions of Ubuntu (I am now using 7.10).  I don't particularly mind this behavior - but I don't understand how it could happen.

Anybody else have this situation?  If developers monitor these  forums perhaps they
could tell me??

---

### Post by Jhongy on 2007-10-29
yes it always happenned to me to.

I think you do something like sudo dpkg-reconfigure --update-alternatives usplash to see all the usplashes available?

---

### Post by sdyson on 2007-12-08
This worked for me: 

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_change_the_USplash_Screen_on_startup.2Fshutdown](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_change_the_USplash_Screen_on_startup.2Fshutdown)

---

