---
title: "disabled desktop wall and unity"
date: 2011-05-14
forum: Desktop Environments
---

### Post by amoateng on 2011-05-14
So i was following this manual online on how to get the compizcube on ubuntu 11.04.. i had to disable the desktop wall and unity.. problem is, i also closed the Compiz Configuration Settings Manager.. now i have no bars at the top and at the bottom, so i can't even shut down the computer properly.. so can someone help me? i can open folders and stuff thought through my desktop.

thanks

---

### Post by wojox on 2011-05-14
Did you try Alt+F2 

```
unity --reset
```

---

### Post by Krytarik on 2011-05-14
> **wojox said:**
> Did you try Alt+F2 

```
unity --reset
```
Alt+F2 doesn't work if Unity is disabled.

Please see this troubleshooting guide:
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

To enable the Cube see this one:
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

Greetings.

---

### Post by Atermoon on 2011-05-14
The default shortcut for terminal is Ctrl + alt + T. Use that instead of Alt + F2

---

### Post by Krytarik on 2011-05-14
> **Atermoon said:**
> The default shortcut for terminal is Ctrl + alt + T. Use that instead of Alt + F2
That doesn't work also. ;-)

Addition: ...in most of the cases. Because the "Gnome Compatibility" plugin might get disabled as a matter of cascade effect when trying to enable the Cube the 'simple way'. But since the OP just disabled the "Desktop Wall" and the "Ubuntu Unity Plugin", Ctrl+Alt+T might still work.

---

### Post by falexge on 2011-06-02
I messed up my system similar to what you did and here is the procedure I used to restore the Desktop Wall.

[LIST=1]
[*]Right click on your desktop and choose **Create Launcher...**
[*]Input the following in the dialog box:
**Type:** Application in Terminal
**Name:** Reset Unity (*you can use anything here*)
**Command:** unity --reset
**Comment:** (*anything*)

Screenshot:
[IMG]http://i.imgur.com/LaRpt.png[/IMG]

[*]Now double click on the link to open it in a terminal window.
[*]When everything is done (when your bars are back) restart your computer.
[/LIST]

---

