---
title: "How to disable only PDF thumbnails"
date: 2011-01-11
forum: Desktop Environments
---

### Post by Kognit on 2011-01-11
Hi

I want to disable only PDF thumbnails not the png, jpg or any other image format. In gconf-editor /apps/nautilus/preferences there is option only to disable all thumbnails. Is there any way to disable only pdf thumbnails?

thx

---

### Post by Kirboosy on 2011-01-11
Open a terminal and type
```
gconf-editor
```Navigate to /desktop/gnome/thumbnailers

and disable the PDF one


~Caboose

---

### Post by Kognit on 2011-01-11
Thx for reply

I tried that solution earlier but that only prevents of creating new thumbnails and do nothing about existing ones. By following your solution my pdf thumbnails are still there. Any other suggestion? thx

---

### Post by Kirboosy on 2011-01-11
what if you move the files around? Will it still retain the thumbnail?

---

### Post by Kognit on 2011-01-11
Yes, it still stays the thumbnail

---

### Post by Kirboosy on 2011-01-11
```
sudo chmod u=rw /usr/bin/evince-thumbnailer
``` 
It will make the thumbnailer read and write, not execute. It might just work. If it doesn't work, I have no other suggestions.

---

### Post by Kognit on 2011-01-11
No, it doesn't work. Thx for help anyway

---

### Post by asmoore82 on 2011-01-11
You can delete all files from "$HOME/.thumbnails"
This will force Nautilus to rebuild all thumbnails and
since you have PDFs disabled, they shouldn't get any.

You may have to kill nautilus or restart for the change to take effect.

---

### Post by Kognit on 2011-01-12
Thx man, that did the trick. Problem solved

---

### Post by Kirboosy on 2011-01-12
> **asmoore82 said:**
> You can delete all files from "$HOME/.thumbnails"
This will force Nautilus to rebuild all thumbnails and
since you have PDFs disabled, they shouldn't get any.

You may have to kill nautilus or restart for the change to take effect.

*facepalm* I totally forgot about that folder. I'm glad you were on your "A" game. :)

---

