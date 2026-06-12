---
title: "Fluxbox - Hotkey for Volume (using Fn key?)"
date: 2007-06-23
forum: Desktop Environments
---

### Post by nightfire117 on 2007-06-23
Hey. Using Fluxbox, the ONLY gripe with it is the volume (and the lack of an alt-tab display, which I can live with). Otherwise I love it!

Anyways. My notebook is a Gateway 450SX4, and in Windows you change the volume using Function+PgUp (for volume up) or PgDn (volume down) or Home (mute). Any way I could accomplish this in Fluxbox?

Here's my ~/.fluxbox/keys file:

```
Mod1 Tab :NextWindow
Mod1 Shift Tab :PrevWindow
Mod1 F1 :Workspace 1
Mod1 F2 :Workspace 2
Mod1 F3 :Workspace 3
Mod1 F4 :Close
Mod1 F5 :Workspace 5
Mod1 F6 :Workspace 6
Mod1 F7 :Workspace 7
Mod1 F8 :Workspace 8
Mod1 F9 :Workspace 9
Mod1 F10 :Workspace 10
Mod1 F11 :Workspace 11
Mod1 F12 :Workspace 12
Mod4 Down :ExecCommand amixer -q set Master 2- unmute
Mod4 Up :ExecCommand amixer -q set Master 2+ unmute
Mod4 m :Maximize
None F13 :execCommand screenshot scr
Mod1 F13 :execCommand screenshot win
```

I use ALSA for the sound drivers. My problem is when I change the volume, for some reason sometimes it changes the BALANCE of what seems to be PCM, because when I reset the balance of PCM by running gnome-alsa-mixer it fixes it. (Although the balance appears to be just fine.... And yes, I use the Gnome ALSA mixer. Until this issue is fixed I won't use the terminal one.) The only thing I've done to configure these keys is modify this file, nothing else.

Anyways, I'm skeptical about installing KDE and testing that out but I will anyways. Um, I'd much rather use Fluxbox as it's configured the way I want it and I've already learned a bit about it. 

Thanks in advance, really, you guys are a great community and have always helped me solve the questions I've asked here.

~Nightfire

---

### Post by kerry_s on 2007-06-23
Been looking for that one myself, i finally just gave up and put wmix in the slit. it's just as easy to move to the far right and scroll on to adjust volume.

---

### Post by der_joachim on 2007-06-23
I am not a fluxbox user, but IIRC, there was an option that has to be set in your xorg.conf. *rummages around* Apparently the option is called AllowBiosHotkeys and it should be in your [Device] section.

---

### Post by kerry_s on 2007-06-23
> **der_joachim said:**
> I am not a fluxbox user, but IIRC, there was an option that has to be set in your xorg.conf. *rummages around* Apparently the option is called AllowBiosHotkeys and it should be in your [Device] section.

nope, tried that 1 to, like i said been through that, it's just easier to hide the volume control and have it pop out when i move the the edge of the screen.

 it just gives this for me->

(WW) NEOMAGIC(0): Option "BIOSHotkeys" is not used

---

### Post by kerry_s on 2007-06-23
aha! i found something that actually works.

sudo apt-get install aumix

Control F3 :Exec aumix -v -5
Control F4 :Exec aumix -v +5

i have mine set to the keys with the volume pic's on my laptop, so you can adjust your keys accordingly.

---

### Post by nightfire117 on 2007-06-23
Awesome, thanks! XD Installed KDE, it's much slower than fluxbox, but after all it's a desktop environment.

Going into Fluxbox to try that now, thanks!

~Nightfire

**[EDIT]:** Heh, thanks, the hotkeys work. When I run the terminal and open up GEDIT from it (I usually do in case I need sudo gedit) I see this line repeating itself in the background:

```
ALSA lib pcm_dmix.c:914:(snd_pcm_dmix_open) unable to open slave
```

Now the sound - at least in Exaile - doesn't work, so, erm, yeah. I'll uninstall aumix and then try something else. =P

~Nightfire

---

### Post by RedSquirrel on 2007-06-23
Just tried it myself in Fluxbox. It works very well. :)

