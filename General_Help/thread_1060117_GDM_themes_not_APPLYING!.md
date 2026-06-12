---
title: "GDM themes not APPLYING!"
date: 2009-02-04
forum: General Help
---

### Post by JK3mp on 2009-02-04
Alright, iv'e been trying to install a GDM theme but it WILL not allow me to change from default theme. For some reason when i do this. If i click logout to view then it just shows some line of text including loading boot scripts etc. and then shows the login with the SAME default human theme. When i try to restart it, it then drops me to the xfix, recover, and dropt to root terminal options. I can reboot again and it will generally come back but with the same default human theme.Im using 8.04 hardy heron if that makes any diffrence. Any suggestions of solutions would be appreciated.

---

### Post by RedSingularity on 2009-02-04
Are you going to System>Administration>Login window?  If so did you try Setting STYLE to Themed and setting THEME to Selected only?

---

### Post by JK3mp on 2009-02-08
yes i've tried that still no luck. It appears it won't save any settings i change in the Login manager.

---

### Post by JK3mp on 2009-02-10
Okay so does noone have any idea's why this would be? Also i just noticed i can't change theme of VLC player. I used to be able to..now its stuck on the one i had it on. Idk if these problems go together or not..but i don't like it one bit.xD lol. Any help appreciated. Thnx ahead.

---

### Post by JK3mp on 2009-02-10
Ummm.... *bump*

---

### Post by JK3mp on 2009-02-11
OK...ANY help is appreciated...thus far i've concluded the majority of my problem isn't that there not applying its just not saving ANY changes i make in the Login Window manager... :( ..any idea's?

---

### Post by JK3mp on 2009-02-11
Wow so no one has any idea wat could be up?

---

### Post by RedSingularity on 2009-02-11
Type this in terminal:    sudo gedit /etc/gdm/gdm.conf-custom

You may be able to change the theme manually from here.
Its under GraphicalTheme:

---

### Post by JK3mp on 2009-02-11
It won't open the file... :(. Just goes to next line like it worked but then just stay's there and it never opens.

---

### Post by RedSingularity on 2009-02-11
Ok so we can try to get to the file manually.  In terminal type ```
sudo nautilus /etc/gdm
```  You should see a directory with folders named "Int" "modules" "PostLogin".  (These are only a few that are actually in there)  You should see a file named  ** "gdm.conf-custom"**.  Open that file and that is where you need to be.  If that doesnt work you will probably have to reinstall your system because there are some major files missing!

---

### Post by JK3mp on 2009-02-12
Says no application installed for this file type.. :( tried opening in gedit and said could not read the coding if trying to open binary blah blah blah et

---

### Post by JK3mp on 2009-02-12
*bump*?

---

### Post by RedSingularity on 2009-02-12
I think your asking for a total reinstall then.  I am out of ideas.  If you want you can try putting this question the the "General" area.  There are a lot more people in there all the time.  Someone there may have a fix but i cant guarantee it.  No harm in trying though.

---

