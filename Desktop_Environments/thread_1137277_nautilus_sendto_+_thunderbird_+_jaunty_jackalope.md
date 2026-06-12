---
title: "nautilus sendto + thunderbird + jaunty jackalope"
date: 2009-04-25
forum: Desktop Environments
---

### Post by oliv66 on 2009-04-25
Hello,

I just migrated from Ubuntu 8.10 to Ubuntu 9.04 from scratch with no problem.

Under nautilus, I can use sendto function (right click) but not use the thunderbird client. Only Evolution is displayed. I removed evloution and chose Thunderbird in the Preferred applications Menu.

I used sudo gconf-editor to change the value under /desktop/gnome/urlhandlers/mailto/usr/bin/thunderbird %s

It doesn't work...

Any suggestion ?

Thanks in advance

Olivier

---

### Post by bradamante on 2009-05-01
> **oliv66 said:**
> Hello,

I just migrated from Ubuntu 8.10 to Ubuntu 9.04 from scratch with no problem.

Under nautilus, I can use sendto function (right click) but not use the thunderbird client. Only Evolution is displayed. I removed evloution and chose Thunderbird in the Preferred applications Menu.

I used sudo gconf-editor to change the value under /desktop/gnome/urlhandlers/mailto/usr/bin/thunderbird %s

It doesn't work...

Any suggestion ?

Thanks in advance

Olivier

Devi inserire /desktop/gnome/urlhandlers/mailto/usr/bin/mozilla-thunderbird %s
Impostandolo così a me funziona con la 9.04
Non so però come cambiare la voce di menù "Invia a Email (Evolution)"

---

### Post by cmschoonbee on 2009-05-08
I have/had the same problem - the Send To shows Email (Evolution) even though Thunderbird is my Gnome default email client.  

It did not occur to me to try to send the email anyway until I found the following bug report:
 [https://bugs.edge.launchpad.net/ubuntu/+source/nautilus-sendto/+bug/366410](https://bugs.edge.launchpad.net/ubuntu/+source/nautilus-sendto/+bug/366410)

It appears that the name 'Evolution' has been hardcoded or something into the GUI.  Just ignore it and send the file.

Your default email program will be opened to compose the message - Thunderbird in my case.

This bug will be fixed in the next Ubuntu release.

---

### Post by oliv66 on 2009-05-08
thanks for your reply.

I use nautilus-actions to bypass the problem.

It is a pity to have hard coded Evolution...

---

### Post by christopheccc on 2010-05-06
hi, you can do this :

[http://ubuntuforums.org/showpost.php?p=9251482&postcount=23](http://ubuntuforums.org/showpost.php?p=9251482&postcount=23)

---

### Post by oliv66 on 2010-05-09
many thanks Christopher,

---

