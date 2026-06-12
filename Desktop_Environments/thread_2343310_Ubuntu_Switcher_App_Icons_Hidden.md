---
title: "Ubuntu Switcher App Icons Hidden"
date: 2016-11-15
forum: Desktop Environments
---

### Post by mmcneilly on 2016-11-15
[https://goo.gl/ervh7p](https://goo.gl/ervh7p)


Does anyone know what has happen here to my Ubuntu Switcher menu. I'm not sure what has happened but all of a sudden the app icons are hidden by a display of the actual windows. I don't know if I have done something with the Unity Tweak Tool, I have tried resetting my personal unity tweak settings on it and it has made no difference. Any tips. 
Thanks for your help.

---

### Post by ajgreeny on 2016-11-15
Please do not add huge images inline.
Use the Attach icon (paperclip) in the toolbar to navigate to an image on your hard disk and then upload it.

Which version of Ubuntu are you using and what hardware are you using to run it on?

---

### Post by mmcneilly on 2016-11-15
Ok sorry about that, first time posting, duly noted. 
Version: Ubuntu 16.04 LTS
Hardware: Acer Aspire V5-571 Laptop 

If you need anymore info just ask.

---

### Post by ajgreeny on 2016-11-15
Thanks for the info.
It would appear that the laptop uses Intel integrated graphics; correct?

If you're not sure run terminal command ```
lspci | grep -i vga
```

---

### Post by mmcneilly on 2016-11-15
Yes that is correct

---

### Post by ajgreeny on 2016-11-15
This might be a setting somewhere in the switcher configuration in cssm that is telling it to use thumbnails and not just icons, but I'm afraid I don't use unity so I am not sure of any details of this.

---

