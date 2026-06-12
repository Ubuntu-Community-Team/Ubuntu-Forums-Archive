---
title: "Compiz Config Settings Manager"
date: 2008-02-18
forum: Desktop Effects &amp; Customization
---

### Post by mattstakilla on 2008-02-18
Okay so i got compiz working and the wobble windows and cube all working. What im trying to do is change the way windows open and close but when i go to animations to switch it, i get stuck

i accidentally deleted what was there already. instead of changing what was there.

now what i have is 

close effect          duration                  windows match
burn                    500                        (type=Normal)

how do i choose other closing options and what other windows matches are there? is there a list or easier way to select them,

---

### Post by mbailey90 on 2008-02-18
start>system>preferences>advance desktop effects settings

---

### Post by mattstakilla on 2008-02-18
> **mbailey90 said:**
> start>system>preferences>advance desktop effects settings

i got that far. im inside that, if anyone has anything that could help me, it would be greatly appreciated.

i need to know the names of windows for the animation selection

---

### Post by merlinDwizzard on 2008-02-18
once inside animations click on effect then click edit, you should see some arrows to the right, click on that to reveal a drop down list to chose from different effects here is what mine says,[COLOR="MediumTurquoise"]close effect beam up 200 window match((type=Normal | Utility | Unknown ) | name = sun-awt-X11-XFramePeer | name=sun-awt-X11XDialogPeer) & !(role=toolTipTip_l role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver). [/COLOR]

---

### Post by mattstakilla on 2008-02-18
wow, does anyone read what im writing. i need the windows names. like drop down. normal, and **** like that. i have everything else. effect and stuff. i need the name of windows.

---

### Post by Triggerhapp on 2008-02-18
Oh god. I just made a fool of myself as well :D
ok here goes. Close Animation : 
```

Effect    Duration
Glide 2  200 ((type=Normal | Utility | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)
Fade 150   (type=Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog | Normal)
Fade 150 (type= Tooltip | Notification)
```

---

### Post by mattstakilla on 2008-02-18
> **Triggerhapp said:**
> Hey forgive me im half asleep by now, so if i misunderstood you too, please hit me.
I assume this is what you're after.

```
Toolbar | Menu | Utility | Dialog | Normal | Unknown
```

That's the window list that I use for wobble, as far as i recall, its what came with the install

Oh stupid me I just gave you the wrong list. Updated

perfect, thats what im looking for. so menu would be the drop down menu like for applications?

---

### Post by merlinDwizzard on 2008-02-18
sorry, i had to edit, i typed in everything mine has listed, it should be what you need. Just go back and look at my post again. it took me a second to realize what you were asking

---

### Post by Triggerhapp on 2008-02-18
I would assume so. my experience at these window lists so far is the hack/slash approach known better as copy and paste.
Anything more I could help with in this area? :)

---

