---
title: "Menu bar - add option for the global menu to make it always visible"
date: 2014-10-03
forum: Desktop Environments
---

### Post by tamir2 on 2014-10-03
Currently in Ubuntu 14.04 there is an option local integration of global header menu application windows. And this, in my opinion, very good. But there is a problem, in order to see the menu of the application instead of the name you have to cross to go window's title bar, which is very inconvenient for photo / video editors and other programs on the user's choice. There is a long-standing bug-report on this issue on the global menu for a particular application with a permanent location in the particular menu of the window (for faster orientation on it). 
Please write what you think about it, how to fix it in Ubuntu 14.04 / 14.10. And you can support this bug-report! 
link - [https://bugs.launchpad.net/ayatana-design/+bug/955193](https://bugs.launchpad.net/ayatana-design/+bug/955193)

---

### Post by grahammechanical on 2014-10-03
This really is not a support request. At least not the type of support request that is usually in this section of the forum. This post should be in the Ubuntu, Linux and OS chat section of the forum.

That said, I really see no difference between moving the mouse pointer to the top left of the top panel and the top of an application window's title bar. We are still moving the mouse pointer.

That bug report seems to be related to a Gnome 3 shell design concept. The options of "hidden" and "visible" are not present in Ubuntu Unity System Settings>Appearance>Behavior. We only have the option to show an application menu panel in the Unity menu bar or the application's title bar.

Something I heard or read somewhere tells me that bringing in Locally Integrated Menus was a non-trivial task for the developers. I may be wrong.

[http://www.omgubuntu.co.uk/2014/02/locally-integrated-menus-ubuntu-14-04](http://www.omgubuntu.co.uk/2014/02/locally-integrated-menus-ubuntu-14-04)

No. You do not get my vote.

Regards.

---

### Post by tamir2 on 2014-10-03
I badly guided by the forum because the interface is not the native language, I'm sorry. I hope that the moderators will transfer a topic in the appropriate section. 

[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323"),
In any case, thanks for your opinion. Perhaps  in reality it is a difficult task, however, it seems that it is solvable. For example, in Ubuntu 14.04, developers have done what seemed impossible on the global menu. 
I think they can improve the interface more to give real flexibility of unity. And all we can to bring this desire to developers, at least supporting a bug-report.

---

### Post by tamir2 on 2014-10-06
As an alternative, you can make suggestions on the example of Ubuntu 12.04, where the Global Menu could completely disable + easy access to the switch this behavior Unity.

---

### Post by tamir2 on 2014-10-12
**In Ubuntu 14.04** added add-on that can be **added to the application exceptions** in the **windows which will [COLOR=red]show the regular menu.[/COLOR]** Which is very useful if you have such applications are not run in full screen. 

  To add applications to the list of exceptions, we need **editor dconf.** 
  To install it, run the following command in the terminal:
```
sudo apt-get install dconf-editor
```
Open it and go to **com> canonical> unity-gtk-module. **There is a setting in the blacklist here it is necessary to make a list of applications that you want to display a standard menu.Template making the list of applications is as follows.
However, this option does not pass in single-window mode in Gimp and Libre Office. How to fix it?

---

### Post by tamir2 on 2014-10-15
In Gimp 2.8.14 fixed the problem. How to disable the global menu Libreoffice, who can know?

---

### Post by tamir2 on 2014-12-27
It is finished! [B]
Thanks to the developers[/B] for what to include an option that I wanted. Link to the news -** [http://www.webupd8.org/2014/12/unity-to-probably-get-option-to-always.html](http://www.webupd8.org/2014/12/unity-to-probably-get-option-to-always.html).**

---

### Post by tamir2 on 2015-01-06
oops

---

