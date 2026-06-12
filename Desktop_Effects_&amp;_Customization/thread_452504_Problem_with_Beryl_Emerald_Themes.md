---
title: "Problem with Beryl Emerald Themes"
date: 2007-05-23
forum: Desktop Effects &amp; Customization
---

### Post by cl_audio on 2007-05-23
Hey! I have been using Ubuntu now for quite some time and decided to look into beryl. After a successful install I attempted to change the theme. Using the emerald theme manager I selected a new theme. Now I noticed that one I reload the theme all that is changed is the top bar of the windows, not the buttons, not the start menu, etc. I can send screenshots or give more info if anyone would like that.


So to recap:
-applied new theme (using emerald)
-only windows border is active with theme
-Start menu, buttons, backgrounds, interior window are NOT themed. Just basic gray on square boxes.

Thanks! and hope someone will help me soon!!

---

### Post by Kobalt on 2007-05-23
This is normal. To change the buttons, backgrounds, etc. you can use a different GTK2 theme. You'll find many of them on [www.gnome-look.org](www.gnome-look.org). 
Once you've downloaded them, extract these and install them from System > Pref. > Themes.
The "start" menu is changable through the installation of different applications, while you can edit the panels from a right-click and Properties.

---

### Post by crimesaucer on 2007-05-23
Also...if you look in your Emerald Theme Manager, and look at the left hand column that has the name of every Emerald theme in bold print, now look underneath the name, and you will see the description of the theme.

Then there are three lines that are 1.) Version number 2.) Created by.....and 3.) Use With.

Now some of those themes will have the name of the gtk theme that the Emerald theme is pictured with...or is suggested to be Used With.

So now you know what theme to search for at Gnome-Looks.org or Xfce-Looks.org to make it look like the Emerald pictures.

---

### Post by bewareofthecow on 2007-08-13
This makes more sense as I'm having a similar problem as the original poster. The screen shots in emerald themes are misleading as they almost imply that they change window colours and such. 

My question is how do I manually change the colour of the translucent selection rectangle and drop down selection menu highlighting? I can't find anything in system > pref > themes for that.

---

### Post by VictorR on 2007-08-13
> My question is how do I manually change the colour of the translucent selection rectangle and drop down selection menu highlighting? I can't find anything in system > pref > themes for that.
By default these cannot be changed. It depends on how the particular GTK theme was designed. Let clarify some things. What you see on your screen or on theme previews consists of following independent parts:
1. GTK theme - how buttons, entry/combo boxes, menus... are drawn.
2. Icon theme - common icons and pictures on the buttons
3. Metacity or Emerald theme - window borders and titles

Most of the GTK themes from Gnome-look.org don't allow changing colours, as they use hard-coded colours inside. Those which use custom colours (System - Pref - Themes - Colors are enabled) can play with six colours only (from the mentioned dialogue above), the rest is again hard-coded ones or combinations of the six.

There is a GUI tool called Gnome Color Chooser you can try - find it among Best Rated in Metacity or GTK themes on Gnome-look.org. Let us know if it helped, this tool I mean.

---

### Post by Speedbird787 on 2008-01-04
I have emerald theme manager and i have downloaded a couple of themes and was able to successfully import themes in emerald manager ... but I am unable to apply those themes ... i tried double click and everything but nothing works :(
i can see themes in emerald theme manager but they are not working :( ... anyone up for help !!? :confused:

---

### Post by cl_audio on 2008-01-04
Sorry dude, No help from me... I still am yet to find any help from anyone, thats why I decided to switch back to windows....




Also, for next time, just so you don't get in any trouble from the mods, try starting your own thread instead of hi-jacking others...

---

### Post by ispy on 2008-01-04
> **Speedbird787 said:**
> I have emerald theme manager and i have downloaded a couple of themes and was able to successfully import themes in emerald manager ... but I am unable to apply those themes ... i tried double click and everything but nothing works :(
i can see themes in emerald theme manager but they are not working :( ... anyone up for help !!? :confused:

Don't hijack the thread. start a new one. try clicking one, logging out, and logging back in. worked for me... :)

---

### Post by shifty2 on 2008-01-04
Select the theme that you want to use as if you would then want to click an apply button. Press alt-f2 then type

```
emerald --replace
```

your screen should refresh with the new theme

---

### Post by VictorR on 2008-01-04
> 

Code:

emerald --replace

your screen should refresh with the new theme 


The above should start Emerald immediately. In CompizConfigSettingsManager enable Window Decorations, and put the same command
emerald --replace
into "Command" field, to launch it automatically along with Compiz-Fusion.

---

