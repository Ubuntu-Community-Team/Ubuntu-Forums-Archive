---
title: "How can I disable pasting via middle mouse button?"
date: 2005-08-25
forum: Desktop Environments
---

### Post by tsteuerwald on 2005-08-25
Hi all,

can please anybody help?  :roll: 

This is the mouse section in my xorg.conf file:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "false"
        Option          "ZAxisMapping"          "4 5"
EndSection

``` 

Cheers,

Timo

---

### Post by tsteuerwald on 2005-09-05
This issue is still unresolved.  :?

Cheers,

Timo

---

### Post by Pikapooh on 2005-09-05
Lol, I was thinking about the same problem, so I open ubuntuforums.org, and voila - second post fom the top "How can I disable pasting via middle mouse button?" :DDD.

Anyway, it is little-but-annoying thingie. I have habit of clicking middle mouse button in Opera to bring new tab. When I do it under Linux current clipboard content (silly and random usually) is pasted in location bar. I ask Mr.Google few times but w/o results...

So.. any ideas?

---

### Post by Galoot on 2005-09-05
[QUOTE=Pikapooh]I have habit of clicking middle mouse button in Opera to bring new tab. When I do it under Linux current clipboard content (silly and random usually) is pasted in location bar. I ask Mr.Google few times but w/o results...

So.. any ideas?[/QUOTE]
Yeah. Change habits.  :grin:

In Opera:
[list]
[*]Double-clicking on a blank area of the page bar opens a new, blank page.
[*]Mouse gesturing (down) opens a new, blank page.
[*]CTRL+N opens a new, blank page.
[*]Re-enabling the "New Page" icon that you disabled because it's dumb, then clicking on it, opens a new, blank page.
[/list]

I don't know of a way to disable middle-click pasting. It's built into X.

---

### Post by Pikapooh on 2005-09-06
Heh, I use Ctrl-N or LMB doubleclick... but MMB is more handy :D.

Ok, it looks that I must live with this weird 'feature' :x

---

### Post by Lollipop on 2005-09-06
It might be possible with the imwheel package - no guaranty though

---

### Post by MaX on 2005-09-06
Try to learn how to paste with the middle mouse instead, it works in 9/10 applications for linux.
You'll miss it like hell in windows afterwards.

---

### Post by progressnerd on 2007-11-13
Any solution yet? I prefer my middle-button to just scroll. When I'm scrolling in my text editor, the middle button is so sensitive, that I wind up pasting everywhere. It sucks. Please tell me how to disable it.

---

### Post by maniaq on 2008-04-10
has anyone got an answer beyond "get used to it" for this?

I too click the middle mouse button by accident all hte time and randomly pasting stuff into my documents is UNACCEPTABLE!

I'd rather disable the damn thing than have it perform some function I HATE...

---

### Post by maniaq on 2008-04-10
ok - in answer to my own question - 

replace the emulate3button option in your xorg.conf file with this:

Option "ButtonMapping" "1 1 3 4 5"

this remaps the middle button into the left button, essentially turning the middle-click into a left-click!

no more random pastes!

---

### Post by lowsignal on 2008-04-18
hello,

i had the same problem myself with the middle mouse click in opera. here's what to do...

in the url or address bar, type in... "opera:config" then scroll down to near the bottom of the page to "user preferences" and click on it. then scroll down to "center mousebutton action". look to the right and there should be a number there (proabably 2). click on the "up" arrow to set the number to '5'. the number 5 will set the mouse to do nothing with the middle click button. you will need to restart opera for the change to take effect.

---

### Post by lowsignal on 2008-04-18
well it worked with setting the number to '5' for a while and then it reverted to its old ways just after i made my post here. ok.... i did the same operation setting the number to '4' this time. so far it is working, but now i don't trust that it won't revert.

before i changed the number i checked user prefs again and it was still on 5. it didn't go back to 2. so it's a mystery to me why the action reverted to as if the setting were 2. anyway. it is working on '4' at this time and the action hasn't changed back yet. i'll upate the thread if for some reason it reverts again later.

---

### Post by lowsignal on 2008-04-24
maniaq,

i think i found another answer that might be easier for people that aren't used to programming. check it out and see what you think..

---------------

how to disable middleclick (or 'wheelclick') in the mouse for opera, epiphany or swiftweasle (and proabably firefox).


first opera:

type 'opera:config' in the url or address bar and hit enter.

scroll down and click on 'user prefs'

scroll down to 'center mouse action' and set that number to '6'.
[B][U]
THEN[/U][/B] scroll further down to 'extended mouse action' and set that number to '2'.

scroll to the bottom and click on 'save'.

---------------------

next is for both epiphancy and swiftweasle (and probably firefox).

type 'about:config' in the url or address bar and hit 'enter'.

scroll down to:

middlemouse.contentLoadUrl and doubleclick on it to make it 'false'. 

do the same for:

middlemouse.openNewWindow

and

middlemouse.paste

close the tab and you're finished. middle mouseclick (or 'wheelclick') has been disabled.

--------------------------

---

