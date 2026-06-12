---
title: "Opera 9.0 - CSS problem?"
date: 2006-06-22
forum: Desktop Environments
---

### Post by Copter on 2006-06-22
Hi!

Ive just installed Opera 9.0. It works almost as fine as 8.5, but it cant handle wiki pages. Its looks like it doesnt recognise style sheets properly or something. Konqueror reads the same sites normally. What can be wrong here? Btw. using KDE (fresh Kubuntu Dapper install)

Posting screens.

thnx for help,
Copter :]

---

### Post by Copter on 2006-06-22
ive tried 3 different opera versions. none of them has fixed the problem. finaly i used this method:

[QUOTE=remusus]The way I did it was to extract the opera deb:

```
dpkg-deb --extract *opera deb here* operadeb
dpkg-deb --control *opera deb here* operadeb/DEBIAN
```

Edit operadeb/DEBIAN/control, and remove xlibs from the dependency list... then rebuild the deb.
```
dpkg-deb --build operadeb newopera.deb
```

Then install newopera.deb, and it works perfectly.[/QUOTE]

it looks ok now... it shouldnt be like this...

copter :]

---

### Post by Copter on 2006-08-23
[SIZE="4"][COLOR="Red"]**SOLVED**[/COLOR][/SIZE]

[http://my.opera.com/community/forums/topic.dml?id=144404]("http://my.opera.com/community/forums/topic.dml?id=144404")

> Originally posted by xargos:
Just purge scim-qtimm package and it should work correctly.
i knew it wasnt only MY problem...

---

