---
title: "How do i use xmonad on gnome?"
date: 2009-12-03
forum: Desktop Environments
---

### Post by pedrotuga on 2009-12-03
Instructions in here appear to be outdated/wrong...

[http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_Gnome#Ubuntu_Karmic](http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_Gnome#Ubuntu_Karmic)

There's no entry called 'gnome-wm' in the start up applications menu.

So, how do i disable metacity and replace it with xmonad instead.

Just so i can backup my configurations. Where are the start up apps configurations saved. I guess the answer would be something like 'in gconf'. So, to be clear: which file must i backup if i want to mess around with the start up apps in a way that my DE gets unusable?

---

### Post by semperfizh on 2009-12-07
Yes most documentations are confusing!

I made the following:

1. Install xmonad with all dependences. This is done 
automatically, if you use synaptic package manager. 

2. Create directory .xmonad, i.e. mkdir ~/.xmoand

3. Create  file "xmoand.hs" in ~/.xmonad

4. Put the following into that file with your favorite editor (e.g. vim ~/.xmonad/xmonad.hs):
                import XMonad 
                import XMonad.Config.Gnome

                main = xmonad $ gnomeConfig

5. To test it, open terminal and type "killall metacity ; xmonad &"
Note that if you close that terminal you will turn off xmonad.

6. use mod-<num> to change workspaces, mod-shift-enter to open new terminal, mod-q to recompile it...
mod stays for left alt key.

7. If you like it edit the following file:
"~/.gconf/desktop/gnome/session/required_components/%gconf.xml"
by replacing metacity in the line <stringvalue>metacity</stringvalue>
by xmonad

Next time you log in (Gnome session) you should have xmonad working:)
Edit: Oh and I did this on Ubuntu Karmic (9.10)

Cheers.

---

### Post by pedrotuga on 2009-12-07
Thank you semperfizh.
Nice to see some straight forward information.

I'll get back as soon as i try it out.

---

### Post by semperfizh on 2009-12-07
Anytime; hope it is going to work.

Cheers

---

### Post by pedrotuga on 2009-12-09
wow! it works like a charm. It feels like having the best of both worlds, pretty much all gnome functionality is till there, plus xmonad awsomeness.

I'm loving it, i am defenatly keeping this configuration and recomend it to whomever wants to put a high gear in his/hers productivity on gnome.


I need to make fine adjustments now to fulfill my personal preferences.
Any suggestions on some reading on xmonad configuration?

Is it possible to define extra costumized  tilling algorithms?

In case somebody walks the same path, this cheat is a big help:
```
mod-shift-return      launch a term
mod-p 	              launch dmenu
mod-space 	      cycle through available layout algorithms
mod-c 	              kill a client window
mod-j 	              move focus to the next window on the screen (also mod-tab)
mod-k 	              move focus to the previous window
mod-return 	      swap current window, with window in master pane
mod-shift-j 	      swap current window with its next neighbour
mod-shift-k 	      swap current window with its previous neighbour
mod-h 	              shrink the size of the master pane
mod-l 	              grow the size of the master pane
mod-comma 	      move clients into the master pane
mod-period 	      move clients out of the master pane
mod-q 	              dynamically reload xmonad, with a new configuration
mod-shift-q 	      quit xmonad
mod-1 .. 9 	      move to workspace ("virtual desktop"/"window group") number
'n'
mod-shift- 1 .. 9     move current client to workspace number 'n'
mod- w,e,r            move to Xinerama screens 1, 2 or 3.
mod-r                 launch gmrun
```

---

### Post by m_duck on 2009-12-10
There is a graphic cheat sheet for XMonad [here]("http://haskell.org/haskellwiki/Image:Xmbindings.png") on the [XMonad wiki]("http://www.haskell.org/haskellwiki/Xmonad").