I couldn't get my keyboard's volume keys to work properly and I meant to find a solution at some point, but kerry_s--you've saved me the trouble. Thanks!

Here's what I'm using with my keyboard:

```

XF86AudioMute :Exec aumix -v 0 
XF86AudioLowerVolume :Exec aumix -v -5
XF86AudioRaiseVolume :Exec aumix -v +5

```I didn't see a better way to MUTE other than dropping the volume to 0; if I missed something, please let me know. ;)

EDIT:

I decided to install the gtk version (aumix-gtk)...

---

### Post by nightfire117 on 2007-06-23
I'm having difficulties now. That Aumix thing messed up my ALSA or something since I can't hear anything now. See the post above RedSquirrel's for info. (It's this line that's important: ```
ALSA lib pcm_dmix.c:914:(snd_pcm_dmix_open) unable to open slave
``` - ahhh!)

~Nightfire

---

### Post by kerry_s on 2007-06-23
Hmm, that's weird its not suppose to touch the alsa settings.
run> sudo alsaconf
to reset up your soundcard
then> alsalmixer 
to adjust your settings

---

### Post by nightfire117 on 2007-06-23
Yes, I'm sorry. I was being dumb and didn't even reboot, heh. It's a bad practice on my part to only reboot X and not the whole comp but it works fine now. 

~Nightfire

**[EDIT]:** I may as well try that aumix again. Heh. Even with alsamixer in the terminal it's a hit-or-miss with the centering, I have no idea why. But I'm giving aumix another shot.

~Nightfire

---

### Post by kerry_s on 2007-06-23
> **RedSquirrel said:**
> Just tried it myself in Fluxbox. It works very well. :)

I couldn't get my keyboard's volume keys to work properly and I meant to find a solution at some point, but kerry_s--you've saved me the trouble. Thanks!

Here's what I'm using with my keyboard:

```

XF86AudioMute :Exec aumix -v 0 
XF86AudioLowerVolume :Exec aumix -v -5
XF86AudioRaiseVolume :Exec aumix -v +5

```I didn't see a better way to MUTE other than dropping the volume to 0; if I missed something, please let me know. ;)

EDIT:

I decided to install the gtk version (aumix-gtk)...


the gtk version looks pretty nice. on mine the volume keys are fn-f3 mute and fn-f4+arrow keys up down for volume, of course the fn does not work, so that's why i went the different route. :)

---

### Post by nightfire117 on 2007-06-23
> **kerry_s said:**
> the gtk version looks pretty nice. on mine the volume keys are fn-f3 mute and fn-f4+arrow keys up down for volume, of course the fn does not work, so that's why i went the different route. :)

I just tried the GTK version instead, it works great, thanks! I couldn't figure out how to do Control (or Mod4) + PgUp/Dn so I am using Control + F5 (mute), F6 (vol down), and F7 (vol up) where F8 I will save for future use. (Can't wait until we can map the Fn key. No pun intended.) Works good, thank you. :)

~Nightfire

---

### Post by dxmosiris on 2007-07-04
Aumix  - what a great solution works like a charm. I have been looking for a solution for this for a while.

Nightfire -- 
                   PgUp is Prior 
                   PgDn is Next
                   End is End.

 If you wanted to map those keys. Now all we need is function key support as others have stated!

---

### Post by nightfire117 on 2007-07-09
Heh, yeah, Fn key support. Though I've heard that it's been done with Toshiba (with a special utility) and Acer laptops (using ACPI-something), universal Fn support though unlikely would be good.... I guess we can use the Windows key - hehe. Though I wonder how I would say "PgUp,"" PgDn," "Home," and "End" in that config file - anyone know? Anyways....

~Nightfire

---

### Post by kerry_s on 2007-07-09
It's right above your post. also i ditched aumix for amixer.
if you have problems finding keys you can use xev, just run xev in terminal and press the key it will tell you what it is.
i also i haven't figured out how to use the fn key yet, but i know it works.

My new ~/.fluxbox/keys

```

