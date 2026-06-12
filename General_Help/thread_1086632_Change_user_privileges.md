---
title: "Change user privileges"
date: 2009-03-04
forum: General Help
---

### Post by gased on 2009-03-04
Hi there guys

How can i change user privileges through terminal?
I'm not able through the gui as everything is greyd . I've done every possible solution but didn't worked out.
So i'm going to do it through terminal which is easier.
How can i change their privileges. Let's say for example, for letting some users or groups install programs.

Any help would be great.

---

### Post by stumbleUpon on 2009-03-04
> **gased said:**
> Hi there guys

How can i change user privileges through terminal?
I'm not able through the gui as everything is greyd . I've done every possible solution but didn't worked out.
So i'm going to do it through terminal which is easier.
How can i change their privileges. Let's say for example, for letting some users or groups install programs.

Any help would be great.

System > Administration > Users and groups > Unlock 
then give your password. You should be able to change anything you want.

See here more info

[http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups](http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups)

---

### Post by gased on 2009-03-04
Well as i mentioned before everything is greyed out. I can not press unlock. Its grey.
That's why i asked for a terminal option

---

### Post by taurus on 2009-03-04
Do you have permission to run sudo/gksudo (root privilege)?  Are you the original user that created during the installing process?

What's the output of this command from a terminal?

```
id
```

---

### Post by gased on 2009-03-04
uid=0(root) gid=0(root) groups=0(root)


Yeah i have root privileges. It's a fresh install of ubuntu.

---

### Post by stumbleUpon on 2009-03-04
If you have permissions to run sudo, then you should be able to click the unlock button.

Is the unlock button also greyed out in system > administration > users and groups...?

---

### Post by taurus on 2009-03-04
> **gased said:**
> uid=0(root) gid=0(root) groups=0(root)

Yeah i have root privileges. It's a fresh install of ubuntu.

You log in as root!

---

### Post by gased on 2009-03-04
uid=1001(admin) gid=114(admin) groups=114(admin)
The other one was from putty, this is from gui.

---

### Post by gased on 2009-03-04
Yeah unlock is grey. Check here

---

### Post by taurus on 2009-03-04
> **gased said:**
> uid=1001(admin) gid=114(admin) groups=114(admin)
The other one was from putty, this is from gui.

I think that could be your mistake right there.  There is already an admin group in /etc/group that gives you a root privilege but now you have created another account using admin as your username and group.  Are you even able to use sudo if you log in as the first person, the one that you created during the installing process, UID=1000?

---

### Post by gased on 2009-03-04
Well it's a dedicated server and they gave me this one as username and i am able to do everything. I had to enable though root user in order not to type every time i use sudo , my pass.

---

### Post by gased on 2009-03-04
Is there any way to do it through terminal or no??

---

### Post by gased on 2009-03-06
Bump. :(

---

### Post by erik2912 on 2010-02-07
I know i'm quite late with this reply (but i add it for whoever has this problem again and just fyi). I found this thread because i had this problem too. But i found it's quite easy to fix!!
Open a terminal
([alt]+[f2] and enter "gnome-terminal" (without quotes))
type "sudo usermod -aG root {username}" also without quotes and where is {username} you type your own username. 

There you go. -a is to keep all your current groups and -G is to add a secundary group.
You can also just edit your /etc/group file, but i cannot recommend that.

---

