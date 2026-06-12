---
title: "thunderbird opens links in konquerer"
date: 2006-05-04
forum: Desktop Environments
---

### Post by Cirrocco on 2006-05-04
I've got this weird thing where clicking on html links in thunderbirds starts konquerer to open the url.

firefox is my default web browser, it is defined in my 'preferred apps' and all other html links open firefox.

I wouldn't care if konquerer wasn't so slow to open in gnome, but it's hatefully slow.  How can I change that?

---

### Post by jazzmuzik on 2006-05-04
Perhaps the system can't find Firefox and it's defaulting to Konqueror? Did you install Firefox in a non-standard place or via a deb file?

---

### Post by Cirrocco on 2006-05-04
i did reinstall FF using a .deb (to my knowledge, it wasn't a non-standard place)...but why would TB use konquerer instead of telling me it can't find FF?

---

### Post by jazzmuzik on 2006-05-04
Maybe something is not set quite right in Preferred Applications. What does your browser setting look like in pref. apps. And where does firefox, the binary, reside? ('whereis firefox') ?

I seem to have three versions of firefox on my system and didn't realize until now. The original 1.0.8 which I believe was upgraded from 1.0.7. I've got a version that Synaptic installed, 1.0.5.1. And then I've got 1.0.5.3 installed in my user directory.

---

### Post by FISHERMAN on 2006-05-10
-open thunderbird
-go to edit->preferences
-Chose Advanced-tab General and click on configuration editor
-You now should get an about:config for thunderbird
-go to 
**network.protocol-handler.app.http**
**network.protocol-handler.app.https**
-Enter the location of Firefox(because I updated it to Ff 1.5 mine is located at **/opt/firefox/firefox**, but if you still use Ff 1.0.8 from the repo's it will be in a differant locations).

---

