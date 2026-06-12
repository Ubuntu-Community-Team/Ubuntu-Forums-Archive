---
title: "evolution hangs"
date: 2006-06-12
forum: Desktop Environments
---

### Post by bbarrons on 2006-06-12
evloution started hanging about a month ago whenever I try to reply to sender. It will take about 3 minutes before the reply email opens up. Has anyone else run into this problem? If so have you found a way to fix it?
thanks
Bill B

---

### Post by henriquemaia on 2006-06-12
[quote=bbarrons]evloution started hanging about a month ago whenever I try to reply to sender. It will take about 3 minutes before the reply email opens up. Has anyone else run into this problem? If so have you found a way to fix it?
thanks
Bill B[/quote] 
I don't have this problem, but you can try this:

[http://ubuntuforums.org/showthread.php?t=167862&highlight=evolution+kmail]("http://ubuntuforums.org/showthread.php?t=167862&highlight=evolution+kmail")

If this doesn't help, try this: **backup your ~/.evolution** folder and removing it afterwards. Restart evolution (without any of your previous configurations) and try it to see if runs ok. I insist on the backup part. If you try this, do not forget to backup that folder first.

---

### Post by bbarrons on 2006-06-12
made sense.... I renamed my ./evo folder to ./evo.../old and then restarted evolution. It does start a new email or reply to sender much faster now. must have been something in the home folder making it hang
thanks for the quick reply
Bill B

---

### Post by bbarrons on 2006-06-12
made sense.... I renamed my ./evo folder to ./evo.../old and then restarted evolution. It does start a new email or reply to sender much faster now. must have been something in the home folder making it hang
thanks for the quick reply
Bill B

---

### Post by henriquemaia on 2006-06-12
[quote=bbarrons]made sense.... I renamed my ./evo folder to ./evo.../old and then restarted evolution. It does start a new email or reply to sender much faster now. must have been something in the home folder making it hang
thanks for the quick reply
Bill B[/quote]

If now you want to import mails from your backup directory to your new configuration, look at this thread:

[http://ubuntuforums.org/showthread.php?t=185062](http://ubuntuforums.org/showthread.php?t=185062)

The steps are very similar.

---

