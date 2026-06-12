---
title: "Theme package"
date: 2010-11-25
forum: Desktop Environments
---

### Post by parth.s on 2010-11-25
Hey! Been using ubuntu 10.04 for quite some time now. After some searches here and there i was able to configure and use the compiz effects.

Recently i came across the theme....and cant figure out a way...

i have the murrine and equinox engines installed....I have also tried to copy the gtk-2.0 folder to .~/themes...but incompletely

Btw... im assuming that 10.10 themes work on 10.04

Please help...Thanks

---

### Post by parth.s on 2010-11-25
srry forgot to post the link..;)

this is the link
[http://rasa13.deviantart.com/art/November-Desk-Ubuntu-10-10-184663031](http://rasa13.deviantart.com/art/November-Desk-Ubuntu-10-10-184663031)

---

### Post by Frogs Hair on 2010-11-25
I only see a link for an image of the theme and not the theme it's self . I can't test it without the theme package. Rasa13 is a forum member you could pm him , he is often on the screen shots thread. (known as Rasa1111 on the forum)

---

### Post by parth.s on 2010-11-26
Hey! The links are right there below the image...Rasa13 has posted them below....just before the comments start

[http://rasa13.deviantart.com/art/November-Desk-Ubuntu-10-10-184663031](http://rasa13.deviantart.com/art/November-Desk-Ubuntu-10-10-184663031)

Thanks

---

### Post by koleoptero on 2010-11-26
1. Extract the zip.
2. Find the folder that contains the gtk-2.0 folder (not the gtk-2.0 folder itself but one folder up). 
3. Open appearance preferences.
4. Drag and drop that folder on the appearance preferences window.
5. Select the theme from that window.
6. ????
7. PROFIT!!


This applies to all packaged themes that don't have custom installers.

---

### Post by parth.s on 2010-11-26
@koleoptero: THanks!! i am able to get the windows border and color combn. but i also want to get the taskbar like that how to get the complete look!

---

### Post by koleoptero on 2010-11-27
> **parth.s said:**
> @koleoptero: THanks!! i am able to get the windows border and color combn. but i also want to get the taskbar like that how to get the complete look!

That isn't the regular gnome panel (gnome-panel). That is avant-window-navigator. Install it from their ppa to get the latest by entering in a terminal:

sudo add-apt-repository ppa:awn-testing/ppa
sudo apt-get update
sudo apt-get install avant-window-navigator-trunk dockmanager

After that run it from the menus, from Applications -> Accessories. You'll see a very regular dock at the bottom. You can then contact Rasa1111 here in the forums asking him to send you the AWN theme, and install it from its preferences.

You can also toy with it to get it to look in whatever way you want it.

To get rid of the regular panel completely you can search around, there are at least 3 ways of doing it.

---

### Post by Rasa1111 on 2010-11-27
Hi parth.s

Glad you got the GTK theme going. :)

You can use the instructions provided by koleoptero to install AWN, 
or use this link~
[http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html](http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html)
Both will get you to the same place I believe. lol

The AWN theme~ "the black/purple" in the dA screenshot, 
ive uploaded here 
~[ Click to download AWN theme~]("http://ubuntuone.com/p/R4X/")

To install the theme in AWN~
 Open the AWN preferences.. [right click dock, choose 'dock prefs.']
.make sure you apply "Lucido" under "style".

 Then go to the "themes" 'tab', choose 'install theme', 
navigate to the file you just downloaded from here, 
and choose ok/open. 
The theme will be installed now.
 Just choose it and click "apply". 

 To make the top panel 'gone', you can do a couple things.. 
If you dont want to totally remove it, you can simply move it to the bottom, and choose "autohide" for it,
so it will only appear when you place your mouse at the bottom of the screen.
Thats what I did for months before i took it away. 

The other way to do it, without completely removing it,
is to change the settings so that avant-window-navigator 
is the 'main panel' at startup , rather than gnome-panel. 

 I forget exactly how I did it, lol :duh:
but I was instructed by someone here,
So if thats what you want to do, let me know and Ill go find the instructions if you like. 

or, like i said, you can simply just hide it at the bottom. 

 Hope that helps. 
<3 
Peace

---

### Post by Penguin=) on 2010-11-27
> **parth.s said:**
> srry forgot to post the link..;)

