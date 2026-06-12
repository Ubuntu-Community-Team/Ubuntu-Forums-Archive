---
title: "few questions on icons"
date: 2009-11-10
forum: Desktop Environments
---

### Post by JacobK on 2009-11-10
I'm tweaking the appereance of my laptop a bit at the moment, and it now looks like in the screenshot.

-How can I change the icons in the right upper corner, the trashcan, and the icons for the folders? I want to make them white as well. I can just edit the files in GIMP, but I don't know where to find them.

-Can I change the forward/reload etc. icons in Firefox without downloading an iconpack?

Thanks! :)

---

### Post by Kilz on 2009-11-10
The location of the icons depends. If you installed the icons by downloading them and adding them they reside in a hidden folder in your home directory. ~/.icons/iconthemename . If they came pre installed or installed with apt/synaptic they can be found in /usr/share/icons . 

You can change any icon, even the ones in Firefox with the above locations as long as you are using the default theme that came with Firefox as it uses system icons.

---

### Post by JacobK on 2009-11-10
Okay, that helps a lot :) And where can I find icons for programs running in Wine? And actually, does anybody have a Humanity White Icon Pack? For folders etc, that is.

---

### Post by JacobK on 2009-11-10
Hmm, when I edit an icon (for instance the Dropbox one) and I open the program it still uses the original one. What am I doin wrong?

---

### Post by mrboojive on 2009-11-10
> **JacobK said:**
> And where can I find icons for programs running in Wine?

I think they are located in the .local/share/icons/ folder in your home directory.

> **JacobK said:**
> Hmm, when I edit an icon (for instance the Dropbox one) and I open the program it still uses the original one. What am I doin wrong?

Probably you are editing the wrong file. There are different files for displaying the icon, depending on what size the icon is going to be when displayed. In the folders for each icon theme, there are icons for 16x16, 24x24, 48x48, etc. which have the icons for that size. There is also an svg folder which has scalable icons. You need make sure that you are making changes to the correct size as well as the correct icon. You might also try logging out and logging back in after changing the icon, or changing the theme and then changing it back.

---

