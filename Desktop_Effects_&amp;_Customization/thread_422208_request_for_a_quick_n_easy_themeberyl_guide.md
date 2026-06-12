---
title: "request for a quick n easy theme/beryl guide"
date: 2007-04-24
forum: Desktop Effects &amp; Customization
---

### Post by JLAudioFan on 2007-04-24
I find trying to customize the look of ubuntu quite confusing...

Trying to figure out what to change to get the look I want is difficult, especially when I don't know what look I want.

Could someone do a quick write up on how to add themes?  

There's a "Theme" manager listed in system>preferences, but sometimes it works?  Here's what I am looking for:

Take a screenshot of your desktop with a couple windows open.  Mark it up and say "Emerald changes this part" or "Beryl can change this".  A list of file formats for themes, etc, would also help alot.

So far I've figured out that Emerald changes how the window title bar looks.  I don't know how to get a new theme in beryl...

Or, if there's already a nice simple howto or walkthrough, possibly a link to that?  Try and reply assuming I know absolutely nothing about ubuntu or linux (although I know some, I am sure there are others that are totally new to this kickarse OS and have the same questions.)


Thanks!!!

---

### Post by randomstuff on 2007-04-25
I'm sure that it is possible to find the answers to your questions by extensive googling, but I know that that answer is annoying, so I will try to explain it to you:

The remaining sections each describe one part that can be customized. I'm assuming you're using GNOME, I know next to nothing about KDE

**1) boot splash (displayed while booting up)**

don't know much about this one.

**2) login screen (when the machine boots up and prompts you for your password**

System -> Administration -> Login window. Get themes from art.gnome.org

**3) splash screen (displayed while logging in, if enabled)**

System -> preferences -> Splash screen. Get themes from art.gnome.org

**4) Window Manager: window frames, including title bar**

This is where you currently seem to be using emerald. Instead of emerald, you could be using the standard gnome window manager, called metacity. The window manager is responsible for drawing the frame around a window, as well as the title bar and any buttons upon it.

Emerald themes are changed by right-clicking the beryl-manager and opening the emerald theme manager from the menu. You may need to install emerald-themes first before you can select a different:

sudo apt-get install emerald-themes

then open the emerald theme manager again. After selecting a theme, you need to right-click the beryl-manager icon again and select "Reload Window Decorator".

Metacity themes are changed in the gnome theme manager in  Sytem-Preferences. Metacity themes can also be found on art.gnome.org.

**5) applications - buttons, scroll bars, textboxes, window background etc...**

In gnome, gtk themes decide how buttons etc. look in applications (assuming they do use gtk, most do). Themes can once again be found on art.gnome.org, but so far my favorite is one of the pre-installed ones, called glossy. Oh, and application themes are also managed with the gnome theme manager.

**6) icons - icons on all sorts of launchers/shortcuts**

Get them from art.gnome.org, manager them in the gnome theme manager.

**7) wallpaper**

Get them from art.gnome.org or elsewhere. Set them by right-clicking the desktop, select "Change Desktop Background", click on "Add" and select the wallpaper you downloaded.

---

### Post by Guitar Man on 2007-04-25
:guitar: Hi

I have been playing with Beryl (steady!!) as a newbee, for a few days and had the same question - can't find the cursed instructions!!

I hope I'm not teaching granny to suck eggs here.......

**Beryl** is the desktop environment / window settings tool.
**Emerald** is one of the Beryl theme manager applications.  

First of all, **Beryl** will change the way your screen, desktop and windows behave.
**Emerald** will change the looks of toolbars, buttons - buttons "pictures", colours and textures

Do this first:
1. You will need to enable desktop effects from the system / preferences menu.
2. When Beryl is installed and running you should have a red diamond icon, on bottom right of the tool bar.
3. Right click this and go though the settings (don't touch anything you are not sure about!)
4. You will probably need to set the "window decorator" to "standard"
5. If you loose your title bars from the windows or get a corrupt screen :( , a quick  CNTL+ALT+backspace works for me :)  (restarts the x-session)

Right - change your theme:
1. Right click the red Beryl diamond icon and select Emerald Theme Manager (takes a while to load.)
2. Click on a theme you fancy
3. there we go!! (you can tweak the themes colours etc using the edit themes tab but I never bother as they are usually spot on anyway)

Get that fancy, show off 3D cube, desktop thingy to impress your friends!:
1. Close Emerald, right click the diamond again and chose Beryl Settings Manager (takes a while to load.)
2. Aggrrr! I hear you shout - what a scary array of settings - **[COLOR="Red"]don't mess with too many at once and write down what you change!![/COLOR]**
3. Make sure the desktop effects are on as mentioned earlier - press shift + F9 (toggles the rain on and off) or hold CNTL + windows start key and move the mouse (clever huh!?)
4. The main things you will probably want are probably already on but in the Desktop and Visual Effects menus - turn on the desktop cube, 3D effects and animations.
5. I'll say it again...**[COLOR="Red"]don't mess with too many at once and write down what you change!![/COLOR]**
6 To "populate" the cube with windows, spin to each face and open an application on each one (CNTL + ALT + leftmouse and move mouse or CNTL + ALT + arrow keys or hover over desktop and use mouse scroll wheel.)
7. Pictures can be added to the top and bottom faces (called "caps" in Beryl settings.)
8. If all your windows suddenly spring up in thumbnail format (hovering over the top right of a window causes thsi - turn the stupid thing off!!) just spin the cube or click an empty desktop.
9. there, I think that will do you for now!!
If this font is too small, try holding the windows key and scrolling the mouse wheel!!!
[http://www.gnome-look.org/](http://www.gnome-look.org/) has a fantastic array of quality wallpapers and themes.
Also there is a Beryl wiki site (*when they mention the "super" key they mean the windows/ start key*)

---

### Post by JLAudioFan on 2007-04-25
Wow, thanks guys!  This is a lot of useful information, and I really appreciate it!  I think I have a pretty good idea of how the themes/window managers work now.

Thanks again!!

---

### Post by raun on 2007-06-23
yes, very helpful advice!  thankyou!

---

