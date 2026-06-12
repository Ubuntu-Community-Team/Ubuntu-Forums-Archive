---
title: "TIP: How to remove the timeout for the Linux Grub"
date: 2009-03-21
forum: General Help
---

### Post by Combs on 2009-03-21
You have Windoz or Mac or whatever and [most important]...Ubuntu :D And every time you start your computer, you have that timeout showing you that by Default, Ubuntu will start...This can be fun or sometimes when your out, Not At All. So today, I'll show you how to remove the time.With that removed, the grub will need you to start any O.S :KS
So, let's start :)

Open your menu.list file with our favorite Text Editor

```
sudo gedit /boot/grub/menu.lst
```
***Sudo*** means that you will be a "temporary Administrator" while you open the Software called. In our case: Gedit
Now find the section that looks like this:

   ```
 ## timeout sec
    # Set a timeout, in SEC seconds, before automatically booting the default entry
    # (normally the first entry defined).
    timeout 3
``` Just put a "#" (without the quotes) in front of "timeout 3"

Have fun..and take care of the planet
combs.S

---

