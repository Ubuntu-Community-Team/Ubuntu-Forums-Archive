---
title: "deleted compiz to get ubuntu to work, now what."
date: 2009-04-04
forum: General Help
---

### Post by tkearn5000 on 2009-04-04
In order to get ubuntu to go past the login screen, I had to delete the compiz files (compiz, and compiz-core). Aparantly my graphics card didn't support the 3d graphics.

After deleting the compiz files, getting ubuntu up and running, and learning more about how it works, I am interested in attempting to get the 3D graphics to work. 

My video card is: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device. It is from Intel. 

If I reinstall the compiz files that I deleted, would I be able to restart in low graphics mode, and see if the proprietary drivers for my card are available on the hardware drivers menu. I found a site that offers open source drivers for people running linux with this card, but I think installing that way might be over my head.

If anyone has experience with this, I would appreciate the help.
Thanks,
-TK

---

### Post by JordyD on 2009-04-04
For installing drivers for your video card, you can just go to System > Administration > Hardware Drivers, and enable any needed proprietary drivers. I think after that step you need to restart.

Then you can reinstall the package for the files that you deleted (not sure which one that is, maybe somebody else can help you there). To reinstall a package, you can use Synaptic Package Manager (System > Administration > Synaptic Package Manager), find the package using the search feature, right click on it and select 'Mark for Reinstallation'.

Hope that helps,
Jordy

---

### Post by tkearn5000 on 2009-04-04
Currently the Hardware Drivers menu is empty. I was thinking that re-installing the deleted packages (compiz and compiz-core) might result the hardware driver menu realizing that I am missing a driver to run the 3d graphics. Since everything is working fine without them, maybe the menu doesn't realize that I'm missing something.

Hopefully that makes sense.

Thanks
-TK

---

### Post by tkearn5000 on 2009-04-04
Also, I've seen a number of posts on here pertaining to people not being able to get past the login screen, and having to delete compiz. Is this a known problem? Should I file an error report?

---

### Post by mocoloco on 2009-04-04
Nope, the hardware drivers app doesn't care if you have compiz installed or not. It works independently. Also, I don't know about yours but most intel chips have open source drivers so you don't need to use "hardware drivers" which is just for closed-source stuff.
Open a terminal and run this
```
glxinfo | grep render
```

If for direct rendering it says "yes" you're in business, and the compiz issues were caused by something else.

---

### Post by tkearn5000 on 2009-04-04
Thanks for the reply. I entered the code you supplied, and got back a yes answer. Any idea what my next step should be. I did find open source drivers for my graphics card, but I'm not sure if I need to, or how to install them.
Thanks,
-TK

---

### Post by tkearn5000 on 2009-04-04
I finally found out my problem. My graphics card is blacklisted in ubuntu. Apparently it can cause problems when trying to run the 3d graphics. It looks like I'll have to live without them until I get a new card. 

Thanks for the help,
-TK

---

