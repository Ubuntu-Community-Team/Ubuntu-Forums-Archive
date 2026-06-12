---
title: "add icons to application menu in Xfce..."
date: 2008-08-25
forum: Desktop Environments
---

### Post by nicedog on 2008-08-25
hi,

tried the menu editor from the setup screen... only able to open the menu for system (recalled 3 entries,including sytem and quit... none for applications), is it a bug for menu editor?

note that i am using Xubuntu ...

---

### Post by kerry_s on 2008-08-25
> **nicedog said:**
> hi,

tried the menu editor from the setup screen... only able to open the menu for system (recalled 3 entries,including sytem and quit... none for applications), is it a bug for menu editor?

note that i am using Xubuntu ...

no, not a bug the editor just sucks.
[http://xubuntu.wordpress.com/2006/07/12/manually-edit-the-xfce-menu/](http://xubuntu.wordpress.com/2006/07/12/manually-edit-the-xfce-menu/)

---

### Post by nicedog on 2008-08-25
> **kerry_s said:**
> no, not a bug the editor just sucks.
[http://xubuntu.wordpress.com/2006/07/12/manually-edit-the-xfce-menu/](http://xubuntu.wordpress.com/2006/07/12/manually-edit-the-xfce-menu/)

tks for your reply...

probably due to my location/region, i am not able to the site you referred.

would u mind to copy and paste of its key content in reply?

tks!

---

### Post by kerry_s on 2008-08-25
> **nicedog said:**
> tks for your reply...

probably due to my location/region, i am not able to the site you referred.

would u mind to copy and paste of its key content in reply?

tks!

alright:
> Manually edit the Xfce menu
July 12, 2006 at 9:43 am | In tips and tricks, xubuntu |

Let’s face it, the built-in Xfce menu editor sucks. It leaves invalid XML and crashes at the oddest moments. If you’re feeling adventurous, you can manually edit the menu yourself. If you’re familiar with XML, this will be easy.

1) Copy Xfce’s default menu into your home folder:

cp /etc/xdg/xfce4/desktop/menu.xml ~/.config/xfce4/desktop/menu.xml

Here’s an overview of how the code works:

<xfdesktop-menu></xfdesktop-menu>: You need these! Otherwise, the menu is not loaded.

<app name="Name in menu" cmd="Command to run" term="false" icon="iconfile" snotify="false" visible="true" />:

To add a shortcut to an application, use <app>.

name tells the menu what the name of your shortcut is.

cmd says what is launched when you click the shortcut.

If you want a shortcut icon, put the full filename of the icon under iconfile.

snotify sets whether or not the program supports startup notification. (You can probably leave this to false.)

visibility tells the menu whether you want to see this shortcut or not. You should leave it to true.

<separator /> : Adds a separator between shortcut items.

<menu name="Name in menu" icon="iconfile" visible="true"></menu> :

This acts the same as app. However, this creates a menu, where you can put more shortcut items within. Make sure that you put </menu> afterwards when you are done!

<title name="Name in menu" icon="iconfile" visible="true" /> : Adds a title to the top of your menu (Where it currently says “Desktop Menu”).

<include type="file" src="menu2.xml" visible="true" /> : Allows you to add another menu file within a menu file. Under src, put the filename of this menu. This can serve as a backup in case one goes corrupt.

<include type="system" style="simple" unique="true" visible="true" /> : This code allows you to put in the system-generated menu. Use this if you want your menu file to be automatically updated when you install a new program.

<!-- 'comment' --> :
Use this to add comments within your menu. This will not show up in the menu. Obviously, replace ‘comment’ with your own comments.

2) Edit the menu:

mousepad ~/.config/xfce4/desktop/menu.xml

The rest is self-explanatory. Scroll down to <xfdesktop-menu>, where the menu starts, and change whatever you see fit. It’s very easy once you get used to it!

---

