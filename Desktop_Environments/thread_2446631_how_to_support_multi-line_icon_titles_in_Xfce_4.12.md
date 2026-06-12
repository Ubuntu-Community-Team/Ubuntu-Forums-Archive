---
title: "how to support multi-line icon titles in Xfce 4.12?"
date: 2020-07-04
forum: Desktop Environments
---

### Post by Skaperen on 2020-07-04
[here]("http://ipal.net/ss.png") is a picture of a desktop with one icon added to ~/Desktop/ (left side, bottom of the only column) which has a multi-line name that only works in this one userid but does not work in any other userid.  in the others, only one line shows up.  the name does have the 2 characters "\n" (not an actual newline byte) in it which seems to be understood as the end of line 1 even in the other userids.  but only line 1 is displayed except for this one userid.  can someone say what to set or configure to get all name lines to show up?  below is the code of the actual desktop file.
```

[Desktop Entry]
Version=1.0
Type=Application
Name=Linux\nQuestion
Comment=linuxquestions.org
Exec=inws 8 /usr/lib/firefox/firefox -p linux_q -no-remote https://linuxquestions.org/
Icon=firefox
Terminal=false
StartupNotify=false

```
*inws* is a local script that runs a command in a specified workspace.

---

### Post by &amp;KyT$0P# on 2020-07-04
What do you have in your [FONT=Courier New]~/.gtkrc-2.0[/FONT] (and the files it includes, if any)?  I got xfdesktop to work how you want by putting this in -
```
style "xfdesktop-icon-view" {
    XfdesktopIconView::ellipsize-icon-labels = 0
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

```

I use this in Xubuntu 18.04.  See [here]("https://docs.xfce.org/xfce/xfdesktop/advanced") for more info.

---

### Post by Skaperen on 2020-07-04
that was the thing that did it.  thanks!  i was looking for differences in settings but it was this file.  i copied it to all userids.

---

### Post by &amp;KyT$0P# on 2020-07-04
You're welcome :KS

---

