---
title: "Need some help with konqueror servicemenus"
date: 2006-09-12
forum: Desktop Environments
---

### Post by qpieus on 2006-09-12
I'm trying to make a new servicemenu (right-click menu) that will verify files using par2. I made a .desktop file and placed it in the appropriate directory. I can see the newly made right click menu selection in konq. The problem is that par2 is a command line program and I cannot see it's output the way I currently have this structured. Here's what I have so far in the .desktop file:
```

[Desktop Entry]
Encoding=UTF-8
ServiceTypes=all/all
Actions=par2verify

[Desktop Action par2verify]
Name=par2 Verify
Exec=par2verify -v %f
Icon=kfm

```
What I need to do is somehow get the par2 output to be visible. I'm envisioning a terminal box opening up with the par2 output inside it, but I don't know how to do  that. An alternative would be to have the output go to a file and then have kate open the file.
I tried this in the .desktop file, but it did not work:
```

Exec=par2verify -v %f > /tmp/result; kate /tmp/result

```
I was attempting to put 2 commands in the Exec line, but that did not seem to work. Perhaps the syntax is wrong? Or can I not use 2 commands like this?

I read several documents on servicemenus, but none showed me exactly what I want to do.
Any help would be appreciated. Thanks!

---

### Post by qpieus on 2006-09-14
Figured it out.

Exec=konsole --noclose --nomenubar --notoolbar -e par2verify -v %f

Works perfectly, konsole box opens with the par2 output inside.

This servicemenu thing is cool. I was running quickpar (for windows) via wine, but no need to now.

---

### Post by pdxsam on 2007-03-31
Happened upon this little svc menu. 

Is there a way to have the box close  once you've done with the check?

I know little of scripting.

Thanks!

---

