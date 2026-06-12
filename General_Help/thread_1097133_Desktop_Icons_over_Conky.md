---
title: "Desktop Icons over Conky"
date: 2009-03-15
forum: General Help
---

### Post by Altay_H on 2009-03-15
I've messed around with [DSL]("http://en.wikipedia.org/wiki/Damn_Small_Linux") and although I don't like it much, it has one feature I've been unable to achieve in Ubuntu. In DSL I can drag icons over Torsmo (an older, lighter version of Conky). In Ubuntu when I try to drag icons over Conky they end up under it.

I don't mind trying out different desktop environments or window managers, so if the issue is that Conky doesn't get along with Gnome, Metacity, Xfce, or xfdesktop I don't mind trying a different DE/WM.

Does anyone know how to get the behavior I desire from Conky? Thanks for any help.

---

### Post by mistypotato on 2009-03-18
ditto....

:popcorn:

---

### Post by Altay_H on 2009-03-20
[This thread]("http://ubuntuforums.org/showthread.php?t=976017") suggests there's a setting in Compiz that allows Conky to sit between the icons and the wallpaper. I was hoping for a lighter-weight solution, but if it works I might switch to Compiz.

---

### Post by Altay_H on 2009-04-26
Bump...

Does anyone know how/why DSL can do this, but not Ubuntu?

---

