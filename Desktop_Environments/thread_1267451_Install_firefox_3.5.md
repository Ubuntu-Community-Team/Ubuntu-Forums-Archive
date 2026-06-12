---
title: "Install firefox 3.5"
date: 2009-09-15
forum: Desktop Environments
---

### Post by Burillo on 2009-09-15
How do i install firefox 3.5 through repositories? i have a 3.5 package available but whenever i install it i end up having firefox 3.0. I tried purging and all that stuff. What can be done about that? Using 9.04

---

### Post by steveneddy on 2009-09-15
If you've already installed it, look under

Applications --> Internet --> Shiretoko

That is FF 3.5

Otherwise just do a Google search:

[http://www.google.com/search?hl=en&source=hp&q=install+firefox+3.5+ubuntu&aq=f&oq=&aqi=](http://www.google.com/search?hl=en&source=hp&q=install+firefox+3.5+ubuntu&aq=f&oq=&aqi=)

Google is your friend.

I'll also bet that there are over 100 threads on these forums asking the same question.

---

### Post by Burillo on 2009-09-15
> **steveneddy said:**
> If you've already installed it, look under

Applications --> Internet --> Shiretoko

That is FF 3.5

Otherwise just do a Google search:

[http://www.google.com/search?hl=en&source=hp&q=install+firefox+3.5+ubuntu&aq=f&oq=&aqi=](http://www.google.com/search?hl=en&source=hp&q=install+firefox+3.5+ubuntu&aq=f&oq=&aqi=)

Google is your friend.

I'll also bet that there are over 100 threads on these forums asking the same question.

i wonder why are they asking it in the first place... since if i choose to install 3.5 - i expect apt to install 3.5 not 3.0... anyway, i found a useful tool called ubuntuzilla, it solved my "problem"... the fact i am using a modern distro and have to google how to install the most common software one can imagine makes me nervous about future of Linux...

oh and by the way - why the hell is it Shiretoko? isn't 3.5 final already?

---

### Post by steveneddy on 2009-09-15
> **Burillo said:**
> i wonder why are they asking it in the first place... since if i choose to install 3.5 - i expect apt to install 3.5 not 3.0... anyway, i found a useful tool called ubuntuzilla, it solved my "problem"... the fact i am using a modern distro and have to google how to install the most common software one can imagine makes me nervous about future of Linux...

[COLOR=Blue]**oh and by the way - why the hell is it Shiretoko?**[/COLOR] isn't 3.5 final already?

Ubuntuzilla, huh? OK - your choice.

You're gonna have to ask the Mozilla guys about that.

Um - you know about Synaptic Package Manager don't you?

System --> Administrator --> Synaptic Package Manager

This is the graphical front end to apt.

You can look through all of the software that is not only installed but that is available for you to download.

Enjoy.

---

### Post by mdlueck on 2009-09-15
> **Burillo said:**
> anyway, i found a useful tool called ubuntuzilla, it solved my "problem"...

Here here! UbuntuZilla is great! And the author / developer is very responsive.

Mozilla produces official binaries for Windows, and Linux as well.

Using UbuntuZilla, you install the official Mozilla binaries into your version of Ubuntu.

---

### Post by Burillo on 2009-09-16
> **steveneddy said:**
> Ubuntuzilla, huh? OK - your choice.

You're gonna have to ask the Mozilla guys about that.

Um - you know about Synaptic Package Manager don't you?

System --> Administrator --> Synaptic Package Manager

This is the graphical front end to apt.

You can look through all of the software that is not only installed but that is available for you to download.

Enjoy.

when i said apt i meant the apt itself - didn't mean i don't use synaptic.

anyway, looks like i finally understood the problem in its entirety.

When i install firefox 3.5 it installs 3.0 AND 3.5 (Shiretoko). I can understand why this is happening. What i fail to understand, however, is the point of it - i want firefox 3.5 and i get firefox 3.0 + shiretoko. brilliant! this leads to confusion as when i press firefox icon i expect it to launch my new firefox 3.5 - and turns out i am supposed to know that i should run shiretoko instead. Why 3.0 gets installed in the first place? And no, this is the logical problem in ubuntu repos - i have to ask ubuntu about that, not mozilla. Mozilla gave me official Firefox 3.5 binaries, it's ubuntu who installs shiretoko.

---

### Post by gradinaruvasile on 2009-09-16
> **Burillo said:**
> How do i install firefox 3.5 through repositories? i have a 3.5 package available but whenever i install it i end up having firefox 3.0. I tried purging and all that stuff. What can be done about that? Using 9.04

Just download the latest version (its an archived generic linux version) from the mozilla site, unpack it wherewer u want, launch the firefox executable from that folder....

---

### Post by Burillo on 2009-09-16
> **gradinaruvasile said:**
> Just download the latest version (its an archived generic linux version) from the mozilla site, unpack it wherewer u want, launch the firefox executable from that folder....

i know i can use mozilla's official binaries, but i wanted to do it "the right way" - that is, through repositories.

---

### Post by HTML-insane on 2009-09-16
I wouldn't mind this situation so much, if Facebook and Google Docs actually recognized Shiretoko as Firefox (the FB AJAX instant messaging doesn't work in Shiretoko and Google complains that my browser doesn't support Gears). I can't believe I have more success using Konqueror with browser identification set to Firefox then I do actually using Firefox!

---

### Post by Burillo on 2009-09-16
couldn't care less about facebook but Google Gears seem to work fine under "normal" (non-ubuntu-repo) firefox 3.5. i would advice you to try ubuntuzilla.

btw, if i got it right - some of you are less than happy with ubuntuzilla. that raises the question - why FOSS people keep hating software that works and praise one that doesn't?

---

