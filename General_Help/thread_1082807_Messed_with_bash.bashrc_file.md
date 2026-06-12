---
title: "Messed with bash.bashrc file"
date: 2009-02-28
forum: General Help
---

### Post by satish_j on 2009-02-28
I am getting list of errors after starting the terminal window This is after editing the bash.bashrc file in etc directory.I went on to add foll to it:
```

PATH=/usr/local/mysql/bin
export PATH

```
Now,everytime I go to terminal,I get the foll
```

bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
bash: uname: command not found
bash: uname: command not found
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: sed: command not found
bash: complete: is: no completion specification
bash: complete: not: no completion specification
bash: complete: included: no completion specification
bash: complete: in: no completion specification
bash: complete: the: no completion specification
bash: complete: PATH: no completion specification
bash: complete: environment: no completion specification
bash: complete: variable.: no completion specification
satish@TITAN:~$

```
I took the backup of bash.bashrc file before making the change,but Iam not able to restore it back as it says that 'cp command is in /usr/bin and /usr/bin is not included in PATh variable.
In a dire need of help..pls

---

### Post by heindsight on 2009-02-28
Try:
```
/bin/cp bash.bashrc-backup /etc/bash/bashrc
```
(of course you'll have to change bash.bashrc-backup to the actual location where you saved the backup.

If you want to add something to the path, you should use:
```
PATH=$PATH:/usr/local/mysql/bin
```

---

### Post by taurus on 2009-02-28
> **heindsight said:**
> Try:
```
/bin/cp bash.bashrc-backup /etc/bash/bashrc
```
(of course you'll have to change bash.bashrc-backup to the actual location where you saved the backup.

If you want to add something to the path, you should use:
```
PATH=**[COLOR="Blue"]$[/COLOR]**PATH:/usr/local/mysql/bin
```

I am sure you have to include the $ in there though.

---

### Post by heindsight on 2009-02-28
> **taurus said:**
> I am sure you have to include the $ in there though.

Of course :oops: 
Thanks for pointing that out

---

### Post by satish_j on 2009-02-28
> **heindsight said:**
> Try:
```
/bin/cp bash.bashrc-backup /etc/bash/bashrc
```
(of course you'll have to change bash.bashrc-backup to the actual location where you saved the backup.


But,i already have tried that without any success.
I have kept the backup on desktop and,on restoring:
```
cp ~/Desktop/bash.bashrc /etc/bash.basgrc
```
it gives me err:
cp command is in /usr/bin and /usr/bin is not included in PATh variable

---

### Post by taurus on 2009-02-28
> **satish_j said:**
> But,i already have tried that without any success.
I have kept the backup on desktop and,on restoring:
```
cp ~/Desktop/bash.bashrc /etc/bash.bas**[COLOR="DarkRed"]g[/COLOR]**rc
```
it gives me err:
cp command is in /usr/bin and /usr/bin is not included in PATh variable

You need to use the whole path now.

```
sudo /usr/bin/cp ~/Desktop/bash.bashrc /etc/bash.bashrc
```
Then reboot.

---

### Post by satish_j on 2009-02-28
> **taurus said:**
> You need to use the whole path now.

```
sudo /usr/bin/cp ~/Desktop/bash.bashrc /etc/bash.bashrc
```
Then reboot.

That did the work for me.Now its working all fine..Thanks a million..
Also,can anyone tell me the easiest way to set PATH env variable for mysql.
I have to always type the full path to mysql for getting the mysql prompt.
My first exp with editing the bash file(after googling)was not good as you saw from above.
Or,am i on the right track(just missing the $ before 'PATH')??

---

### Post by heindsight on 2009-02-28
Nevermind, I see you got it fixed.

If you want to add that mysql directory to your path, see [post=6813749]my earlier post in this thread[/post].

---

### Post by taurus on 2009-02-28
Edit ~/.bashrc

```
gedit ~/.bashrc
```
and add these two lines to the end of it.

```
PATH=$PATH:/usr/local/mysql/bin
export PATH
```
Save it and then run

```
source ~/.bashrc
```
/usr/local/mysql/bin should be in your path now.

---

### Post by satish_j on 2009-02-28
All prob solved.THanks all for your prompt support....:P:P

---

