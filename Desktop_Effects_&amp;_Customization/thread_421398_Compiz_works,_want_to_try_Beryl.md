---
title: "Compiz works, want to try Beryl"
date: 2007-04-24
forum: Desktop Effects &amp; Customization
---

### Post by tehbeermang on 2007-04-24
I am rather proud of myself. WIth a little guidance in the newbie section of this forum, I was able to get ubuntu to dual boot on my ancient laptop (Dell Latitude C610, has an ATI mobile chipset) and get all of the cool Compiz effects to run with minimal "stuttering" and no "white screen of death". 

I want to try Beryl for additional 3d coolness (and to further torture my aging hardware). I installed all of the Beryl packages with synaptic, but I have no idea where to start in making it my default window manager. 

I'm a Win32 addict on the Linux Methadone program, show me a "point and click" method of changing window managers, if at all possible. ;)

---

### Post by Ender Black on 2007-04-24
First of all congrats!

All you need to do is start the Beryl Manager (either type in beryl-manager in terminal or you can find it in the applications pull-down menu)

Then from the Beryl Icon you can right click and choose window manager and window decorators.

To make it the default, go to System -> Preferences -> Sessions and add beryl-manager to the start-up apps.

And now you have beryl all the time.

---

### Post by tehbeermang on 2007-04-24
Holy cow, that is easy!

---

### Post by dorogavtsev on 2007-04-24
Ender Black, thanks, mate! :-)

---

### Post by Rayyeter on 2007-04-24
I am so jealous...

I can't get eith beryl or compiz to work on my t60 with an ati x1400 mobility in it. I think I've tried everything. :confused: :(

---

### Post by blamecanada on 2007-04-24
I was having problems w/ my 1800xt, but I just threw an old x300 in there that should work, though I haven't installed yet.

---

### Post by Cervantez on 2007-04-24
I'd stick with compiz... (well, I'm just using metacity now). My computer has a 7600gt and is powerfull enough for  Beryl and Compiz (I have both installed) but Beryl DEFINATELY **has way too many bugs** at this point to use sensibly. Compiz also stopped working correctly when I installed Beryl. Beryl crashes constantly and doesn't load propperly the first login after you boot up. It also dissables your gnome splash screen and causes tabs at the bottom panel to become dead very often. It's also a lot slower than compiz. Beryl will be much better when it is finished, but I don't recommend using is while it's in alpha.

---

### Post by pertti on 2007-04-25
> **Rayyeter said:**
> I am so jealous...

I can't get eith beryl or compiz to work on my t60 with an ati x1400 mobility in it. I think I've tried everything. :confused: :(

Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=399913"). It's a guide for a Dell 6400 with an ATI X1400, but one person on that thread says that it has worked perfectly on a T60.

---

### Post by tehbeermang on 2007-04-25
> **Cervantez said:**
> Beryl DEFINATELY **has way too many bugs** at this point to use sensibly. {snip}  Beryl will be much better when it is finished, but I don't recommend using is while it's in alpha.

I had it running last night. I had one crash.

It simply reverted back to Metacity. 

Much more elegant behavior than what was expected. But then I haven't pushed it really hard yet.

---

### Post by jivemuffin on 2007-05-10
> **tehbeermang said:**
> I am rather proud of myself. WIth a little guidance in the newbie section of this forum, I was able to get ubuntu to dual boot on my ancient laptop (Dell Latitude C610, has an ATI mobile chipset) and get all of the cool Compiz effects to run with minimal "stuttering" and no "white screen of death". 

I want to try Beryl for additional 3d coolness (and to further torture my aging hardware). I installed all of the Beryl packages with synaptic, but I have no idea where to start in making it my default window manager. 

I'm a Win32 addict on the Linux Methadone program, show me a "point and click" method of changing window managers, if at all possible. ;)

Oh gosh, any chance of you posting your xorg.conf? I just could not get acceleration to work at all! It makes me sad.

---

### Post by misfitpierce on 2007-05-10
I got it running on ATI Xpress 200M :)
Rather tricky task only took 2 hours or so.... But I run beryl consistantly and have hit no bugs I can see... Runs smooth in fact and am very happy... I just cant play games through cedega with beryl or XGL running and its too hard on ATI 200M but other than that 1 word... Great

---

### Post by RavanH on 2007-05-11
> **misfitpierce said:**
> I got it running on ATI Xpress 200M :)
Rather tricky task only took 2 hours or so.... But I run beryl consistantly and have hit no bugs I can see... Runs smooth in fact and am very happy... I just cant play games through cedega with beryl or XGL running and its too hard on ATI 200M but other than that 1 word... Great

Hi misfitpierce, could you please (and I do mean: please) share how you made this work for you and your Xpress 200M? Got the same onboard videocard and cannot get ANY of the fancy stuff :( no matter what I tried! Not even a hint of shade - at least not stable... and no transparancy let alone that cube everybody is ranting about :cry: 

This ATI driver thing is not driving my videocard but it's driving *me* mad for sure. After my last attempt (installed 8.36.5) I got stuck with broken Suspend and Hibernation. And 3D rendering (glxgears) seems slower than it was before: ~900FPS instead of ~1200FPS  ](*,)

---- This is where I stop complaining and ask you agian: can you  [-o< share your path to enlightenment (or victory, if you will) with the rest of us? I am surely not the only one who's VERY keen to know how it can be done...

Thanks! :)

EDIT:
Oh, and maybe any of you Radeon Xpress 200M owners (who haven't done so already) would be so kind as to sign this petition for getting ATI/AMD to push on with AIGLX support: [http://www.petitiononline.com/x200MLin/petition.html](http://www.petitiononline.com/x200MLin/petition.html) ?

---

### Post by sowelie on 2007-05-11
> **Rayyeter said:**
> I am so jealous...

I can't get eith beryl or compiz to work on my t60 with an ati x1400 mobility in it. I think I've tried everything. :confused: :(

What kind of issues are you having?

---

### Post by strumluff on 2007-05-12
I also got it working on my ATI Xpress 1100, basically the 200M. To install you must have the closed source, ATI proprietary drivers installed, you must have an XGL session created and you can only use a specific version of Beryl for the time being (i'm not sure if the status of this has changed).

Want a guide? Here's a good one: [Linky]("http://ubuntuforums.org/showpost.php?p=2564461&postcount=13")

---

