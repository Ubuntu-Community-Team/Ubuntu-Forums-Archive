---
title: "Metacity in Xfce4"
date: 2011-08-06
forum: Desktop Environments
---

### Post by frangoitia on 2011-08-06
Hello. I installed metacity in Xfce4 in order to have border windows when using Compiz Fusion. I want to change the theme and font of metacity, how can I do it ? There is no icon to metacity personalization in the menu.
Thanks in advance.

---

### Post by SalHelder on 2011-08-07
Go to a console and type:

gnome-control-center

Look for the "Appearance" option, there to the font tab and select the font and size you want for the window decoration.

---

### Post by mikewhatever on 2011-08-07
Hold on a sec. Metacity is Gnome window manager, Compiz is also a window manager, but it doesn't need Metacity to work. Last but not least, XFCE uses xfwm4 - yet another window manager. So if you want to modify the way Compiz looks, use Compiz config tool. Installing more window managers is not going to help.

---

### Post by SalHelder on 2011-08-07
Sure, I though he used it because he liked Metacity more, he could also try Emerald.

---

### Post by frangoitia on 2011-08-15
Thanks for you answers. 
I would use xfwm4 with Compiz because is my favourite manager but I cant do it, when i type that command in compiz configuration i dont have the effects, it disable Compiz.

---

### Post by frangoitia on 2011-09-01
So, Im still having this problem, I have to use Metacity with Compiz (Im using the 0.9.x version so Emerald doesnt work, plus I dont like Emerald since it uses a lot of resources). 
So, anyone knows the command to select metacity theme ?

---

### Post by 3Miro on 2011-09-01
Lets clear some confusion. Compiz, Metacity and XFWM4 are separate windows managers. Most windows managers come with their own inbuilt windows decorator (that draws the themes around the windows), however, Compiz can be modified to work with different windows decorator.

Compiz can use either emerald or "gtk-windows-decorator" (I think this has a different name in 11.04: "compiz-decorator"). The "gtk-windows-decorator" can use Metacity themes, however, setting the proper theme under xfce can be a problem.

First make sure you have "gtk-windows-decorator" installed. Then try to run it from the terminal with:
```
gtk-windows-decorator --replace
```
You can also try that for the CCSM settings under Windows Decorator, you can enter the command gtk-windows-decorator --replace.

After you get gtk-windows-decorator working, you should be able to change themes either from "Gnome-control-center" or "gconf-editor" (you can run those from the terminal). Since Metacity is the Gnome WM and since gtk-windows-decorator is designed to work for Gnome, you will need some Gnome tools to be installed.

---

### Post by frangoitia on 2011-09-04
Thanks, I got finally window decorator working after installing "compizconfig-backend-gsettings-git".
And I could do it from gconf-editor (after installing).
Thanks a lot !

---

