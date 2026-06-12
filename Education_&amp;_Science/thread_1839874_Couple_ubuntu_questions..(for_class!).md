---
title: "Couple ubuntu questions..(for class!)"
date: 2011-09-06
forum: Education &amp; Science
---

### Post by weeman1 on 2011-09-06
Hey all. I recently installed ubuntu and dual booting it with Windows 7. I'm using ubuntu for my Introduction to Data Structures class where we are required to learn unix.

My friend, who recently took the class told me all about this. He told me to learn the ssh commands and to learn linux/unix/bash.

1. What is bash?? I know linux and unix are the same(?) but unsure of what bash is.

2.What are the ssh commands and where can I find them to study them?

3.Where can I learn how to hand compile code for the languages Java, C in terminal?

I am currently using a unix tutorial to learn some unix commands, but I feel it is not enough. My programming skills are HORRIBLE and this class is arguably the toughest class in the entire campus!!

help!!!

---

### Post by Drenriza on 2011-09-06
> **weeman1 said:**
> Hey all. I recently installed ubuntu and dual booting it with Windows 7. I'm using ubuntu for my Introduction to Data Structures class where we are required to learn unix.

My friend, who recently took the class told me all about this. He told me to learn the ssh commands and to learn linux/unix/bash.

1. What is bash?? I know linux and unix are the same(?) but unsure of what bash is.
Bash is a linux scripting language.

> 2.What are the ssh commands and where can I find them to study them?
open a terminal in linux and type```
man ssh
```
but ssh is straight forward
```
ssh username_on_remote_server@remote_server_ip
```
if u need a port number
```
ssh -p port_number username_on_remote_server@remote_server_ip
```

> 3.Where can I learn how to hand compile code for the languages Java, C in terminal?
```
apt-get install gcc
``` C compiler type ```
man gcc
``` ```
To compile a single source file, type: gcc -o outputfile file1.c
To compile multiple files, type: gcc -o outputfile file1.c file2.c file3.c
```for more info
read here for java compiler post #2
[http://ubuntuforums.org/showthread.php?t=152449](http://ubuntuforums.org/showthread.php?t=152449)

> I am currently using a unix tutorial to learn some unix commands, but I feel it is not enough. My programming skills are HORRIBLE and this class is arguably the toughest class in the entire campus!!

What do you want to learn. Linux commands or programming? Not 100% the same thing :p

Im not the best at linux but i don't see myself as the worst. Been lucky enough to work as a server administrator for what 2 years now. And used linux 2 years before that. If you want some help to linux commands, feel free to leave me a PM and i will try and help you out.

---

### Post by 2F4U on 2011-09-06
Bash is what is usually called the shell. It is the command line interface in Linux/Unix. You may know that Linux doesn't necessarily need a desktop environment and can be completely operated by using a shell.

[http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29]("http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29")

SSH is a network protocol that allows you to establish a secure connection to another computer.

[http://en.wikipedia.org/wiki/Secure_Shell](http://en.wikipedia.org/wiki/Secure_Shell)

---

### Post by Drenriza on 2011-09-06
> **2F4U said:**
> You may know that Linux doesn't necessarily need a desktop environment and can be completely operated by using a shell.

Thats why linux is so great :p no fuss with a GUI. Thats the way to administrate systems ,) and not like MS :( pheff

---

### Post by haqking on 2011-09-06
**1. What is bash?? I know linux and unix are the same(?) but unsure of what bash is.**

Linux and Unix are not the same per se but for intents and purposes they come 
under the same umbrella.

for BASH see here :
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)
[http://www.gnu.org/s/bash/manual/html_node/What-is-Bash_003f.html](http://www.gnu.org/s/bash/manual/html_node/What-is-Bash_003f.html) 

**2.What are the ssh commands and where can I find them to study them?**

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
[http://www.webhostgear.com/35.html](http://www.webhostgear.com/35.html)

**3.Where can I learn how to hand compile code for the languages Java, C in terminal?**

[http://www.cyberciti.biz/tips/linux-how-to-compile-program.html](http://www.cyberciti.biz/tips/linux-how-to-compile-program.html)
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by kaldor on 2011-09-06
> **weeman1 said:**
> Hey all. I recently installed ubuntu and dual booting it with Windows 7. I'm using ubuntu for my Introduction to Data Structures class where we are required to learn unix.

My friend, who recently took the class told me all about this. He told me to learn the ssh commands and to learn linux/unix/bash.

1. What is bash?? I know linux and unix are the same(?) but unsure of what bash is.

2.What are the ssh commands and where can I find them to study them?

3.Where can I learn how to hand compile code for the languages Java, C in terminal?

I am currently using a unix tutorial to learn some unix commands, but I feel it is not enough. My programming skills are HORRIBLE and this class is arguably the toughest class in the entire campus!!

help!!!

1) Bash is the default shell in Linux systems. The shell is the command line. Other UNIX systems may use other shells, but in the end they are all quite similar. You can use commands to create shell scripts which automate tasks or other things you may need to do.

2) SSH is a remote connection protocol. You can use it via commands or via a GUI program. Check out Filezilla for a graphical version of SSH. I recommend you learn the commands first, though. This is a very easy thing to learn once you get the concepts.

3) Linux uses the GNU Compiler Collection (GCC) for compiling. You can also use Makefiles, etc.

UNIX and Linux are not the same, but Linux is largely replacing traditional UNIX systems right now. Linux was meant to be a free clone of the proprietary and expensive UNIX systems. Nowadays, Linux is the OS of choice for servers with something like 70% of servers running it. 

I recommend you learn about Red Hat Enterprise Linux and Oracle's Solaris systems. RHEL and RHEL-based systems are commonplace on servers, and Solaris is a "true UNIX" system which still has a decent following. 

I also suggest you install Virtualbox on your Windows partition so you can play around with Linux without worrying about messing anything up. 

Have fun :)

---

### Post by weeman1 on 2011-09-06
So are the commands for Linux/Unix are the same?

---

### Post by haqking on 2011-09-06
> **weeman1 said:**
> So are the commands for Linux/Unix are the same?


Most of the main system commands are the same.

There are some differences, as there is across some distros. But not enough to worry about, any new system you would deal with you can soon pick up the differences.

this sums things up [http://www.cyberciti.biz/faq/what-is-the-difference-between-linux-and-unix/](http://www.cyberciti.biz/faq/what-is-the-difference-between-linux-and-unix/)

---

### Post by kaldor on 2011-09-06
> **weeman1 said:**
> So are the commands for Linux/Unix are the same?

Mostly. I use BSD, OS X, and Linux on a regular basis and for the most common bits they are the same.

---

