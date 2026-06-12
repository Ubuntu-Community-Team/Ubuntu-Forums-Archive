---
title: "Beginner problem or something serious?"
date: 2006-02-08
forum: Desktop Environments
---

### Post by auranen on 2006-02-08
Hello,

I am a new Ubuntu user and just installed the system yesterday.
Everything went just fine and the system is up and running...applications work ok, so does the network etc.

But: when I try to install all available updates, nothing happens....also, whatever I select from the system-control menu (e.g. sharing of directories), the cursor blinks for a while, the taskbar says "Opening..." and after that nothing happens. No window is opened, nothing is done, period. This is the case with almost any type of setting/control related activity I try to start from the menus....if I select something from the application side, everything works ok.

Does anyone know what could be the problem, have I done something wrong in the installation? 

BR,
Tero

---

### Post by kaamos on 2006-02-08
Hello and welcome to the forums!

What happens when you open a terminal (Applications->Accessories->Terminal) and type```
sudo update-manager
```
?

---

### Post by hashimoto on 2006-02-08
This has been on the list several times. The symptoms seem to tell that you (as user) do not have the administrative rights. Did you do an expert install? This seems to be related to it.

Two ways to fix (of which I'm not sure about the second, because I just learned about it and haven't tested). If you have root password (you should if you did an expert install) you can go directly to termial and do
```
su
``` and give your root password to get root rights.
Othewise you need to boot to rescue mode, which will give you root rights.

Fix 1:
Then do:
```
visudo
```
This will open the sudoers file. Go to the end of the file and look for
```
 root ALL = (ALL) ALL
```
add the following line after that:
```
your_username ALL = (ALL) ALL
```
(using your username, naturally). Then save and exit. Your username now has administrative rights.

Fix 2:
same procedure, but instead of using your username in sudoers file, add:
```
%admin ALL = (ALL) ALL
```
Then add your username to admin group.
Haven't done this and don't know how it works.

---

### Post by auranen on 2006-02-08
Thank You Hashimoto!

Yes, I did the expert install (not because I think I'm an expert, obviously ;-), but because I wanted to leave some disc partitions available)...

I have not tried the solution yet (since the machine is not here at the moment) but I'm pretty sure it's going to work since it seems quite clear that this is an access right problem.

Thanks!

BR,
Tero

---

### Post by kaamos on 2006-02-08
You can do manual partitioning without expert install as well.

---

### Post by auranen on 2006-02-08
[QUOTE=kaamos]You can do manual partitioning without expert install as well.[/QUOTE]

OK, thanks. I did not know that so I wanted to make sure I don't loose the data.

Very fast answers at this forum, great!

BR,
Tero

---

### Post by hashimoto on 2006-02-09
Glad I could help and welcome to Ubuntu, fellow Finn! This forum is great and I have got a lot of help here.

---

### Post by PapaWiskas on 2006-02-09
Agreed this is by far the best Linux forum I have ever been on.

---

