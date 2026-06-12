---
title: "Please teach me how to install this theme?"
date: 2009-02-20
forum: Desktop Environments
---

### Post by nemomarlin on 2009-02-20
hi,

Can someone teach me how to install this theme? It's harder to install then the average theme. I am unable to extract it to theme folder. I love this theme. So please help me. thanks!

[http://gnome-look.org/content/show.php/Orange+door+hinge?content=77212](http://gnome-look.org/content/show.php/Orange+door+hinge?content=77212)

---

### Post by Armor Nick on 2009-02-21
Let's see, I think I used this theme a long time ago...
You should extract the archive and then put it under ~/.themes or /usr/share/themes
If I'm wrong, correct me as I'm currently not using Linux so I can't check it.

---

### Post by pastalavista on 2009-02-21
Extract the folder and archive it again as a tar.gz file, then drag the tar.gz into the System>Preferrences>Appearance>Theme window.

---

### Post by nemomarlin on 2009-02-21
I tried both methods but it didn't work. I think I need to run ubuntu as root? How do I do that?

---

### Post by ellalan on 2009-02-21
Download the theme to your desktop,right click and select "extract here",
then system->preferences-> Appearance and select Themes tab,now drag the extracted folder in to themes. HTH.

---

### Post by nemomarlin on 2009-02-21
Thanks. It worked beautifully. 
But it says the theme will not look as intended because GTK+ theme engine is not installed. 

Also how do I install the emerald window border that goes with the theme? Do I change some compiz settings?
[http://gnome-look.org/content/show.php/Orange+door+hinge?content=77207](http://gnome-look.org/content/show.php/Orange+door+hinge?content=77207)

---

### Post by mcduck on 2009-02-22
> **nemomarlin said:**
> Thanks. It worked beautifully. 
But it says the theme will not look as intended because GTK+ theme engine is not installed. 

Also how do I install the emerald window border that goes with the theme? Do I change some compiz settings?
[http://gnome-look.org/content/show.php/Orange+door+hinge?content=77207](http://gnome-look.org/content/show.php/Orange+door+hinge?content=77207)

don't worry about the error, it's just a bug in the theme manager itself. (when it tells you that it's missing a *GTK+ engine "*, that's a bug. When it tells you that it's missing a *GTK+ engine "nameoftheengine"* it's a proper warning and you need to install the engine that's missing for the theme to work correctly).

For the emerald theme, you need to install the Emerald Theme Manager, and probably Emerald itself since it's not likely that you have it installed if you haven't got the theme manager for it.. When you have both installed change the command for windo manager in Compiz settings to "/usr/bin/emerald", and use the Emerald Theme manager to install & enable your theme.

---

### Post by nemomarlin on 2009-02-22
thanks guys, there's just one last thing to do. I need to change the font to AvantGarde LT Medium. But it is not available as default. What do I do?

---

### Post by mcduck on 2009-02-22
Find the font somewhere, then put it into ~/.fonts (create the directory if it doesn't exist) or /usr/share/fonts (for system-wide installation).

After that, go to System/Preferences/Appearance and set the font on the Fonts-tab. If you are not able to see the font there log out and back again, programs sometimes need this before detecting new installed fonts.

---

### Post by nemomarlin on 2009-02-22
I am having difficulty finding the font(that's free for download). What kind file is font folder? I mean the suffix like .doc, .jpg..

---

### Post by balaknair on 2009-02-22
For the font ttf
[http://www.4shared.com/file/80527999/920a5bc8/ITC_Avant_Garde_Gothic_LT_Medium.html](http://www.4shared.com/file/80527999/920a5bc8/ITC_Avant_Garde_Gothic_LT_Medium.html)
[http://www.4shared.com/file/54523219/b6ae98b4/Avant_Garde_Medium_BT.html](http://www.4shared.com/file/54523219/b6ae98b4/Avant_Garde_Medium_BT.html)

Couldn't find a link for AvantGarde LT Medium, not one that's free anyway. It seems it's not a free font, so I'd suggest using something else(check out the 'liberation' fonts, available in the Ubuntu repositories, looks fantastic).

A font file will have a suffix like .ttf or .otf and to install it just copy it into the /home/*username*/.fonts/ folder. If you want to enable it for all users on the computer, copy it into /usr/share/fonts/

---

### Post by nemomarlin on 2009-02-22
Cool I had to log in as root to install the font but it worked thanks.

---

### Post by balaknair on 2009-02-22
The folder in your home directory is a hidden folder(to see hidden files and folders, open your home folder, and press ctrl+h ---> the hidden files and folders will have a . before their names, like  .fonts or .icons, just find the one you want, double click to open, and copy the file(xxxx.ttf) into it).

Alternatively, you can install it to /usr/share/fonts/ so that it is installed for all users. Open Nautilus file browser with admin privileges(alt-F2--> gksudo nautilus /usr/share/fonts/truetype), and paste the ttf file there).


You might need to log out and log in again to see the font in your list of available fonts.

---

### Post by mcduck on 2009-02-23
> **nemomarlin said:**
> Cool I had to log in as root to install the font but it worked thanks.

You *never* have to log in as root in Ubuntu. Use sudo instead.

In this case you could have ran "gksudo nautilus" to open the file manager with root permissions, and then use that to move the font file into /usr/share/fonts.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by nemomarlin on 2009-02-26
> **mcduck said:**
> You *never* have to log in as root in Ubuntu. Use sudo instead.

In this case you could have ran "gksudo nautilus" to open the file manager with root permissions, and then use that to move the font file into /usr/share/fonts.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Thank you so much for that piece of information!

---

