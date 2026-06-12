---
title: "GNOME 3 extensions not installing (manual install)"
date: 2012-08-15
forum: Desktop Environments
---

### Post by andrew3 on 2012-08-15
Hi there,I'm trying to manually install some GNOME 3 extensions. I've downloaded the GNOME 3.0 Frippery extensions, extracted in a directory, and placed one of the extensions in ~/.local/share/gnome-shell/extensions.
In ~/.local/share/gnome-shell/extensions I have:```
user@pc:~/.local/share/gnome-shell/extensions$ ls
Shut_Down_Menu@rmy.pobox.com
```and ~/.local/share/gnome-shell/extensions/Shut_Down_Menu@rmy.pobox.com I have:```
user@pc:~/.local/share/gnome-shell/extensions/Shut_Down_Menu@rmy.pobox.com$ ls
extension.js  locale  metadata.json
```However, I do ALT+F2 > lg > Extensions tab and it says &quot;No extensions installed&quot;.
I have tried restarting the shell and my computer... any ideas?
Andrew.

---

### Post by markbl on 2012-08-15
Isn't it just much easier to add the extension directly from [https://extensions.gnome.org/extension/14/shut-down-menu/?](https://extensions.gnome.org/extension/14/shut-down-menu/?)

That site also automatically notifies you of updates each time you visit.

BTW, your problem may be that the name of the directory has to match the uuid in the metadata.json file.

---

### Post by andrew3 on 2012-08-15
> **markbl said:**
> Isn't it just much easier to add the extension directly from [https://extensions.gnome.org/extension/14/shut-down-menu/?](https://extensions.gnome.org/extension/14/shut-down-menu/?)
 
That site also automatically notifies you of updates each time you visit.
 
BTW, your problem may be that the name of the directory has to match the uuid in the metadata.json file.
 
Hi markbl, thanks for your response.
 
I just had a look in Looking Glass again, and in the Error tab it said I had an incorrect GNOME or GJS version. I will keep looking into it though...
 
Unfortunately I couldn't install extensions from their website. I get linked to this page: [https://extensions.gnome.org/about/#old-version](https://extensions.gnome.org/about/#old-version)
 
That is unusual, because I've installed extensions for GNOME 3.0 from that website in the past, but that error denies the possibility of being able to do that. Anyway, thanks for your help - I will look into it some more and see if I can get other extensions working.
 
Andrew.

---

### Post by andrew3 on 2012-08-15
OK, I've got it all working now. :) I used Firefox instead of Epiphany, and it worked.
 
I'm guessing that Epiphany didn't work because it was Epiphany 3.0.4. Turns out that I do have GNOME 3.2, not 3.0.
 
Thanks for your help Mark.
Andrew.

---

