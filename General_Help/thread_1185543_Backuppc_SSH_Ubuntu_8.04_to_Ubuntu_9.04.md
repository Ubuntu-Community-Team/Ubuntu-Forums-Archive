---
title: "Backuppc SSH Ubuntu 8.04 to Ubuntu 9.04"
date: 2009-06-12
forum: General Help
---

### Post by dwanders on 2009-06-12
I have set up BackupPC on my Ubuntu 9.04 computer. It is working great for the local PC, but now I want to add a remote Ubuntu server running 8.04 LTS to the mix (I am experimenting with the possibility of BackupPC replacing my current backup scenario for its data-de-duplication ability). When I run the full backup I am getting the error:

(ssh-askpass:29952): Gtk-WARNING **: cannot open display: :0.0
No protocol specified

If I manually run the command ssh-askpass I get the same error.
If I manually run the ssh command executed by BackupPC:
 
```
ssh -q -x -n -l root server env LC_ALL=C /bin/tar -c -v -f - -C /var/www --totals .
root@server's password:
```

I get a console prompt for roots password on server, and after I enter the password, I get the stream of data I believe BackupPC is expecting. 

Would anyone have any suggestions for why my ship is not going? At this point I believe I have followed all the instructions in the documentation but have been know to miss a thing er two!

Any help is greatly appreciated.

---

### Post by dwanders on 2009-06-17
Wow - nobody - not even something to check or a link to another post even. Huh.

---

### Post by crush304 on 2009-06-27
[http://www.howtoforge.com/linux_backuppc_p4](http://www.howtoforge.com/linux_backuppc_p4)

---

### Post by dwanders on 2009-08-10
This turned out to be a problem with the location and name of my ssh keys. After I renamed them correctly - all seemed to begin working hunky dory. 

Thanks.

---