OnDesktop Mouse1 :HideMenus
OnDesktop Mouse2 :WorkspaceMenu
OnDesktop Mouse3 :RootMenu


Mod1 F2 :Exec fbrun -font Sans-16 -w 500 -h 50 -pos 250 350
Mod1 t :Exec qsynaptics

Mod4 w :WorkspaceMenu
Mod4 s :ShowDesktop
Mod4 t :ToggleDecor
Mod4 Delete :Exec xkill

Control F3 :Exec amixer set PCM 0%
Control F4 :Exec amixer set PCM 100%
Control Prior :Exec amixer set PCM 1%+
Control Next :Exec amixer set PCM 1%-


Control F5 :Exec spicctrl -b0
Control F6 :Exec spicctrl -b255

Control Mod1 Delete :Exec sudo /sbin/reboot

Print :Exec scrot %T.jpg
Home :Exec emelfm
Menu :RootMenu

F1 :Exec iceweasel
F2 :Exec xlinks2 google.com
F3 :Exec pidgin

F12 :Exec xterm


```

---

### Post by nightfire117 on 2007-07-09
Haha, wow, thanks. I didn't even realize I was being so dumb and didn't notice what you meant by 

> "Nightfire --
PgUp is Prior
PgDn is Next
End is End."

Haha, sorry! And thanks for your config, I'll tweak it a bit. =D

~Nightfire

---

### Post by RedSquirrel on 2007-07-10
> **kerry_s said:**
> also i ditched aumix for amixer.

I tried amixer a while ago, but it was misbehaving. Your settings work well. Thanks.

Just in case you hadn't noticed, amixer provides **mute**, **unmute**, and (even better) **toggle**. Here's what I have setup:

```
XF86AudioMute :Exec amixer set PCM toggle
XF86AudioLowerVolume :Exec amixer set PCM 1%-
XF86AudioRaiseVolume :Exec amixer set PCM 1%+

```No need to use two keys for muting/unmuting, and the nice thing is that when you mute, it preserves the volume level you were using.

The Fluxbox keys file syntax has the command **:ToggleCmd**, but we don't need that here since amixer provides its own 'toggle'. :)

---

### Post by kerry_s on 2007-07-10
thanks RedSquirrel,
  i should have mentioned that 1, i went with 2 because i wanted it fully muted or 100%, i didn't use toggle because i didn't want the last level i was at. i think amixer is better though and it doesn't require to install another app just to control sound. also i have to use that extra key for something. :) 1 shows a mute and the other key has the volume up sign, on the sony it has a single key for up and down, your suppose to press fn+f4 and use the up/down arrows, you know finger acrobatics.

i was using that macrocommand 1 for disabling/enabling my touchpad, but i didn't like it, since it runs the commands in a row i had to press it several times and it was hard to tell which it was on. i was going to get all crazy with it and have it throw up a xmessage window for each press to tell me, but i said screw that and just launch qsynaptics.

---

### Post by RedSquirrel on 2007-07-10
> **kerry_s said:**
> thanks RedSquirrel,
  i should have mentioned that 1, i went with 2 because i wanted it fully muted or 100%, i didn't use toggle because i didn't want the last level i was at. i think amixer is better though and it doesn't require to install another app just to control sound. 

I agree. By the way, I realized later that you undoubtedly had a good reason for not using the toggle. I hope my post wasn't too offensive. :oops:

Have you seen anything in your .xsession-errors? I get some entries that don't look like an error, more like "FYI". When I press my keys for volume etc., I get:

```
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 29 [94%] [9.00dB] [on]
  Front Right: Playback 29 [94%] [9.00dB] [on]


