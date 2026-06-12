---
title: "Mutiple Desktop Customizations"
date: 2007-12-01
forum: Desktop Effects &amp; Customization
---

### Post by dethredic on 2007-12-01
I am a long time windows user, and I would like to be able to change a couple settings which I am so used to from windows.

I change / edit my screen information via Terminal -> gksudo nvidia-settings. Refer to #4 and 5.

[COLOR="Gray"]1) In Firefox, when the scroll wheel is clicked / held down but not on a link, I would like the up down thing to appear (little circle with up down arrow in windows), so that when I move my mouse above / below where I clicked the page will scroll accordingly. **_- [COLOR="Red"]COMPLETED[/COLOR]_**[/COLOR]

2) Is there anyway to have multiple "Windows Key" Keyboard shortcuts like Windows? I am very accustom to "Windows Key" + D for desktop, and "Windows Key" + E for My Computer (Home Folder in Ubuntu) and being able to do this would help greatly.
[COLOR="Gray"]
3) Is there any way to make keyboard shortcuts for applications? Such as "Ctrl+ Alt + T" runs Terminal.[/COLOR] **[COLOR="Red"]- COMPLETED[/COLOR]**

[COLOR="Gray"]4) I have 2 monitors, the right one is on the right side and the left one is on the left side (which is what I want :P), but the taskbars are on the right screen whereas I want them on the left one. I have them set up as Separate X screen, with Xcinima enabled. This is probably due to my left screen being screen 1, and my right screen being screen 0, The only problem is I can't switch it. Any ideas?[/COLOR] **_[COLOR="Red"]- COMPLETED[/COLOR]_**

5) When I decided to use a wallpaper picture instead of just a solid colour, none of the options work well for my two screens. If possible I would like it so there is one image on one screen and another on the other screen, but it is not that big of a deal. The main problem, is that if I I use stretch or zoom, it covers both of the screens as if they were 1. I would prefer if the image appeared twice, scaled to fit each screen separately.

6) Can I remove the "Wired network connection" icon from beside the date/time?
[COLOR="Gray"]
7) Can I remove the games / other options from the Applications menu on the top left?**_ - [COLOR="Red"]COMPLETED[/COLOR]_**[/COLOR]

8 ) Is there any way to hide a window from appearing in the bottom taskbar? I want the Pigeon window open 100% of the time, on my left screen, and It would be handy if I could remove it from the bottom taskbar, and control it from the icon in the top taskbar. You probably can't do this, but I decided to throw this out there.

[COLOR="Gray"]9) Where can I get the default Ubuntu 6.10 wallpaper (default Avatar image)[/COLOR] [COLOR="Red"]**_- COMPLETED_**[/COLOR]

So Ya, if you can help with one, or all of them it would be appreciated.

---

### Post by rainwalker on 2007-12-01
1) In Firefox, go Edit > Preferences > Advanced > "General" tab, and under Browsing check the box for "Use autoscrolling" (I don't know why it's disabled by default, probably has to do with the middle-click paste function)

2) There might be a way with Compiz Fusion, to set shortcuts like that, I'll look

3) There is probably a way to do that, but I'm not aware of it

4) I don't know anything about dual monitors, sorry

5) Same as #4, but I think I've seen that done in some places

6) I think you can right-click on it and remove it, but I'm not sure

7) Right-click on the menus and choose "Edit menus", or go System > Preferences > Main Menu

8) I only know how to do this with Compiz Fusion, are you running it?

9) Try a Google Image search, that's where I went to find the Dawn of Ubuntu wallpaper
That, or you could search Flickr or other photo sites

---

### Post by dethredic on 2007-12-01
> **rainwalker said:**
> 1) In Firefox, go Edit > Preferences > Advanced > "General" tab, and under Browsing check the box for "Use autoscrolling" (I don't know why it's disabled by default, probably has to do with the middle-click paste function)

2) There might be a way with Compiz Fusion, to set shortcuts like that, I'll look

3) There is probably a way to do that, but I'm not aware of it

4) I don't know anything about dual monitors, sorry

5) Same as #4, but I think I've seen that done in some places

6) I think you can right-click on it and remove it, but I'm not sure

7) Right-click on the menus and choose "Edit menus", or go System > Preferences > Main Menu

8) I only know how to do this with Compiz Fusion, are you running it?

9) Try a Google Image search, that's where I went to find the Dawn of Ubuntu wallpaper
That, or you could search Flickr or other photo sites

1) Works great

