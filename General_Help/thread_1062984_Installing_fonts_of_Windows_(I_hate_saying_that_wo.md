---
title: "Installing fonts of Windows (I hate saying that word)"
date: 2009-02-07
forum: General Help
---

### Post by DarkTxS on 2009-02-07
Hello everybody~

I searched and couldn't find any thread or tutorial that shows how I can put another fonts like Arial and Tahoma in Ubuntu 8.10.
If there is anything I didn't find, I would be thankful if you could give me the link, or just explain me how I can do so (:

Thanks.

---

### Post by cmnorton on 2009-02-07
Have a look.

[http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/)

---

### Post by GammaRay256 on 2009-02-07
Look up msttcorefonts in Synaptic

Or type this command in terminal:
```
sudo apt-get install msttcorefonts
```

Otherwise, if you still have Windows, you can copy all the fonts to the "~/.fonts" directory.  If you haven't used it before, you will need to create the folder ".fonts" in your home directory (keep in mind that the "." means it is hidden).

---

### Post by wstout on 2009-02-07
If I'm not mistaken, and I could be, but I think if you install the restricted extras, this will install those fonts along with things needed to play mp3's, flash , java and all that good stuff. ```
sudo apt-get install ubuntu-restricted-extras
``` If not i know that link above this post will get it for you but while your at it if you need the other stuff might as well get it too.

---

### Post by DarkTxS on 2009-02-07
I knew there was something!
Thank you! (:

---

### Post by chris.olive on 2009-02-08
Yes I have done that and have the M/S fonts instaled but does anyone know how to add other fonts to this folder.
When I try I get ' you are not the owner so you cannot add to this file' how then can I make myself the owner, which I am. Ubex 8.10

---

