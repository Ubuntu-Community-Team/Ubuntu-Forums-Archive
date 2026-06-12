---
title: "different GUI languages for different applications in UBUNTU"
date: 2011-08-13
forum: Desktop Environments
---

### Post by serge_o on 2011-08-13
Hello There, Ubuntians!

I am keen on learning foreign languages, so I occasionnaly install forein versions of applications to learn the language. for instance, under win7 English I had a french Skype and a german Firefox.

I moved to Ubuntu-Desktop a while ago (actually i had been working with linux servers for years now) . In Ubuntu-English all programs in App Manager are english as well (as it should be).

what is the simpliest way for me to install Firefox and, for example, OpenOffice in another language using Synaptec (I understand I can download and compile pretty much everything myself or download .debs - I just do not want go this way).
?

---

### Post by N1GHTS on 2011-08-13
You could always just go to the website for that product, find out how to do it, then do it.

*Example*:

[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)

---

### Post by serge_o on 2011-08-13
> **N1GHTS said:**
> You could always just go to the website for that product, find out how to do it, then do it.

*Example*:

[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)


Yes I could
And no I could not. Going this way I am loosing the ability to update my software with synaptec, aint I? because it is not an ubuntu package this way, its just simply a "linux program" on its own.

---

### Post by N1GHTS on 2011-08-13
If they have a **Debian** compatible package available for your target language, you could use **apt-build** to install it, which will register it with the system that **Synaptec** also uses for updates.

Here is more info on the subject: [http://chris.olstrom.com/howto/build-deb-packages-from-source/](http://chris.olstrom.com/howto/build-deb-packages-from-source/)

---

