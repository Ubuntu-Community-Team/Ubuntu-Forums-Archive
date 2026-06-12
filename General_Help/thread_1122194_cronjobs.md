---
title: "cronjobs"
date: 2009-04-10
forum: General Help
---

### Post by ironic1122 on 2009-04-10
when i try to edit or create a cronjob on my user account it wont allow me to do so only root can or unless i sudo it!!

```

ezzi@PureVoltage:~/eggdrop$ crontab -e
crontabs/ezzi: Permission denied

```

or

```

ezzi@PureVoltage:~/eggdrop$ crontab -l -u ezzi
crontabs/ezzi: Permission denied

```

root account is locked and when i do a hash check it does have the "!" in front of the password hash so i dont know what i have to do to get this working i've searched google cant find anything on it please help me!!

---

### Post by lavinog on 2009-04-10
taken from crontab man page:
> If  the /etc/cron.allow file exists, then you must be listed therein in
       order to be allowed to use this command.  If the  /etc/cron.allow  file
       does  not  exist  but the /etc/cron.deny file does exist, then you must
       not be listed in the /etc/cron.deny file in order to use this  command.
       If neither of these files exists, then depending on site-dependent con&#8208;
       figuration parameters, only the super user will be allowed to use  this
       command,  or  all  users will be able to use this command. For standard
       Debian systems, all users may use this command.

I would check to see if /etc/cron.allow or /etc/cron.deny exists and see what is in them.

---

### Post by ironic1122 on 2009-04-10
ezzi@PureVoltage:~$ crontab -l
You (ezzi) are not allowed to use this program (crontab)

after i looked there was no cron.allow so i made one and then cron.deny was created :S and inside cron.deny it has "nobody" so i added my nick to cron.allow and then i get premission denied when i have the allow list empty and deny to nobody i get the error above same as if vice versa

---

### Post by lavinog on 2009-04-10
> **ironic1122 said:**
> 

root account is locked and when i do a hash check it does have the "!" in front of the password hash so i dont know what i have to do to get this working i've searched google cant find anything on it please help me!!

What do you mean by the root account is locked?
Can you not use sudo?

---

### Post by ironic1122 on 2009-04-10
no no i use sudo but for security i sudo passwd -l root

---