this is the link
[http://rasa13.deviantart.com/art/November-Desk-Ubuntu-10-10-184663031](http://rasa13.deviantart.com/art/November-Desk-Ubuntu-10-10-184663031)

This doesen't look so good, i think it looks like the default theme that you get with it. Sorry.:popcorn:

---

### Post by Rasa1111 on 2010-11-27
Oh, I forgot~

 The windows buttons are not from that GTK theme~ 

They are from the theme called ["Equinox Ambient"]("http://techie-buzz.com/foss/equinox-ubuntu-themes-awesome.html")

---

### Post by Rasa1111 on 2010-11-27
> **Penguin=) said:**
> This doesen't look so good, i think it looks like the default theme that you get with it. Sorry.:popcorn:

lol, like the default? :lol: not quite, but ok.
Why you need to say sorry?
 for giving your opinion? 
I dont think an apology is in order for giving a personal opinion. lol  :p

---

### Post by parth.s on 2010-11-27
@Rasa1111 : Thanks a lot! i am almost done with the look here...
i dont mind hiding the panel for now..
just that my dock shows only a few applets on them (mozilla, chrome etc)  how do i get the icons on the gnome panel on the docky...

i have attached what my desktop looks like..

---

### Post by Frogs Hair on 2010-11-27
When you open an application that you want on the dock an icon will appear on the dock . To add right click and select add as launcher . To add applets such as clock and weather go in to awn settings and pick the ones you like by selecting the applet and using the arrow . Keep a menu installed until you have added the launchers you want or install a menu from the applets list in awn.

---

### Post by Rasa1111 on 2010-11-27
> **parth.s said:**
> @Rasa1111 : Thanks a lot! i am almost done with the look here...
i dont mind hiding the panel for now..
just that my dock shows only a few applets on them (mozilla, chrome etc)  how do i get the icons on the gnome panel on the docky...

i have attached what my desktop looks like..

No prob. :)
 Lookin good. 

To get the rest of the things from the panel on your dock~

 Add applets like. "digital clock", weather, garbage, 

~indicator applet(shows the volume, messaging menus/applets,), 

~Notification area (shows network connection) But you need to remove that from the panel first. It wont run in both I guess. 
then other things, like your desktop switcher, if you use it, the applet is called "shiny switcher", 

and then add "cairo main menu" or "yet another menu applet"
to get the "start button" up there. 


 hmm...
not sure what else...

 lemme know if i forgot something, or didnt make it clear enough. 


 Also, this post *may* help you set it up more how you want,...  lol
[http://ubuntuforums.org/showpost.php?p=9979588&postcount=388](http://ubuntuforums.org/showpost.php?p=9979588&postcount=388)

---

### Post by parth.s on 2010-11-27
Thanks Rasa1111 and Frogs Hair! Finally got the complete look..just one last question how did you put the applets on the black separator itself for me its placing applets between them..

nyways have a long way to go before i can finally switch to ubuntu completely..This forum is make ubuntu experience worth while!

Thanks

---

### Post by Frogs Hair on 2010-11-27
You can add & remove separators from the applets list and move them by dragging while the awn settings are open . Experiment  until you find a look that you like. Search awn tutorials I know there is one at Web Upd8 and I think You Tube has some as well.

---

### Post by Rasa1111 on 2010-11-27
> **parth.s said:**
> Thanks Rasa1111 and Frogs Hair! Finally got the complete look..just one last question how did you put the applets on the black separator itself for me its placing applets between them..

nyways have a long way to go before i can finally switch to ubuntu completely..This forum is make ubuntu experience worth while!

Thanks

hi parth.s

Most welcome!
Glad we could help! :)

> how did you put the applets on the black separator itself for me its placing applets between them..

hmmm..... 
let's see... 

Does this screenshot help you figure it out any better? 
[ATTACH]176796[/ATTACH]
Being able to see the dock, and the active applets window together,
does it make it any clearer?  

 If not, Ill put something a little better together if you like. ..
Not really sure how to put it into words in good way... lol
Sorry. 
But you just grab the applets and drag them where you want. 

Let me know. <3

---

