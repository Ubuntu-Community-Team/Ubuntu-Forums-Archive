---
title: "delete OS from menu.lst"
date: 2008-12-30
forum: General Help
---

### Post by Feivel on 2008-12-30
I finally decided to do a full install of Ubuntu and dump my Wubi install so now I have Ubuntu on a nice clean 320 GB SATA formated in ext3. Question is I would like to delete windows off my secondary HD but doing that will still leave an entry in GRUB. Can I just comment out or delete the line in my menu.lst? I don't want to set my timeout to 0 because then I can't access the GRUB menu if something goes wrong.

---

### Post by eBoxNet on 2008-12-30
in order to edit grub menu you can do : 

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Feivel on 2008-12-30
> **eBoxNet said:**
> in order to edit grub menu you can do : 

```
sudo gedit /boot/grub/menu.lst
```

I know how to edit it. I'm asking if I can just delete or comment out the windows entry.

---

### Post by eBoxNet on 2008-12-30
oh sorry my bad,
its better to comment the entry you don't need.

Backup the menu.lst : 

```
sudo cp /boot/grub/menu.lst  /boot/grub/menu.backup
```

then edit it :

```
sudo gedit /boot/grub/menu.lst
```

and comment by adding # to the proper lines.

---

### Post by mikewhatever on 2008-12-30
> **Feivel said:**
> I know how to edit it. I'm asking if I can just delete or comment out the windows entry.

Yes, absolutely. Delete it since you are removing Windows.

---

### Post by Feivel on 2008-12-30
> **mikewhatever said:**
> Yes, absolutely. Delete it since you are removing Windows.

Will do. I haven't booted into Vista since I installed Wubi last March. About time I did a full install. I'll keep my laptop as a duel boot with XP.

---

