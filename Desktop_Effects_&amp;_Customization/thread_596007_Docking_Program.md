---
title: "Docking Program"
date: 2007-10-29
forum: Desktop Effects &amp; Customization
---

### Post by kshane on 2007-10-29
Looking for a nice dock for my desktop.  I tried Kiba, but don't care for it.  Anyone have any other suggestions?

Thanks!

Kevin

---

### Post by sinsq on 2007-10-29
i use avant windows navigator and it is nice.

---

### Post by gjtoth on 2007-10-29
Try GDesklets.

---

### Post by kshane on 2007-10-29
> **gjtoth said:**
> Try GDesklets.

Does it come with a dock?

---

### Post by Inxsible on 2007-10-29
+1 for Awn

AWN or Avant Window Navigator is the most popular and most stable dock around.

---

### Post by santiagoward2000 on 2007-10-29
Personally, I love Kiba, but well...

---

### Post by notwen on 2007-10-29
+1 for AWN.  How-to on installing AWN [here]("http://ubuntuforums.org/showthread.php?t=385981").  You will need a composite manager(Compiz-Fusion) running in order to use AWN.  Good luck w/ whatever dock you choose. =]

---

### Post by kshane on 2007-10-29
> **notwen said:**
> +1 for AWN.  How-to on installing AWN [here]("http://ubuntuforums.org/showthread.php?t=385981").  You will need a composite manager(Compiz-Fusion) running in order to use AWN.  Good luck w/ whatever dock you choose. =]

Thanks...  I'll give it a shot!

Kevin

---

### Post by kshane on 2007-10-29
Whoa!  AWN is just a little too buggy for me.  Maybe I'll give Kiba another shot.

Are there any besides AWN and Kiba?

Thanks!

Kevin

---

### Post by craigyjack on 2007-10-29
I was going to +AWN. I use it all the time and it is pretty stable for me. i dont get many bugs at all and it works nice for me. But maybe its not as nice to you i guess. I love my AWN.

---

### Post by Inxsible on 2007-10-29
> **kshane said:**
> Whoa!  AWN is just a little too buggy for me.  Maybe I'll give Kiba another shot.

Are there any besides AWN and Kiba?

Thanks!

KevinWhat bugs did you find?
What installation method did you use ?

---

### Post by It_Was_Luck on 2007-10-29
I tired over 7 different ways to install AWN, 3 worked, except strangely they were all different. This install method was the one that worked the best.

Add these sources to your sources.list:

```
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
```

Run the rest in your terminal:


```
wget http://download.tuxfamily.org/syzygy42/reacocard.asc
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update
```

```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr 
```

---

### Post by kshane on 2007-10-29
> **craigyjack said:**
> I was going to +AWN. I use it all the time and it is pretty stable for me. i dont get many bugs at all and it works nice for me. But maybe its not as nice to you i guess. I love my AWN.

Well, I re-installed kiba and followed the instructions to a "T"...  It seems alright, so long as I don't try to edit a launcher.  If I edit a launcher, Kiba crashes and I have to restart X..  I'm still open to a new docker, if there are any others.  But, Kiba looks good now....

Kevin

---

### Post by notwen on 2007-11-01
What errors are you having w/ AWN?  Post them here or in the thread that I linked you to.  =]

---

### Post by jayaramk on 2007-11-01
usew either awn or simdock

---

### Post by boeing777 on 2007-11-01
Avant hasn't cause any problem with Compiz on my Ubuntu yet.

---

### Post by spec-chum on 2007-11-01
I'm quite happy with the dock with gdesklets.  I wasn't that keen on AWN and kiba wouldn't work for me.

---

### Post by meg23 on 2007-11-01
Cairo Dock is the master of all other docks!

---

### Post by kshane on 2007-11-01
> **Inxsible said:**
> What bugs did you find?
What installation method did you use ?

Sorry, I just looked around and couldn't find the how-to I used.  It was one that had you compile and install AWN.  When I said buggy, it was because it felt really unstable on my box.  I also had difficulties configuring it.

In any case, I went with Kiba-dock.  It has a few quirks, too, but I have it working well for me.  I attached a screenshot below...

Thanks for your input!  It IS appreciated...

Kevin

---

### Post by kshane on 2007-11-01
> **Inxsible said:**
> What bugs did you find?
What installation method did you use ?

Ah!  I found the guide I used.  Here's the link:

[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

Kevin

PS:  Don't take me wrong.  Didn't mean to trash AWN. I'm sure if I'd kept at it, I would have gotten it going good.

---

### Post by carlos1992 on 2007-11-01
i use Kiba Dock and i made a kind of apple mac os x leopard theme and kiba is just fine:)

---

### Post by kshane on 2007-11-03
> **carlos1992 said:**
> i use Kiba Dock and i made a kind of apple mac os x leopard theme and kiba is just fine:)

Yeah, I think I have settled on Kiba.  It's working well for me and looks terrific, too!  I put a screen shot together, below...  Pretty sweet, eh?

Kevin

---

### Post by rcamanda on 2007-11-06
> **kshane said:**
> Yeah, I think I have settled on Kiba.  It's working well for me and looks terrific, too!  I put a screen shot together, below...  Pretty sweet, eh?

Kevin

How did you get the blue glowing edges around your windows.  Do you have instructions for installing kiba-dock?

---

### Post by santiagoward2000 on 2007-11-06
> **rcamanda said:**
> How did you get the blue glowing edges around your windows.  Do you have instructions for installing kiba-dock?

mattgaunt wrote this how-to for Kiba, and it worked perfectly for me:
[http://ubuntuforums.org/showthread.php?t=554127]("http://ubuntuforums.org/showthread.php?t=554127")

---

### Post by rcamanda on 2007-11-07
> **santiagoward2000 said:**
> mattgaunt wrote this how-to for Kiba, and it worked perfectly for me:
[http://ubuntuforums.org/showthread.php?t=554127]("http://ubuntuforums.org/showthread.php?t=554127")

Thanks, but the pic you posted of your dock shows all the windows with glowing blue edges. Luminous.  How did you do that or what is the theme name?

---

### Post by kshane on 2007-11-07
> **rcamanda said:**
> Thanks, but the pic you posted of your dock shows all the windows with glowing blue edges. Luminous.  How did you do that or what is the theme name?

It's an Emerald Theme.  "Transcendentalism", I think it was called.

Kevin

---

### Post by santiagoward2000 on 2007-11-07
> **rcamanda said:**
> Thanks, but the pic you posted of your dock shows all the windows with glowing blue edges. Luminous.  How did you do that or what is the theme name?

Well, it's not my pic :lolflag:

---

### Post by rcamanda on 2007-11-07
> **kshane said:**
> Yeah, I think I have settled on Kiba.  It's working well for me and looks terrific, too!  I put a screen shot together, below...  Pretty sweet, eh?

Kevin


KShane where did you get the glowing blue windows edges or borders?

---

### Post by kshane on 2007-11-07
> **rcamanda said:**
> KShane where did you get the glowing blue windows edges or borders?

Transcendentalism in Emerald Themes.  Got it with the GPLed Themes, I believe.  I like it.  It's got several configuration options, too.

Kevin

---

### Post by carlos1992 on 2007-11-09
looks cool but still like a bit more my mac4lin kit (i would love a mac pro with fluxbox inside!!!)

---

