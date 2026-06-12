---
title: "E1505N Media Direct Button"
date: 2007-06-28
forum: Dell  Ubuntu Support
---

### Post by troy1of2 on 2007-06-28
By default the Media Direct button comes configured to bring up Rhythmbox when pushed which is cool but I was wondering how I might go about configuring it to bring up something else like Amarok or maybe my Last.fm player or whatever if I wanted to. How would I go about doing that?

---

### Post by magicfab on 2007-06-28
Have you tried System &#8211;> Preferences &#8211;> Keyboard Shortcuts ?

---

### Post by mtbsoft on 2007-06-28
On my 9400 under 7.04 the MediaDirect button appears to mapped already.  The entry in Keyboard Shortcuts is listed as "Launch music player" and has the shortcut of 0xed - it fires up RhythmBox automatically.

Hope that helps.

---

### Post by neptho on 2007-06-28
This is a known issue; in the older version of GNOME (last I ran Feisty, it was current) version shipped, it was actually hardcoded to call 'rhytmbox'.  The easiest way to make it launch something else is to reset your paths:   Ensure /usr/local/bin is in your path before /usr/bin, then 

```
%sudo ln -s /usr/bin/amarok /usr/local/bin/rythmbox
```

Replace, of course, with your program of choice.

Alternatively, you can install KeyNote, and override the settings by having KeyNote handle your keyboard; however, under heavy system loads, I've had KeyNote crash and leave me with a functionless keyboard.  That was not fun.. and keep in mind I am not using GNOME so this may have been addressed since that time; I'm happily using amaroK  ;)

---

### Post by mtbsoft on 2007-06-29
Sorry, what I was clumsily trying to say was that I could easily change it through the Shortcuts screen.

I would love to know what keys all the hex codes map to though e.g. 0xec is mapped to e-mail - what the heck is key 0xec?!?!  Can anyone point me to a key mapping table?

---

### Post by neptho on 2007-06-29
> **mtbsoft said:**
> Sorry, what I was clumsily trying to say was that I could easily change it through the Shortcuts screen.

I would love to know what keys all the hex codes map to though e.g. 0xec is mapped to e-mail - what the heck is key 0xec?!?!  Can anyone point me to a key mapping table?

The easiest way is to use xev:

```
KeyRelease event, serial 31, synthetic NO, window 0x1800001,
    root 0x81, subw 0x0, time 8560604, (1161,566), root:(1164,588),
    state 0x0, keycode **160** (keysym 0x1008ff12, XF86AudioMute), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
```

Here's a shortcut to what the keys actually are to save you some time;

```
keycode 160 = XF86AudioMute
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 162 = XF86AudioPlay
keycode 164 = XF86AudioStop
keycode 144 = XF86AudioPrev
keycode 153 = XF86AudioNext
keycode 168 = XF86AudioMedia
```

For others (not yourself, since you're doing it directly):  You may want to map these automatically; I have done it with xmodmap (and xbindkeys previous to handling the application from GNOME/KDE.  Here's how to bind the keys with xmodmap if you don't want to use a local .xmodmaprc:

```
xmodmap -e 'keycode 160 = XF86AudioMute'
xmodmap -e 'keycode 174 = XF86AudioLowerVolume'
xmodmap -e 'keycode 176 = XF86AudioRaiseVolume'
xmodmap -e 'keycode 162 = XF86AudioPlay'
xmodmap -e 'keycode 144 = XF86AudioPrev'
xmodmap -e 'keycode 153 = XF86AudioNext'
xmodmap -e 'keycode 164 = XF86AudioStop'
```

Here's how you can bind them with xbindkeys; note that I had them bound to audacious:

```
"amarok -t"
  m:0x0 + c:162
  XF86AudioPlay
"amarok -s"
  m:0x0 + c:164
  XF86AudioStop
"amarok -r"
  m:0x0 + c:144
  XF86AudioPrev
"amarok -f"
  m:0x0 + c:153
  XF86AudioNext
```

One quick note: If you change your keyboard mapping in /etc/X11/xorg.conf from 'pc105' to 'inspiron' as others have suggested, you'll kill your bindings within GNOME/KDE, so I suggest against that.

---

### Post by mtbsoft on 2007-08-15
Thanks for the info.

---

