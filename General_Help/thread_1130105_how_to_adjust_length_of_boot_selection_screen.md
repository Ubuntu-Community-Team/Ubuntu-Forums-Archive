---
title: "how to adjust length of boot selection screen"
date: 2009-04-19
forum: General Help
---

### Post by bded on 2009-04-19
title says it all really, how can i make the boot selection longer or shorter?

i have windows 7 on an old 80 gig ide, xp pro on my 500 gig sata and ubuntu on a little 50 gig ide i found. i like the fact that i can select from the boot menu where to go but i have problems explaining the selections to others in my house when i goes by to fast.
still the menu is easier then adjusting boot priorities in bios.

---

### Post by BugFixBug on 2009-04-19
In a terminal:
```

sudo gedit /boot/grub/menu.lst

```

a gedit window will popup with the grub conf file.
look for:
> 
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10


and change the timeout value to whatever you like.

---

### Post by LiamWilson on 2009-04-19
Are you using grub as the default bootloader?

If you are, paste 
```
sudo gedit /boot/grub/menu.lst
```

Then, under the section that says "Timeout" (The default is 3, i think), set it to a larger number, such as 5 or 10, whichever you prefer.

---

### Post by bded on 2009-04-19
i don't know if i'm using grub or not, probably am if it is default.

thank you for the replies i'm gonna see if it works now.

[edit] worked just fine.

---

