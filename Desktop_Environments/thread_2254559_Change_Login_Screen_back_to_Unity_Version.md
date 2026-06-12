---
title: "Change Login Screen back to Unity Version"
date: 2014-11-28
forum: Desktop Environments
---

### Post by baudrillard on 2014-11-28
I've recently installed a pretty bare version of the Gnome DE from the Ubuntu Software Center, and I really like the outlay of things, more so than Unity's.

However, I don't really like the look of Gnome's login screen, and would like to know if there's a way to set the login/sleep screen to Unity, while keeping the DE to whatever I choose for a session.

Thank you!

(I know this is very picky of me, sorry for bothering you all with this.)

---

### Post by ibjsb4 on 2014-11-28
This what you looking for.

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=edit+login+screen&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=edit+login+screen&sa=Search&cof=FORID:9)

---

### Post by kansasnoob on 2014-11-28
Maybe 'gdm' was installed along with the GNOME packages so you could try running:

```
sudo dpkg-reconfigure lightdm
```

If both 'lightdm' and 'gdm' are installed you'll be offered the choice of choosing which to make default. That can be done using the arrow and/or tab keys.

---

### Post by baudrillard on 2014-11-30
Both posts were helpful and relevent, but Kansasnoob's code did exactly what I needed. Thanks! Marked as solved.

---

