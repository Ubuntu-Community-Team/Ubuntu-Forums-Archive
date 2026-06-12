---
title: "Speed up X?"
date: 2006-07-13
forum: Desktop Environments
---

### Post by arrowhead on 2006-07-13
Is there a way to speed up the X server in Linux? 
Whenever I use Linux (not just Ubuntu) I get very sore eyes and begin having headaches after about half an hour of use. My Horizontal and Vertical refresh rates for my monitor are detected correctly, and I have tried different graphics cards. The only thing I have noticed is that if I use pure Debian (which uses Xfree86 rather than Xorg) the problem isn't as bad and I can use it for longer. I know none of my equipment is faulty because I can use Windows XP all day without a problem. 
I would love to use Ubuntu but unless I can find a fix for this I'm stuck with XP and IE constantly crashing :o( 
Any ideas welcome.

---

### Post by philippe_carlo on 2006-07-13
What kind of graphics card do you have?

---

### Post by arrowhead on 2006-07-13
It's an Intel 82915G/GV/910GL card built into the motherboard on this my main PC. I also have an older PC that I have tried an Nvidia FX5200, an old Nvidia Geforce 2, and an even older ATI Rage 128. The monitor is a Viewsonic VG712 LCD but, all of my graphics cards only have VGA connectors and I'm not in a position at the moment to buy one with a DVI connector.

---

### Post by philippe_carlo on 2006-07-13
It is very weird that you would get a head ache from an LCD monitor, since -unlike older CRT's- they are not supposed to flicker, right?

---

### Post by arrowhead on 2006-07-13
This is true philippe_carlo, having used CRT type monitors I know what flicker looks like and this LCD monitor is not flickering. When I scroll up and down on a webpage for example I can see that the scrolling isn't as smooth in Linux as it is in Windows, I am not sure if that is the problem or not but I was just hoping that there was some way to speed up the x server or give it more resources so that it was smoother to see if things improved.
I am begining to think it might be a medical problem I have because I feel the same after playing a 3D type game in Windows.

---

### Post by philippe_carlo on 2006-07-13
Ok, THAT I have seen too. The only way around this however is a video card with accelerated 2D drivers for Xorg, I'm afraid. I'm not sure if there is a better Xorg driver for your card, though. Good luck.

---

### Post by arrowhead on 2006-07-13
Thank you very much philippe_carlo, I am glad that someone has heard of this before and now I know I'm not imagining it :D.
I do have an old 2D only graphics card, I might dig that out and give it a try. I'll let you know if it works.

David

---

### Post by mcduck on 2006-07-13
here's some tricks you could try to make Gnome faster:

1. open Configuration Editor (in Applications/Accessories, or run 'gconf-editor' in terminal)

2. browse to apps/panel/global and uncheck the 'enable_animations'-key
3. in apps/metacity/general check the 'reduced_resources'-key

There are some more available here: [http://www.ubuntuforums.org/showthread.php?t=189309&highlight=nautilus+resources]("http://www.ubuntuforums.org/showthread.php?t=189309&highlight=nautilus+resources")

---

