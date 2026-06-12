---
title: "Panels autohide delay - Xubuntu 18.04 with XFCE4.14"
date: 2020-02-10
forum: Desktop Environments
---

### Post by zyga91 on 2020-02-10
Hi there,

I have a little problem with tweaking my new Xubuntu 18.04 installation. Is there any way to delay panels autohiding in XFCE4.14?

By google i found this one [https://forum.xfce.org/viewtopic.php?id=11816](https://forum.xfce.org/viewtopic.php?id=11816) but it doesn't work. I tried old method with editing/creating "[COLOR=#333333][FONT=Verdana].gtkrc-2.0", but it was blind shot [/FONT][/COLOR]obviously[COLOR=#333333][FONT=Verdana].

Any help? :([/FONT][/COLOR][COLOR=#333333][FONT=Verdana]
[/FONT][/COLOR]

---

### Post by webaake on 2020-03-12
Here are some tips for xfce4-panel 4.14 GTK3 themeing: [https://docs.xfce.org/xfce/xfce4-panel/theming](https://docs.xfce.org/xfce/xfce4-panel/theming). But the implemntation of GTK3 doesn't seem complete in 4.14, for the panel anyway.

*I just upgraded my xfce to 4.14 yesterday too, on 18.04. Seems great!

---

### Post by guiverc on 2020-03-12
You might want to confirm your XFCE version & release details.

 A new installation of Xubuntu 18.04 LTS has XFCE 4.12.4,  Xubuntu 19.10 comes with 4.14, or did you add the Xubuntu teams PPA to upgrade to 4.14 or something else?

---

### Post by webaake on 2020-03-12
Yayy! Solved it! For 4.14 GTK3 it's the file ~/.config/gtk-3.0/gtk.css you have to edit. Example;```
/* xfce4-panel 4.14 test */
* {
-XfcePanelWindow-popup-delay: 5000;
-XfcePanelWindow-popdown-delay: 1000;
-XfcePanelWindow-autohide-size: 10;
}


```

5000 is a lot! Restart xfce4-panel with: ```
xfce4-panel -r 
```

---

### Post by him610 on 2020-03-12
In Xubuntu 20.04, right click on panel background....
Scroll down to 'Panel,' highlight-click on 'Panel Preferences'
Where it says 'Lock panel', click the box to the left to unlock it (shows no check mark)
Where it says 'Automatically hide the panel:' highlight box to the right -
In the dropdown list, select [ Never | Automatically | Always ]
Close

---

### Post by webaake on 2020-03-12
And how do you control the delay?

---

### Post by him610 on 2020-03-12
> **webaake said:**
> And how do you control the delay?
My apologies, I missed that part; however, I looked up the documentation here, [https://docs.xfce.org/xfce/xfce4-panel/start]("https://docs.xfce.org/xfce/xfce4-panel/start")
Autohiding of the panel is not discussed. Doesn't mean it can not be done.
It could be a matter for a discrepancy (bug) report detailed here, [https://docs.xfce.org/contribute/start#bug_reporting_and_testing]("https://docs.xfce.org/contribute/start#bug_reporting_and_testing")

---

### Post by webaake on 2020-03-13
Did you read my post with the solution?

---

### Post by him610 on 2020-03-13
Congratulations on finding a solution to your issue. Now, how about using the thread tools to mark it *Solved*.

---

