---
title: "Kubuntu + composite/xcompmgr working...need help with some configuation."
date: 2008-04-16
forum: Desktop Effects &amp; Customization
---

### Post by Meskarune on 2008-04-16
I have a radeon ati mobility 9800 graphics card for my laptop. I set up the fglrx driver. I also have 2 gig of ram and 20 gig for my Xubuntu partition with +-300 mb swap. 

My friend convinced me to switch over from fluxbuntu. So I loaded up Xubuntu Gutsy. De-bloated the install a bit, but decided to mess with compiz-fusion before getting rid of it. I got xgl up...but it used so much memory I couldn't go any further and just uninstalled it and compiz. 

I heard about xfce having its own composite manager, so I enabled it by editing xorg.conf and wmtweaks.xml and then created my own on/off button using[ this guide.]("http://ubuntuforums.org/archive/index.php/t-272890.html") This is what xfce's comp manager looks like in use:

[[IMG]http://b.imagehost.org/t/0512/xfce.jpg[/IMG]](http://b.imagehost.org/view/0512/xfce.png)

It also allowed cairo clock to work. But it has some problems with rendering menues and messing up some of the window contents (I would just have the panels transparent...but even the non-transparent stuff gets messed up) I don't know if its my graphics card or what...or if I need to do some more configing. That theme was the original xfce theme, so it anything was going to work with transparecy that should have. 

Anyway, I just installed xcompmgr and transset. I ran xcompmgr in the terminal with "xcompmgr -c" and then did" transset n" to make various windows translucent. Iit looked really nice and didn't seem to have memory problems or problems rendering the menues...the start menue would scramble for half a second before rendering correctly but other than that there really wasn't anything I could see. One thing that is really different is not being able to confige stuff like I did with xfce's settings manager.

Can I make xfce's settings manager use xcompmgr instead of its native compositioning manager? Is there other things I can do to make my graphics card work better? Also, could I make an on/off button for xcompmgr? (This is so I can turn it off when I do hardcore cpu  stuff like rendering with blender)

I would also like to have a dock. (you can see in the screenshot I'm sort of using my xfce panel as one) I downloaded cairo dock, but could not get it to work. It would start and show up in the process list...but nothing would happen on the desktop, even with xcompmgr working. I also downloaded gdesklets to try and use the launch bar...and the launch bar would not work. It would start, but I could not add anything to it using the right click menues. AWN Dock will not work at all. (my graphics card isn't friendly with it)

Any help configuring xcompmgr and maybe getting the gdesklet dock or cairo dock/ gnome dock to work would be much appreciated.

---

