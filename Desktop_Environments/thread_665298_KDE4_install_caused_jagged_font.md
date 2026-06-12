---
title: "KDE4 install caused jagged font"
date: 2008-01-12
forum: Desktop Environments
---

### Post by subru77 on 2008-01-12
Hi, 

I installed KD4 in my Ubuntu install today. But now the fonts are jagged once you login to gnome or KDE. The login  window seems fine. 

I tried reconfigure xorg (Should I?) and then uninstalled KD4.(thinking that will solve the problem)
But I am still having  no "anti alias" 

Could someone please help ? 

I have Nvdia video card in my system FYI

---

### Post by pecos7 on 2008-01-12
I have the same problem, but i have an ATI card. I did the same thing and like you I didn't resolv the problem.

---

### Post by subru77 on 2008-01-13
I am not sure if this is the right solution. I tried adding the font local.conf file as mentioned in the below thread 

[http://ubuntuforums.org/showthread.php?t=622951&highlight=fuzzy+fonts](http://ubuntuforums.org/showthread.php?t=622951&highlight=fuzzy+fonts)

This may not be the correct method. But it worked for me. 

Hope to see someone give a better solution.

---

### Post by lentiflo13 on 2008-01-17
This will solve all your font problems in any of the *buntu's:

**1)** Either in KDE, GNOME, or XFCE set font antialiasing to: **OFF**.

**2)** Go to: [http://www.sharpfonts.com/]("http://www.sharpfonts.com/")

**3**) Click on **Download** at the top.

**4)** Download all .exe files. (These are the original microsoft fonts.)
[INDENT]-(Don't use the *ubuntu microsoft fonts.)[/INDENT]

**5)** Follow the simple instructions on the site. (There is only 3 steps there.)

**6)** Open up a terminal and update ur font cache: **sudo fc-cache -fv**

**6)** Log out and in again, (I recommend rebooting.)

_Recommendations:_
[INDENT]-Set Desktop and application font to Verdana or Tahoma (Same as Windows).[/INDENT]
[INDENT]-Set Window Title font to Verdana Bold (It's a very crisp font)[/INDENT]
[INDENT]-Use Times New Roman or Tahoma for other font setttings.[/INDENT]
[INDENT]-Use Courier New for the terminal font.[/INDENT]

_Firefox Settings:_
[INDENT]-Set Firefox Default font to: **Times New Roman, Size 16**[/INDENT]
[INDENT]-Now Click Advanced in that same Options dialog:[/INDENT]
[INDENT][INDENT]-Set: Proportional to **Serif** [/INDENT][/INDENT]
[INDENT][INDENT]-Set: Serif to **Times New Roman** [/INDENT][/INDENT]
[INDENT][INDENT]-Set: Sans-Serifl to **Arial** [/INDENT][/INDENT]
[INDENT][INDENT]-Set: Monospace to **Courier New**,Size 13 [/INDENT][/INDENT]

Your Results will look similar to this:
[IMG]http://www.mikeanzalone.com/kde4shot.png[/IMG]

**Enjoy Your nice fonts!!**

---

### Post by Robvdl on 2008-01-25
I had something similar...

I was happily running Ubuntu Gutsy using Gnome, and decided to give KDE4 a shot from the PPA mentioned on the Kubuntu site.

I didn't really like KDE4 as I kind of suspected, and went back to Gnome. I noticed my terminal font was suddenly a lot more bold than before, and a bit more fuzzy. Now I don't wish to turn hinting off all together like some examples seem to recommend, infact I prefer to only change Ubuntu's font settings to 'best contrast', which I prefer on my LCD, and leave everything as is.

Thing is, KDE4 left all other fonts alone, but only did something to the Gnome terminal font. It only affects the Gnome terminal too, the integrated terminal for example in my Geany editor for example is fine, even though both Geany's terminal, and Gnome terminal use the exact same font (DejaVu Sans Mono 11, regular), yet Gnome terminal's is using bold, even though in it's options are specifically set to regular.

I played around a little, but can't seem to be able to fix it, so I will just have to get used to it, until I reload Hardy.

---

### Post by Robvdl on 2008-01-25
Actually, I just found the solution:

KDE4 seems to have added a .fonts.conf file in my home directory, which was causing only Gnome Terminal to have bold fonts, other applications did not seem to be affected.

Close any Gnome Terminal windows, delete the .fonts.conf file, open Gnome Terminal up again, it should be fixed then.

I have not yet tested if this file is recreated if I log back into KDE 4, but if it does, I can always create a little script that deletes this file every time I log into Gnome as a workaround.

---

