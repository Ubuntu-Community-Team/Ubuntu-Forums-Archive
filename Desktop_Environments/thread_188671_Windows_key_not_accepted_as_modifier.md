---
title: "Windows key not accepted as modifier?"
date: 2006-06-04
forum: Desktop Environments
---

### Post by steini on 2006-06-04
Hi,

I'm used to having Windows-Key + [1..4] mapped to the desktops 1..4. However, in Settings->Window Manager, I can't use this combination. At first, it treated the Win key as a normal key press, so when I pressed "Win + 1", it would immediately recognize this as "Super_L", but dismiss the "1". Ok... that should be easy to solve via xmodmap:
xmodmap -e "add mod3 = Super_L"
and maybe a
xmodmap -e "keycode 127 ="
xmodmap -e "keycode 115 = Super_L"
first. But nope, that doesn't work. Now the Super_L is never recognized; when I press "Win + 1" it comes out as just "1". What am I missing here?

Thanks in advance,
  Steini

---

### Post by ebash on 2006-06-04
Go to System > Preferences > Keyboard
Then go to the 'Layout Options' tab  and look under 'Alt/Win key behaviour' choose 'Meta is mapped to the Win-keys.'

Then go to System > Preferences > Keyboard Shorcuts and everything should work as expected.

---

### Post by steini on 2006-06-04
Sorry, but this menu entry doesn't even exist with Xfce...
I figure this might do the same as "setxkbmap -option 'win:meta'", though. Tried it, didn't work :/

---

### Post by loell on 2006-06-04
[QUOTE=ebash]Go to System > Preferences > Keyboard
Then go to the 'Layout Options' tab  and look under 'Alt/Win key behaviour' choose 'Meta is mapped to the Win-keys.'

Then go to System > Preferences > Keyboard Shorcuts and everything should work as expected.[/QUOTE]

xubuntu does not have these menus...

---

### Post by ebash on 2006-06-05
[QUOTE=steini]Sorry, but this menu entry doesn't even exist with Xfce...
I figure this might do the same as "setxkbmap -option 'win:meta'", though. Tried it, didn't work :/[/QUOTE]
I'm sorry I didn't notice that you where using XFCE.

---

### Post by NAbyss on 2006-09-06
After tooling around with XFCE's Keyboard settings for a while, I found a solution. You'll need to manually setup a shortcut theme.

Put this in *~/.config/xfce4/shortcuts/MyStyle.xml*:

```
<?xml version="1.0" encoding="UTF-8"?>
<shortcuts-theme name="Win32">
        <shortcut command="xfce4-popup-menu" keys="Control+Escape"/>
        <shortcut command="xfhelp4" keys="Super+F1"/>
        <shortcut command="xflock4" keys="Super+l"/>
        <shortcut command="xfrun4" keys="Super+r"/>
        <shortcut command="xkill" keys="Control+Alt+Escape"/>
</shortcuts-theme>

```

In this case (as you've already determined with xmodmap), the Windows key is mapped to Super. Unfortunately, the UI for the keyboard settings just doesn't like Super or Hyper at all. However, chucking it directly in the file works just fine.. the above settings make it semi-Win32-like in terms of bindings.

After setting up this file, just jump into the keyboard settings again, and select MyStyle. Easy!

---

### Post by proselyte on 2006-10-12
> **ebash said:**
> Go to System > Preferences > Keyboard
Then go to the 'Layout Options' tab  and look under 'Alt/Win key behaviour' choose 'Meta is mapped to the Win-keys.'

Then go to System > Preferences > Keyboard Shorcuts and everything should work as expected.

well, im using gnome, and the layout options are blank, using xgl/beryl, with  hp dv8000t

EDIT: and the layout options tab is blank.  Thats an awefully important thing to leave out...

---

### Post by jozef.kutej on 2006-11-02
> **NAbyss said:**
> After tooling around with XFCE's Keyboard settings for a while, I found a solution. You'll need to manually setup a shortcut theme.

Put this in *~/.config/xfce4/shortcuts/MyStyle.xml*:

```
<?xml version="1.0" encoding="UTF-8"?>
<shortcuts-theme name="Win32">
        <shortcut command="xfce4-popup-menu" keys="Control+Escape"/>
        <shortcut command="xfhelp4" keys="Super+F1"/>
        <shortcut command="xflock4" keys="Super+l"/>
        <shortcut command="xfrun4" keys="Super+r"/>
        <shortcut command="xkill" keys="Control+Alt+Escape"/>
</shortcuts-theme>

```

In this case (as you've already determined with xmodmap), the Windows key is mapped to Super. Unfortunately, the UI for the keyboard settings just doesn't like Super or Hyper at all. However, chucking it directly in the file works just fine.. the above settings make it semi-Win32-like in terms of bindings.

After setting up this file, just jump into the keyboard settings again, and select MyStyle. Easy!

yes but steini wanted the desktop switching.

launch xfce-setting-show -> window manager -> keyboard -> add -> PROFILENAME

then go to ~/.themes/PROFILENAME/xfwm4/keythemerc and set this:

```

workspace_1_key=Super+1
workspace_2_key=Super+2
workspace_3_key=Super+3
workspace_4_key=Super+4

```

back in xfce-setting-show -> window manager -> keyboard change to default and back to PROFILENAME and the keys should be activeted.

---

### Post by cac on 2006-11-13
> **NAbyss said:**
> After tooling around with XFCE's Keyboard settings for a while, I found a solution. You'll need to manually setup <snip>

Okay this has got me for a loop.  I want to assign <Win>+l and <Win>+r as lock and run, but can't get them to work.  I am on an IBM T23 laptop, which doesn't have a win key per say, but I have a the right Alt key (keycode 113) mapped to Super_R in my xmodmap.  I have tried assigning it using the Keyboard Settings dialog and by manually creating the settings file as suggested, but neither do it.  For what its worth, the Keyboard Settings dialog accepts and shows Super+l when I type it in, which makes me think that XFCE is detecting the key sequence correctly.

My xmodmap is simply:
```
keycode 113 = Super_R
```

xev reports the right Alt is assigned to Super_R:
```
KeyPress event, serial 28, synthetic NO, window 0x2800001,
    root 0x4d, subw 0x0, time 3803068413, (129,-146), root:(552,159),
    state 0x0, keycode 113 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x2800001,
    root 0x4d, subw 0x0, time 3803068556, (129,-146), root:(552,159),
    state 0x80, keycode 113 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
```

Am I missing something?! :confused:

---