2) Whats Compiz Fusion???

3) No ploblem

4/5) No problem

6) If it was that easy I would have got it :P

7) works great, why didn't I think of that?

8) Whats Compiz Fusion??

9) Well, nothing under Ubuntu Wallpaper in the first couple pages..

---

### Post by rainwalker on 2007-12-01
Are you running Gutsy? If so, Compiz Fusion is included. 
Basically, it's software that lets your computer do all kinds of neat things, if your video card supports it. Here are some sites if you want info:
[http://www.compiz-fusion.org/](http://www.compiz-fusion.org/)
[http://en.wikipedia.org/wiki/Compiz_Fusion](http://en.wikipedia.org/wiki/Compiz_Fusion)
[http://wiki.compiz-fusion.org/](http://wiki.compiz-fusion.org/)

---

### Post by dethredic on 2007-12-01
I am running whatever come default with Ubuntu.

From google images, I think it is Gusty.

---

### Post by rainwalker on 2007-12-01
You can check by going System > Administration > System Monitor, under the "General" tab

Anyway, if you're running Gutsy (the latest release of Ubuntu), you can go System > Preferences > Desktop Effects

If you can or already have desktop effects enabled, then that means you're running Compiz Fusion. If you don't have it enabled, or can't enable it, then I can't really help you

CF is what handles all the eyecandy and nifty effects, but you can also use it for productivity. For that, you can install a utility called CompizConfig Settings Manager. To do this, go to System > Administration > Synaptic Package Manager and search for "compizconfig". Install the package named "compizconfig-settings-manager".

---

### Post by dethredic on 2007-12-01
ok, that step seemed to work flawlessly.

Edit - found the option sin preferences.

EDIT - how do these changes take effect??

---

### Post by rainwalker on 2007-12-01
What changes?
Enabling Desktop Effects should take place immediately
Anything you edit in CompizConfig Settings Manager should happen immediately, too

Of course, to use the settings you set in CompizConfig, you have to choose "Custom" for your desktop effects setting

---

### Post by vjones777 on 2007-12-02
> **dethredic said:**
> 

2) Is there anyway to have multiple "Windows Key" Keyboard shortcuts like Windows? I am very accustom to "Windows Key" + D for desktop, and "Windows Key" + E for My Computer (Home Folder in Ubuntu) and being able to do this would help greatly.


One thing I've found useful is the ability to use the Win key to pull up the main (Applications) menu to save having to move to the mouse.  To do that,  
Open your "System" menu, "Preferences", and then "Keyboard".

In the "Keyboard Preferences" window, open the "Layout Options" tab.

Click "Alt/Win Key Behavior." Select the "Add the standard behavior to Menu key." radio button.

Close that window, and go back to "System" -> "Preferences" -> "Keyboard Shortcuts."

Under Desktop, you should have "Show the panel menu" set to Alt+F1. Click it. Now hit the windows key and close that window.

To get Win+key working have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=208795").  Some of the linked posts note that you may have to use Mod4 rather than Super_L.

After reading those posts I managed to get "Win+e" to open Nautilus
```

gconf-editor  (Applications -> System Tools -> Configuration Editor)
go to apps -> metacity -> keybinding_commands, and choose a command, eg command_1. Edit command_1 to nautilus 

Then in global_keybindings, Edit command_1 to read <Mod4>e
```
But to get that to work I had to revert the opening applications menu back to Alt-F2.  :-(  

> **dethredic said:**
> 3) Is there any way to make keyboard shortcuts for applications? Such as "Ctrl+ Alt + T" runs Terminal.


Open  "System" -> "Preferences" -> "Keyboard Shortcuts."

Under Desktop, find "Run a terminal" and press CTRL ALT t
Save it.  

For other keyboard shortcuts a couple of useful links are
[ Creating Application specific shortcuts]("http://www.codejacked.com/create-custom-keyboard-shortcuts-in-linux/") and
[ More detail on app specific shortcuts]("http://ubuntuforums.org/showthread.php?t=333265")
Note that shortcuts are specific to each user, so different users can define their own.

---

### Post by dethredic on 2007-12-02
> **vjones777 said:**
> 
To get Win+key working have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=208795").  Some of the linked posts note that you may have to use Mod4 rather than Super_L.

After reading those posts I managed to get "Win+e" to open Nautilus
```

gconf-editor  (Applications -> System Tools -> Configuration Editor)
go to apps -> metacity -> keybinding_commands, and choose a command, eg command_1. Edit command_1 to nautilus 

Then in global_keybindings, Edit command_1 to read <Mod4>e
```
But to get that to work I had to revert the opening applications menu back to Alt-F2.  :-(  



Ok, this is not really working for me. Now whenever I press the windows key (with no other key or any key) it opens my home folder.

---

### Post by skjoldfetter on 2007-12-02
5) - got this problem myself.. :P

6) you can right click anything on the task bars and remove it, or the entire bar if you wish, or rightclick an empty space on the bar and add stuff
the wired connection thingy is in the system tray though, so to remove that you'd have to remove the other programs too

(forgot the number, the move taskbars one) you can drag taskbars anywhere you want

---

### Post by benzo8 on 2007-12-02
Pidgin can be hidden on the task bar using the Pidgin Extended Preferences:

```
sudo apt-get install pidgin-extprefs
```

Press Ctrl-U in Pidgin, select the Pidgin Extended Preferences plugin and ensure that "Show buddy list entry in taskbar" is not checked. (I believe it defaults to not-checked, so just installing the plugin should hide the entry in the taskbar for you.)

---

### Post by luke16 on 2007-12-02
5) I want to know how to get dual wallpapers too. Funny thing is, I thought that at one point in time I had that working, but that was a long time ago on an older ubuntu and I could be wrong.

