---
title: "Default GTK/Metacity theme for new users"
date: 2005-12-23
forum: Desktop Environments
---

### Post by nocturn on 2005-12-23
I would like to set a system up so that all new users get assigned a certain GTK and Metacity theme with specific icon set and a custom background.

What would be the easiest way to do this?

---

### Post by mcduck on 2005-12-23
I think that you can create one user account, set things the way you want and then copy everything in that users home directory to /etc/skel/

Not sure about that, I've never tried ;)

edit: Here's something for you: [http://www.ubuntuforums.org/showthread.php?t=67831&highlight=skel](http://www.ubuntuforums.org/showthread.php?t=67831&highlight=skel)

---

### Post by nocturn on 2005-12-30
> **mcduck]I think that you can create one user account, set things the way you want and then copy everything in that users home directory to /etc/skel/

Not sure about that, I've never tried  said:**
> http://www.ubuntuforums.org/showthread.php?t=67831&highlight=skel[/url]

Thanks, I thought about that,  but that has some complications.  
I checked out /etc/skel, and there is nothing aboutn gnome/firefox in there, yet Ubuntu did set a different theme from default Gnome...

---

### Post by Perfect Storm on 2005-12-30
What about making symblinks?

sudo ln -s /home/<username>/.themes /home/<to the other username>/.themes
sudo ln -s /home/<username>/.icons /home/<to the other username>/.icons
sudo ln -s /home/<username>/.fonts /home/<to the other username>/.fonts

---

### Post by khc on 2005-12-30
After a 2 minute investigation, it appears that you want to change

/etc/gconf/gconf.xml.defaults/apps/metacity/general/%gconf.xml so that the value for theme looks like your ~/.gconf/apps/metacity/general/%gconf.xml

I have no idea if this works or not, but it sounds correct.

---

### Post by nocturn on 2006-01-02
[QUOTE=khc]After a 2 minute investigation, it appears that you want to change

/etc/gconf/gconf.xml.defaults/apps/metacity/general/%gconf.xml so that the value for theme looks like your ~/.gconf/apps/metacity/general/%gconf.xml

I have no idea if this works or not, but it sounds correct.[/QUOTE]


Cool, thank you.

---

