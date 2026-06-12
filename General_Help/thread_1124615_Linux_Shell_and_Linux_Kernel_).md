---
title: "Linux Shell and Linux Kernel :)"
date: 2009-04-13
forum: General Help
---

### Post by JCC_0863668 on 2009-04-13
Hello my friends it's me again :)

I wanna ask about the relationship between Linux Shell and Linux Kernel ? 

And I want to know the most important basic commands about Linux Ubuntu ? 

Thank You Soo Much :).

---

### Post by Bakon Jarser on 2009-04-13
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php) is a great place to start with the command line.  Have fun;)

---

### Post by brunogirin on 2009-04-13
The Linux Kernel is the core piece of software that orchestrates the way the Ubuntu operating system works: it manages processes and hardware devices, allocate processor time to each process, etc.

There is no real such thing as the Linux Shell. Rather there are a number of "shell" programs, such as bash, ksh, csh (you'll notice they all end up in 'sh'). A shell is run when you open a terminal window and allows you to interact with the operating system using a command line interface. By default, Ubuntu will run the shell program called bash. What commands are important will depend on what you intend to do. However, I would suggest you start by getting familiar with the man command as it will enable you to get detailed information on any command; then the basic file system traversal ones such as: cd, ls, pwd; then try some simple file manipulation ones such as: cp, mv, mkdir, rm (careful, this one can be dangerous!); I would also suggest having a look at commands such as: cat, echo, grep, head, tail, less. However, what makes the shell extremely powerful is the ability to pipe or redirect commands so try to get familiar with special characters such as > < >> |.

---

### Post by Aubergines on 2009-04-13
**I wanna ask about the relationship between Linux Shell and Linux Kernel?**

Simplicity the shell acts as a translator between human language you type in and machine language that the kernel understands and vice versa. The shell in Linux is the commandline interface (CLI) whereas in Windows you can think of the shell as the desktop.

Here's a picture

[img]http://files.opensuse.org/opensuse/en/e/e2/Flow1.jpg[/img]

**And I want to know the most important basic commands about Linux Ubuntu?**

Hmm, I guess the most important commands would be the basic ones required to operate the OS or everything in the package [coreutils](http://packages.ubuntu.com/intrepid/coreutils) :D The easiest way to learn is simply to move around. Lucky for me I was comfortable with MSDOS and just grabbed a [DOS to Linux equivalent commands table](http://www.faqs.org/docs/linux_intro/app2.html).

*Edit: Bakon Jarser's link above is pretty good*

---

### Post by zvacet on 2009-04-13
It will be good that you look at the link Bakon Jarser adviced.When you feel comfortable you can look these too

[http://www.linuxcmd.org/en/linux_commands_line.php?MenuShow=AllCmd]("http://www.linuxcmd.org/en/linux_commands_line.php?MenuShow=AllCmd")

[http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/]("http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/")

[http://www.oreillynet.com/linux/cmd/]("http://www.oreillynet.com/linux/cmd/")

---

