---
title: "xubuntu docks?"
date: 2007-11-14
forum: Desktop Effects &amp; Customization
---

### Post by Mikooster on 2007-11-14
I know this is a common topic, but I have done a lot of searching and can't find anything about my problems:

I am running xubuntu on my laptop.  I have tried both adesklets yab, and gdesklets starter bar.

yab works, but I can't edit the default icons.  When I right click > config, nothing happens. I read that you can edit the config.txt file manually in the /home/.desklets/yab directory.  I did that, and for some reason yab won't update itself and it still has the default icons on it.  I've tried restarting the program and rebooting my computer but it hasn't worked.

When I couldn't get yab to work, I installed gdesklet's starter bar.  This doesn't work at all.  It opens and looks fine, but if I click on the default "home" icon, nothing happens.  If I right click > edit launcher, or add launcher, nothing happens.  I can't add or edit or change the shortcuts on it.

I don't know what else to do.  I'd really like some sort of dock.  Does anyone know how I can fix either of those, or perhaps know of a better dock to try?  I'm a major newb and I don't know what will work well on xubuntu and what won't.

Thanks for your help!

---

### Post by Espreon on 2007-11-14
If your system can handle it, try AWN + Compiz Fusion (CF is needed).

---

### Post by Mikooster on 2007-11-14
I don't think my laptop could run that well.  I want something light and fast, that's why I installed xubuntu in the first place.

That's why I thought adesklets would be good if I could get it to work...

thanks though

---

### Post by Espreon on 2007-11-14
Well could you give me your system specs?
So I can see if CF is out of the question, if the comp was made in the middle of this millennium say 2004-2005 minimum there is a decent chance you can get CF to run efficiently and just cause you have CF does not mean you need to enjoy its resource eating eyecandy we all know and love.

 Because my old desktop  (made in 2000) that ran Ubuntu 7.04, now runs Xubuntu 7.10 (I might put CF on it) (I think it is a medium end system for its time) could do lots of basic eyecandy in Beryl SVN (like the Cube, Snow and wobbly windows and glass) without that much system penalty.

---

### Post by Mikooster on 2007-11-14
Thanks for helping me.

I have a Dell laptop which is decently new, but only 12.1" so it's not very high powered but it's not bad:

1024mb RAM
Intel 2.0ghz
120GB HD...
no graphics card 

I also don't really get how to install AWN because I don't see it in the package manager?

---

### Post by Espreon on 2007-11-14
So I am assuming it is an integrated chip, it might be able to work, so here what you need to do:

1. Open Synaptic

2. Settings (I think)>Repositories

3.Enable the Universal Repos (check the checkbox)

4. Close out of that window and when it prompts you to Reload apt hit cancel

5. Hit the big Reload button

6. Close out of Synaptic

7. Download the attached script named cfscript.sh to your home folder

8. Enter this in the terminal:

```

sh cfscript.sh

```

9. Reboot and see if CF works if not try to obtain help to get it working

You may need to enter this in the terminal to start CF:

```

compiz

```

10. If CF is working please resume

11. To get AWN working follow this tutorial: [http://ubuntuforums.org/showthread.php?t=572019](http://ubuntuforums.org/showthread.php?t=572019)

Good Luck!

If CF refuses to work after lots of help or its WAY too slow download the other attached script called uncfscript.sh, download it to your home folder and enter this in the terminal:

```

sh uncfscript.sh

```

---

### Post by Mikooster on 2007-11-14
I installed compiz and it didn't work - it said that "no configurable displays" were found...

however, it made all my window title bars disappear, and I don't know how to get them back!  Even after removing compiz, and restarting, they are not back!

---

### Post by Espreon on 2007-11-14
Thats weird, try entering this in the terminal:

```

xfwm4

```

Sorry for the wasting of your time, but if you could figure out the make and model of your integrated chip I am sure you can get help to get CF to work.

---

### Post by Mikooster on 2007-11-14
Typing that command worked, lol... thanks.

Don't apologize - I really appreciate your time and help.

I will see if I can get it working but I wish gdesklet or adeskelts worked.  I just don't understand why they won't.

---

### Post by Espreon on 2007-11-14
OK, Thanks.

---

### Post by sanicki on 2007-11-14
My two cents: For an older machine the best thing to do is stick with yab. It just needs to be restarted to show your changes.

---

### Post by Mikooster on 2007-11-14
I said in my original post, the problem is that it's not applying the changes I'm making.

I have restarted it, restarted my computer, and reinstalled (registered) it.  I don't know why it won't update the changes but it won't...

---

### Post by Jouke74 on 2007-11-15
Might be a poor man's solution. But I simply emptied the trash and desktop switcher from lower panel / menubar. Switched the panel to make the width not full screen.


[IMG]http://www.xfce.org/images/about/tour/xfce44-panel-manager.png[/IMG]

Removed the tasklist or whatever it's called from the top tab bar and added the windows Iconbox. 

[IMG]http://www.xfce.org/images/about/tour/xfce44-panel-additem.png[/IMG]

[IMG]http://www.xfce.org/images/about/tour/xfce44-panel-iconbox.png[/IMG]

It's not exactly Awn or Kibda or Adesklets. But it doesn't eat resources either.
Plus no compiz fusion or composite required....

See also: [http://www.xfce.org/about/tour](http://www.xfce.org/about/tour) REALLY informative.

---

### Post by Mikooster on 2007-11-15
> **Jouke74 said:**
> Might be a poor man's solution. But I simply emptied the trash and desktop switcher from lower panel / menubar. Switched the panel to make the width not full screen.


I don't mind your idea really, the only thing that bothers me about your solution is that if I maximize a window, it won't take up the whole screen and it will leave a big bar on the bottom where that panel is.

Is there a way around that?  can you make the panel always on the desktop rather than always in front of windows?

---

### Post by Jouke74 on 2007-11-15
I just moved everything to the top panel :)
Never looked at those options so I don't know, check using the window margins settings, and panel options maybe.

Screenshot of my desktop: [http://img248.imageshack.us/my.php?image=screenshot2nw5.jpg](http://img248.imageshack.us/my.php?image=screenshot2nw5.jpg)

---

### Post by tears.of.angels on 2007-11-15
i'm not sure how well it works in gutsy, but i know in feisty if i enabled display compositing 
(settings manager>window manager tweaks>compositor>enable)

then i was able to get some programs that needed compiz/beryl to work for me. i know i tried kiba dock, and while it was a little slow (i think that's my laptop's fault) the program worked without compiz.

you could try enabling xfwm's compositing and see if that works.

---

### Post by sanicki on 2007-11-16
Look for the hidden ~/.adesklets file. Try deleting it then configuring yab then starting it. 

> **Mikooster said:**
> I said in my original post, the problem is that it's not applying the changes I'm making.

I have restarted it, restarted my computer, and reinstalled (registered) it.  I don't know why it won't update the changes but it won't...

---

### Post by darthchaosofrspw on 2008-02-25
I wish Engage (the standalone version, not the E17 module) was still around somewhere. IIRC, you could use that without using a compositing window manager (such as Compiz, Beryl, or Compiz Fusion).

EDIT: I tested Simdock on my old Ubuntu 7.04 system and really liked it. I noticed on getdeb.net that the version of Simdock on there is for Feisty and not Gutsy. I'll try to download the source code and build a Debian package.

---

