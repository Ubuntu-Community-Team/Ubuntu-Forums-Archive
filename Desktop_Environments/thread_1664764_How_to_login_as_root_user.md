---
title: "How to login as root user?"
date: 2011-01-11
forum: Desktop Environments
---

### Post by ankur.trapasiya on 2011-01-11
when installing ubuntu i created one user account named myself but it sometimes doesnot allows me to copy or run some files. It simply says "Permission Denied". 

I know i can run that files and scripts using sudo command but i want to login as a root user which has all the required permissions by default... 

How to do that ???

---

### Post by Polar Humenn on 2011-01-11
Ankur,

Use the "sudo -s" command. That will get you a root shell.

Cheers,
-Polar

---

### Post by Polar Humenn on 2011-01-11
Ankur,

Use the "sudo -s" command. That will get you a root shell.

Cheers,
-Polar

---

### Post by Rubi1200 on 2011-01-11
By default the root account is locked in Ubuntu and we do not provide support regarding how to log in to the account.

See here for more details:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

On that note, what exactly are you trying to run that is giving these errors?

For graphical applications you need to use gksu/gksudo

If you tell us more perhaps we can help you.

EDIT: @[Polar Humenn]("http://ubuntuforums.org/member.php?u=1019382"); the correct command to use is > sudo -i
see here for why:[http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

---

### Post by ankur.trapasiya on 2011-01-11
i want to one file from one location to another location... but it is saying "permission denied" ...

so i need to be root user.... now how can i copy that file without using terminal ???? This is the exact problem which i am facing...

---

### Post by JOHNNYG713 on 2011-01-11
In terminal, sudo nautilus This will open root nautilus and you can do what you need to there, It is the same as regular nautilus but with root permissions !

---

### Post by Rubi1200 on 2011-01-11
> **JOHNNYG713 said:**
> In terminal, [COLOR=Red]sudo nautilus[/COLOR] This will open root nautilus and you can do what you need to there, It is the same as regular nautilus but with root permissions !

Again, with all due respect, but the correct command for graphical applications is to use either gksu or gksudo.

Thus, ```
gksudo nautilus
```

Beware, you can truly mess up your system copying/moving files like this so please understand what you are doing.

---

### Post by JOHNNYG713 on 2011-01-11
> **Rubi1200 said:**
> Again, with all due respect, but the correct command for graphical applications is to use either gksu or gksudo.

Thus, ```
gksudo nautilus
```Beware, you can truly mess up your system copying/moving files like this so please understand what you are doing.
Yes I stand corrected ! gksudo !

---

### Post by 9000cse on 2011-07-08
Thanks guys, I give it a try.

Andy

---

### Post by nithin111 on 2011-07-08
May be this thread will help 
[http://techtimely.forumotion.net/t5-how-to-gain-unlock-root-power-in-ubuntu-1104](http://techtimely.forumotion.net/t5-how-to-gain-unlock-root-power-in-ubuntu-1104)

---

