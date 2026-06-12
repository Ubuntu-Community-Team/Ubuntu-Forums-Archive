---
title: "Question: How to change window list icons?"
date: 2006-09-03
forum: Desktop Environments
---

### Post by phisquare on 2006-09-03
I've installed Eterm and I was curious how I can change the window list icons.  Currently, the icon that appears is the standard icon that usually appears when an icon can not be located for the application running.  I would like to know how to do this for not only Eterm but also other apps as well.  Any ideas or hints are appreciated.

Thanks!

PHi

---

### Post by erusan on 2006-09-04
I'm wondering the same thing, sort of.

I've got the nightly VLC installed with the OSX icon theme, and while the menu icon looks great, I get some generic window icon for the taskbar.

---

### Post by crossedout on 2006-09-04
You can alter any icon through your <theme> folder located under .icons.
Navigate to your home folder, ctrl+h (to show hidden files/folders), .icons, <themename>.  That is where all the icons are located for each particular theme.  Icon themes seldem have a replacement for every application and so some need to be imported in.

You'll need to know the name of the icon image to be replaced.  For example, the trash icon is trash.png or .svg depending on the theme.

Second, decide which icon you want to use (it doesn't matter what theme it is from or what the name is) and copy/paste it to your current theme folder.  For example: copy/paste the trash.png icon from the CrystalClear icon theme to the OSX icon theme (preferably to the same subfolder for orginizational purposes).  You can choose to replace the icon altogether or rename the old one to trash-OLD.png if you want to revert later.

-Xout

---

### Post by PhilipGanchev on 2007-03-19
This does not seem to work with programs like Dillo or xterm.  I set my theme to "Human", created a directory ".icons/Human" and copied a 32x32 size images called dillo.png there.  But when I start Dillo, it uses the default application icon.  Is there a way to make this work?

---

