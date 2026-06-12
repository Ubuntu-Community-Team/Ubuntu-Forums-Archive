---
title: "Make KDE slimmer?"
date: 2009-12-07
forum: Desktop Environments
---

### Post by Roasted on 2009-12-07
I find KDE to be pretty snappy, even on machines dating back to the Pentium 4 era with only 512mb of RAM. However, what if I want to really minimize KDE's usage as much as possible to make it more friendly with laptops that should probably be in a museum. What steps with the graphic effects can I do to make it snappier for olllld video cards?

---

### Post by akashiraffee on 2009-12-07
> **Roasted said:**
> What steps with the graphic effects can I do to make it snappier for olllld video cards?

If your question is, how can I make a really old piece of junk look just like my Quad 8 super-GeForce box, the answer is you can't.

You can run a graphical desktop on linux on a 386 with <128 mb of ram, but KDE and probably ubuntu are not the best choices for that.

It's important to understand that the linux DE's just barely existed 10 years ago.  They rapidly gained popularity because they are easy to use, but **they do use a lot of resources**.

---

### Post by Roasted on 2009-12-07
Well yeah, it's not really so much from a RAM standpoint, since KDE and Gnome both use almost the same amount of memory.

It's just certain computers I've played with KDE on didn't really handle the 3d stuff so well.

As we all know, Gnome is relatively boring till you fire up Compiz. Easy solution - don't install Compiz.

But KDE comes "out of box" with more eye candy, transparent windows, etc. Is there a way to kinda disable all that stuff to knock back the need for a decent graphics card then?

---

### Post by akashiraffee on 2009-12-07
> **Roasted said:**
> 
As we all know, Gnome is relatively boring till you fire up Compiz. Easy solution - don't install Compiz.

But KDE comes "out of box" with more eye candy, transparent windows, etc. Is there a way to kinda disable all that stuff to knock back the need for a decent graphics card then?

Gnome should by no means be considered lite either.   NONE of the DE's should be considered lite. 

It is not the RAM or the video card dude, altho those are both factors.  It is the processor.  This is especially true if you mean an old PCI video card that has, comparatively, a wee sliver of a GPU.  Processors have gotten faster, but GPU's have gotten WAY faster.  Without the GPU, all the workload is now on the processor. And old GPU's do not have any 3D hardware acceleration at all.  None.  So that must all be done by the processor.

To give you an illustration of what that means, I just started work on an openGL project.  I don't play games, so I didn't have a video card.  Even without lighting and texturing, eventually I got down to **20fps**.  So I went out a week ago and bought a bottom o' the line ATI 4350 card for $50.  Once I got it working, the ungoverned frame rate for the program went up to OVER **300fps**.  For real.   And I'm using a 2x2.2Ghz processor.

So now you want to do the 3D desktop on a first generation pentium with a S3 card?  Forget it.

Really, that means forget KDE and Gnome too.  You are basically saying, "My fav game is Far Cry 2.  I wanna play it on this old portable I found in someone's basement".  No, you don't.  There may be games you can play on it, but Far Cry 2 is not one of them.

