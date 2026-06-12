---
title: "Epiphany fails to start"
date: 2005-12-18
forum: Desktop Environments
---

### Post by Omer on 2005-12-18
Epiphany fails to start ever since my fresh install of flight 2, and also after dist-upgrading tonight.
No terminal output available, except this text box:
```
Epiphany can't be used now. Mozilla initialisation failed.
```

---

### Post by spark on 2005-12-19
Run the following:

```
sudo rm /usr/lib/mozilla-firefox/components/compreg.dat
```

---

### Post by encho on 2005-12-19
That worked! But why did it happen? Hm... considering those 'firefox/epihany as default' discussions, I may even think that was a sabotaging of epiphany :razz:

---

### Post by Omer on 2005-12-19
[QUOTE=spark]Run the following:

```
sudo rm /usr/lib/mozilla-firefox/components/compreg.dat
```[/QUOTE]

Thanks!

really missed Epiphany's tags.

---

### Post by bluevoodoo1 on 2006-05-12
[QUOTE=spark]Run the following:

```
sudo rm /usr/lib/mozilla-firefox/components/compreg.dat
```[/QUOTE]


YES!!! Thank you!

---

### Post by madjo on 2006-05-31
for me it was /usr/lib/firefox/components/compreg.dat but after renaming it, epiphany worked once again :) (and I can once again do my e-banking)

---

