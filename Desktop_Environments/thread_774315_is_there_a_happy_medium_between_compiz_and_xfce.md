---
title: "is there a happy medium between compiz and xfce?"
date: 2008-04-29
forum: Desktop Environments
---

### Post by linuxgrrl on 2008-04-29
hi,
I started with a completely default installation of Ubuntu Gutsy, but it did not work properly with f-spot (fullscreen did not work), at first I thought it was an f-spot bug but then I learned I needed a "compositing" window manager, so installed compiz and that fixed my f-spot problem.

But comppiz uses about 17-25% of my CPU, even if I choose "no effects" or whatever the lowest option is. I am usng this box for hdtv playback (mythtv) and I need all the CPU I can get.  So I installed XFCE, which works great with f-spot and myth (no stutter on the HDTV - yay!) but it is frankly too ugly to use for anything else.  I'm not that into eye-candy but I can't even surf the web on this thing (it's a livng room PC) without making my eyes bleed.  I'm not sure if it's the lack of anti-aliasiing or what, but XFCE's just not going to cut it.

Is there a "compositing" wndow manager that uses less memory than Compiz, but is not going to make me go blind? :)  Or is there some way to strip Compiz down even further?

thank you in advance!

---

### Post by agim on 2008-04-29
You can change the way xubuntu looks.
But if you don't want to do that, I would suggest kde-core. It worked incredibly well on my machine and left a very small footprint. You won't get all of the wonderful kde apps, but it worked well for me.
I don't know if that is always the case, or just a quirk with my machine.
Good luck!

There are also a lot of other photo apps than f-spot. If thats the entire hold up, than rather than change your system, it would probably make more sense to change a single app.

---

### Post by linuxgrrl on 2008-04-29
> **agim said:**
> There are also a lot of other photo apps than f-spot. If thats the entire hold up, than rather than change your system, it would probably make more sense to change a single app.

yes, that would make more sense but I have 4 years of photos tagged in f-spot.  Guess I'll try kde-core - thanks for the suggestion.

As to the prettying-up of xubuntu, I'm not sure where to start. The fonts seem 'off' somehow ... some too small, some just plan ugly ... guess I'll start researching that.

---

### Post by agim on 2008-04-29
hmmm, four years of photos. That makes it a bit harder. If you find a reasonable solution be sure to post it. Someone will inevitably have the same problem.

---

### Post by eriqjaffe on 2008-04-29
> **linuxgrrl said:**
> Is there a "compositing" wndow manager that uses less memory than CompizThere's xcompmgr, which can run with any window manager.  I run it with Openbox and it doesn't really seem to eat up much CPU at all.

---

### Post by linuxgrrl on 2008-04-29
> **eriqjaffe said:**
> There's xcompmgr, which can run with any window manager.  I run it with Openbox and it doesn't really seem to eat up much CPU at all.

Okay, cool, I want to make sure I understand now.  Is Openbox a substitute for (i.e, replaces) XFCE?  If so, can you give me a sense of its relative "pretty-ness" (or lack thereof) ... how will it look on a living room pc?

---

### Post by linuxgrrl on 2008-04-29
and come to think of it, is there a way to run xcompmgr with the default Gnome installation, thereby solving my original problem without Compiz?  

The possible options boggle the mind ...:confused:

---

### Post by Pogeymanz on 2008-04-29
Well, XFCE can be made to look as pretty as Gnome, technically. But that might be more work than you want to do.

So, how about you use Gnome and use xfwm4 as your window manager?

You see, Gnome and XFCE are desktop environments that use Metacity and xfwm as window managers, respectively. What you need is a compositing window manager, which is why you install compiz. I'm saying, instead of using compiz or metacity or the whole XFCE DE, just steal its window manager.

I don't use Gnome, so I'm not exactly sure how to set xfwm as the default window manager, but if you're already logged into Gnome, you can open the terminal and type:
```
sudo xfwm4 --replace &
```

I think. It might be one dash... I don't know.

Then you will have the Gnome you're used to, but a compositing window manager. (I think xfwm is better than metacity in all ways anyway)

---

### Post by urukrama on 2008-04-29
> **linuxgrrl said:**
> Okay, cool, I want to make sure I understand now.  Is Openbox a substitute for (i.e, replaces) XFCE?  If so, can you give me a sense of its relative "pretty-ness" (or lack thereof) ... how will it look on a living room pc?

Openbox is a window manager that you can use either on its own, or inside a desktop environment like Gnome, Xfce and KDE. 

Openbox can be pretty, I think -- you basically decide how it looks.

There are plenty of themes to choose from (see box-look.org), and Openbox is very configurable. Coming from Gnome and Xfce you may find it a bit too spartan, but keep in mind that that is Openbox' strength: Openbox just manages the windows, and allows you to add whatever else you want to it. It therefore needs a little attention to set up your Openbox desktop, but it isn't that hard. Openbox comes with great configuration tools (obconf and obmenu) that make it all super easy. Give it some time and you might fall in love with it, like so many did before you.

If you want to try the Openbox way, have a look at the guide linked to in my signature. It should help you get started and overcome the usual obstacles to get a nice Openbox setup.

If you want to know what Openbox can look like, have a look at [box-look.org]("http://box-look.org/index.php?xsortmode=high&page=0&xcontentmode=7402") or at the [screenshots]("http://urukrama.wordpress.com/screenshots/") on my blog (perhaps not everyone's aesthetic though :-))

As for your problems with Xfce, what exactly is the font problem? Have you tried adjusting the font settings (in Menu > Settings >User Interface Settings)? Perhaps post a screenshot to show us what exactly goes wrong.

---

### Post by eriqjaffe on 2008-04-29
> **linuxgrrl said:**
> and come to think of it, is there a way to run xcompmgr with the default Gnome installation, thereby solving my original problem without Compiz?Off-hand, I'm not sure.  I don't see why not, though, xcompmgr isn't a window manager on its own, it just enables compositing.

You can just install it from Synaptic, and then give it a test-drive by invoking it from a terminal:

```
xcompmgr -cCfF -t-5 -l-5 -r4.2 -o.55 -D6 &
```

Then you could add it to your startup items if it works well.  There's also a utility called transset that lets you set individual window transparency.  I don't use that, though.

---

### Post by linuxgrrl on 2008-04-30
> **EmosSuck777 said:**
> Well, XFCE can be made to look as pretty as Gnome, technically. But that might be more work than you want to do.

So, how about you use Gnome and use xfwm4 as your window manager?



Ding ding ding!!  That's exactly what I needed. The command you suggested did not quite work for me (it seemed concerned that another window manager was already running) but I tried using pkill as described here: [http://www.ubuntutips.net/node/17](http://www.ubuntutips.net/node/17) 
and, voila, compositing gnome using 3% CPU. :guitar:
Thank you!!!!!

---

