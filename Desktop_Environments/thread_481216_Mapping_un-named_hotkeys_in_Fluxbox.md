---
title: "Mapping un-named hotkeys in Fluxbox?"
date: 2007-06-22
forum: Desktop Environments
---

### Post by krandun on 2007-06-22
I'm trying to map some of the media keys from my laptop using the Fluxbox 'keys' file. The problem is that xev returns keycodes for them, but 4 of the keys I want to map are named "NoSymbol". I tried using the keycode in the keys file, but it didn't work. I got other keys to work using their unique names in the keys file, but these don't have unique names.
Can I still map these in Fluxbox's key file, or do I need another app? Or am I going to have to forget about using those 4 keys?

Thank you.

---

### Post by RedSquirrel on 2007-06-22
You need to use xmodmap to setup those keys. Create the file ~/.Xmodmap and put your key settings in there.

Here are some examples:

```
keycode 160 = XF86AudioMute
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 162 = XF86AudioPlay
keycode 164 = XF86AudioStop
keycode 144 = XF86AudioPrev
keycode 153 = XF86AudioNext
keycode 236 = XF86Mail
keycode 229 = XF86Search
keycode 230 = XF86Go
keycode 178 = XF86HomePage
keycode 223 = XF86Sleep
```Here is a guide that is helpful yet not too wordy:

[http://cweiske.de/howto/xmodmap/allinone.html](http://cweiske.de/howto/xmodmap/allinone.html)

gdm is already setup to load ~/.Xmodmap, so if you login with gdm just put your xmodmap settings in ~/.Xmodmap and you're in good shape. If you login to the console and start X from there, just add a line to load ~/.Xmodmap to your ~/.xinitrc.

Once you have those keys setup, you can configure them in your ~/.fluxbox/keys file.

---

### Post by Nythain on 2007-06-23
omg you are my fluxbox hero... thanks for that very informative link on xmodmap and xev... now i can figure out the keycode for my media keys, and set them to what i want them to be

---

### Post by RedSquirrel on 2007-06-23
Glad to help. It is fun to have the media keys *working* rather than collecting dust. :D

For my desktop, the keyboard I'm using has a model that I have specified in xorg.conf so my media keys are setup automatically. I just tell them what to do in ~/.fluxbox/keys. These days, I only use xmopmap to setup "middle-click" on my trackball.

---

### Post by axelabs on 2008-04-22
Fluxbox 1.0.0 supports keycodes in the keys file.  Here are two entries from mine:

```
none 117 :RootMenu
none 222 :ExecCommand xscreensaver-command -lock & sleep 1 && xset dpms force suspend
```

-Bart

---

