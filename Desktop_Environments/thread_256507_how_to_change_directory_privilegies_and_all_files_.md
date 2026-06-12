---
title: "how to change directory privilegies and all files privilegies in it?"
date: 2006-09-13
forum: Desktop Environments
---

### Post by Lualah on 2006-09-13
how to change directory privilegies and all files privilegies in it?

i try sudo chmod 777 test but only dir has new privilegies.
if i try
sudo chmod -r 777 test i get error of wrong command.

thx

---

### Post by smelly_sox on 2006-09-13
In a terminal
*sudo chown -R* username username /home/some-other-user/
Regards

---

### Post by pelagic on 2006-09-13
```

cd dir
find . | xargs chmod 750

```
if it shall be 750 of course.

**edit**:
alternatively it could be
```
sudo chmod -R 750 dir
```

btw:
the OP asked for change of **permissions **not of **ownership**

rtm:
```
man chmod
```

---

### Post by mitjab on 2006-09-13
```
In a terminal
sudo chown -R username username /home/some-other-user/
Regards
```

i think it is sudo chown -R username:username /home/some-other-user

: is between username

---

### Post by Lualah on 2006-09-13
i try

sudo chown -R cvsd:cvsd cvsrepo


but i still get permission denied!

---

### Post by smelly_sox on 2006-09-13
My bad
> username:username
definately : between
Also i read directory privileges in title of post. To change the file or directory owner is done via *chown*
The *chmod* command is for changing file permission. I hope I haven't confused the issue?
Regards

---

### Post by Lualah on 2006-09-13
with chown not working.

I think i need chmod, files and folder permission.

How to chnage files and folder permission.

sudo chmod 777 test change just test folder permission and not files permission in it!

thx

---

### Post by pelagic on 2006-09-13
> **Lualah said:**
> 
sudo chmod 777 test 
change just test folder permission and not files permission in it!
thx
```
sudo chmod **-R** 777 test
```
and as I said before:
**Read the manual** page of chmod to find out about it's options!!!
```
man chmod
```

---

