---
title: "Can't acces to &quot;/home/myfolder/&quot; through the terminal"
date: 2007-05-09
forum: Desktop Environments
---

### Post by pacsum on 2007-05-09
I can't acces my folder with the terminal so I can't install files, what can it be?? :(

---

### Post by heimo on 2007-05-09
> **pacsum said:**
> I can't acces my folder with the terminal so I can't install files, what can it be?? :(

Could you be more specific, what command fails and what does it say?

---

### Post by Lord Illidan on 2007-05-09
You can't access your home directory, you mean?

Your home directory is /home/<your username>

for instance, mine is /home/jean

Then, if you have a folder called myfolder, it will be in /home/jean/myfolder

You can also use ~/myfolder . The tilde (~) refers to your home directory.

---

### Post by taurus on 2007-05-09
If you download something with firefox, changes are it would be saved to ~/Desktop.

```
cd ~/Desktop
ls -la
```

---

### Post by pacsum on 2007-05-09
> **Lord Illidan said:**
> You can't access your home directory, you mean?

Your home directory is /home/<your username>

for instance, mine is /home/jean

That's the one, mine is /home/pacsum but i can't access it through
 the terminal.

---

### Post by heimo on 2007-05-09
> **pacsum said:**
> That's the one, mine is /home/pacsum but i can't access it through
 the terminal.

Please try to explain in detail how you're trying to access it, and if there's any warnings or errors.

---

### Post by Lord Illidan on 2007-05-09
Any error provided?

---

### Post by EndPerform on 2007-05-09
> **pacsum said:**
> That's the one, mine is /home/pacsum but i can't access it through
 the terminal.

When you bring up the terminal, by default you are sitting in your home directory.  Does the terminal give an error, or do you seem something like:

pacsum@hostname:~

If you see the above, you're in your home directory already.

---

### Post by pacsum on 2007-05-09
when I type **cd /home/pacsum** it doesn't access the folder it just returns again to **<username@username-desktop:** then I try **cd /home** it accesses the home folder **pacsum@pacsum-desktop:/home$** then I type cd /pacsum and it throws me this **bash: cd: /pacsum: No such file or directory**

---

### Post by heimo on 2007-05-09
> **pacsum said:**
> when I type **cd /home/pacsum** it doesn't access the folder it just returns again to **<username@username-desktop:** then I try **cd /home** it accesses the home folder **pacsum@pacsum-desktop:/home$** then I type cd /pacsum and it throws me this **bash: cd: /pacsum: No such file or directory**

Well. Type just
```
cd
```

Now you're in your home directory. Most probably /pacsum doesn't exist, your home directory is under /home/. / stands for "root" of the file system. You'd need to enter "cd pacsum" without / if you're already in /home.

---

### Post by pacsum on 2007-05-09
LOL... well nice to know that. I didn't knew about that, all the time I was on my <username> folder, now let's see if I can install yumex, thanks.

---

### Post by Lord Illidan on 2007-05-09
> **pacsum said:**
> when I type **cd /home/pacsum** it doesn't access the folder it just returns again to **<username@username-desktop:** then I try **cd /home** it accesses the home folder **pacsum@pacsum-desktop:/home$** then I type cd /pacsum and it throws me this **bash: cd: /pacsum: No such file or directory**

You are entering the wrong commands.

The root directory in Linux is the / directory.
The home directory is a subdirectory of it. So, it will be in /home
Your userdirectory is a subdir of /home. So it will be in /home/pacsum

Thus if you go to /home, then you have to type cd pacsum.

the ```
ls
``` command will also show you the contents of a directory.

This site may be useful : [http://www.linux-tutorial.info/](http://www.linux-tutorial.info/)

---

### Post by heimo on 2007-05-09
Let's also add Kyral's [terminal for beginners]("http://ubuntuforums.org/showthread.php?t=73885").

---

### Post by EndPerform on 2007-05-10
Another handy command is **pwd**, which will show you the current directory you are in.

---

