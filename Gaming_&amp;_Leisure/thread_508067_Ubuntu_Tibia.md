---
title: "Ubuntu Tibia"
date: 2007-07-23
forum: Gaming &amp; Leisure
---

### Post by sub7 on 2007-07-23
Is tibia completely unsupported on ubuntu?
The linux client 8.00 they provide doesn't run at all, it pops up and disappears instantly...

I have read every wine tutorial but the GUI is utterly mutilated.

[https://secure.tibia.com/account/?subtopic=downloadclient](https://secure.tibia.com/account/?subtopic=downloadclient)

---

### Post by Cappy on 2007-07-23
Extract the file, change to the extracted directory using the console and if the binary is "Tibia" then you'll need to ```
./Tibia
```It is case sensitive. 
It will probably give you an error message and you can copy and paste it back here.

 If you get a "no such file or directory" kind of error you are in the wrong directory or the binary is not called "Tibia".

---

### Post by sub7 on 2007-07-24
Thanks :D

X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  58
  Current serial number in output stream:  59

I'm using Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
Seems to be ok as beryl works fine on it.

---

### Post by wana10 on 2007-07-24
try disabling beryl before running tibia. i have a few games that refuse to run when beryl is running. you don't have to exit beryl, just right click the icon and select metacity as window manager.

---

### Post by sub7 on 2007-07-24
The same error still appears :( good suggestion though.

---

### Post by Cappy on 2007-07-24
I have the same card in my laptop.
Try
```
sudo apt-get install xserver-xorg-video-intel
```
If you have the older i810 (the default) this will install the newer driver.

---

### Post by sub7 on 2007-07-24
Thanks for the driver update, but the tibia error continues to popup :(
I wonder what it could be :S

---

### Post by Cappy on 2007-07-25
I googled and it looks like you can't run the Linux version because you need a Nvidia or ATI card (something other than MESA). It is just the way they programmed the linux client =(

The windows client may work with WINE but according to appdb:
[http://appdb.winehq.org/appview.php?iVersionId=5403&iTestingId=6174](http://appdb.winehq.org/appview.php?iVersionId=5403&iTestingId=6174)
you'll need to install wine 0.9.15 or lower for it to work.

The only place I see that wine is here:
[http://wine.budgetdedicated.com/archive/ubuntu/dapper/wine_0.9.15~winehq0~ubuntu~6.06-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/dapper/wine_0.9.15~winehq0~ubuntu~6.06-1_i386.deb)
I'm not sure if that would work on Feisty

---

### Post by sub7 on 2007-08-01
Err... that kinda worked... Your a genius...

---

