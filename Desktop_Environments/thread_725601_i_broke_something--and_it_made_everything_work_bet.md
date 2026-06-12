---
title: "i broke something--and it made everything work better!!?"
date: 2008-03-15
forum: Desktop Environments
---

### Post by brnetonboy on 2008-03-15
I just installed Ubuntu 7.10 Gutsy Gibbon. I'm new to Linux, but not computers. So I know that usually when you break something, the system either stops working completely, or it works much worse. 

However, I experienced something more like in the movies where if a computer has an error it can become self-aware!

Ok, so I was messing around with Start-Up Manager trying to get it to display text or a theme or something, instead of just a black screen for like 20 seconds while booting. I was generically following these instructions:

[http://hacktivision.com/index.php?blog=2&title=how-to-customize-grub-in-ubuntu&more=1&c=1&tb=1&pb=1](http://hacktivision.com/index.php?blog=2&title=how-to-customize-grub-in-ubuntu&more=1&c=1&tb=1&pb=1)

and I was rebooting over and over and messing with the resolution--when suddenly after one boot, everything was different!

I saw a quick error message too quick to read, and then suddenly my mouse wasn't sluggish and jumpy! it moved cleanly and quickly across the screen. Also, all the icons are different from what they normally are. (See screenshot below.) For example, the question mark icon is now a life-saver. 

Furthermore, when I scroll my mouse, it switches to the other workspace--this was something I was trying to get my mouse to do. I was actually trying to get the thumb buttons to do it--but I was having no success, (see my *still unanswered* thread on that topic here: [http://ubuntuforums.org/showthread.php?t=724715](http://ubuntuforums.org/showthread.php?t=724715) shameless plug, haha) The point is now suddenly it works mostly the way I wanted.

Also I am getting a weird error message when trying to change some of the settings (like the mouse settings). I captured a screenshot with that error message for y'all to read, as well as to see what my icons look like now. It's attached, also here's a link:


[CENTER]
**Screenshot:**_ [http://image.bayimg.com/jajbhaabd.jpg]("http://image.bayimg.com/jajbhaabd.jpg")_
(If that doesn't work try: [http://bayimg.com/jajBHAaBd](http://bayimg.com/jajBHAaBd))
[/CENTER]


So what gives? Is my computer becoming self-aware? I'm assuming it somehow is loading into a "backup" desktop environment? What environment is this? Why is it so much better? I have three main concerns now:

1. Fix what went wrong so I can load up in normal mode again with the pretty Ubuntu colors and icons.
2. Find out what this other mode is that works so much better
3. Apply whatever it is that makes this other mode work so much better to my normal mode!
4. Make sure that my computer is not going to take over the world.

In that order!!

---

### Post by rainwalker on 2008-03-15
I'm not sure what happened, but it looks like you somehow got Compiz to work

---

### Post by brnetonboy on 2008-03-17
I was able to get a screenshot of the error. I still dont' know what's going on. Can anyone help me?

---

### Post by OllyNewport on 2008-03-17
I thought so, it looks like you have disabled something with your video card, and it has stopped Ubuntu from showing all the fancy snazzy stuff, so that's why it should run quicky.

---

### Post by rainwalker on 2008-03-17
> **OllyNewport said:**
> I thought so, it looks like you have disabled something with your video card, and it has stopped Ubuntu from showing all the fancy snazzy stuff, so that's why it should run quicky.

No, it means that something has been ENABLED. In this case, Compiz, because he has shadows around his windows. The Gnome Settings Daemon is what handles your theme settings, which is why things are gray and blocky

---

### Post by Jouke74 on 2008-03-18
Yep, you messed up your theme settings, and now you're getting the standard Gnome. It has nothing to do with Compiz (as this is the window manager). Go to Appearance in the preferences tab and change the theme into something you like (you also have the customize button). If this is working better for you then choose default Gnome and Gnome Icons. 

Note I cannot gurantee that you keep this speed. :lolflag:

You might also want to rebuild your Icon cache, which will speed things up, but I forgot the command to do that manually.

---

### Post by rainwalker on 2008-03-18
Also, you could try running the command ```
gnome-settings-daemon
``` from the terminal and see what happens

---

### Post by brnetonboy on 2008-03-20
So whatever I broke apparently fixed itself--I'm not getting anymore errors and all my windows are in the default Ubuntu orange again. I honestly didn't change anything! 

I tried ```
gnome-settings-daemon
``` and it spit this back to me: ```

** ERROR **: You can only run one xsettings manager at a time; exiting

aborting...
Aborted (core dumped)
``` which I guess makes sense--the error I got before was because xsettings wasn't working. Now that it fixed itself, it is running again, so I can't run it again.

I don't know what xsettings is, or why that would cause me to go into Gnome instead of Ubuntu. I don't really understand the difference there anyway. I thought that my entire OS was Ubuntu, but that I had a few GUI choices, including Konqueror and Gnome... 

Because I'd like to switch to using Gnome if that's what it was, since everything was markedly faster. I don't mind having blue windows and older looking icons. 

How do I switch to Gnome? (or turn off the Ubuntu skin or whatever happened?) And the icon thing sounds useful--I'll try to look up how to do it. Thanks!

---

### Post by mcduck on 2008-03-20
> **brnetonboy said:**
> So whatever I broke apparently fixed itself--I'm not getting anymore errors and all my windows are in the default Ubuntu orange again. I honestly didn't change anything! 

I tried ```
gnome-settings-daemon
``` and it spit this back to me: ```

** ERROR **: You can only run one xsettings manager at a time; exiting

aborting...
Aborted (core dumped)
``` which I guess makes sense--the error I got before was because xsettings wasn't working. Now that it fixed itself, it is running again, so I can't run it again.

I don't know what xsettings is, or why that would cause me to go into Gnome instead of Ubuntu. I don't really understand the difference there anyway. I thought that my entire OS was Ubuntu, but that I had a few GUI choices, including Konqueror and Gnome... 

Because I'd like to switch to using Gnome if that's what it was, since everything was markedly faster. I don't mind having blue windows and older looking icons. 

How do I switch to Gnome? (or turn off the Ubuntu skin or whatever happened?) And the icon thing sounds useful--I'll try to look up how to do it. Thanks!
You _are_ already using Gnome. That's the default desktop environment in Ubuntu.

Things working better is because you got Compiz running (easy to tell from the window shadows) which means your graphics card is doing part of the work.

Blue/grey theme is just Gnome's old default, and using that instead of whatever theme you normally use is because of your problem with gnome-settings-daemon. When the daemon works correctly it loads whatever GTK theme you are using, when it fails to work you get the ugly default theme instead.

---

