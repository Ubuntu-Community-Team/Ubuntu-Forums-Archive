---
title: "Beryl not really ultra smooth for anyone?"
date: 2007-02-18
forum: Desktop Environments
---

### Post by CaptSaltyJack on 2007-02-18
I'm under the impression Beryl isn't 100% silky smooth for anyone.  Unless you've got a high end system.  I've got a GeForce 6200 LE card in my machine.  Now, that should be enough, right?  I mean, we're just talking about 3D'izing some windows, and rendering a cube.  Hell, a GeForce4 could handle this I would think.  So on my system, wobbly windows are ultra smooth.  The cube isn't bad.. it's a little bit laggy but nothing serious.  But once there are a lot of windows up, wobbly windows slows a bit.  And resizing windows, forget it!  I had to switch to "Stretch" mode for that, it was unbearable.

Also, Beryl doesn't play nice with other 3D apps.  if I load up a 3D game, or an OpenGL screensaver, it's sloooowww..even though Beryl is just sitting there.

So what's up with this?  I'm thinking it's just bad programming at work here.  No way should rendering cubes and flat 3D shapes be so intensive like that.  Does anyone know if Compiz runs better?  And plays nice with other 3D apps?

---

### Post by phoqueyoo on 2007-02-18
I tried both Compiz and Beryl yesterday and Compiz has much smoother cube rotating and the scrolling bug isn't as bad. Unless you NEED explosive and shinny effects than compiz is much better.

Are you sure you configured your card correctly?

---

### Post by CaptSaltyJack on 2007-02-18
Yeah I configured my card correctly.... I think.  I was using this guide:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

But I may have done the whole linux image part wrong.  I have linux-image-2.6.17-10-generic and 2.6.17-11-generic installed already.  But my CPU is an Athlon64.. linux-image-amd64-k8 is not installed.  Should it be?

Other than that, yes the nvidia-glx stuff is installed correctly and works, 3D games/apps work fine.

Hey as long as Compiz can do the cube, and the Mac Expose type feature.. I'm good.  Maybe I'll give Compiz a try.
(err.. I'd try Compiz if there was actually a 64-bit package out there for it..grr)

---

### Post by MetalMusicAddict on 2007-02-18
That card is fine. Im running Beryl on much less of a card as we speak.

 The guides on [Beryl's WIKI]("http://wiki.beryl-project.org/wiki/Main_Page") are better to go by.

---

### Post by CaptSaltyJack on 2007-02-18
> **MetalMusicAddict said:**
> That card is fine. Im running Beryl on much less of a card as we speak.

 The guides on [Beryl's WIKI]("http://wiki.beryl-project.org/wiki/Main_Page") are better to go by.

Maybe the Ubuntu wiki should just point there then.  Having multiple conflicting documents like that is very confusing.

---

### Post by benndamann33 on 2007-02-18
seriously though, beryl isn't that smooth, it's kind of excessive without a particularly large amount of functionality

---

### Post by CaptSaltyJack on 2007-02-18
I will try compiz first, as I'm going to reformat and install a 32-bit version of Kubuntu.  There are some other apps (NoMachine) that won't work on 64-bit properly.. tired of this 64-bit stuff and packages not being built for it.

---

### Post by thx_1138 on 2007-02-18
I have now played around with both Beryl and Compiz on my laptop which has an ati 200m video card. I found Beryl to run just a shade slow on my machine and when it got updated it broke it. I finally gave Compiz a try and have been playing with it for a few hours. I must say although it is not as glossy (so to speak) or there doesn't seem to be as many features out of the initial install, but the performance does seem smoother on my machine. I hope to keep testing it for a few weeks and see how it fares when updated.

---

### Post by RAOF on 2007-02-18
You might want to try installing the compiz-extra package - that's got extra plugins, like the *animation* plugin from Beryl.  You can make windows burn in Compiz, too.

Also, where did you get Compiz from?  There's a (fairly old) version in Edgy Universe, and a current version in Feisty Universe.  The guide on [www.go-compiz.org](www.go-compiz.org) is the best and most current.

---

