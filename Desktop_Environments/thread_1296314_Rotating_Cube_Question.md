---
title: "Rotating Cube Question"
date: 2009-10-20
forum: Desktop Environments
---

### Post by bro brian on 2009-10-20
Hello all -
  In the Desktop Environments section, Sticky topic, it reads:
**How can I get the "cube" effect?** - overdrank[INDENT][(Image)]("http://ubuntuforums.org/attachment.php?attachmentid=71841&d=1211934590") First, install compizconfig-settings-manager. Then, in **System > Preferences > Advanced Desktop Effects Settings**, go to General Options, Desktop Size tab, and make sure **Horizontal Virtual Size** is set to 4. Go back to the main window, and enable the Desktop Cube and Rotate Cube plugins.
You can "spin" the cube by pressing Ctrl+Alt+Left and Ctrl+Alt+Right, or hold Ctrl+Alt and click and drag.

[/INDENT][B]I'm running the Jaunty verson of Ubuntu. I have intalled the compizconfig-settings-manager. Then the instructions state, "Then, in system>Preferences> _Advanced Desktop Effects Settings_, go to General Opttions.....
  I cannot find the _Advanced Desktop Effects Settings_ tab. It's simply not there....Were these instructions made for a different distro? At this point, I have stopped. I'm sure someone here will clarify.

[/B]

---

