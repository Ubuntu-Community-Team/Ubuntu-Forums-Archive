---
title: "[SOLVED] can some one set me on the right path (flux and compiz)"
date: 2008-08-09
forum: Desktop Environments
---

### Post by drawhole on 2008-08-09
Ok so fist i am willing to learn to program again in a new language to accoplish this..

what i would like to do is smiple well you'd think it should be. I would like to run flux but i don't want to loose the eye candy from compiz. i've been doing a lot of reading on this... every thing says the same thing ... both are window managers ... and scince you can only run one at a time you can't do it ... now i don't belive in can't ... it's won't but i'm hoping i can get some people together hopefully some with more knolege than me ... so i can get pointers and such ... i know the basics of programing but i'd need to learn it in much more detail if i am going to pull this off....

so it's smiple i have a few slotions that i've thought up ... any more are welcome ...

first to program a plugin for compiz which will give me the fluxbox right click menu while on desktop area .....

or as was said by some one else recompile nauticlus to do it instead ...

or the best thing yet but also probally the hardest merging compiz with fluxbox --- this would be my untimite goal .... but there is no way i can do it with the knowlage i have ...

and if i do get it working i'd be more than happy to release the soure code ... so it could be improved and hopefully be added into the repo ... there is a lot of people that want this .... if anyone has any links or what not to get me going that would be great ...

or maybe some how converiting flux  into a desktop manager .

Thanx everyone

---

### Post by p_quarles on 2008-08-09
Adding plugins to make Compiz behave more or less like Fluxbox might make sense, but merging the projects would strike a lot of people as kind of a bizarre goal. Adding the minimalist panel and the right- and middle-click menus to Compiz would be easy. Any more than that, though, and you would be changing the underlying basis of both window managers to the extent that you would have an entirely new project. 

Anyway, the place to start is with the source code. Both projects are coded in C, I believe.

---

### Post by x1a4 on 2008-08-09
Hi,

Run a FluxBox Session, than switch window managers.

Good luck.

---

### Post by p_quarles on 2008-08-09
> **x1a4 said:**
> Hi,

Run a FluxBox Session, than switch window managers.

Good luck.
I fail to see the point of that.

---

### Post by x1a4 on 2008-08-09
That's obvious.

---

### Post by p_quarles on 2008-08-09
> **x1a4 said:**
> That's obvious.
You want to explain why anyone would want to do that?

---

### Post by drawhole on 2008-08-09
> **x1a4 said:**
> Hi,

Run a FluxBox Session, than switch window managers.

Good luck.

ya i've tried this it dose not show up in the list --- is there a quick fix for the problem? 

i'd assume you'd need more infoemation ... i'm not sure sure where to find all the log so a little direction would be nice thanx.

---

### Post by damis648 on 2008-08-09
> **drawhole said:**
> ya i've tried this it dose not show up in the list --- is there a quick fix for the problem? 

i'd assume you'd need more infoemation ... i'm not sure sure where to find all the log so a little direction would be nice thanx.

After starting the fluxbox session, try opening a run dialog and enter:
```
compiz --replace
```
and see if this gets you what you want.

---

### Post by yabbadabbadont on 2008-08-09
Fluxbox is a window manager, not a desktop environment.  (it just happens to have a toolbar)  Switching window managers simply closes Fluxbox and launches compiz.  Hence, it is pointless.  Just start compiz by itself in the first place.

---

### Post by drawhole on 2008-08-09
> **p_quarles said:**
> You want to explain why anyone would want to do that?


ya i can ... in my searches i've found a lot of people that like the usabilitly of fluxbox but don't want to leave behind compiz .... compiz it nice to look at but i don't like the way gnome hanldes the right click on the desktop ... and kde no offance intended just dose not seem to run as nicely  ..... i really what i would like to do in full it this ....... i would like and others ... to be able to run fluxbox ... with all it's nice features .... windows in windows and such but not loose that eye cany in doing so ... I realize that this is going aganst what fluxbox is all about, but i just don't want to switch over and not have my cube snow and such ... and as much as i like gnome making menus for it is a pain for me and others that install and remove programs on a daily basis, fluxbox's right click menu is what i want really ... having every thing else would just be a great bonus  ... 

this help you understand?

---

### Post by drawhole on 2008-08-09
ok i've tried for hmmm 1 week now to get compiz to run in flux .... every time i do i get ... i'll have to look up the error by doing it again i'll post that in a sec. 


but basicly it tells me there is already a window manager running and it quits out as you can only have one running at a time.

---

### Post by drawhole on 2008-08-09
> **damis648 said:**
> After starting the fluxbox session, try opening a run dialog and enter:
```
compiz --replace
```
and see if this gets you what you want.

so on doing this i got 

Checking for Xgl: not present. 
Detected PCI ID for VGA: 04:00.0 0300: 10de:0393 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Another window manager is already running on screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: Screen 0 on display ":0.0" already has a window manager


i ran it as my usr and as root same message both times hmm Xgl do i need this maybe .... compiz works fine in gnome thou

---

### Post by yabbadabbadont on 2008-08-09
I guess no one bothers to read replies...  ;)

I've already stated that you can't run fluxbox and compiz at the same time.  They are both window managers and, as your error message clearly shows, there can be only one.  :D

