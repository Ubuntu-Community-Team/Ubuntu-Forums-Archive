---
title: "Gnome panel hides window titlebar"
date: 2011-03-25
forum: Desktop Environments
---

### Post by hashcode on 2011-03-25
I moved my laptop screen "below" external screen (was using left/right config before). There's a little problem.
  When my gnome panel is on top of laptop screen, all windows I  maximize "drawn" under top gnome panel. Therefore, I cannot see window  titlebar.
  I tried suggested fixes as metacity --replace and so on, but none worked. When I move my taskbar to bottom it works just fine.
  Any ideas? Thank you.


On this picture you can see, that panel hides window titlebar:
[http://img828.imageshack.us/f/hides.png/](http://img828.imageshack.us/f/hides.png/)

On this picture you can see, that it also hides icons of skype and eclipse:
[http://img189.imageshack.us/f/alsoicons.png/](http://img189.imageshack.us/f/alsoicons.png/)

---

### Post by hashcode on 2011-03-29
bump ...

---

### Post by irv on 2011-03-29
Are you using a Mac? or just the Macbuntu theme? If you are using the theme, try changing it and see what happens.

---

### Post by hashcode on 2011-03-29
It just a theme and it's wrong with any theme (like default ambiance :))

---

### Post by irv on 2011-03-29
> **hashcode said:**
> It just a theme and it's wrong with any theme (like default ambiance :))

I am wondering if it is your video card. If this is a new install and this has done this from the install it might be a driver issue.
When you did the install did you load any proprietary drivers for your video? If not you might have too. Go to System> Administration> Additional Drivers and see if it finds any for your video card. 

May I suggest going to your Control panel "CP" on this forum and adding information on your hardware. You can add it to your signature. It help others see what you have and what OS and version you are using.

---

### Post by hashcode on 2011-03-30
Thanks, but I am using same nvidia propiertary drivers since begining :)

---

### Post by Copper Bezel on 2011-03-30
Since your desktop is vertically expanded, it's all one workspace - the virtual desktop is a rectangle, and you've probably noticed that you can move your mouse cursor into that black space where your lower monitor ends, right off the screen edge. As far as Gnome Panel knows, it's floating in the middle of the screen, which seems to be confusing its ability to redefine the size of the workspace for maximized windows.

This is just a work-around, but would you consider setting it to auto-hide? If you're willing to try it, you can set it in the panel Properties menu and fine-tune the auto-hide settings in gconf-editor, under /apps/panel/global.

---

### Post by hashcode on 2011-03-30
Hi, I tried that and I found it too annoying :(

Only acceptable solution is to palce gnome panel to the bottom of lower screen, but I lke it more on top :/

---

### Post by Copper Bezel on 2011-03-30
Sorry. = ( I can reproduce the problem on my rig, but I can't fix it.

---

### Post by hashcode on 2011-03-30
No problem, maybe someone else can :)

---

### Post by Krytarik on 2011-03-30
I couldn't find a fix or workaround for that issue so far, neither by tweaking Compiz' options nor those of gnome-panel, and I searched really hard. ](*,)

But I finally found a bug report regarding that, it is quite new, and I suggest to enlist there:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/707346](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/707346)

Here is another one, in the Gnome bug tracker:
[https://bugzilla.gnome.org/show_bug.cgi?id=616217](https://bugzilla.gnome.org/show_bug.cgi?id=616217)

Greetings.

---

### Post by hashcode on 2011-03-31
Hi thank you, but what am I supposed to do with bug report? I don't want to be untahantkful, but this just confirms my problem, doesn't solve :( 

I am starting to be pesimistic now :(

---

### Post by irv on 2011-03-31
The thing about bug reports is someone is now aware of the problem and it will be looked into and maybe fixed in the next update or release. One just has to wait. I know that doesn't sound like a good answer, but things just sometimes move slowly. 
I had a problem with a HP utility one time but it got fix with the next release of the software.

---

### Post by hashcode on 2011-04-01
Okay thank you guys, I guess then we'll see in next ubuntu, maybe with Unity it's gonna be completely different:)

---

### Post by Copper Bezel on 2011-04-01
Actually, yes, Unity uses Compiz to define the boundaries for maximized windows, rather than having Gnome Panel displace them, so at the very least, it *should* work fine in Unity. = )

---

### Post by triple.eh on 2012-04-15
I realize this post is somewhat dated, but I finally figured out how to "fix" this way too long after being frustrated by the same issue so I wanted to share the information.

It is as simple as a configuration change using CompizConfig Settings Manager.

Open up the Compiz settings manager and click "Window Management" then select "Window Rules" and add

```
class=Gnome-panel & type=DOCK
```

to the "Below" text box... then you're done!

You could probably leave out "type=DOCK"; the code shown above worked well for me and my maximized windows no longer have their title bar hidden by the panel on the monitor below the other.  The window's title bar does hide the panel though, but I can live with that since I can just un-maximize to get the panel back.

---

### Post by irv on 2012-04-15
> **triple.eh said:**
> I realize this post is somewhat dated, but I finally figured out how to "fix" this way too long after being frustrated by the same issue so I wanted to share the information.

It is as simple as a configuration change using CompizConfig Settings Manager.

Open up the Compiz settings manager and click "Window Management" then select "Window Rules" and add

```
class=Gnome-panel & type=DOCK
```

to the "Below" text box... then you're done!

You could probably leave out "type=DOCK"; the code shown above worked well for me and my maximized windows no longer have their title bar hidden by the panel on the monitor below the other.  The window's title bar does hide the panel though, but I can live with that since I can just un-maximize to get the panel back.

Thanks for posting the fix

---

### Post by prorokjchs on 2013-02-03
I had the same problem and I was really annoyed by it. After reading this fix I have found even better and simpler solution:

Open up the "Compiz settings manager" and enable "Place Windows" plugin (part of the "compiz-plugins-default" package), click on it to go to its preferences and then in "Placement Mode" select menu chose "Centered".

Since now every new window will be centered, and the problem of default (0,0) coordinated will be no more :D

I hope it will be helpful to everybody who has this annoying problem ;)

---

