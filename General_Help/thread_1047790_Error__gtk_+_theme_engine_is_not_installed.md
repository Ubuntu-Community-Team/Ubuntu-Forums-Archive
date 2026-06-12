---
title: "Error : gtk + theme engine is not installed"
date: 2009-01-22
forum: General Help
---

### Post by birlindo on 2009-01-22
:( after i got new themes plus i cons it didnt work well and i recives error (gtk + theme engine is not installed ) i searched for it in pacage manneger but i didnt find it :( pls help me here the picture attached

---

### Post by birlindo on 2009-01-22
any helps are welcomed . pls help me

---

### Post by mcduck on 2009-01-23
I'd say that's just a small bug in the theme manager itself, as it doesn't even tell what theme engine it's missing.. Half of my themes do that in 8.10, and work correctly. Just ignore the error.

(Of course if the error tells you what engine it's missing, then install that engine.)

---

### Post by birlindo on 2009-01-23
the proplem exactly in icons :( also i looked for this engine but i didnt find it in package mannger . thank you for your help

---

### Post by mcduck on 2009-01-23
Icons are not related to GTK theme. And if that error was a valid error, it would tell you what engine is missing; for example something like "This theme will not look as intended because the required GTK+ engine **"Aurora"** is not installed"

The message in your screenshot doesn't tell what engine it would be missing, just a single quote mark. 

Really, the theme selection dialog simply is a bit buggy at the moment. It gives the same message even with some themes that only use engines that definitely are installed. ;)

If some theme actually tells you what engine it's missing, look first from repositories (searching for gtk2-engine" in Synaptic works fine). if you can't find the right one you can most likely download it from gnome-look.org

---

### Post by IceReaver75 on 2009-01-23
you can fix this so it doesn't say it anymore by opening the gtk-2.0 file in the actual themes folder, usually found in either /home/.themes(hidden) or in /usr/share/themes and opening the gtkrc file in there with a text editor.  Search for all entries of engine with the find feature.  You will usually find one that says:

style "unstyle"
{
  engine ""
  {
  }
}


If you change it to this:

style "unstyle"
{
  engine "pixmap"
  {
  }
}

it will stop complaining about theme engine "" isn't installed.  If there is any other rc files in there also like the panelrc etc.  you may have to look in there also.  Like others have said it doesn't hinder the theme at all but I change them so I don't have to look at the message every time I open the apperance window.

---

