---
title: "Message to GRUB:"
date: 2005-07-13
forum: Desktop Environments
---

### Post by Curlydave on 2005-07-13
Stop randomly deleting my Windows boot section from menu.list, thanks.

Does anyone else suffer from this issue?

---

### Post by Xian on 2005-07-13
Do you have the windows menu entry located below this line?
```
title		Other operating systems:
```

---

### Post by byen on 2005-07-13
well. I have a similar problem too.... but not as deadly as yours... i have Ubuntu and Xp and this is what my grub menu shows :
title Ubuntu, Custom built - Pro Edition (well..i edited this..yeah i know..kinda cheesy ) 
title Ubuntu, kernel 2.6.10-5-386 (recovery mode)
title Ubuntu, kernel memtest86+ 
Other operating systems:
Microsoft Windows XP
title Ubuntu, kernel 2.6.10-5-386 
title Ubuntu, kernel 2.6.10-5-386 (recovery mode)
title Ubuntu, kernel memtest86+ 
title Ubuntu, kernel 2.6.10-5-386 
title Ubuntu, kernel 2.6.10-5-386 (recovery mode)
title Ubuntu, kernel memtest86+ 

Initially it was ok.. but after I changed the Primary Title using "grubconf" this started happening. Nothing happens when i delete it but it somehow reappears again. Did you use "grubconf" as well? if so we might have hit something here....

Sorry this wasnt a solution... good luck!

---

### Post by Curlydave on 2005-07-13
Hmmm. No, it's not as that's on the bottom and I want WinXP on top so it boots by default. Would moving the whole section to the top fix this? Thanks.

---

