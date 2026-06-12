---
title: "&quot;.dmrc is being ignored&quot;"
date: 2006-06-29
forum: Desktop Environments
---

### Post by blacktorch on 2006-06-29
When I login with gdm there's an error message coming up saying something about "$HOME/.dmrc is being ignored" and "need 644 permissions.". I tried to set it to 644 permissions with 'sudo chmod 644 .dmrc', however, when I try to login it's the same thing. I do get past it, however, since it's not fatal, but how can I remove it?

---

### Post by arizonagroovejet on 2006-06-29
Just delete the .dmrc file?

$ cd
$ rm .dmrc

---

### Post by ayoli on 2006-06-29
your home dir must not be group writeable, you can change that with:
```
sudo chmod g-w /home/your_user_name
```
then chmod .dmrc as said in message.

---

### Post by blacktorch on 2006-06-29
arizonagroovejet, I meant to delete the error, not the file, or isn't the file needed, is that what you're saying?

[QUOTE=ayoli]your home dir must not be group writeable, you can change that with:
```
sudo chmod g-w /home/your_user_name
```
then chmod .dmrc as said in message.[/QUOTE]
I tried that now, but it didn't stop the error message from popping up.

---

### Post by blacktorch on 2006-06-29
I fixed this problem by doing 'sudo chmod 740 -R /home/username'. Hope it helps someone else too.

---

### Post by ayoli on 2006-06-29
i missed the -R but chmoded to 0750 should work, since it works for me

---

### Post by az on 2006-06-29
I had filed a bug about this.  The problem is that one message is cryptic to non-geeks and it tries to kill two birds with one stone.  The permissions of .dmrc and the home folder are two different things.

I was told to file it upstream, after release.  I will do that....


In this case, you should have gotten a message saying that it is a security problem to allow other users to write to your home folder and "do you want to change that now?"  (with a "change" or "leave it" options and a tick box to not display the message again if you want to leave it.) The same should be for the .dmrc, too.

---

### Post by mrazster on 2006-06-29
Had this problem to...and the following worked for me.

```
sudo chmod 740 -R /home/username
```

---

### Post by El Chupacabras on 2008-04-30
Don't you mean chmod 750?
I tried 740, and that made my wallpaper disappear and then when I changed it to 750, GCONF gave me an error.

---