```Normally my .xsession-errors is almost empty (a good sign!), but now it's full of this junk.


> **kerry_s said:**
> you know finger acrobatics.

Yeah, I'm doing that right now. I'm finally adding some more stuff to my keys file and it's coming along (bit of a mess at the moment though :)).

---

### Post by kerry_s on 2007-07-10
Yeah, i saw that fixed it with " > /dev/null & "

```
Control F3 :Exec amixer set PCM 0% > /dev/null &
Control F4 :Exec amixer set PCM 100% > /dev/null &
Control Prior :Exec amixer set PCM 1%+ > /dev/null &
Control Next :Exec amixer set PCM 1%- > /dev/null &
```

There's 1 error i been trying to track down for a while " apps file failure ", i have no idea what the heck is failing. it's always there on start before i even open anything, even on a clean install.
I think it's a bug in debian, i see they did something with the background in the changelog.

---

### Post by RedSquirrel on 2007-07-11
Fluxbox is expecting to find the file ~/.fluxbox/apps, so create that and the error should disappear:

```
touch ~/.fluxbox/apps
```

---

### Post by mbsullivan on 2007-07-11
> **nightfire117 said:**
> 
Anyways. My notebook is a Gateway 450SX4, and in Windows you change the volume using Function+PgUp (for volume up) or PgDn (volume down) or Home (mute). Any way I could accomplish this in Fluxbox?


Hi,

It looks like you've got quite a bit of help as to how to change volume... Now, about the Fn key:

I believe that what you want (to use the Fn key as a modifier, and then press PgUp or PgDn to change the volume) may or may not be possible, depending on how your laptop is made. I believe that it would NOT possible on my Thinkpad T20, and I'll tell you why in a bit. But first...

(1) find out what keyname (if any) is given to the function key by running

```
xev
```

and pressing the function key. The output should be something similar to the following (which is from my function key):

```
KeyRelease event, serial 32, synthetic NO, window 0x1000001,
    root 0x3f, subw 0x0, time 1758890, (172,-14), root:(841,22),
    state 0x1, keycode 227 (keysym 0xffe0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

The reason why this won't work with my Fn key is because it only activates upon release (for some reason). If yours is different (has both a KeyPress and KeyRelease event, then we should be in business... Goto step 2...

(2) If your key, (like mine) has no name (the "NoSymbol" part), then follow this step (otherwise, goto step 3):

Decide upon an unused symbol to assign the key to...

(2a) you can see what symbols are in use by observing the output of
```
 xmodmap -pk 
```

(2b) you can see a bunch of valid key symbols by looking at /usr/include/X11/keysymdef.h
 or /usr/share/X11/XKeysymDB.

... for the sake of argument, let's just assign your function key to "F34" by doing one of the following:

(2c) Temporary solution:

```
sudo xmodmap -e "[KEY#]=F34"
```

... where "[KEY#]" is the number of your key (taken from xev).

(2d) Permanent solution:

Add the following line to the end of ~/.Xmodmap (and create it if it doesn't exist):

```
keycode [KEY#] = F34
```

.. which could be accomplished with the following command (among others):

```
echo "keycode [KEY#] = F34" >> ~/.Xmodmap
```

(3) Now that our key has both a number and a name, let's make it a modifier (so that you can put it at the beginning of your fluxbox hotkey commands):

(3a) Get the list of current modifiers by observing the output of:

```
xmodmap
```

If, like me, you don't have a Mod3 defined, use that one! (Otherwise, you'll have to add it to another modifier or something similar.)

(3b) Temporary method:

```
xmodmap -e "add mod3 = F34"
```

(3c) Permanent method:

Add the following line to the end of ~/.Xmodmap (and create it if it doesn't exist):

```
add mod3 = F34
```

.. which could be accomplished with the following command (among others):

```
echo "add mod3 = F34" >> ~/.Xmodmap
```

(4) Now add the volume down / volume up actions to your ~/.fluxbox/keys file using any of the methods mentioned above.

Hope this helps! Let me know if you have any problems.

Mike

---

