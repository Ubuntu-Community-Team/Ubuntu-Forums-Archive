---
title: "Setting a default media player?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Rackerz on 2006-06-03
How can I set rhythmbox to be my default media player? When I press the media button on my keyboard it does nothing, this is because no default player is set.

---

### Post by Rackerz on 2006-06-03
Nobody?

---

### Post by Toe on 2006-06-03
right-click on one of your music files , choose properties and select the "open with" tab.
there you can change the default application for this file type.

i don't know whether this will also make your media button work.

---

### Post by PriceChild on 2006-06-03
Maybe going to System>preferences>keyboard shortcuts ?

---

### Post by Rackerz on 2006-06-03
[QUOTE=PriceChild]Maybe going to System>preferences>keyboard shortcuts ?[/QUOTE]

All that does is say that the button will launch a player, not the correct one. That's what I want to change the player it launches with.

---

### Post by justinflavin on 2006-06-03
to change the default player, you have to right click on the mp3 -> properties
-> select "open with" tab 

pick your media player. close.

now single or double click on the mp3 and your preferred player will open up the mp3 file.

---

### Post by hopstah on 2006-06-14
this is an exact problem that i'm having - i know how to change what happens when i double click on any given file, but not how to change what happens when i push the media button on my logitech keyboard.  some help would be awesome!

---

### Post by hopstah on 2006-06-14
i just found a fix for this - creating a symlink to the player by doing this:
```
ln -s /usr/bin/amarok /usr/local/bin/rhythmbox
```

substitute whatever player you want to use in place of amarok and it should work

but use amarok if you're not.  1.4 kicks some serious ... stuff

---

### Post by jacksenechal on 2007-03-04
I would love a solution to this question. When I press the music button on the keyboard it opens up Rythmbox, but I want it to open Amarok. Ideally, this would be set under the System -> Preferences -> Preferred Applications panel. But surely in leau of that there is some configuration file I can hack to change this?

---

### Post by sparks1372 on 2007-03-13
Thanks for the > ln -s /usr/bin/amarok /usr/local/bin/rhythmbox command, worked perfectly but you need to be as a superuser or put "sudo" before the command above for it to be able to work

---

### Post by younus_malik on 2007-06-27
i have dell laptop with mediadirect button on it. i used the following command and it it worked like a charm.


sudo ln -s /usr/bin/elisa /usr/local/bin/rhythmbox

Now my mediadirect button runs elisa instead of crappy dell media experience

Thank you for your support guys :p

---

### Post by BlkDragon96 on 2007-07-06
FYI:  Not sure exactly what is different about my system from the original poster's but I had to use
```
sudo ln -s /usr/bin/amarok /usr/local/[SIZE="6"]_s_[/SIZE]bin/rhythmbox
``` for this to work.  But fear not, work it did.

---

### Post by 6StringKng on 2007-07-10
> **hopstah said:**
> i just found a fix for this - creating a symlink to the player by doing this:
```
ln -s /usr/bin/amarok /usr/local/bin/rhythmbox
```

substitute whatever player you want to use in place of amarok and it should work

but use amarok if you're not.  1.4 kicks some serious ... stuff

wow, thank you so much for this, I LOVE YOU!!!

---

### Post by pvangarde on 2007-07-15
> **hopstah said:**
> i just found a fix for this - creating a symlink to the player by doing this:
```
ln -s /usr/bin/amarok /usr/local/bin/rhythmbox
```

substitute whatever player you want to use in place of amarok and it should work

but use amarok if you're not.  1.4 kicks some serious ... stuff

This is bad. Don't do this. Find a different way to do things than make sym links to trick the system. Next time something upgrades or changes you have to do this again.

---

### Post by revilodraw on 2007-08-20
> **younus_malik said:**
> i have dell laptop with mediadirect button on it. i used the following command and it it worked like a charm.


sudo ln -s /usr/bin/elisa /usr/local/bin/rhythmbox

Now my mediadirect button runs elisa instead of crappy dell media experience

Thank you for your support guys :p

me too, except i did exaile.. thanks heaps!

---

### Post by crjackson on 2007-08-25
Do I need to restart X for this to work?  It changes nothing for me.

---

### Post by ezeebee on 2007-10-24
the way i did this was to run [PHP]gconf-editor[/PHP] from terminal, in the gui that appears, go to apps -> metacity -> keybinding_commands and set "command_1" value to [PHP]amarok[/PHP]

Then go to apps -> metacity -> global_keybindings and set run_command_1 's value to the code for your custom media key or whatever. I'm not sure if there's an elegant way to find this code out, but it will be visible if you have tried to use the limited ubuntu default graphical tool for keyboard shortcuts in System->Preferences. for my logitech wireless keyboard it was 0x81 or something. 

You may need to disable the link to this key if you've already set it up in the default GUI application mentioned above.

I think this method should stay in place despite upgrades but am not sure - as i understand it, now when you press the key, it's just like typing "amarok" into a terminal.  

It will only load one instance of amarok at a time on my machine, which is nice as i was worried that pressing it when amarok was already running would just load another one. Instead it brings the playlist window to the front.  :)

Hope this helps, but if not, forgive me, as i'm pretty noobie.

---

### Post by locketine on 2007-10-24
there we go. I'd like to point out that with the latest ubuntu, gutsy, you can finally select other for prefered media application but you still need to make a link to the amarok executable.....bug?

sudo ln -s /usr/bin/amarok /usr/local/bin/amarok

gets it working while keeping your rythmbox intact.

---

### Post by crjackson on 2007-10-24
> **locketine said:**
> there we go. I'd like to point out that with the latest ubuntu, gutsy, you can finally select other for prefered media application but you still need to make a link to the amarok executable.....bug?

sudo ln -s /usr/bin/amarok /usr/local/bin/amarok

gets it working while keeping your rythmbox intact.

Excellent.  Although I've found that my previous problems with rythmbox box have went away with the install of Gutsy.

---

### Post by Drone4four on 2007-10-29
> **Toe said:**
> right-click on one of your music files , choose properties and select the "open with" tab.
there you can change the default application for this file type.

i don't know whether this will also make your media button work.

I want to change my default media player from totem to beep-media-player.  When I right click on one of my mp3s, I click "open with".  I click "open with other application."  I get a list of apps.  I click "use custom command".  I type "beep-media-player".  I click OK.  Then the next time i click on an mp3, it uses totem.  wtf? how do permanently change my default media player from totem to beep-media-player?

---

### Post by Drone4four on 2007-10-29
bluto20 and scragar in #ubuntu on FreeNode pointed out that all I have to do is right click the file, click "properties", then click "open with" and select the media player of my choice. easy =D

---

### Post by Chymera on 2007-11-05
how exactly do you change your default music player in gutsy?

---

### Post by lebnan60 on 2008-02-10
Not sure if this will solve your problem, but try going to System > Preferences > Preferred Applications.

---

### Post by rainwalker on 2008-02-10
For everyone who is trying to get their multimedia keys to work with whatever player, check out KeyTouch: [http://keytouch.sourceforge.net/download.php](http://keytouch.sourceforge.net/download.php)
I've been using it since Edgy and it's great! Plus, no symlinks involved

---

### Post by AeroGT3 on 2008-04-27
> **lebnan60 said:**
> Not sure if this will solve your problem, but try going to System > Preferences > Preferred Applications.

MUCH simpler than the other fixes posted here, and also better!

---

