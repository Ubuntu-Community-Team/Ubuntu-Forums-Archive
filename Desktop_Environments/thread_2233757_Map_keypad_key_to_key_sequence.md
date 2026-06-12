---
title: "Map keypad key to key sequence"
date: 2014-07-10
forum: Desktop Environments
---

### Post by Zoot_Nerper on 2014-07-10
Hi Folks,

I am trying to map a key on the keypad to a key sequence. So, if I press "1" (End) on the keypad, I want the sequence "Alt_L + 1"

I am using Ubuntu 14.04

I have been using xev to find the key code. I get this:

[INDENT]KeyRelease event, serial 125, synthetic NO, window 0x6c00001,
    root 0x299, subw 0x0, time 43140241, (107,121), root:(1849,173),
    state 0x0, [COLOR=#ff0000]keycode 87 (keysym 0xff9c, KP_End)[/COLOR], same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
[/INDENT]

Then I kill xbindkeys and then restart it passing it a file with the following lines:

[INDENT]"xte 'keydown Alt_L' 'key 1' 'keyup Alt_L'"
  c:87
[/INDENT]

But this does not work. xev shows a different output when I press the keypad "1" as follows:


[INDENT]FocusOut event, serial 126, synthetic NO, window 0x6c00001,
    mode NotifyGrab, detail NotifyAncestor

MappingNotify event, serial 126, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

FocusOut event, serial 127, synthetic NO, window 0x6c00001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 127, synthetic NO, window 0x6c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 127, synthetic NO, window 0x0,
    keys:  4294967193 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

[/INDENT]
So, something is happening, just not what I want.

I have used xev and xbindkeys before to successfully assign a key sequence to a mouse button.

Any ideas?

Thanks

---

### Post by Zoot_Nerper on 2014-07-10
Ooops!


Well, it appears I can use Custum Shortcuts in the keyboard settings.

I can click the Plus sign to bring up an edit window, enter a name (a descrition), put the xte command in the command entry, hit Apply. Your name for the shortcut appears at the left end of the row and "disabled" on the right

The help at the bottom of the window says "click on the row and hold down the new keys"

Clicking on the row just pulls up the edit window again. So you go round in circles for a bit wondering what it is that you have done wrong.

Turns out if you click on the word "Disabled" at the right end of the row, **then** you can enter the keys you want.


Maybe you can do it with xbindkeys too, but I will give up on that front. Spent enough time finding a solution.

Sorry, if my post seemed a mite pointless given that the solution is in "Settings". I did search with Google and tried different possible solutions.

---

