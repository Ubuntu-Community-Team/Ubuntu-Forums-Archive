---
title: "gdm troubles / themed greeter disappeared"
date: 2006-07-03
forum: Desktop Environments
---

### Post by schambee on 2006-07-03
i'm having serious troubles with my gdm. suddenly the "themed greeter" option disappeared. i only can select "face browser".
any suggestions?
thanx

---

### Post by schambee on 2006-07-03
anyone?

---

### Post by HAARP on 2006-07-21
I've got the same problem. I can't change **Style**, because there's only one option there which is already selected! The other ones dissapeared.

[[IMG]http://img111.imageshack.us/img111/1111/screenshotloginwindowpreferencesvn2.th.png[/IMG]](http://img111.imageshack.us/my.php?image=screenshotloginwindowpreferencesvn2.png)

---

### Post by HAARP on 2006-07-22
Got the solution.
Open /etc/gdm/gdm.conf.custom and make it look like this:

```
#blah
#blah

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]
```

Logout. Switch to a console, log in and type:
```
sudo /etc/init.d/gdm restart
```
Now you can configure it again.

---

