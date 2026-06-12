---
title: "[SOLVED] Mounted Drives On Desktop"
date: 2008-05-27
forum: Desktop Environments
---

### Post by Mr.Macdonald on 2008-05-27
When i mount drives via "sudo mount /dev/sda1 /mnt/folder" My desktop gets a nice mounted drive icon. I don't like this because i already symbol link my drives every which way and these icons are annoying.

can i remove them

---

### Post by NikoC on 2008-05-27
ALT + F2
gconf-editor
apps > nautilus > desktop > volumes_visible

I think this was what you were looking for, right?

Cheers

---

