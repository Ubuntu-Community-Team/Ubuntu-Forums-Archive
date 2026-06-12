---
title: "odd behavior on ~/bin directory"
date: 2010-12-18
forum: Desktop Environments
---

### Post by jambel on 2010-12-18
Hi,

I've create a ~/bin directory to use it for my projects and I wanted to be path. I currently see that is included in $PATH environment but I can't call a script for example which is under this directory

I do echo $PATH and I get this

**/home/john/bin**:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

which means that is already path

now I have a shell script test.sh under ~/bin/test.sh
when I try to do that..
cd ~
sh tesh.sh I get can't open test.sh
and if I run it that way
sh ~/bin/test.sh I get the result

any ideas?

---

### Post by clrg on 2010-12-18
That's not what PATH is for. You don't need to invoke sh, your shebang line takes care of this. If you have execute permission and the program is somewhere in PATH, you can invoke it just by typing its name:

```
cd /wherever/the/hell/i/want/it/doesnt/matter
test.sh
```

Tip: 'cd ~' is unnecessary. Just type 'cd', and it will take you to ~ automatically.

---

### Post by jambel on 2010-12-18
thanks for your reply, results..
tesh.sh
bash: /home/john/bin/gmail.sh: Permission denied
sudo test.sh
sudo: test.sh: command not found

My actual problem is that I need to open a mono develop .exe file from anywhere
mono test.exe
Cannot open assembly 'test.exe': No such file or directory.

> **clrg said:**
> That's not what PATH is for. You don't need to invoke sh, your shebang line takes care of this. If you have execute permission and the program is somewhere in PATH, you can invoke it just by typing its name:

```
cd /wherever/the/hell/i/want/it/doesnt/matter
test.sh
```Tip: 'cd ~' is unnecessary. Just type 'cd', and it will take you to ~ automatically.

---

### Post by directhex on 2010-12-18
> **jambel said:**
> thanks for your reply, results..
tesh.sh
bash: /home/john/bin/gmail.sh: Permission denied
sudo test.sh
sudo: test.sh: command not found

gmail.sh doesn't have execute permissions, so you can't run it directly. chmod a+x gmail.sh

> My actual problem is that I need to open a mono develop .exe file from anywhere
mono test.exe
Cannot open assembly 'test.exe': No such file or directory.

Doesn't work like that. $PATH is for stuff you run directly, not for things passed to other programs. If you had a script in $PATH with "mono /path/to/test.exe" in it, you could run that from anywhere, but you can't just run "mono text.exe" because mono is looking in the current folder only.

---

### Post by jambel on 2010-12-18
Got it, thank you very much!

> **directhex said:**
> gmail.sh doesn't have execute permissions, so you can't run it directly. chmod a+x gmail.sh



Doesn't work like that. $PATH is for stuff you run directly, not for things passed to other programs. If you had a script in $PATH with "mono /path/to/test.exe" in it, you could run that from anywhere, but you can't just run "mono text.exe" because mono is looking in the current folder only.

---

