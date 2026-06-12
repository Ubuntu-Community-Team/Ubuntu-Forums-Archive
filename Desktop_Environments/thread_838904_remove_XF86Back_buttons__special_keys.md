---
title: "remove XF86Back buttons / special keys"
date: 2008-06-23
forum: Desktop Environments
---

### Post by aot2002 on 2008-06-23
I've seen this site to handle getting the keys to work

[http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work](http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work)

i've got a T61 IBM laptop and those keys annoy me ? where is this stored so i can remap them to NULL

please im gonna smash this keyboard soon

---

### Post by aot2002 on 2008-06-24
no one?

---

### Post by markjensen on 2008-06-24
A little unclear, but did you want keys to WORK?  Or did you want to DISABLE some keys?

Which keys, in particular.   Certainly not the backspace key.  Did you mean you want to disable CTRL+ALT+BACKSPACE from killing/restarting X?

---

### Post by aot2002 on 2008-06-24
I've got two keys forward and backward next to my arrow keys i want to disable them?

i tried looking for xmodmap but im just at loss finding where to change this setting, i only get annoyed by these keys in firefox 3

fyi im on hardy

---

### Post by markjensen on 2008-06-24
Ok, it is a little more clear now that you explained where the buttons are and using your model number from your first post, I guess you are talking about these custom buttons:
[http://www.slashgear.com/gallery/data_files/7/4/IBM_ThinkPad_T61_3.JPG](http://www.slashgear.com/gallery/data_files/7/4/IBM_ThinkPad_T61_3.JPG)

Sounds like you should be able to set up your Gnome keyboard shortcuts and either remove these, or define them to some null task or such.   Unfortunately, I am not much of a Gnome guy, but this may give you enough of a direction to find out where the keybindings/shortcuts are set up in your configuration.

If you are still stuck, I can install Gnome when I get home and play with it a bit.

---

### Post by aot2002 on 2008-06-24
Yes you are correct those are the buttons

and yes im stuck because i went through my gnome shortcut configs and couldn't find any place XF86BACK was located?

i usually find everything i need and have no need to post on the forum but this one has me stumped

---

### Post by markjensen on 2008-06-24
If you run xev, does it show XF86BACK as the key name when you press that funky back button, and some other key when you do the forward?
```
KeyPress event, serial 32, synthetic NO, window 0x2c00001,
    root 0x13b, subw 0x2c00002, time 673831179, (25,27), root:(400,652),
    state 0x0, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False
```(in this case, I pressed the "Super_L" as reported on the third line.

---

### Post by aot2002 on 2008-06-24
back key produces
> 
KeyPress event, serial 27, synthetic NO, window 0x3600001,
    root 0x40, subw 0x0, time 113302595, (597,721), root:(602,770),
    state 0x0, keycode 234 (keysym 0x1008ff26, XF86Back), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 27, synthetic NO, window 0x3600001,
    root 0x40, subw 0x0, time 113302595, (597,721), root:(602,770),
    state 0x0, keycode 234 (keysym 0x1008ff26, XF86Back), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False




Front key does this
KeyPress event, serial 30, synthetic NO, window 0x3600001,
    root 0x40, subw 0x0, time 113326486, (607,674), root:(612,723),
    state 0x0, keycode 102 (keysym 0xff53, Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x3600001,
    root 0x40, subw 0x0, time 113326558, (607,674), root:(612,723),
    state 0x0, keycode 102 (keysym 0xff53, Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

---

### Post by markjensen on 2008-06-24
Have you set up anything with xmodmap yet?   In your link, it mentioned creating an .Xmodmap file.  Have you done this, and can you post what you have?

It sounds like you will want to map them to non-existant F19 and F20, as suggested as an option in the link.

---

### Post by aot2002 on 2008-06-24
i dont have Xmodmap on in /etc/X11/Xmodmap

but i got this one

> 
sudo cat /usr/share/xmodmap/xmodmap.us
! Converted keytable file to xmodmap file
! with mk_modmap by [email]root@chanae.alphanet.ch[/email] vie nov 27 02:24:27 CET 1998
clear Mod1
clear Mod2
!  us.map
!  with some additions from [email]quinlan@spectrum.cs.bucknell.edu[/email] (Daniel Quinlan)
!  14 Mar 1994
keycode   9 = Escape Escape
keycode  10 = 1 exclam
keycode  11 = 2 at at
keycode  12 = 3 numbersign
keycode  13 = 4 dollar dollar
keycode  14 = 5 percent
keycode  15 = 6 asciicircum
keycode  16 = 7 ampersand braceleft
keycode  17 = 8 asterisk bracketleft
keycode  18 = 9 parenleft bracketright
keycode  19 = 0 parenright braceright
keycode  20 = minus underscore backslash
keycode  21 = equal plus
keycode  22 = BackSpace Delete
keycode  23 = Tab Tab
keycode  24 = q
keycode  25 = w
keycode  26 = e E currency
keycode  27 = r
keycode  28 = t
keycode  29 = y
keycode  30 = u
keycode  31 = i
keycode  32 = o
keycode  33 = p
keycode  34 = bracketleft braceleft
keycode  35 = bracketright braceright asciitilde
keycode  36 = Return
keycode  37 = Control_L
keycode  38 = a
keycode  39 = s
keycode  40 = d
keycode  41 = f
keycode  42 = g
keycode  43 = h
keycode  44 = j
keycode  45 = k
keycode  46 = l
keycode  47 = semicolon colon
keycode  48 = apostrophe quotedbl
keycode  49 = grave asciitilde
keycode  50 = Shift_L
keycode  51 = backslash bar
keycode  52 = z
keycode  53 = x
keycode  54 = c
keycode  55 = v
keycode  56 = b
keycode  57 = n
keycode  58 = m
keycode  59 = comma less
keycode  60 = period greater Multi_key
keycode  61 = slash question
keycode  62 = Shift_R
keycode  63 = KP_Multiply
keycode  64 = Alt_L Meta_L
keycode  65 = space space
keycode  66 = Caps_Lock
keycode  67 = F1 F11
keycode  68 = F2 F12
keycode  69 = F3 F13
keycode  70 = F4 F14
keycode  71 = F5 F15
keycode  72 = F6 F16
keycode  73 = F7 F17
keycode  74 = F8 F18
keycode  75 = F9 F19
keycode  76 = F10 F20
keycode  77 = Num_Lock
keycode  78 = Scroll_Lock
keycode  79 = KP_7
keycode  80 = KP_8
keycode  81 = KP_9
keycode  82 = KP_Subtract
keycode  83 = KP_4
keycode  84 = KP_5
keycode  85 = KP_6
keycode  86 = KP_Add
keycode  87 = KP_1
keycode  88 = KP_2
keycode  89 = KP_3
keycode  90 = KP_0
keycode  94 = less greater bar
keycode  95 = F11 F11
keycode  96 = F12 F12
keycode 108 = KP_Enter
keycode 109 = Control_R
keycode 112 = KP_Divide
keycode 113 = Mode_switch
keycode 114 = Break
keycode 110 = Find
keycode  98 = Up
keycode  99 = Prior
keycode 100 = Left
keycode 102 = Right
keycode 115 = Select
keycode 104 = Down
keycode 105 = Next
keycode 106 = Insert
! right windows-logo key
! in "windows" keyboards the postion of the key is annoying, is where AltGr
! usually resides, so go definie it as AltGr
keycode 116 = Mode_switch
! right windows-menu key, redefined as Compose key
keycode 117 = Multi_key
add Mod1 = Alt_L
add Mod2 = Mode_switch


---

### Post by aot2002 on 2008-06-24
I didnt think it would work but it did




jason@jason-laptop:/www$ vim /home/jason/.Xmodmap

jason@jason-laptop:/www$ xmodmap ~/.Xmodmap

jason@jason-laptop:/www$ cat /home/jason/.Xmodmap 
keycode 233 = F19
keycode 234 = F20

---

### Post by markjensen on 2008-06-24
> **aot2002 said:**
> I didnt think it would work but it did




jason@jason-laptop:/www$ vim /home/jason/.Xmodmap

jason@jason-laptop:/www$ xmodmap ~/.Xmodmap

jason@jason-laptop:/www$ cat /home/jason/.Xmodmap 
keycode 233 = F19
keycode 234 = F20

Cool!  Glad you got it working (or "disabled" from working in this case) the way you wanted it. :)

---

### Post by EdSantilli on 2011-08-02
[http://www.streamreader.org/askubuntu/questions/24412/disable-xf86back-and-xf86forward-backforward-on-lenovo-thinkpad](http://www.streamreader.org/askubuntu/questions/24412/disable-xf86back-and-xf86forward-backforward-on-lenovo-thinkpad)

That did it for me.

---

