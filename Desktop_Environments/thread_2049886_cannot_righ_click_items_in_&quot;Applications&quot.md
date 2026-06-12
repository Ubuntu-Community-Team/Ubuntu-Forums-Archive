---
title: "cannot righ click items in &quot;Applications&quot; menu"
date: 2012-08-29
forum: Desktop Environments
---

### Post by paichkash on 2012-08-29
hi
i want some apps to appear on the taskbar in xubuntu .. currently there is just ff and a help icon .. i want few more apps like opera browser and skype and other apps to be shown there.. so when i click on the applicatons menu and try to right click on skype or opera or anything it launches it.. it also launches it on left/middle click.. i tried pressing alt,ctrl and other key combinations to get the right click context menu but was thoroughly unsuccessfull. however i can do so in gnome ..but not in xfce..

so i formated and reinstallled ubuntu but still the same .. i formated and reinstalled it twice with no luck.. any help ?
thanks

---

### Post by Elfy on 2012-08-29
Well xfce is not gnome. 

Right click panel - add new item - add a launcher - right click launcher - properties - add new item 

OR you can right click panel - panel preferences - items tab and do effectively the same thing.

---

### Post by LewisTM on 2012-08-29
OR drag and drop from the menu to your panel or desktop. That's shortest route.

---

### Post by paichkash on 2012-08-30
> **LewisTM said:**
> OR drag and drop from the menu to your panel or desktop. That's shortest route.):P
how can i drag it if i cant drag it ?
i can i gnome but not in xfce... )

from above posters response it seems that xfce doesnt support draging esp in the case of draging a shortcut/link to an app from the Applications menu (at the top leftmost side of screen) to the panel. and only way out is like the one quoted by above fellow... thats very painfull way of doing ... and then changing the icon is also PITA.. whareas in gnome just drag and drop and icon is set to the apps default..

---

### Post by Elfy on 2012-08-30
> **LewisTM said:**
> OR drag and drop from the menu to your panel or desktop. That's shortest route.

Can't say I've ever managed to drag and drop :(

But then again I'm not too worried about doing it the other way either :)

---

### Post by cmcanulty on 2012-08-30
you have to slowly drag and hold it over panel until a box shows then release, takes a while to figure it out and it still usually takes me a couple of tries

---

### Post by LewisTM on 2012-08-30
Once you've mastered the drag and drop trick, there is one more thing you can do.
As pointed out, you can't edit menu items in-place in Xfce. A workaround is to create a new panel or desktop launcher with execute command
```
exo-desktop-item-edit %f
```
Then you can drag menu items and drop them onto that launcher. It will execute the desktop file editor so you can modify the details of the item.

---

### Post by cmcanulty on 2012-08-30
also this works for me but I have no clue why. I get everything I want in my panels (I use 3) in gnome classic then logout and back in to xfce or xubuntu and everything from classic is carried over.

---

### Post by paichkash on 2012-09-07
i installed "Main menu Editor" package now i can do what i want through it... 
i installed it few days ago so dont remember exact process.. but search for the above pacakge and its info ..u will be able to solve ur problem as well...

---

