---
title: "Installing application location"
date: 2007-05-19
forum: Desktop Environments
---

### Post by penkie on 2007-05-19
I want to install a custom application. What would be a good location to install it to? So what would be typically the linux variant to window's "program files"? Of course I could install it anywhere I like, but I would like to know what would be a typical place to do it in "the spirit" of Linux.

The program defaults to "/home/user/", however if I look around I also see quite some programs installed in "/usr/lib", What do you think?

-edit- oops, I actually meant to post this question in the beginners forum.I don't see how to move the thread, so maybe you guys can help?

---

### Post by RedSquirrel on 2007-05-19
"program files" on linux is often /usr/bin or /usr/local/bin. Sometimes /opt is used for custom applications.

I would install it under your home directory. That's a safe way to do it. ;)

---

### Post by aysiu on 2007-05-19
I'd use /opt or /usr/local/bin

---

### Post by RedSquirrel on 2007-05-19
> **aysiu said:**
> I'd use /opt or /usr/local/bin

The nice thing about putting it somewhere under your home directory is that you don't need root permissions for that, but you do if you use /opt or /usr/local/bin.

---

### Post by aysiu on 2007-05-19
> **RedSquirrel said:**
> The nice thing about putting it somewhere under your home directory is that you don't need root permissions for that, but you do if you use /opt or /usr/local/bin.
Well, you'll need root permissions (a simple *gksudo nautilus* suffices) to put the files in /opt or /usr/local/bin, but once they're in there, any user should be able to execute the program.

---

### Post by RedSquirrel on 2007-05-19
> **aysiu said:**
> Well, you'll need root permissions (a simple *gksudo nautilus* suffices) to put the files in /opt or /usr/local/bin, but once they're in there, any user should be able to execute the program.


In the case of an installer program (not just copying files manually), you would have to run the installer with sudo (or gksudo) to have it place files in /opt or /usr/local/bin, which may not be safe if you don't know what the installer is going to do. Just my $0.02.

---

### Post by aysiu on 2007-05-19
I don't see why it wouldn't be safe.

---

### Post by RedSquirrel on 2007-05-19
What else is the installer going to do to your system once you give it root permissions? Maybe I'm being paranoid, but when I can get away with not running sudo, I will.

---

### Post by aysiu on 2007-05-19
> **RedSquirrel said:**
> What else is the installer going to do to your system once you give it root permissions? Maybe I'm being paranoid, but when I can get away with not running sudo, I will.
Well, my take on it is: if you don't trust the application, don't use the application.

---

### Post by RedSquirrel on 2007-05-19
> **aysiu said:**
> Well, my take on it is: if you don't trust the application, don't use the application.

That's a reasonable policy. It does, however, deal in absolutes: you either trust the application or you don't. If I trust the application *partially*, then I can try to install it in such a way as to minimize its effects.

---

### Post by aysiu on 2007-05-19
> **RedSquirrel said:**
> That's a reasonable policy. It does, however, deal in absolutes: you either trust the application or you don't. If I trust the application *partially*, then I can try to install it in such a way as to minimize its effects.
What you're saying makes sense in theory, but in practice I haven't come across any applications I trust only partially--it's either fully or not at all.

---

### Post by penkie on 2007-05-20
Quite some discussion here. :D

For me as an ex-windows user going from logging in as an root/admistrator all to time to using sudo/kdesu is already quite a big step. ;)
And even in windows I personally never really encountered problematic behavior of software by mainly not installing or running everything, but think first before clicking on anything (and monitor my running processes and using a firewall all the time). 

Thanks a lot for all your recommendations, I will use them!

---

