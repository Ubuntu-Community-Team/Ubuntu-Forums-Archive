---
title: "Compiz Fusion Keybindings using extra keyboard keys"
date: 2007-08-24
forum: Desktop Effects &amp; Customization
---

### Post by 00l0 on 2007-08-24
hi,
i would like to assign some of my extra keyboard keys as keybindings in the CCSM. Ubuntu's hotkeys configurator(system-preferences-hotkeys) recognizes those extra keys and gives me some address (0x74, 0x81....), how can i use those keys in compiz fusion?
i searched around the forums but couldn't find the answer, also i posted a thread in compix fusion forums, but no luck  ;(

thank you!

---

### Post by Romanus81 on 2007-11-22
Hey, I figured this out, if you still need help with it.
With me it was some extra keys on my keyboard, namely, the zoom in and out buttons.

**Finding Keycode with xev**

Type xev into terminal.
It will bring up a small box, press the key you want to use, and look at the output. It should say something like
```
KeyRelease event, serial 31, synthetic NO, window 0x3400001,
    root 0x87, subw 0x3400002, time 1709139522, (31,59), root:(702,109),
    state 0x10, **keycode 148** (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```If it gave an answer for keycode, then skip ahead. If not, read below;

**Binding your key to a key code**

I pressed one button, and typed "dmesg | grep atkbd.c:" into terminal, this gave me this error at the bottom
> 
[  823.228832] atkbd.c: Unknown key pressed (translated set 2, code 0x**XY** on isa0060/serio0).
[  823.228840] atkbd.c: Use 'setkeycodes **XY** <keycode>' to make it known.

XY should be the two letters or numbers, such as 6b or 71
Then type into terminal
```
xmodmap -pke >~/.xmodmap
```
This will print all the keycodes and what they are bound to and place it into a hidden file callled .xmodmap in your home directory.
Then
```
gedit ~/.xmodmap
```
Toward the end look for some numbers that are not bound to anything, there should be plenty.
Then type into terminal. (root privileges needed)
```
sudo setkeycodes XY ABC
```
ABC should be the keycode you found in the .xmodmap file, XY should be the letters dmesg gave you.

NOTE: The lines you type should be placed in your ~/.bashrc file so that they are set at startup. If you don't do this your keys won't work when you restart your PC.
**Bind your keycode to a button**

If you haven't done so, export your xmodmap settings.
```
xmodmap -pke >~/.xmodmap
```
and open the file
```
gedit ~/.xmodmap
```
Then edit your keycode lines, DEF and ABC are variables, and should be the keycode found in xev or the one you bounded to it.
```
keycode ABC = Meta_L
keycode DEF = Meta_R
```
and this line at the end.
```

add mod4 = Meta_L Meta_R
```

Meta is a key not found on many keyboards, L and R tells your computer if you pressed the left or right one. You can also use Hyper_L and Hyper_R, if you have none, or use no hyper keys. There may be more, but you will have to find that yourself.

Load the changes.
```
xmodmap ~/.xmodmap
```

