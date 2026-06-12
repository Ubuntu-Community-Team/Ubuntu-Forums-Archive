---
title: "How do I share a folder so that it's accessible to other computers on the network?"
date: 2009-04-09
forum: General Help
---

### Post by Asham on 2009-04-09
I'm running Kubuntu on my computer and I'd like to share a folder in my home dir. I've right clicked the folder in Dolphin, clicked the config file sharing button. It then asks me for my password which I enter, but after that - nothing. Do I need to configure anything else?

I guess that is the first thing I need help with. 

The other thing is how do I connect to the shared Linux folder from another computer (running Windows XP)?

---

### Post by Asham on 2009-04-10
I've re-read the forum description and I'm not so sure this is the right forum for this question. I would appreciate it if a mod could move it to a better suited forum, e.g. general help.

---

### Post by Elfy on 2009-04-10
so moved :)

---

### Post by Asham on 2009-04-11
Thanks. :)

I've tried accessing the shared folder by entering \\computer\share but that wont work. I assume this is Windows syntax and wont work with Linux shares, right? 

Do I need a FTP-server to enable file sharing in my network? That's not exactly ideal. I was hoping to being able to map a network drive in the file explorer or such.

---

### Post by Elfy on 2009-04-11
In the past folders I have shared from ubuntu have been available in windows 

Try looking here under XP client

[https://help.ubuntu.com/community/SettingUpSamba#Connect%20to%20a%20samba%20server](https://help.ubuntu.com/community/SettingUpSamba#Connect%20to%20a%20samba%20server)

---

### Post by Wonslung on 2009-04-11
> **Asham said:**
> I'm running Kubuntu on my computer and I'd like to share a folder in my home dir. I've right clicked the folder in Dolphin, clicked the config file sharing button. It then asks me for my password which I enter, but after that - nothing. Do I need to configure anything else?

I guess that is the first thing I need help with. 

The other thing is how do I connect to the shared Linux folder from another computer (running Windows XP)?

the best thing to do is setup a samba server...with that you can set up samba shares for any folder you currently have or an entirely new folder.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
or just google.

when i was 100% new to linux i also found WEBMIN to be a HUGE help with setting up stuff like samba
[http://webmin.com/](http://webmin.com/)

---

