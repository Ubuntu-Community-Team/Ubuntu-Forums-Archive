---
title: "fluxbox window tabs"
date: 2006-01-11
forum: Desktop Environments
---

### Post by key on 2006-01-11
Hi everyone,

I just made the switch from KDE to fluxbox and I am seriously digging it. Flux rocks!

Maybe I am missing something here but I can't figure out "**window tabs**". Where are they? How do I use them? Are they style specific? 

I have "**session.tabs:   true**" in my ./fluxbox init file, but I still don't see them.

thanks,

key

---

### Post by hillbilly on 2006-01-11
Hey i have the same problem. But the tab functionality works though. If I middle click the square on the top left corner of a window and drag it ono the top left corner of another window, they get tabbed together. But somehow without the tab button stickting out, it doesnt look as good ;) ! 

Anyone else worked around this problem yet or does anyone else have this problem ?

---

### Post by hillbilly on 2006-01-13
** Bump ** ! 
Does anyone have the same problem with fluxbox ?

---

### Post by key on 2006-01-14
Hey Hillbilly,
guess its just me and you on this one ... :)

I downloaded some new fluxbox styles (with the tabs clearly visible in the screen shots) but I still dont have them on my screen. Leads me to believe that tabs are turned off in some config file in .fluxbox in ubuntu and are not style specific. I've looked in $HOME/.fluxbox/init and  $HOME/.fluxbox/startup, but I must have missed it. 

I read something on the fluxbox site that says there should be options to configure tabs in the configure submenu. I don't have those options in my menus so maybe I should figure out how to put it in. 

The config files in .fluxbox should override /usr/share/fluxbox, but I guess I should check there too. 

I am really digging this minimalist wm thing though. I don't think I will ever be able to go back to KDE now. We'll see what KDE4 brings...

happy hunting,
key

---

### Post by ardchoille on 2006-01-14
middle-click and drag the titlebar of one window to another window's titlebar and they will merge. Middle-click the tab you want to take out and drag it off the titlebar and it will unmarge. There is lots of documentation of the fluxbox site on how to make this feature automatic when "grouping windows".

Yes, fluxbox rocks!

---

### Post by key on 2006-01-14
Thanks ardchoille

I am running on a laptop with my trackpad so I didn't have middle button options. I plugged in my mouse and I have to say that window merging is **[SIZE="3"]incredibly[/SIZE]** cool. 

fluxbox gets better!

I read though some docs at fluxbox and they mention a submenu under 'configuration' that allows you to control tab placement etc.

You can see the submenu in the screenshot at the bottom of this page:
[http://www.fluxbox.org/features/tabs.php](http://www.fluxbox.org/features/tabs.php)

direct link:
[http://www.fluxbox.org/images/shots/fluxbox/gimplord.jpg](http://www.fluxbox.org/images/shots/fluxbox/gimplord.jpg)
 
Apparently this config menu is native in fluxbox, i.e. not directly accessible in .fluxbox/ config files. Is this right?

Any ideas how to get to that?

key

---

### Post by ardchoille on 2006-02-10
That menu is available by either left or right clicking the panel, if I remember correctly.

---

### Post by dbw on 2006-02-14
Key- 
 If you use both mouse buttons at once, this will emulate the third button, even on your two button laptop.

---

