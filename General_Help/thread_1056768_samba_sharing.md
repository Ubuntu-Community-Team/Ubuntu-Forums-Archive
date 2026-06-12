---
title: "samba sharing"
date: 2009-02-01
forum: General Help
---

### Post by everplays on 2009-02-01
I have googled a much but all i found was editing "/etc/samba/smb.conf".
my issue is folders that i shared by nautilus is not included in smb.conf!
where are they? is there any way to share folders without editing smb.conf?

---

### Post by sanemanmad on 2009-02-01
I always use the terminal to edit the smb.conf file, (it has always been quick and easy).

? Why don't you just add the folder to smb.conf

Check out this link [http://ubuntuforums.org/showthread.php?t=76647]("http://ubuntuforums.org/showthread.php?t=76647")


```

comment = Directory name
browseable = yes
read only = no
create mask = 0765
directory mask = 0765
```

try adding that to the end of your smb.conf -- change to fit your needs.


I forgot to mention, on my laptop (Ubuntu 8.04) I can simply r-click on any folder, choose "Sharing-Options" and tick "Sharing" or "Create Share" I forget... Hope this helps :P

---

### Post by everplays on 2009-02-01
:) tnx for response.

but where are my shared folders now? they are not included in smb.conf but they are
accessable via network. i think probably there is a configuration file for each user
& we can use it instead of main smb.conf.

---

### Post by sanemanmad on 2009-02-01
You can make a custom script for each user/machine as well as the ```
smb.conf
``` file, you will need to edit ```
/etc/samba/smb.conf
``` and uncomment the line that uses a > per-machine-basis config.

---

### Post by everplays on 2009-02-01
tnx, this is what i was looking for.

---

