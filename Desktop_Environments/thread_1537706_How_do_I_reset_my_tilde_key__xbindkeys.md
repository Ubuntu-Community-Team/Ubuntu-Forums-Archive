---
title: "How do I reset my tilde key?  xbindkeys"
date: 2010-07-24
forum: Desktop Environments
---

### Post by JonnyPickel on 2010-07-24
So I've made a bit of a mess of things.  I installed Tilda and had it working like a charm.  I bound it to the tilde key (shares a key with ~, maybe it's called grave?) and it was great.

I also have a Logitech MX Revolution mouse and decided to use xbindkeys to fix the thumb wheel which is the only set of actions that doesn't work out of the box.  I decided to set the wheel press action to the tilde key, hoping to have a button on my mouse to open Tilda.

After fumbling around trying to figure out how to identify the tilde key I somehow managed to bind it to xterm.  This wouldn't do.  So in an effort to clear the binding to default I bound it to "".  Well now the key does nothing unless I use it in conjunction with the shift key, in which case it produces the normal ~.

So here's my question: how do I restore that key to it's default function?  I should point out that I just started using Ubuntu 10.04 exclusively a day ago and have had limited experience on Linux before this.

Sorry for the wall of text and thanks in advance!

---

### Post by sgosnell on 2010-07-24
Sounds like you do have it back to its default, which is to produce ~.  If you want to use it to open Tilda, then open Tilda from the Applications menu, right-click on the Tilda window, and select Preferences.  Click on the Keybindings tab, then Grab keybinding, and then press the tilde key, or whatever you want to use to invoke Tilda.

---

### Post by JonnyPickel on 2010-07-24
No that's the thing, I only get a ~ if I use shift-<the key I can't use>.  If I just hit the key it does nothing, and I don't just mean it won't print the weird '-ish character in a text field.  I've tried using the Preferences in Tilda to grab it as the keybinding, but when I press the key the Tilda Preferences box acts like I haven't pressed a key at all.

---

### Post by JonnyPickel on 2010-07-24
Aha!  It seems I had about a billion xbindkeys processes running, so after killing those and Tilda my ` key works again!

I suppose one of those threads for xbindkeys still had ` bound to "" and was taking priority?

---

### Post by sgosnell on 2010-07-24
Dunno.  The grave and tilde characters are bound to the same key, just like 1 & !, and all the other keys.  I've always used a function key for invoking Tilda, usually F10, but whatever works for you...

---

