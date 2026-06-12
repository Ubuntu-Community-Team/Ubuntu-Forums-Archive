---
title: "change shortcut icon on Desktop"
date: 2009-05-30
forum: Desktop Environments
---

### Post by richard_nl on 2009-05-30
Hi,

This is problem probably very simple but I can't figure it out even after searching for a bit. I have a shortcut to eclipse on my desktop. At the moment it shows up as this ugly *** cog wheel icon. I just want to set to a normal eclipse icon. How do I do this? 

When I right click the shortcut I can only select 2 things:
1. Icon settings
2. Desktop options

selecting the Icon settings I only get 1 window with 2 tabs:
1. general
2. permissions

Both these tabs don't offer me to change the icon.
How should I do this?

---

### Post by kerry_s on 2009-05-30
do you got eclipse with the right icon in the menu? if so you could try dragging that to the desktop and deleting the other 1 if it works.

---

### Post by richard_nl on 2009-05-30
Hi thanks for the reply.
> **kerry_s said:**
> do you got eclipse with the right icon in the menu? if so you could try dragging that to the desktop and deleting the other 1 if it works.

I don't have eclipse in my menu at all. Previously I installed eclipse using Adept-Manager. That was the tidiest way which did set up the correct icon and added it under the development category in my menu. 

However adept installs version 3.2.2. This version of eclipse isn't compatible with the pdt extension which I really need. Because of that I downloaded eclipse from [http://www.eclipse.org/pdt/downloads/](http://www.eclipse.org/pdt/downloads/) and installed it manually. 

Eclipse works nicely only it isn't in my menu and it has ugly icon now which sorta irritates me. So is there anyway to correct this?

Thanks in advanced,

Richard

---

### Post by kerry_s on 2009-05-30
i'm sorry i can't even remember kde, i haven't used it in so long. you'll have to wait for a kde user to help you on this 1.
i use xfce4, it's as easy as right click> edit launcher

---

### Post by krazyd on 2009-05-31
@richard_nl: the icon on the general tab is a button. click it. ;)

---

### Post by richard_nl on 2009-05-31
> **krazyd said:**
> @richard_nl: the icon on the general tab is a button. click it. ;)
Hmmm do you mean the wrench icon? When I click that I get an popup with the following message "Could not find the program 'keditfiletype'"

I also tried clicking the icon in the general tab a few times which is a cog wheel pic right now. That didn't work :-k

---

### Post by krazyd on 2009-05-31
How did you install KDE? Is this a clean install?

So you are saying that the cog on the general tab is a button that 'moves' in when you click it, but nothing happens?

---

### Post by richard_nl on 2009-06-01
> **krazyd said:**
> How did you install KDE? Is this a clean install?

I installed it with a kubuntu distro
> **krazyd said:**
> 
So you are saying that the cog on the general tab is a button that 'moves' in when you click it, but nothing happens?
It's just an icon in the panel
Here is what it looks like:
[http://s144.photobucket.com/albums/r197/Dj_Kat/?action=view&current=eclipse.jpg](http://s144.photobucket.com/albums/r197/Dj_Kat/?action=view&current=eclipse.jpg)
Somehow the img bb code doesnt work so I used a link instead

---

### Post by krazyd on 2009-06-02
That property page in your screenshot is for the eclipse *executable* - the actual program - not a link/shortcut. As such, you can't change the icon.

If you create a link/shortcut on your desktop, then you can change the icon.

I thought you said the icon was on your desktop?

---

### Post by STEN1138 on 2012-01-19
In Kubuntu 11.10 you can create a shortcut by right-clicking on the Desktop folder, and selecting create new>link to Application. Fill in the info, most importantly the "run command" for that app. 
  
  Once the shortcut exists you can change the icon by right-clicking on it, and selecting "open with Kate," (or other text editor). In the text editor, shortly after the 'comment' and 'app command' text, you should see something like 'Icon=exec,' (ignore the quotes) change it to  "Icon=(application_name)." 
  If that doesn't work it's likely because the icon name, and the app name are not the same. If that is the case you are going to have to navigate to the program folder and find out the icon name (or download one- see; bottom of this post). 
  An example: for Reconq I go to root>usr>share>applications>kde4 and I see the Reconq application. Really you don't have to find the app, you just have to find something with the correct Icon, and that will likely by the app itself. 
  When you have found that, right-click and "open with Kate" again, and you will see in the text the value you are looking for, i.e. "Icon=(the correct term for the icon)."  
  Write that text into the text editor for your original shortcut, save, and that should do it. 
  
  Finish by reveling in the glory of your new pimped-out shortcut!

  You can't find the right icon? :(
  In that case, download an icon (whatever makes you happy), and place "Icon=(file_path>file_name)" there. 
  Example: Icon=/home/(user_name)/Downloads/ICON.png

---

### Post by justgrant2009 on 2012-01-19
STEN,
Haha, I think this thread was dormant for a while before you posted this, but none-the-less, I was just now looking for how to do this myself and luckily it looks like you posted this an hour ago.  Thank you!

---

