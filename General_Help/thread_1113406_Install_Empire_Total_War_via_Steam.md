---
title: "Install Empire Total War via Steam"
date: 2009-04-01
forum: General Help
---

### Post by actarus000 on 2009-04-01
Has anyone tried this?
I installed Steam thru Wine with no problems. When I click on "Install Demo", nothing happens.

Has anyone had any luck ?

---

### Post by 3Miro on 2009-04-01
Have you tried at the winehq forums. [http://www.winehq.org/](http://www.winehq.org/)


You may also want to look at Crossover, it is a commercial add-on on wine that officially supports many steam games. 
[http://www.codeweavers.com/products/cxgames/download_trial/](http://www.codeweavers.com/products/cxgames/download_trial/)

Also, there is a rumor that steam is working on a native Linux client.

---

### Post by 3Miro on 2009-04-01
I have also found this.

[http://developer.valvesoftware.com/wiki/Steam_under_Linux](http://developer.valvesoftware.com/wiki/Steam_under_Linux)

---

### Post by atorch on 2009-07-23
I have the exact same problem, maybe I'll attach a screenshot to help make clear what's going on..

---

### Post by atorch on 2009-08-17
See attachments -- most Steam buttons work, but not the Install Demo button (pictured in attachment).  I click on it and nothing happens.  But all the navigation buttons that get me to screenshot (ie search for the game, click on its name, click on official demo) -- all of those work.

Steam's Home page under Store does say You will need to install the latest flash plugin to view this page properly.  The install button is a link, but clicking on it does nothing.

---

### Post by solnyshok on 2009-10-26
to install demos with steam under wine use

cd ~/.wine/drive_c/Program\ Files/Steam
wine Steam.exe -applaunch XXXX

where XXXX is a code of the game you want, can be seen in the url of the game (for that you need to open store.steampowered.com in the browser in linux)

---