I would guess (altho I don't know for sure) that there is probably NOT a way to significantly lighten KDE up.  Why?  Because it's not intended for that.  There are probably a dozen lightweight, fully functional window managers around that do not require a "Desktop Environment" to work.  They provide everything you  need -- windows, menus, taskbars, etc, but no applications.  You gotta find your own.

Keep in mind, you do not want the GUI to "barely make it".  You want it to run with a minimum of overhead to leave room for applications, because on a machine 100 times slower than your desktop, every application uses significant resources.  So you need to leave some.  If you are not interested in doing some homework and learning some new software for this, just leave the thing in the basement.

---

### Post by Roasted on 2009-12-07
> **akashiraffee said:**
> Gnome should by no means be considered lite either.   NONE of the DE's should be considered lite. 

It is not the RAM or the video card dude, altho those are both factors.  It is the processor.  This is especially true if you mean an old PCI video card that has, comparatively, a wee sliver of a GPU.  Processors have gotten faster, but GPU's have gotten WAY faster.  Without the GPU, all the workload is now on the processor. And old GPU's do not have any 3D hardware acceleration at all.  None.  So that must all be done by the processor.

To give you an illustration of what that means, I just started work on an openGL project.  I don't play games, so I didn't have a video card.  Even without lighting and texturing, eventually I got down to **20fps**.  So I went out a week ago and bought a bottom o' the line ATI 4350 card for $50.  Once I got it working, the ungoverned frame rate for the program went up to OVER **300fps**.  For real.   And I'm using a 2x2.2Ghz processor.

So now you want to do the 3D desktop on a first generation pentium with a S3 card?  Forget it.

Really, that means forget KDE and Gnome too.  You are basically saying, "My fav game is Far Cry 2.  I wanna play it on this old portable I found in someone's basement".  No, you don't.  There may be games you can play on it, but Far Cry 2 is not one of them.

I would guess (altho I don't know for sure) that there is probably NOT a way to significantly lighten KDE up.  Why?  Because it's not intended for that.  There are probably a dozen lightweight, fully functional window managers around that do not require a "Desktop Environment" to work.  They provide everything you  need -- windows, menus, taskbars, etc, but no applications.  You gotta find your own.

Keep in mind, you do not want the GUI to "barely make it".  You want it to run with a minimum of overhead to leave room for applications, because on a machine 100 times slower than your desktop, every application uses significant resources.  So you need to leave some.  If you are not interested in doing some homework and learning some new software for this, just leave the thing in the basement.

Hm, well, if it seems to be all processor intensive, here's a curve ball:

Gnome flies on my laptop.
KDE 4.3.2 is noticably slower on my laptop, but still [somewhat] acceptable.

Laptop specs?

Processor = 2.66ghz Intel Core 2 Duo
Memory = 4GB DDR2 667 RAM
Graphics = Integrated Intel

Clearly I have a pretty powerful processor to push KDE, while my graphics card is the only lacking feature in the mix.

This indicates that the graphics card can indeed play a key role in KDE running slower, despite whatever core processor power you have.

So my question stands - Is there a way I can slim KDE's effects down so it can run slightly better on my laptop?

---

### Post by akashiraffee on 2009-12-07
> **Roasted said:**
> 
This indicates that the graphics card can indeed play a key role in KDE running slower, despite whatever core processor power you have.


No it means if you do not have a 3D capable card, your processor has to do all the work.  That is why it is called "hardware acceleration" -- it's not that the video card is "slower", it's that the video card does not do ANY of the work a 3D card does.  The processor does it instead.  So with a crappy video card, *it is the processor which is important.*  But a modern processor will never ever make up for the lack.  

2D is a slightly different story, which desktop transparency etc are not 3D effects.  All video cards have some 2D acceleration.  One factor here will be the kernel module driver.  I would actually say my inboard via chrome chip handled 2D better than the new 3D ATI card, maybe...

Anyway, your laptop is not an old machine.  If you are comparing it to your desktop, which has a **3D accelerated card** in it, I just gave you an example of the difference that can make.  But that difference ONLY applies SPECIFICALLY to 3D affects that involve one of two things 1) OpenGL 2) MS DirectX.  

Without a 3D card, openGL/directX applications must now be run 100% by the processor.

So, your number one goal should be: eliminate the use of ANY 3D effects.

Beyond that, there are tons of possible factors, if you are just comparing "Bob's laptop" to "Dave's desktop" -- these are singular realities and it may simply be that KDE runs slower on your laptop, end of story.  Try a different DE or WM, or even a different linux distro.

---

### Post by Roasted on 2009-12-07
Two questions then:

Why do my processor cores in system monitor rarely even go above 20%, yet I still have laggy windows loading at times? 

Secondly - where do I disable ALL 3d effects?

---

### Post by akashiraffee on 2009-12-07
> **Roasted said:**
> Two questions then:

Why do my processor cores in system monitor rarely even go above 20%, yet I still have laggy windows loading at times? 

Secondly - where do I disable ALL 3d effects?

I'm not actually a KDE user so I can't help you with that.

Looks to me like Compiz -- which is the openGL 3D stuff -- is also intended for KDE, so if you are not running compiz, then you are probably not running any real 3D.

With regard to the 2D acceleration, I guess the graphics chip is a big factor, because IT IS capable, so the processor will delegate that work to the graphics chip.  But there are a lot of factors at work here.  If you are not satisfied with how KDE performs on your laptop and you've done as much as you can to simplify, try a different DE or window manager.  If you don't want to do that, live with it.  Like I said, they are not gearing the product toward moderation -- there are already other products that do that.  They are aiming to be the no-holds barred heavyweight champion.

On the other hand, maybe some KDE wiz will come along and make your day!  Good luck.

---

### Post by Roasted on 2009-12-07
I wonder if I screwed something up last time. Or maybe had too much going on with all the widgets I had on the desktop. I installed Xubuntu on my laptop to check it out. Very nice, very simple, but too simple. It'd be the prime choice if I needed a desktop OS with a GUI to run as a server, but it's not my cup of tea to work on all day.

Put Kubuntu back in - DAMN it's fast. Oh well! Looks better now.

---

### Post by Zorael on 2009-12-08
Disabling effects; System Settings -> Desktop -> Desktop Effects -> uncheck Enable Desktop Effects?

---

### Post by Roasted on 2009-12-08
> **Zorael said:**
> Disabling effects; System Settings -> Desktop -> Desktop Effects -> uncheck Enable Desktop Effects?

Yeah, I see that now. Still getting used to KDE. :P 

I wonder if I had a heavy theme set up before or something. It used to feel kind of blahhh when navigating around. Now it's wicked fast after I redid it. Very impressed. :popcorn:

---

### Post by Roasted on 2009-12-09
> **rocks.fus said:**
> Processor = 2.66ghz Intel Core 2 Duo
Memory = 4GB DDR2 667 RAM
Graphics = Integrated Intel

^^^^^ 
I am already I have the upove specification

Pardon? :confused:

---

