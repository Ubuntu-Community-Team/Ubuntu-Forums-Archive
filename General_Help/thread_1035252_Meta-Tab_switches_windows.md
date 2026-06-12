---
title: "Meta-Tab switches windows"
date: 2009-01-09
forum: General Help
---

### Post by snikeris on 2009-01-09
Hi all,

I've been trying to get my keyboard layout the way I want it; but am having some difficulty.

I've used xmodmap to modify my keymappings so that the key with 'Alt' written on it is Meta_L, the windows key is Alt_L, 'Ctrl' is Caps_Lock, and 'Caps Lock' is Control_L.  The expressions I used were:

```
remove Lock = Caps_Lock
remove Control = Control_L
remove mod1 = Alt_L
remove mod1 = Meta_L
remove mod4 = Super_L

keysym Control_L = Caps_Lock
keysym Caps_Lock = Control_L
keysym Super_L = Alt_L
keysym Alt_L = Meta_L

add Lock = Caps_Lock
add Control = Control_L
add mod1 = Alt_L
```

Now, as far as I can tell, xev is reporting that the above expressions accomplish what I intended them to:

Press 'Alt':

```
KeyPress event, serial 31, synthetic NO, window 0x3c00001,
    root 0x8f, subw 0x0, time 10380827, (168,-13), root:(1198,64),
    state 0x0, keycode 64 (keysym 0xffe7, Meta_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

Press (Windows-key):

```
KeyPress event, serial 34, synthetic NO, window 0x3c00001,
    root 0x8f, subw 0x0, time 10382498, (168,-13), root:(1198,64),
    state 0x0, keycode 133 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

However, there are a couple abnormalities:

1) Emacs is recognizing both 'Alt' and the windows key as Meta.  ie. 'Alt'-x & (Windows-key)-x do the same thing.

2)Gnome is switching windows when I press 'Alt'-tab and also when I press (Windows-key)-tab.  Furthermore, 'System->Preferences->Keyboard Shortcuts->Move between windows with popup' seems like it is completely useless.  When you change from the default 'Alt-Tab', pressing 'Alt-Tab' still moves between windows.  Is anyone else getting this behavior?

I'd greatly appreciate some help with these issues.

Regards,
Joe

---

### Post by snikeris on 2009-01-10
Any ideas?

---

