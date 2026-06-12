---
title: "Human in blue instead of brown"
date: 2005-03-31
forum: Desktop Environments
---

### Post by earobinson on 2005-03-31
Just as the name asks can i get the Human theme in blue instead of brown?

---

### Post by bored2k on 2005-03-31
[QUOTE=earobinson]Just as the name asks can i get the Human theme in blue instead of brown?[/QUOTE]
 Clearlooks in blue looks a little bit like it  8-[

---

### Post by earobinson on 2005-04-01
Ya it is, but all the other colours in Human are perfect, just not a fan of the brown. Any way i can edit this? Anyone else looking for something like this?

---

### Post by Buffalo Soldier on 2005-04-01
[QUOTE=earobinson]Ya it is, but all the other colours in Human are perfect, just not a fan of the brown. Any way i can edit this? Anyone else looking for something like this?[/QUOTE]Controls: Clearlooks-DeepSky. Window Border: Clearlooks. Icon: GNOME.

---

### Post by earobinson on 2005-04-01
[QUOTE=Buffalo Soldier]Controls: Clearlooks-DeepSky. Window Border: Clearlooks. Icon: GNOME.[/QUOTE]

The greay is a bit darker see

---

### Post by Buffalo Soldier on 2005-04-01
you're looking for a darker blue?

---

### Post by earobinson on 2005-04-01
[QUOTE=Buffalo Soldier]you're looking for a darker blue?[/QUOTE]
 no i want every thing the same but the brown to be blue, just that in the theme you said the grays are not the same

---

### Post by Buffalo Soldier on 2005-04-01
Yeah, now I see what you mean. I guess you either have to edit the metacity files (I have no idea how) or wait till someone creates a Human-Blue theme. It would interesting to see how it looks thought. Sorry for not being able to help you more here.

---

### Post by Darrena on 2005-04-02
*ducks*

Don't kill the messenger but the default Red Hat Bluecurve theme might be what you are looking for.  There is a port of the theme here:
[http://themes.freshmeat.net/projects/bluecurvedebian/](http://themes.freshmeat.net/projects/bluecurvedebian/)

I used alien to convert an RPM of the theme and it worked great so that may be an option for you as well.

*ducks again*

I know it isn't a popular choice, but like you I don't really like the tan theme...

*dives to the ground*

---

### Post by J. S. Jackson on 2005-04-02
Maybe you should check gnome-look.  There are loads of clearlooks themes in all different colors.  Surely you will find one that strikes your fancy?

---

### Post by earobinson on 2005-04-02
[QUOTE=J. S. Jackson]Maybe you should check gnome-look.  There are loads of clearlooks themes in all different colors.  Surely you will find one that strikes your fancy?[/QUOTE]
 looked at both, i want EVERYTHING the same, but the brown and nothing else has that

---

### Post by arctic on 2005-04-02
copy the theme from your /etc/usr/share/themes folder to your home folder . now open it and edit the gtkrc file. in there you will find some codes for colors:

    fg[ACTIVE]            = "#0F1A31"
    fg[SELECTED]        = "#FFFFFF"
    fg[NORMAL]        = "#000000"
    fg[PRELIGHT]        = "#000000"
    fg[INSENSITIVE]        = "#445362"

    bg[ACTIVE]        = "#BFC2C4"
    bg[SELECTED]        = "#3D4861"
    bg[NORMAL]        = "#DCDFE1"
    bg[PRELIGHT]        = "#E1E4E6"
    bg[INSENSITIVE]        = "#DCDFE1"

    base[ACTIVE]        = "#BFC2C4"
    base[SELECTED]        = "#3D4861"
    base[NORMAL]        = "#FFFFFF"
    base[PRELIGHT]        = "#3D4861"
    base[INSENSITIVE]    = "#B0B0B0"

    text[ACTIVE]        = "#0F1A31"
    text[SELECTED]        = "#FFFFFF"
    text[NORMAL]        = "#000000"
    text[PRELIGHT]        = "#000000"
    text[INSENSITIVE]    = "#445362"

each color has a combination of numbers and/or letters. just modify these to your liking and save the file. then rename the theme-folder to e.g. human-blue and copy it to your /home/yourdirectory/.themes folder.

if you do not know, which code is which color, open gimp or inkscape and select a color. you will find the color code there. (e.g. black= 000000, white = ffffff)

---

### Post by bvc on 2005-04-03
download
[http://www.kernow-webhosting.com/~bvc/theme/gtk/clearlooks/0.5/Clearlooks-HumanBlue.tar.gz](http://www.kernow-webhosting.com/~bvc/theme/gtk/clearlooks/0.5/Clearlooks-HumanBlue.tar.gz)

screenie's
[http://www.kernow-webhosting.com/~bvc/theme/gtk/clearlooks/0.5/Clearlooks-HumanBlue.jpg](http://www.kernow-webhosting.com/~bvc/theme/gtk/clearlooks/0.5/Clearlooks-HumanBlue.jpg)

[http://www.kernow-webhosting.com/~bvc/theme/gtk/clearlooks/0.5/Clearlooks-HumanBlue1.jpg](http://www.kernow-webhosting.com/~bvc/theme/gtk/clearlooks/0.5/Clearlooks-HumanBlue1.jpg)


hey arctic! :grin:

---

### Post by Jad on 2005-04-03
I love XFCE control in gnome, with Human borders and Clearlook Icons.

---

### Post by arctic on 2005-04-03
[QUOTE=bvc]download
[http://www.kernow-webhosting.com/~bvc/theme/gtk/clearlooks/0.5/Clearlooks-HumanBlue.tar.gz]("http://www.kernow-webhosting.com/%7Ebvc/theme/gtk/clearlooks/0.5/Clearlooks-HumanBlue.tar.gz")

screenie's
[http://www.kernow-webhosting.com/~bvc/theme/gtk/clearlooks/0.5/Clearlooks-HumanBlue.jpg]("http://www.kernow-webhosting.com/%7Ebvc/theme/gtk/clearlooks/0.5/Clearlooks-HumanBlue.jpg")

[http://www.kernow-webhosting.com/~bvc/theme/gtk/clearlooks/0.5/Clearlooks-HumanBlue1.jpg]("http://www.kernow-webhosting.com/%7Ebvc/theme/gtk/clearlooks/0.5/Clearlooks-HumanBlue1.jpg")


hey arctic! :grin:[/QUOTE]
hey, man... i almost thought you really got lost. nice to see you again. :D

---

### Post by earobinson on 2005-04-03
[QUOTE=bvc]download
[http://www.kernow-webhosting.com/~bvc/theme/gtk/clearlooks/0.5/Clearlooks-HumanBlue.tar.gz](http://www.kernow-webhosting.com/~bvc/theme/gtk/clearlooks/0.5/Clearlooks-HumanBlue.tar.gz)

screenie's
[http://www.kernow-webhosting.com/~bvc/theme/gtk/clearlooks/0.5/Clearlooks-HumanBlue.jpg](http://www.kernow-webhosting.com/~bvc/theme/gtk/clearlooks/0.5/Clearlooks-HumanBlue.jpg)

[http://www.kernow-webhosting.com/~bvc/theme/gtk/clearlooks/0.5/Clearlooks-HumanBlue1.jpg](http://www.kernow-webhosting.com/~bvc/theme/gtk/clearlooks/0.5/Clearlooks-HumanBlue1.jpg)


hey arctic! :grin:[/QUOTE]
 thanks that is perfect

---

### Post by PaRRoT.it on 2005-04-04
[QUOTE=earobinson]no i want every thing the same but the brown to be blue, just that in the theme you said the grays are not the same[/QUOTE]
 You have to use Clearlooks-DeepSky as Control and you have Human in Blue.

---

### Post by bvc on 2005-04-04
[QUOTE=PaRRoT.it]You have to use Clearlooks-DeepSky as Control and you have Human in Blue.[/QUOTE]
not quite
[IMG]http://www.kernow-webhosting.com/~bvc/theme/images/Ds-Hb-compare.png[/IMG]

---

### Post by earobinson on 2005-04-05
[QUOTE=bvc]not quite
[IMG]http://www.kernow-webhosting.com/~bvc/theme/images/Ds-Hb-compare.png[/IMG][/QUOTE]
 what program shows you the themes like that

---

### Post by bvc on 2005-04-05
[QUOTE=earobinson]what program shows you the themes like that[/QUOTE]
[http://www.users.monornet.hu/linux/](http://www.users.monornet.hu/linux/)
go to 'stuffs'

---

