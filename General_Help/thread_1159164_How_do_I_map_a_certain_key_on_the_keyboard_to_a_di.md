---
title: "How do I map a certain key on the keyboard to a different function"
date: 2009-05-14
forum: General Help
---

### Post by bcasanov on 2009-05-14
Hi!  I have an Acer Aspire One with a French Canadian keyboard set up.  As you can see in the picture below, [IMG]http://static.zooomr.com/images/5591202_07da1b3d43.jpg[/IMG] 
the left shift key has less than ideal space.  I would like to make the key immediately to the right of the left shift key a left shift key also (in other words, if I pressed that key, it would function as a shift key).  I would also like the key that says "Alt Car" to function exactly like the Alt key to the left does.  I would appreciate any help you can give me.

---

### Post by BslBryan on 2009-05-14
Hello. :-)

Forgive me, because I do not know terribly much about the solution I can provide, but I know that xmodmap can do precisely what you're asking. ```
sudo apt-get install xmodmap
```
:-)

---

### Post by bcasanov on 2009-05-14
How do I use xmodmap?

---

### Post by BslBryan on 2009-05-14
Firstly, sorry for the vague reply, I was on my phone, and for some reason it only lets you input 200 characters of text. :roll:

Anyway, I know that, once downloaded, in /etc/X11, you'll find /xmodmap.  This is where you put all of your key bindings.  

I, however, do not want to chance screwing you up here, so I would seriously suggest looking for a tutorial on Google.

I'm so sorry I couldn't have been of greater help.  

Please do post any problems here, and I will help to my greatest ability.

Best to you, and good luck. :-)

---

### Post by bcasanov on 2009-05-14
I used the xev program to find out my keycodes and keysyms, but I don't know which is which, and I am kind of confused as to how to change the keysyms from the instructions I found in the xmodmap man page.  The following is the xev output (only the KeyPress event) for:

-The left shift key:

KeyPress event, serial 35, synthetic NO, window 0x4200001,
    root 0x9a, subw 0x0, time 32548143, (66,-14), root:(740,12),
    state 0x0, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

-The key to the right of the left shift key:

KeyPress event, serial 32, synthetic NO, window 0x4200001,
    root 0x9a, subw 0x0, time 32681579, (-73,293), root:(601,319),
    state 0x0, keycode 94 (keysym 0x3c, less), same_screen YES,
    XLookupString gives 1 bytes: (3c) "<"
    XmbLookupString gives 1 bytes: (3c) "<"
    XFilterEvent returns: False

-The left Alt key:

KeyPress event, serial 35, synthetic NO, window 0x4200001,
    root 0x9a, subw 0x0, time 32895648, (-534,391), root:(140,417),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

-The "Alt Car" key:

KeyPress event, serial 35, synthetic NO, window 0x4200001,
    root 0x9a, subw 0x0, time 32987575, (-235,347), root:(439,373),
    state 0x0, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


From my assumption of what I have read in the xmodmap man page instructions, the commands I would use are:

xmodmap -e "keycode 94=Shift_L"
xmodmap -e "keycode 108=Alt_R"

Are these correct for what I intend?

---

### Post by BslBryan on 2009-05-14
As I have never used xmodmap or xbindkeys, I'm not sure.  I would try to map a key to a key that you have no use for, to see if it works.  If it does, then try to map it to the correct key.

Keep us posted.

---

### Post by bcasanov on 2009-05-14
The second command I listed worked!  I now have an Alt key on the right that works immediately.  I did not need to log out or anything.  The first command, however, did not work.  When I pressed the key I wanted changed (keycode 94) and tried to make an uppercase letter, it did not work at all.  When I press the key by itself, nothing happens (no character appears on screen in a text field).  The xev output when I press the key is:

KeyPress event, serial 32, synthetic NO, window 0x4200001,
    root 0x9a, subw 0x0, time 38664432, (-200,433), root:(474,459),
    state 0x0, keycode 94 (keysym 0xffe1, Shift_L), same_screen YES,
    XKeysymToKeycode returns keycode: 50
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

---

### Post by bcasanov on 2009-05-15
bump

---

### Post by bcasanov on 2009-05-18
This issue was resolved by this post: [http://ubuntuforums.org/showpost.php?p=7298453&postcount=4](http://ubuntuforums.org/showpost.php?p=7298453&postcount=4)

---

