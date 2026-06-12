---
title: "Menu Editing in Ubuntu"
date: 2005-12-07
forum: Desktop Environments
---

### Post by Catsworth on 2005-12-07
Hi Guys,

I'm a total n00b to Ubuntu, and a relative n00b to Linux (I installed SuSE 10.0, played with it for a few days, decided I didn't like it, and then installed Ubuntu).

So far I've managed to sort out a couple of niggly little problems without too much hassle (for example, the fact that the installation didn't add me to the sudoers list so I had to edit it manually) but I've hit a brick wall now and I'm hoping someone can help me out.

I'd like to be able to edit the menus within Ubuntu, I've installed some software (called menu editor) that allows me to edit some of the menus but it doesn't quite do what I need it to do.

I can add things to one of the existing sub-menus (say, 'Applications' -> 'System Tools' -> {My New Entry Here} ) but I can't add/edit any of the top level menus (for example, I can't add 'Applications' -> {My New Entry Here} ).

Am I missing something really obvious?  If there's a nice graphical way of doing it then that's fine, if I need to delve around in the config files somewhere then that's ok too.  I'd just like to be able to set my menus up the way that I want them set up.

Thanks,

*Cats*

---

### Post by aysiu on 2005-12-07
I don't think there's an easy way to do what you're talking about. There are many things I love about Gnome, but for things like this, KDE is way ahead of Gnome.

---

### Post by Catsworth on 2005-12-07
That's what I was afraid of :( 

It doesn't need to be an "easy" way, any way would be nice.....

---

### Post by Catsworth on 2005-12-08
Don't mean to be pushy on this guys, but anybody got any ideas on how I can accomplish what I want to?

Or am I going to have to uninstall Ubuntu and try something else?

---

### Post by landotter on 2005-12-08
[quote=Catsworth]

Or am I going to have to uninstall Ubuntu and try something else?[/quote]

Basing your decision on whether to use a distro or not on the ability to edit a menu is pretty bone headed if you ask me. ;) :P 

You do know that pressing alt + f2 gives a run dialog where you can simply type the name of the prgam you want to run and press enter? It tab completes.

---

### Post by DirtDawg on 2005-12-08
No I agree this is a real problem. With Warty, the user could use the RMB on any menu and change the icons/programs, etc, etc. But for whatever reason, the developers trashed this small, extremely usefull and endearing feature. I mean, why?

---

### Post by Laestrygo on 2005-12-08
What you are probably looking for can be found here:[http://www.gnomefiles.org/app.php?soft_id=1183](http://www.gnomefiles.org/app.php?soft_id=1183)

download the package and

```
sudo dpkg -i alacarte_0.8-0ubuntu1_all.deb
```

---

### Post by neighborlee on 2005-12-08
[QUOTE=DirtDawg]No I agree this is a real problem. With Warty, the user could use the RMB on any menu and change the icons/programs, etc, etc. But for whatever reason, the developers trashed this small, extremely usefull and endearing feature. I mean, why?[/QUOTE]

That is odd..does anyone know if this was done in d evelopers dyes to remove duplicate means of achieving editing ?...I could see it only if it really   removed duplicate features but not if you can't alter a main menu item..

I also am curious why did gnome developes choose not to include a menu editor and instead use this option where you just check/uncheck the item ?? ( sure simplicity rules but at the expense of baSic functionality..and I wonder if they asked userbase before deciding this was a good idea ?)

does kde come with a decent menu editor or do they too rely on distro vendors to enable such functionality ?

cheers
nl

---

### Post by CPUFreak91 on 2005-12-08
[QUOTE=Catsworth]Hi Guys,

I'm a total n00b to Ubuntu, and a relative n00b to Linux (I installed SuSE 10.0, played with it for a few days, decided I didn't like it, and then installed Ubuntu).

So far I've managed to sort out a couple of niggly little problems without too much hassle (for example, the fact that the installation didn't add me to the sudoers list so I had to edit it manually) but I've hit a brick wall now and I'm hoping someone can help me out.
[/QUOTE]

That's not too n00b. Actually you're doing pretty good to install both OSes already.

> Am I missing something really obvious?  If there's a nice graphical way of doing it then that's fine, if I need to delve around in the config files somewhere then that's ok too.  I'd just like to be able to set my menus up the way that I want them set up.

Thanks,

*Cats*

Have you tried right clicking on the Applications > And then Edit Menus?
Then clicking on the Menu you want to add another menu to and clicking "New Menu"?

You must then place a check mark on the new menu in order to see it when you click Applications > Wherever > Your Menu

---

### Post by Catsworth on 2005-12-09
[QUOTE=landotter]Basing your decision on whether to use a distro or not on the ability to edit a menu is pretty bone headed if you ask me. ;) :P 

You do know that pressing alt + f2 gives a run dialog where you can simply type the name of the prgam you want to run and press enter? It tab completes.[/QUOTE]

I didn't know that (so I've learnt something new today, thanks) but I'd still like to be able to set the menus up the way I want them.  Call me lazy (or stubborn if you like) but I like to at least have the option to access the programs I want through the menu (I'd also like to know that I don't have to live with what the developers thought I would like, and that I can change things around to suit me ;)  ).

---

### Post by Catsworth on 2005-12-09
[QUOTE=DirtDawg]No I agree this is a real problem. With Warty, the user could use the RMB on any menu and change the icons/programs, etc, etc. But for whatever reason, the developers trashed this small, extremely usefull and endearing feature. I mean, why?[/QUOTE]

What does RMB stand for?

Nice to know I'm not alone, thanks :)

---

