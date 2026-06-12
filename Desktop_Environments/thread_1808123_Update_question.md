---
title: "Update question?"
date: 2011-07-19
forum: Desktop Environments
---

### Post by DMGrier on 2011-07-19
So I got a book called Ubuntu unleashed 2011 edition and I am going through each part of the book and I just started.

So I just ran through the first issue, I started with update process. So I started with 

sudo apt-get update

Then apt-get dist-upgrade

and then this pops up

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Would I by right in saying it is telling me I have to be in root to do this update? I heard that root can be a dangerous.

I know there is a GUI for this task but I am trying to learn terminal. Some info on this would be great.

---

### Post by Mr. Shannon on 2011-07-19
The sudo cammand temporarily elevates you to root privleges.  The book just left off the sudo on the second command.  Try this:
```
sudo apt-get dist-upgrade
```

And yes, root can be very dangerous.  When logged in as root I don't even think Linux will ask for confirmation if you try to delete the operating system, but I could be wrong and I'm not about to test the theory.  Note: using sudo can be dangerous as well but you have to explicitly apply it to a command so there is less chance of the user doing something stupid.  To read more about sudo go to this link: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

EDIT: There may be other reasons why sudo is better than root but I don't know for sure.

---

### Post by DMGrier on 2011-07-20
Thanks so much, I can move around Ubuntu pretty well with the exception of terminal. Just never really learned how to use it.

---

### Post by 2F4U on 2011-07-20
Another reason why sudo may be preferable over root is that the root user is well known and a hacker's first target. If there is no root user (as in Ubuntu) a hacker would need to first guess the name of an user account before attempting to guess the password. So there is one additional line of defence.

---

### Post by koleoptero on 2011-07-20
> **2F4U said:**
> Another reason why sudo may be preferable over root is that the root user is well known and a hacker's first target. If there is no root user (as in Ubuntu) a hacker would need to first guess the name of an user account before attempting to guess the password. So there is one additional line of defence.

There is a root user in ubuntu as in every linux system, and in ubuntu it uses the same pass as the user so it's not exactly safer.

---

### Post by tommpogg on 2011-07-20
> **DMGrier said:**
> So I got a book called Ubuntu unleashed 2011 edition and I am going through each part of the book and I just started.

So I just ran through the first issue, I started with update process. So I started with 

sudo apt-get update

Then apt-get dist-upgrade


Notice that apt-get dist-upgrade will upgrade the whole system to the newest release.
If you just want to upgrade the installed software, use
```

sudo apt-get update
sudo apt-get upgrade

```

For more details, you can check the online help or a guide (for instance [Ubuntu Pocket Guide and Reference]("http://ubuntupocketguide.com/index_main.html"))

---

### Post by pinballwizard on 2011-07-20
> **tommpogg said:**
> Notice that apt-get dist-upgrade will upgrade the whole system to the newest release.
[Reference]("http://ubuntupocketguide.com/index_main.html"))

apt-get dist-upgrade** does not **move you to the next release. Where did this idea come from?

```
jason@Vitalstatistix:~$ sudo apt-get dist-upgrade
[sudo] password for jason: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jason@Vitalstatistix:~$ 
```

And I remained on 10.10, and didn't magically migrate to 11.04.

---

### Post by tommpogg on 2011-07-20
> **pinballwizard said:**
> apt-get dist-upgrade** does not **move you to the next release. Where did this idea come from?


You are aright and I am sorry for the mistake.
I read it in the guide I suggested, but the man pages agree with your comment.

Sorry again and thank you for correcting me

---