XMonad is a weird beast for configuration (for me, probably not helped by not knowing haskell!) but I've found the best way for figuring out how to get certain bits to work is looking at other peoples configs. A good first step is the step-by-step guide to a basic configuration on the  [XMonad site]("http://xmonad.org/documentation.html"). Also looking at the other configurations on that site is helpful. There are a number of other places for peoples configurations around the 'net as well such as [this thread in the Arch Linux forums]("http://bbs.archlinux.org/viewtopic.php?id=40636"), and of course there is always the [official documentation and references](http://xmonad.org/documentation.html).

---

### Post by semperfizh on 2009-12-10
> **pedrotuga said:**
> wow! it works like a charm. It feels like having the best of both worlds, pretty much all gnome functionality is till there, plus xmonad awsomeness.


Thats what I am talking about! 

> **pedrotuga said:**
> 
Is it possible to define extra costumized  tilling algorithms?


Dont quite understand your question.

---

### Post by pedrotuga on 2009-12-10
> **semperfizh said:**
> 
Dont quite understand your question.

When i start up my computer, after opening a few wintows, xmonad tiles them using the default geometry (aka tilling algorithm). I would like to tune it a bit to define another geometry. For example, making the main area a bit bigger than half the screen.

Also, when I press mod+space, xmonad rotates through three different geometries. How do add more geometries or remove existent ones?

I am also considering rearranging my keybinds to use Ctrl and Alt insteaf of Alt and Shift.

I guess all this should be doable.

---

### Post by semperfizh on 2009-12-13
> **pedrotuga said:**
> When i start up my computer, after opening a few wintows, xmonad tiles them using the default geometry (aka tilling algorithm). I would like to tune it a bit to define another geometry. For example, making the main area a bit bigger than half the screen.

Also, when I press mod+space, xmonad rotates through three different geometries. How do add more geometries or remove existent ones?

I am also considering rearranging my keybinds to use Ctrl and Alt insteaf of Alt and Shift.:

How about this for key bindings. You should probably replace
"defaultConfig" by "gnomeConfig". Didnt test it, googled it:

Editing key bindings 
 
Editing key bindings means changing the XMonad.Core.XConfig.keys field of the XMonad.Core.XConfig record used by xmonad.  For example, you could write: 
    import XMonad

    main = xmonad $ defaultConfig { keys = myKeys }
and provide an appropriate definition of myKeys, such as: 
 myKeys conf@(XConfig {XMonad.modMask = modm}) =
             [ ((modm, xK_F12), xmonadPrompt defaultXPConfig)
             , ((modm, xK_F3 ), shellPrompt  defaultXPConfig)
             ]
This particular definition also requires importing [XMonad.Prompt]("http://xmonad.org/xmonad-docs/xmonad-contrib/XMonad-Prompt.html"), [XMonad.Prompt.Shell]("http://xmonad.org/xmonad-docs/xmonad-contrib/XMonad-Prompt-Shell.html"), and [XMonad.Prompt.XMonad]("http://xmonad.org/xmonad-docs/xmonad-contrib/XMonad-Prompt-XMonad.html"): 
 import XMonadPrompt
 import ...  -- and so on
For a list of the names of particular keys (such as xK_F12, and so on), see [http://hackage.haskell.org/packages/archive/X11/latest/doc/html/Graphics-X11-Types.html](http://hackage.haskell.org/packages/archive/X11/latest/doc/html/Graphics-X11-Types.html) 
Usually, rather than completely redefining the key bindings, as we did above, we want to simply add some new bindings and/or remove existing ones.

---

### Post by pedrotuga on 2009-12-17
meh... too tricky for a simple configuration. I think I'll stick with the default keybind map. I ended up getting used to it anyway, it's easy to memorize. But thank you.

There are some minor glitches:
-the mouse pointer shows in busy state each time I hover a gnome panel or some other kind of widgets which I don't remember ATM.
-some windows like firefox js popups and others, show in a floating layer, i don't know so well how to manage those. sometimes they just get on the way.

Apart from those, it's rather easy to use, though i would only recommend it to ppl with a large screen.

---

### Post by semperfizh on 2009-12-18
> **pedrotuga said:**
> meh... too tricky for a simple configuration. I think I'll stick with the default keybind map. I ended up getting used to it anyway, it's easy to memorize. But thank you.

There are some minor glitches:
-the mouse pointer shows in busy state each time I hover a gnome panel or some other kind of widgets which I don't remember ATM.


Hm... Do you have a slow computer? I cant reproduce that one on
my toshiba r500 laptop.

> **pedrotuga said:**
> 
-some windows like firefox js popups and others, show in a floating layer, i don't know so well how to manage those. sometimes they just get on the way.


Does that happen with many applications?

Anyway, you are right about the big screen and using xmonad.
I, however, use it on my 12,1'' laptop, in which case I use "shift-mod-<num>"
to put my appl. to another desktop number <num>.

About your question on other tiling algorithms:
You can find them (look under layouts) here:
[FONT='PrimaSans BT,Verdana,sans-serif'][http://xmonad.org/xmonad-docs/xmonad-contrib/](http://xmonad.org/xmonad-docs/xmonad-contrib/)[/FONT]
and install them just by including them into your config-file (xmonad.hs).
You should try this one:
[FONT='PrimaSans BT,Verdana,sans-serif'][http://xmonad.org/xmonad-docs/xmonad-contrib/XMonad-Layout-Maximize.html](http://xmonad.org/xmonad-docs/xmonad-contrib/XMonad-Layout-Maximize.html).
"Maximizes" the current app you use.

Cheers.
[/FONT]

---

### Post by pedrotuga on 2009-12-25
Thanks for all the help semperfizh.

My computer is a regular 2 year old laptop:

Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz

I believe the mouse pointer problem has to do with some gnome or xmonad settings or so.

> I, however, use it on my 12,1'' laptop, in which case I use "shift-mod-<num>"
to put my appl. to another desktop number <num>.
That's what i find myself doing all the time. Using xmonad only for that purpose was a bit overkill IMHO. Maximizing all windows and then using Alt-tab gives basically the same functionality.

As for the links, I hope they are of some good use in the future. I might use xmonad in the future. At the moment haskell is uninteligible to me, maybe some time in the future.

I might come back to this topic within a few months.
Thank you for all the help anyway.

---

### Post by nilarimogard on 2009-12-27
I use Bluetile (is based on Xmonad) which is a bit more user-friendly than Xmonad itself  but harder to install: [http://projects.haskell.org/bluetile/](http://projects.haskell.org/bluetile/)

If interested, [this how-to]("http://www.webupd8.org/2009/12/how-to-install-bluetile-in-ubuntu.html") should still work ("still work" because Blutile branch recently merged into Xmonad).

---

### Post by semperfizh on 2010-01-06
> **nilarimogard said:**
> I use Bluetile (is based on Xmonad) which is a bit more user-friendly than Xmonad itself  but harder to install: [http://projects.haskell.org/bluetile/](http://projects.haskell.org/bluetile/)

If interested, [this how-to]("http://www.webupd8.org/2009/12/how-to-install-bluetile-in-ubuntu.html") should still work ("still work" because Blutile branch recently merged into Xmonad).

Interesting project indeed. However I dont see much advantage over classical
xmonad. I think that different installation/configuration makes it a bit confusing.
It should be embedded into xmonad as an option rather than a
different  WM, which has its own configs and installations. 

Thanks for the info :)

Cheers

---

