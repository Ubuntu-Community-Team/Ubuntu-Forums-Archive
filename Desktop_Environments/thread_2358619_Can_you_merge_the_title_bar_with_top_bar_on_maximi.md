---
title: "Can you merge the title bar with top bar on maximized windows, with Ubuntu Gnome?"
date: 2017-04-15
forum: Desktop Environments
---

### Post by toninguy3n on 2017-04-15
So I've been using Ubuntu 16.04 with Unity 7 for quite some time and I was very satisfied with how simple and efficient it is for workflow (with the exception to graphical glitches that gets annoying, but I was mostly happy with what it could do). With the future releases of Ubuntu moving towards Gnome (unless rumors are wrong and Unity 8 is still being officially worked on), I decided to install ubuntu-gnome 17.04 on my laptop and I've noticed a few things that I would really miss from Unity 7. 

What I liked about Unity 7 was that you could include menus in your title bars, and those menus would merge with the top bar when you maximize a window; this is great for saving screen space, even on mid-large screens (I do this on my desktop as well for 27" 1440p - laptop is 13" 1080p). In Gnome, there doesn't seem to be a way around this in the settings. I've checked some extensions, but they don't exactly do the same thing. One of the extensions I've tried was to hide the top bar when a window is maximized, but it comes at the cost of losing the clock, which is too great of a sacrifice to me. I don't want to press the window/super button or move the mouse all the way to the top left corner, just to make the clock pop up. 

I liked how Unity 7 would hide the menu and show the title of the window in the top left of a maximized screen. Gnome separates this, so you have 2 giant bars that serve little purpose. I also like how the time, settings, power, background apps are all in the top right corner for unity 7, with opened applications in the left bar which I leave on autohide to save space. 

Gnome gives great first impressions, but when you start using it, it doesn't feel as great as Unity 7. I commend it for not glitching all over the place like Unity does on my laptop and desktop (which I believe is more of an issue with Xorg), but the amount of space it unnecessarily consumes is a deal breaker. Gnome looks pretty, it's smooth, but it hasn't been as great for productivity so far (~12 hours use over 2 days). 

Is there an extension that would alleviate these issues I'm having with Gnome (on a usability standpoint), or are there any desktop environments that do the same things I liked most about ubuntu unity 16.04? I value screen space, so if there's a bar on top and on bottom for a single window, or 2-3 bars on top, I'll start to feel that it's wasted space. 1 bar on top is enough, and I'm happy with how Unity handles it, but I need to consider alternatives if unity 8 development is discontinued.

---

### Post by Frogs Hair on 2017-04-16
I would check at the link . All I located were discontinued projects and I'm guessing there's a reason for that.There was a fairly primitive attempt in 2011 still available in 2015.  

[https://extensions.gnome.org](https://extensions.gnome.org)

---

### Post by vanadium on 2017-04-17
You probably did not yet bump into the "Pixel saver" extension. This will remove window decorations (aka the title bar) for maximized applications. Gnome Shell (at least in version 3.22) shows the title as the application menu button, so you keep the title. The windows control buttons are also relegated to the top bar.

---

### Post by toninguy3n on 2017-04-17
> **vanadium said:**
> You probably did not yet bump into the "Pixel saver" extension. This will remove window decorations (aka the title bar) for maximized applications. Gnome Shell (at least in version 3.22) shows the title as the application menu button, so you keep the title. The windows control buttons are also relegated to the top bar.

That sounds like a part of what I'm looking for. I'll check it out some time tonight or tomorrow and will report back its compatibility with Gnome 3.24 in 17.04.

---

### Post by toninguy3n on 2017-04-19
The "Pixel saver" was able to successfully install. When it works, it's great, but there are some applications that it doesn't work with. LibreOffice Writer and Terminal are some examples where it wasn't able to hide the titlebar on maximized state. I guess I'll play around with KDE in the future (all I know is that it was really buggy when I used it in the past), but I'll keep Gnome on the laptop a little longer while sticking to Ubuntu Unity 16.04 on my main desktop.

---

### Post by monkeybrain20122 on 2017-04-20
Short answer is no. I have been trying to find such an extension but can't . You mentioned kde and actually you can duplicate a lot of unity's feels and look with plasma 5 including menus in the title bar apparently. [https://www.youtube.com/watch?v=F1i7jAtHcw4](https://www.youtube.com/watch?v=F1i7jAtHcw4)

I am trying this out on a Fedora kde partition. There are some glitches here and there and doesn't feel as polished as unity (probably can be adjusted, I am not very experienced with KDE) but so far a lot better than gnome shell, for one thing there is no ugly thick empty top bar in windows even out of the box,  animation is a lot smoother rather than the jerky laggy way of gnome shell. It is very configurable, perhaps too configurable if that can ever be a bad thing. I am only half way through so can't specifically tell you about the top bar and menu thing yet.

---

### Post by toninguy3n on 2017-04-21
> **monkeybrain20122 said:**
> Short answer is no. I have been trying to find such an extension but can't . You mentioned kde and actually you can duplicate a lot of unity's feels and look with plasma 5 including menus in the title bar apparently. [https://www.youtube.com/watch?v=F1i7jAtHcw4](https://www.youtube.com/watch?v=F1i7jAtHcw4)

I am trying this out on a Fedora kde partition. There are some glitches here and there and doesn't feel as polished as unity (probably can be adjusted, I am not very experienced with KDE) but so far a lot better than gnome shell, for one thing there is no ugly thick empty top bar in windows even out of the box,  animation is a lot smoother rather than the jerky laggy way of gnome shell. It is very configurable, perhaps too configurable if that can ever be a bad thing. I am only half way through so can't specifically tell you about the top bar and menu thing yet.Great video! One of my major gripes with KDE in the past, was the stability. I remember that it was a huge resource hog as well as being super buggy - worse than Unity. I think it would be great if Canonical would work with KDE and contribute to its development, because what was shown in that video looks very promising.

---

