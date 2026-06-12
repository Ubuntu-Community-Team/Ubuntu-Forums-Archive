---
title: "Applications Opened As Root Don't Use GTK And Icon Theme"
date: 2008-06-27
forum: Desktop Environments
---

### Post by Mark76 on 2008-06-27
I'm using a home brew desktop environment (slim for session management, icewm for windows management, xplanet for backdrop, xfce4-panel for widgets and pcmanfm for file management).  I'm using the LUX gtk2 theme with the BlankOn icon set, but everytime I run an application that requires a password to open it (the application) uses something else (possibly clearlooks).  I've looked at my gtkrc-2.0 file and that says

>   # DO NOT EDIT!  This file will be overwritten by LXAppearance.
# Any customization should be done in ~/.gtkrc-2.0.mine

gtk-theme-name="LUX"
gtk-icon-theme-name="BlankOn"
gtk-font-name="Serif 9"
gtk-toolbar-style=2
include "/home/mark/.gtkrc-2.0.mine"


Which is exactly right.  So why does it only work on non SUDO apps?

If you need to know I'm using lxappearance to set gtk and icon themes

---

### Post by Xgen on 2008-06-27
Root reads what's in the root folder. Possibly rename the .gtkrc-2.0 in root and copy the home one over to try.

---

### Post by Mark76 on 2008-06-27
That kind of did the trick, but I need the root copy to rewrite itself as well when I change themes. What do I need to change to bring that about?

---

### Post by llelectronics on 2008-06-27
If you are changing your theme via the "Gnome Theme Manager" than start it as root (sudo) . 
My suggestion is to simply set a symbolic link from the roots gtkrc-2.0 to the one in your home folder. So that everytime you update your theme the theme as root will be updated too.

---

### Post by vishzilla on 2008-06-27
create symbolic links to the icon and theme folders in your home directory

```
sudo ln -s .icons/ /root/.icons
sudo ln -s .themes/ /root/.themes
```

---

### Post by Mark76 on 2008-06-27
I'm changing it via lxappearance (see above).

Pcmanfm doesn't seem to have a "create symbolic link option. What's the CL way?

Something more complex than sudo create symlink file1-file2, no doubt.

Thanks Vish.

---

### Post by Xgen on 2008-06-27
A blanket answer, as I don't know all the facts...if the theme/icon set is in the shared usr/share folder, then both  root and home will change together. Any themes/icon sets (usually created or modified) in my home folder that I want root to follow, then I create a link with the same name in the root theme/icon folder. Of course you can get creative if you want the root to be a different theme than home by linking the theme in home that you want for root and renaming it to the one that is presently being used in home. OR (as I have)...changing the text in root to red (by .gtkrc-2.0) so that I know when I am in a root application.
Aye...too late, didn't see the upper responses.

---

### Post by Mark76 on 2008-06-27
Actually, I realised after I'd set the symlinks that the icons and themes folders are in /usr/share; not root.  I also don't keep any icons or themes folders in my home directory.

---

### Post by mcduck on 2008-06-27
> **Mark76 said:**
> I'm changing it via lxappearance (see above).

Pcmanfm doesn't seem to have a "create symbolic link option. What's the CL way?

Something more complex than sudo create symlink file1-file2, no doubt.

Thanks Vish.

The commands are the ones that vishzilla posted.

All themes and icons you install from the appearacnce-window (as opposed to unpacking them manually into /usr/share/themes) will be installed into your home directory. These commands link those theme directories into corresponding direcories for the root user.

---

### Post by joninkrakow on 2008-06-27
Actually, one ought to consider if he really wants the root apps to look like the rest! I, for one, appreciate the fact that an app running as root looks differently, as it gives me an indication that I'm running it as root, and to be careful. I've accidently moved files to the wrong location because I forgot that my file manager was running as root--and that's with the visual difference. ;-) I've learned to use that difference as a cue to what I'm doing. 

IMO, it's a good thing, in the end, that sudo'd apps look different.... IMO, of course, and food for thought.

-Jon

---

### Post by Mark76 on 2008-06-27
So you don't get a warning bar just under the toolbar then?

Like this

---

### Post by mcduck on 2008-06-27
> **joninkrakow said:**
> Actually, one ought to consider if he really wants the root apps to look like the rest! I, for one, appreciate the fact that an app running as root looks differently, as it gives me an indication that I'm running it as root, and to be careful. I've accidently moved files to the wrong location because I forgot that my file manager was running as root--and that's with the visual difference. ;-) I've learned to use that difference as a cue to what I'm doing. 

IMO, it's a good thing, in the end, that sudo'd apps look different.... IMO, of course, and food for thought.

-Jon

I like the app theme to be the same. However I always set the background in root Nautilus to dark red. It still looks nice but the red color is so clear warning that it's pretty much impossible to ignore.

For other apps there's no problem as there's not really much need as most of the apps are only used as root or as normal user but not as both.

---

### Post by joninkrakow on 2008-06-27
> **Mark76 said:**
> So you don't get a warning bar just under the toolbar then?

Like this

I don't remember seeing that before, but I got it just now in PCMan.

BTW, is that xfce or lxde DE? 

BTW, xfe does not show the warning bar. It just shows "(root)" in the title bar.

-Jon

---

### Post by Mark76 on 2008-06-27
It's MYbuntu :D

IceWM + xfce4-panel + xplanet

---

### Post by joninkrakow on 2008-06-27
> **Mark76 said:**
> It's MYbuntu :D

IceWM + xfce4-panel + xplanet

Aha. I _knew_ I'd seen that theme before. :-) 

So, where's ROX filer? ;-)

---

### Post by Mark76 on 2008-06-27
I haven't got round to reinstalling ROX-Desktop yet.

---

