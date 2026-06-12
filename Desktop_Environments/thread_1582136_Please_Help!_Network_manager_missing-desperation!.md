---
title: "Please Help! Network manager missing-desperation!"
date: 2010-09-26
forum: Desktop Environments
---

### Post by ThanosShadow on 2010-09-26
Basically, congratulations for the forum, i believe it will help us a lot!
Well, i accidentally removed the "Network manager" from the right-top of the "default" ubuntu panel(u know, the icon that, by clicking on it, displays the wired and wireless connections. So, i right click, select "add to panel" and i can't find it anywhere! Please, it's vital to get it, what have i to do?:confused:

---

### Post by nothingspecial on 2010-09-26
It`s part of indicator applet or notification area, one of those two

---

### Post by ThanosShadow on 2010-09-26
I know where it is and what it is, but i accidentaly removed it from the panel, and when i try to add it again with "add to panel" option, i can't find it. I was next to the volume, on right top. How can i put it again??????????????????????????????????????????????????//

---

### Post by nothingspecial on 2010-09-26
What happens if you press Alt-F2 and type

```
nm-applet
``` into the little box that appears?

---

### Post by ThanosShadow on 2010-09-26
it says: Could not open location 'file:///home/thanos/nm-aplet'. But where is the point? 
I am not sure if u understand what i am looking for.:(

---

### Post by nothingspecial on 2010-09-26
You`ve lost the network doodah that shows on the panel

Right click the panel and remove then add both indicator-applet and notification area.

If that doesn`t work try removing then reinstalling nm-applet

```
sudo apt-get remove nm-applet && sudo apt-get install -y nm-applet && nm-applet 
```

If that doesn`t work, create a new panel, add notification-area and indicator applet. If the network thingy appears on there then add everything else you like to that panel, remove the old one and put the new one in it`s place

---

### Post by ThanosShadow on 2010-09-26
OMG I LOOOOOOOOOOOOOOOVE UUUUUUUUUUUUUU!!! I added the notification area and it was added with the language and the search!!! Thnx a lot!
But i have another one problem about the panel. I click "places" and there is no "trash"!:shock:

---

