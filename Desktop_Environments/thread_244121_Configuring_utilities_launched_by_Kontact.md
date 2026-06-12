---
title: "Configuring utilities launched by Kontact"
date: 2006-08-25
forum: Desktop Environments
---

### Post by ZooDirt on 2006-08-25
So, Kontact does everything that I need it to do. However, there is one last think that I'd like it to do.   

I'd like to use something different than amarok to play .wav files that I recieve as attachements.  (I recieve voicemail from Vonage if you're really interested).  When I right-click on the attachement and click on "Open With" I'm able to open the attachement with /usr/bin/xine just like I want, however, when I check the "Remember application association for this type of file" box it never seems to stick. The next time I click on the attachement it opens with amarok.  

Has anyone run into this yet?  I didn't see it in the forum...

---

### Post by ZooDirt on 2006-08-26
Nevermind, it wasn't an issue with kontact at all. Amarok is the default player for kubuntu. I still couldn't figure out how to change this though...

But I stopped being a pu$$y and did the following...

sudo mv /usr/bin/amarok /usr/bin/amarok.I_hate_amarok
sudo ln -s /usr/bin/xine amarok

...off to the races...

---

