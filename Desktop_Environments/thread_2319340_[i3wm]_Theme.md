---
title: "[i3wm] Theme"
date: 2016-04-03
forum: Desktop Environments
---

### Post by Tichun on 2016-04-03
Greetings.
As I've changed from Unity to i3wm[SUP][1][/SUP]  I noticed that things like scrollbars and new tab sign etc. have changed and so
I'm willing to change them to something that steals less attention but would like to do so from system config or firefox configs and not from Firefox userstyles or external programs.
This is mainly about FF and LibreOffice as scrollbars in Nautilus and Terminal are same as they were.

[SUP][1] - (200 MiB vs 20 MiB vram at idle and my gc has 256MiB)[/SUP]

---

### Post by vasa1 on 2016-04-03
What version of Firefox are you using? Fx 45? Fx 46 (beta)?

---

### Post by Tichun on 2016-04-03
I'm on 45.0.1

---

### Post by vasa1 on 2016-04-03
A screenshot might help ...

---

### Post by Tichun on 2016-04-03
[ATTACH=CONFIG]268152[/ATTACH][ATTACH=CONFIG]268153[/ATTACH][ATTACH=CONFIG]268154[/ATTACH][ATTACH=CONFIG]268155[/ATTACH]

i3wm uses those and I want to change them.

---

### Post by oldos2er on 2016-04-03
Did you install lxappearance as suggested in your link? It will pull in gtk2-engines so you should be able to do what you want.

---

### Post by Tichun on 2016-04-03
I've tried it but thought of something more precise.
Now I'm using just stylish addon for firefox to change those as anyway using additional software to change it misses the point same way or even lil' bit more as it messes system and used method could mess ff only.
I thought that if those things were defined somewhere that I could redefine them and customize it a lot.

---

### Post by vasa1 on 2016-04-03
Seems like the Raleigh theme.

What is the output of *ls -d /usr/share/themes/*/* and *ls -d /usr/share/themes/*/*/*?

---

### Post by Tichun on 2016-04-04
```
~$ ls -d /usr/share/themes/*/
/usr/share/themes/Adwaita/       /usr/share/themes/Default/       /usr/share/themes/Radiance/
/usr/share/themes/AgingGorilla/  /usr/share/themes/Emacs/         /usr/share/themes/Raleigh/
/usr/share/themes/Ambiance/      /usr/share/themes/Esco/          /usr/share/themes/Redmond/
/usr/share/themes/Atlanta/       /usr/share/themes/HighContrast/  /usr/share/themes/Simple/
/usr/share/themes/Bright/        /usr/share/themes/Industrial/    /usr/share/themes/ThinIce/
/usr/share/themes/Clearlooks/    /usr/share/themes/Metabox/
/usr/share/themes/Crux/          /usr/share/themes/Mist/
```

```
~$ ls -d /usr/share/themes/*/*/
/usr/share/themes/Adwaita/metacity-1/       /usr/share/themes/Esco/metacity-1/
/usr/share/themes/AgingGorilla/metacity-1/  /usr/share/themes/HighContrast/gtk-2.0/
/usr/share/themes/Ambiance/gtk-2.0/         /usr/share/themes/HighContrast/gtk-3.0/
/usr/share/themes/Ambiance/gtk-3.0/         /usr/share/themes/HighContrast/metacity-1/
/usr/share/themes/Ambiance/metacity-1/      /usr/share/themes/Industrial/gtk-2.0/
/usr/share/themes/Ambiance/unity/           /usr/share/themes/Metabox/metacity-1/
/usr/share/themes/Atlanta/metacity-1/       /usr/share/themes/Mist/gtk-2.0/
/usr/share/themes/Bright/metacity-1/        /usr/share/themes/Radiance/gtk-2.0/
/usr/share/themes/Clearlooks/gtk-2.0/       /usr/share/themes/Radiance/gtk-3.0/
/usr/share/themes/Crux/gtk-2.0/             /usr/share/themes/Radiance/metacity-1/
/usr/share/themes/Crux/metacity-1/          /usr/share/themes/Radiance/unity/
/usr/share/themes/Default/gtk-2.0-key/      /usr/share/themes/Raleigh/gtk-2.0/
/usr/share/themes/Default/gtk-3.0/          /usr/share/themes/Redmond/gtk-2.0/
/usr/share/themes/Emacs/gtk-2.0-key/        /usr/share/themes/Simple/metacity-1/
/usr/share/themes/Emacs/gtk-3.0/            /usr/share/themes/ThinIce/gtk-2.0/


```

---

### Post by vasa1 on 2016-04-04
> **Tichun said:**
> Greetings.
As I've changed from Unity to i3wm[SUP][1][/SUP]  I noticed that things like scrollbars and new tab sign have changed and so
I'm willing to change them to something that steals less attention but would like to do so from system/firefox configs and not from Firefox userstyles.
This is mainly about FF as scrollbars in Nautilus and Terminal are same as they were.

That is the only similar post that I've found - [https://www.reddit.com/r/unixporn/comments/1vl1g2/archi3_how_do_i_change_the_look_of_my_scrollbars/](https://www.reddit.com/r/unixporn/comments/1vl1g2/archi3_how_do_i_change_the_look_of_my_scrollbars/) - but I don't know how to follow as those GTK folders are empty in my 16.04 and my skill would allow me to edit them only by changing values and I'm not sure what would it even affect, probably not FF?
...

[LIST]
[*]You are on 16.04.
[*]You installed a window manager called i3wm
[*]You have Firefox 45.x.
[*]You say that "those GTK folders are empty". That confuses me. Please be specific here without referring us to other threads elsewhere. You don't mention which theme you're using. Your images remind me of the Raleigh theme which is used whenever something is broken. You don't mention whether you have some sort of theme changer. IIUC, Unity requires specialized tools to change themes.
[*]You say that Nautilus and Terminal are the same as they were. AFAIK, changing a window manager should not affect scrollbars.
[*]I've fiddled a lot with scrollbars. 
[LIST][*]If you're on vanilla Firefox 45, the gtkrc folder of the active theme controls what your scrollbars look like.
[*]If you're on vanilla Firefox 46 beta, which currently is in gtk3 mode, your scrollbars are probably controlled by gtk-widgets.css.
[*]If you've installed a variety of styles and extensions, you need to detail those 
[/LIST][/LIST]

---

### Post by oldos2er on 2016-04-05
I believe *lxappearance* is the theme changer, perhaps OP could clarify.

---

### Post by Tichun on 2016-04-24
Fixed it by creating ~/.gtkrc-2.0 with gtk-theme-name = "themeName" inside.

---

