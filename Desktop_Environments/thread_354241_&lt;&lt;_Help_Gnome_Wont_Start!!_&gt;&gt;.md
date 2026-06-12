---
title: "&lt;&lt; Help Gnome Wont Start!! &gt;&gt;"
date: 2007-02-05
forum: Desktop Environments
---

### Post by Opeth115 on 2007-02-05
Ok, well i was screwing around with compiz and xgl to see if i could get it up and running since beryl wouldn't work.  But now when i log out then back in, it just gives me an error message.  i couldnt' copy paste it obviously cuz it would only give me the error message tehn cut me out of my session so i tried to write it down.

basically it says that ur session has lasted less then 10 seconds if u did not log out your self something may be wrong...  the in details it says 

/home/matt/.Xsession: 2: XGL: Not Found
/home/matt/.Xsession: 4: Gnome Window Decorator: Not Found
/home/matt/.Xsession: 5: Compiz: Not Found

please somebody help me out of this im running in failsafe gnome right now.

---

### Post by shareMenaPeace on 2007-02-05
You can uninstall it with synaptic i guess.

Open a terminal and type 

> **synaptic**

than search for compiz and uninstall it. This should work try if you can login again. 
You than can reinstall compiz to see if it is ok but maybe you need to remove some folders aswell (as under beryl).

To check your home folder for any compiz folder (after runinstall went ok) 
Open your home folder and 
Then choose  View - > Show hidden files or use CTRL + H.


Today i had a similar problem with beryl and i had to manualy remove beryl folder in order to delete settings. So to get an idea here is what i did to fix this for beryl. 
[http://ubuntuforums.org/showthread.php?t=354228](http://ubuntuforums.org/showthread.php?t=354228)

And im welcoem to hear a feedback if there are better ways ...

---

