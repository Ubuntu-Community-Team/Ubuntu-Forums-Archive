---
title: "Accidentally Deleted Main panel, how to restore?"
date: 2008-08-24
forum: Desktop Environments
---

### Post by montymintypie on 2008-08-24
Hey guys,

I recently managed to delete my menu panel (was trying to delete some white space, found out I should've used the move option to reorganise my icons) and have got the panel back, but there are no buttons/menus etc. If I try to get them back manually, they look nothing like the original (eg, network monitor is not good at all, and battery monitor looks like it's from Windows 98 ). Is there a way to reset the menu to it's original state? Perhaps a configuration file I can copy from my other Ubuntu machine? I can't even get the proper applications/preferences/places menu's in properly.

This is a REALLY annoying problem, but I reckon there's a simple fix. Can anyone help me???? I don't want to re-install :(

Thanks in advance,

Will

---

### Post by gorillastrong 2 on 2008-08-24
i did this as well at one point. i tried making the panel again, but couldn't get the right side to resize with the current open programs. had to reformat my computer for another reason, that reloaded it, but i wouldn't recomend...surely there's an easier way :)

---

### Post by bigdee973 on 2008-08-24
> **montymintypie said:**
> Hey guys,

I recently managed to delete my menu panel (was trying to delete some white space, found out I should've used the move option to reorganise my icons) and have got the panel back, but there are no buttons/menus etc. If I try to get them back manually, they look nothing like the original (eg, network monitor is not good at all, and battery monitor looks like it's from Windows 98 ). Is there a way to reset the menu to it's original state? Perhaps a configuration file I can copy from my other Ubuntu machine? I can't even get the proper applications/preferences/places menu's in properly.

This is a REALLY annoying problem, but I reckon there's a simple fix. Can anyone help me???? I don't want to re-install :(

Thanks in advance,

Will

You will have to recreate the panel yourself but do not fret it is quite simple to do.

1. on the other panel, right-click & choose "new panel"
2. then right click the NEW PANEL that was just created & click "add to panel" 
3. now choose and add "menu bar", "quit", "notifiication Area", "clock", "volume control" one by one and you should have the original setup 
4. right-click on each icon and you can choose "move" to move the icons and "lock to panel" to make the icon stay put and be still after that you should be all done.

now if want to create lil quick launch icons to launch certain applications such as FireFox just go to applications..highlight the application u want..rightclick it and click "add this launcher to panel".  There are also other things you can add to the panel such "weather applet", "eyes", "system monitor", "fish" + more in "add to panel" when you right-click the panel which i think are cool.

---

### Post by montymintypie on 2008-08-25
Thankyou! That's exactly what I was looking for. I love the eyes (had them on the old menu bar too). Useless brilliance.

Thanks again!

Will

---

### Post by Sisyphus48 on 2008-08-26
Thanks so much Bigdee973!  I accidentally deleted my main panel and could not get it back.  Your instructions were very clear, to the point, and brilliant!

---

### Post by Omecron on 2008-08-27
> **bigdee973 said:**
> You will have to recreate the panel yourself but do not fret it is quite simple to do.

1. on the other panel, right-click & choose "new panel"
2. then right click the NEW PANEL that was just created & click "add to panel" 
3. now choose and add "menu bar", "quit", "notifiication Area", "clock", "volume control" one by one and you should have the original setup 
4. right-click on each icon and you can choose "move" to move the icons and "lock to panel" to make the icon stay put and be still after that you should be all done.

now if want to create lil quick launch icons to launch certain applications such as FireFox just go to applications..highlight the application u want..rightclick it and click "add this launcher to panel".  There are also other things you can add to the panel such "weather applet", "eyes", "system monitor", "fish" + more in "add to panel" when you right-click the panel which i think are cool.

Copy and pasted into my Documents folder for my future goof up. I salute you :biggrin:

---

### Post by EnGorDiaz on 2008-08-27
> **montymintypie said:**
> Hey guys,

I recently managed to delete my menu panel (was trying to delete some white space, found out I should've used the move option to reorganise my icons) and have got the panel back, but there are no buttons/menus etc. If I try to get them back manually, they look nothing like the original (eg, network monitor is not good at all, and battery monitor looks like it's from Windows 98 ). Is there a way to reset the menu to it's original state? Perhaps a configuration file I can copy from my other Ubuntu machine? I can't even get the proper applications/preferences/places menu's in properly.

This is a REALLY annoying problem, but I reckon there's a simple fix. Can anyone help me???? I don't want to re-install :(

Thanks in advance,

Will

do this command in terminal gnome-panel
then right click and click add to panel 
then add the programs you want
done.

---

### Post by bigdee973 on 2008-08-29
you guys are welcome im glad i could help

---

### Post by wenuswilson on 2008-08-30
How about getting open Applications to the panel, ie, Pidgin's icon or Rhythmbox's icon (default next to clock) I got everything I wanted back except for those icons. Or the compiz-fusion icon.

Found it:

terminal type, "gksudo gnome-panel" it restores to default, found that in another forum.

---

### Post by bigdee973 on 2008-10-01
> **wenuswilson said:**
> How about getting open Applications to the panel, ie, Pidgin's icon or Rhythmbox's icon (default next to clock) I got everything I wanted back except for those icons. Or the compiz-fusion icon.

Found it:

terminal type, "gksudo gnome-panel" it restores to default, found that in another forum.

i would try it without gksudo and see if that works because i deleted my panel and did gksudo gnome-panel and it switched me over as root and applied it as user:root but did not do it for the user that im under so its not a good idea to use gksudo in my opinion unless someone objects..i would just type in gnome-panel to see if that works

---

### Post by Yneth on 2010-06-06
Isn't it better to just reset it?? I happened to do the same, deleted the main panel accidentally but then i could get the exact same thing i had before deleting. 
what i did was
Alt+f2  
gnome-terminal (open terminal)
rm -r .gconf
rm -r .gcond
rm -r .gnome2
rm -r .gnome_private
and also reboot after this.

---

