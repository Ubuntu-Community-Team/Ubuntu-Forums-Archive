---
title: "Basic, basic, basic Linux + gnome question"
date: 2005-05-19
forum: Desktop Environments
---

### Post by valnar on 2005-05-19
Since I'm a newbie, I don't know if this is a basic Linux or Gnome specific question.  But coming from Windows.....


I added my first new application today from the repository - yah, I'm taking it slow.  It was the first on the list - 3D Chess.

I noticed as compared to Windows, it doesn't create an icon (shortcut) for it anywhere, so I hunted down the application 3Dc and made one on my desktop.  Well, I made it on my desktop because I can't figure out how to throw it into the Applications/Games menu in ubuntu.  I assume it is not a folder like from Windows 95 on up as an analogy?  If not then where can I put it?  Where are the other shortcuts stored?  And how come Linux (or Gnome) doesn't support any right clicking of anything of value??!!   ](*,) 

Thanks!
Robert

---

### Post by NeoChaosX on 2005-05-19
Not all installed programs create menu entries. I don't get it either.

For now, you can't add new entries to the GNOME Applications menu by default; that won't be implemented until GNOME 2.12. However, you can use the [Smeg Menu Editor](http://ubuntuforums.org/forumdisplay.php?f=67) by Amaranth to add new entries to your menu. Hope that works.

---

### Post by valnar on 2005-05-19
You have got to be kidding?  Gnome doesn't support something as basic as that?

Perhaps I should try KDE...  OK, thanks.

Robert

---

### Post by NeoChaosX on 2005-05-19
Oops, maybe I should've been clear: there's no PROGRAM to add entries included in GNOME 2.10. You could add shortcuts manually, but that's a pain in the butt to do. But Smeg gives you menu-editing powers until GNOME 2.12 rolls around.

---

### Post by valnar on 2005-05-19
What's the manual way, if I may ask?

Robert

---

### Post by himuraken on 2005-05-19
Not sure if it much of a consultation to you but until Gnome 2.2 comes out I have been dragging frequently used icons/programs onto the actual "taskbar" <- Windows terms, and the icons can be simply dragged and dropped as in Win32 OS's.

---

### Post by valnar on 2005-05-19
I really like ubuntu, but so far am disliking Gnome.   Unfortunately, Kubuntu isn't that hot, so I would have to leave ubuntu-land to get a KDE oriented distro.  I don't want to do that because the immense amount of learning I can do from reading on these forums is tremendous.  decisions....


Thanks for the replies so far.


Robert

---

### Post by NeoChaosX on 2005-05-19
[QUOTE=valnar]What's the manual way, if I may ask?[/QUOTE]
Creating .desktop files through a text editor (so you can specify which folder they go in) and dumping them into /usr/share/applications

---

### Post by logan2004 on 2005-05-19
[QUOTE=valnar]I really like ubuntu, but so far am disliking Gnome.   Unfortunately, Kubuntu isn't that hot, so I would have to leave ubuntu-land to get a KDE oriented distro.  I don't want to do that because the immense amount of learning I can do from reading on these forums is tremendous.  decisions....


Thanks for the replies so far.


Robert[/QUOTE]

maybe you just need to warmup to gnome. if you right click one of your panels, and then select "+ add to panel" you can put any program up there.

or maybe you should try [fluxbox](http://fluxbox.sourceforge.net/zoom.php?shots-dev/majes_fluxbox.jpg) which is quite customizable, but not as standard as gnome.

---

### Post by Stormy Eyes on 2005-05-19
[QUOTE=logan2004]or maybe you should try [fluxbox](http://fluxbox.sourceforge.net/zoom.php?shots-dev/majes_fluxbox.jpg) which is quite customizable, but not as standard as gnome.[/QUOTE]

I've found that [Openbox](http://www.openbox.org) is more reliable. YMMV. But, as others said, you can add custom icons to your panel. Right-click on it for a menu, select "Add to Panel", and then choose "Custom Launcher".

---

### Post by bored2k on 2005-05-19
[QUOTE=Stormy Eyes]I've found that [Openbox](http://www.openbox.org) is more reliable. YMMV. But, as others said, you can add custom icons to your panel. Right-click on it for a menu, select "Add to Panel", and then choose "Custom Launcher".[/QUOTE]
 Hey Stormy I'm having a hardtime with Openbox and it's alt+tab (only shows one application, not a list like Metacity does!). Is there any way around this ?

---

### Post by Stormy Eyes on 2005-05-20
[QUOTE=bored2k]Hey Stormy I'm having a hardtime with Openbox and it's alt+tab (only shows one application, not a list like Metacity does!). Is there any way around this ?[/QUOTE]

You can middle-click the desktop to bring up a "desktop menu", which will show you the names of all of your currently open windows by desktop. You can also modify the alt+tab keybinding to bring up the desktop menu if you want to. I'll post info on how to do that in the HOWTO thread tomorrow. I want to finish a batch of themes that I'm working on before I finally go to bed.

---

### Post by bored2k on 2005-05-20
[QUOTE=Stormy Eyes]You can middle-click the desktop to bring up a "desktop menu", which will show you the names of all of your currently open windows by desktop. You can also modify the alt+tab keybinding to bring up the desktop menu if you want to. I'll post info on how to do that in the HOWTO thread tomorrow. I want to finish a batch of themes that I'm working on before I finally go to bed.[/QUOTE]
 Thanks in advance for the howto on this :D.

---

