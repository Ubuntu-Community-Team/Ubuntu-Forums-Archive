---
title: "Compiz flickering on fullscreen games....."
date: 2008-12-12
forum: Gaming &amp; Leisure
---

### Post by RaiCoss on 2008-12-12
I think i've found a kinda cure for this(it works for me anyway), just enable Opacity,Brightness and Saturation in compiz settings, under Window Specific Settings, click New and name the new item (labeled as windows) "dock" and set the bar (Windows values) to desired transparency (0-100, concureent to the amount of transparency that you want to apply), and voila no more flickering (y)

---

### Post by hikaricore on 2008-12-12
Compiz is not really meant to run along side games.

I personally suggest disabling desktop effects while playing games that cause issues such as this.

---

### Post by forrestcupp on 2008-12-12
> **RaiCoss said:**
> I think i've found a kinda cure for this(it works for me anyway), just enable opacity in compiz settings, under window specific settings, click add and name the new item "dock" and set the bar to desired transparency, and voila no more flickering (y)

Hey, if that really works, then good job!

Another workaround is to buy an nvidia card.  But not everyone can just go do that, can they?

---

### Post by RaiCoss on 2008-12-12
well no, i have a nvidia card lol, so that not really true =P, as for the disabling compiz comment, i always do, i just forgot when going to play etqw, and expected i'd have to ctrl+alt+backspace out to gdm, but to my surprise it didnt, and in fact everything ive tried now works fullscreen, and its definitley this that does it as when i disable opacity in compiz options, it flickers again, so it fixes it for me, whether or not it will work for other people i dont know, i just thought i'd post it incase it helps =]

---

### Post by Vadi on 2008-12-12
I don't get flickering on my nvidia card

---

### Post by RaiCoss on 2008-12-12
What kind of card do you have?? I've had the same problem on every nVidia card I've ever tried (GeForce 4MX/FX 5700/6200/7300GT (all AGP). and an 8600GT PCI-E my current card).

---

### Post by Vadi on 2008-12-12
8600m gt

I also use nvidia's drivers from system&#8594;administration&#8594;hardware drivers and on ubuntu 8.10

---

### Post by RaiCoss on 2008-12-12
8600m as in 8600 mobile or just a typo, and do you have compiz enabled when you run the games fullscreen?

---

### Post by Vadi on 2008-12-12
mobile, and yeah always got compiz on

I tried running some 3d phoronix tests with it on or off and concluded it wasn't worth the inconvenience before

---

### Post by forrestcupp on 2008-12-12
> **RaiCoss said:**
> 8600m as in 8600 mobile or just a typo, and do you have compiz enabled when you run the games fullscreen?

Yeah, are you using nvidia's proprietary binary drivers?  I've never had flickering with nvidia using those drivers.  If you're using the restricted drivers, you shouldn't have flickering because they include their own hacked glx so that you don't have problems like that.  I've always been able to do full screen *and* windowed 3D stuff with Compiz on without trouble.

Usually it's the ATI people that complain about flickering.

You're not using Xgl by chance, are you?  If you are, that's your problem.

---

### Post by RaiCoss on 2008-12-13
No I'm using the repository restricted driver (177.80) and still got the flickering till i came accross this, and don't even mention At-crappy-i, i hate them after the experience I've had with their drivers!

---

### Post by BigSilly on 2008-12-13
I have this problem too on my fairly numpty Nvidia 6200, and it's nothing new. Happens when playing DVD's too. Disabling Compiz before gaming is all well and good but it's not really a great solution. All it leads to is disabling Compiz altogether and not bothering, which I reckon is probably the best solution for now for most users I suppose.

Myself, I tend to try it every six months after a fresh install. What usually happens is I try it, it borks on me, and I forget it for the next six months.  Still, it's not even reached it's first release yet, so I expect when version 1.0 comes out it'll be pretty solid. 

I tend to think of it as one to watch for the future.

---

### Post by RaiCoss on 2008-12-13
Hmmmmm. I don't get any problems with fullscreen videos/dvds, what are your system specs? And if you want a slightly more convenient way of switching between compiz and metacity try compiz switch.....

[http://blogage.de/files/3611/download?compiz-switch_0.4.3%7Eubuntu-1_all.deb](http://blogage.de/files/3611/download?compiz-switch_0.4.3%7Eubuntu-1_all.deb)

Just add it to your task bar and then its just a single click to switch between them.

---

### Post by plasmarox on 2008-12-13
The best way to resolve this is to do:
```
metacity --replace
```

when you play the game, then do:
```
compiz --replace
``` when you've finished. Works everytime for me.

---

### Post by RaiCoss on 2008-12-13
Tbh compiz is a little pointless i guess, at least until they iron out all the glitches, metacity is rock solid, and thats really what you want isn't it =/

---

### Post by Vadi on 2008-12-13
Nope, I can't live without Compiz now. It offers a lot of extra functionality of a plain 2d window manager.

---

### Post by RaiCoss on 2008-12-13
Haha, fair enough, I only use compiz for vSync really, why oh why cant metacity vSync properly x(((

---

### Post by maddog46113 on 2008-12-13
> **RaiCoss said:**
> I think i've found a kinda cure for this(it works for me anyway), just enable Opacity,Brightness and Saturation in compiz settings, under Window Specific Settings, click New and name the new item (labeled as windows) "dock" and set the bar (Windows values) to desired transparency (0-100, concureent to the amount of transparency that you want to apply), and voila no more flickering (y)

where exactly is Window Specific Settings. I use CompizConfig Settings Manager.

---

### Post by RaiCoss on 2008-12-13
> **maddog46113 said:**
> where exactly is Window Specific Settings. I use CompizConfig Settings Manager.



Thats what i use too, in the Accesibilty section, its under Opacity, Brightness and Saturation (click it once) and its at the bottom, then follow the instructions in the original post ;]

---

### Post by maddog46113 on 2008-12-13
Sweet works fantasticly. Thankls for the solution xD

---

### Post by RaiCoss on 2008-12-16
> **maddog46113 said:**
> Sweet works fantasticly. Thankls for the solution xD

 no problem (y)

---

