---
title: "Setting new background color in 19.10"
date: 2019-11-07
forum: Desktop Environments
---

### Post by Edward_Diener on 2019-11-07
I am running Ubuntu 19.10 using the Ubuntu desktop. I had set a background color for my desktop in Ubuntu 19.04. But when I try to change my background color using Settings | Background I am not given a choice of colors but rather background pictures. How can I set the background to some other color ?

---

### Post by Frogs Hair on 2019-11-07
The option is missing in my installation as well . It looks like that feature has been removed by the Gnome developers. A work around would include creating folder with solid color background images.

---

### Post by Dennis N on 2019-11-08
> **Edward_Diener said:**
> I am running Ubuntu 19.10 using the Ubuntu desktop. I had set a background color for my desktop in Ubuntu 19.04. But when I try to change my background color using Settings | Background I am not given a choice of colors but rather background pictures. How can I set the background to some other color ?

Hello Edward;

For setting a desktop background color in Ubuntu 19.10 a different method is now needed:

install and use **dconf-editor** utility:

_disable background images:_
navigate to: **org.gnome.desktop.background.picture-options**
Be sure default value switch = off
Click on custom value box and select 'none'. this will turn off using an image.
Click 'Apply'

_set color:_
navigate to: **org.gnome.desktop.background.primary-color**
Be sure default value switch = off
Click on custom value and set color hexcode in format #334b32
Click 'Apply'

Background will change to custom color instantly.

---

### Post by Frogs Hair on 2019-11-08
Thanks Dennis, I usually use pictures , but it's good to know how to apply a solid background.

---

### Post by Edward_Diener on 2019-11-14
> **Dennis N said:**
> Hello Edward;

For setting a desktop background color in Ubuntu 19.10 a different method is now needed:

install and use **dconf-editor** utility:

_disable background images:_
navigate to: **org.gnome.desktop.background.picture-options**
Be sure default value switch = off
Click on custom value box and select 'none'. this will turn off using an image.
Click 'Apply'

_set color:_
navigate to: **org.gnome.desktop.background.primary-color**
Be sure default value switch = off
Click on custom value and set color hexcode in format #334b32
Click 'Apply'

Background will change to custom color instantly.

Works fine. Thanks !

---

### Post by corradoventu on 2020-02-14
It looks like that feature has been removed by the Gnome developers
but in the help I see:

---

### Post by corradoventu on 2020-02-15
To set a solid color background create a small picture (.jpg or .png) of the preferred color in Your Pictures folder, right click on the picture and select 'set as wallpaper'
I submitted a bug for this problem: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1862945](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1862945)
if you have the same problem please confirm my bug

---

### Post by kamasys on 2020-06-08
> **Dennis N said:**
> Hello Edward;

For setting a desktop background color in Ubuntu 19.10 a different method is now needed:

install and use **dconf-editor** utility:

_disable background images:_
navigate to: **org.gnome.desktop.background.picture-options**
Be sure default value switch = off
Click on custom value box and select 'none'. this will turn off using an image.
Click 'Apply'

_set color:_
navigate to: **org.gnome.desktop.background.primary-color**
Be sure default value switch = off
Click on custom value and set color hexcode in format #334b32
Click 'Apply'

Background will change to custom color instantly.

I can confirm that this works too in Ubuntu 20.04. With dconf-editor   it's also possible to have one image stretched over two monitors by   setting a suitable large image to 'spanned'. In Unity this was a   standard feature.

---

### Post by johnnymcc on 2020-06-09
The option to do this via settings did not come back in 20.04.  Before I knew about dconf-editor, I used gsettings which is installed by default.  For primary-color you can also use 'rgb(R,G,B)' or 'hsl(H,S,L)'.

---

