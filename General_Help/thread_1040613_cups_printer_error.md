---
title: "cups printer error"
date: 2009-01-15
forum: General Help
---

### Post by Wartender on 2009-01-15
recently i was aksed to install some updates concerning cups, and while installing them, i got this message that it wanted to replace a file, i hit yes because i thought it was going to upgrade it or something... but now i can't print anymore. i have lexmark z2320, and have installed drivers from the lexmark website, and it was working perfectly before this update. the error says "Printer (my printer): 'cups-missing-filter'" i don't know what to do, i tried reinstalling cups from synaptic but that didn't work, can someone help?

---

### Post by Wartender on 2009-01-15
anyone? hello? i really need this for school work!
and btw totally unrelated but where'd all the thanks things go? i was all proud cause lots of people had thanked me for helping them and now it's not there anymore :(

---

### Post by Wartender on 2009-01-16
nothing? come on i really need help with this!!

---

### Post by Wartender on 2009-01-16
ok... bumping for the last time, but please can SOMEbody help? nobody has ever had this problem before? come on i'm desperate here!!

---

### Post by Wartender on 2009-01-24
ok, i found out it's a permissions problem, by opening cups in firefox, it can't open usr/lexmark/etc/printdriver because it doesn't have permission. i tried changing the permissions to let it be accessed and edited by all users but it didn't work, it still says permission denied! can anyone help?

---

### Post by Wartender on 2009-01-25
nobody? come on please! i don't like bumbing this... i really need this fix can anyone suggest ANYthing?

---

### Post by Wartender on 2009-01-25
well i finally found the answer after googling a while, i ran the command 
sudo aa-complain cupsd
now it works, no thanks to everyone that helped! ;)

---

