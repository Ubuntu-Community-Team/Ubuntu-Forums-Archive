---
title: "Background image on menus?"
date: 2007-12-13
forum: Desktop Effects &amp; Customization
---

### Post by Blice on 2007-12-13
Hi. 

I can apply background images to panels in Gnome, but I was wondering how I would go about making a background image for menus? Like, on the Applications/Places/System menu, for example, to have the same background image as the panel itself or a different one. 

Thank you! :]

---

### Post by Blice on 2007-12-14
I hope this forum doesn't mind bumps; Thread was a few pages in.


Edit:
Quick note; I don't mind if I have to install another app to do this, or a plugin, or whatever. I just need to know if it's -possible-. Thanks.

---

### Post by Blice on 2007-12-14
Is there any way I can edit the gtkrc for this? Would I have to edit the 'Main menu' widget's source code? Where can I get that source code, and after I edit and compile it, where do I put it so it works OK? Is this even possible?

---

### Post by NilsE on 2007-12-14
Go to any theme in usr/share/themes and pick a theme that has a gtk-2.0 folder with images in it.  You can edit the gtkrc file with a text editor  and see which image is used for the menus and change the image and it will automatically get changed when you refresh the theme in appearences. You may have to tinker with parms unless you make the image exactly the same size as the original.

It should be in a section of the file that looks something like this

style "menu"			= "default"
{
  engine "pixmap"
  {
    image
    {
      function			= BOX
     recolorable    		= TRUE
      detail			= "menu"
      file			= "menu.png"
      border			= { 6, 6, 6, 6 }
      stretch			= TRUE
    }
  }
}

---

### Post by fabsh on 2008-04-16
Sorry... Wrong thread.

---

