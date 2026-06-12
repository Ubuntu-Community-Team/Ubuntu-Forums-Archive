---
title: "How can I read the shutdown log?"
date: 2006-02-25
forum: Desktop Environments
---

### Post by Marcos.Rufino on 2006-02-25
Whenever I reboot or shutdown Ubuntu Breezy Badger I can see some error messages. The problem is that those messages disappear too fast so I can't read them. Isn't there a log file where I can't read those messages carefully. I came from Fedora and this task was very easy to accomplish there. I'm really jaded reading every f* file inside /var/log/ and find nothing.

What am I missing here? Any suggestions? 

Thanks in advance.

---

### Post by dcstar on 2006-02-25
[QUOTE=Marcos.Rufino]Whenever I reboot or shutdown Ubuntu Breezy Badger I can see some error messages. The problem is that those messages disappear too fast so I can't read them. Isn't there a log file where I can't read those messages carefully. I came from Fedora and this task was very easy to accomplish there. I'm really jaded reading every f* file inside /var/log/ and find nothing.

What am I missing here? Any suggestions? 

Thanks in advance.[/QUOTE]
Should be in /var/log/messages.

---

### Post by Marcos.Rufino on 2006-02-25
Thanks David for your reply. But I couldn't find what I want in /var/log/messages. I've tried this before, without success. I don't know what that file is telling but I'm certain that it is not what appears when I shutdown or reboot my machine.
When I restart/reboot, appears some error messages telling something about a conflict about folding@home activities. Nothing of that appears in /var/log/messages. By the way, none of the text that appears when I exit Ubuntu appears to be in that file.

---

### Post by dcstar on 2006-02-25
[QUOTE=Marcos.Rufino]Thanks David for your reply. But I couldn't find what I want in /var/log/messages. I've tried this before, without success. I don't know what that file is telling but I'm certain that it is not what appears when I shutdown or reboot my machine.
When I restart/reboot, appears some error messages telling something about a conflict about folding@home activities. Nothing of that appears in /var/log/messages. By the way, none of the text that appears when I exit Ubuntu appears to be in that file.[/QUOTE]
Edit /etc/default/bootlogd to:

BOOTLOGD_ENABLE=Yes

and see if that adds any useful stuff to your log files on reboot.

---

