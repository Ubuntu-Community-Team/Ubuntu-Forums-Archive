---
title: "Ownership of folders"
date: 2010-09-25
forum: Desktop Environments
---

### Post by buster2209 on 2010-09-25
In order to get my PIC programmer to work through Piklab, I have to change the ownership of the /bus folder to myself;

sudo chown MYUSERNAME -R /dev/bus

The ownership of the folder then reverts back to root after some time.

Is there anyway to make it PERMANENTLY under MYUSERNAME ownership?

---

### Post by linux-hack on 2010-09-25
Change the group of the file to your username group

```
sudo chown USERNAME:USERNAME /dev/bus
```

An may be the sticky bit will help to :

```
sudo chmod +t /dev/bus
```

---

### Post by asmoore82 on 2010-09-25
I think the only good long-term solution is going to involve setting some custom udev rules...

I know not how - I would suggest changing the thread title to something mentioning "udev rules"

---

### Post by asmoore82 on 2010-09-25
This might be it!! ...
[http://sourceforge.net/apps/mediawiki/piklab/index.php?title=USB_Port_Problems#For_distributions_using_.22udev.22_.28Debian_Sid.2C_Ubuntu_6.2C7.2C8.2C....29](http://sourceforge.net/apps/mediawiki/piklab/index.php?title=USB_Port_Problems#For_distributions_using_.22udev.22_.28Debian_Sid.2C_Ubuntu_6.2C7.2C8.2C....29)

It looks very promising because if you [Google "piklab udev rules"]("http://www.google.com/search?q=piklab+udev+rules"),
this is the first result which is a very similar solution:
[http://usbpicprog.org/?page_id=13](http://usbpicprog.org/?page_id=13)

---

