---
title: "Unable to run any administrative tool"
date: 2007-01-23
forum: Desktop Environments
---

### Post by bprof on 2007-01-23
Hi,

I've just installed Ubuntu, had a little hard time but managed to make it work. My problem is that whenever I try to run any administrative tool for instance Networking, I got a message saying user doesn't have privilege to do this task.

I've read that:

> 
All of the default graphical configuration tools in Ubuntu already use sudo, so they will prompt you for your password if needed. 

But I'm an unable to do that. Can anyone please help me with this problem?

I'm using the latest version of Ubuntu, this the first time I use Ubuntu.

Thanks,

---

### Post by ComplexNumber on 2007-01-23
> whenever I try to run any administrative toolfirstly, what sort of administrative tools are you wanting to use (what are their names)?

btw if you are using *graphical* applications, use gksudo(not sudo).

---

### Post by bprof on 2007-01-23
Thanks for the prompt reply.

> firstly, what sort of administrative tools are you wanting to use (what are their names)?

I'm trying to configure my wireless settings.

> btw if you are using graphical applications, use gksudo(not sudo).

Is there a list that I can refer to in regard to the name of graphical applications mainly network configuration, and users.

i.e gksudo application_name

Thanks so much for the help,

---

### Post by ComplexNumber on 2007-01-23
> Is there a list that I can refer to in regard to the name of graphical applications mainly network configuration, and users.if, when you run it from the commandline, a graphical user interface pops up, use gksudo for it. for example, nautilus, gedit, a calculator, a media player, a painting program, etc etc.


> I'm trying to configure my wireless settings.what command(s) did you type into the commandline that the system tells you you don't have the correct privilages for?

---

### Post by bprof on 2007-01-23
> what command(s) did you type into the commandline that the system tells you you don't have the correct privilages for?

It wasn't a command, it was an icon (Networking) from the graphical menu.

Thanks again for your help,

---

### Post by ComplexNumber on 2007-01-23
ok. i'm confused. so what exactly did you you try where it claimed that you didn't have the right privilages?

---

### Post by bprof on 2007-01-23
After logging in using the user that was created during the installation. I tried to change the settings on of my network so I went to:

System-->Administration-->Networking

It gave me this message:

The configuration could not be loaded

You are not allowed to access the system configuration.


So how can I run any graphical application from the System-->Administration list?

Please help me,

---

### Post by ComplexNumber on 2007-01-23
seems odd. works for me. when i first click on 'networking' form the menu, it just loaded it up. i added and deleted a search demain as a test, and it didn't ask for a password.

the program is called 'network-admin'. run that on the commandline, but don't prefix it with "gksudo".

---

