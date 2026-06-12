---
title: "uninstall samba"
date: 2009-04-27
forum: General Help
---

### Post by 762sks on 2009-04-27
ive searched all over and thought id post. i messed up my config file so i thought id uninstall it and reinstall it.

only problem is i cant figure out how to do that. i installed it using terminal, but i am not sure how to uninstall it. 


please help


thanks 
762sks

---

### Post by cwbar_1 on 2009-04-27
You can search for "samba" in Synaptic package manager and mark to remove. Or apt-get remove samba.

---

### Post by 762sks on 2009-04-27
life saver thank you

---

### Post by Iowan on 2009-04-27
If it's just the config file that's fubar, it might be easier to get a fresh copy of that - rather than uninstall/reinstall. I usually  copy  my /etc/samba/smb.conf to /etc/samba/smb.bak to before trying anything "new".

---