### Post by Catsworth on 2005-12-09
[QUOTE=Laestrygo]What you are probably looking for can be found here:[http://www.gnomefiles.org/app.php?soft_id=1183](http://www.gnomefiles.org/app.php?soft_id=1183)

download the package and

```
sudo dpkg -i alacarte_0.8-0ubuntu1_all.deb
```[/QUOTE]

Ok, thanks for that.

I got the package but got the following message when I tried to install:

```
Selecting previously deselected package alacarte.
(Reading database ... 60174 files and directories currently installed.)
Unpacking alacarte (from alacarte_0.8-0ubuntu1_all.deb) ...
dpkg: dependency problems prevent configuration of alacarte:
 alacarte depends on python-xdg (>= 0.15); however:
  Version of python-xdg on system is 0.9-1.
dpkg: error processing alacarte (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 alacarte

```

I understand that the Alacarte package needs to have the python-xdg(0.15) package installed to be able to install, how do I go about updating my version of python-xdg?

I looked in the System > Administration Synaptic Package Manager lists and couldn't find the version needed.

Thanks.

*Cats*

---

### Post by Catsworth on 2005-12-09
[QUOTE=CPUFreak91]That's not too n00b. Actually you're doing pretty good to install both OSes already.[/QUOTE]

Thanks :D 

[QUOTE=CPUFreak91]
Have you tried right clicking on the Applications > And then Edit Menus?
Then clicking on the Menu you want to add another menu to and clicking "New Menu"?[/QUOTE]

Yep, the options I get are:

--Help
--Remove From Panel
--Move (greyed-out)
--Lock To Panel

---

### Post by DirtDawg on 2005-12-09
RMB means "Right Mouse Button". 

I can vouche for the "Edit Menus" option. It's fairly worthless.

---

### Post by Catsworth on 2005-12-10
[QUOTE=DirtDawg]RMB means "Right Mouse Button". 

I can vouche for the "Edit Menus" option. It's fairly worthless.[/QUOTE]

Oh, thanks for that (RMB, it's fairly obvious really ;)  ) I should have worked that out for myself.

---

### Post by Catsworth on 2005-12-10
Ok, this whole Ubuntu/Linux experience is starting to go a bit sour now..

Am I really the only person in the world that wants to do this?

Why is it that such a (seemingly) simple function has been left out of Ubuntu?

Why have I got to bugger about trying to install a seperate app. just to edit my menus the way that I want to? More to the point, why is it that the particular app. that I need to install appears to be the only thing in the whole damn world that I _can't_ install because my installation doesn't have the right version of some obscure file?

Somebody _please_ help me sort this out.  I really want to learn but I'm starting  to wonder what the point is when something this simple is so bloody frustrating and seemingly impossible to solve.

There _must_ be somebody out there that has got this sorted......

---

### Post by Zonkle on 2005-12-10
I was looking also of how to edit the menus and sort them .... I hope it will be easy ... but it doesn't look like so ..

---

### Post by bonzodog on 2005-12-10
There is a way of editing the gnome menus, but I found that smeg (the graphical tool) seems to break things. I actually manually hand write the .desktop files in /usr/share/applications. Adding to that dir then re-spawning gnome will add menu Items successfully. 

The ubuntuguide.org menu how-to applies in breezy as well as hoary and should work for you. 

Look at other .desktop files to get an idea of their structure, and then learn how to write one for the app you want yourself.

Gnome menu editing is still buggy at this stage, but we are hoping to sort it by dapper.

---

### Post by Catsworth on 2005-12-12
Success at last!

Re-installed Ubuntu and now (after yet more buggering about with the sudoers file because, for some reason, Ubuntu doesn't set me up as being able to sudo for root) I can edit menus the way I should be able to.

Thanks for the help guys, much appreciated :)

---

### Post by varunus on 2005-12-12
I think the issue was that you installed the menu editor from synaptic.  Ubuntu comes with its own menu editor called SMEG.  It lets you add new categories.  The one you installed must have replaced smeg priority wise in the "edit menus" option (which makes sense, since if you install it Ubuntu goes "OK, use that one").  Smeg lets you make new categories and organize your menus how you want to.

Glad you got it working.

---

### Post by Zonkle on 2005-12-13
Catsworth .,... how did you do it ???

---

### Post by ninotob on 2005-12-13
[QUOTE=Zonkle]Catsworth .,... how did you do it ???[/QUOTE]

open your terminal, type "smeg" and press enter.  If you don't have smeg, you've uninstalled it somehow and should get it from synaptic.  Normally you can right click on "Applications" and choose menu editor -- this lets you add menus and programs, but note the prior poster who mentioned that the default right click-menu editor (smeg) may have been replaced by a custom option, so try running smeg from the command line to ensure that is what you are using.

---

### Post by Catsworth on 2005-12-15
[QUOTE=Zonkle]Catsworth .,... how did you do it ???[/QUOTE]

I'm really not sure.

I deleted the Linux partitions, and then reinstalled Ubuntu.

After that it seemed to work {*shrugs*}.

---

### Post by Zonkle on 2005-12-17
Oh ... I know "smeg"!! ... but it edits only the Applications menu!

I wanted to edit the other menus like "Places" and "System" (Sort,Edit,Delete,Insert).

Thanks any way ;)

---

### Post by varunus on 2005-12-20
Editing "places" can kind of be done in Nautilus.  Open up your file browser, and set the left pane to be "Places."  I think you can then drag and drop folders over there to add them to your places.

System, unfortunately, you can't edit yet...apparently the GNOME devels are working on fully customizable menus for the next release, hopefully it'll make it in.  The reason we have all these problems with menu editing is because GNOME switched their menu system recently so that KDE, GNOME, and XFCE would all have the same menu systems.  Your applications menu will become your K menu if you ever switch to KDE.

---

