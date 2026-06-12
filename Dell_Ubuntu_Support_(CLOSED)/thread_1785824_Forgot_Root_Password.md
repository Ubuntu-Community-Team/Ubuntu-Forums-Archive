---
title: "Forgot Root Password"
date: 2011-06-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by PLEASEHELPMENOW on 2011-06-18
Hello. I have a Dell Inspiron Mini 10 with Ubuntu. I accidentally saved my review notes for a midterm in a temporary directory and have lost them. I would like to recover them but I cannot install the tool without root access, and I have forgotten my root password. I have to take the midterm tomorrow, someone please help me!

---

### Post by snowpine on 2011-06-18
Welcome to the forums!

There is no "root password" in the default install of Ubuntu. Rather, we use "sudo" as described here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) 

If you've fogotten your password, you can easily reset it following these instructions:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Worst-case scenario, if your system is irrecoverably unbootable, you can boot using an Ubunut Live CD or USB and recover your files. :)

---

### Post by PLEASEHELPMENOW on 2011-06-18
If I type sudo before the command, it still asks me for a password

---

### Post by snowpine on 2011-06-18
The password is your user password.

What is "the command" of which you speak?

Also if this is a data recovery situation where you have accidentally deleted the files, then I really recommend booting from a Live CD/USB. If you install software on the system then there is a greater risk you'll overwrite the file you're trying to recover. If you stop, take a deep breath, and give all the details of the problem, I'm sure there is someone on the forums who can help. :)

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by PLEASEHELPMENOW on 2011-06-18
Holding the shift key while I boot up does nothing, is there some other way to enter recovery mode?

---

### Post by PLEASEHELPMENOW on 2011-06-18
In that case, I have forgotten my user password. I accidentally saved a file to /tmp. It no longer exists. I REALLY need this file. What should I do?

---

### Post by lisati on 2011-06-18
> **PLEASEHELPMENOW said:**
> Holding the shift key while I boot up does nothing, is there some other way to enter recovery mode?

What version of Ubuntu are you using? Some older versions require you to press the "Esc" key.

---

### Post by snowpine on 2011-06-18
I am not a file recovery expert, unfortunately.

The best advice I can give is DON'T BOOT THE COMPUTER. Hop on another computer with web access and do some research about file recovery. It may be as simple as booting with an Ubuntu Live CD and browsing to the /tmp folder. Sorry I can't be of further assistance.

---

### Post by PLEASEHELPMENOW on 2011-06-18
I also tried using the escape key, I searched for solutions before asking this forum. It is Ubuntu 8.04. The file recovery guide seems to be based around recovering files from an unreadable drive, which is not what I need to do. Thank you anyway, I had no reason to be so distraught, it is only a midterm.

---

### Post by kakkerpolakke on 2011-06-26
I have a similar problem.

I lost my root password. Tried the recovery mode, went down to root shell, and changing password there. However, all I get is an authentication token manipulation error.

I searched for about a week for an answer, different people have different theories, none worked for me :)

Do you know any way that could help me change the f-ing password? If not, I'm actually ready to format the whole goddamn computer: how do you do it from root shell? :confused:

Thanks for your help :(

---

### Post by haqking on 2011-06-26
unless you pruposely created a root password and in doing so enabled the root account there is not one.

any password it asks you should be the one you use to login etc (unless you have auto login)

when it asks for root it is asking for root permission which you get by using sudo

so when it asks for a password type in your own

---

### Post by kakkerpolakke on 2011-06-26
I'm sorry, I probably should've explained more clearly (and I am terribly new to Ubuntu :()

I lost my regular password, which is why I went down to root shell to change it. However, this does not work, as I get an "authentication token manipulation error".

---

