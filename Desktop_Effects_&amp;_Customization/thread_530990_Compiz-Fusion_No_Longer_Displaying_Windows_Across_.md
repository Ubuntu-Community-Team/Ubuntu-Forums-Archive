---
title: "Compiz-Fusion No Longer Displaying Windows Across All Desktops"
date: 2007-08-21
forum: Desktop Effects &amp; Customization
---

### Post by mrgnash on 2007-08-21
Ok, so I upgraded to the version of compiz fusion from polycoke's repository, and it seems to work fine for the most part, except that now when I hover the mouse in the top-right hand corner of the screen it no longer displays all the windows across all workspaces, but only the ones on the immediate workspace. I'm not even sure what plugin governs this behaviour, so am unsure of what settings to adjust in order to fix it. Any suggestions?

---

### Post by Rupertronco on 2007-08-21
It's the scale plug-in, you can find it in the window management section. Open that, go to the actions tab,  and in the section where it says Window Picker For All Windows, put "TopRight" in the screen edge column.

---

### Post by tact on 2007-08-21
> **Rupertronco said:**
> It's the scale plug-in, you can find it in the window management section. Open that, go to the actions tab,  and in the section where it says Window Picker For All Windows, put "TopRight" in the screen edge column.

It used to be like that.  Now tho - there is no "actions" tab in the scale plugin settings.  I guess its just the configuration manager a bit messed up.  Perhaps next update will see it fixed

---

### Post by Sikarian on 2007-08-22
I've got this same issue as well.  No actions tab.  Is there a way to manually edit a config file?

---

### Post by tact on 2007-08-23
I changed over to use vorian's repo and updated.  At least scale now I can configure scale to show all windows from all desktops.

Still other favourites like screensaver and 3D windows on cube rotate, and being able to rotate cube by pressing and holding centre mousebutton dont work yet

---

### Post by CFBauer on 2007-09-20
> **tact said:**
> It used to be like that.  Now tho - there is no "actions" tab in the scale plugin settings.  I guess its just the configuration manager a bit messed up.  Perhaps next update will see it fixed
Same with me.  I look forward to using scale for all of my desktops again.

---

### Post by koshari on 2007-09-24
its easy to change back on the laters build, 

go to compizconfig settings manager, 
window management section, select scale, 
click on the bindings tab,
then enable the initiate window picker for all windows, and clicl on the top right of the graphical.

a prompt will come up saying that this binding is already reserved for initiate window picker, it will give you some options, choose the one you want.

---

