---
title: "No window title bar after expanding past a certain size or maximize"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by Ryan Marcus on 2007-04-20
I'm having a rather interesting problem with the new desktop effects in Feisty.

When I have a normal, non-maximized window, for example, a terminal, everything is fine. But once I maximize a window or expand it to the right past a certain, static point, the title bar (and buttons) disappear.

Here is an example with Firefox.

Everything is fine when the window is only this big:
[img]http://marcusfamily.info/~ryan/ubuntu/Fine.png[/img]

But when I expand the window a little to the right:
[img]http://marcusfamily.info/~ryan/ubuntu/Notfine.png[/img]

---

### Post by magomago on 2007-04-20
I have the EXACT same problem...

but I don't have to be maximized!

I just upgraded to feisty from edgey

once it turns on, I lose the borders and all my windows become "frozen" since there is nowhere to grab or drag them...

---

### Post by jiminycricket on 2007-04-20
I had a similar problem.  Your video card might not have enough memory, so try this:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/91850/comments/4](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/91850/comments/4)

You can create /etc/drirc file with the following contents:
<option name="allow_large_textures" value="2" />

However, it's most probable your graphics card does not enough video RAM to handle the multiple large textures anyway.

---

### Post by Ryan Marcus on 2007-04-21
That did not seem to work for me, even after restarting X.

---

### Post by maddentim on 2007-04-24
almost the same thing here.  I do not even get the buttons on the bottom panel for the windows that are open.  i was messing around with beryl and xgl.  one time i had a window get really big and then it went fully heywire shortly thereafter.  I can even switch between the windows.  This is not good.  I may need to go back to 6.10 for a few weeks.

---

### Post by maddentim on 2007-04-24
oh, and if i log in failsafe gnome, it is fine...  so something is loading that is broken.  weird.

---

### Post by sarracenia88 on 2007-04-24
If your windows get stuck like this, you can always hold down ALT and drag it with your mouse.

---

### Post by Cervantez on 2007-04-24
I've never heard of the title bars being there but disappearing when the windows are maximized, but the title bars disappearing is a common problem. One main reason is that your **window manager is incompatible with your window decorator**. For example, if you have both Compiz and Beryl installed, or Beryl installed on Feisty with Compiz there by default, when you run Beryl the first time, it makes Emerald your window decorator. However, Compiz is only compatible with Metacity. If that's your problem, then you can go into Beryl Manager > Window Decorator > Heliodor and choose that as your window decorator. Hope that helps;)

---

### Post by Baasha on 2007-04-24
It is not a video card problem nor is it a compatibility problem with a window decorator.  I have a bare bones system with none of that extra stuff loaded.  Everything worked just fine until I upgraded to Feisty.  Even Feisty worked fine for the first two days and then it went downhill.  Windows are frozen, no title bar, no tabs showing in the status bar at the bottom of the screen.  If you have more than one application running the only way to switch is to keep closing down applications until you get to the one you want.  This is probably a corrupted configuration file somewhere, but I don't know where to look or how to fix it.  I hope someone who knows what is going on will come up with a fix soon.  It is a real bummer having to work with one application at a time in a half-sized window.  And BTW you can't drag windows around by holding down ALT either, at least not on my system.

---

### Post by engineer on 2007-04-25
i also had this problem and discussed it [here]("http://ubuntuforums.org/showthread.php?t=279685").

i have an old ati graphics chip. the memory size wasn't detected correctly, so i had to set it manually in xorg.conf.

now it works.

---

### Post by c@rc@ss on 2007-04-27
Is the window manager that is not working.

To use it type in console   metacity.

This is how I fixed it.

System-->Preferences-->Desktop Effects

Click on Enable effects.

Wait
crl-alt-BkSp

I think that it is a bug that when you click on enable effects it actually disables it.

if that doesn't work try this thread
[http://ubuntuforums.org/showthread.php?t=406225](http://ubuntuforums.org/showthread.php?t=406225)

---

### Post by jpatton on 2007-04-27
> **maddentim said:**
> almost the same thing here.  I do not even get the buttons on the bottom panel for the windows that are open.  i was messing around with beryl and xgl.  one time i had a window get really big and then it went fully heywire shortly thereafter.  I can even switch between the windows.  This is not good.  I may need to go back to 6.10 for a few weeks.

It may be a combination of things, beryl and a not so trendy video card? My laptop has a decent card for doing work, but nothing what you need for today's games and such which is fine by me.  

I know on my laptop I experienced the same problem after I unloaded all the Beryl and Emerald stuff. The computer would come up with no "Windows" around the applications.

Open a terminal and type gdm I believe, if the Windows come back then you can do what I did to resolve my problem. I believe what I did to resolve this problem was after making sure that everything related to bery and emerald were gone, starting up a terminal typing gdm, buttons came back, going into system > preferences > sessions and clicking save session, then unchecking automatically save sessions.

When I rebooted, which I doubt I needed to do, everything was back to normal. I also think the unchecking autosave was not needed either.

Not sure if this will even help, but I figured I'd drop my 2cents!

---

### Post by john.n on 2007-05-07
I had same problem, no bars on screen. Changed the .conf file as it says above, that didnt work Changed the "Window Decorator" in beryl to GTK, things all fixed

---

### Post by timzak on 2007-05-07
I'm having the same problem too (find my post in this forum) but it is directly related to enabling Desktop Effects.    The problem goes away when I disable Desktop Effects.  Prior to this problem, I had other problems with enabling Desktop Effects, so I'm disabling them until the situation gets resolved.

---

