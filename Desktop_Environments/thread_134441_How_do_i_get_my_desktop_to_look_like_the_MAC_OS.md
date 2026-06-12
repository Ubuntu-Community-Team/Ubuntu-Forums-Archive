---
title: "How do i get my desktop to look like the MAC OS?"
date: 2006-02-21
forum: Desktop Environments
---

### Post by risknothin on 2006-02-21
I saw this screenshot [http://www.ubuntuforums.org/attachment.php?attachmentid=5767&d=1138808922](http://www.ubuntuforums.org/attachment.php?attachmentid=5767&d=1138808922)
and was wondering how i could get my desktop to look like that and to have the  weather program in the bottom right.

Thanks for any help

---

### Post by bluevoodoo1 on 2006-02-21
[QUOTE=risknothin]I saw this screenshot [http://www.ubuntuforums.org/attachment.php?attachmentid=5767&d=1138808922](http://www.ubuntuforums.org/attachment.php?attachmentid=5767&d=1138808922)
and was wondering how i could get my desktop to look like that and to have the  weather program in the bottom right.

Thanks for any help[/QUOTE]


Gdesklets. You can get a bunch of weather apps and the 'starter bar' from gdesklets. It's available with Synaptic.

---

### Post by risknothin on 2006-02-21
thank you, how about the mac look with the icons on the bottom?

---

### Post by bluevoodoo1 on 2006-02-21
[QUOTE=risknothin]thank you, how about the mac look with the icons on the bottom?[/QUOTE]

The icons are from the "starter bar" launcher applet within gdesklets. So, the weather applet and starter bar are both available with gdesklets. :mrgreen:

---

### Post by taurus on 2006-02-21
And don't forget about gkrellm on the right side of the screen either...  ;)

---

### Post by Killgore on 2006-02-22
What about the see-thru irc client? What and how would you do that?

---

### Post by xhie on 2006-02-22
yeah what is that irc client? thats pimptastic

---

### Post by nalmeth on 2006-02-22
gdesklets.gnomedesktop.org/index.php

its all here

---

### Post by ardchoille on 2006-02-22
[QUOTE=xhie]yeah what is that irc client? thats pimptastic[/QUOTE]
That looks like the irssi IRC client running in a borderless transparent terminal.

---

### Post by xhie on 2006-02-22
I know how to make my terminal transparent, how do i make it borderles?

---

### Post by Perfect Storm on 2006-02-22
You can use Alltray to that or use eterm terminal

---

### Post by nmastae on 2006-02-22
I'm a newbie. I have downloaded gdesklets. How do I install it in Gnome?

Also, I have put a MacOSX theme on my desktop. How do I install the icons, which came in a separate package?

Will gdesklets work with this earlier Mac look-alike setup?

Thanks!

---

### Post by bluevoodoo1 on 2006-02-22
[QUOTE=xhie]I know how to make my terminal transparent, how do i make it borderles?[/QUOTE]

Eterm. I use it exclusively with Blackbox. I know with blackbox you have to use the Esetroot command to "set" your background image (to make the terminal transparent). I'm not sure how to do it with GNOME, probably have to add "Esetroot /path/to/your/image.jpg" it to some startup script so you don't have to manually do it everytime... If not, you'll just get a random image whenever Eterm is started. Here's a code for a transparent/borderless/buttonbar-less Eterm.

```

Eterm -x -0 --trans --scrollbar=off --buttonbar 0

```

EDIT:
If you downloaded gdesklets with Synaptic then it *should* be in one of your menus. That's the easiest way to get it. 

Open your theme manager. I believe it's System > Preferences > Theme and simply drag the icon theme set to the open dialog window (you don't have to untar them). And then select it.

The icon launcher is called 'starter bar' as previosly mentioned. You'll have to add the icons and commands to each application. I'm not sure what the weather app is called, but if I remember correctly there are a bunch to choose from.

---

### Post by Perfect Storm on 2006-02-22
You might take a look at this: [http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)

---

### Post by nmastae on 2006-02-22
EDIT:
If you downloaded gdesklets with Synaptic then it *should* be in one of your menus. That's the easiest way to get it. 

Open your theme manager. I believe it's System > Preferences > Theme and simply drag the icon theme set to the open dialog window (you don't have to untar them). And then select it.

