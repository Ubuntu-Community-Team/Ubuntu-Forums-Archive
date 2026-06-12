---
title: "copy ubuntu/gnome menus to xubuntu/xfce menu?"
date: 2011-10-30
forum: Desktop Environments
---

### Post by Kilarin on 2011-10-30
running Ubuntu 11.04, recently installed xubuntu-desktop to avoid unity.

Under my Ubuntu/Gnome menus, I had sorted my applications into different sub folders.  For example, I had my games menu split up into different sub folders for different kinds of games.

When I moved to xubuntu, I lost all of that, and most of it ended up in the "other" menu.    

Obviously I can rebuild the same structure again, create the needed folders, move each application into the correct folder one at a time.  BUT, I was hoping there was a simpler way to do this.

Is there a way to directly copy my old ubuntu/gnome menu structure into the xubuntu/xfce menus?

thanks!

---

### Post by NTL2009 on 2011-11-02
I was curious, as I've been setting up and trying out some new systems and have the same question.

I have not looked into XFCE/Xubuntu yet, but both Ubuntu and Kubuntu save a file in ~/.config/menus. They have similar header info (references to 'DTD Menu 1.0....', but the format looks a bit different. It seems the file is not created until you actually edit the menu from the default. 

Not sure if it would be any easier to edit that file, but you could compare them and see.

-NTL2009

---

### Post by Kilarin on 2011-11-03
> I have not looked into XFCE/Xubuntu yet, but both Ubuntu and Kubuntu save a file in ~/.config/menus
Yep, they have a menu file in the same folder.  It CAN be edited, which, in some circumstances, is faster than using the GUI.  Thank you for the advice.

Still seems to me that we need an automated way to convert the menus between different versions of the desktop.

---

### Post by NTL2009 on 2011-11-03
Or better yet, if we had a set of application launchers for each of the derivatives that all use the same format for that menu file.

People keep talking about the flexibility of Linux to load whichever Desktop Environment you prefer, and that's great, but every time I try something I can spend so much time configuring this and that, finding that ABC is available in one set, but not in another (or the config is different), so I have to find the XYZ equivalent and learn it's ins/outs/configs - it's more than many people would want to spend time doing.

Sure, there are going to be differences due to the underlying libraries, but some added standardization across the basics would be helpful, I think.

-NTL2009

---

### Post by gsmanners on 2011-11-03
> **NTL2009 said:**
> ... but some added standardization across the basics would be helpful, I think.

-NTL2009

You mean, like this: [http://standards.freedesktop.org/menu-spec/menu-spec-1.0.html](http://standards.freedesktop.org/menu-spec/menu-spec-1.0.html)

---

### Post by NTL2009 on 2011-11-03
> **gsmanners said:**
> You mean, like this: [http://standards.freedesktop.org/menu-spec/menu-spec-1.0.html](http://standards.freedesktop.org/menu-spec/menu-spec-1.0.html)

Yes, it appears so! Thanks.
 
I couldn't quite get thru all the techno-talk there - is/are there actual application launcher packages available for Ubuntu and the derivatives that I could install (or are these just tools for developers to use?)? If available, I would certainly like to try them out. I do a fair amount of customization of my desktops and panels, and it takes a lot of time. This would help, and the concept should (IMO) be applied to as many user interface areas as possible, to ease transitions.

-NTL2009

---

### Post by gsmanners on 2011-11-03
Standards are primarily for the devs, yes. The tools are mostly still a work in progress right at the moment. You can use leafpad and your understanding of that standard to edit the menus right now if need be.

---

### Post by Kilarin on 2011-11-04
[quote="NTL2009"]This would help, and the concept should (IMO) be applied to as many user interface areas as possible, to ease transitions.[/quote]

Yes, that would be fantastic.  If you could switch between desktops and have your menus transfer seamlessly between them.

---