Finally, go into the compiz config settings manager and find the keys you want to bind, in my case, I wanted my zoom in and zoom out buttons to flip my cube, so I went to the rotate cube plug in and for the "Key" collum I double clicked until it gave me a screen where I could type it in myself (you could try typing gconf-editor in terminal, going to apps, compiz, and edit it from there, too) and I typed in Meta_R and Meta_L. Worked like a charm.
If it worked, place this script into the ~/.bashrc file:
```
# Only run xmodmap if logging into an X session
if [ ! -z "$DISPLAY" ]; then
    # Don't run xmodmap in VNC, it breaks the keymap.
    xvendor=`xdpyinfo | head -n3 | tail -n1 | cut -d: -f2`
    if [ "$xvendor" != "    AT&T Laboratories Cambridge" ]; then
        xmodmap $HOME/.xmodmap
    fi
fi
```
The script and a lot of the help came from these topics:
[http://everything2.com/index.pl?node_id=490903](http://everything2.com/index.pl?node_id=490903)
[http://forum.compiz-fusion.org/showthread.php?t=5290&highlight=extra+keys](http://forum.compiz-fusion.org/showthread.php?t=5290&highlight=extra+keys)

---

### Post by 00l0 on 2007-11-22
> **Romanus81 said:**
> Hey, I figured this out, if you still need help with it.
With me it was some extra keys on my keyboard, namely, the zoom in and out buttons.

**Finding Keycode with xev**

Type xev into terminal.
It will bring up a small box, press the key you want to use, and look at the output. It should say something like
```
KeyRelease event, serial 31, synthetic NO, window 0x3400001,
    root 0x87, subw 0x3400002, time 1709139522, (31,59), root:(702,109),
    state 0x10, **keycode 148** (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```If it gave an answer for keycode, then skip ahead. If not, read below;

**Binding your key to a key code**

I pressed one button, and typed "dmesg | grep atkbd.c:" into terminal, this gave me this error at the bottom

XY should be the two letters or numbers, such as 6b or 71
Then type into terminal
```
xmodmap -pke >~/.Xmodmap
```
This will print all the keycodes and what they are bound to and place it into a hidden file callled .Xmodmap in your home directory.
Then
```
gedit ~/.xmodmap
```
Toward the end look for some numbers that are not bound to anything, there should be plenty.
Then type into terminal
```
setkeycodes XY ABC
```
ABC should be the keycode you found in the .xmodmap file, XY should be the letters dmesg gave you.

**Bind your keycode to a button**

If you haven't done so, export your xmodmap settings.
```
xmodmap -pke >~/.Xmodmap
```
and open the file
```
gedit ~/.xmodmap
```
Then edit your keycode lines, DEF and ABC are variables, and should be the keycode found in xev or the one you bounded to it.
```
keycode ABC = Meta_L
keycode DEF = Meta_R
```
and this line at the end.
```

add mod4 = Meta_L Meta_R
```

Meta is a key not found on many keyboards, L and R tells your computer if you pressed the left or right one. You can also use Hyper_L and Hyper_R, if you have none, or use no hyper keys. There may be more, but you will have to find that yourself.

Load the changes.
```
xmodmap ~/.Xmodmap
```

Finally, go into the compiz config settings manager and find the keys you want to bind, in my case, I wanted my zoom in and zoom out buttons to flip my cube, so I went to the rotate cube plug in and for the "Key" collum I double clicked until it gave me a screen where I could type it in myself (you could try typing gconf-editor in terminal, going to apps, compiz, and edit it from there, too) and I typed in Meta_R and Meta_L. Worked like a charm.
If it worked, place this script into the ~/.bashrc file:
```
# Only run xmodmap if logging into an X session
if [ ! -z "$DISPLAY" ]; then
    # Don't run xmodmap in VNC, it breaks the keymap.
    xvendor=`xdpyinfo | head -n3 | tail -n1 | cut -d: -f2`
    if [ "$xvendor" != "    AT&T Laboratories Cambridge" ]; then
        xmodmap $HOME/.Xmodmap
    fi
fi
```
The script and a lot of the help came from these topics:
[http://everything2.com/index.pl?node_id=490903](http://everything2.com/index.pl?node_id=490903)
[http://forum.compiz-fusion.org/showthread.php?t=5290&highlight=extra+keys](http://forum.compiz-fusion.org/showthread.php?t=5290&highlight=extra+keys)

omg that really is a reply!

thanks!

---

### Post by hotdoog on 2008-04-29
That's an awesome reply 00l0, thanks!

It's pretty dissappointing how convoluted the keybindings are however. I don't understand why we can't have on authoritative place to put this that can be simplified. All I want to do is change my ctrl-alt-del to gnome-system-monitor. It shouldn't be this hard. I use to use automatix because I was lazy with metacity and with compiz it is confusing as to what is authoritative. But now automatix won't work for hardy.

This is the thing that I hate about gnome. They lock out development of vital things like this because they want to only allow their own vision.

KDE is ugly. But I'm considering trying it again if this solutions of yours doesn't work for me. Really ubuntu should be looking at this. Keybindings and fonts don't need to be rocket science. I wish I could do some work on those things but I have no idea how to program anything except bash scripts.

---

### Post by hotdoog on 2008-04-29
Well I couldn't figure out xev. But then I took another look at CompizConfig and found that it has a General>General Options>Command menu which lets you assign keys reasonably. So yay for them! I still don't want to mess with the metacity vs compiz issues so I just decided to put gnome-system-monitor on Ctrl-Del and leave ctrl-alt-del as it is. I'll have to relearn my habits but its ok for now.

The compiz general options is nice and i guess I should whine less. But it ain't gnome that did it. AND I still think there should be a simple config file backend somewhere for cases when it gets tricky.

---

