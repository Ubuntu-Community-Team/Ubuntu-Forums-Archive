---
title: "RegnumOnline"
date: 2011-02-15
forum: Gaming &amp; Leisure
---

### Post by dado prso on 2011-02-15
Is it a problem that regnum is installed as root?
The desktop icon has a silver lock on it.
When I click the program to start it, I get an error saying 
> 04:33:07 PM: Directory 'en_US' couldn't be created (error 13: Permission denied)
04:33:07 PM: can't open file 'rolauncher.mo' (error 13: Permission denied)

and

> 04:33:07 PM: can't create file 'eula_temp.html' (error 13: Permission denied)
04:33:07 PM: Unable to open requested HTML document: eula_temp.html

When I look at the icons permissions, it shows owner: root, group: root, others: blank

Thanks you,
Dado

---

### Post by sakuramboo on 2011-02-15
Yes.

---

### Post by Carpentr on 2011-02-17
I encountered that problem before as well. All I had to do was log in to my root account and change the permission settings of the files. If you don't have a root account set up then just run this in the terminal.
```

sudo passwd root

```

For future reference, I'm pretty sure, when you install an application if you put the command ```
sudo
``` in front of your install command you won't have any permission problems.

---

