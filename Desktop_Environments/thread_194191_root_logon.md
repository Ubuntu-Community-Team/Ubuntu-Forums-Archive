---
title: "root logon"
date: 2006-06-11
forum: Desktop Environments
---

### Post by MrSam on 2006-06-11
I really need to find out how to logon as root. When I try to logon at the start page it tells me that root can not logon from that page.

I have a very nice Samba server set up and I have been able to access the drives there but everytime I need to use them I keep getting prompted for a password. I want to edit my fstab to make the connection permanent at bootup.

If there is another way to stop the repeated password prompt that would be apreciated too but the big thing here is the root logon. Too many setup and maintenance actions require root access.

---

### Post by adwait on 2006-06-11
Any command that requires root prevlieges can be appended with
```
sudo
```

Or if you want to absolutely logon as root, first enable the root account with
```
sudo passwd
```

Not edit the GDM properties in Settings, so that it allows Graphical root login.

---

### Post by carontis on 2006-06-11
I ususally used this: System ==> Administration ==> Login window ==> nd when in there go to Security and give permission. After this, go to System ==> Administration ==> Users and Groups and afetr panel is open, mark the one to see all users; you'll see the first should be root; click on it and go to preferences (near it); after open the panel you'll see in the end there are two rows with astrisks; change those aterisks with password you need. DONE!
Anyway also in Ubuntu doesn't ask, it should be better reboot it again so everything will be well reported to its db.

Bye

---

### Post by frying_fish on 2006-06-11
To be honest, whenever you need to run an administration task as root, you don't need to login to X as root.  You can still login as your regular user, then if its something that you need to do from a console, such as editing fstab, then just open a terminal and type 'sudo -s'  for a root shell, from there you can keep doing root tasks in that terminal whilst you need.  This is a much better way than logging in to everything as root.


On the topic of making the connection permanent, make your fstab line for the samba connectionl look similar to this:

```

//computer/share /mount/point smbfs defaults,credentials=/etc/samba/smb.credentials,rw,uid=YourUser 0 0

```

then create the credentials file with the following format:
```

Username:
username = username

Password:
password = password

```

And once you have created the credentials file.  change to the directory you have saved it, and set the correct permissions:

```

chmod 700 smb.credentials; chown root:root smb.credentials

```

That way, without root access no one will be able to look at the file, as the passwords are stored in plain text.

---

### Post by Vinze on 2006-06-11
You can also go into a terminal and type ```
sudo su
```.

---

### Post by MrSam on 2006-06-11
Thanks everyone. People here sure are great about helping out. Makes life a lot easier. :cool:

---

