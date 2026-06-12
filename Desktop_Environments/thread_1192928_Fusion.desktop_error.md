---
title: "Fusion.desktop error"
date: 2009-06-20
forum: Desktop Environments
---

### Post by Feelin_froggy8877 on 2009-06-20
I recently created a shell script for compiz stand alone WM/DE. It was working fine until I removed cairo-dock..It was...

#!/bin/bash
compiz ccp &
emerald &         
fusion-icon &
cairo-dock -c

Now It's 
#!/bin/bash
compiz ccp &
emerald &         
fusion-icon 

Since I removed cairo I'm getting the "your last session has lasted only ten seconds"
 Thats the only thing I changed, but not sure If that caused this problem.
I came across one solution about deleting ICEauthority from my home/"user"/ directory. But that did not do the trick.

---

### Post by Locutus_of_Borg on 2009-06-20
for one, you dont need 'compiz ccp' if you are also using fusion-icon

just fusion-icon by itself will start compiz up, and as long as you have emerald in the window decorator option of ccsm, emerald will also start

are you sure cairo was all that got removed?

if you start another session and then run fusion-icon, do you get any errors?

also try starting the compiz session from the text login rather than from GDM/KDM or check /var/log/Xorg.0.log for any errors

---

### Post by Feelin_froggy8877 on 2009-06-21
Thanx for the tips. And actually, When I pasted that here There was something left out and I noticed it after going over the commands again.

#!/bin/bash
compiz ccp &
emerald &
fusion-icon&

HAHA, [&] It didn't get put here and forgot to take it out in the script. Thats what it was. Is it xsession-manager that handles appearance? Is there another way I can set Icons/appearance without running Xsessions-manager.

---

### Post by Feelin_froggy8877 on 2009-06-21
Didn't want to start a new thread for this...And I posting and reading all over the place.(with not much luck) But are there any AntiX users out there that know how to do this under AntiX?

---

### Post by Locutus_of_Borg on 2009-06-21
use lxappearance to manage icons and themes

---

### Post by Feelin_froggy8877 on 2009-06-21
When I add that to my bash script to run at startup, is there a way to force it to the background? So the window does not pop up upon login?

---

### Post by Feelin_froggy8877 on 2009-06-22
Well, it was actually  (gnome-settings-daemon) I was looking for.
I had just manually started gnome-panel opened up appearence properties and checked whet processes were opening up.

 [before]
 
#!/bin/bash
compiz ccp &
emerald &


 [after]

#!/bin/bash
compiz ccp &
emerald &
gnome-settings-daemon

This has go to be the best customization yet! Lovin it.

---

### Post by Feelin_froggy8877 on 2009-06-23
"Update" That command did not work with that script. Ended up getting "your session has lasted less than ten seconds....." Is there something I need to add to the command?

---

### Post by Locutus_of_Borg on 2009-06-23
```
#!/bin/bash
fusion-icon
```

That is all you need, nothing else in the start-up script is needed.

once you have logged into the session, run the command 'ccsm' and select window decorations, insert "emerald --replace" into the 'command' option

then run 'lxappearance' and select your gtk and icon theme

that is all you need to do to retain window decorations, themes, icons, etc



you might, however, want to start some way of launching other applications once inside compiz, either auto-start a terminal emulator, set keybindings in ccsm to launch a terminal emulator, or use compiz-deskmenu to give you a right click menu, as otherwise, you will not be able to open anything once in the compiz standalone session

---

### Post by Feelin_froggy8877 on 2009-06-23
I have all my commands/keyboard shortcuts set. Kinda confused on how to get my themes/icon settings to load at login though.

Upon login, as of right now. I have gmrun set in compiz in commands. I'll open that and then run "gnome-settings-daemon" And all my icon/themes load. Why is it I cant just add that to my script, gnome-settings-daemon that is?

---

### Post by Locutus_of_Borg on 2009-06-23
I have no idea why you need to run gnome-settings-daemon

i dont have to run any such settings daemons

all i have done is once, the first time i logged into my compiz session, ran lxappearance, and ever since then my themes and icons have stayed what i set them to be

