---
title: "Custom keyboard map is causing issues with stuck keys"
date: 2010-05-16
forum: Desktop Environments
---

### Post by Grumbel on 2010-05-16
I have a Microsoft Ergonomic 4000 keyboard and I am running a custom keymap (dvorak with some stuff for umlauts):

  [http://pingus.seul.org/~grumbel/tmp/md5/b054e11505c88e1bfc6ebd5da46bdb78-xmodmap_pke](http://pingus.seul.org/~grumbel/tmp/md5/b054e11505c88e1bfc6ebd5da46bdb78-xmodmap_pke)
  [http://pingus.seul.org/~grumbel/tmp/md5/f5e42a5b8ba4a034c5945f719b3d2608-xmodmap_pm](http://pingus.seul.org/~grumbel/tmp/md5/f5e42a5b8ba4a034c5945f719b3d2608-xmodmap_pm)

This used to work fine for years and it still does, except that I am having issues with a stuck Mode_switch key. When I hit Control_R and Mode_switch at the same time (happens a lot by accident), the Mode_switch key gets into a 'stuck' state, all letters I type afterwards come out in their umlaut form as if Mode_switch is pressed. I can unstuck the Mode_switch by again hitting Control_R and Mode_switch at the same time, but that leaves Gnome in a broken state where it doesn't react to my Gnome keyboard shortcuts any longer. The key presses themselves are still registered by the window manager as one can see changes in the applications (cursor in Gnome Terminal will turn into an unfilled rect, as if the application lost focus), but don't trigger the bound action.

Does anybody have a clue what could be causing this? Or does anybody has an idea how I could debug this?

xev doesn't seem to help here, as it is reporting normal KeyPress/KeyRelease events, even when the key is stuck and Gnome is in the 'broken' state.

I am using Ubuntu 10.04 with Gnome and Metacity.

---

### Post by shusai on 2010-09-17
I have a very similar problem. I am using Japanese keyboards and as I have to type German text from time to time I assigned the umlauts like this:

```
keycode  30 = u U udiaeresis Udiaeresis
keycode  32 = o O odiaeresis Odiaeresis
keycode  38 = a A adiaeresis Adiaeresis
```

The Windows-keys are made mode_switch using
```
keycode 133 = Mode_switch Mode_switch
keycode 135 = Mode_switch Mode_switch
```

This worked great for many years and also with different PCs but with Ubuntu 10.04 the problem with the stuck mode_switch started.

It happens only with the right Windows-key (keycode 135) pressed together with any shift key.

It can be reproduced like this:

First I press slowly the right Windows-key (keycode 135), then one of the shift-keys and keeping both pressed finally "a", "u" or "o" and voila - mode_switch is stuck. 

To release it, I have to press the right Windows-key (keycode 135) after a second or two a shift key and then "a", "u" or "o".

The mode switch does not get stuck or can be released when the keys are pressed very rapidly, it needs a few seconds.

As I could not find a solution yet, I had to disable the right mode_switch... :(

---

### Post by arided on 2010-11-10
Similar issue here, but in my case the AltGr layer stops working, rather than getting stuck in an "always-on" mode.  This seems to only apply to keycodes mapped in the third layer, e.g. it applies to

```
keycode  39 = o O Left
```

which then simply produces an "o" when Mode_switch+o is pressed (it should result in "Left").

I experienced the issue under both Gnome and Ratpoison on Ubuntu 10.04, and again under Ratpoison on 10.10 -- I've found that xmodmap breaks as described above in all cases...  Bummer because I use Xmodmap to give myself lots of modifier keys in order to save my wrists!  It's hard to type (especially code) without my "standard" enhancements.  (See [http://metameso.org/~joe/config/dvorak-plus.modmap]("http://metameso.org/%7Ejoe/config/dvorak-plus.modmap") for details.)

---

### Post by roger.keays on 2011-12-14
I have the same problem and found this workaround:

```
$ setxkbmap -layout us
```Read "[Alt-Tab Shortcuts Broken In Ubuntu Lucid With XModMap]("http://www.ninthavenue.com.au/alt-tab-shortcuts-broken-in-ubuntu-lucid-with-xmodmap")" for more details.

---