### Post by undecim on 2009-10-20
Looks for CompizConfig Settings Manager (that's what mine is called) or try ALT+F2 and type "ccsm"

---

### Post by bro brian on 2009-10-20
> **undecim said:**
> Looks for CompizConfig Settings Manager (that's what mine is called) or try ALT+F2 and type "ccsm"
That was it. I clicked on CompizConfig Setings Manager, and it was all there.
  I didn't see the cube until I went ahead & did a Ctrl/Alt Left (or Right). Well this is the shiznit for sure! I went ahead, and change my desktop setting to 4 desktops. I guess I'll play around with this stuff for a while until my laptop screen is looking wild & crazy. That means I may be asking more questions (the novice I am).
Thanks for the clarification.
Brian

---

### Post by earthpigg on 2009-10-20
> **bro brian said:**
> That was it. I clicked on CompizConfig Setings Manager, and it was all there.
  I didn't see the cube until I went ahead & did a Ctrl/Alt Left (or Right). Well this is the shiznit for sure! I went ahead, and change my desktop setting to 4 desktops. I guess I'll play around with this stuff for a while until my laptop screen is looking wild & crazy. That means I may be asking more questions (the novice I am).
Thanks for the clarification.
Brian

sounds good.

want to save yourself some future hassle, anticipating that you may/will end up breaking things while playing around with them (playing with things until they break is part of the fun, of course)?

compiz settings are stored here:

```
/home/yourusername/.config/compiz
```

easy way to back that up is to make a copy of it.

```
cp -r /home/yourusername/.config/compiz /home/yourusername/.config/compizbackup
```

since the compiz folder only containes 10-20kb of information, there is no reason you cant make 4 or 5 backups of different self-made compiz 'themes'.

then you can play with compiz without fearing breaking your user interface... because if/when you do make it unusable, just delete the compiz folder and rename compizbackup to compiz. log out and back in, and you will be back to where you where when you backed that folder up.

there is also no reason you can't replace another user's compiz config folder with your own so they get your settings, if you like, or even on another computer - possibly even another computer running an entirely different distribution.

heck, you can go ahead and turn that compiz folder into an single-file archive, upload it somewhere and share it with the world if you like.

---

### Post by earthpigg on 2009-10-20
also, easy way to turn compiz on/off when you break things:

alt+f2 to get to the 'run' menu, or run this command in a terminal.

turn compiz off and replace with metacity window manager (Ubuntu's default before you ever turned 'desktop effects' on):
```
metacity --replace
```

turn it back on when you have fixed things:
```
compiz --replace
```

(the --replace convention is used pretty much as standard across window managers, but mileage may vary.)

ubuntu's 'fusion-icon' package will add a point-and-click thingie in your taskbar with the same functionality, too.

think of it as a 'one-or-the-other' thing, though... either use --replace or use fusion-icon, but try don't mix and match.

---

### Post by undecim on 2009-10-20
> **earthpigg said:**
> also, easy way to turn compiz on/off when you break things:

alt+f2 to get to the 'run' menu, or run this command in a terminal.

turn compiz off and replace with metacity window manager (Ubuntu's default before you ever turned 'desktop effects' on):
```
metacity --replace
```turn it back on when you have fixed things:
```
compiz --replace
```(the --replace convention is used pretty much as standard across window managers, but mileage may vary.)

You can also set up the "Crash Manager" plugin to run that command when compiz crashes.

> **earthpigg said:**
> ubuntu's 'fusion-icon' package will add a point-and-click thingie in your taskbar with the same functionality, too.

YES! The fusion icon is great! That's one of the first things I install on ubuntu.

---

### Post by bro brian on 2009-10-20
> **earthpigg said:**
> also, easy way to turn compiz on/off when you break things:

alt+f2 to get to the 'run' menu, or run this command in a terminal.

turn compiz off and replace with metacity window manager (Ubuntu's default before you ever turned 'desktop effects' on):
```
metacity --replace
```turn it back on when you have fixed things:
```
compiz --replace
```(the --replace convention is used pretty much as standard across window managers, but mileage may vary.)

ubuntu's 'fusion-icon' package will add a point-and-click thingie in your taskbar with the same functionality, too.

think of it as a 'one-or-the-other' thing, though... either use --replace or use fusion-icon, but try don't mix and match.

OK - I'm a little cornfused.
If I've got this right:
Now that I've got the cube thing happening, I should back up compiz by using the command line mentioned earlier.
Next, I can install the 'fusion-icon' package to add a "point & click" icon in the taskbar (which will replace the old desktop functon (or metacity?) - or where IS the fusion-icon package?
  Does it sound like I've got the drift?

---

### Post by earthpigg on 2009-10-20
> **bro brian said:**
> OK - I'm a little cornfused.
If I've got this right:
Now that I've got the cube thing happening, I should back up compiz by using the command line mentioned earlier.


i wouldn't use the word 'should'. you can if you want to. i do. you can do it 100 ways differently than the method i suggested, too. "choice overload" is a normal part of Free Software :D

whatever method you use to back it up, the end result is that it will ensure that you can always get back to where you are now if you break things experimenting. 

> Next, I can install the 'fusion-icon' package to add a "point & click" icon in the taskbar (which will replace the old desktop functon (or metacity?) - or where IS the fusion-icon package?
  Does it sound like I've got the drift?

the fusion-icon package will let you easily switch between compiz ("desktop effects on") and metacity ("desktop effects off").

metacity and compiz and openbox and iceWM and a zillion other things are all examples of [window managers]("http://en.wikipedia.org/wiki/X_window_manager#Popular_X_window_managers"). 

compiz may be an especially sexy window manager, but its still just a window manager. nothing magical about window managers.

except that you can only have one window manager running at once. all fusion-icon does is hangs out in your system tray and switches between the compiz window manager and another window manager when you tell it to.

all ccsm / "Advanced Desktop Effects Settings" does is configure one of the Window Managers you currently have installed on your system (compiz, in this case). System -> Preferences -> Appearance configures another one... metacity.

fusion-icon can be found in synaptic, add/remove applications, or apt-get install fusion-icon. take your pick, the end result is all the same.

:guitar:

***component A)*** X runs on top of Linux or any other UNIX-like environment. 
***component B)*** a Window Manager runs on top of X. metacity and compiz are examples of window managers.
***component C)*** a Desktop Environment runs on top of a Window Manager. GNOME (in ubuntu by default), KDE (in Kubuntu by default), and LXDE (in Masonux by default) are examples of desktop enviornments.

this whole fusion-icon and "metacity --replace" stuff is just talking about replacing one example of component B with another example when you break one playing around.

you can have as many examples of components B and C as you want installed, all at the same time.

---

### Post by bro brian on 2009-10-20
OK, EP, I've done it! Whew - What a relief! So glad you all pointed that out to me. Just in case I screw something up for sure.
I guess we got a little bit off topic here, however it makes sense that the Rotating Cube, backing up, and the Compiz Fusion icon would go "hand in hand" - It all ties together.

---

### Post by bro brian on 2009-10-20
Back to the backing up part...
I think I backed it up al-right. Here's what I did in Konsole:

> bri@system76-pc:~$ cp -r /home/bri/.config/compiz /home/bri/.config/compizbackup


But then, when I typed the following in (for compiz settings), I got a "bash":

> bri@system76-pc:~$ /home/bri/.config/compiz
bash: /home/bri/.config/compiz: is a directory


Does this look right?
Bri

---

### Post by earthpigg on 2009-10-20
good!

and the method i describe of digging for some folder or file starting with a dot, and backing up/restoring it?

those files and folder are called dotfiles. note the dot (.) in ".config".

and they work with ***every*** application.

firefox? it's settings are in .mozilla.
pidgin? it's settings are in .purple. (random, i know)

et cetera. if you cant find an app's dotfiles or dotfolder, make a thread and someone will point it's location out to you.

these dotfiles in your /home are also why it is a good idea to back /home up. ubuntu install cd's are dime-a-dozen, but your personal data and settings are irreplacable. 

in the file manager (nautilus) click view -> show hidden files. dig around and explore the dotfiles in your /home/your-username/ folder.

here is something with dotfiles you want to be aware of, for security reasons.... if you use pidgin, make sure no one is looking over your shoulder and run this command:
```

cat ~/.purple/accounts.xml | grep password
```

yeah. make sure your /home backup dvd/usb/whatever is kept somewhere secure. or encrypted. or both.

---

### Post by bro brian on 2009-10-21
Thanks, EP. I'm getting the "first things first" stuff in my head here. I don't know what pidgin is, but if I ever use it, I will be real careful to watch my back.

---

### Post by earthpigg on 2009-10-21
> **bro brian said:**
> Thanks, EP. I'm getting the "first things first" stuff in my head here. I don't know what pidgin is, but if I ever use it, I will be real careful to watch my back.

it's the instant messenger, so you can talk to your buddies that use MSN, Yahoo Chat, Gmail Chat, etc.

it's in applications -> internet.

---

