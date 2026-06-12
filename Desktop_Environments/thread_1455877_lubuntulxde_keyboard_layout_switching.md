---
title: "lubuntu/lxde keyboard layout switching?"
date: 2010-04-16
forum: Desktop Environments
---

### Post by michael.conner on 2010-04-16
I'm using lubuntu 10.04 beta 2. I've read wikis on xkb and various other topics related to switching keyboard layouts *without* the use of a dedicated applet (as lxde doesn't seem to yet have one) and really cannot figure out how to set up keyboard layout switching.

I want to be able to switch keyboard layouts between English and German while holding down the CAPSLOCK key -- in other words, just for typing German characters such as ö, ä, ü, and ß. I don't want to switch completely to the German keyboard. 

The solution I'm using right now works and is somewhat inelegant: I installed xfce4-panel and xfce4-xkb-plugin, started xfce4-panel, added the keyboard layouts plugin, then removed everything BUT the keyboard layout plugin, set it to "normal width" and "auto-hide." So it just hangs out on the very margin of my screen and lets me switch keyboard layouts like I want to do.

Is there an easier way to do this natively without using the xfce4 panel? Granted, it's not like a little xfce4 applet takes up a lot of memory.

---

### Post by mikewhatever on 2010-04-16
I've used lxde last summer, not Lubuntu though, and the following worked for switching layouts.
[http://ubuntuforums.org/showthread.php?t=1039107](http://ubuntuforums.org/showthread.php?t=1039107)

It's not quite what you want, but a short in the right direction.

---

### Post by michael.conner on 2010-04-19
> **mikewhatever said:**
> I've used lxde last summer, not Lubuntu though, and the following worked for switching layouts.
[http://ubuntuforums.org/showthread.php?t=1039107](http://ubuntuforums.org/showthread.php?t=1039107)

It's not quite what you want, but a short in the right direction.

Thanks... I'd seen that one, couldn't really figure out how to get there from here, if you know what I mean. I ended up just doing a minimal netboot install and installed a "minimal-enough" XFCE desktop for my purposes.

---

### Post by mikewhatever on 2010-05-03
> **michael.conner said:**
> Thanks... I'd seen that one, couldn't really figure out how to get there from here, if you know what I mean. I ended up just doing a minimal netboot install and installed a "minimal-enough" XFCE desktop for my purposes.

Should have PM`ed me for clarifications, anyway, hope you're enjoying xfce minimal.
I've been testing Lubuntu-10.04 in a Virtual Box today, and there is still no straightforward way to switch keyboard layouts. Apparently, after issuing the following command switching English and Hebrew layouts worked:

```
setxkbmap -option grp:ctrl_shift_toggle "us,il"
```

Just some notes:
I used Ctrl_Shift and not Alt_Shift, because the latter was set too, and switched keyboard layouts on the host machine.
The layout setting survived several virtual machine restarts.
Found [another way]("http://foo-gr.blogspot.com/2010/04/keyboard-layout-configuration-for.html"), but it didn't work.

---

### Post by Dreiggy on 2010-10-22
> **mikewhatever said:**
> Should have PM`ed me for clarifications, anyway, hope you're enjoying xfce minimal.
I've been testing Lubuntu-10.04 in a Virtual Box today, and there is still no straightforward way to switch keyboard layouts. Apparently, after issuing the following command switching English and Hebrew layouts worked:

```
setxkbmap -option grp:ctrl_shift_toggle us,il
```

Just some notes:
I used Ctrl_Shift and not Alt_Shift, because the latter was set to, and switched keyboard layouts on the host machine.
The layout setting survived several virtual machine restarts.
Found [another way]("http://foo-gr.blogspot.com/2010/04/keyboard-layout-configuration-for.html"), but it didn't work.

but this dont work after system restarting... Maybe is better way?

---

### Post by 3Miro on 2010-10-22
You can make that into a script that runs as a startup application. It is a bit more involved in LXDE than say Gnome, but it can be done. Try finding documentation about startup applications under LXDE.

---

### Post by GrouchyGaijin on 2010-10-26
I use a really cool utility called Auto Key to paste in phrases I often use, like my email address or home address.
The problem is that Auto Key doesn't recognize when I switch keyboard layouts using the panel applet. This results in the ä in my address, for example, being dropped.

I need to use setxkbmap

I can type setxkbmap us or setxkbmap se in a terminal window to change the layouts, but I'd realy like to have a hot key or launcher to do this. How can I set up a hot key or launcher to run the setxkbmap command?

I know it involves a Bash file, but I'm lost as to the specifics.
I'm running Gnome in Ubuntu 10.10

I also noticed that if I just use setxkbmp us all the characters above the number keys (! @ etc) stop working.  Any ideas on what I need to change so that these work?



I'd appreciate any help.

---

### Post by nomnex on 2010-12-12
To add a keyboard layout using LXDE (change "jp" for your default, and "ch(fr)" for your second layout):

```
setxkbmap -layout "jp,ch(fr)" -option "grp:alt_shift_toggle"
```Copy the command at the end of your /home/user/.bashrc file. The file is hidden by default. (see sample below)

```
# .bashrc

# Source global definitions
if [ -f /etc/bashrc ]; then
    . /etc/bashrc
fi

# User specific aliases and functions

setxkbmap -layout "jp,ch(fr)" -option "grp:alt_shift_toggle"
```Log-out/in.

---

### Post by mörgæs on 2011-02-05
Thanks Nomnex, it works fine. 

The method extends to more than two languages:

```
setxkbmap -layout "dk,is,fr" -option "grp:alt_shift_toggle"
```

---

### Post by hallboy3 on 2011-05-21
open file /etc/default/keyboard and add necessary options:

```

XKBMODEL="pc105"
XKBLAYOUT="us,ua,ru"
XKBVARIANT=","
XKBOPTIONS="grp:ctrl_shift_toggle,grp_led:scroll"

```

than restart X session

---

### Post by jards on 2011-05-24
Thanks, nomnex, it works fine for me to.

---

### Post by TheStefan12345 on 2011-07-02
> **hallboy3 said:**
> open file /etc/default/keyboard and add necessary options:

```

XKBMODEL="pc105"
XKBLAYOUT="us,ua,ru"
XKBVARIANT=","
XKBOPTIONS="grp:ctrl_shift_toggle,grp_led:scroll"

```

than restart X session

How to put in both serbian cyrillic and serbian latin keyboards?

---

### Post by jablan on 2011-10-11
> **TheStefan12345 said:**
> How to put in both serbian cyrillic and serbian latin keyboards?

Try this way:

```

XKBMODEL="pc105"
XKBLAYOUT="us,rs,rs"
XKBVARIANT=",latin,"
XKBOPTIONS="grp:ctrl_shift_toggle,grp_led:scroll"

```

poz.

---

### Post by amjjawad on 2011-10-12
Old Thread :)

---

### Post by kvalvik01 on 2011-10-19
Thank you nomnex and hallboy! Both your versions work well on my Lenovo S10-2 - until I switch off or reboot, that is. Although the inserted commands are still there (in bashrc, resp. in the keyboard-layout), alt_shift doesn't toggle the keyboard anymore.

Any advice? ty

upate:

I did both, now it works; my next problem is how to switch from latin script to hiragana, katakana and kanji in japanese - I installed anthy from the synaptic packet manager, but that hasn't had any effect so far

Any advice

---

### Post by Neosano on 2011-10-23
And the easiest solution is to add this line to /etc/xdg/lxsession/Lubuntu/autostart

@setxkbmap -option grp:alt_shift_toggle "us,ru"


so simply type this into your terminal and it's going to be ok after restart.
```

echo '@setxkbmap -option grp:alt_shift_toggle "us,ru"' | sudo tee -a /etc/xdg/lxsession/Lubuntu/autostart

```

---

### Post by absurdus_delirium on 2011-11-10
> **Neosano said:**
> And the easiest solution is to add this line to /etc/xdg/lxsession/Lubuntu/autostart

@setxkbmap -option grp:alt_shift_toggle "us,ru"


so simply type this into your terminal and it's going to be ok after restart.
```

echo '@setxkbmap -option grp:alt_shift_toggle "us,ru"' | sudo tee -a /etc/xdg/lxsession/Lubuntu/autostart

```

Thanks guys! Worked like a charm! I'm just posting this reply because when I first pasted the code into my terminal I didn't change the "us,ru" part so I ended up successfully toggling english and russian. Only problem is I am Greek! O_o
I tried re-entering the code with the proper changes but it didn't seem to matter. What I found out when I checked /etc/xdg/lxsession/Lubuntu/autostart was that each time I ran the code through the terminal a new line was added at the end of the file but it just ignored anything past the "us,ru" one. So, if you find yourself in the same situation, edit the file and leave just the part of the code you need. In my case it is ```
@setxkbmap -option grp:ctrl_shift_toggle "us,gr" 
``` because I prefer switching with ctrl+shift.

---

### Post by nomnex on 2011-11-10
the easiest way it to use ibus input (you can set most languages and keyboards in the prefs.), else look at the arch wiki lxde, you will get all the answers, and more, along this thread.

there is a keyboard layout configuration on the way for lxde

---lxde list---
Gabriel thanks for your corrections. 

The main difference between lxkb-config and lxkeymap is that lxkeymap is wrote in python what makes it consume more resources. The version that you see is quite immature in fact it is just the version 0.1 by the next two weeks I will be working on it. 


TODO list: 
- Add test box to try the layouts 
- Upgrade the UI (not gtk 3 yet*) 
- Upgrade system integration (add .desktop file to the package) 
- Add "model selection" functionality 
- Add "options and shorcuts selection" functionality 
- Complete the package documentation (I need help here!) 

** I'm not going to take the application right now to gtk3 because the lxde desktop is not in GTK 3. But i will do it in the future. 

Greetings

---

### Post by dajare on 2011-11-28
I can get the keyboard "toggle" working well, using something like:

```
setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll gb,ar,ru
```My questions: 
(1) how to set up a "hot-key" to **switch** (rather than "toggle") to a different keyboard layout?
(2) how to use "alt + [num]" combinations as the "hot-key"?

The scenario is having several (even many) different lang/kbds available  from the press of a key-combo. Using "toggle" to cycle through 5, 10, 15+  options is not realistic.

What I've found (in addition to this useful thread): for (1), a [BodhiLinux forum thread]("http://forums.bodhilinux.com/index.php?/topic/286-toggle-between-two-keyboard-layouts/") with useful kbd toggling information; and for (2) some info on [using xev to determine the keybinding name]("http://crunchbanglinux.org/wiki/xev-determine_custom_keybindings").

Unfortunately, when I use something like:

```

setxkbmap -option grp:switch,grp:alt_1_toggle gb
setxkbmap -option grp:switch,grp:alt_2_toggle ar
setxkbmap -option grp:switch,grp:alt_3_toggle ru

or

setxkbmap -option grp:switch,grp:alt_1_switch gb etc. ...

```(or substitute "Alt_L" for "alt" in the lines above) (these are my best guesses), I don't get the switch action - perhaps because the hotkey combination isn't accessible in the new keyboard? Maybe?

I don't know! But I hope someone does. Thanks for any help with this!

**Bonus**: How nice would it be to have some [means of displaying]("http://awesome.naquadah.org/wiki/Change_keyboard_maps") the current language/keyboard? (Answer: very nice!)

---

### Post by nomnex on 2011-12-06
> **dajare said:**
> I can get the keyboard "toggle" working well, using something like:

I use Fedora. The path on Ubuntu might be different. For a list of all the options:

       /usr/share/X11/xkb/rules/xog.lst

---

### Post by dajare on 2011-12-09
> **dajare said:**
> My questions: 
(1) how to set up a "hot-key" to **switch** (rather than "toggle") to a different keyboard layout?
(2) how to use "alt + [num]" combinations as the "hot-key"?


In doing a recent forum search, [the "obkey" announcement]("http://ubuntuforums.org/showthread.php?t=1883847") came up as a hit. Does exactly what's need! Hope this is a help to others looking to use hotkeys to **switch** keyboard layouts rather than **toggle** them. Works for me!

---

### Post by nomnex on 2011-12-09
dajare, why don't you simply rely on ibus for your different input languages?

Ctrl + Space turns ibus on
Alt+Shift switches input languages

---

### Post by dajare on 2011-12-10
> **nomnex said:**
> dajare, why don't you simply rely on ibus for your different input languages?

Because I didn't know I could? ;) And in large part the point is *not* to cycle through language options, but to be able to switch immediately to any one of a dozen or more possibilities.

> **nomnex said:**
> 
Ctrl + Space turns ibus on
Alt+Shift switches input languages

And this appears to do nothing on my setup. Obviously I'm doing something wrong -- but hard to know what that might be! :confused:

**Update:** That would be because ibus isn't installed. ... :rolleyes: I'm still not sure it will do the any-to-any *switching*, though, as opposed to cycling through options. Can anyone confirm?

---

### Post by nomnex on 2011-12-11
> **dajare said:**
> to switch immediately to any one of a dozen or more possibilities.

Do you need that many languages? You can use 4 different keyboard layouts in i-bus.

> I'm still not sure it will do the any-to-any *switching*, though, as opposed to cycling through options. Can anyone confirm?You can define your shortcuts*. Or you can use your mouse, and left-click to change language.

* next/previous input language

---

### Post by paulkiss on 2012-05-24
> **Neosano said:**
> And the easiest solution is to add this line to /etc/xdg/lxsession/Lubuntu/autostart

@setxkbmap -option grp:alt_shift_toggle "us,ru"


so simply type this into your terminal and it's going to be ok after restart.
```

echo '@setxkbmap -option grp:alt_shift_toggle "us,ru"' | sudo tee -a /etc/xdg/lxsession/Lubuntu/autostart

```Thanks, man, you saved me!

---

