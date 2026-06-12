---
title: "change ownership?"
date: 2010-03-19
forum: Desktop Environments
---

### Post by AJHunter on 2010-03-19
Ok, here's a riddle (and I don't know the punch line, so don't ask):

Let's say there's a guy, and he's running Ubuntu (of course). Now, this guy installed the Ubuntu himself, and is the only user registered in the system. For some reason, he can't open the '/root' directory. The reason is given that the user, with the only registered username on the computer, who is also the person that owns the computer, is not the owner, and needs to log in as the owner in order to gain access to '/root'. How might he gain access without reinstalling the system? Also, he's already tried the terminal, using this:
```
*sudo chown -R* username username /home/some-other-user/
```Of course, the user was smart enough to change the second 'username' to his own, thinking that maybe the first 'username' might say the following word is a username, and, of course, this user changed 'some-other-user' to his own directory. Now, What would the *PAWS* (***P***roblem, ***A***ssets, ***W***ork-it-out, ***S***olution; it's not *my* acronym!) be like in this situation?

---

### Post by doas777 on 2010-03-19
well, you should never need to get into /root, under normal operations, but if you do, just use sudo/gksu. the logical place to start is here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

also don't go crazy with chown. users are not supposed to have access to most of / , and if you chown many of those files from their default, your system will not boot correctly. never modify systemfile ownership or permissions unless you know exactly what you want to happen and how to do it.

---

### Post by teejmya on 2010-03-19
You can also use ```
sudo passwd
``` That will allow you to change the password to your root account, and you will have access to root, and whatever it has access too.

---

### Post by AJHunter on 2010-03-19
oh. ok, thanks.

---

