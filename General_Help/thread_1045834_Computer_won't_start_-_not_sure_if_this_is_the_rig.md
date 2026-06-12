---
title: "Computer won't start - not sure if this is the right place for this"
date: 2009-01-20
forum: General Help
---

### Post by NintendoTogepi on 2009-01-20
Okay, so I was using my older testing computer, and I was setting up another installation of Ubuntu mini. I finish it up, etc. 

Now the computer won't start up, it just takes me to a screen saying
```

GRUB Loading stage1.5.

GRUB Loading, please wait...

Error 22
```

Any idea what the problem is or if it is fixable?

I don't care if this computer becomes permanently unusable as it's an old computer of mine that I mainly use for Linux and testing.

Right now I'm using the "broken" computer - running on a DSL Live CD. 

So, if anyone knows, I'd appreciate it. Once again, no urgency. If I am told "It is unfixable", my reaction is "Oh well, I'll have to pick up a new testing computer. Can you tell me why it broke so I can avoid the mistake again? :)"

---

### Post by NintendoTogepi on 2009-01-20
bump

---

### Post by Will4 on 2009-01-20
just boot from the live CD and after it opens go to the terminal and type

Code: 

> sudo grub

grub> find /boot/grub/stage1
grub> (hd0,?)
grub> root (hd0,?)
grub> setup (hd0)

after it says (Done...)

press ESC to save and exit.

then terminal again

Code: 

> sudo gedit /boot/grub/menu.lst

and at this part change the root (hd0,?)

> ## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=fd4b1619-59ad-4341-ab35-d8a332bac727 ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet

Enjoy it!!

---

### Post by Sef on 2009-03-05
Locked.  [Duplicate Post]("http://ubuntuforums.org/showthread.php?p=6845662#post6845662").

---

