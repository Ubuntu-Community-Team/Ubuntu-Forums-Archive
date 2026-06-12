---
title: "[SOLVED] I forgot my Ubuntu Password"
date: 2006-06-12
forum: Desktop Environments
---

### Post by RonB123123 on 2006-06-12
I read some directions on a different thread and he spoke of putting the live cd in (in order to fix the already installed Ubuntu), opening the terminal, and then said what to put in. When I finished the first line, it said I had to login to Super User. 

I didn't know the Super User's password, so I was stuck once again.

Could anyone help me? I really don't feel like reinstalling Ubuntu all over again. Last time we did that our second partition with XP on it was totally erased and we had a damaged Ubuntu and a second installed Ubuntu lol. 

Please help, I'm so confused. I used the search button but the topic I spoke of previously was the only one I found about recovering passwords. Thank you.

~Ron

---

### Post by DeShark on 2006-06-12
There is no Superuser Password on the live CD... afaik. You should be able to reset your password by editing the shadow file... either that or chrooting and using passwd (from a live CD)

---

### Post by nanotube on 2006-06-12
[QUOTE=RonTheCon]I read some directions on a different thread and he spoke of putting the live cd in (in order to fix the already installed Ubuntu), opening the terminal, and then said what to put in. When I finished the first line, it said I had to login to Super User. 

I didn't know the Super User's password, so I was stuck once again.

Could anyone help me? I really don't feel like reinstalling Ubuntu all over again. Last time we did that our second partition with XP on it was totally erased and we had a damaged Ubuntu and a second installed Ubuntu lol. 

Please help, I'm so confused. I used the search button but the topic I spoke of previously was the only one I found about recovering passwords. Thank you.

~Ron[/QUOTE]
you probably forgot to use "sudo" with your commands. just preface the commands you are trying to execute with sudo, and it should not complain. (as in, enter "sudo yourcommand" instead of just "yourcommand").

for more info on sudo, see [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by RonB123123 on 2006-06-12
Hello,

Thank you very much for the help. I finally figured it out thanks to both of you. I wasn't using the sudo command, and I just found the shadow file and it did the trick. :)

~Ron

---

### Post by frying_fish on 2006-06-12
much simpler option than messing with the livecd and chroots and stuff, is to just boot "recovery mode" unless you have deactivated / require a password to access that, as that logs in as root, and then you can just type
```

passwd USER

```
where USER is the user you want to change the password for, then reboot the machine and you're set.

---

