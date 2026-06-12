---
title: "Different wallpaper for each desktop"
date: 2009-11-10
forum: Desktop Environments
---

### Post by psyboy55 on 2009-11-10
i looked at some tutorials and i got all the way to the part with compiz settings manager. I went to desktop cube and appearance but there was nothing for backgrounds! It should have been right above cube caps but it isn't! Can anyone help me? Also is there any way to delay or stop the desktop change when i have the mouse at the side of the screen? it's kinda annoying when i'm reaching for the scroll bar. 

P.S. this is kinda random but is it possible to have a wallpaper changer for each desktop?

---

### Post by RedSingularity on 2009-11-11
To your first problem:

Check in System>Prefs>Compiz settings manager.
Go to the "desktop" part.  Look for rotate cube.  In there make sure "edge flip pointer" and "edge flip move" are unchecked.  See if that solves it.

As for your second question:  I am not sure if you can have different wallpaper on each side of the cube.  I have never seen it before though.  I do know that the cube caps can be different.

---

### Post by psyboy55 on 2009-11-11
You solved one of my problems. I think when compiz settings manager was updated they moved the backgrounds option to a different place. Im running 9.10 if that helps.

---

### Post by RedSingularity on 2009-11-11
Ok if you want to change the backround go to System>Prefs>Compiz and click the "desktop cube".  Change the "skydome" in appearance tab for a picture.  And make sure skydome is on with a check mark.

---

### Post by psyboy55 on 2009-11-11
I know how to do that but i want to change the desktop on each side of the cube.Here is the tutorial i was looking at. I can't get passed step section 3 step 6. >  Re: Can I Make Each Workspace Have a Different Wallpaper
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

---

### Post by RedSingularity on 2009-11-11
Well i just checked that myself.  I dont even see the option that the guide refers to.  You sure it wasn't for a older version of the compiz settings manager?

---

### Post by psyboy55 on 2009-11-11
Thats what im thinking. In the newer version they probably moved it somewhere. But where! i Doubt they would actually take it out.... May be there is a more up to date tutorial somewhere?

---

### Post by RedSingularity on 2009-11-11
Maybe.......but you never know.  They could have removed it.  I have actually never seen any screen shots of compiz with different wallpaper on each side of the cube.

---

### Post by psyboy55 on 2009-11-11
Well they could have gotten rid of it. Here is a image. Wouldn't there be some kind of plugin to do this if they did get rid of it?
[IMG]http://allforlinux.com/2008/09/how-to-get-a-different-wallpapers-on-each-workspaces-in-ubuntu/[/IMG]

---

### Post by psyboy55 on 2009-11-11
I Got it! They actually renamed it as "wallpaper" under Utility. Here is a tutorial [http://ubuntuguide.net/different-wallpapers-on-each-workspace-in-ubuntu](http://ubuntuguide.net/different-wallpapers-on-each-workspace-in-ubuntu)

---

### Post by RedSingularity on 2009-11-11
Wow.  That pretty cool actually!  I never knew about this effect.

---

