---
title: "Mount samba share on every boot"
date: 2008-01-03
forum: Desktop Environments
---

### Post by frodemt on 2008-01-03
Hi

I want to mount samba share on every bootup. This must happen automaticaly.

I use "mount -t smbfs -o username=bruker,password=passord //lamp2/frimappe /sikker"

This works only as long as I dont reboot. How do I make this permanent?

---

### Post by mauripop on 2008-01-03
Hi frodemt. 

This is how I accomplished what you want. It is all done from konsole (what fun!)

[FONT="Courier New"]cd /etc/init-d[/FONT]

You are going to create a text file called start_smb on that folder that will execute the command you need every time you boot. 

[FONT="Courier New"]sudo nano start_smb[/FONT]

A text editor will be invoked, type this into it: 

[FONT="Courier New"]#!/bin/bash
mount -t smbfs -o username=bruker,password=passord //lamp2/frimappe /sikker
[/FONT]

Press Ctrl-O to save and Ctrl-X to exit 

Now still on konsole: 

[FONT="Courier New"]sudo chmod +x start_smb
sudo update-rc.d start_smb defaults
[/FONT]

That's it! 
Hope it helps.

---

### Post by chiru on 2008-01-03
I think fstab will do this stuff.

Edit /etc/fstab (as root) and add something like:

```
//lamp2/frimappe  /sikker   smbfs    username=bruker,password=passord 0 0
```

I'm not sure if the trailing zeros are ok, but meybe some googling wil help to guess this numbers.

Cheers

---

### Post by frodemt on 2008-01-03
Thank you for your answers. I think I will stick with mauripop's way this time because I understand it.

---

