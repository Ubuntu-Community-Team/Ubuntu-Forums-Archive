---
title: "default bash prompt"
date: 2017-03-09
forum: Desktop Environments
---

### Post by Capetownlad on 2017-03-09
I have spent far too long looking for what I think must be a simple fix.  My command prompt looks wrong to me and I'd like to set it to the default, username and directory etc. I have looked at suggestions on here but it all seems too complicated to me.
Any help would be much appreciated
This is what it looks like...
 pumba@pumba-System-Product-Name:~

Please keep responses simple....like me!

---

### Post by howefield on 2017-03-09
To reset to default, use the command..

```
sudo cp /etc/skel/.bashrc ~/
```

Then either restart the terminal or use..

```
source ~/.bashrc
```

for it to take effect, although your prompt doesn't look particularly "wrong".

---

### Post by steeldriver on 2017-03-09
It looks to me like the underlying issue is that you accepted the default hostname at install time, rather than supplying your own choice of hostname

```

pumba-System-Product-Name

```

---

### Post by cariboo on 2017-03-11
Have you tried:

```
sudo hostname NEW_NAME_HERE
```

then

```
systemctl restart systemd-logind.service
```

---

### Post by Hakachukai on 2017-03-11
export PS1='\u@\h:\w >';

That command will do the trick.

PS1 is the var that contains what is shown on the command prompt in bash.

\u shows the username
@ just shows a literal @ symbol
\h shows your hostname ( the name of your machine )
: just shows a literal : symbol
\w shows the current working directory ( I.E. the directory that you are current in )

This will make a command prompt like this:
---------------------------------------------------------------
user@machine:~/directory >

There are a million other options for colors and other things like that... but that's the simple answer to your simple question.

---

### Post by Capetownlad on 2017-03-19
Thanks for your reply and suggestion.  Unfortunately, I didn't get notification of this and ending up re-installing.

---

