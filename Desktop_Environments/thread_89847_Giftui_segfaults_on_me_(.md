---
title: "Giftui segfaults on me :("
date: 2005-11-13
forum: Desktop Environments
---

### Post by madjo on 2005-11-13
Hi everyone, 

I tried to start giftui in Breezy, but somehow upon starting it gives a segmentation fault.

```
$ giftui
Segmentation fault
```


I found this thread in the dev-discussion:
[http://ubuntuforums.org/showthread.php?t=65618&highlight=giftui+segmentation](http://ubuntuforums.org/showthread.php?t=65618&highlight=giftui+segmentation)

could someone help me on this? 

Oh and btw, giFToxic does work, but I don't quite like the UI of it. :)

---

### Post by madjo on 2005-11-14
*bump*

---

### Post by arnieboy on 2005-11-14
[QUOTE=madjo]*bump*[/QUOTE]
please give the details of how u installed giftui

---

### Post by tagbre on 2005-11-14
[QUOTE=madjo]Hi everyone, 

I tried to start giftui in Breezy, but somehow upon starting it gives a segmentation fault.

```
$ giftui
Segmentation fault
```


I found this thread in the dev-discussion:
[http://ubuntuforums.org/showthread.php?t=65618&highlight=giftui+segmentation](http://ubuntuforums.org/showthread.php?t=65618&highlight=giftui+segmentation)

could someone help me on this? 

Oh and btw, giFToxic does work, but I don't quite like the UI of it. :)[/QUOTE]


Yep, that's my thread! I filed a bug long ago:
[https://launchpad.net/distros/ubuntu/+source/giftui/+bug/2451]("https://launchpad.net/distros/ubuntu/+source/giftui/+bug/2451")

Anyway, in the meantime I partially solved it by installing a debian package I found in some debian mirror, don't remember where now. The problem is that I have the update-manager permanently in my tray, wanting to "update" to the ubuntu package, but at least giFTui is working fine now.

---

### Post by madjo on 2005-11-15
[QUOTE=arnieboy]please give the details of how u installed giftui[/QUOTE]
I got it from the repositories. ("sudo apt-get install giftui", but I gather that you already know that) :)

giftd itself does work well, it is just that particular client that doesn't want to start.

[quote=tagbre]Anyway, in the meantime I partially solved it by installing a debian package I found in some debian mirror, don't remember where now. The problem is that I have the update-manager permanently in my tray, wanting to "update" to the ubuntu package, but at least giFTui is working fine now.[/quote]
You don't happen to know where you found it, right?

I will try a google search to see if something comes up. :)

---

### Post by Vinze on 2006-03-11
I have the same problem, installed it with Synaptic and it never worked, have done a few fresh install since I first tried, and everytime I installed giftUI and got the same error... I guess it's an error with the package.

---

