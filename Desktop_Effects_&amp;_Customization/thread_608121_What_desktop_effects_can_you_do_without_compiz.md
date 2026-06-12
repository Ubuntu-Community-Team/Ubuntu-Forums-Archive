---
title: "What desktop effects can you do without compiz?"
date: 2007-11-09
forum: Desktop Effects &amp; Customization
---

### Post by dboot on 2007-11-09
After spending several weeks trying to get Compiz Fusion to work on my laptop (Dell c840 with a Geforce 440 Go), I've decided that it can't be done. I was only able to enable "desktop effects" after forcing compiz to skip all error messages with an outcome of black content within each window.

So, what desktop effects can I do that doesn't involve Compiz Fusion?

Thanks!

---

### Post by luisromangz on 2007-11-09
If you are using KDE, you can enable window shadows and transparency in KWin (KDE's window manager). I used to do this way before the Compiz project started, and it only needed the xorg's XComposite extension to be enabled.

It worked with my GForce440MX, so I think it maybe works with your card too.

---

### Post by ardchoille42 on 2007-11-09
None, desktop effects aren't useful, they're just for show. Compiz is a worthless resource-wasting toy.
</opinion>

---

### Post by atomkarinca on 2007-11-09
have you tried [beryl]("http://www.beryl-project.org/")?

---

### Post by dboot on 2007-11-09
When I used desktop effects on my desktop, I found that only after I install compiz fusion and awn was I able to fully utilize multiple desktops. I'd like that for my laptop too. Of course, I agree that there are lots of useless showy aspects of compiz mixed in with the functional features.

I used to use beryl and enjoyed it a lot. I'm under the impression that beryl is the older version of the same program and therefore won't work either. I'll give it a shot.

---

### Post by arbulus on 2007-11-09
I'm on the fence with desktop effects.

Firstly, I think they are brilliant for what they have brought to the Linux world.  They've taken Linux in general and thrown it out there with the big boys.  I think the things Compiz Fusion can do is infinitely better than Aero or anything in Leopard.  So many people have switched to Linux just based on having seen a nice 3D desktop.

However, on everyday usage, I think I've decided that I really don't care for it that much. I do like a nice looking desktop, but I also want it to be functional, and the function comes before form.  I want a USEFUL desktop that looks good.  Compiz Fusion bogs down my machine (and I have 1GB of ram and a 128MB video card).  I really like Avant Window Navigator.  I think it's an amazing app.  However, you have to have a compositor to run it, which is frustrating.  Honestly, if it weren't for AWN, I wouldn't use Compiz fusion, just because it takes up too much resources. And it frustrates me that such a great dock app can only be used with a compositor.  Now if I had 4 GB of ram and a 256MB or 512 MB video card, then it wouldn't be a problem because I'd have enough resources to spare.

But honestly, I've been using Openbox as my GUI for a while and I really dig the sleekness and customizability of it and I also like a desktop that is ready to go from login in under a couple of seconds. I really feel like I can get some work done, but I feel like I can also have fun. 

So while I think Compiz Fusion has done amazing things for the community and has pushed Linux development is great new ways, it does get in the way of performance. 

If only there could be a dock as great as AWN that can run without a compositor, I'd be in heaven.

---

### Post by Zorael on 2007-11-09
I've really come to like Expo and Group/Tab Window. Sure, the cube is eyecandy and nice to show yet-to-be-converted Windowlings, but it's hardly more useful than Desktop Wall, in my eyes.

I'm not sure I could ever live without Expo now that I've tasted its deliciousness. Damn your eyes, Expo.

---

### Post by dboot on 2007-11-09
> **Zorael said:**
> I've really come to like Expo and Group/Tab Window. Sure, the cube is eyecandy and nice to show yet-to-be-converted Windowlings, but it's hardly more useful than Desktop Wall, in my eyes.

I'm not sure I could ever live without Expo now that I've tasted its deliciousness. Damn your eyes, Expo.

What is Expo? An add-on of Compiz Fusion?

---

### Post by urukrama on 2007-11-10
> **arbulus said:**
> If only there could be a dock as great as AWN that can run without a compositor, I'd be in heaven.

You should be able to run it with xcompmgr, which is a compositor, but much lighter than CompizFusion and the like and usable in other window managers, like Openbox or Fluxbox.

Xcompmgr can give you shadows, fading menus, and if used with transset, true transparency. [Here]("http://ubuntuforums.org/showthread.php?t=75527&highlight=xcompmgr+howto") is an excellent howto to set it up and configure it to your liking.

You can use skippy for an expose-type overview of open, uniconified windows. I quite like it, and use it often when I don't use a panel.

You can also use 3ddesktop to have a cube to switch desktops. I've never used it, though.

---

### Post by spec-chum on 2007-11-10
> **dboot said:**
> What is Expo? An add-on of Compiz Fusion?

Yep.  This is Expo.  You can drag apps from one virtual desktop to another there.  It is very handy, and I use it all the time too.  That and the Scale plugin are the two plugins I use over and over.

---

### Post by jviscosi on 2007-11-10
> **urukrama said:**
> You should be able to run it with xcompmgr, which is a compositor, but much lighter than CompizFusion and the like and usable in other window managers, like Openbox or Fluxbox.

Indeed, I've found that Fluxbox in particular works well with xcompmgr because it supports transparency of focused/unfocused windows, dock, menu, etc.

> **urukrama said:**
> Xcompmgr can give you shadows, fading menus, and if used with transset, true transparency. [Here]("http://ubuntuforums.org/showthread.php?t=75527&highlight=xcompmgr+howto") is an excellent howto to set it up and configure it to your liking.

Also, [devilspie]("http://burtonini.com/blog/computers/devilspie") can give you control over window classes and types, which in turn affects how xcompmgr effects are applied to them.  For instance I used to use devilspie to turn gdesklet widgets into docks, which prevented them from being shadowed.

> **urukrama said:**
> You can use skippy for an expose-type overview of open, uniconified windows. I quite like it, and use it often when I don't use a panel.

I found that skippy-xd caused a significant slowdown in other effects, especially 3ddesktop.  (I set up a keybinding for kompose instead, though I hardly ever use it.) Have you experienced that or does it all work fine for you?

> **urukrama said:**
> You can also use 3ddesktop to have a cube to switch desktops. I've never used it, though.

Oh ... never mind my question above.  Dboot, if your experience is like mine, skippy-xd and 3ddesktop won't play nicely together.  I ended up deciding I wanted 3ddesktop more than I wanted skippy-xd.  If you try running both, I'd be interested in hearing if skippy-xd slows 3ddesktop down for you as well.

Note that skippy-xd will terminate if you bind it to a key that's already assigned to a different function, with a message similar to this one:[INDENT][B]X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  33 (X_GrabKey)
  Serial number of failed request:  77
  Current serial number in output stream:  77
[/B][/INDENT]

---

### Post by urukrama on 2007-11-11
> **jviscosi said:**
> I found that skippy-xd caused a significant slowdown in other effects, especially 3ddesktop.  (I set up a keybinding for kompose instead, though I hardly ever use it.) Have you experienced that or does it all work fine for you?

I generally don't use xcompmgr and skippy together, and as I mentioned I don't use 3ddesktop. 

Are you aware that skippy and skippy-xd are two different applications. From the [skippy website]("http://thegraveyard.org/skippy.php"):

[INDENT]> Skippy-XD is a version of Skippy that uses the new XDamage, XComposite and XFixes extensions (found in FreeDesktop.org's Xserver project) to provide you with 'live' versions of the windows. Exciting, isn't it?[/INDENT]

I've never used skippy-xd as I don't need 'live' versions of my windows. I suppose skippy-xd uses more resources than skippy, and since it uses xcomposite it is likely to create some difficulties with xcompmgr.

---

### Post by jviscosi on 2007-11-11
> **urukrama said:**
> I generally don't use xcompmgr and skippy together, and as I mentioned I don't use 3ddesktop.

Yeah, that's why I said "never mind" in [Emily Litella]("http://en.wikipedia.org/wiki/Emily_Litella") fashion.  ;-)

> **urukrama said:**
> Are you aware that skippy and skippy-xd are two different applications. From the [skippy website]("http://thegraveyard.org/skippy.php"):
I've never used skippy-xd as I don't need 'live' versions of my windows. I suppose skippy-xd uses more resources than skippy, and since it uses xcomposite it is likely to create some difficulties with xcompmgr.

Yep, I'm aware of that.  As I recall "regular" skippy wouldn't run properly with some or other extensions (composite-related, I think) enabled in xorg.conf, but it's been a long time since I used it and I don't remember exactly what the problem was.  But anyway the upshot was I had to run skippy-xd if I wanted the compositor running.  (I should have clarified this in my original reply.)

I just tried it again and skippy still won't fire on my machine, but skippy-xd is performing a lot better than I remember with both xcompmgr and 3ddesktop.  I did recently upgrade my video card to a 512MB GeFORCE 7600 which probably helps ...

---

### Post by brickbat on 2007-11-11
> **ardchoille42 said:**
> None, desktop effects aren't useful, they're just for show. Compiz is a worthless resource-wasting toy.
</opinion>

I disagree.  The zoom feature is very useful. Also the special-e desktop switcher that lets you move windows from one workspace to another is very useful for keeping things organised.  I use the special-tab switcher too because the graphics are bigger and its easier to see what happening.  The live preview windows are really useful and being able to put the widgets on a F9 button is useful too.

---

### Post by limac on 2007-11-11
Yeah beryl is really good. I used it. Or you can install Gutsy and install campixconfig-settings. And then you can customize it as you want it to be. 

BTW Gutsy is a whole lot better than Feisty. Many of the bugs that exist in Feisty are fixed in Gutsy. 

Good Luck! And have fun!

---

### Post by limac on 2007-11-11
make the "campixconfig" compizconfig. Srry for that.

---

### Post by dboot on 2007-12-10
I found [SimDock]("http://www.getdeb.net/app.php?name=SimDock"). It doesn't require compiz or 3D acceleration. It's not as fun as other docking stations that I've tried, but it's better than nothing!

---

