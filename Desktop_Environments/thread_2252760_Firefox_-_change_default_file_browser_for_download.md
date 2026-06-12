---
title: "Firefox - change default file browser for downloaded files kubuntu"
date: 2014-11-14
forum: Desktop Environments
---

### Post by maxpesa on 2014-11-14
Hi everybody, 
in ff, when I download something if I click the downloads button (the down arrow) a drop-down menu appears: if I click a downloaded file, ff opens it, if I click the little folder button "Open containing folder" it opens the directory using Gwenview, but I want it to use Dolphin, better as file browser.
How can I do this?

---

### Post by ajgreeny on 2014-11-14
This is an ongoing problem, I think.  I use xubuntu but had nautilus installed as well as thunar and I simply could not get FF to use thunar in this situation. Same problem as yours, just different applications.

I tried all I could find in the google search results at [https://www.google.co.uk/search?q=open+containing+folder+firefox&ie=UTF-8](https://www.google.co.uk/search?q=open+containing+folder+firefox&ie=UTF-8), particularly the answers at [http://askubuntu.com/questions/267514/open-containing-folder-in-firefox-does-not-use-my-default-file-manager](http://askubuntu.com/questions/267514/open-containing-folder-in-firefox-does-not-use-my-default-file-manager) but nothing worked.  I removed nautilus and thunar was then used, not surprisingly, but when I reinstalled nautilus it again took over this function and try as I might, I could not stop it.

As I now no longer need nautilus it has gone totally from my system and only thunar remains, but it was very annoying when it opened those folders by default.

Let us know if you succeed; I'll be very interested to know how you manage it

---

### Post by Rog131 on 2014-11-14
**Firefox from the Ubuntu repositories**

At here the FF seems to get the default file browser if I go to the KDE System Settings > File Associations > folder .

[IMG]http://i.imgur.com/EMoLz48.png[/IMG]

And shuffle the 'Application Preference Order' so that the 'Apply' button will be available. The 'Apply' will write the default application to the ~/.local/share/applications/mimeapps.list. It seems that the FF can read the default application from the local mimeapps.list.


**Firefox from the Mozilla**

The FF will ask the default application and later the default application can be set from the FF preferences.

[IMG]http://i.imgur.com/HJEqo52.png[/IMG]

---

### Post by maxpesa on 2014-11-14
Yeeee thank you! changing the file associations and swiching them back worked!

For you, fellow surfers, move up gwenview > apply > OK close application. do the same moving up dolphin. restart ff!

---

