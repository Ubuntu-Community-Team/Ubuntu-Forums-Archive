---
title: "Webmin on Breezy; can't login"
date: 2006-01-02
forum: Desktop Environments
---

### Post by akniss on 2006-01-02
I've been banging my head against the wall for a few days trying to manually edit the samba config file to share a printer...  So I decided to try Webmin.  I installed it with synaptic.  When I try to access [https://localhost:10000](https://localhost:10000), I can't login. Not with my normal login, anyway.  Any ideas?

---

### Post by akniss on 2006-01-02
Googled around and found this, so I can now login.

sudo /usr/share/webmin/changepass.pl /etc/webmin root [password]

So now I have a new problem... I don't have access to any modules???  I installed the webmin-samba from synaptic.  How do get this working??

---

### Post by akniss on 2006-01-02
[QUOTE=akniss]Googled around and found this, so I can now login.

sudo /usr/share/webmin/changepass.pl /etc/webmin root [password]

So now I have a new problem... I don't have access to any modules???  I installed the webmin-samba from synaptic.  How do get this working??[/QUOTE]

Attached is what I see when I log in to webmin.

---

### Post by eniacpx on 2006-01-02
Try this. 

1. Do a complete removal of all things webmin.
2. Change your actual root passwd on the box.
3. Reinstall webmin.

I had a hard time getting webmin up and running too, until I did this.

---

### Post by akniss on 2006-01-02
Problem fixed... I did not have the root account enabled.  I had to ```
sudo passwd root
``` then add a root account to Webmin.  Does anyone know if it is possible to run webmin without enabling root in Ubuntu?

---

### Post by tinsami1 on 2006-01-06
[QUOTE=akniss]Problem fixed... I did not have the root account enabled.  I had to ```
sudo passwd root
``` then add a root account to Webmin.  Does anyone know if it is possible to run webmin without enabling root in Ubuntu?[/QUOTE]

Add another admin user in webmin.  Then disable root again.

---

