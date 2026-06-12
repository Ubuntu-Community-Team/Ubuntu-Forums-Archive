---
title: "Restore Dapper Human theme"
date: 2006-07-02
forum: Desktop Environments
---

### Post by Chua-Chua on 2006-07-02
Hello,

I've tried installing Symphony OS's Mezzo and I tried installing the metatheme theme.
However, this messed up ALL of my themes, replacing the orange colours of Human theme with blue. All of the Dapper themes are now blue.

Is there a way of restoring all the themes?

I tried to search for "theme" in Synaptic and reinstall those packages, but I still have the blue colours.
I saw in one forum that deleting the .gnome folder works. I deleted the .gnome and .gnome2 folders but I still get blue colours.


Any tips?

---

### Post by Rui Pais on 2006-07-02
Hi,
Human theme belongs to ubuntu-artwork package.

Human icons are stored in /usr/share/icons/Human/

You can search for which package a file belongs usinf dpkg -S:
```
 dpkg -S /usr/share/icons/Human/index.theme
ubuntu-artwork: /usr/share/icons/Human/index.theme
```

hope that helps

---

### Post by Chua-Chua on 2006-07-02
I've done that, but Human still looks blue.

I think the metatheme install screwed up Gnome's colours.
I removed ubuntu-artwork and the Gnome's themes still look blue.

Is there a way to "dpkg-reconfigure" the themes?

Even Grand Canyon theme is blue.
[IMG]http://this.boldlygoingnowhere.org/pictures/theme_screenshot.png[/IMG]

---

### Post by Rui Pais on 2006-07-02
[QUOTE=Chua-Chua]I've done that, but Human still looks blue.

I think the metatheme install screwed up Gnome's colours.
I removed ubuntu-artwork and the Gnome's themes still look blue.

Is there a way to "dpkg-reconfigure" the themes?

Even Grand Canyon theme is blue.[/QUOTE]

Oh, do you mean window borders and controls...
Just click on the 'Theme Details' button... you should be able to choose among several themes.

---

### Post by Chua-Chua on 2006-07-03
Thanks for your help and responses.

I got it fixed.

I read the metatheme README and it turns out metatheme overrides the theme's toolkits with its own...which causes ALL themes to adapt the blue colours.

The readme states that to turn off the metatheme toolkit,
enter:
>metatheme-install -u

I did that and restarted my session...Human theme went back to normal.

---

