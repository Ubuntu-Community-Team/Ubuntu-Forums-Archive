---
title: "beautifying my XFCE !! BUT.."
date: 2007-08-30
forum: Desktop Effects &amp; Customization
---

### Post by smokinjoe on 2007-08-30
Does anyone know how to get rid of "right-click desktop menu" Icons ???

I want my right click menu with no icons on it.. You know.. just like Fluxbox menu

Sometimes, I can get my menu the way I want, with no icons, but with a blank space where the icons are supposed to be.. anyway.. however the icons later, keep coming back

Anyone could help me ????

Thanks a lot !

---

### Post by Slychilde on 2007-08-30
To get the XFCE menu completely editable is a big pain in the butt and rather obscure.  [Here]("http://xfce.wikia.com/wiki/Frequently_Asked_Questions") is a link to the instructions among other things.
> 
cp ~/.cache/xfce4/desktop/menu-cache-name-of-the-generated-file.xml ~/.config/xfce4/desktop/menu2.xml
cd ~/.config/xfce4/desktop/
cat menu.xml > menu3.xml
cat menu2.xml >> menu3.xml
mv menu.xml menu.orig.xml
mv menu3.xml menu.xml

Now, you already have a menu with all the categories in the main tree with some duplicates, but you must first edit menu.xml with your favorite editor and remove the 4 following lines in the middle of the file, otherwise the menu editor will complain about a wrong format:

</xfdesktop-menu>
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE xfdesktop-menu>

<xfdesktop-menu>


After you do that, you can completely edit your right click menu, including changing or removing the images.  To get rid of the images, go to the menu editor, double click on an entry, click on the image, then click the clear button in the lower right.  Hopefully that works.

Edit: I reread your post and it looks like you already did this.  I don't think you can get rid of the blank space to the left of the entry. Sorry!

---

### Post by smokinjoe on 2007-09-01
there must be a way to get rid of the blank space.. I know it's silly.. but my fun is customize linux.. you know.. that's the point of linux over windows: more customization things.. hehe

take a look at this screenshot, please

[http://fc01.deviantart.com/fs15/f/2007/037/0/f/Xfce_070207_by_thrynk.png](http://fc01.deviantart.com/fs15/f/2007/037/0/f/Xfce_070207_by_thrynk.png)

thanks!

---

### Post by Lord Illidan on 2007-09-01
Forgive me if I look like an ***, but what's wrong with that pic?

---

### Post by urukrama on 2007-09-01
It is not very difficult to get rid of the icons in the menu on your panel. Right click on the menu icon, click Preferences, and untick the box 'show icons in menu' (at the bottom). I'm not too sure how to achieve this for the desktop menu, though. At least in the dapper version of xfce, removing the icons from the panel menu doesn't affect the desktop menu. Perhaps that was fixed in a later version. Try it out, and let me know if it works.

---

### Post by Stan_1936 on 2007-09-01
> **smokinjoe said:**
> ....[http://fc01.deviantart.com/fs15/f/2007/037/0/f/Xfce_070207_by_thrynk.png](http://fc01.deviantart.com/fs15/f/2007/037/0/f/Xfce_070207_by_thrynk.png)...

What theme is that?

---

### Post by smokinjoe on 2007-09-01
I gonna search in the Arch forum!! They are geekier than us!! hehehe

Cheers!

---

### Post by smokinjoe on 2007-09-10
just figured out yesterday. To get rid of the icons With the blank spaces left in desktop menu,

Just add this in your .gtkrc-2.0 archive:

gtk-menu-images = 0

that's all !!!

cheers!

---

