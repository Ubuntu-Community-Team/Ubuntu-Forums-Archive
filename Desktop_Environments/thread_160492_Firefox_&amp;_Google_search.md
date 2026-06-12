---
title: "Firefox &amp; Google search"
date: 2006-04-15
forum: Desktop Environments
---

### Post by Bob Gould on 2006-04-15
I would like to know how to remove the Google search from the Firefox toolbar. I can't find anyway of doing it in the Firefox preferences. Is there a Firefox version without Google or would I have to use an alternative browser.

---

### Post by neoflight on 2006-04-15
[QUOTE=Bob Gould]I would like to know how to remove the Google search from the Firefox toolbar. I can't find anyway of doing it in the Firefox preferences. Is there a Firefox version without Google or would I have to use an alternative browser.[/QUOTE]


right click on the ff tool menu bar somewhere... and chose customize.... then crag the  google toobar and drop into the customize toolbar....thats it.....u can put it back by the same way.....

:mrgreen:

---

### Post by aysiu on 2006-04-15
First, close Firefox.

Then go to Applications > Accessories > Terminal.

The bold stuff is what you should type: ```
user@ubuntu:~$ **sudo updatedb**
Password:
user@ubuntu:~$ **locate google.src**
/usr/share/firefox/searchplugins/google.src
/usr/lib/mozilla/searchplugins/google.src
/usr/local/bin/firefox/searchplugins/google.src
user@ubuntu:~$**sudo rm /usr/share/firefox/searchplugins/google.src**
user@ubuntu:~$**sudo rm /usr/lib/mozilla/searchplugins/google.src**
user@ubuntu:~$**sudo rm /usr/local/bin/firefox/searchplugins/google.src**
user@ubuntu:~$**sudo rm /usr/share/firefox/searchplugins/google.gif**
user@ubuntu:~$**sudo rm /usr/lib/mozilla/searchplugins/google.gif**
user@ubuntu:~$**sudo rm /usr/local/bin/firefox/searchplugins/google.gif**
``` Of course, I have one in /usr/local/bin, but yours might be somewhere else--adapt as appropriate.

---

### Post by Bob Gould on 2006-04-15
[QUOTE=neoflight]right click on the ff tool menu bar somewhere... and chose customize.... then crag the  google toobar and drop into the customize toolbar....thats it.....u can put it back by the same way.....

:mrgreen:[/QUOTE]

I tried that first & there is nothing about Google under the Customisation menu. I think aysiu may have a better solution.

---

### Post by Bob Gould on 2006-04-15
[QUOTE=aysiu]First, close Firefox.

Then go to Applications > Accessories > Terminal.

The bold stuff is what you should type: ```
user@ubuntu:~$ **sudo updatedb**
Password:
user@ubuntu:~$ **locate google.src**
/usr/share/firefox/searchplugins/google.src
/usr/lib/mozilla/searchplugins/google.src
/usr/local/bin/firefox/searchplugins/google.src
user@ubuntu:~$**sudo rm /usr/share/firefox/searchplugins/google.src**
user@ubuntu:~$**sudo rm /usr/lib/mozilla/searchplugins/google.src**
user@ubuntu:~$**sudo rm /usr/local/bin/firefox/searchplugins/google.src**
user@ubuntu:~$**sudo rm /usr/share/firefox/searchplugins/google.gif**
user@ubuntu:~$**sudo rm /usr/lib/mozilla/searchplugins/google.gif**
user@ubuntu:~$**sudo rm /usr/local/bin/firefox/searchplugins/google.gif**
``` Of course, I have one in /usr/local/bin, but yours might be somewhere else--adapt as appropriate.[/QUOTE]

Ok this looks like what I need to know.
Thank you very much.

---

### Post by aysiu on 2006-04-15
neoflight may not have understood what you were asking. The customize menu solution removes not only Google, but also the entire search box.

---

### Post by Bob Gould on 2006-04-15
[QUOTE=aysiu]neoflight may not have understood what you were asking. The customize menu solution removes not only Google, but also the entire search box.[/QUOTE]

Actually that's what I want to do. Remove the entire search box. In the version of Firefox I have it is not listed as an option under the customise menu.  I have all the options for changing the icons & text on the toolbars & adding & removing bars but nothing about the search box.

---

### Post by Bob Gould on 2006-04-15
[QUOTE=Bob Gould]I tried that first & there is nothing about Google under the Customisation menu. I think aysiu may have a better solution.[/QUOTE]

Sorry I didn't understand what you meant. It was too easy! I was looking for a more complicated way to do it.

Thanks to both you that replied.

---

