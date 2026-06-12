---
title: "Transparent Aterm not so transparent"
date: 2006-11-17
forum: Desktop Environments
---

### Post by Cal on 2006-11-17
See bottom for solution:

I'm having trouble getting X to follow my .Xdefaults file.  I always set up a.Xdefaults file in my /home/user/ directory to make aterm transparent.  I have the following in .Xdefaults

```
aterm*loginShell:true
aterm*transparent:true
aterm*shading:60
aterm*background:Black
aterm*foreground:White
aterm*scrollBar:true
aterm*scrollBar_right:true
aterm*transpscrollbar:true
```

It has always worked before but now I get a black background in the terminal.  Thanks for any help.  I have added a screen shot.

[IMG]http://www.hcfolds.com/flux/desktop.jpg[/IMG]


EDIT:  I found someone in the forums with the same problem who tried "xrdb -merge .Xdefaults"   it didn't work for me.

EDIT2: Gnome-Terminal does the same thing as Aterm in transparent mode.

EDIT3: I tried to go around the problem by running xcompmgr .  This changed my entire desktop black (icons and menus were visible, only the backdrop was back.  are there two backgrounds that fluxbox and X can't agree on...  a black one that aterm and xcommgr are using and a picture that fluxbox is using??




SOLUTION:  fbsetbg couldn't find feh, so it fell back on Gnome's background setter which didn't play nice with fluxbox and xcompmgr.  I installed feh ```
sudo apt-get install feh
``` which fbsetbg automatically chooses by default and set a new background.  Now everything works fake and real transparent windows.


BTW:  Even without a 3d card my sis graphics Laptop does really well with real X transparency on edgy.  It was way to slow on dapper.


Thanks, Cal
P.S.  I'm not sure if I should leave this up...  I solved my own problem, but it might save someone else a few minutes if they find themselves in my situation.

---

