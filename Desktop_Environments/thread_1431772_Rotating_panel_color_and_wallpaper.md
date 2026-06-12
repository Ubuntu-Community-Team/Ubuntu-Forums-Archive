---
title: "Rotating panel color and wallpaper?"
date: 2010-03-17
forum: Desktop Environments
---

### Post by opethfan89 on 2010-03-17
Hi all.

Would it be possible to write a script or something that allows me to change the color of my panels to match that of my desktop wallpaper, and have it rotate at regular intervals? 

Also, is it possible to enable different wallpapers on each of the different workspaces? I've seen screenshots of this and I know KDE has it but I have not seen it in gnome

I am running ubuntu 9.10 64-bit.

Thanks, opethfan89

PS: I typed this post from my itouch....what a pain!!!

---

### Post by bignol on 2010-03-17
i dont know if its different in 9.10, but i'm using 9.04 and all i did was right click in the panel near the three horizontal lines. go to properties.

im uncertain about having two seperate desktop backgrounds

---

### Post by sikander3786 on 2010-03-17
Hi you can do it with compiz.

> 
 Re: Can I Make Each Workspace Have a Different Wallpaper
To have different wallpapers for each desktop, follow these steps:

I. Disable "show desktop" in Nautilus
1. ALT+F2
2. gconf-editor
3. Apps --> Nautilus --> Preferences
4. Untick "show desktop"

II. Install Compiz Fusion
1. In Terminal, input the following:
Code:

sudo aptitude install compizconfig-settings-manager

2. Exit Terminal

III. Select your desktop wallpaper
1. System --> Preferences --> Advanced Desktop Settings
2. Tick "Desktop Cube" and opt to disable desktop wall if prompted
3. Tick "Rotate Cube"
4. Select "Desktop Cube"
5. Click "Appearance" tab
6. Click "Add" under the "Background Images" field
7. Browse for your desired wallpaper(s), ordering them based on which face of the cube you want them to appear


But you will have to give up all your dekstop icons.

Not sure about panel colors.

Regards.

Sikander.

Edit: If you want the panel to follow the color of your wallpaper, just set it to such a transparency that suits you. That's the easy way.

---

### Post by mcduck on 2010-03-17
Actually changing the panel color from a script would be quite easy thing to do, as the setting is stored in gconf and you can use gconftool-2 to set gconf keys from command line.

The wallpaper is set through gconf as well, so syou cna use the same method for it (or alternatively just create .xml wallpaper to get Nautilus to automatically change the wallpaper at set times with nice smooth transitions)

Getting different wallpapers for each desktop is a bit harder, Gnome/Nautilus has no support for that and like mentioned above, you can do it with Compiz but then you'll loose all the icons and the right-click menu on your desktop.

---

### Post by opethfan89 on 2010-03-17
@Sikander
Thanks for the response. I'm not -that- crazy about rotating wallpapers to lose my desktop icons and right click capabilities, just thought it would be cool to have.

@Mcduck
Would you be able to instruct me how to make said script, or at least reference me to a website that does so? I'm not terribly knowledgeable with scripting.

Thanks,
Opethfan89

---

### Post by drreed on 2010-04-19
> **mcduck said:**
> Actually changing the panel color from a script would be quite easy thing to do, as the setting is stored in gconf and you can use gconftool-2 to set gconf keys from command line.

The wallpaper is set through gconf as well, so syou cna use the same method for it (or alternatively just create .xml wallpaper to get Nautilus to automatically change the wallpaper at set times with nice smooth transitions)

Getting different wallpapers for each desktop is a bit harder, Gnome/Nautilus has no support for that and like mentioned above, you can do it with Compiz but then you'll loose all the icons and the right-click menu on your desktop.


This is the sort of answer I look for.

Having just spent 12 hours removing compiz, emerald, and repairing the havoc wrought, I think the other suggestion qualifies as a "destructive command" :)

In my opinion, compiz-fusion and Emerald are malwarez. You might as well tie a ships anchor to your penguin.

---

