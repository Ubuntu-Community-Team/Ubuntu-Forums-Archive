---
title: "Changin locale in particular way.."
date: 2009-04-01
forum: General Help
---

### Post by James- on 2009-04-01
I know that the local is handled by:

*/etc/default/locale*

what I am trying to do is change the time local to japanese
by adding: 
LC_TIME=[JAPANESE LOCALE CODE HERE]

to the locale folder
I was wondering what the local code was..

---

### Post by James- on 2009-04-01
found out how
edited:
*/var/lib/locales/supported.d/local*
added ja_JP.UTF-8 UTF-8

then 
*/etc/environment*
added: LC_TIME="ja_JP.UTF-8

ran:
sudo dpkg-reconfigure locales
and rebooted

all this after installing the JP language pack with the language manager(System->Administration->Languge Support)

Now I have the O/S in english but times and dates in Japanese ^_^;

---

