---
title: "Dual boot, Windows as default???   Can it be done"
date: 2009-03-30
forum: General Help
---

### Post by GrnFrag on 2009-03-30
Hi all,  silly question

I have dual-booted Ubuntu 8.10 and Windows XP.   I use the Grub menu to select the OS, and my question is how do i change the default OS?    I'd like to know how to make Winders the default, so when Grub times out, Windows is loaded.  i do know how to edit the menu.lst, but i am a complete noob at Ubuntu.     

I'm sure i'll take flak for this, so let me just say that this computer is used by my whole family.    AND when someone else boots and forgets to choose windows, i get a phone call.   Doesn't matter who it is, or how many times i've explained this, they call.   So please help.   I'll take all the flak you can dish out, if you can help me  :D

---

### Post by 3Miro on 2009-03-30
Family, gotta love them.

Install a grub editor from the Add/Remove programs. Under KDE KGrub Editor works great. You can install it under Gnome (the default Ubuntu), but it is better if you use a Gnome Gtk one (I am not even sure if there is one). Then you can choose the default and other options.

Alternatively you can edit the grub menu.lst. Back up the existing one and then edit the new one:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.mybackup
sudo gedit /boot/grub/menu.lst

```

The you have to read some of the instructions in the file. There is a value:
```
default         0
```
and later entries for all the OS installed
```

title           Ubuntu 8.10, kernel 2.6.27-11-generic
uuid            04f2e089-6565-4f00-a516-ca8b1f60f7fe
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=04f2e089-6565-4f00-a516-ca8b1f60f7fe ro quiet splash
initrd          /boot/initrd.img-2.6.27-11-generic
quiet
...
title           Other operating systems:
root

title           Microsoft Virus XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```
Counting starting form 0, set the default to the entrie number of windows.

If I were you, I would really use a grub editor program.

---

### Post by GrnFrag on 2009-03-30
Sweeeeeeeet!!!    That worked perfectly, and no, i didn't use the grub editor.    just beggin for trouble, imagine how many calls i'd get if this thing wouldn't load EITHER OS.     LOL


Thanks alot

---

