---
title: "Move and rename file (read for details)"
date: 2009-04-02
forum: General Help
---

### Post by Chesamo on 2009-04-02
I'm trying to write a shell script to be used in conjunction with Xchat. Xchat logs to a file, which I then want automatically moved to a different directory at the end of the day. I would use the Scheduler to do this.

But! I don't want the new file to overwrite the old one -- I'd lose the contents of the old file. Is it possible to have the file renamed to, say, the current date? Or maybe prefix the file with a rising number.

Is this possible to do in a shell script, or will I have to learn python to do it?

---

### Post by change_mode on 2009-04-02
Should be possible with the date command (man date for more info).

I don't know what the whole command would look like though.

---

### Post by kanikilu on 2009-04-02
I may be misunderstanding what you are trying to do here, but if you just need to move and rename, you could just use:```
mv chat.log "/path/to/chat.log-$(date '+%F').log"
``` This will move the file "chat.log" and rename it to "chat-2009-04-02.log" (in the case of today's date). **man date** for more options if you want it formatted differently.

---

### Post by Chesamo on 2009-04-06
> **kanikilu said:**
> I may be misunderstanding what you are trying to do here, but if you just need to move and rename, you could just use:```
mv chat.log "/path/to/chat.log-$(date '+%F').log"
``` This will move the file "chat.log" and rename it to "chat-2009-04-02.log" (in the case of today's date). **man date** for more options if you want it formatted differently.
Cron doesn't accept +%F (it considers % a special character). I need a command that can be scheduled.

---

### Post by kanikilu on 2009-04-06
Escape it with a backslash? ```
mv chat.log "/path/to/chat.log-$(date '+\%F').log"
```

---

### Post by Chesamo on 2009-04-15
That works, but only partially. The log becomes chat.log-\2009-04-15, and thanks to that backslash my Windows FTP client can't even see it.

---

### Post by StuartN on 2009-04-15
Save the command in a script first, then schedule the script. You will need to change permissions on the script file to make it executable (in Properties).

---

