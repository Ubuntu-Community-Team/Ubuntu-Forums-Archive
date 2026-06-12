---
title: "How to choice icon theme for Clementine?"
date: 2012-07-18
forum: Desktop Environments
---

### Post by Macfunky on 2012-07-18
I love Clementine but i hate that it doesn't automatically use the same icon theme that is set for Unity/Gnome shell. I don't know why and haven't been able to figure out how to make it do so. Anyone know how to do this?

---

### Post by Frogs Hair on 2012-07-18
Open the main menu from applications , select the category in the left pane were Clementine is installed (probably sound & video). In the right pane double click the line that Clementine is displayed on to open launcher properties. 

Select the icon image on the left side of the properties dialog box and navigate to the clementine icon in the set you are currently using and select open. log out and back in.

---

### Post by Whovian on 2012-07-18
could be that the icon set is not in the .icons folder in the home directory or in the /usr/share/icons. I am not sure but it might be the problem.

---

### Post by Macfunky on 2012-07-18
I know how to change icon themes. I should have made myself clearer. I was referring to the applications icon theme. Being a QT application it doesn't seem to follow the selected theme for the Gnome enviroment. I have a screenshot attached. I am using the Faenza icon theme but clementine is stuck using the default Gnome icon theme. Is there a way to tell it to use the same icon theme as the rest of the desktop?

---

### Post by Frogs Hair on 2012-07-18
I thought you were writing about the launcher icon. I have never changed the actions icons in a non native application and don't know why they default to an icon set other than the one you are using.

---

### Post by Macfunky on 2012-07-18
> **Frogs Hair said:**
> I thought you were writing about the launcher icon. I have never changed the actions icons in a non native application and don't know why they default to an icon set other than the one you are using.

Reading back at my original post i realise it did sound like i was talking about that :) Oh well. It is unusual that it doesn't use the default theme. Thanks anyway :)

---

### Post by Macfunky on 2012-09-13
Back to answer my own question in case it helps anyone else. If you install gconf-editor go to desktop > gnome > interface > icon_theme. This was set to the default ubuntu icon theme so while i was able to change my icon theme and have it work for everything gtk, qt apps weren't taking it onboard cause of this setting. Change it to whatever icon theme you are using and it will also apply it to all qt apps. Simple when you know how :) Hope this helps someone.

---

