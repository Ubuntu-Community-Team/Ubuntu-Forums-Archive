---
title: "Delete key suddenly invokes Print Screen application in place of deleting..."
date: 2008-02-04
forum: Desktop Environments
---

### Post by motin on 2008-02-04
My delete key works as the print screen button. This is mighty annoying since I usually press delete a few times in a row now and then and the computer have to process opening a lot of save screenshot dialogues. 

I think this started happening because I have connected a wiimote which I use now and then, but this issue remains even after the wiimote is disconnected. 

I have no other key than the print screen button mapped through keyboard shortcut properties, the problem persists without having xbindkeys running, and the keyboard layout and type are all set to default pc105 and swedish layout as they should. 

The xev events for Print Screen and Delete respectively:

```
KeyPress event, serial 27, synthetic NO, window 0x3400001,
    root 0x88, subw 0x0, time 3839988540, (336,265), root:(340,313),
    state 0x0, keycode 111 (keysym 0xff61, Print), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x3400001,
    root 0x88, subw 0x0, time 3839988597, (336,265), root:(340,313),
    state 0x0, keycode 111 (keysym 0xff61, Print), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

```
KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  4294967293 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

LeaveNotify event, serial 30, synthetic NO, window 0x3400001,
    root 0x88, subw 0x0, time 3839934221, (107,169), root:(111,217),
    mode NotifyGrab, detail NotifyNonlinear, same_screen YES,
    focus YES, state 0

EnterNotify event, serial 30, synthetic NO, window 0x3400001,
    root 0x88, subw 0x0, time 3839934221, (107,169), root:(111,217),
    mode NotifyUngrab, detail NotifyNonlinear, same_screen YES,
    focus YES, state 0

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  4294967293 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  
```

How can I restore my Delete key?

Thanks for any help!

---

### Post by Monohielo on 2008-02-05
Unfortunately, I don't have any help for you, but I would like to add to the problem.  I am using a Logitech MX3100 keyboard/mouse combo with evdev and I have almost the same exact problem, with the exception of my "trigger" key being the up arrow.  If I disable the Num-Lock, the arrow key there functions as normal.  

Any help would be appreciated.

Thanks.

---

### Post by Monohielo on 2008-02-05
I think I might have a little help.  Apparently, while configuring my Screenshot keyboard shortcut in System->Preferences->Keyboard Shortcuts, I had set they screenshot key to my "PrintScreen" Button.  Something in the hardware config must have my Up Arrow and the PrintScreen mapped to the same keycode, because after I removed the shortcut for the PrintScreen, my Up Arrow works the way it should.

Surprisingly, though, my PrintScreen does not function the same as my Up Arrow.

---

### Post by motin on 2008-02-05
You're right - you had a little help ;)

Changing the key combination to another one for taking a screenshot (Ctrl + F12 instead of Print screen) makes the Delete key behave as usual!

Now this is enough for now - it's 97% less irritating...

One thing I have realized is that it works perfect for other users on the system - so it must be some kind of user setting somewhere. 

Thanks this far!

Anyone have some more light to shed upon this strange user keyboard issue?

---

