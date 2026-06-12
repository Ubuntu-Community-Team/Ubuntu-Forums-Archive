---
title: "no network activity icon"
date: 2009-03-30
forum: General Help
---

### Post by rudi009 on 2009-03-30
my network activity icon disappeared suddenly yesterday and now i'm not able to connect to any network. in the add to panal options also the network icon is not there .help...

---

### Post by |Porsche on 2009-03-30
Are you talking about the network icon that is on the Notify area? If so go to panel, add to panel, type notification ( i think its called notification area) and add it.

---

### Post by rudi009 on 2009-03-30
i tried that but notification icon is not same which appears by default.

---

### Post by ispy on 2009-03-30
Open up a terminal and copy/paste 

```
nm-applet
```

Should start it.

If that doesn't work try this:

```
sudo killall nm-applet
```

followed by this:

```
nm-applet
```

---

### Post by rudi009 on 2009-03-30
command not found .
try sudio apt-get install.

---

