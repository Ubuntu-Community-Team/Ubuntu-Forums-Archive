---
title: "How can I install gnome-do 0.8 ?"
date: 2009-01-31
forum: General Help
---

### Post by emshains on 2009-01-31
I was pretty excited, when the beta with docky came out. I tried to compile it from source, but it didn't want to compile, so I thought it was the fact that it was beta. 

Now, that it has become stable, I hoped to see a hardy .deb, I already found an interpid deb, but there was no hardy deb for the 0.8 version of gnome-do. I picked the interpid deb, because many debs I've used seemed backwards/forwards compatible. But this complained about libglib2.0-cil, which can be found in /local/lib, I also downloaded a hardy deb for this lib, but with no results, it still complained about it. 

 So I decided to compile from source. It ./configured pretty good, but it didn't want to make gnome-do out of itself. Here's the output: 
```
Making all in .
make[1]: Entering directory `/home/emils/Desktop/gnome-do-0.8.0'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/emils/Desktop/gnome-do-0.8.0'
Making all in Do.Universe
make[1]: Entering directory `/home/emils/Desktop/gnome-do-0.8.0/Do.Universe'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/emils/Desktop/gnome-do-0.8.0/Do.Universe'
Making all in Do.Platform
make[1]: Entering directory `/home/emils/Desktop/gnome-do-0.8.0/Do.Platform'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/emils/Desktop/gnome-do-0.8.0/Do.Platform'
Making all in Do.Interface.Linux
make[1]: Entering directory `/home/emils/Desktop/gnome-do-0.8.0/Do.Interface.Linux'
Compiling Do.Interface.Linux.dll...
./src/Do.Interface/Do.Interface.AnimationBase/BezelColors.cs(107,73): error CS1501: No overload for method `ShadeColor' takes `1' arguments
./src/Do.Interface/Do.Interface.AnimationBase/BezelColors.cs(108,77): error CS1501: No overload for method `ShadeColor' takes `1' arguments
./src/Do.Interface/Do.Interface.AnimationBase/BezelColors.cs(109,77): error CS1501: No overload for method `ShadeColor' takes `1' arguments
./src/Do.Interface/Do.Interface.AnimationBase/BezelColors.cs(110,73): error CS1501: No overload for method `ShadeColor' takes `1' arguments
./src/Do.Interface/Do.Interface.AnimationBase/BezelColors.cs(111,73): error CS1501: No overload for method `ShadeColor' takes `1' arguments
Compilation failed: 5 error(s), 0 warnings
make[1]: *** [../build/Do.Interface.Linux.dll] Error 1
make[1]: Leaving directory `/home/emils/Desktop/gnome-do-0.8.0/Do.Interface.Linux'
make: *** [all-recursive] Error 1
```

Could anyone help me get this going ? I really want docky!

---

### Post by MarblePanther on 2009-01-31
[https://launchpad.net/~do-core/+archive/ppa](https://launchpad.net/~do-core/+archive/ppa)

---

### Post by emshains on 2009-01-31
That's where I found the interpid version. Please try to pay attention and check the link again, because there is no hardy release.

---

### Post by MarblePanther on 2009-01-31
Then if you want it that badly, upgrade to Intrepid.

---

### Post by emshains on 2009-01-31
This sucks. I am almost speechless. 

K I'll just make a enormous backup of everything, then upgrade, then install all the packages I had, then make a fresh install after the upgrade has failed, then try to find everything that wasn't ported to interpid, then I am going to copy my backup, and then use docky ?

---

### Post by MarblePanther on 2009-01-31
Calm down.  Either wait until a deb is released for hardy, upgrade to intrepid through your update-manager, or BREATHE and RELAX.  It is just a dock.  You'll live.

---

### Post by joey-elijah on 2009-02-01
Have you tried installing all of the dependencies individually then trying to make it?

---

### Post by raashell on 2009-02-01
I'm another Hardy user who got the same error.  I guess that it is dependency related to a mono library.  I found a Google groups discussion and that linked to this page:

[http://directhex.mfgames.com/hardy.html](http://directhex.mfgames.com/hardy.html)

When you link up Synaptic to this guys repository it allows you to install a later version of the library and finish building .8 from source.  I'm still messing around with it, but I had to go into the directory where I built it and execute it.  The result is that Do is version .8 with a docky that is slow as hell.

I'd upgrade to Intrepid, but it's like they said above, a major back up for me that would require me buying another hard drive and spending a day upgrading.

Hope this helps,  John

---

### Post by MarblePanther on 2009-02-01
> **MarblePanther said:**
> Calm down.  Either wait until a deb is released for hardy, upgrade to intrepid through your update-manager, or BREATHE and RELAX.  It is just a dock.  You'll live.

Sorry for my rudeness the other day.

I would recommend also trying AWN or Cairo-Dock. (both are in the repos)

[http://wiki.awn-project.org/index.php?title=Main_Page](http://wiki.awn-project.org/index.php?title=Main_Page)

[http://tombuntu.com/index.php/2008/05/01/how-to-install-cairo-dock/](http://tombuntu.com/index.php/2008/05/01/how-to-install-cairo-dock/)

---

### Post by hyperdude111 on 2009-02-01
Compile it from source, thats what i did. However the dock feature is not that impressive jus some usefull bug fixes.

---

### Post by emshains on 2009-02-02
I already had awn, but the reason why I wanted docky is because it doesn't require compiz. When I play games or do some work, I need most of the computers resources for the useful apps, not compiz/emerald. So I thought that a gnome/metacity alternative would be faster. 

Thanks anyway.

---

### Post by MarblePanther on 2009-02-02
Here is a dock that needs no compositing: 

[http://sourceforge.net/projects/simdock/](http://sourceforge.net/projects/simdock/)

Screenshot of it:  [http://sourceforge.net/projects/simdock/#item3rd-2](http://sourceforge.net/projects/simdock/#item3rd-2)

---

### Post by alperyilmaz on 2009-02-02
Unfortunately, there's no easy workaround for this problem. This is already a known bug. Read more [_here_]("https://bugs.launchpad.net/bugs/323835").

---

### Post by joey-elijah on 2009-02-03
I gotta be honest, the dock is pretty dire. I know it's early stages and I'm sure you're keen to try it out, but you're not really missing much. The animation isn't overly smooth; you can't specify icons for applications meaning you get some horrible 4x4 pixelated icons - Yuk! 

I love it as a concept though - in theory it's essentially far superior to OS X and Windows 7's "docks". I can't wait for it to become more stable/usable and add more features. 

I'm an AWN fanboi so what do i know anyway! ^_^

---

### Post by Lobais on 2009-02-05
As described here: [http://www.ubuntu-unleashed.com/2009/01/announcing-gnome-do-08-with-20-new.html](http://www.ubuntu-unleashed.com/2009/01/announcing-gnome-do-08-with-20-new.html) you can get gnome-do 0.8 for older ubuntus by adding a few repositories.

Also you should notice, that you can run all docks on the market using metacity using this tip: [http://lifehacker.com/5091740/get-3d-compositing-effects-in-linux-without-compiz](http://lifehacker.com/5091740/get-3d-compositing-effects-in-linux-without-compiz)

---

