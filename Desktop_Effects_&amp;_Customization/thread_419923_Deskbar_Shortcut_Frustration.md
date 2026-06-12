---
title: "Deskbar Shortcut Frustration"
date: 2007-04-23
forum: Desktop Effects &amp; Customization
---

### Post by Apreche on 2007-04-23
So like many people I use the Gnome Deskbar a lot. It definitely provides a great increase in productivity and general computer usage efficiency. However, that only remains true as long as the keyboard shortcut to focus it is easy to hit. 

The problem I'm having is that setting the restrictions on what can and can not be the shortcut are intolerable. Not only that, but they are different between Edgy and Feisty! I use both, and I'd like to have the same shortcut on both. 

My Edgy machines are desktops with Happy Hacking Keyboards. My Feisty machine is a laptop (Fujitsu P7230). I have the desktops set to <Control>Space, which is fine. Feisty won't let me use Control<Space>, so I used Menu. You know, that weird key that opens context menus that nobody uses. 

Because I like to have keyboard shortcuts be the same on all machines, so I get used to them, I tried to set it to Menu on the Edgy desktops as well. Of course, they have Happy Hacking Keyboards which don't have a Menu key. That's ok, I can set it to Super_R, which is basically the same thing. I never use Super_R, always Super_L, so who cares? Well, it won't let me set it to Super_R. As far as deskbar is concerned, both Supers are the same key, even though xev can tell the difference. Also, it won't let me use Super on its own. I have to use it in combination with other keys. 

Listen, if the key combination is too difficult or hard to reach, it reaches a point where it is just easier to use the mouse. At that point, there's no reason to use deskbar at all. It would be faster to open a terminal with a keyboard shortcut and type in there. 

What do I do?

---

### Post by TimmyJ on 2007-04-23
Sorry I can't help with your problem, I just wanted to voice my frustration with setting the deskbar shortcut as well. It is to the point where I don't even use it soley because I can't set the shortcut to anything I find usable. Very frustrating.

---

### Post by TimmyJ on 2007-04-23
Hey, Upon further investigation the deskbar-shortcut can be configured to any value you like if you are using gconf-editor. So simply open up gconf-editor go to apps -> deskbar and there will be a 'keybinding' setting. Set this to whatever you like, it appears there are no restrictions. Good luck.

---

### Post by Apreche on 2007-05-01
Awesome. I was finally able to set it to <Super>Tab, which is working out well for me. Apparently, if you try to use gconf-editor in Feisty, it is not able to change this value because it is type schema. This method only works in Feisty.

---

### Post by drjimmy42 on 2007-05-30
I'd like to set it to something similar to quicksilver on my mac as its already under my hands.  
I tried setting <Alt>Space in gconf-editor but it didn't work and the shortcut text field in the deskbar prefs was blank after setting it.  

Has anyone successfully set it to something quicksilver-like?

---

### Post by luopio on 2007-06-26
Just got it working with <Control>space. That's my quicksilverish setting and works nicely on this keyboard. <Alt>space won't work though

---

### Post by drjimmy42 on 2007-06-26
Unfortunately Ctrl-space clobbers a very important emacs key binding.

---

### Post by ldrn on 2007-07-04
> **drjimmy42 said:**
> Has anyone successfully set it to something quicksilver-like?
I wanted alt-space, too.   I didn't.. set it to alt space, but I did get it to work as if I had.

I downloaded the xmacro package, then created a shell script in vim:

```
#!/bin/bash
echo KeyStrRelease space KeyStrPress Alt_L KeyStrPress F3 Ke
yStrRelease F3 KeyStrRelease Alt_L | xmacroplay "$DISPLAY"


```

I saved it as "alt-f3.sh" in a hidden directory named .xmacro under my home, but it should work anywhere. After that, I made it executable and set my window manager to launch it on alt-space (I'm using compiz, but it should work with gnome and metacity if you use gconf-editor to set it up).
I hope this helps someone else.     :)

---

### Post by Apreche on 2007-10-01
Alright, so. More on this issue. Up until now, using Feisty, I have used the gconf-editor to change my deskbar shortcut to be <Super>Tab. I have gotten very used to <Super>Tab over the past six months, and I'd like to keep it. However, I'd also like to upgrade to gutsy. 

So I put the gutsy beta on my laptop. I go to gconf-editor and I change the shortcut to <Super>Tab. It doesn't work. Not only that, but the deskbar has been changed from an actual bar to just a button that launches an application. 

