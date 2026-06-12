---
title: "[SOLVED] Where are font settings stored?"
date: 2008-12-28
forum: General Help
---

### Post by dwasifar on 2008-12-28
When you change the font settings in System>Preferences>Appearance>Fonts, where are your settings stored?  I'm hoping to be able to change the font settings with a script or by editing a settings file.

---

### Post by TransitMan on 2008-12-29
> **dwasifar said:**
> When you change the font settings in System>Preferences>Appearance>Fonts, where are your settings stored?  I'm hoping to be able to change the font settings with a script or by editing a settings file.

Either in /home/<user name>/.fonts or in /usr/share/fonts

---

### Post by dwasifar on 2008-12-29
> **TransitMan said:**
> Either in /home/<user name>/.fonts or in /usr/share/fonts

No, I know where the fonts themselves live.  I want to know where the SETTINGS go.  Like say for instance you go to System>Preferences>Appearance>Fonts, and you change the application font setting from 10 point to 8 point.  Where is that setting stored?

---

### Post by zika on 2008-12-29
> **dwasifar said:**
> No, I know where the fonts themselves live.  I want to know where the SETTINGS go.  Like say for instance you go to System>Preferences>Appearance>Fonts, and you change the application font setting from 10 point to 8 point.  Where is that setting stored?

the best way to get for yourself answer to the things like that is to change something and then to search for the file that just have changed ... ;)

---

### Post by lswest on 2008-12-29
For me my settings are in .font.conf (in my home directory) and there are some cache files in .fontconfig/

Not 100% sure these are Ubuntu's though (I had ArchLinux installed using the same home partition where I had to create the file for fonts in openbox, it is still from that install, but I don't know if the settings are being used, or if they just happen to be Ubuntu's default).

Hope that helps,
Lswest

*EDIT* [http://www.howtogeek.com/howto/ubuntu/enable-smooth-fonts-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/enable-smooth-fonts-on-ubuntu-linux/)

If you want auto-hinting:
> Configuration

The standard Gnome fonts control panel does not allow one to configure the use of the auothinter. This must be configured using the command line:

% sudo dpkg-reconfigure fontconfig-config

Executing this command will result in some dialog questions. In the first question, be sure to choose the "autohinter" option over "native". The remaining two questions can be answered with their default selections.

Finally, use the Gnome Appearance Preferences to set the remaining settings. Under Smoothing, choose Subpixel and under Hinting choose Slight. from [here]("http://www.ubuntutips.net/node/35")

---

### Post by sstusick on 2008-12-29
> **zika said:**
> the best way to get for yourself answer to the things like that is to change something and then to search for the file that just have changed ... ;)
You could be a little clearer than that.

---

### Post by zika on 2008-12-29
> **sstusick said:**
> You could be a little clearer than that.

I'm sorry, I did not want to offend anybody. I just gave a hint on how I am answering for myself on questions like that. since I was not prepared to explore that myself (cause I was in a 'project' of my own at this time) I thought that a hint like that could be helpfull. I was obviously wrong (eventhough I've been very thankfull for hints like this given on this great forum). I will surely get a getter grip on my behaviour and control myself ... sorry again.

---

### Post by dwasifar on 2008-12-29
> **zika said:**
> the best way to get for yourself answer to the things like that is to change something and then to search for the file that just have changed ... ;)

I've actually already tried that, with no real luck.  I did find that ~/.gconf/apps/nautilus/preferences/%gconf.xml changed, but when I looked at that file it only contained one font setting ( desktop font = Sans 8 ).  And that wasn't even the font setting I changed.  So I have to think they're being stored somewhere else and not showing up in this kind of search.  I was hoping someone could point me to some documentation on how this is handled.

---

### Post by ajcham on 2008-12-29
**Font faces (family, size):**
~/.gconf/desktop/gnome/interface/%gconf.xml

**Font rendering (anti-aliasing, hinting):**
~/.gconf/desktop/gnome/font_rendering/%gconf.xml

---

### Post by dwasifar on 2008-12-29
> **ajcham said:**
> **Font faces (family, size):**
~/.gconf/desktop/gnome/interface/%gconf.xml

**Font rendering (anti-aliasing, hinting):**
~/.gconf/desktop/gnome/font_rendering/%gconf.xml

Well, that got me far enough to know that I probably don't want to do it this way.  :)

Appearance > Fonts gives you the opportunity to set five fonts: Application, Document, Desktop, Window title, and Fixed width.  Of those, ~/.gconf/desktop/gnome/interface/%gconf.xml contains the settings for Fixed and Document fonts; ~/.gconf/apps/nautilus/preferences/%gconf.xml contains the setting for Desktop font; and I haven't found the others yet.  I sort of expected that they would all be in the same place, and that doesn't appear to be so.  The point here was to try to script some font changes but if I have to hit all these different files for it I'm probably not going to bother.

It's too bad Gnome doesn't handle fonts like KDE's system settings, where you can apply a change globally.  Say you want them all to be size 8; in Gnome's Appearance > Fonts you have to change each one to 8 individually, whereas in KDE you can check a box and they all go to 8 in one shot.

Edit: It appears that the %gconf.xml files are not the only place that the font information is stored.  I tried editing one manually and found that, though the font changed, when I opened Appearance > Fonts, the old value was still there.  So it must be storing it somewhere else.  The second or third manual edit broke some of the window rendering, too, making everything fall back to what looks like default X windows with big blocky tabs and taskbars.  Fortunately logging out and back in restored things to normal.

---

