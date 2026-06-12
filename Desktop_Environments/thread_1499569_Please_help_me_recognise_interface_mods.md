---
title: "Please help me recognise interface mods"
date: 2010-06-02
forum: Desktop Environments
---

### Post by Istrebitel on 2010-06-02
Greetings!

I am new to Kubuntu and i dont yet know how to fully set up its interface. I looked for some settings and tried every option in "All Effects" and i could achieve some eyecandy but...
I've seen this video [http://www.youtube.com/watch?v=xC5uEe5OzNQ](http://www.youtube.com/watch?v=xC5uEe5OzNQ) and it shows pretty nice interface quirks i dont pretty know how to activate or install.

What i am interested in partiular:
- Windows "magic lamping" into their buttons with percision
- Cube having no top and bottom (my cube has KUBUNTU written there and blue background and this is not pretty transparent so i cannot clearly see through the top o the back side of the cube) 
- Cube has a nice 3d background like you are in some room with that creature and stones
- That panel with some icons that can be thrown around
- Windows burning with magical flashes
- Hovering over a window button makes i briefly appear over other windows, transparent

PS: Also, could anyone please tell if there is a convinient method of switching themes at once? 
Because i have a very dark theme i would like to switch to a brighter one in order to, for example, edit word documents etc. This theme is called Ghost and i installed it with built-in installer. It required changes in numerous places (wallpaper, plasma desktop, windows decoration, color scheme,..). In order to change to another scheme, i would have to go through all those menus and manually switch everything there, but i would like to be able to do it with one click, from one template (Ghost wallpaper, plasma,color scheme, window decoration) to another (Default wallpaper, .....). Is that possible at all?

---

### Post by Zorael on 2010-06-02
Those window effects are from using the old Beryl window compositor, nowadays superseded by Compiz. By default Kubuntu uses KWin for window management, decoration and compositing, and KWin doesn't have equavilents to all of Compiz's plugins. But you could just install it and change to it.

```
$ sudo aptitude install **compiz compizconfig-settings-manager compiz-kde compiz-fusion-plugins-extra**
```

Then in Default Applications in System Settings, set the Window Manager to be Compiz. Log out and back in. You'll find the Compiz configuration tool in your menu - else you can just run **ccsm** to start it manually.

If you find that the window manager that Compiz uses (kde-window-decorator from **compiz-kde**) crashes a lot, you may have better luck with **Emerald**, though it uses its own window decoration themes and is not compatible with KDE's normal theming. You can find some themes over on [kde-look.org](http://kde-look.org/index.php?xcontentmode=102), confusingly named as "Compiz themes".

Emerald is also available from the repositories, package name **emerald**. There used to be an **emerald-themes** package, but it was removed some releases back. Perhaps due to licensing issues, I've no idea. Also, note that you will have to use Emerald's own theme manager to change your decoration theming. It should be in your menus - else the binary should be called **emerald-theme-manager**.

As for the panel, I think that's **Avant Window Navigator**, package name **awn**. Do a textual search for that on these forums for help on how to set it up. I haven't used it much myself as I'm pathologically short on vertical screen budget (1024x600 on a 10" screen).

---

### Post by Istrebitel on 2010-06-03
But isnt there a way to expand "all effects" list? for example there is only one entry in the "eyecandy" group - the "snow". I dont belive there is no way to add to this list, seeing how you can download themes, schemes and window decorators in a blink of an eye!

I just dont want to install that solution of yours .... yet... because as you said, it crashes and stuff, so i'd like to stick to standart kde means of decoration for now... or am i wrong somewhere ?

---

