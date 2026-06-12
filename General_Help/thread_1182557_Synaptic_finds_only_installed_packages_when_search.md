---
title: "Synaptic finds only installed packages when search"
date: 2009-06-09
forum: General Help
---

### Post by Seregwethrin on 2009-06-09
Hello;

I don't know why, synaptic says voer 26.000 packages listed but when I search I find only installed ones. But while I'm checking the sections like Editors I can see no installed ones too.

Is there some setting should I check?

---

### Post by Legace on 2009-06-09
Open Synaptic, select  Settings, select Filters, select **Search Filter** and click on the **Select All** button. Press OK and it should work.

---

### Post by Seregwethrin on 2009-06-09
Didn't solve :(

Please check the screenshot
[[IMG]http://img41.imageshack.us/img41/3193/screenshottot.th.png[/IMG]](http://img41.imageshack.us/img41/3193/screenshottot.png)

---

### Post by Legace on 2009-06-09
1) Close Synaptic
2) Open Terminal and type in:
```
sudo update-apt-xapian-index
```

It should work now..

---

### Post by Seregwethrin on 2009-06-09
Well, it did work but I didn't do anything :). Just fixed by itself :)

---

### Post by Legace on 2009-06-09
> **Seregwethrin said:**
> Well, it did work but I didn't do anything :). Just fixed by itself :)

Oh, well. Enjoy ;)

---

