---
title: "Realplayer"
date: 2005-10-20
forum: Desktop Environments
---

### Post by seismicmike on 2005-10-20
So... I downloaded the rpm of Realplayer

supposed to be really nice

except.. it doesn't work...

i did:

sudo -s
alien [reallylongfilename].rpm
alien dpkg -i [reallylongfilename].deb

now... 

where do I go to run the file I just installed? :confused:

---

### Post by TristanMike on 2005-10-21
Hi. You could try "real" or "realplayer" or something similar in a terminal or check the "/usr" directory, probably "/usr/bin" but it could be somewhere in there, or just do a search for real.

There was a simpler solution, all you need do is go to [here](http://www.real.com/realcom/R?href=http%3A%2F%2Fforms.real.com%2Freal%2Fplayer%2Fdownload.html%3Ff%3Dunix%2FRealPlayer10GOLD.bin%26product%3Dplayerplus%26system%3Dlinux%26pcode%3Drn%26src%3Drealhome_linux_0_1_1_0_0_3_0%26opage%3Drealhome_linux&pageid=unagi.8083677&pageregion=offer_button) and download this file. Then a simple ```
chmod a+x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin
```And you shouldn't have a problem. I believe this method also adds a link in the Applications menu.

Hope this helps.

---

### Post by seismicmike on 2005-10-21
hmm... i may try that

---

