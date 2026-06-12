---
title: "Runing commands"
date: 2009-02-28
forum: General Help
---

### Post by RedSingularity on 2009-02-28
How would you go about running a command in terminal one after the other in one line?  You know, not having to type the first command, hit enter and then type the second and hit enter.  Thanks

---

### Post by howefield on 2009-02-28
[https://help.ubuntu.com/community/CommandlineHowto#Multiple%20Commands](https://help.ubuntu.com/community/CommandlineHowto#Multiple%20Commands)

Have a quick read..

---

### Post by RedSingularity on 2009-02-28
Perfect :)  Thanks

---

### Post by thtrgremlin on 2009-02-28
great link howefield.

I'll also add that that in addition to that quick read, a LONG, brain smashing of a read is ```
man bash
```

It is quite long, and easier to read on the Gnu website than in a terminal.

If getting a bit more power out of your command line is what you desire,it is the next step. It is a LOT of fun once you get the hang of it.

[http://www.gnu.org/software/bash/manual/bashref.html]("http://www.gnu.org/software/bash/manual/bashref.html")

---

### Post by RedSingularity on 2009-03-01
Another question, say i wanted to run commands that require a password.  How do i put the password in so it automatically reads it and i dont have to enter it?  

Example:  sudo -i && (password) && depmod -a && modprobe ndiswrapper

---

### Post by thtrgremlin on 2009-03-01
> **Shadow121 said:**
> Another question, say i wanted to run commands that require a password.  How do i put the password in so it automatically reads it and i dont have to enter it?  

Example:  sudo -i && (password) && depmod -a && modprobe ndiswrapper

When you use sudo, it won't ask for your password again till you go 3 minutes without using sudo, so these are some, among many, options:

write a script: put the commands into a text file just like you would put them on the command line, but make the first line #!/bin/bash, so, for example: > #/bin/bash
depmod -a && modprobe ndiswrapper
save it as 'myscript', for example, then```
chmod +x myscript/CODE] to set the executable flag. switch to a root shell:[CODE]sudo su
```and then run the script as root.```
./myscript
```
Hmm... technically, you could just run the commands as root
```
depmod -a && modprobe ndiswrapper
```
but also, this works:
```
sudo depmod -a && sudo modprobe ndiswrapper
```
It won't ask for the password again unless depmod takes more than 3 minutes, but even then, it will just prompt again for password. If you are really worried depmod will take longer, here is a really hacked way of doing it
```
sudo su <username> -c 'echo "`(depmod -a && modprobe ndiswrapper)`"'
```
sudo will cause password to be asked for. the () creates a subshell, but since you can't start a subshell directly with sudo, use echo as an intermediary to print the output. The `` (back ticks) are basically a "take the output of everything in the backticks and substitute. and the quotes ensure that the output is contained. the '' contain the rest literally since su only executes a single argument after the username.

Likely way more than you were interested, but I am a shell programming addict, and from the sounds of it, you would love it too. Hope that was a bit of insight into possibilities, and provides a worthy solution to your immediate issue.

Best luck.

---

### Post by Xiong Chiamiov on 2009-03-01
You _can_ use pipes and echo to enter a password (echo 'password' | sudo -s), but that's not really a good idea, since you'll have your password in plain text.  You could probably also use [expect](http://expect.nist.gov/).

---

### Post by thtrgremlin on 2009-03-01
while one may not worry about plaintext being displayed on the screen momentarily, all commands are logged, and depending on what you are doing, in several places. ~/.bash_history, for example, would store a copy of your password in plaintext for virtually forever (or till you delete it)

It is at very least poor practice.

'expect' looks interesting though  :)

---

