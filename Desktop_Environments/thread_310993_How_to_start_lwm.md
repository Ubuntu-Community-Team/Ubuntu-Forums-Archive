---
title: "How to start lwm?"
date: 2006-12-02
forum: Desktop Environments
---

### Post by lungan on 2006-12-02
How do i start lwm, it doesn't appear in the sessionslist, only the 4 first I installed shows upp there, i have ubuntu dapper with gnome orginal but now i use fluxbox

---

### Post by thomashauk on 2006-12-02
Fist you need to find the command to lauch lwm as a session, haveing never used it I don't know it but its probably just ```
lwm
```

Now open a terminal and cd to /usr/share/xsessions/

Open your favorate text editor using sudo and paste and fill in the blanks.

```

[Desktop Entry]
Encoding=UTF-8
Name= lwm #The Name of the session
Comment= #A comment
Exec= #the command to start it as a session
Icon= #An pic (optional)
Type=XSession

```

And save it as lwm.desktop

---

