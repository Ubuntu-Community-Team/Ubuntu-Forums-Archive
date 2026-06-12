---
title: "Modifying Colours of Certain Texts In Firefox"
date: 2013-09-24
forum: Desktop Environments
---

### Post by 3246251196 on 2013-09-24
I like the dark *axiom* theme with xfce4. However, since the change, Firefox will show a page like [ATTACH=CONFIG]246480[/ATTACH]

I have looked in about:config, and searched for "color", the options are not quite showing the color shown in the attached screenshot which would be approx #E.......

Does anyone know how to override *this* particular type of text color?

Oh, I have also noticed automatic spell checker is not running either. Does anyone know where to enable this? (It does work in some things, not in others)

Thanks.

---

### Post by Frogs Hair on 2013-09-24
There is a spell checker bug that affects some users that goes back to 12.10 or earlier . You can manually start the spell checker by right clicking to open the context menu . Under Languages select the default language in use and the spell checker should work until the browser is closed. I added a spell check  extension to avoid this work around.  

One way I get around dark theme problems in Firefox is to use complete themes since many have their own font and color schemes. The default theme doesn't work well with most dark themes.

 [https://addons.mozilla.org/en-us/firefox/complete-themes/](https://addons.mozilla.org/en-us/firefox/complete-themes/)

---

### Post by vasa1 on 2013-09-24
> **3246251196 said:**
> I like the dark *axiom* theme ...

Does anyone know how to override *this* particular type of text color? ....
See if [Make firefox only use GTK theme on browser chrome, but ignore on websites]("http://askubuntu.com/q/254479/25656") or [Mediterranean themes for Unity - Change input form colors]("http://askubuntu.com/q/342497/25656")
is of help.

---

### Post by 3246251196 on 2013-09-25
> **vasa1 said:**
> See if [Make firefox only use GTK theme on browser chrome, but ignore on websites]("http://askubuntu.com/q/254479/25656") or [Mediterranean themes for Unity - Change input form colors]("http://askubuntu.com/q/342497/25656")
is of help.

Thank you both.

It looks like I will use the chrome/user*.css approach to manually change websites that are causing issues. I did install a "proper" dark theme for Firefox but even still I had a grey text on white background. However, this *.css solved this issue.

Cheers; Solved.

---