### Post by Altay_H on 2009-05-08
I found another thread that seems relevant:
[http://www.linuxquestions.org/questions/linux-newbie-8/need-help-with-conky-530460/](http://www.linuxquestions.org/questions/linux-newbie-8/need-help-with-conky-530460/)

Unfortunately it suggests that the integration with the desktop does not work with nautilus. I think the "own_window no" option is what I want, but I don't know which desktop environments it works with. The "background yes" option also looks promising, but again, I don't know with which desktop environments it will work.

Does anyone know anything about conky's or torsmo's compatibility with various desktop environments? Is it possible to use Compiz to get the desired behavior like the thread mentioned in post #3 suggested?

---

### Post by terdon on 2009-06-10
Changing "own_window_type override" to "own_window_type normal" in .conkyrc fixed it for me.

---

### Post by Altay_H on 2009-06-10
Thanks for your reply, but changing own_window_type from override to normal only does the following for me (see attached pictures).

Are you using GNOME and Compiz as well, or did you get it to work with a different setup?

---

### Post by terdon on 2009-06-10
Try this:

```

own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```

That should make everything work fine except that minimize all, or show desktop or whatever also minimizes conky. So, go to compiz settings and uncheck "Hide Skip Taskbar Windows".

By everything working I mean conky allows the icons to be drawn with no problems and will cover any icons present below it. 

And yes, I am using Gnome and Compiz.

---

### Post by terdon on 2009-06-10
Sorry, I hadn't understood your original problem :oops:

My solution fixed the desktop icons and minimize problems but the icons are still under conky. I just have it on a part of my desktop where there are no icons...

---

### Post by Altay_H on 2009-06-10
> **terdon said:**
> Sorry, I hadn't understood your original problem :oops:
Well, I spent a couple minutes in GIMP preparing an illustration of the desired behavior, so I'll post the image to make sure no one else is confused.

It's ironic that the tiniest, most basic distribution of Linux does what I want by default, yet I can't get the most user-friendly, attractive distribution of Linux to accomplish the same task.

---

### Post by terdon on 2009-06-10
Are you using the same .conckyrc file in both distros?

---

### Post by Altay_H on 2009-06-10
> **terdon said:**
> Are you using the same .conckyrc file in both distros?
No. DSL does not use Conky. It uses the lighter-weight predecessor to Conky: Torsmo. I know very little about torsmo. Also, DSL does not use GNOME. Instead it uses JWM, so I image it's a completely different situation.

---

### Post by terdon on 2009-06-10
Well it may be  a feature specific to torsmo of course... The only other thing I can think of is trying a simple window manager like WindowMaker and see how it works there.

---

### Post by Altay_H on 2009-06-10
Well, torsmo isn't in the repositories because Conky is newer, has more features, and is maintained. Torsmo has bugs and lacks features, and Conky's code is based on Torsmo's. You'd think, therefore, that Conky should be able to do anything Torsmo can and more.

As far as desktop environments go, I'd like to know why the most popular two lack features provided by older, simpler, more basic desktop environments. What makes JWM so special that it can integrate a window into its desktop background despite the fact that neither GNOME nor KDE have accomplished this feat.

I noticed that in a thread linked earlier in this one someone suggested that the desired behavior is possible to accomplish via the Window Rules plugin for CompizConfig Settings Manager, but that thread hasn't received any replies either.

I'm slightly surprised that not knowing whether or not some of the desktop icons are hiding under Conky doesn't bother anyone. Hopefully this feature will be added to either GNOME or KDE in the future.

Also, I noticed that some people have a terminal as part of their desktop background. Are they also unable to see the icons covered by the terminal, or is it somehow possible to place a terminal between the desktop icons and the desktop background. Thanks for any information.

---

### Post by terdon on 2009-06-10
I found a workaround which is good enough for me. All settings basically as before:

```

own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
alignment top_right

```

Then, right click on the GNOME desktop and select "Keep aligned". That keeps all the  desktop icons aligned on the left, and away from conky. 

If using compiz, deselect "Hide Skip Taskbar Windows" in the "General" tab of "General Settings" in compiz config. Otherwise, conky will be minimized like other windows.

Conky can still cover desktop icons but icons are at least no longer placed under it and in any case it can be moved by Alt-clicking.

---

### Post by scarf on 2009-12-16
> **Altay_H said:**
> Well, I spent a couple minutes in GIMP preparing an illustration of the desired behavior, so I'll post the image to make sure no one else is confused.i, too, would like to figure out how to allow desktop icons to be placed on top of conky, so conky is basically between the wallpaper and the icons.

---

### Post by terdon on 2009-12-28
I think that is possible if you are NOT running compiz.

---

### Post by scarf on 2010-03-08
i don't even have compiz installed

---

### Post by waka_choko on 2010-05-13
> **Altay_H said:**
>  Does anyone know how to get the behavior I desire from Conky?

 Me too. I want to know how this should be done without compiz (Conky under desktop Icons). Did anyone find the solution? how about you @Altay?

---

### Post by Altay_H on 2010-05-13
> **waka_choko said:**
> Me too. I want to know how this should be done without compiz (Conky under desktop Icons). Did anyone find the solution? how about you @Altay?
I haven't found a satisfying solution, though I have gotten it to work with the following settings:
```

own_window no
double_buffer no

```

These settings produce the desired behavior (see attached screenshot), but cause conky to flicker every time it refreshes. I used these settings for about one day before the flickering drove me insane, and I switched it back. If you set "double_buffer yes" then the flickering is gone, but the desktop icons vanish until you hover over them.

I think "own_window no" might work if you use something other than nautilus. I'll post here if I decide to be adventurous and try out some other desktop.

---

### Post by binaryplease on 2011-01-20
Did you find out somethink on this topic?
I would love to have conky set up between wallpapaer and icons, since my configuration is meant to cover the whole desktop background. Plese let me know.

---

### Post by Altay_H on 2011-01-20
> **binaryplease said:**
> Did you find out somethink on this topic?
I would love to have conky set up between wallpapaer and icons, since my configuration is meant to cover the whole desktop background. Plese let me know.
I tried out Openbox, but since it's just a window manager and not a desktop environment the desktop icons weren't displayed at all. Installing a separate desktop environment lead to its own issues. I decided that GNOME is more important to me than Conky, so I gave up trying other setups. You can always try the "own window no" and "double buffer no" options and see if you're pleased with the result. It behaves correctly, it just flickers a lot.

---

### Post by Simian Man on 2011-01-20
I can't understand why this is something you want so bad, but then I can't understand using conky either so hey.

Anyway, just because torsmo isn't in the repos doesn't mean you can't install it.  If you've used LFS, you should be able to compile a simple program.  If you use Torsmo and JWM, then you should get the same results no matter what distro you're on.

---

### Post by RomanIvanov on 2011-02-12
Altay_H, please post a solution if you found it.

Covering of desktop icons is real inconvenience :(.

---

### Post by Altay_H on 2011-02-12
> **RomanIvanov said:**
> Altay_H, please post a solution if you found it.
My best solution is already posted in #20 of this thread. Changing desktop environments is a bigger sacrifice than giving up Conky, so I just don't use Conky anymore.



EDIT:
The following settings in your .conkyrc file *might* be good enough for you:
```
own_window no
double_buffer yes
```

---

### Post by stinkeye on 2011-02-12
Just move conky to the right hand side by adjusting these preferences in
your conkyrc.
```
alignment tr
gap_x 
gap_y  
```


For info enter in terminal
```
man conky
```

---

