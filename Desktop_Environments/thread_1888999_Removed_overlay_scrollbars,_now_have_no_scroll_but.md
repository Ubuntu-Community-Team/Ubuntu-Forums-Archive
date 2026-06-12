---
title: "Removed overlay scrollbars, now have no scroll buttons"
date: 2011-11-30
forum: Desktop Environments
---

### Post by SixedUp on 2011-11-30
Like many, I'm having real problems with Unity. I don't want to switch distributions, so I've tried Gnome Shell, Lubuntu and Xubuntu, but for various reasons (not all technical) I'm probably going to be forced to stick with Unity, which I'm not completely happy about. So I'm trying to customise it to better suit my needs.

I've disabled the overlay scrollbars on 11.10, and now have "normal" scrollbars back throughout the operating system. However, there are no scrollbuttons present (except on Firefox!), which makes fine control on long scroll buffers a real issue. 

Given that Firefox is "right" and nothing else is, I suspect this is simply a GTK theme issue. However, but I've never really messed with themes before; at most I've switched to one of the other presupplied themes in "Appearance Preferences", so I'm struggling to work out what to do next.

Can anyone point me in the right director to get scrollbuttons at each end of the scroll bar on all the windows that Unity would normally put its overlay scrollbars?

Thanks!

---

### Post by vasa1 on 2011-11-30
> **SixedUp said:**
> ... However, there are no scrollbuttons present (except on Firefox!), which makes** fine contro**l on long scroll buffers a real issue. ...
Can anyone point me in the right director to get scrollbuttons at each end of the scroll bar on all the windows that Unity would normally put its overlay scrollbars?
Thanks!
I don't have scroll buttons either but don't have any problems with fine control. Could you elaborate on why you need those buttons for fine control?

---

### Post by SixedUp on 2011-11-30
> **vasa1 said:**
> I don't have scroll buttons either but don't have any problems with fine control. Could you elaborate on why you need those buttons for fine control?

Sure ... this is on a laptop, with no mouse. On windows with very large scroll buffers (particularly things like terminals with several thousand lines of output in them) it is almost impossible to accurately position within the buffer because the bigger the buffer, the more magnified the effects of moving the scrollbar puck becomes. I'm sure it's possible to find other ways to achieve this aim, but my preference is for some scroll buttons :)

---

### Post by vasa1 on 2011-11-30
> **SixedUp said:**
> Sure ... this is on a laptop, with no mouse. On windows with very large scroll buffers (particularly things like terminals with several thousand lines of output in them) it is almost impossible to accurately position within the buffer because the bigger the buffer, the more magnified the effects of moving the scrollbar puck becomes. I'm sure it's possible to find other ways to achieve this aim, but my preference is for some scroll buttons :)

Like you, I've uninstalled the overlay stuff.

I hope you don't think I'm being frivolous but on my laptop I'm quite content with PageUp and PageDn and the Up and Down arrows since my hands are already on the keyboard.

I've even modded the scrollbars in both Chrome and Firefox to omit the scroll buttons!

---

### Post by SixedUp on 2011-11-30
> **vasa1 said:**
> Like you, I've uninstalled the overlay stuff.

I hope you don't think I'm being frivolous but on my laptop I'm quite content with PageUp and PageDn and the Up and Down arrows since my hands are already on the keyboard.

I've even modded the scrollbars in both Chrome and Firefox to omit the scroll buttons!

Not at all. That's one of the big positives of Linux - we can all make it work the way that works best for us - if we can only work out how! The page up and down and cursor keys are the workarounds I'm using now, but I'd much prefer the scroll bar buttons back if anyone knows how ... ?

---

### Post by Frogs Hair on 2011-11-30
Remove Overlay Scrollbars ```
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar3-0.2-0 liboverlay-scrollbar-0.2-0

```

Install Overlay Scrollbars ```
sudo apt-get install overlay-scrollbar liboverlay-scrollbar3-0.2-0 liboverlay-scrollbar-0.2-0
```

---

### Post by vasa1 on 2011-11-30
> **SixedUp said:**
> ..., but I'd much prefer the scroll bar buttons back if anyone knows how ... ?
If I come across something, I'll post here (if it isn't too late).

---

### Post by kansasnoob on 2011-12-01
> **SixedUp said:**
> Like many, I'm having real problems with Unity. I don't want to switch distributions, so I've tried Gnome Shell, Lubuntu and Xubuntu, but for various reasons (not all technical) I'm probably going to be forced to stick with Unity, which I'm not completely happy about. So I'm trying to customise it to better suit my needs.

I've disabled the overlay scrollbars on 11.10, and now have "normal" scrollbars back throughout the operating system. However, there are no scrollbuttons present (except on Firefox!), which makes fine control on long scroll buffers a real issue. 

Given that Firefox is "right" and nothing else is, I suspect this is simply a GTK theme issue. However, but I've never really messed with themes before; at most I've switched to one of the other presupplied themes in "Appearance Preferences", so I'm struggling to work out what to do next.

Can anyone point me in the right director to get scrollbuttons at each end of the scroll bar on all the windows that Unity would normally put its overlay scrollbars?

Thanks!

In my experimenting with the classic "fallback" in Oneiric I found that removing the overlay-scrollbars really does tend to mess up Unity. I noted that in step #9 here:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

You might want to browse through that whole post, and see if it's of any interest to you.

---

### Post by vasa1 on 2011-12-01
> **kansasnoob said:**
> In my experimenting with the classic "fallback" in Oneiric I found that removing the overlay-scrollbars really does tend to mess up Unity. I noted that in step #9 here:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

You might want to browse through that whole post, and see if it's of any interest to you.
Hi, Kansasnoob, I've removed the overlay-scrollbars but have not noticed anything adverse as a result. Other than that, I haven't tweaked Unity (3D). Is it possible that the reason for Unity  "messing up" in your experience lies elsewhere?

---

### Post by MonoAM on 2011-12-17
Hello,

I'm also having this issue. Also found the overlay scrollbars difficult to use, so I removed them but now the scrollbar doesn't have the scroll buttons and I do need them. Also, the shade of the scroller is very pale and difficult to see within the scrollbar. I also thought it could be a theme issue and even tried changing the theme (via gnome-tweak-tool), but the only themes that show the scrollbar properly make Ubuntu look like an old Unix graphics terminal from 1990! Is there a way of tweaking the Ambiance theme to re-enable the scrollbar buttons and change the scroller colour? 

thanks,
Mono.

---

### Post by gaigoleb2 on 2011-12-27
really the overlay scrollbars are a pain. follow [http://hashprompt.blogspot.com](http://hashprompt.blogspot.com) to remove them in few easy steps

---

### Post by MonoAM on 2011-12-29
> **gaigoleb2 said:**
> really the overlay scrollbars are a pain. follow [http://hashprompt.blogspot.com](http://hashprompt.blogspot.com) to remove them in few easy steps

Thanks gaigoleb2. I found this post on removing the overlay scrollbars in that blog:
[http://hashprompt.blogspot.com/search?q=overlay](http://hashprompt.blogspot.com/search?q=overlay)

However, as you can see in the very last screenshot, the resulting scrollbars have no buttons and the scroller itself is quite difficult to see. The post doesn't mention anything about this issue, which is what we're trying to solve in this thread.

Thanks,
Mono

---

