---
title: "Using Synergy with Unity"
date: 2011-04-13
forum: Desktop Environments
---

### Post by Apex9 on 2011-04-13
I use Synergy to connect my Windows7 laptop and my Ubuntu machine. I recently upgraded to 11.04 to try out Unity and noticed that when I use Synergy and set it to move the cursor over to the Windows machine when your mouse exits the left side of the Ubuntu screen, it's no longer possible to unhide Unity's left panel via the mouse.

I haven't spent much time, but at first glance it doesn't seem that there's an easy way to initiate this menu via mouse when you're using the left side of your screen for Synergy.

And anyone else think that the delay time for the menu to unhide is a little bit too long?

---

### Post by xOrphenochx on 2011-04-16
I was showing my coworker this problem, the trick is to aim for the corner of the screen, and it'll pop up.

---

### Post by Azzmodan on 2011-04-23
I had the same issue, but since I didn't like moving to the top left all the time I decided to just disable the "autohide" dodge thing it did.

I installed the "Compiz configuration settings manager" and then after starting ccsm I was able to change the Unity launcher hide setting from the default "dodge" to "never".

---

### Post by andrewmv on 2011-05-02
I'm also having this issue.  Mousing to the top left corner of the screen does seem to work in lieu of "pushing the left edge", but this is actually a lot *more* mousing to do than simply clicking on the old Gnome style taskbar.

You can also turn on scroll lock on your keyboard to prevent synergy from switching screens.  This is really only practical if you switch screens rarely, though.

I like the concept of the new Unity launcher, and would like to spend some time getting used to it, but not being able to move it to the right side of the screen makes it impractical.

I'm considering physically swapping my monitors, but in the meantime I'm just logging in using the "Ubuntu Classic" mode.

---

### Post by andrewmv on 2011-05-06
After playing with this a bit, I found a workaround that's generally pretty usable.  Setup your synergy.conf so only the bottom half of the left edge of the screen is "hot".  This way you can roll the cursor off the bottom half of the left edge of the screen, and "push" the top half of the left edge of the screen to cue the launcher.

This isn't ideal, but seems to be pretty usable, even when doing lots of screen switching, and I'm already finding I'm starting to like Unity now that the launcher isn't conflicting with Synergy.

Just put something like the following in your synergy.conf:

```
section: links
	windows:
		right	= ubuntu
	ubuntu:
		left(50,100)= windows(50,100)
end
```

---

