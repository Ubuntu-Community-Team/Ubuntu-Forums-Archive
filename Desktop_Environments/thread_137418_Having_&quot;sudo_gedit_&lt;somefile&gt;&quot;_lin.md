---
title: "Having &quot;sudo gedit &lt;somefile&gt;&quot; link"
date: 2006-02-27
forum: Desktop Environments
---

### Post by Xerak on 2006-02-27
Hello,

Linux noob here. I was wondering if there was a way to have a link on the desktop (Gnome) to a "sudo egedit <file>" and have the interface ask us for the password before viewing the file? Right now I created a link but of course it doesnt do anything because I don't have the right to edit the specific file. I would like something faster than going in console and typing "sudo gedit <file>".

Hu, I hope it's clear enough :-) Any help appreciated.

---

### Post by aysiu on 2006-02-27
Try making the launcher have the command: ```
gksudo gedit /home/blah/somefile
```

---

### Post by Xerak on 2006-02-28
Thanks, I got further.

Trying to edit using command "gksudo gedit /usr/local/apache2/conf/httpd.conf" but it seems that my "user space" is used by default and it's trying to create the file in /home/mysername/'/usr/local/apache2/conf/httpd.conf ... Any idea?

---

### Post by Xerak on 2006-02-28
So, no way of doing this I guess?

---

### Post by RAOF on 2006-03-01
```
gksudo gedit /usr/local/apache2/conf/httpd.conf
``` should work.  That's an absolute path - it should work no matter what the cwd is.  If it doesn't work... well, I've got nothing :(

---

