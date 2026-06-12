---
title: "'Open Link in Browser' not working"
date: 2009-04-12
forum: General Help
---

### Post by mcpancakes on 2009-04-12
As the topic title states, since a couple days ago, the 'Open Link in Browser' item when you right-click a link mysteriously stopped working. Also, clicking the links is ineffective--I have to copy/paste them myself. I checked and made sure Firefox was still the default browser. Any suggestions as to why this is happening would be greatly appreciated.

---

### Post by _Purple_ on 2009-04-13
Please go to System > Preferences > Preferred Applications and check if Firefox is selected as your default Web Browser under Internet tab.

---

### Post by mcpancakes on 2009-04-14
> **_Purple_ said:**
> Please go to System > Preferences > Preferred Applications and check if Firefox is selected as your default Web Browser under Internet tab.

It is, yes.

---

### Post by dcstar on 2009-04-14
> **mcpancakes said:**
> As the topic title states, since a couple days ago, the 'Open Link in Browser' item when you right-click a link mysteriously stopped working. Also, clicking the links is ineffective--I have to copy/paste them myself. I checked and made sure Firefox was still the default browser. Any suggestions as to why this is happening would be greatly appreciated.

Maybe something is corrupted, close Firefox and rename the (hidden) .mozilla folder, start Firefox again and see it things are working.

---

### Post by mcpancakes on 2009-04-14
I closed Firefox, renamed ~/.mozilla to .mozilla1, ran Firefox. .mozilla was recreated. I tried clicking some links, but still the issue remains. Then I just deleted the new .mozilla and renamed .mozilla1 back to .mozilla.

---

### Post by mcpancakes on 2009-04-18
Fixed. See [this thread]("http://ubuntuforums.org/showthread.php?p=7056659") for what happened.

---

