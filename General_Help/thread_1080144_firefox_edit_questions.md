---
title: "firefox edit questions"
date: 2009-02-25
forum: General Help
---

### Post by mdinh on 2009-02-25
i just installed ubuntu and i have some problems with firefox thats really annoying

1. i want to make it so that the first click on the address bar highlights everything like it does in windows

2. my backspace button does nothing in firefox and i want to make it work like normal

please give me detailed instructions on how to fix those problems

---

### Post by mcduck on 2009-02-25
1. type about:config in the address bar & press enter to get into Firefox's configurations. Then find the key called "browser.urlbar.clickSelectsAll" (typing "urlbar" as filter makes finding the key easy), right-click it and select "Toggle" to change it's value to "True".

2. What's "normal"? Do you mean backspace doesn't erase text in Firefox?

edit: I suppose you mean that backspace doesn't move you to previous page? In that case, go to about:config again, find "browser.backspace_action" and change it's value to "0".

---

### Post by mdinh on 2009-02-25
thanks alot u solved both my problems

the thing i dont get though is why ubuntu doesnt enable those functions in the first place just like if you were to use firefox on windows

i installed ubuntu years ago and had the exact same problems with firefox on a fresh install

---

### Post by simeon87 on 2009-02-25
> **mdinh said:**
> thanks alot u solved both my problems

the thing i dont get though is why ubuntu doesnt enable those functions in the first place just like if you were to use firefox on windows

i installed ubuntu years ago and had the exact same problems with firefox on a fresh install

It's personal preference I guess.. I'd find it annoying if Firefox forced selection of the whole address each time because I often edit parts of an URL manually. Also, double clicking selects the whole URL so it's not that far away..

---

### Post by oldos2er on 2009-02-25
F6 will highlight the address bar.

---

