---
title: "Kate not working??"
date: 2005-10-13
forum: Desktop Environments
---

### Post by SilverTab on 2005-10-13
when I open kate from the menu, nothing happens, from the console, I get this:
kate: ERROR: Communication problem with kate, it probably crashed.


anyone with the same problem?

---

### Post by SilverTab on 2005-10-13
Note: I'm on a fresh Kubunty Breezy install

---

### Post by mlomker on 2005-10-13
Try running it from a Konsole prompt, both to see if it will run as root and because it'll often provide better error information.

```

kdesu kate

```

---

### Post by SilverTab on 2005-10-13
works fine when I run it with kdesu.....

however...I cant run it from the KDE Menu, nor from the console without using kdesu...is this normal??

---

### Post by escobar on 2005-10-13
Yea it is apprarently normal. I stated this same question in another thread. Bottom line is Kate doesn't respond too well to 'sudo' even though other apps do just fine. Doesn't bother me, just remeber to use 'kdesu' instead. Or, scrap Kate altogether and use Kwrite. You can launch that from terminal, it does not appear in the K menu. Hope that helps.

---