theres no reason you cant add that to your script though

```
#!/bin/bash
gnome-settings-daemon&
fusion-icon
```

---

### Post by Feelin_froggy8877 on 2009-06-24
My bad, Wasn't trying to be difficult. :) I'd be happy with whatever works. And so far lxappearance is doing the trick. But was curious as to why I was having a problem adding the daemon to the script.

---

### Post by Feelin_froggy8877 on 2009-06-24
One other thing. My icon and cursor themes are separate in the icons section. I can only choose one or the other. I decided to try to add the aero-drop to my icon theme folder. And then repack it, then install from lxappearance. So far, no good. Any ideas?

---

### Post by Locutus_of_Borg on 2009-06-24
You can set your cursor theme in the ~/.Xdefaults file

Assuming your desired cursor theme is in the /usr/share/icons directory, add the following to the ~/.Xdefaults file, create it if it does not already exist:
```
Xcursor.theme: [Name_Of_Theme]
```

Don't include the brackets, the name is simply the name of the directory that is within /usr/share/icons

you can also set the size with Xcursor.size:

restart X for it to take affect

---

### Post by Feelin_froggy8877 on 2009-06-24
Well, from the looks of it when I started, I had to create .Xdefaults. I was also assuming the file was in my home dir. But either way, didn't work. The name of the dir of my cursor theme is "aero-drop" After creating the .Xdefaults file, there was a second .Xdefaults file created. You'll see it there in the screenshot. It look as though it's an image file. Was that normal?

---

### Post by Locutus_of_Borg on 2009-06-24
I'm sorry, I just looked at my .Xdefaults, the syntax is wrong, it's ```
Xcursor*theme:
```

That is kind of weird that it gets an image mime-type icon, but that shouldn't matter, and the reason a second gets created is because gedit defaults to making a backup of every text file that you modify with it.


Also, just in case, Ubuntu might use the .Xresources file instead of .Xdefaults, so if your settings still do not work after changing the . to a * rename ~/.Xdefaults to ~/.Xresources, then restart X again

---

### Post by Feelin_froggy8877 on 2009-06-24
Appreciate it.  I'll give it a try. Let ya know how it goes in a bit. Been trying to find some documentation on useing cf as stand alone DE, cant seem to find much that go into detail. I'm assuming your running pretty much the same thing here, you ever have a problem with the volume being all the way down at login?

---

### Post by Locutus_of_Borg on 2009-06-24
I ran CF standalone for many months up until recently, now i use openbox primarily

I have a startup script to set my volume levels at boot:

First set your sound levels how you'd like them to be with alsamixer, then run 'sudo /usr/bin/alsactl store'

now put '/usr/bin/alsactl restore' into your 'local' init script, which on Ubuntu I believe is /etc/init.d/local

that should take care of it

---

### Post by Feelin_froggy8877 on 2009-06-24
Had to rename to .Xresources, and then worked like a charm. thanks again man.

---

### Post by Locutus_of_Borg on 2009-06-24
glad to see it's working.  compiz standalone is pretty awesome

