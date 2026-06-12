---
title: "gnome toolbars too big"
date: 2006-02-20
forum: Desktop Environments
---

### Post by bernardfrancois on 2006-02-20
After I installed Ubuntu (already a long time ago), it seemed like the 14" screen of my laptop got smaller... The problem is that the titlebars of the windows here are bigger than my preference in FC4. Here is a [screenshot](http://www.evonet.be/~bfran/screenshots/hpob4150.jpg) in which you can see the size of the titlebars how it was before.

I would like to have such minimal titlebars in Ubuntu as well. Can anyone explain how to do that? Ideal would be a solution without an increase of disk usage (since I only have few megabytes left).

Thanks in advance to anyone who can help me!

---

### Post by angkor on 2006-02-20
Just try a different theme. System -> Preferences -> Themes. Some themes have smaller titlebars.

---

### Post by bernardfrancois on 2006-02-20
All I have here is 'human', 'clearlooks' and 'default', which all have the same big toolbars.

---

### Post by opticyclic on 2006-02-20
[QUOTE=bernardfrancois]All I have here is 'human', 'clearlooks' and 'default', which all have the same big toolbars.[/QUOTE]
Try downloading something from [www.gnome-look.org](www.gnome-look.org)

---

### Post by bernardfrancois on 2006-02-20
I did some searches on that site (in the description of the GTK 2.x themes) for the search terms *minimalistic, minimal, fast, performance*, and I didn't see even one theme with smaller title bars. I also checked some of the highest rated and the most downloaded GTK 2.x themes.
I searched google on similar terms, with no results as well.

Is anyone using a theme with small title bars and read this? Please give me a reference or at least a name...
I would like to have seen cut the size of those bars in half... 8)

---

### Post by pataphysician on 2006-02-20
once you chose a theme you can click on "theme details," to customize it. the window border tab has about 15 or so borders you can chose (at least, that's how many i have, and i don't think i've downloaded anything extra here). "esco," is pretty thin. i use "sloth," and there's also "smokey," which aren't too big.

---

### Post by bernardfrancois on 2006-02-20
Thanks, I just tried esco, it seems to be the tinnest available here.

Now that I know that I have to search for borders, I found more on the following page:
[http://art.gnome.org/themes/metacity/?sort_by=add_timestamp&thumbnails_per_page=1000&view=list&order=DESC](http://art.gnome.org/themes/metacity/?sort_by=add_timestamp&thumbnails_per_page=1000&view=list&order=DESC)

I checked all of them by comparing the border sizes in the pictures there, I installed the ones which appear to have the smallest border sizes, and the one called **spiffcity** seems to have the smallest borders. But it turned out that the sizes in the pictures aren't real sizes; I tried 'sandwich' also (which seemed to have the smallest borders), but that set had a huge title bar... So maybe I didn't find the smallest yet (but this will do now).

Looking at the url of the previous page, I noticed I should look under the Metacity section of gnome-look.org . Unfortunately, there's no easy way to compare border sizes there, since for each style there is a full-screen screenshot. I won't check it.

But if somebody has a nice and very small border set, feel free to post what you use here...

[edit]
Maybe I should try to make a more ubuntu-flavoured tiny border set (with the same brown color). The black-blue colors are spoiling my ubuntu-mood now :)
[/edit]

---

### Post by maruchan on 2006-02-28
Can we see a screenshot of what your large titlebars look like? You know that the font size influences this, right?

---

### Post by JimS on 2006-02-28
...

I have a 20" monitor.  I killed all tool bars, except the top panel.
This gives me a clean bottom and sides.  Maybe on your 14"
monitor this would not work.  

Probably better for you to keep the bottom panel also.

[COLOR="Blue"]JimS
Prostate Cancer Aware
[/COLOR]
...

---

### Post by soulestream on 2006-02-28
are you using the same resolution as you did before?


soule

---

### Post by bernardfrancois on 2006-03-01
[QUOTE=maruchan]Can we see a screenshot of what your large titlebars look like? You know that the font size influences this, right?[/QUOTE]
I don't have that laptop with me today, probably tomorrow I will post a screenshot of my desktop before and after the change.
I don't know what you mean about the influence of the font size, can you clarify that a bit?

[QUOTE=soulestream]are you using the same resolution as you did before?[/QUOTE]
Im not sure if this question was directed to me.
I didn't change the resolution, since this is won't give a good result on a 14" lcd screen.

---

### Post by maruchan on 2006-03-01
> I don't know what you mean about the influence of the font size, can you clarify that a bit?

Well, last I checked (haven't used GNOME lately), the size of the titlebar font dictates the size of the titlebar. I had awkwardly-big titlebars until I chose a different font for them in system prefs. Hope that helps somehow.

---

### Post by bernardfrancois on 2006-03-01
I checked the theme *theme details* section of *theme preferences* (which is what you get when you click *system > preferences > Theme*, and I didn't see anything about setting the font used in the titlebar. 
As far as I know, the font depends on the style of titlebars...

---

### Post by Ramses de Norre on 2006-03-01
```
gconf-editor /apps/metacity/general
```
There's a key titlebar_font by which you can set the font.

---

### Post by maruchan on 2006-03-01
No, the font setting I changed didn't have anything to do with themes, I just used the Fonts preferences item (can't remember the name, but it's pretty easy to find). There is an entry for "titlebar font" and it lets you choose the style of antialiasing you want, too.

---

### Post by maruchan on 2006-03-01
System -> Preferences -> Font -> Window title font: Mine is set to 9...if yours is set to 12, 13, etc. your window titles will be inflated. So be sure to check it.

---

### Post by Ramses de Norre on 2006-03-01
That's the same as the one in gconf.

---

### Post by bernardfrancois on 2006-03-01
Interesting tool... but dangerous! I was playing around with the resolution of the fonts, and I changed the value from 96 to 1200. Now everything is HUGE, and there's no way I can set it back like that... Can anyone help me out to set it back?

[edit]
I solved it.
I switched to another user and entered the following commands:
```

sudo xhost +
su ber
gconf-editor

```
(ber is the user that I used to mess with gconf-editor)
[/edit]

[edit2]
Seems to be safer to use system > preferences > fonts.
[/edit2]

---

### Post by angkor on 2006-03-01
[QUOTE=bernardfrancois]Interesting tool... but dangerous! I was playing around with the resolution of the fonts, and I changed the value from 96 to 1200. Now everything is HUGE[/QUOTE]

*lol*

Btw if you _really_ want minimal.....I don't have _any_ titlebars, just thin lines of different colour for active / inactive windows. I use the [Sawfish windowmanager with the lines theme]("http://www.xs4all.nl/~gerben77/pics/Screenshot.png")

Very minimal but looks great imo.:)

---

### Post by drotter on 2006-03-01
You can just go to system-preferences-font...and click on details.

You can change the font resolution from 96 to something like 75.  I think that that might be what you're looking for.  But it changes the font size globally instead of specifically with the title bars.

---

### Post by bernardfrancois on 2006-03-01
[QUOTE=angkor]Btw if you _really_ want minimal.....I don't have _any_ titlebars, just thin lines of different colour for active / inactive windows.Very minimal but looks great imo.:)[/QUOTE]

How do you move your windows?

---

### Post by angkor on 2006-03-01
[QUOTE=bernardfrancois]How do you move your windows?[/QUOTE]

Alt-Left Button (it grabs the focused window anywhere)

Alt-Right Button to resize

---

