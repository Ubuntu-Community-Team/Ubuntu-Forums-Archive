---
title: "qt_temp files"
date: 2009-05-21
forum: General Help
---

### Post by nutu on 2009-05-21
hello,

i was just wondering if there is a way to disable qt_temp files from creating themselves? everytime i write a text file or edit one then i find several qt_temp files are created in the directory i am working in. now, i am all about backup but i do not like the idea of having these files flood my directory and make it hard for me to look for things. if it helps, i am using kwrite as a text editor.

so, are qt_temp files normal? do they delete themselves or should i disable them?

thanks in advance.

---

### Post by nutu on 2009-05-21
or are the qt_temp files simply a byproduct of the kwrite text editor, and perhaps can be somehow disabled?

---

### Post by mcduck on 2009-05-21
Sounds a lot like those files are created by the text editor you are using. You should check it's settings, there must be an option for disabling backup files.

---

### Post by nutu on 2009-05-21
the problem is that if i go to:

Settings --> Configure Editor --> ...

(which seems to be the only place to play with the settings for kwrite)

and then go to: 

... --> Open/Save

there are no settings that really mention anything about the qt_temp files. there is a place to backup saved files (default ending with '~') but this is something else and i have disabled this anyways.

any more suggestions?

---

### Post by Andtsk on 2010-01-05
settings -> configure kate -> Open\Save -> Advanced
and uncheck in the "Backup on save" a "Local files" box.
Worked for me.

---

