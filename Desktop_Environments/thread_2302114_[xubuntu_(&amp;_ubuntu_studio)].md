---
title: "[xubuntu (&amp; ubuntu studio)]"
date: 2015-11-07
forum: Desktop Environments
---

### Post by yoshii on 2015-11-07
How do i change icons for specific file types to some PNG files that I have?  
And is there a graphical utility for accomplishing this too?  
I don't want to install any special themes, I just want to change a few icons.

---

### Post by Dennis N on 2015-11-07
Here is a link to a guide for changing the icon for a file type:

[How to change a file type icon in XFCE (Thunar)]("http://unix.stackexchange.com/questions/23776/how-to-change-a-file-type-icon-in-xfce-thunar")

I actually used this once myself to change a file type icon, so it does work.

---

### Post by yoshii on 2015-11-08
hey thanks, Dennis N

I tried to get Assogiate, but it's no longer available for Ubuntu and the developer's site is gone now.  Also, the Debian version failed to install.  
The other instructions look really complex but maybe I'll give it a try.

---

### Post by Dennis N on 2015-11-08
> **yoshi2 said:**
> hey thanks, Dennis N

I tried to get Assogiate, but it's no longer available for Ubuntu and the developer's site is gone now.  Also, the Debian version failed to install.  
The other instructions look really complex but maybe I'll give it a try.

There is a thread about this where changing a file type icon was discussed, and shows some code that worked, based on the article. That is here:

[http://ubuntuforums.org/showthread.php?t=2278819](http://ubuntuforums.org/showthread.php?t=2278819)

What that did was change the icon for certain file type: like the icon for Microsoft Word files to a Libre Office Icon. 

Maybe not what you had in mind. There are mime type icons in your icon theme you might be able to switch to an alternate. Look in /usr/share/icons/your-icon-theme-name for a mimetypes folder. There are more folders inside that with icons of various sizes, and to completely change one type, you would have to change icons for all the sizes of the mime type . You might try to change one or two and see what happens. I suggest you copy the entire icon folder into ~/.icons and work on that set rather than in /usr/share/icons because you don't need sudo to modify the ones in ~/.icons, and you can just delete them if things don't work out well. Icons in ~/.icons also have priority over the others.

---