---

### Post by p_quarles on 2008-08-09
> **drawhole said:**
> ya i can ... in my searches i've found a lot of people that like the usabilitly of fluxbox but don't want to leave behind compiz .... compiz it nice to look at but i don't like the way gnome hanldes the right click on the desktop ... and kde no offance intended just dose not seem to run as nicely  ..... i really what i would like to do in full it this ....... i would like and others ... to be able to run fluxbox ... with all it's nice features .... windows in windows and such but not loose that eye cany in doing so ... I realize that this is going aganst what fluxbox is all about, but i just don't want to switch over and not have my cube snow and such ... and as much as i like gnome making menus for it is a pain for me and others that install and remove programs on a daily basis, fluxbox's right click menu is what i want really ... having every thing else would just be a great bonus  ... 

this help you understand?
Okay, you seem not to understand what these two applications do: they are both window managers. You cannot use both of them to manage the same windows. The only way you could run both simultaneously would be with two instances of X, or via virtualization. With some creativity, I imagine you could convince your system to run different programs under the auspices of different window managers, though this would be a great deal of work with very little payoff, and wouldn't achieve the effects you are looking for. 

The bottom line is that a window cannot be created and controlled simultaneously by two different window management applications. That is what you are asking for, and it simply doesn't work. It is equivalent to trying to run Vista and Ubuntu at the same time, on the same computer, without virtualization.

The best you can do (and as you said, this would require coding) is to add the desired features to one or the other window managers.

---

### Post by Anzan on 2008-08-09
Fluxbox is so fast that turning a cube is meaningless. Menus and title bars can have transparency. If you want your windows to jiggle just log into Gnome for a few minutes and then log back into Fluxbox.

I do agree that the root menu is incredible. The various *boxes and Xfce have it. Until Gnome or KDE do as well, they are much less useable despite their other virtues..

---

### Post by yabbadabbadont on 2008-08-09
If the main thing you miss from flux is the menu, then you could run a standalone one instead.  Something like dmenu perhaps?

[http://www.suckless.org/programs/dmenu.html](http://www.suckless.org/programs/dmenu.html)

Edit: it is provided by dwm-tools in Ubuntu.  There are also 9menu and deskmenu in the repositories.

---

### Post by drawhole on 2008-08-09
> **yabbadabbadont said:**
> I guess no one bothers to read replies...  ;)

I've already stated that you can't run fluxbox and compiz at the same time.  They are both window managers and, as your error message clearly shows, there can be only one.  :D


yes i am aware ... if you read my origanal post you'd see i new that hence forth why i wanted to do what i wanted to do. 



it's just people said to try it so i did ... if there in an easy way to do it i'm going to take that route which is why i tried again.

---

### Post by drawhole on 2008-08-09
> **yabbadabbadont said:**
> If the main thing you miss from flux is the menu, then you could run a standalone one instead.  Something like dmenu perhaps?

[http://www.suckless.org/programs/dmenu.html](http://www.suckless.org/programs/dmenu.html)

Edit: it is provided by dwm-tools in Ubuntu.  There are also 9menu and deskmenu in the repositories.



hmmm well this mite do it thanx i'll play with this for now and see if i can get it to work the way i want .... thanx

---

### Post by yabbadabbadont on 2008-08-09
> **drawhole said:**
> yes i am aware ... if you read my origanal post you'd see i new that hence forth why i wanted to do what i wanted to do. 



it's just people said to try it so i did ... if there in an easy way to do it i'm going to take that route which is why i tried again.

Sorry, I was actually replying to the others in the thread that were telling you to do that...  I should have made that clear.

The reply about the alternate menu programs was directed at you however.  :D

---

### Post by drawhole on 2008-08-09
> **yabbadabbadont said:**
> Sorry, I was actually replying to the others in the thread that were telling you to do that...  I should have made that clear.

The reply about the alternate menu programs was directed at you however.  :D

sry no hard feelings

---

### Post by drawhole on 2008-08-09
well hmm if Xfce can have the root menu like flux then it would most likely be easiest to run, Xfce with compiz. correct me if i'm wrong but Xfce is a desktop manager right so compiz could be used in conjunction with it right?

and i would be able to lets say use any thing i'm currently using 

and it would be able to mount my 250 gb usb NTFS drive and write to it ... with little headache like ok i'm all for getting this to work but the less i have to do the better as i don't want it to take 4 months for me to get my system "right" it it has to fine i would rather be using GNU/Linux over win anyway ... only reason i have windows is because of games .... GNU/Linux dose everything else better once it works.

guess i should have searched this first -- sry

---

### Post by yabbadabbadont on 2008-08-09
xfwm has it's own compositor, but yes, you can use compiz with xfce.  I'm not sure if you will still get the root menu if you do though...  I've never tried it, and haven't read about anyone else's experience doing it.

---

### Post by drawhole on 2008-08-09
well i'm going to try it just dling Xubuntu now so i'll know in however long it takes to dl and install i can let you know if you want.

i know i could just use the repo but i've got a lot of junk now... better to just fresh install and I have not looked much at Xubuntu so ... now it time.

---

### Post by drawhole on 2008-08-09
and yes i do believe this is the way to go works nicely and the menu editor in Xfce is better than i would have expected thanx everyone for your help.

---

