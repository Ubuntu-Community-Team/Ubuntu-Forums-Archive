---
title: "Click and select in Firefox"
date: 2005-12-25
forum: General Help
---

### Post by zeeone on 2005-12-25
In WinXP when I click the URL bar in Firefox and Opera it automatically selects it allowing me to type over. That does not happen in Linux. How can I make it happen?

---

### Post by Zio84 on 2005-12-25
Doubleclick, and it will be selected.

---

### Post by 23meg on 2005-12-25
Type about:config in the address bar and change the value of the "browser.urlbar.clickSelectsAll" key to "true". The reason this default is different in the Linux version is that selecting any piece of text automatically copies it to clipboard in X (you can paste the text you copy by selecting with the middle button).

---

### Post by zeeone on 2005-12-25
Thanks 23meg! That did it.

---

