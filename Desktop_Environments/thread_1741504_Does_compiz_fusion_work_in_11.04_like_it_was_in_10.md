---
title: "Does compiz fusion work in 11.04 like it was in 10.10?"
date: 2011-04-28
forum: Desktop Environments
---

### Post by panderohit on 2011-04-28
Hi. I'm really excited about the launch of 11.04 today. However one of my main concerns is to know if 11.04 would be compatible with compiz-fusion the same way as it was in 10.10 (64-bit)?

To clarify this, I would like to say that I fell in love with ubuntu linux largely due to the desktop cube, wobbly windows and the burn effects. Would they still be there in 11.04 either in unity or gnome 3? Cuz if they are not I would be reluctant to upgrade to 11.04.

Thanks and regards.

---

### Post by nilarimogard on 2011-04-28
Yes, Unity works with Compiz and in fact Unity can't run without Compiz (unless you install Unity 2D). On the other hand, Compiz doesn't work with Gnome 3.

---

### Post by 3Miro on 2011-04-28
Unity doesn't work with the 3D cube (yet). If you want to use the 3D cube, you will need to use Ubuntu Classic mode (logout and select different session).

---

### Post by 3Miro on 2011-04-28
My bad:

[http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/)

Apparently you can enable to cube in 11.04 + Unity.

---

### Post by ted_rmt on 2011-05-04
Doesn't work for me. The tab to enable effects is missing in the Appearance.

After 11.04 upgrade, all of my CCSM settings were still selected including custom backgrounds and caps for my 3D sphere but neither the sphere (custom cube) nor any animations can be enabled, even in a Ubuntu classic session.

nVidia driver removed and downloaded again. It says in Additional Drivers, it is activated but it is "not being used." Above description says you need that driver enabled to use compiz effects. Driver worked fine in 10.10 and unity does what it is supposed to. 

I would wait on an upgrade if I were you. I wish I had.

---

### Post by ted_rmt on 2011-05-04
Went back into CCSM to give it another try. Have absolutely no idea why many things are working now because I restarted many times and tried all kinds of fixes to enable the effects before I made my decisions in the previous post.

So I have found the following:

If you want to have a cool cone or sphere or 3d cube flipping desktops in Unity, forget it. You need to have Large Desktop enabled for Unity and that requires Desktop Wall, which cannot play nice with Desktop Cube.

However, animations work and can be assigned normally to open, close maximise and minimise windows and you can paint fire on the screen.

There is no enable visual effects tab in the appearance menu anymore, but it looks like effects are now on by default. You now have the option of logging on to your session without effects when you choose your session on the login screen. That could be very handy if you are sharing a computer with someone who hates your special effects. :P

Most CCSM changes will screw up the top bar and nothing will make it redraw except a system restart as fasr as I know.

Also, when you use CCSM, be patient. Seems as if enabling changes is automatic now and takes time. I likely went too fast and disabled things before I saw them take effect.

---

### Post by Krytarik on 2011-05-04
> **ted_rmt said:**
> 
If you want to have a cool cone or sphere or 3d cube flipping desktops in Unity, forget it. You need to have Large Desktop enabled for Unity and that requires Desktop Wall, which cannot play nice with Desktop Cube.
That's not true, many users are running the Cube just fine. Just try following the instructions under the title "Update: An alternative gui way" in the guide *3miro* linked to.
> **ted_rmt said:**
> 
There is no enable visual effects tab in the appearance menu anymore, but it looks like effects are now on by default. You now have the option of logging on to your session without effects when you choose your session on the login screen.
Exactly, whether Compiz will be used or not is specified by the session settings now.
> **ted_rmt said:**
> 
Most CCSM changes will screw up the top bar and nothing will make it redraw except a system restart as fasr as I know.Just a relogin would be sufficient in those cases.

---

### Post by ted_rmt on 2011-05-06
Ok looked over the link to get unity and the cube together. Three problems.

1. I now hate Unity. Makes me sick to even look at it. Other programs showing instability I never had before. This will interfere with my objectivity.

2. I don't have a working cube anymore, so exporting my settings is not an option. Neither is the GUI fix.

3. Download option is an html page with machine language, not a simple archive file, so I save that as what? Then open the archive and do the import?

Problem is, I am out of time and patience. I would have loved to have spent this time learning how to do simple things like downloading someone's machine language to make my own tar files or just simply compiling a program in linux. I simply don't have any more time to learn after wasting so many hours trying to get compiz to work. 

And as for having to relog so I can just use my desktop. No. Simply, no. Won't do it. Unity is broken and going in the dust bin. Telling the user that they have to research the basics of the operating system every time there is an update is simply unacceptable. Kind of thing I would expect from Microsoft.

---

### Post by ted_rmt on 2011-05-06
Reposting this link:

[http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/)

Got the sphere to work in 11.04 in a Unity session using the GUI option, (disabling automatic plugin sorting)

Have to re-enable several plug-ins and reconfigure to get it to look the way it used to. Still not there, but now that it works I can do the fine tuning.

So to the original topic. Does it work, like the way it does in gnome? No. It does not. Gnome just worked. Thanks to the community for this[COLOR=Blue] workaround[/COLOR].

---

### Post by panderohit on 2011-07-26
Hi. This is the OP. I got the desktop cube to work using this [link]("http://www.youtube.com/watch?v=O-iYoy1BGak"). However, since I loved 11.04, but was not too fond of unity, I have now moved over to linux mint 11 and all is well once again.

---

