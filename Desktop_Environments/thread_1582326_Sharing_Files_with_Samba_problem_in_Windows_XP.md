---
title: "Sharing Files with Samba problem in Windows XP"
date: 2010-09-26
forum: Desktop Environments
---

### Post by LepeKaname on 2010-09-26
I have almost no experience with Samba as usually I don't use Windows. Being said that, here is the "strange" problem:
I shared home folders to be accessible from a Windows XP notebook computer which my wife uses some times. One of the folders contains many pictures which I later renamed (bulk rename at the ubuntu box). The pictures at the Windows box still have the old name and they can be opened as usual. However, when my wife rotated a picture and saved it with the same name, the picture just disappeared. For some reason It can not display the new names. I removed the Thumbs.db files, restarted samba and re-configure again the connection with samba but no luck. It is not a big problem but I was wondering if someone knows what this is happening?

This is my samba config file:

```
[global]
        workgroup = WORKGROUP
        server string = %h Ubuntu
        dns proxy = no
        log file = /var/log/samba/log.%m
        max log size = 1000
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        security = user
        encrypt passwords = true
        obey pam restrictions = yes
        unix password sync = yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        pam password change = no
        map to guest = bad user
        usershare allow guests = yes

[homes]
   comment = Home Directories
   browseable = yes
   read only = no

[printers]
        comment = All Printers
        browseable = no
        path = /var/spool/samba
        printable = yes
        create mask = 0700

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
```

Thank you in advance.

---

### Post by tom4everitt on 2010-09-26
I'm not a Samba expert, but out of curiosity: What exactly did you name the files? Was it something inherently Windows unfriendly perhaps?

Also, I assume it was in Windows the file "disappeared". Can you see it from the Windows command line? 
Removing the Thumbs.db would probably have helped better if the viewing problem was in Linux. I wonder what the Windows equivalent of Thumbs.db would be...

Does switching the names back help?

---

### Post by LepeKaname on 2010-09-27
Thank you tom4everitt.

> Was it something inherently Windows unfriendly perhaps?
I believe the names are fine: they were renamed from something like : "IMG_0001.JPG" to something like: "20100927_181005.JPG" (date and time)

I didn't check for the names using the command line in Windows but my guess is that it would be the same (I will check that later though). I used an image viewer (irfanview) to open the files, so in my believe it skips the explorer apis. 

I wonder if samba has some kind of filename cache? 
or if it is done when you access a network drive in windows? 

More than 2 weeks have passed since I renamed the files and still getting the old names. New files are added with the correct names (as expected).

---

### Post by LepeKaname on 2010-09-29
tom4everitt, you were right. The problem was that the new names were in the form: **20100927:181005.JPG** and not **20100927_181005.JPG** as I thought. So samba was hashing the names in order to be displayed in Windows. Oh... it was really a series of misunderstandings (everyday life).

Thank you for your time.

Still wondering why the file disappeared after being edited... But anyway... now names are fixed and everything works as expected. :)

---