you might be interested in compiz-deskmenu: [http://forum.compiz-fusion.org/showthread.php?t=7070](http://forum.compiz-fusion.org/showthread.php?t=7070)

(use the version from post #6 though)

---

### Post by Feelin_froggy8877 on 2009-06-24
Yeah, I'm pretty impressed. And thanx again. Instead of the right click, I been useing keyboard shortcuts, witch is very simple. Checking out the screenlets as widgit layer right now. I noticed they make their owne .desktop file for autostarting. Have any idea how I would work them into the standalone?

---

### Post by Locutus_of_Borg on 2009-06-24
it has been a while since i used screenlets but i think they are simply python scripts, and can be launched straight form the terminal provided you know the path

try to locate the full path to one of them, it is probably something like /usr/share/screenlets/*
or /usr/local/share/screenlets/*

the file in question should be the name of the screenlet with the .py extension, once you have found one, you can launch it from the terminal with 'python /path/to/screenlet.py'

if that does work, you could add that to the fusion.desktop script, though you would probably need to delay it slightly in order to wait for compositing to start

something like the following would likely be sufficient:
```
#!/bin/bash
[other stuff]
(sleep 5 && python '/usr/local/share/screenlets/clock.py')&
fusion-icon
```
for example

just launch each one on a separate line like that one, and note that the sleep time is not incremental, so the next line will not wait 5 seconds

---

### Post by Feelin_froggy8877 on 2009-06-24
Perfect, Although I may not stick with the widget thing. But pretty cool to know. I'll give it a try for a while, see hoe it effects performance. Didnt have no luck with the volume though. read a couple other threads on it. The file "asound.state" is in /var/lib/alsa. And I ended up iseing the command.  sudo alsactl store 0

It did replace the asound file after deleting it, but when i restarted was back to zero. There seems to be alot of posts on this.

---

### Post by Locutus_of_Borg on 2009-06-25
you could try putting the following command into your startup script:
```
amixer set Master 70%&
```

---

### Post by Feelin_froggy8877 on 2009-06-26
Still trying to figure some things out with this. One thing is, My display turns off after about 15 min's in the power management I have it set to never, wouldn't think it would be running anyway, second, I've lost volume control on my wireless keyboard. my play/pause still work for rhythmbox and totem.

The extra command for alsa didn't do it. I'm ona search fora fixthough.

---

### Post by Locutus_of_Borg on 2009-06-26
Check the ServerLayout section of /etc/X11/xorg.conf for any BlankTime options or anything similar.

is it possible a kernel module for your soundcard is not being loaded?

what is it that you have to do after you log in to get sound working?

i would recommend using xmodmap to get your keyboard's volume control buttons to work

first install xev if it isn't already, then paste this into a terminal:```
xev | sed -n 's/^.*keycode *\([0-9]\+\).*$/keycode \1 = /p' | uniq
```
now press each of your volume buttons one at a time.
once you close the xev window that will have popped up, the keycodes for the volume buttons will appear in the terminal
it will look something like:
keycode 136 =
keycode 146 =
keycode 156 =
then simply copy that into the file ~/.Xmodmap and add the corresponding keysyms to each keycode,

for example, if the first button you pressed was volume up, and the first line in the terminal after closing xev was keycode = 113, you would want the following line in ~/.Xmodmap:
```
keycode 113 = XF86AudioRaiseVolume
```
Of course change Raise with Lower for volume down, mute is "XF86AudioMute"
substitute Mute with Play or Stop for the play and stop buttons and Next and Prev for the forward and rewind buttons, if you have them.

just in case it is not already being started by either your profile or your xinitrc, you can put the following line into your startup script to make sure .Xmodmap is being sourced:```
xmodmap ~/.Xmodmap&
```

once doing this, your volume buttons *should* be working

---

### Post by Feelin_froggy8877 on 2009-06-26
Nothing of that nature in my xorg.conf. As for the sound, At first I was manually starting gnome-panel turning up my volume and then ending process on the panel. Although I have tried leaving the panel running and then trying my keyboard controls, thinking it was linked with the panel, but made no difference. Now I have the volume screenlet in my start-up script, keep it as a widgit so I don't have to look at it, haha. But, it's kinda strange, I'm pretty sure the volume controls on the keyboard had worked since I started the standalone. I'll go through the steps you provided and let ya know how it went.

apt-get reports a replacement. "X11-utils".

---

### Post by Feelin_froggy8877 on 2009-06-26
O.k nevermind, I guess x11-utils is actually in turn xev. the command worked just fine.

Whats with the "keycode 8 =" Shows up even if i dont press a button, should I add that to the .Xmodmap file or leave it out?

keycode 121 = XF86AudioMute
keycode 123 = XF86AudioRaiseVolume
keycode 122 = XF86AudioLowerVolume
 And put...
xmodmap ~/.Xmodmap &
 In my start-up script.

Somehow I had some volume at restart, but controlls still don't work.

---

### Post by Locutus_of_Borg on 2009-06-26
dont worry about the 8, i think it is maybe from mouse movement?

i dont know, i get 36 when i dont press anything

okay, I guess we will have to map those keysyms to mixer controls then.

in ccsm, there should be some keybindings options, you can, for the key section, put in the XF86AudioMute/RaiseVolume/etc., and for the command section, use "amixer set Master toggle" for mute, "amixer set Master 3+" for raise volume, and "amixer set Master 3-" for lower volume

if you are running out of keybindings in ccsm, you can install an application called xbindkeys to give you an unlimited amount of keybinding, briefly, after installing xbindkeys, run the following:```
xbindkeys --key >> ~/.xbindkeysrc
``` then press whatever key you want to bind to a command. then open .xbindkeysrc and change where it says "NoCommand" to whatever command you want associated with those keys.   Lastly, run "xbindkeys" by itself and place "xbindkeys&" into the startup script as well.


without anything in your startup script related to alsa, or any mixer settings, or volume control widgets, after logging in, what is the output of "amixer|head -n7"?

---

### Post by Feelin_froggy8877 on 2009-06-26
So I put "XF86AudioRaiseVolume" where it says "NoCommand"? And "XF86AudioLowerVolume" ? A lil confused on this one.


[.xbindkeysrc]

Press combination of keys or/and click under the window.
You can use one of the two lines after "NoCommand"
in $HOME/.xbindkeysrc to bind a key.
"(Scheme function)"
    m:0x0 + c:123
    XF86AudioRaiseVolume

Press combination of keys or/and click under the window.
You can use one of the two lines after "NoCommand"
in $HOME/.xbindkeysrc to bind a key.
"(Scheme function)"
    m:0x0 + c:122
    XF86AudioLowerVolume

I was outta commands for ccsm, but replaced 2 for this purpose. With rhythmbox playing, I can see the highlighted song thats playing kinda flash, as though its receiving a signal for raise and lower, but does not. (no volume change)

---

### Post by Feelin_froggy8877 on 2009-06-26
Here's the output...

 k-dawg@ubuntu:~$ amixer|head -n7
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'Tone',0
  Capabilities: pswitch

Well Volume is up when I first log-in now. Not sure how that came about. Still same results for volume keys. Considering I put what I was supposed to where "NoCommand" was.

---

### Post by Locutus_of_Borg on 2009-06-26
sorry if that didnt quite work out.

in your ~/.xbindkeysrc file, you should have the following:
```

 "amixer set Master toggle"
    XF86AudioMute

 "amixer set Master 3+"
    XF86AudioRaiseVolume

 "amixer set Master 3-"
    XF86AudioLowerVolume

```

and nothing else that isn't at least commented out( # at beginning of line)

with this as your .xbindkeysrc, you can remove the volume bindings in ccsm (compiz does sometimes read keys differently e.g. Page Down vs Prev) but xbindkeys definitely will use the same as xev
then just make sure xbindkeys is running

---

### Post by Feelin_froggy8877 on 2009-06-27
[Bet!] Works like a charm. Appreciate your time man. Any idea's on my display turning off? 

[xorg.conf]

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


BTW, do you play nexuiz?

---

### Post by Locutus_of_Borg on 2009-06-27
the only thing I can think of that might be turning your display off is if 'setterm' or something similar is being started by one of your init scripts, for example, the default Slackware installation has setterm set in /etc/rc.d/rc.M to blank the screen after 15 minutes

I have not played nexuiz yet, but it is one of the games ive been meaning to install now that i have a graphics card capable of playing more than frozen-bubble


glad it's working for you now, feel free to ask me anything should something arise

---

### Post by Feelin_froggy8877 on 2009-06-27
Reason I ask, is I seen a "Locutus" on one of the servers. I just learned about it yesterday, pretty cool game.  Anyway, the display thing isn't that big a deal. The volume issue was, thanx again. Hopefully that will be all for a while.

---

### Post by Feelin_froggy8877 on 2009-07-14
Well, I ended up giving the compiz-deskmenu a try. Adding launchers is not a problem, but how would I add a logout,reboot, maybe even suspend in there ?  I went with this method ...[http://ubuntuforums.org/showthread.php?t=874458](http://ubuntuforums.org/showthread.php?t=874458) fourth post.

---

