---
title: "Uninstalling software not present in Synaptic"
date: 2009-05-22
forum: General Help
---

### Post by Lockheed on 2009-05-22
I have installed this Tucan download manager but now I want to remove it. I cannot find it in synaptic so how do I get rid of it?

---

### Post by _Purple_ on 2009-05-22
How did you install it?

---

### Post by fballem on 2009-05-22
Also, what version of ubuntu are you running?

---

### Post by Lockheed on 2009-05-22
U9.04. I think I downladed a deb file from Tucan's website and installed it.

---

### Post by chriskin on 2009-05-22
> **Lockheed said:**
> U9.04. I think I downladed a deb file from Tucan's website and installed it.

.debs are supposed to be found in synaptic. are you by any chance at add/remove by mistake? only synaptic can find them

---

### Post by fballem on 2009-05-22
> **Lockheed said:**
> U9.04. I think I downladed a deb file from Tucan's website and installed it.

If you select System > Administration > Computer Janitor, you should get a panel similar to the attached screenshot.

Included in this list are applications that you installed from debs. Make sure that you clear the checkmarks from all packages, then select the Tucan application. Once selected, then select the Cleanup button and that should remove the application.

Hope this helps,

---

### Post by chriskin on 2009-05-22
damn i didn't even think of it
good idea :)


edit : _**where did you get the fluendo package? :) **_

---

### Post by fballem on 2009-05-22
> **chriskin said:**
> damn i didn't even think of it
good idea :)


edit : _**where did you get the fluendo package? :) **_

I subscribed to it - if I remember correctly it was about 29 euros, and the annual renewal is about 9 euro. It allows me to play Windows media lossless (my CD collection) and is an excellent package. One of the few things that I pay for (and am pleased to pay for) in a linux environment. Link is at: [http://www.fluendo.com](http://www.fluendo.com)

Hope this helps,

---

### Post by chriskin on 2009-05-22
> **fballem said:**
> I subscribed to it - if I remember correctly it was about 29 euros, and the annual renewal is about 9 euro. It allows me to play Windows media lossless (my CD collection) and is an excellent package. One of the few things that I pay for (and am pleased to pay for) in a linux environment. Link is at: [http://www.fluendo.com](http://www.fluendo.com)

Hope this helps,

hope i had 29 euros to spare for listening to wma files i do not have :P

i guess i will stay without experimenting with new fancy stuff until i can get them :|

---

### Post by fballem on 2009-05-22
> **chriskin said:**
> hope i had 29 euros to spare for listening to wma files i do not have :P

i guess i will stay without experimenting with new fancy stuff until i can get them :|

In my case, I had the need, so I spent the money. I think there are also some DVD formats that can be played with fluendo that can't be played with free stuff. If you don't have the need, then don't spend the money.

---

### Post by chriskin on 2009-05-22
> **fballem said:**
> In my case, I had the need, so I spent the money. I think there are also some DVD formats that can be played with fluendo that can't be played with free stuff. If you don't have the need, then don't spend the money.

is their dvd player present in the package as well?

---

### Post by fballem on 2009-05-22
> **chriskin said:**
> is their dvd player present in the package as well?

Codecs only - I don't think their DVD player is ready yet. I don't know when it's ready if it will be included in the package.

I'm also thinking that we've gone somewhat off topic.

---

### Post by chriskin on 2009-05-22
> **fballem said:**
> Codecs only - I don't think their DVD player is ready yet. I don't know when it's ready if it will be included in the package.

I'm also thinking that we've gone somewhat off topic.

yeah and i got offtopic on another thread :P

the op hasn't answer yet eh? anyway. it most probably worked

well, i stop being offtopic, so bb :)
and thanks for the info :) :)

---

### Post by Lockheed on 2009-05-22
Oh no. I was mistaken. I installed it from tar.gz archive.

---

### Post by chriskin on 2009-05-22
> **Lockheed said:**
> Oh no. I was mistaken. I installed it from tar.gz archive.

oh , then you have to find the instructions given by the one who made it, usually there is a "uninstall" named text file in the tar

---

### Post by Lockheed on 2009-05-22
I checked and there is no such file or any notes about deinstallation in any of the text files within the archive.

---

### Post by chriskin on 2009-05-22
> **Lockheed said:**
> I checked and there is no such file or any notes about deinstallation in any of the text files within the archive.

i would contact the one who made it, the ways to uninstall apps from tars seem to be just as many as the ways to install them via the same route.

---

### Post by bacardiandwatermelon on 2009-05-22
In the readme file it says to run..

```
sudo make uninstall
```

---

### Post by chriskin on 2009-05-22
> **bacardiandwatermelon said:**
> In the readme file it says to run..

```
sudo make uninstall
```

by doing so,after you have cd-ed to the folder that comes when you extract the tar.gz, the package will disappear :) 

--so there were notes of deinstallation :)

---

### Post by Lockheed on 2009-05-24
Thanks everyone. It seems I had some incomplete package on my hands.

---

