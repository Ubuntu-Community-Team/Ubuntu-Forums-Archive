---
title: "Strange gui glitch when closing Opera"
date: 2011-12-10
forum: Desktop Environments
---

### Post by shayminfreak on 2011-12-10
Well, whenever I close Opera, the GUI flickers and changes to a past version. All of the icons for my files and folders change to a blank piece of paper. Every once in a while, only the icons change, but not the GUI. The change will be one of the two, it is random. I'm using the Unity shell. The only thing that really changes is the GUI, programs and folders run the same, albeit with a slightly different interface. It is a bit confusing and necessitates a restart every time it happens. Obviously, I don't want to leave Opera always open or always closed, so help would be very much appreciated. Please don't recommend that I change web browsers, and yes, I am using the latest version. Thanks in advance.

---

### Post by Frogs Hair on 2011-12-10
Hello and Welcome

I am using Opera with Unity and the Gnome shell no problem . Opera just updated to 11.60 on Tuesday  and I didn't notice any strange behavior . From your description Nautilus may be crashing which causes the theme to look like Win 95 and the icons appear as you described . You can restart Nautilus with the terminal command below , but other than reinstalling Opera I don't know what to suggest .```
nautilus -q
```

---

### Post by shayminfreak on 2011-12-11
@Frogs Hair
Thank you very much! That solution worked excellently. Now, all I have to do it type the command and open my home folder (restarting nautilus) and everything works perfectly again! Much faster than what I used to do.... Anyone else have any answers? I'd be cool with closing the topic, but if anyone else has a solution of their own, I'd be happy to hear it!

---

### Post by Frogs Hair on 2011-12-11
The command is a work around and the cause is still unknown . I am glad it is working for you . Opera's servers were having problems yesterday and last night I couldn't a load Google search . I found this out by using the portal page and everything is working fine today so far .

---

### Post by shayminfreak on 2011-12-11
@Frogs Hair
I couldn't connect either last night, but I don't believe that's the cause. It's been happening to me every time I shut Opera down.... I think I'll try a reinstall and see what happens.

---

### Post by Frogs Hair on 2011-12-11
The commands below may prevent the problem and are found at the link . ```
sudo apt-get remove nautilus-open-terminal

``` ```
nautilus -q
``` [http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

### Post by shayminfreak on 2011-12-11
Ah, that did it. Thank you!

---

### Post by Frogs Hair on 2011-12-11
Glad it's working !  :)

---

