---
title: "Enlightenment DR17 - file manager"
date: 2008-06-03
forum: Desktop Environments
---

### Post by Inxsible on 2008-06-03
What is the name of the default file manager for DR17?

I cant say I am a fan of it. It opens multiple windows when you open folders. I know we can get rid of that by enabling the "Open folders in place" config item. But then I cannot go back or forward.

Is there a way to configure this? If not, can someone tell me the name of the file manager so I can un-install it and install thunar in its place?

---

### Post by squaregoldfish on 2008-06-03
To disable the file manager, simply disable the module.

Left-click on the desktop, select Configuration -> Modules

Scroll down the right-hand list to the System section, select File Manager, then Unload Module.

I'm not sure if you can replace the menu entry with something else, but you can edit your favourites menu to include any program you like - file manager included.

Steve.

---

### Post by Inxsible on 2008-06-03
Thanks...I might just go with emelFM2 or pcmanfm. Thunar depends on a few xfce libraries that I dont want to install. 

But another question I have is:

How do we add a new app to the Applications list ?

I have been racking my brains over it for the last hour..and nothing I do in the configuration is helpful.

I would have thought that installing a new app (Mirage in my case) would automatically give me a menu item under Applications. It does not. I don't mind manually putting it there, but how do I do that?

---

### Post by Inxsible on 2008-06-03
I just tried unloading the File Manager Module, but then the desktop icons all disappear and I actually have to go into the File Manager to the Desktop folder to do anything. 

I guess I will have to keep the module around and simply use another app. How can I make emelFM2 the default File Manager for E17 ?

---

### Post by squaregoldfish on 2008-06-05
I don't think you can change the default file manager in e17.

As for adding programs to the Applications menu, do you mean Applications or Favorite Applications?

For the former, e17 uses the standard Desktop Menu Specification, which I believe is used by Gnome and others as well. If your app hasn't added itself to this menu, then it won't have added it to any system menu.

For the Favorites menu, you have to add it yourself, either through the Configuration Panel -> Menus -> Favorites Menu, or by editing the menu by hand (in ~/.e/e/applications/menu/favorite.menu)

Either of these options requires a .desktop file. You can try to find it by typing 'locate <appname>.desktop'. If you can't find the file, that's why it's not in any menus. You might be able to find a ready-made icon on the net, or you can roll your own fairly easily by looking at an existing file and changing the bits you need.

Steve.

---

### Post by Inxsible on 2008-06-05
> **squaregoldfish said:**
> I don't think you can change the default file manager in e17.

As for adding programs to the Applications menu, do you mean Applications or Favorite Applications?

For the former, e17 uses the standard Desktop Menu Specification, which I believe is used by Gnome and others as well. If your app hasn't added itself to this menu, then it won't have added it to any system menu.

For the Favorites menu, you have to add it yourself, either through the Configuration Panel -> Menus -> Favorites Menu, or by editing the menu by hand (in ~/.e/e/applications/menu/favorite.menu)

Either of these options requires a .desktop file. You can try to find it by typing 'locate <appname>.desktop'. If you can't find the file, that's why it's not in any menus. You might be able to find a ready-made icon on the net, or you can roll your own fairly easily by looking at an existing file and changing the bits you need.

Steve.Thanks Steve. I did mean the Applications. I know how to add stuff in the Favorite.

However, I have a ubuntu minimal install and E17 sits on top of it. I installed mirage and it didnt show up under Applications. But when I try to add it in Favorite, it DID show me mirage in list of available apps and I can add it to Favorite. 

But I don't want to add all the apps in my Favorite....you know what I mean?

Is there a way to add an app to the Applications given that I will create a .desktop file for it manually?

i.e. how do I add that .desktop file to the Applications?

---

### Post by squaregoldfish on 2008-06-05
I understand what you're after now.

I think the menu system simply scans a few pre-defined directories for .desktop files, and builds the menus using what it finds. My guess is that, for some reason, the directories used for creating menus, and those for making the list of available applications, are different. I can't tell you where such things are configured, unfortunately.

Looking at my machine, it seems that your first port of call would be to add the .desktop files to ~/.local/share/applications - I've put a few custom e17 icons in there, and they've automatically turned up in my Applications menu.

Steve.

---

### Post by Inxsible on 2008-06-05
> **squaregoldfish said:**
> I understand what you're after now.

I think the menu system simply scans a few pre-defined directories for .desktop files, and builds the menus using what it finds. My guess is that, for some reason, the directories used for creating menus, and those for making the list of available applications, are different. I can't tell you where such things are configured, unfortunately.

Looking at my machine, it seems that your first port of call would be to add the .desktop files to ~/.local/share/applications - I've put a few custom e17 icons in there, and they've automatically turned up in my Applications menu.

Steve.
Alrite, I shall try it out tonight.

---

### Post by leewebb on 2009-06-25
> **Inxsible said:**
> 
I cant say I am a fan of it. It opens multiple windows when you open folders. I know we can get rid of that by enabling the "Open folders in place" config item. But then I cannot go back or forward.

Is there a way to configure this?

To get forward/back/favourite/reload buttons, you need to load the EFM Navigation module, then open up a location using the file manager, right-click on the toolbar (which'll probably be empty at this stage), and use the "Set toolbar contents" item to add the EFM Navigation module

[Better late than never.]

---

### Post by stanca on 2009-10-03
Usually is Thunar.

---

