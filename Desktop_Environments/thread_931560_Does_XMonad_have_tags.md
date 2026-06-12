---
title: "Does XMonad have tags?"
date: 2008-09-27
forum: Desktop Environments
---

### Post by onero on 2008-09-27
I'm using xmonad 0.7 under GNOME (heresy, I know, but I don't really need a lightweight environment since my PC is fairly powerful, I just like the tiling and other features).

Anyway, as far as I can see the workspaces are set up as numbers. Is there any way I can have user-defined tags, similar to wmii? I like xmonad better, but I like the way wmii implements tags. Thanks in advance!

---

### Post by chucky chuckaluck on 2008-09-29
> **onero said:**
> I'm using xmonad 0.7 under GNOME (heresy, I know, but I don't really need a lightweight environment since my PC is fairly powerful, I just like the tiling and other features).

Anyway, as far as I can see the workspaces are set up as numbers. Is there any way I can have user-defined tags, similar to wmii? I like xmonad better, but I like the way wmii implements tags. Thanks in advance!

you have to do that in an xmonad conf. file. here's an example you can edit and use, storing it as .xmonad/xmonad.hs - [http://haskell.org/haskellwiki/Xmonad/Config_archive/Template_xmonad.hs_(0.7](http://haskell.org/haskellwiki/Xmonad/Config_archive/Template_xmonad.hs_(0.7))

---

### Post by onero on 2008-09-30
Yeah, I actually did that already, thanks :) This seems more like what I was looking for, since I was looking for on-the-fly window tagging: [XMonad.Actions.TagWindows]("http://xmonad.org/xmonad-docs/xmonad-contrib/XMonad-Actions-TagWindows.html")

The problem is, I don't understand the key bindings fully. I read the editing overview, but the config file I was using as a basis used shortcuts like "M-S-g" to mean Modkey-Shift-G. I got that (modMask x, xK_f) is equivalent to "M-f" and so on, but when I try to use the previous format, I get a compile error due to x (in the modMask x statement) not being defined. Which format should I be using for the keybindings?

Additionally, what does the .|. symbol mean? Example: 

(modMask x .|. shiftMask,   xK_f  ) 

I assume that means M-S-f (mod-shift-f). Lastly, what's the modWinMask key? Thanks for the help!

---

### Post by onero on 2008-09-30
Hey, I'm kinda getting the hang of it, I can add and delete tags on windows now, yay! But I don't know how to show all the windows of a given tag :(

Can anybody tell me what function I should use in the aforementioned TagWindows to do this, and how to call it? The focus* methods just shift focus from window to window. Is it supposed to be the withTagged* functions? I don't know how to call them properly though, I keep getting syntax errors.

I have to say though, I'm really enjoying XMonad :) I can't wait to get the kinks worked out. By the way, I still don't understand the keybindings fully, so if anyone could point me to a good overview, that would be great. And if anyone could help me out with the tagging, that would be beyond awesome. Thanks!

---

### Post by mbsullivan on 2008-11-21
Hey onero,

If you're still having problems with focusing tagged windows, post your xmonad.hs file and I'll see if I can give you some keybindings that'll emulate the functionality you want :)

Xmonad under Gnome definitely gives a pretty damn good mix of Gnome's features and ease-of-use with the practical advantages and power of a configurable tiling window manager. I'm a fan.

Mike

---

