---
title: "Desktop GUI for creating/mounting DM-Crypt / LUKS containers"
date: 2008-01-14
forum: Desktop Environments
---

### Post by ariel on 2008-01-14
Hi, I'm looking for a GUI / system tray tool that allows the creation of DM-Crypt / LUKS volume containers, and mounting them when needed. 

Gnome can handle LUKS-encrypted usb keys pretty well, but now I need some easy way to handle containers. Something like "easy crypt" or "forcefield" but for LUKS / DM-Crypt.

Curiously I can't find any GUI.

Hints, anyone?

TIA

---

### Post by dimeotane on 2008-01-25
I agree its not really needed with removeable volumes, like USB drives.  
Because you enter a few terminal commands to make the encrypted volume at the start. 
From then on, any time you insert the removeable volume which is encrypted, Ubuntu should detect the lukformat volume and prompt for a password. 
But you're thinking of something different than encrypted USB drives though, like encrypted folders perhaps? 

Check out [cryptkeeper]("http://www.tomatarium.pwp.blueyonder.co.uk/cryptkeeper.html")
Check out [crypt manager]("http://www.ubuntugeek.com/crypt-manager-an-encrypted-folder-manager-for-ubuntu-linux.html ")
A new one is [conceal]("http://linux-tutor.org/?q=en/node/11")

---

### Post by ariel on 2008-01-25
Thanks, for this application I was thinking "file containers" like the ones truecrypt handles.

I didn't find any tool for container creation, so I ended up using truecrypt.

I was looking for is an easy way to create optical backups of (say) a home folder, also encrypted.

Still haven't found anything better than creating a 4.3GB container (truecrypt, but would have preferred LUKS/Dmcrypt) in the HD, copying the files I want to backup, and then burning it with brasero. Not very user friendly, but at least works.

I'm still waiting for a real backup tool that can encrypt on the fly, and split the backup in multple dvd's though.

---

### Post by dimeotane on 2008-01-26
you've tried Easy Crypt for a GUI with truecrypt?

I often burn to backup DVD-RW my easycrypt container file.

you might like that

---

### Post by ariel on 2008-02-02
> **dimeotane said:**
> you've tried Easy Crypt for a GUI with truecrypt?

I often burn to backup DVD-RW my easycrypt container file.

you might like that

Thanks, that's what I'm using right now (burning true-crypt containers).

---

