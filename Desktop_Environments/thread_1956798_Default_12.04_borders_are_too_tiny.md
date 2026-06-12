---
title: "Default 12.04 borders are too tiny"
date: 2012-04-11
forum: Desktop Environments
---

### Post by projectshave on 2012-04-11
I loaded a fresh copy of 12.04 into VMware. I can't grab the edge of any window to expand the size. The border appears to be 1 pixel wide. Every time I click I miss. I did grab it once by clicking a million times. I also don't like the pop-up scroll bars. I usually have to wave my mouse around to get it to pop out. Finally, I tried to hide the launcher bar, but then it wouldn't pop out when I moved my mouse to the edge. Is this behavior an artifact of VMware? Or do other people have this problem in a native install? 

Also, is there a theme that will give me thicker boarders and a normal scroll bar? 

Thanks.

---

### Post by arpanaut on 2012-04-11
```
sudo apt-get remove overlay-scrollbar
```will get the normal scrolling back

alt +middle mouse drag will resize the window

press and hold the Super(win) key and an overlay of all the shortcut keys will show up.

Also right click the desktop and choose change background then the behavior tab move the scroll bar to the right to increase the sensitivity of the launcher reveal.
edit: sometimes you gotta give it a little nudge not just move the mouse/cursor there, i.e. move the mouse there with a little velocity.

HTH

---

### Post by projectshave on 2012-04-11
Thank you for your help. Everything you wrote works except that last part. I turned on auto-hide and kept the reveal location on the left. I slammed my mouse pointer into the left side repeatedly, but it didn't work. The part where it says "Reveal Sensitivity  Low High" is weird. There's no way to change the sensitivity. Frankly, I don't know what that line means. 

My panel looks like [this]("http://3.bp.blogspot.com/-iT6OBC1izWk/T1R-W_5ZiVI/AAAAAAAAEb0/Ojg8RzDgiYg/s1600/Screenshot+at+2012-03-05+16:05:57.png"). 

> **arpanaut said:**
> 
Also right click the desktop and choose change background then the behavior tab move the scroll bar to the right to increase the sensitivity of the launcher reveal.
edit: sometimes you gotta give it a little nudge not just move the mouse/cursor there, i.e. move the mouse there with a little velocity.


---

### Post by arpanaut on 2012-04-12
Are you in a fully updated 12.04?
Have you updated the image in your VM?

That does not look like what I have in a fully installed & updated PP.

---

### Post by projectshave on 2012-04-12
I was only using the 12.04 ISO. I fully updated my system (400MB of stuff!) and I still don't have your screen! Now I have the sensitivity slider, but I lost the "Reveal Location" part. Anyway, I turned the sensitivity all the way to high and slammed my mouse into the left border (and top-left corner), but it still doesn't work. I even reduced the screen size so I could explicitly see the screen border, but still no luck. 

I've attached a screenshot. Strange, ain't it?

---

### Post by mc4man on 2012-04-13
The reveal is not based on 'hitting' the left edge, it's really a 2 part deal - go to left edge, then push against.
So the setting is the 'pressure' of the push

By default it's set to 20, to try a very low value (less pressure) then try this in terminal

```
gconftool-2 -s -t int /apps/compiz-1/plugins/unityshell/screen0/options/reveal_pressure 5
```

If that happens to make it too easy to reveal then raise a bit, like 10

The lowest value is 1

---

### Post by projectshave on 2012-04-13
I tried pushing, still no luck. I changed the reveal_pressure setting to 1. Still doesn't work. Take a look at the screenshot of my panel. You'll notice it's missing the "reveal location" section. Any idea what might cause that? This is a clean install and update. I didn't make any changes.

---

### Post by nicklas898haohao on 2012-04-13
I even reduced the screen size so I could explicitly see the screen border, but still no luck. [IMG]http://**************************/g.gif[/IMG]

---

### Post by noisygecko on 2012-10-30
This is so crazy!  I can't believe that Ubuntu 12.04 is released with such a horrible bug (sorry, "feature"). It is so hard to just resize a window!

And why do people keep pointing out that you can resize by trying to figure out how to get the weird scrollbar to show up and grabbing that.  And it only works horizontally, anyway.

The crazy thing is that I can't even figure out a way to make the border bigger after searching for an hour and trying all sorts of stupid suggestions like gnome-tweak-tool and changing themes.

I am fine with Unity, but the microscopic border is driving me crazy.

---

