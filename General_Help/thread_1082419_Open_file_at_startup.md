---
title: "Open file at startup"
date: 2009-02-27
forum: General Help
---

### Post by Alex2610 on 2009-02-27
Hello.

There's a (jar) file that I have to open every time I use my computer.

Is there any script or something similar that I can use in order to open this file with Sun Java 6 Runtime at startup?

Keep in mind that I know nothing about scripts :P


Thanks.-

---

### Post by jonobr on 2009-02-27
How do you start this program as it stands?

Let me give firefox as an example of a program to start at boot time.


To start the firefox normally I can click an icon or , in a terminal i can just type firefox,
To autostart this, I put the command into a new file,
Put it in my home dir or desktop and enter the start command in there
The file will contain
```
firefox &
```

I save the file and then go to system-> prefs->sessions

in startup programs tab click add.

Give it a name,
broswe to your file,
Hopefully that will work for your java program also

I do this manually in my start scripts, but I think this is the easier graphical way. There may be another way, but this should work

---

### Post by issih on 2009-02-27
I think that adding the following command to your session (look under System->Preferenes) should do what you want:

```
java -jar jarname
```

Where jarname is the jar file you want to run.

Hope that helps

---

### Post by Alex2610 on 2009-02-27
Oh, ok, that solves my problem.

Many thanks.

---

