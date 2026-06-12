---
title: "ubuntu 11.04 - add a new menu in unity !?!"
date: 2011-04-28
forum: Desktop Environments
---

### Post by madeinfamous on 2011-04-28
allo all,

i would like to add a custom menu to unity,

i have google/forum search but could not find anything, it's too new for me and i don't have all the keyword to do a nice search,

i have done a screen capture of what i would like to do:

[https://sites.google.com/site/nueusx/addanewmenu.png]("https://sites.google.com/site/nueusx/addanewmenu.png")

if anyone knows and is willing to explain... it will be greatly appreciated

thank you all, have a nice weekend!

---

### Post by rafaeljusto on 2011-04-29
Here is the solution:

1. Create a file in ~/.local/share/applications/ called something.desktop

2. Fill the file with the following content (change it to call the programs that you want):

```


[Desktop Entry]
Name=Example
Comment=This is just an example
Exec=
Icon=server
Terminal=false
Type=Application
Categories=GNOME;

X-Ayatana-Desktop-Shortcuts=Item1;Item2;

[Item1 Shortcut Group]
Name=Item1
Exec=gnome-terminal --command="top"
OnlyShowIn=Unity

[Item2 Shortcut Group]
Name=Item2
Exec=gnome-terminal --command="ps aux"
OnlyShowIn=Unity


```

3. This file should be executable (chmod +x something.desktop)

4. Drag and drop the created file on the Unity dock

5. Right click on the icon to get what you want

Best regards,
Rafael Justo

---

### Post by Ctulhu on 2011-04-30
I think it's great that you have the answer and that you provide it like this. Seriously!

But let me ask (in general): THIS TYPE OF CRAP is how we're now supposed to do this? I want to install the programming language R and used to have an application-in-terminal item in the main menu, which was supereasy to do. And now in 11.04, this is the (most unintuitive) solution for this? Canonical has got to be kidding ...

---

### Post by Krytarik on 2011-04-30
@Ctulhu: The OP was asking about how to add a new submenu into the launcher/dash menu, like the title of this thread states. But the instructions stated in post #2 are indeed a way to create a launcher, a very awkward way, the result of that would be a launcher with which you can run different commands through the right-click menu.

But for you, you can (at least) just
- create a launcher at your desktop
- move it into "~/.local/share/applications"
- drag it into the launcher from there

Yeah, I know, it is still more complicated than before, for now.

---

### Post by rafaeljusto on 2011-05-02
For now I didn't find any "point and click" solution. I just started using Unit last Thursday (when Ubutnu 11.04 was released) and, as you, I was wondering why they removed this great functionality for organizing menus. I think that after some time the Unity will have the same functionalities of GNOME, otherwise I'm going to migrate to GNOME3.

---

### Post by madeinfamous on 2011-05-02
allo Rafael!

thank you, i appreciated, & will try that!

i will put a "solve" in the title if it work when i'm done!

have a nice week!

:)

---

### Post by jascayne on 2011-07-06
Did you ever have any luck getting new items added to Dash? I've been scouring Google and have only found suggestions on adding things to the launcher. I found that if I search specifically for the name of the custom .desktop file I added to the same folder where a launcher item would go (~/.local/share/applications) it will return the application in question, but it will not appear in the category I want it to.

---

### Post by ashton93 on 2011-07-06
Sorri for interrupting but i am also new too and i was wondreing how to make a post or thread on here?

---

### Post by demondev on 2011-08-03
Why don't you use "drag & drop"? It works fine for me...

---

### Post by Ctulhu on 2011-08-03
Drag and drop for a custom menu entry??? I don't think you understood the question: I want to a create a new menu entry myself, with a user-defined command line entry etc. - there is nothing to drag ...

---

### Post by mc4man on 2011-08-03
> **Ctulhu said:**
> Drag and drop for a custom menu entry??? I don't think you understood the question: I want to a create a new menu entry myself, with a user-defined command line entry etc. - there is nothing to drag ...
You should probably be a bit more clear on what you want
If wanting to add a new category to the 12 now available in the 'all applications' drop down then grab the source and have fun.
If wanting a custom .desktop (aka launcher) to show in a specific category that's fairly simple
If wanting a custom menu available in unity that's not too difficult, though based on prior post I gather you're not interested in such stuff

---

### Post by Ctulhu on 2011-08-03
What I wanted at the time of the initial posting - i.e., updates may have taken care of this by now altho I still read how difficult Unity is to configure without non-Ubuntu addons - was to create a launcher with the following propoerties:

Type: Application in Terminal
Name: R 2.12.1
Command: /usr/lib/R/bin/R

And at the time at least it seems that was not possible without gconf crap (and certainly not with drag-and-drop, as one would reasonably have expected). I moved on to Mint for now where this is all easy, I'll check back w/ Ubuntu for 11.10 0 - otherwise, I'll stick w./ Mint.

---

### Post by mc4man on 2011-08-03
> **Ctulhu said:**
> What I wanted at the time of the initial posting - i.e., updates may have taken care of this by now altho I still read how difficult Unity is to configure without non-Ubuntu addons - was to create a launcher with the following propoerties:

Type: Application in Terminal
Name: R 2.12.1
Command: /usr/lib/R/bin/R

And at the time at least it seems that was not possible without gconf crap (and certainly not with drag-and-drop, as one would reasonably have expected). I moved on to Mint for now where this is all easy, I'll check back w/ Ubuntu for 11.10 0 - otherwise, I'll stick w./ Mint.

That was (then) and still is quite simple, basically explained previously (create a custom .desktop, add as standalone or just add to an existing launcher icon as a quicklist entry
(or as I do  - create launcher icon menus

Though I don't use there is an app indicator for natty/unity that provides the old gnome2-panel menu (and I'd assume can be edited as before w/ edit menus/alacarte

As far as 11.10+ - most of what anyone wants to do in these areas in quite doable, but it will be left up to the user to implement. For instance gnome3 has removed the ability to directly use custom commands, you have to do it yourself thru various means
Such is the future...

---

### Post by Ctulhu on 2011-08-03
Ok, I may look into that again altho I think that all of these are more geeky than this kind of stuff has to be. If this whole unity stuff is about luring ppl away from Windows, well, my dad is not gonna fk around with a customized .desktop, and as a matter of fact, neither do I (altho I use the console, use tow programming languages, etc. An OS does its job best if it's not in the way. But that's just me rambling :-) thanks for your responses!

---

