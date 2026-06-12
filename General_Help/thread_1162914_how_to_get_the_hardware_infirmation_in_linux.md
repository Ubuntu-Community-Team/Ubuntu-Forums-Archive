---
title: "how to get the hardware infirmation in linux"
date: 2009-05-18
forum: General Help
---

### Post by suresh_vandiyur on 2009-05-18
i need the my system hardware information. which command i will get the information.. plz help me..

---

### Post by geirha on 2009-05-18
Try ```
sudo lshw
# It gives a lot of output, so you might want to store it in a file
sudo lshw > hardwarelist.txt
```

There's also a graphical version which you install with the package [lshw-gtk](apt:lshw-gtk)

---

### Post by danwood76 on 2009-05-18
you can also output the lshw to html to view in a web browser:
```

lshw -html > hwinfo.html

```

---

### Post by suresh_vandiyur on 2009-05-18
> **danwood76 said:**
> you can also output the lshw to html to view in a web browser:
```

lshw -html > hwinfo.html

```
Thank u so Much..

---

