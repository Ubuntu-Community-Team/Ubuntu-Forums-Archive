---
title: "Xgl/Compiz (Nvidia) Memory hog?"
date: 2006-07-26
forum: Desktop Environments
---

### Post by shawnrgr on 2006-07-26
Is this a memory hog? How safe is it and if i have problems is it easy to uninstall?

---

### Post by shawnrgr on 2006-07-26
anyone? everyone is alking about it. i just want to make sure my laptop can handle it and still not notice a change in performance. (amd64 3700+ 1gig ram ubuntu6/gnome)

---

### Post by John.Michael.Kane on 2006-07-26
shawnrgr you need to give complete system spec's. video card make ect. if anyone going to be able to offer help.

---

### Post by RAOF on 2006-07-26
In order:
1) Depends on the current development status ;).  Not for me, at the moment, but it has in the past had some annoying memory leaks.

2) Totally safe, as far as I can give that assurance.  It's not going to eat your children, but maybe you'll be the first to find a file-destroying bug.  I'd be amazed if it did something like that, though.

3) Easy to uninstal.

4) Unless your laptop has a seriously underpowered graphics card, you won't notice any negative change in performance.  If you haven't been using a composite manager, some things will probably be **faster**.  Composite hides some redraw bugs in GTK :)

Check out [compiz.net](compiz.net).

---

### Post by jgcamp99 on 2006-07-26
I'm using it with an ATi Radeon 9600 XT 256 MB card. It is noticably more mechanical when opening a window, meaning the border os say Firefox will square out in sequentially larger boxes. It's probably has more to do with the effects and settings. I don't see it taking more resources of physical memory, it's probably loading and caching more in the video card's memory in that regard. The Ubuntu install I did was the session xGL installation, so I have to go out of my way to use it. Otherwise, on a 35 GB partition, it's not even noticeable in that regard. 

Now Project Looking Glass is another story, it takes more resources from what I see in the physical memory.

I would say that perhaps the reason xGL & Compiz are preferred to PLG, is for that reason. Linux and even OS X users are resource minimalists when it comes to physical memory that an OS requires. Windows users from my perspective, well, they want to minimalize what system memory is used, but many could care less if their OS/Desktop loads to 250-300 MB.

Ubuntu loads on mine 7 % of 1.5 GB of PC3200 for Programs not running xGL, 11 % running it in session mode. So what are we talking about here, the difference between 105 MB and 165 MB in regards to 1.5 GB of system memory. I don't know what it does regarding the video card memory. Naturally there is a tax on the resources, but with today's computer hardware it's not an issue if you've built a robust system. Walk out with the bare minimum configuration many of these OEM's build and yeah, you'll have trouble, then again xGL and Compiz aren't the problem, that a more modern day video card and another stick of memory won't cure. Even without xGL and Compiz, upgrading those 2 components will make a big difference.

---

### Post by shawnrgr on 2006-07-27
well too late, i already installed it lol. but thanks for you comments. as for performace. it runs great. seems alot smoother than before. and the cube view is tripn me out lol, its awsome.

only drawbacks for me:

I cant watch full screen video from browser (mplayer-firefox) havent tried with normal video from hd bc i don't have any, will try tomorrow.

also window resizing wasn't that great to begin with but now its x5-10 worse. just really laggy and painful to watch really.

however im overly estatic about this and everything else works great. give it a year or two and this will be standard on new distros. I can't wait for that.

---