This is terrible. At least let advanced users set any shortcut they want, even if you want to hide the option from average users. The deskbar applet is one of the most useful things in Ubuntu/Gnome. I use it a zillion times every day. But now in Gutsy, it has been made worse, not better. 

What to do?

---

### Post by GreatSlovakia on 2007-10-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/deskbar-applet/+bug/88354](https://bugs.launchpad.net/deskbar-applet/+bug/88354) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Does someone actually know why they changed it into such a horrible window... and @ldrn... I am just using linux 2 months now and I don t get [s]how you bind this script to a key[/s] totally what you do....

---

### Post by drjimmy42 on 2007-10-08
They changed it to the window because deskbar was completely rewritten during the google summer of code to allow it to develop new features.  They were pretty much at the end of the current architecture's abilities.  Anyway, returning the little popup is top priority for next release.

[http://arstechnica.com/reviews/os/gnome-2-20-review.ars/3](http://arstechnica.com/reviews/os/gnome-2-20-review.ars/3)

---

### Post by barrettorama on 2007-10-13
> **ldrn said:**
> I wanted alt-space, too.   I didn't.. set it to alt space, but I did get it to work as if I had.

I downloaded the xmacro package, then created a shell script in vim:

```
#!/bin/bash
echo KeyStrRelease space KeyStrPress Alt_L KeyStrPress F3 Ke
yStrRelease F3 KeyStrRelease Alt_L | xmacroplay "$DISPLAY"


```

I saved it as "alt-f3.sh" in a hidden directory named .xmacro under my home, but it should work anywhere. After that, I made it executable and set my window manager to launch it on alt-space (I'm using compiz, but it should work with gnome and metacity if you use gconf-editor to set it up).
I hope this helps someone else.     :)



Thanks Idrn, your solution worked great. I'm adding a couple notes for metacity functionality.

[LIST=1]
[*]Disable the <Alt>Space in System > Keyboard shortcuts by changing to something else (I used <Ctrl><Alt>Space)
[*]in gconf-editor apps/metacity/global_keybindings set one of the run_commands to your desired key combo (I used <Alt>space, note the lowercase s in space)
[*]down one group to apps/metacity/keybinding_commands set the file location for your script (which Idrn provides)
[/LIST]

Thanks again, 
-barrettorama

---

### Post by hk0i on 2007-10-30
I just installed Gutsy a few nights ago... I actually haven't really used Ubuntu much since Dapper or Edgy... So I've never really seen this gnome deskbar before.

I'm having a bit of a strange problem though. I typically bind my Alt+F3 key combination to pop
a new terminal window, which is always how I've set up my linux under any window manager.
It seems like I can change my shortcut but there is some bug that won't remove the Alt+F3
binding no matter what... And then at one point I managed to get the key binding GUI component
to get stuck so that whenever I hit a CTRL or ALT key it quickly exited the key bindings and would
not allow me to change it at all until I manually edited the key binding through gconf-editor.

I didn't have any problems getting Ctrl+Space to work through the GUI after that though.

Actually I've changed the key binding a few times... now it seems like any one of those keys I've
set works... so currently if I want my deskbar F1, F3, F4, Alt+F3, Ctrl+F3, Ctrl+F1, and Ctrl+Space
all trigger the deskbar... whoohoo!

Does anyone know where the config file is for deskbar if there is one?
It seems like every time I changed the key binding it just added it to the end
of an ever growing list.

I'll keep looking and post back if I find a solution for this.

---

### Post by hk0i on 2007-10-30
Sorry to double post, but I fixed the problem already. I opened up a terminal window and did:

killall -9 deskbar-applet

I got a message from the deskbar saying it quit unexpectedly and a prompt
to restart it. I restarted the deskbar and now everything works fine, and my
Alt+F3 is now vacant :D

---

### Post by Crafty Kisses on 2007-10-30
> **hk0i said:**
> Sorry to double post, but I fixed the problem already. I opened up a terminal window and did:

killall -9 deskbar-applet

I got a message from the deskbar saying it quit unexpectedly and a prompt
to restart it. I restarted the deskbar and now everything works fine, and my
Alt+F3 is now vacant :D
That's super weird.

---

### Post by Endolith on 2008-04-26
<Super>z for both Deskbar in Ubuntu and Launchy in Windows :)

---

### Post by Can+~ on 2008-04-26
Gnome-do does the trick for me.

Super+Space <type type type> enter.

... oh wait, this post is really old. (looks at Endolith)

---

