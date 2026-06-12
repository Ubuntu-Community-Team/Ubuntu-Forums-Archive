---
title: "Hide menu item in grub"
date: 2009-03-22
forum: General Help
---

### Post by arod529 on 2009-03-22
The following entry in *menu.lst* makes me think that I can makke a boot choice hidden. Does anyone know how? I typed "hiddenmenu" on the line before the entry but had to boot to the cd and remove the line because it wouldn't boot anymore.

## hiddenmenu
#Hides the menu by default (Press esc to see the menu)
# hiddenmenu

Sorry if this is in the wrong place, I couldn't rally find a boot catagory.

---

### Post by unutbu on 2009-03-22
When your menu.lst contains the word
```

hiddenmenu
```

Then you don't get the see the GRUB menu unless you press ESC during boot.

I think the option you want is the 
```

howmany=NUM
```

option. Count how many **different** kernels you wish to see, and use that number for NUM. For example, if you use
```

howmany=1
```

then you will see the first boot option, and its associated recovery mode.

---

### Post by sakamoto on 2009-03-22
just remove # on the 3rd line and do this as root

sudo gedit /boot/grub/menu.lst

this will make the whole menu hidden. if you just want to hide specific lines, use # before the appropriate lines in menu.lst

---

### Post by arod529 on 2009-03-22
I was hoping to make an entry still acessible but temporarily invisible like sakamoto said to do with the whole menu.
Thanks anyway.

---

