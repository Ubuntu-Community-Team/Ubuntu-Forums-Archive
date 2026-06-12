---
title: "How do I move the icons on the top menu bar?"
date: 2015-02-28
forum: Desktop Environments
---

### Post by cole8 on 2015-02-28
So I am going to theme my ubuntu and I need to know how to move icons on the top black bar where you sign out

---

### Post by v3.xx on 2015-02-28
Which *buntu ?

---

### Post by Frogs Hair on 2015-02-28
Hello and Welcome

If you are using the default Unity desktop with the launcher panel on the left you won't be able to move application icons to the top panel although there are Ubuntu versions that allow for that. The Gnome Flash Back session is also available in the software center. The linked instruction will work in 14.10 as well.


[http://www.webupd8.org/2014/04/how-to-install-and-tweak-gnome.html](http://www.webupd8.org/2014/04/how-to-install-and-tweak-gnome.html)

[http://www.kubuntu.org/getkubuntu](http://www.kubuntu.org/getkubuntu)
[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

---

### Post by cole8 on 2015-02-28
thanks for your kind help i really appreciate it bye babes

---

### Post by deadflowr on 2015-02-28
Well, if you are using Ubuntu/w unity version 14.04 you can manipulate the icons by changing the position settings in the files located in
/usr/share/unity/indicators.
A typical file looks like this, 
for the file com.canonical.indicator.session (the cog icon at the very end of the panel)
```
[Indicator Service]Name=indicator-session
ObjectPath=/com/canonical/indicator/session
Position=10


[desktop]
ObjectPath=/com/canonical/indicator/session/desktop


[desktop_greeter]
ObjectPath=/com/canonical/indicator/session/desktop_greeter


[desktop_lockscreen]
ObjectPath=/com/canonical/indicator/session/desktop_lockscreen


[ubiquity]
ObjectPath=/com/canonical/indicator/session/desktop_greeter

```
You would change the position number to something else.
Note that the numbers move from right to left so 10 is the far right and 100 would be further left.
( I believe they are placed at intervals of 10; so the first is at 10 and the second is at 20, and so on)

Once you see how they are laid out you'll basically understand how you can change them to fit your design goal.

A couple of sidenotes:
Because these are system files and folders you need root; should be obvious.
Something to do to protect yourself from yourself would be to make a copy(or two) of the folder(the indicator folder) somewhere in your home folder.
This way you can edit the files as a normal user.
Then you can copy the files post-edited back into the system folder: /usr/share/unity.
You might also consider making a secondary backup of the original for prosperity.

Also note that per chance a unity update comes through, it might overwrite your personalizations, so perhaps also keep a backup of your changed folder somewhere, so you can easily copy it back into the system folder.

Beats me if this is helpful or not, but have fun anyway.

---

