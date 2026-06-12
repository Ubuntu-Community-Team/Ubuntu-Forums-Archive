---
title: "NVidia problem?"
date: 2005-12-02
forum: Gaming &amp; Leisure
---

### Post by Barts_706 on 2005-12-02
Hi,

I have problem with Wine not working. I was looking through everything I could, and there is one little issue that is bugging me.

When I run glxinfo, I see among other things this :

> direct rendering: No 

Could that be the cause of problems?

I would like to add that my glquake is running fine, so I personally don't know what to think about it. 

And if it's wrong, what can I do about it?

---

### Post by 23meg on 2005-12-02
How exactly Wine "not working"? Where did you install it from? Does it not work with any apps at all? Do you get any errors in the terminal?

---

### Post by Barts_706 on 2005-12-02
Briefly : wine is installed from winehq repository, it theoretically works (when I just type wine in console), but I cannot emulate games I used to be able to play before (under Mandriva 2005 and older version of wine).

The precise description and glxgears info are here :
[http://ubuntuforums.org/showthread.php?p=535067]("http://ubuntuforums.org/showthread.php?p=535067")

In case of Unreal Tournament I am faced with black screen, in case of DarkPlaces.exe (mod for quake) I get following error :

> X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  748
  Current serial number in output stream:  759


At the same time I am able to play glquake at decent framerate, so I think the error is not GL related.

---

