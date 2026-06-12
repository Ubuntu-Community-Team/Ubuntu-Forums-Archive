---
title: "gdeskcal problem"
date: 2006-03-21
forum: Desktop Environments
---

### Post by mtweldon on 2006-03-21
I got it installed no problem, I can type gdeskcal in the terminal and the calendar comes up, but if i close the terminal it closes the calendar.  How can I make the calendar stay up without having the terminal open ?

---

### Post by engla on 2006-03-21
some tricks:
You can start it with the run dialog. Type **alt+F2** to bring it up, type **gdeskcal** and start it.. now the app will run the entire session.

If you want to start it in the terminal, by default all "children" processes of the terminal are killed when it closes. You can change this by using **nohup**

```
nohup gdeskcal >& /dev/null
```

That last part is to send the output to /dev/null, to *nowhere*, as otherwise a file would be created in your home directory to keep track of that.. and we are not interested.

---

### Post by mtweldon on 2006-03-21
Great, thanks for the quick reply, it worked perfectly.  Is it possible to get this to boot up if I log out with save this current set up checked?

---

### Post by engla on 2006-03-21
[QUOTE=mtweldon]Great, thanks for the quick reply, it worked perfectly.  Is it possible to get this to boot up if I log out with save this current set up checked?[/QUOTE]
I don't know, but it's very possible that it will be saved. If not, go to the menu System > Settings > Sessions and add this applications in the last tab.

---

### Post by mtweldon on 2006-03-21
Well the save current settings did not work, but I put nohup gdeskcal >& /dev/null into the session start up and that worked perfectly.  Thanks again for the quick help.

---

### Post by taurus on 2006-03-21
[QUOTE=mtweldon]Great, thanks for the quick reply, it worked perfectly.  Is it possible to get this to boot up if I log out with save this current set up checked?[/QUOTE]
System -> Preferences -> Sessions -> Startup Programs -> Add.  Then type in gdeskcal at the field and click Close.  Log out and back in again and you will see gdeskcal pops up where you have it run last...  \\:D/

---

