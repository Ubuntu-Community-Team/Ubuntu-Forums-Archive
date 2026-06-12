---
title: "&quot;Show Desktop&quot;-indicator in Unity-Panel?"
date: 2011-03-11
forum: Desktop Environments
---

### Post by melodram on 2011-03-11
[COLOR=#000000][FONT=FreeSans, sans-serif][SIZE=2]in ubuntu 11.04 unity, i miss the icon to show the desktop with just one click (like in the gnome-panel).[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=FreeSans, sans-serif][SIZE=2]is there a possibility to get the "show desktop"-indicator?[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=FreeSans, sans-serif][SIZE=2]thx[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=FreeSans, sans-serif][SIZE=2][/SIZE][/FONT][/COLOR]

---

### Post by kerry_s on 2011-03-11
what i do is just use the workspaces & switch to an empty 1, unless your using all 4.

---

### Post by melodram on 2011-03-11
ok. but i just wonder why they forgot the "show desktop"-icon. it would make work faster and easer. it was always in the gnome panel.

---

### Post by kev77 on 2011-03-11
i personally think a "collapse all" button should be included. "show desktop" is a tad outdated

---

### Post by markba on 2011-04-03
You can use the shortcut <Super> + D. This collapses all windows. Using this again, it will expand everything.

But nevertheless, a visual clue or better a speedbutton or something would be better. This is/was available in the classic GNOME interface, so it should be included in Unity.

---

### Post by vivapaco on 2011-04-05
Or control-alt-D or whatever you have in Keyboard Shortcuts under Window Management -> Hide all normal windows and set focus to the desktop.

I'm sure it will be added soon, you can probably install screenlets or something like that and get one.

Does anybody know if how to do it from the terminal? If so you could make your own launcher and add that to the launch bar.

---

### Post by markba on 2011-04-05
> **vivapaco said:**
> Does anybody know if how to do it from the terminal? If so you could make your own launcher and add that to the launch bar.

This guy has a solution, based on terminal:
[https://bugs.launchpad.net/unity/+bug/681348/comments/30](https://bugs.launchpad.net/unity/+bug/681348/comments/30)

> For those like Consumology who need a button to show the desktop, here's a dirty and imperfect workaround , while we wait for the real thing (... in Oneiric):

1. Install xdotool (apt-get install xdotool) - this is a utility to fake keyboard/mouse input, window management, and more

2. Create a launcher, with wahtever name ("show desktop "should do the job!) with this command (this will fake the same as super+d on the keyboard): xdotool : xdotool key super+d super

3. Place this launcher on the Unity launcher bar.

It works... most of the time, with the caveat that you can't toggle quickly between desktop and windows/apps, since once you click on the launcher, you have to wait for the "glowing" effect to stop before you can reclick on it... Also, it may sometimes open the Ubuntu menu. Any improvement suggestion is welcomed.


---

### Post by jiapei100 on 2011-05-01
I've got the same confusion.
It looks Gnome-panel is much more professional than Unity. At least, it has the most important "show-desktop" button. !!

Unity seems to steal the idea from Apple?


Rgds
Pei

---

### Post by kerry_s on 2011-05-01
> **jiapei100 said:**
> I've got the same confusion.
It looks Gnome-panel is much more professional than Unity. At least, it has the most important "show-desktop" button. !!

Unity seems to steal the idea from Apple?


Rgds
Pei

you can add it. look here:
[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

---

### Post by jiapei100 on 2011-05-01
> **kerry_s said:**
> you can add it. look here:
[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)


Hi, thanks for your prompt reply.
However, unfortunately, my laptop seems to use an old video card, which doesn't support 3D. Therefore, I'm currently using Unity 2D. But still thank you, because I noticed that my "Alt+F2" doesn't work right at this moment. ^_^
Let me try to figure this out first.

By the way, why doesn't Unity defaultly afford a functionality as show-desktop? Is it intend to do so? Is there any advantage for the users' convenience by this kind of design? There must be some reasons to bypass "show-desktop"...

Thanks again.


Best Regards
Pei

---

### Post by funicorn on 2011-05-12
[SIZE=2]I don't understand why you guys debate for Ubuntu. I think missing the show-desktop button in the unity panel is a very stupid mistake. Yes I can use super+D to collapse all windows, so what ? I can also press [super] to run any app, whereas  does this make make unity-panel useless ?[/SIZE]

---

### Post by geazzy on 2011-05-13
> **kerry_s said:**
> you can add it. look here:
[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

useful tutorial :D

---

### Post by Zingam on 2011-05-17
I cannot! I don't have super key on the keyboard :D I love my 17 years old pre-Windows 95 IBM keyboard and I'm not replacing it with anything until it dies (and I bet it will outlive me).

A click button on the upper bar should be included!

A good design requires more than one input for certain things (for everything). Shortcuts only = bad design (mostly). Shortucts only interface is the best way to put off novice users!

---

### Post by Copper Bezel on 2011-05-17
Well, you could simply change the shortcut to something more suitable. It's in General Options -> Key Bindings in CompizConfig. It can also be set to an edge binding, which can potentially be useful.

Another option is to install and use xdotool. You can put this command as the exec line in a .desktop and add it to the Unity Launcher:

```
xdotool keydown Super_L key d keyup Super_L
```

---

### Post by markb69 on 2011-10-17
I created a simple Toggle Desktop indicator in Python based on the webupd8.org script. I just did for some fun hacking but I thought others might like it. Read the readme.txt file in the archive to install it.
[http://markbokil.com/downloads/show-desktop.tar.gz]("http://markbokil.com/downloads/show-desktop.tar.gz")


[IMG]http://markbokil.com/images/desktop-indicator.png[/IMG]

---

### Post by arunkp on 2011-11-22
The default show desktop key combination is alt-ctrl-d.
You can change it by opening compiz.
General options>'key bindings' tab>Show desktop.

---

### Post by einfeldt on 2012-05-27
> **kerry_s said:**
> you can add it. look here:
[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

Thanks, this worked for me very well.   :-)

---

### Post by satish_j on 2012-05-28
Have you tried using ubuntu-tweak??There is a setting in it that lets you have a 'show desktop' on launcher..

> **melodram said:**
> [COLOR=#000000][FONT=FreeSans, sans-serif][SIZE=2]in ubuntu 11.04 unity, i miss the icon to show the desktop with just one click (like in the gnome-panel).[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=FreeSans, sans-serif][SIZE=2]is there a possibility to get the "show desktop"-indicator?[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=FreeSans, sans-serif][SIZE=2]thx[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=FreeSans, sans-serif][SIZE=2][/SIZE][/FONT][/COLOR]

---

### Post by typhoon_tip on 2012-05-28
> **satish_j said:**
> Have you tried using ubuntu-tweak??There is a setting in it that lets you have a 'show desktop' on launcher..

Was about to write the same, good old Ubuntu Tweaks !!

It also has a option that let's you set active corners. I use my bottom-left corner as "Show desktop" command, and bottom-right corner as "Show windows" command, very very useful ! No even need to click, just decisively put your mouse in the right place :popcorn:

---