---

### Post by dethredic on 2007-12-03
the wall paper thing is really annoying.

I seem to not have Compiz Fusion installed, as I can't enable visual effects.

---

### Post by dethredic on 2007-12-03
Ok, I installed Compiz Fusion via synpatic but I can't enable visual effects! Any one know what is up?

---

### Post by luke16 on 2007-12-03
> **dethredic said:**
> Ok, I installed Compiz Fusion via synpatic but I can't enable visual effects! Any one know what is up?

What version of ubuntu did you originally install/currently have? I thought compiz was installed in all 7.10 installations.

How will it not let you? Is it just greyed out or something in system>preferences>appearance>visual effects?

---

### Post by dethredic on 2007-12-03
well, I have the newest version, which I believe is 7.10.

When I choose another effect level ( I am on none as of now) it like refreshes my screen for a second, then everything comes back, and I get a message saying "desktop effects could not be enabled".

---

### Post by olejorgen on 2007-12-03
2) As mentioned, this should be possible with metacity (gnome, that is), but I've found it easier to just install **xbindkeys**, and **xbindkeysconfig**. You should add xbindkeys to your startup programs in system->session

---

### Post by luke16 on 2007-12-03
> **dethredic said:**
> well, I have the newest version, which I believe is 7.10.

When I choose another effect level ( I am on none as of now) it like refreshes my screen for a second, then everything comes back, and I get a message saying "desktop effects could not be enabled".

Do you have 3d drivers for your vid card enabled? What video card do you have? Compiz probably won't work without 3d acceleration.

> **olejorgen said:**
> 2) As mentioned, this should be possible with metacity (gnome, that is), but I've found it easier to just install **xbindkeys**, and **xbindkeysconfig**. You should add xbindkeys to your startup programs in system->session

That might work, but I think it would just be easier to go to system>preferences>keyboard>Layout options tab>Alt/win key behaviour, and then select "meta is mapped to winkeys". Then system>preferences>keyboard shortcuts>and then find "hide all windows and show desktop" and map winkey+d from there. I think there is also an option for binding launching home folder to a keystroke as well. However, I think that making the win key launch the "applications" menu on its own won't be possible with it mapped as meta.

---

### Post by olejorgen on 2007-12-04
Wow, that actually worked :) I remember I tried about everything in edgy... I probably overlooked something then

---

### Post by dethredic on 2007-12-04
> **luke16 said:**
> Do you have 3d drivers for your vid card enabled? What video card do you have? Compiz probably won't work without 3d acceleration.



That might work, but I think it would just be easier to go to system>preferences>keyboard>Layout options tab>Alt/win key behaviour, and then select "meta is mapped to winkeys". Then system>preferences>keyboard shortcuts>and then find "hide all windows and show desktop" and map winkey+d from there. I think there is also an option for binding launching home folder to a keystroke as well. However, I think that making the win key launch the "applications" menu on its own won't be possible with it mapped as meta.


I have an Nvidia 880GTS 640mb graphics card, with the accelerated graphics driver installed.

For the keyboard thing, this sorta worked, It let me set the hotkey as Win+d but when I press that hotkey nothing happens.

---

