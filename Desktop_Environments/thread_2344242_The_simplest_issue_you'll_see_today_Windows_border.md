---
title: "The simplest issue you'll see today: Windows borders edge"
date: 2016-11-23
forum: Desktop Environments
---

### Post by icarolenine on 2016-11-23
Hello Friends,

I'm using the Ubuntu 16.04 with GNOME Shell v3.18.5 and Adwaita theme.
How do I remove these edges?

Thanks in advance.

---

### Post by ajgreeny on 2016-11-23
Sorry, but what edges do you mean?  It's not clear to me from the image.

---

### Post by vasa1 on 2016-11-23
I'm guessing OP doesn't like the sharp corners.

---

### Post by ajgreeny on 2016-11-23
Change of theme will do it surely, if that is the complaint?

I do not like nor use the gnome-shell, I'm afraid, so I don't know for certain, but that type of detail is usually theme related.

---

### Post by icarolenine on 2016-11-23
That is the point. 

I want to keep the theme but I hate those sharp corners!

> **ajgreeny said:**
> Change of theme will do it surely, if that is the complaint?

I do not like nor use the gnome-shell, I'm afraid, so I don't know for certain, but that type of detail is usually theme related.

---

### Post by Frogs Hair on 2016-11-23
The theme displayed is ambiance and when I used the gnome shell saw the same problem. There was a third party Gnome variant , but unfortunately hasn't been maintained.

---

### Post by vasa1 on 2016-11-23
In my opinion, the corners are part of the window decorations and should be controlled by the current window manager (unless the application has client-side decorations.

---

### Post by icarolenine on 2016-11-24
Friends,

The matter was solved installing new colors from Ambiance. (I don't use Adwaita as said before)

sudo add-apt-repository ppa:ravefinity-project/ppa
sudo apt-get update
sudo apt-get install ambiance-colors

---

### Post by Frogs Hair on 2016-11-24
> I'm using the Ubuntu 16.04 with GNOME Shell v3.18.5 and Adwaita theme.> (I don't use Adwaita as said before) ??

Glad it's fixed.

---

