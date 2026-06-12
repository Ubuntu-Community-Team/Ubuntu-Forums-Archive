---
title: "setxkbmap not working"
date: 2015-10-02
forum: Desktop Environments
---

### Post by joe.koenig on 2015-10-02
I'm trying to apply my own xkb-layout 'us_de'.  As this didn't work
out as expected, I tried the bare-bones 'setxkbmap' command, in
order to narrow it down.  However, it doesn't seem to work.

```
$ setxkbmap -query
    rules:      evdev
    model:      pc105
    layout:     us
    variant:    ,
    options:    grp:shift_caps_toggle
$ setxkbmap -layout fr
$ setxkbmap -query
    rules:      evdev
    model:      pc105
    layout:     us
    variant:    ,
    options:    grp:shift_caps_toggle
$ setxkbmap -layout "jp,ch(fr)" -option "grp:alt_shift_toggle"
$ setxkbmap -query
    rules:      evdev
    model:      pc105
    layout:     us
    variant:    ,
    options:    grp:shift_caps_toggle
```

Any ideas?  Does it maybe have something to do with this ominous
'ibus' system?  I tried to 'killall -9' it, but my system froze :o)

Thanks for your attention
Joe

Lubuntu

 ```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty
```

I've been through the usual suspects:
[http://duckduckgo.com/?q=lubuntu+setxkbmap](http://duckduckgo.com/?q=lubuntu+setxkbmap)
[http://help.ubuntu.com/community/Lubuntu/Keyboard](http://help.ubuntu.com/community/Lubuntu/Keyboard)

I'm ashamed to admid that I've even rebooted my machine due to this
problem.

However, I still assume it has something to do with this ubiquitous
'IBus' thingy.

I 'apt-get remove'`d it.  I  called up 'im-config' and set

 -->  'none' - do not set any IM from im-config

Which doesn't seem to do anything. The radio-list is un-selected,
everytime I call up 'im-config'.  No option is being
selected/kept/saved.   I.e.: as if I've never set it to
  -->  'none' - do not set any IM from im-config

---

### Post by sudodus on 2015-10-14
I booted a live session from lubuntu-14.04.3-desktop-amd64.iso.

It works for me to change the keyboard with

```
setxkbmap se
setxkbmap de
setxkbmap us
```

If this does not work for you, you have tweaked something (or possibly some program package is upgraded).

-o-

If you want German language installed (not only the keyboard), you should use the menu options

*Preferences -- Language Support*

and

*Preferences -- Keyboard input methods (ibus) -- Input method -- (tick Customize active input methods) -- Select an input method -- Add*

Good luck :-)

---

### Post by joe.koenig on 2015-10-14
> **sudodus said:**
> I booted a live session from lubuntu-14.04.3-desktop-amd64.iso.
Thanks for all the effort,mate.

 ```
setxkbmap de
```

Hmpf.  I wish it was that easy.  As stated before, the whole point of my posting was/is that 'setxkbmap' doesn't work the way it's supposed to do.  Not german (de) not swedish (se) and most certainly not my own XKBLayout "us_de"

```
If this does not work for you, you have tweaked something (or possibly some program package is upgraded).
```

  You're probably right.  I can almost remember having it tweaked to the manner I meant it to be.  Dunno how I did that.  Shame

```
If you want German language installed (not only the keyboard), you should use the menu options
```

Now you're over-simplifying, again :-)

---

### Post by sudodus on 2015-10-14
Sometimes it is easier to re-install than to repair a system that is not working.

I don't know what you want or what you expect to work, but for me it is straightforward to change the key mapping with setxkbmap. You can

1. Work with a persistent live system in a pendrive until you have something that works the way you want.

2. Or if you have enough drive space: Install a second system alongside your current Lubuntu, and work with this second system until you have something that works the way you want.

Start again with a fresh system, if you come to a 'dead end street'. Simplifying - *yes*, but over-simplifying - *no*.

---

### Post by joe.koenig on 2015-10-14
>  Sometimes it is easier to re-install than to repair a system that is not working.
No self-respecting man would ever reboot a system. Let alone reinstalling it :) Just kidding

 I'll probably bootstrap Arhchlinux in the near future, as it's the one I'm accustomed to.  (BTW: have any of you guys beeb using "~/home" as a seperate ditsinctive partition?  Sucks, right?

 Back on topic: You catching my drift at all?  It's not a about a single, specific XKBLayout that can not be loaded.  None can.  Not the german (de), not the swedish (se) and most certainly not my homenbrewn 'us_de'"

  It's setxkbmmap.  setxkbmmap DOES NOT WORK (respectively: I'm too dumb) on my system.  Or at least that's the way it appears to me.

The pendrive sugggestion is a bit offensive, dontcha think?  (Edit: No, I dont' think so, either)

Thanks again, Buddy

---

### Post by sudodus on 2015-10-14
> **joe.koenig said:**
> No self-respecting man would ever reboot a system. Let alone reinstalling it :) Just kidding

I'll probably bootstrap Arhchlinux in the near future, as it's the one I'm accustomed to.  (BTW: have any of you guys beem using "~/home" as a seperate ditsinctive partition?  Sucks, right?

I don't use it. I use a separate **data** partition instead. But I know many people who do, and they are happy with a separate home partition. It makes upgrading to a new version easier.
> 
 Back on topic: You catching my drift at all?  It's not a about a single, specific XKBLayout that can not be loaded.  None can.  Not the german (de), not the swedish (se) and most certainly not my homenbrewn 'us_de'"

  It's setxkbmmap.  setxkbmmap DOES NOT WORK (respectively: I'm too dumb) on my system.  Or at least that's the way it appears to me.

The pendrive sugggestion is a bit offensive, dontcha think?

Thanks again, Buddy

I really think that it is worthwhile to test in a fresh and separate system. Play with a system, where you have not invested much time and effort.

When you have something working, you might be able to port it to your 'production system'. If not, you can be rather sure, that there is something (a program package, a setting) in your production system, that is not working with the new tweaks (that you made working in the fresh system).

---

### Post by joe.koenig on 2015-10-14
> **sudodus said:**
> I don't use it. I use a separate **data** partition instead. But I know many people who do, and they are happy with a separate home partition. It makes upgrading to a new version easier.

Sure, sure.  Sounds reasonable.  However, ditstros tend to compile and package their software in th their own unique fashion.  So, my carefully groomed ~/.config/emelfm2/ might be being rendered useless once I switch from Archlinux to Lubuntu.

---

### Post by sudodus on 2015-10-14
That's right. It would be risky to share or port a home partition to another distro, maybe even to another flavour of Ubuntu.

---

### Post by joe.koenig on 2015-10-14
> **sudodus said:**
> It would be risky to share or port a home partition to another distro

 Well, let's put put it into persperctive, shalln't we?  It's not life-threatening, after all :o)

   ... unless I'm trying to type an "Emergency Alert Message" (Crimson Tide) which is supposed to contain german umlauts.  In which case I'd be screwed. (Adding to the supposition that Vim doesn't support digraphs)

---

### Post by sudodus on 2015-10-14
pupil: Goethe was a great poet.

teacher: [SIZE=3]oe[/SIZE] is pronounced [SIZE=3]ö[/SIZE].

pupil: Göte was a great pöt.

---

### Post by joe.koenig on 2015-10-14
It's supposed to be a joke, right?  Sorry, I'm not getting this one.  Even though I'm a native german speaker :o)

---

### Post by sudodus on 2015-10-15
It is a joke about umlauts, spelling and [too] general conclusions.

In this case also an exercise in typing [SIZE=3]ö[/SIZE].

-o-

Back to the topic of this thread:

Did you try if ```
setxkbmap de
``` works in a [persistent] live session or a fresh installed system of Ubuntu or an Ubuntu flavour?

You mentioned Arch. Are you trying to make it work in an Ubuntu flavour or in Arch?

---

### Post by oui on 2015-10-16
I did install lubuntu yesterday and find no way to select my keyboard layout (us intl, the best keyboard for West-European languages, available in hardware realisation made by fujitsu-Siemens).

but setxkbmap works definitiv well within each new session using the CLI in x-terminal-emulator (clone of Sakura or Sakura itself...): The special-char's appears also in the CLI windows and, of course, in the other: [SIZE=7]äöüáéïóúèêæœçßñãõ«» ...&#472;[/SIZE] (this last is one special double accent char for pinjin = Latin written Chinese!). The signs for magyar etc. are also available (but I am not able to remember how in the moment)...

---

