---
title: "How to gain root permissions?"
date: 2009-05-02
forum: General Help
---

### Post by GL_NORWAY on 2009-05-02
Ok I'm a first time linux user -- LOL! So don't laugh!

I'm having trouble with GRUB and want access to a file under boot/grub/ to play with the boot table settings for my XP partitions (only one of three starts). I can open it but can't save it since "root" is the "owner" and I can't login as root.

How do I gain access to this file or at least edit and save it?

:confused: :D

---

### Post by LoneWolfJack on 2009-05-02
```
sudo gedit /path/to/myfile
```

---

### Post by Peter09 on 2009-05-02
preface your command with sudo

```
sudo <command you want to run>
```

---

### Post by lisati on 2009-05-02
It might be easier for you to install "Startup manager" if you're new to Ubuntu/Linux. You can do this from the Applications->Add/remove software menu.

---

### Post by overdrank on 2009-05-02
To add to Peter09 and LoneWolfJack [RootSudo]("https://help.ubuntu.com/community/RootSudo") should help :)

---

### Post by sahabcse on 2009-05-02
open the terminal in accessories there type

#sudo bash

It will go to root login

#vim /boot/grub/menu.lst

For using the vim or vi editor click [here]("http://sahabm.blogspot.com/2009/04/vi-editor-how-to.html")

---

