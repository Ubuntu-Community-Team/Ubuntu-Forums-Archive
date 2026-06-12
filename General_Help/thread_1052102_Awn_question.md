---
title: "Awn question"
date: 2009-01-27
forum: General Help
---

### Post by psilocybin2 on 2009-01-27
2 questions

how do i hide my top and bottom panels? they get in the way of my awn bar

---

### Post by squee on 2009-01-27
I think you may have to remove everythign from the bar before you can delete the bar. This will also involve "unlocking" somethings so they can be deleted in the first place.

This is all easily done with the mouse - right clicking on the icons, deselecting "lock to panel" then removing the icon. Then you can delete the bar.

There may be a faster way, but I dont know it.

---

### Post by sirebral on 2009-01-27
Right click on your panels, Choose properties, Chose AutoHide, close.

---

### Post by mariner09 on 2009-01-27
If you don't want the panels, regardless of what's on them, you can delete them.  If you set auto-hide, the bottom panel and AWN may both pop up if you choose the option in both.

---

### Post by chamber on 2009-01-27
Why have a bottom bar if you have AWN?  Just move the essential stuff on it to the top bar and delete it.

Also, whats the second question?

---

### Post by psilocybin2 on 2009-01-27
> **chamber said:**
> Why have a bottom bar if you have AWN?  Just move the essential stuff on it to the top bar and delete it.

Also, whats the second question?

do you get little black lines on your awn bar the odd time?
so really i cant get rid of the bars all together?

---

### Post by chamber on 2009-01-27
If you delete it then you get rid of it.

I got rid of my bottom bar pretty much right away and just run a few apps off the top one.

---

### Post by Epidemic_HardyBoy on 2009-01-27
Just delete the two panals.
Remove everything from the panals, and then just remove it

---

### Post by psilocybin2 on 2009-01-27
> **chamber said:**
> If you delete it then you get rid of it.

I got rid of my bottom bar pretty much right away and just run a few apps off the top one.

k thanks did that

but these black bars showing up on my awn bar are annoying..they go away when i scroll my mouse across it but its still annoying

---

### Post by chamber on 2009-01-27
> **psilocybin2 said:**
> k thanks did that

but these black bars showing up on my awn bar are annoying..they go away when i scroll my mouse across it but its still annoying

Thats one of the reasons I moved to Cairo dock, not sure what causes it.

---

### Post by VeeDubb on 2009-01-27
> **chamber said:**
> Thats one of the reasons I moved to Cairo dock, not sure what causes it.


That was also one of my two big reasons for switching to cairo-dock.  That, and the fact that half of the plugins for AWN are perpetually broken.



**As for getting rid of the gnome-panels**:  Just telling someone to delete them both is really NOT helpful, since it's impossible; and telling someone to use auto-hide is bordering on rude.

You can delete all but 1 gnome-panel, but the last one cannot be deleted.


There are two ways to get rid of them completely, each has it's advantages.

Option 1: find the gnome panels in you session settings, and remove it so that it doesn't start up at all.  

This has the advantage that it's completely gone, and not taking up one shred of system resources.  The downside is that if something goes wrong with your dock, it can be a little tricky to bring everything back up without having the gnome-panels to fall back on.

Option 2: Go into CCSM and enable the widget layer, and then add gnome-panel to the list of applications that should be put on the widget layer.  

This will technically take up more system resources, but it shouldn't be noticeable unless you're using a pretty old system.  The real advantage here, is that the gnome-panel will continue to work in the background, so all the desklets, applets, plugins and programs that expect it to be there will still work correctly.  And, a simple hotkey will instantly reveal programs on the widget layer and bring it right back into view.

The only thing you have to be careful of with this, is that if you plan on using a notification area plugin (systray) on your dock, you really need to remove the systray from your gnome panel.  Your menus, shortcuts and everything else can stay on the panel so you have a back-up when needed.

I prefer option 2, and if you plan on using cairo-dock, option 2 is mandatory because the only reliable and consistant way to have a main menu in cairo-dock is to create a launcher that activates the gnome-panel main menu keyboard shortcut.  (alt-F1 by default)

---

### Post by fabounet on 2009-01-28
the GMenu applet exists for that purpose !

you can totally remove the gnome-panel from your system if you use Cairo-Dock.

---

### Post by psilocybin2 on 2009-01-28
Where's the gmenu LOL

---

### Post by VeeDubb on 2009-01-29
> **psilocybin2 said:**
> Where's the gmenu LOL

I'd like to know the same thing.  I'm using version 2.0.0-beta1 and I can't find a plugin called gmenu anywhere, anthough I'd most certainly like to as using the alt-f1 keyboard shortcut on a launcher is a little slow for me.

---

### Post by fabounet on 2009-01-29
err, there should be a GMenu applet in the package (1.6.3 and 2.0-beta)
maybe you miss a dependancy (libgnome-menu), run the dock in the terminal and look for a warning concerning gmenu.

---

### Post by VeeDubb on 2009-02-01
If anybody else has trouble with the gmenu plugin on 8.10 64bit, try [http://ubuntuforums.org/showthread.php?p=6655277#post6655277](http://ubuntuforums.org/showthread.php?p=6655277#post6655277)

---

