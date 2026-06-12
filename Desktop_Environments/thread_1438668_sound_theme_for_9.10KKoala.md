---
title: "sound theme for 9.10KKoala"
date: 2010-03-25
forum: Desktop Environments
---

### Post by Chuck_N on 2010-03-25
Using 9.10 KKoala; standard sound theme package is far from satisfactory. 
  GOOGLE searches have provided only discussions on
the lack of themes and old references to few theme attempts. I don't much care if there's a big selection; just would like one good sound scheme. Know of any?

---

### Post by Daedal on 2010-04-02
there are a few sound themes on [gnome-look.org under system sounds]("http://gnome-look.org/index.php?xcontentmode=25&PHPSESSID=58717286942c93d96692d20ac5db8af0")
but the only ones that are usable right now are the ones that come packaged with an index.theme file which doesn't seem to be all that many. 

there is a star trek sound theme and then one called acoustica that comes with a script that changes some of the default ubuntu drumming sounds to acoustic guitar sounds.  other than those two i haven't really found anything yet.

---

### Post by Chuck_N on 2010-04-02
sure not much available; I'm surprised, but then
it's not a really important feature, I guess.

---

### Post by Daedal on 2010-04-03
or actually this thread sort of helps with making your own. [http://ubuntuforums.org/showthread.php?t=1226558&highlight=sound+themes](http://ubuntuforums.org/showthread.php?t=1226558&highlight=sound+themes)
it lists the file names you need for the various sound files and the format of the index.theme file

so i think the easiest thing to do would be to find a sound theme you like then copy your /usr/share/sound/ubuntu/ folder onto your desktop.

rename the copied "ubuntu" sound folder to MyTheme or whatever you want. then edit the index.theme file.

after that you pretty much just have to rename the new sound files, replace the old ones and convert them to .ogg if needed.
after that it's just a matter of moving your newly renamed folder back to /usr/share/sound/ and then picking that sound theme from your sound preferences.

---

### Post by Chuck_N on 2010-04-03
[COLOR=Red]> **Daedal said:**
> 
or actually this thread sort of helps with making your own. [http://ubuntuforums.org/showthread.php?t=1226558&highlight=sound+themes](http://ubuntuforums.org/showthread.php?t=1226558&highlight=sound+themes)
it lists the file names you need for the various sound files and the format of the index.theme file

so i think the easiest thing to do would be to find a sound theme you like then copy your /usr/share/sound/ubuntu/ folder onto your desktop.

rename the copied "ubuntu" sound folder to MyTheme or whatever you want. then edit the index.theme file.

after that you pretty much just have to rename the new sound files, replace the old ones and convert them to .ogg if needed.
after that it's just a matter of moving your newly renamed folder back to /usr/share/sound/ and then picking that sound theme from your sound preferences.
[/COLOR]   

wow sounds more complicated than I'm comfortable with right now. However, having read[ http://ubuntu-art.org/content/show.php/%22Borealis%22+sound+theme?content=12584]("http://ubuntu-art.org/content/show.php/%22Borealis%22+sound+theme?content=12584")  I sure would be interesting in installing the Borealis package.   -Chuck

---

### Post by d_e_monat on 2010-04-03
I attempted to install the Star Trek theme.  I had trouble with System>Preferences>Sound recognizing the theme.

What I found was the permissions on the folder were wrong.  Make sure that "allow access" is available for "other permissions"

---

