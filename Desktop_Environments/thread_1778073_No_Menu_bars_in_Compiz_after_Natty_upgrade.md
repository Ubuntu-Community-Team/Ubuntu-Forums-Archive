---
title: "No Menu bars in Compiz after Natty upgrade"
date: 2011-06-08
forum: Desktop Environments
---

### Post by cainram on 2011-06-08
After upgrading to Natty from the previous version and switching to Ubuntu Classic my compiz settings were completely wiped out. No problem, I just re-entered them. The problem is that I don't get any menu bar on my windows. It also happens once in a while in Metacity but using the compiz fusion icon utility to reload the window manager will usually fix the issue. I have had this problem intermittently in the past but have always been able to resolve it by reloading the window manager.
Now when I'm using compiz I ALWAYS have this issue and it makes compiz unusable. Compiz is not just eye-candy for me, it has become integral to the way I use my computer. If anyone has any ideas I'm all ears.

Thanks in advance

---

### Post by Copper Bezel on 2011-06-08
Menu bars, or window decorations (title bars?) If it's the latter, resetting Compiz with gconftool2 should, I think, fix the problem. If not, [try this guide]("http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html"). It's Unity-focused but applies to all the common Compiz problems in 11.04.

---

### Post by jerrrys on 2011-06-08
thats a nice site CB

---

### Post by cainram on 2011-06-08
Hey, sorry! I'm usually really specific about these things. It is the Title bar NOT the menu bar. So what is the specific method for using the gconf tool to reset the situation... I've been using ubuntu since 8.04 so I'm no noob but I just don't want to dig a hole. I could re-install but then I wouldn't learn anything.

Thanks

---

### Post by Copper Bezel on 2011-06-08
@ jerrrys - Sikander Khan and Krytarik do great work, yeah. There's a reason they're all over my sig. = )

@ cainram - Hey, cool, I came in on 8.04 as well. = ) This sequence of commands,

```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
```

will reset all your Compiz configurations to default, as if you *were* reinstalling Compiz after a purge. (Essentially, this is the same as erasing an application's folder under .config.) If you don't want to wipe your settings right away, try creating a new user account and see if the problem persists there. If it does, we might need to dig a little deeper than resetting user configuration, which probably *would* mean reinstalling Compiz outright.

I think resetting Compiz should work, however. The new Compiz release is a complete re-write, as I understand it, and there are a lot of new problems, particularly when inheriting settings from an older installation.

One other thing to verify is this: were you using an Emerald theme previously? If so, you'll need to either change over to gtk-window-decorator (you can do this in the session to check by running gtk-window-decorator --replace and permanently from CCSM's Window Decorations plugin) or get a new, patched version of Emerald that was released recently. Annoyingly, the version of Emerald included in the Natty repos just doesn't work.

---

### Post by cainram on 2011-06-09
CB - First off, I'm in SE Wisconsin so MIDWEST 4 LIFE! Anyway, I'm not sure about the Emerald thing... I'm pretty sure that's something I've installed at some point. I use the old school Human theme complimented by the rotating cube, wobbly windows and cube deformation... and 3d windows which I could live without.(stuck in a Human theme world... I was totally psyched when I discovered enabling the Human theme would put my max/min/close buttons back WHERE THEY BELONG!!!!)
I'm off to bed but I'll start hacking away when I get a chance. Thanks for the help and I'll be contacting you if I have any other problems.
Check out the FLOSS weekly featuring Compiz if you haven't already, it's a great episode.
Edit: I should note that I've experienced this issue consistently (although intermittently) over the years on a number of different systems and versions of Ubuntu. I even installed a new GFX card recently and still... Anyway...

---

### Post by cainram on 2011-06-09
Wow, ok now I can't move windows around by grabbing the title bar. Hmmmm...

---

### Post by cainram on 2011-06-09
So, I lied about going to bed.
I ran the commands you (CB) posted and rebooted, maybe not necessary but whatever. Switched over to Compiz using the Compiz Icon utility and everything was ok. Until I enabled the 'Rotate Cube' plugin. It asked the usual questions about disabling and enabling this and that and then... nothing. It (and 'desktop cube') remained unchecked. I tried again, answered the questions and BAM! No title bars. Again. Let's talk about re-installing Compiz... Just use synaptic or what? I could figure it out on my own but having a guide is always better.

P.S. What gives with this goofy scroll bar situation... UGHHH!

---

### Post by Copper Bezel on 2011-06-09
= )

The new scrollbars are meant to save space, since "nobody" uses scrollbars anymore, but you can revert them:

```
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar-0.1-0
```

I haven't played with Compiz in 11.04, but I know the Cube causes hell. [Here's]("http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html") a guide for restoring it. Again, Unity-focused, but applies to Classic as well.

Just so you know, *any* problem that crashes Compiz will result in the same appearance, with the titlebars and window borders disappearing, so this is probably the new problem, not related to any problems you've had in the past with a similar result. This is because Compiz is the window manager and decorators like gtk-window-decorator and emerald are essentially plugins for it, so they stop rendering without Compiz running. You'd see the same phenomenon if you were using Metacity and killed the process, too.

---

### Post by cainram on 2011-06-09
Wow. Every time I log in it is something different. I tried re-installing compiz and now even when I go into ubuntu classic I get the unity menus on the top and left. Huh. Looks like I'm going back to 10.04. I've always liked using an LTS anyway.

Thanks for all of the help, I appreciate it.

---

### Post by kd4dii on 2011-06-12
Hi
     If you have the fusion icon installed run it and rt click the icon and use the select display manager and enable gdm.Also in compis config there is a window decoration plug in,  Enable it and check the move windows and resize windows options are checked.
     Hope this helps
        Bob

---

### Post by wildmanne39 on 2011-06-12
> **cainram said:**
> So, I lied about going to bed.
I ran the commands you (CB) posted and rebooted, maybe not necessary but whatever. Switched over to Compiz using the Compiz Icon utility and everything was ok. Until I enabled the 'Rotate Cube' plugin. It asked the usual questions about disabling and enabling this and that and then... nothing. It (and 'desktop cube') remained unchecked. I tried again, answered the questions and BAM! No title bars. Again. Let's talk about re-installing Compiz... Just use synaptic or what? I could figure it out on my own but having a guide is always better.

P.S. What gives with this goofy scroll bar situation... UGHHH!
Hi, To get the cube working in natty use this link.
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)
after you have finished with this guide and you change other settings it will mess up your windows again so just log out and back in and they will be fixed.

---

