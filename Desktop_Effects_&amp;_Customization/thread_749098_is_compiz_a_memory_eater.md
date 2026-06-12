---
title: "is compiz a memory eater ?"
date: 2008-04-08
forum: Desktop Effects &amp; Customization
---

### Post by brijith on 2008-04-08
Hai friends

          I read some where in this forum about issues with compiz fusion. When I first saw its effects I was stunned. But after few days I realise the disappointing fact about compiz. there are some serious bugs in it.
When I experienced those bugs I really disappointed. Why no one is trying to fix those bugs? Or it already fixed if it is fixed how can I get those fixes.

          Can any one throw some light to this  issue




**[COLOR="Red"]Thanks[/COLOR]**

---

### Post by russo.mic on 2008-04-08
Well, you've placed us all in a very dark room.

What kind of video hardware are you running?  What specific bugs are you experiencing?  

What steps did you take to install the driver for 3d accel for your hardware?

Are you using AIGLX or XGL?  

To answer your direct question, yes of course compiz uses some memory, but I run it with ease and have few bugs.

Russo

---

### Post by brijith on 2008-04-08
Well,
Let me give my system configuration  details 

I am using Intel 915GAV mother board with intel pentium4 3GHz processor,1256MB of RAM
and don't have any graphic card installed. I mean I am happy with on board graphics

		I didn't installed any graphics driver. I installed Ubuntu from CD and Installed Some necessary packages along with compiz. I used to do this off line. I mean I download packages needed when I am in office then install them in my off line PC at home. I installed some video and audio editing software and some programming tool and editors.
		
		actually my problem is when I work with compiz for some time I found that compiz is using more memory. And it keep increasing as time goes. 

When I enable some effects like desktop Cube system becomes slow.
When I take netbeans it loads but can't see anything  in main window. I mean it is blank 

These are some of my issues. 
Do you have any suggestions, What I have to do to compiz run normally

**[COLOR="Red"]Thanks[/COLOR]**

---

### Post by nickdbliss on 2008-04-08
Compiz requires good graphics card to work smoothly, thats what i believe. I had problem using it on my desktop pc since my graphic card was with my friend after ihad it , it was working fine.

---

### Post by russo.mic on 2008-04-09
Compiz does require a fairly decent graphics card to run...And certainly your running some kind of graphics driver, as compiz requires you have 3d acceleration.

What kind of graphics are onboard?  

Run lspci from a terminal and post the output.

---

### Post by brijith on 2008-04-10
> **russo.mic said:**
> 
What kind of graphics are onboard?  

Run lspci from a terminal and post the output.


Sorry I can't run right now. That PC is at my home. And I used to go home at weekends. Any way here is a link [[COLOR="DarkOrange"]To my mother board specification[/COLOR]]("http://www.ciao.co.uk/Intel_Desktop_Board_D915GAV__5738516#productdetail") I hope you can find something helpful in it.

**[COLOR="Red"]Thanks[/COLOR]**

---

### Post by Saint Angeles on 2008-04-10
i got a 256 MB video card and 2 GB RAM...

with compiz running, a couple apps (including a video) and glxgears running... i get more than 2700 fps and only eat up about 18% of my RAM

windows' aero is a memory eater

---

### Post by ma65p on 2008-04-11
> **brijith said:**
> Well,
Let me give my system configuration  details 

I am using Intel 915GAV mother board with intel pentium4 3GHz processor,1256MB of RAM
and don't have any graphic card installed. I mean I am happy with on board graphics

		I didn't installed any graphics driver. I installed Ubuntu from CD and Installed Some necessary packages along with compiz. I used to do this off line. I mean I download packages needed when I am in office then install them in my off line PC at home. I installed some video and audio editing software and some programming tool and editors.
		
		actually my problem is when I work with compiz for some time I found that compiz is using more memory. And it keep increasing as time goes. 

When I enable some effects like desktop Cube system becomes slow.
When I take netbeans it loads but can't see anything  in main window. I mean it is blank 

These are some of my issues. 
Do you have any suggestions, What I have to do to compiz run normally

**[COLOR="Red"]Thanks[/COLOR]**

It might be a good idea to get your graphic card's driver. I'm not sure about your system, but on my computer, without the driver, there is only 32MB internal memory for video card, it looks like crap. But when I got my driver install, it's 128MB, which turns out to be decent enough for compiz

Compiz is not a ram eater. Without quite impressive performance, compiz used only about 100MB RAM, windows always used 300MB for...uh...nothing.

However, I notice that if I open a bunch of windows and play with them for about 30 minutes, RAM start to accumulate  up to 800MB and will not fall back down even after I close all windows. Usually, I just reset the setting on my appearance, say, back to none, then back to compiz and everything is fine again.

---

### Post by spupy on 2008-04-11
Yesterday I tried standalone Compiz on my Gentoo installment. Got the new fglrx drivers for my ATi X200M. Compiz is running fine with AIGLX. 

The problem is that while my Fluxbox desktop uses 50MB RAM after starting X, while X with enabled AIGLX and Compiz running takes up to 200MB. And I have only 512MB. But this is inevitable, considering the stunning effects.

---

