---
title: "OpenOffice problem an '&amp;' in links"
date: 2005-12-07
forum: General Help
---

### Post by guice on 2005-12-07
It would appear that OpenOffice isn't correctly passing a URL to Konqueror when the link contains an '&' within it. How can I fix this? Is this fixable within the document or at the application level?

---

### Post by rwabel on 2005-12-10
for me oo2 under dapper cannot open files with spaces in the name. don't know if that's also the same problem

---

### Post by guice on 2005-12-10
Spaces in the name is no problem for me. Spaces in the URL could be a problem. A space should be coded to %20 in URLs.

---

### Post by rwabel on 2005-12-10
[quote=guice]Spaces in the name is no problem for me. Spaces in the URL could be a problem. A space should be coded to %20 in URLs.[/quote]

for me even such files doesn't work in dapper using oo2!

---

### Post by GoldBuggie on 2005-12-11
Which KDE version do you use?

What is the output of
```
cat /usr/share/applications/ooo2-writer.desktop | grep Exec
``` ?

Should be *Exec=ooffice2 -writer %f* if you are using KDE 3.5. Try changing it if you have a lower version as well.

If it is a %U or %u change it with
```
sudo sed -e 's/%[Uu]/%f/' -i /usr/share/applications/ooo2-writer.desktop
```

---