[COLOR="Blue"]I downloaded it here: [http://www.gdesklets.org/?mod=downloads/gdesklets](http://www.gdesklets.org/?mod=downloads/gdesklets)
When I dragged that .tar.bz2 icon into Theme preferences I got a messaged that said I have to compile it. How?! 

Is there a .tar.gz version of this app? (I learned yesterday that this file type will work...) [/COLOR]

The icon launcher is called 'starter bar' as previosly mentioned. You'll have to add the icons and commands to each application. I'm not sure what the weather app is called, but if I remember correctly there are a bunch to choose from.[/QUOTE]

---

### Post by bluevoodoo1 on 2006-02-22
[QUOTE=nmastae]

[COLOR="Blue"]I downloaded it here: [http://www.gdesklets.org/?mod=downloads/gdesklets](http://www.gdesklets.org/?mod=downloads/gdesklets)
When I dragged that .tar.bz2 icon into Theme preferences I got a messaged that said I have to compile it. How?! 

Is there a .tar.gz version of this app? (I learned yesterday that this file type will work...) [/COLOR]

The icon launcher is called 'starter bar' as previosly mentioned. You'll have to add the icons and commands to each application. I'm not sure what the weather app is called, but if I remember correctly there are a bunch to choose from.[/QUOTE]


The dragging and dropping ONLY refers to your Icons. (that you may have gotten from [http://www.gnome-look.org](http://www.gnome-look.org) or somewhere similar)

If you open up Synaptic (system > administration > synaptic package manager) you can download gdesklets. 

The icons you have and gdesklets are two totally different items. 

Follow the link provided by Artificial Intelligence. It should answer everything in a nice step-by-step fashion.

---

### Post by nmastae on 2006-02-22
[QUOTE=bluevoodoo1]The dragging and dropping ONLY refers to your Icons. (that you may have gotten from [http://www.gnome-look.org](http://www.gnome-look.org) or somewhere similar)

If you open up Synaptic (system > administration > synaptic package manager) you can download gdesklets. 

The icons you have and gdesklets are two totally different items. 

Follow the link provided by Artificial Intelligence. It should answer everything in a nice step-by-step fashion.[/QUOTE]
Thanks. Changed my repositories to include Universe and then downloaded gdesklets in Synaptic without a problem.

Previously, I had downloaded an Icons file from gnome-look.org. Do I have to drag each individual icon into the themes manager? I want to be able to use these mac look-alike icons systemically, but I haven't a clue how to do this.

BTW. I did "select all" and dragged the lot of them into the theme manager, but I see no new icons there. Is there a place in gnome to select specifics icon themes?

Thanks again.

---

### Post by bluevoodoo1 on 2006-02-22
[QUOTE=nmastae]Previously, I had downloaded an Icons file from gnome-look.org. Do I have to drag each individual icon into the themes manager? I want to be able to use these mac look-alike icons systemically, but I haven't a clue how to do this.[/QUOTE]

Just drag the entire file. I have the MAC osx icons too and the file is "OSX2.2.tar.gz" I simply drag that file (no need to open it or untar it) into the open theme manager window and that's all.

---

### Post by xhie on 2006-02-22
Eterm is cool, thank you :)

While were on the topic, how do I set it so that certain programs, like gkrellm and Eterm, in this case, dont show up on the panel when they are running?

---

### Post by bluevoodoo1 on 2006-02-22
[QUOTE=xhie]Eterm is cool, thank you :)

While were on the topic, how do I set it so that certain programs, like gkrellm and Eterm, in this case, dont show up on the panel when they are running?[/QUOTE]

I'm not sure. I hardly ever use gnome-panel with blackbox and I use conky instead of gkrellm. Maybe someone else knows??? Perhaps there is a thread about it? Or ask your question as a new thread.

---

### Post by Perfect Storm on 2006-02-22
I have heard it's possible, but I can't remember where I saw it.

---

### Post by xhie on 2006-02-23
Devils pie took care of Eterm showing up in the taskbar, and everything else for that matter... horray Devil's Pie !  :)

The only problem I have left is this:

Eterm -x -0 --trans --scrollbar=off --buttonbar 0 

runs at start up, its all good except that sometimes, not all the time, it loads with a random background. Why would --trans not work right but the other commands work just fine? And um.. how do I fix this? I saw somewhere on these forums someone saying they had the same problem and the advice they got was to exit Eterm, save the current session and log out, that didnt work for me. 

Incidently if I boot up, Eterm starts with a random background, then I ctrl+alt+bkspc and login again its always fine, why is that?

---

### Post by bluevoodoo1 on 2006-02-23
[QUOTE=xhie]runs at start up, its all good except that sometimes, not all the time, it loads with a random background. Why would --trans not work right but the other commands work just fine? And um.. how do I fix this? I saw somewhere on these forums someone saying they had the same problem and the advice they got was to exit Eterm, save the current session and log out, that didnt work for me.[/QUOTE]

Quoting myself below, you have to use the "Esetroot" command to the target of your wallpaper. 

[QUOTE=bluevoodoo1]Eterm. I use it exclusively with Blackbox. I know with blackbox you have to use the Esetroot command to "set" your background image (to make the terminal transparent). I'm not sure how to do it with GNOME, probably have to add "Esetroot /path/to/your/image.jpg" it to some startup script so you don't have to manually do it everytime... If not, you'll just get a random image whenever Eterm is started. Here's a code for a transparent/borderless/buttonbar-less Eterm.

```

Eterm -x -0 --trans --scrollbar=off --buttonbar 0

```

[/QUOTE]

EDIT: Just tried it in GNOME and it works. Open a terminal type "Esetroot path/to/your/backgroundimage.jpg" to the background you currently have. Then open Eterm with "Eterm --trans" and the transparency will work. As stated above you'll have to add "Esetroot path/to/your/backgroundimage.jpg" to some startup script or you may have to type it everytime you start GNOME.

---

### Post by xhie on 2006-02-23
Awsomeness!  Thank you :)  Works great now :D

---

### Post by John Jason Jordan on 2006-02-23
[QUOTE=bluevoodoo1]Quoting myself below, you have to use the "Esetroot" command to the target of your wallpaper. 
EDIT: Just tried it in GNOME and it works. Open a terminal type "Esetroot path/to/your/backgroundimage.jpg" to the background you currently have. Then open Eterm with "Eterm --trans" and the transparency will work. As stated above you'll have to add "Esetroot path/to/your/backgroundimage.jpg" to some startup script or you may have to type it everytime you start GNOME.[/QUOTE]
The problem is, I don't use a wallpaper background image. I just have it set to a particular color. And the -trans command does not work. Also, I got rid of the scrollbars, but I still have the title bar across the top. Are there other commands? Where is the Eterm documentation for command line arguments?

---

### Post by bluevoodoo1 on 2006-02-23
You can use Esetroot for a background color too. Look at Esetroot --help.  Should be "Esetroot -bgcolor <put your color here>"  Or you could try the command bsetroot... for example...
```

bsetroot -solid rgb:90/77/aa
```

(just tried bsetroot and it works... should be an odd purple color)



This will get you no title, scrollbar or buttonbar. (if you do use an image, use Esetroot and --trans for transparency)

```

Eterm -x --buttonbar 0 --scrollbar=off
```

look at "man Eterm" for more help.

---

### Post by John Jason Jordan on 2006-02-23
[QUOTE=bluevoodoo1]You can use Esetroot for a background color too. Look at Esetroot --help.  Should be "Esetroot -bgcolor <put your color here>"  Or you could try the command bsetroot... for example...
```

bsetroot -solid rgb:90/77/aa
```

(just tried bsetroot and it works... should be an odd purple color)



This will get you no title, scrollbar or buttonbar. (if you do use an image, use Esetroot and --trans for transparency)

```

Eterm -x --buttonbar 0 --scrollbar=off
```

look at "man Eterm" for more help.[/QUOTE]
I already looked at man Eterm on a web site. None of the options work. None at all. No matter what options I add it always comes up in a window that is exactly the same size (too small), with the same hideous random background images, with the title bar, button bar and scroll bars, and with fonts that are extremely low-res pixelated bitmaps (unreadable).

I know zero about programming and practically nothing about entering commands from a terminal, but you'd think I'd have gotten at least one option right. I think it just doesn't work on Ubuntu-64 Breezy with a solid color desktop and no themes. I think you need to have some other kind of desktop before any of this stuff will work. I'm happy with my computer the way it is, I just thought it might be cool to have a terminal that looked like it was floating in the desktop. I can certainly do without it, though, so I just uninstalled Eterm. :(

Thanks for the suggestions anyway. :)

---

### Post by xhie on 2006-02-24
[QUOTE=bluevoodoo1]Quoting myself below, you have to use the "Esetroot" command to the target of your wallpaper. 



EDIT: Just tried it in GNOME and it works. Open a terminal type "Esetroot path/to/your/backgroundimage.jpg" to the background you currently have. Then open Eterm with "Eterm --trans" and the transparency will work. As stated above you'll have to add "Esetroot path/to/your/backgroundimage.jpg" to some startup script or you may have to type it everytime you start GNOME.[/QUOTE]


I swere this is my last question then I'll shut up about this, thank you for being very helpful thus far with me :)

what I noticed after adding the above line to a script that starts up Eterm is that sometimes, not all the time, when I start up for some reason my home folder will be sitting open on my desktop, when I get rid of that line it never does it. What could be causing this?


Btw... this is even more stupid, but: last night I got bored and really liked that wallpaper in the orignal post, but instead of being a wallpaper I think that little apple logo with tux should be that icon that replaces the ubuntu icon in gnome panels... so I made it into an icon, and here it is:
[IMG]http://i38.photobucket.com/albums/e114/xhie/distributor-logo.png[/IMG]

---

### Post by Perfect Storm on 2006-02-24
Rename your icon to distributor-logo.png

Then:
```

sudo cp distributor-logo.png /usr/share/icons/hicolor/48x48/apps
killall gnome-panel

```

---

### Post by bluevoodoo1 on 2006-02-24
[QUOTE=John Jason Jordan]I know zero about programming and practically nothing about entering commands from a terminal, but you'd think I'd have gotten at least one option right. I think it just doesn't work on Ubuntu-64 Breezy with a solid color desktop and no themes. I think you need to have some other kind of desktop before any of this stuff will work. I'm happy with my computer the way it is, I just thought it might be cool to have a terminal that looked like it was floating in the desktop. I can certainly do without it, though, so I just uninstalled Eterm. :([/QUOTE]

Maybe it's the 64 bit environment? I wish I had an idea for you.


[QUOTE=xhie]what I noticed after adding the above line to a script that starts up Eterm is that sometimes, not all the time, when I start up for some reason my home folder will be sitting open on my desktop, when I get rid of that line it never does it. What could be causing this?
[/QUOTE]

Hmmm... I don't know. What does your startup script look like?

---

### Post by xhie on 2006-02-24
```
#!/bin/bash

Esetroot /home/lina/wallpaper/think.jpg
Eterm -x -0 --trans --scrollbar=off --buttonbar 0

```


Is all it is, Im confused, each one individually dont make the home pop up on my desktop, in the command line executed individually they dont do it, but put together they do, even if i exit out of Eterm, then run that script it will sometimes do it.

---

### Post by bluevoodoo1 on 2006-02-24
[QUOTE=xhie]```
#!/bin/bash

Esetroot /home/lina/wallpaper/think.jpg
Eterm -x -0 --trans --scrollbar=off --buttonbar 0

```


Is all it is, Im confused, each one individually dont make the home pop up on my desktop, in the command line executed individually they dont do it, but put together they do, even if i exit out of Eterm, then run that script it will sometimes do it.[/QUOTE]


Hmm perhaps an ampersand on the end of each? and/or putting "" in there too, or even getting rid of the /home/lina/ and just putting wallpaper/think.jpg. Test those out. Maybe something like this...

```
#!/bin/bash

Esetroot "wallpaper/think.jpg" &
Eterm -x -0 --trans --scrollbar=off --buttonbar 0 &

```


NOTE: I have a script for blackbox (that I don't use too often and my Esetroot line looks like this.... Esetroot ".blackbox/backgrounds/fissure.jpg" &) and I just started blackbox with it twice and the Esetroot worked both times.

---

### Post by xhie on 2006-02-24
I tryed any combination of & and "" that I could think of and it still does it, except that with the script you posted it does it every single time heh...

If yours dosent do it on blackbox then this is some sort of strange gnome thing?

---

### Post by bluevoodoo1 on 2006-02-24
[QUOTE=xhie]except that with the script you posted it does it every single time heh...
[/QUOTE]

HAHA!! Whoops, well, I guess I'm not one to ask since I don't really use gnome too much anyway. :)

---

### Post by xhie on 2006-02-27
The answere I got on the gnome support forums was this, thought I would share it since someone else might have the same problem some day

[Quote=jleedev]When your home folder pops up, it means nautilus crashed or was killed.

Nautilus wants to paint the desktop too, so you can't have Esetroot and Nautilus at the same time. You can either disable the nautilus desktop or have it set the wallpaper instead.[/QUOTE]

---

### Post by bluevoodoo1 on 2006-02-28
[QUOTE=xhie]The answere I got on the gnome support forums was this, thought I would share it since someone else might have the same problem some day[/QUOTE]


Very strange indeed.

---

### Post by lapsey on 2006-02-28
this is all quite nice but what the world really needs is a gnome-panel that is used by the currently focused program for its menubar

---

