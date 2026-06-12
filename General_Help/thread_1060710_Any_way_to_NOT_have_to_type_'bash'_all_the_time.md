---
title: "Any way to NOT have to type 'bash' all the time??"
date: 2009-02-05
forum: General Help
---

### Post by bigasif on 2009-02-05
Hi,
I just recently installed Ubuntu (and I'm loving it) but I have a question. Basically, I do a lot of programming (normally done on campus on RedHat computers) and when I was only using vista/xp, I would simply remotely log in to work on everything, but since I've installed ubuntu, I've decided to make things a bit more interesting.

Anyways, what I wanted to do was add a folder to the PATH so that anytime a command name was typed, the executable would be located. What I did was add the following line to the ~/.bashrc file:

export PATH=${HOME}/bin:${PATH}

So I have the executable that I want in a bin folder in my home drive. Anyways, it works fine, but only when I type 'bash' once I open a terminal.

What I want to know is PREFERABLY, is there any way to add this to the default terminal shell environment, instead of bash? I thought that there was a file called .cshrc for the tcsh shell (as we have on our campus labs) and thought I just had to add 'setenv PATH ${HOME}/bin:${PATH}' to the file, and it would work instantly without the need to type anything into the terminal when I open it.

Unfortunately, I couldn't located that file, even after installing tcsh, so I went with the bash route. So if there's NO way to basically modify the default path, is there any way I can set the bash environment as the default when I open terminal so that I don't always have to type 'bash' first?

Not sure if my questions are clear, so if you need clarification, just post back and I'll do my best to explain better. Thanks in advance!

Cheers,
BiGaSiF

---

### Post by jerome1232 on 2009-02-05
Well what I do know is that ~/bin is in your path by default in Ubuntu. I have made zero modifications to my path. My user's name is jeremy.

```
echo $PATH
[COLOR="Blue"]/home/jeremy/bin[/COLOR]:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

--edit-- I take that back it seems to be only true on my installs with a gui :oops:

---

### Post by mcduck on 2009-02-05
Bash _is_ the default shell. and, like the name suggests, .bashrc is configuration file for Bash. And like jerome said, ~/bin is in the path by default, you just need to log out and back again after you create that directory before it works.

If you want to use some other shell, you need to make your changes in that shell's configuration files. I believe tcsh uses ~/.cshrc as it's configuration file. If one doesn't exist, create it yourself.

---

### Post by hockey9876 on 2009-02-05
Can't you just go into the admin --> users & groups and
change your default shell?

---

### Post by jerome1232 on 2009-02-05
> **mcduck said:**
> Bash _is_ the default shell. and, like the name suggests, .bashrc is configuration file for Bash. And like jerome said, ~/bin is in the path by default, you just need to log out and back again after you create that directory before it works.

If you want to use some other shell, you need to make your changes in that shell's configuration files. I believe tcsh uses ~/.cshrc as it's configuration file. If one doesn't exist, create it yourself.

Not to get picky but isn't dash the default shell? (I don't know what the difference's of dash vs bash are I'm sure they are very similiar)

```
ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2008-12-31 10:26 /bin/sh -> dash

```

---

### Post by whitegourd on 2009-02-05
I would just ...

vi /etc/passwd ... grep the username and modify the /bin/bash to /bin/dash ... and :wq

---

### Post by mcduck on 2009-02-05
> **jerome1232 said:**
> Not to get picky but isn't dash the default shell? (I don't know what the difference's of dash vs bash are I'm sure they are very similiar)

```
ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2008-12-31 10:26 /bin/sh -> dash

```

Dash is the default shell for system itself, but Bash is used as user login shell by default.
```

mcduck@hyperion:~$ echo $SHELL
/bin/bash
```

---

### Post by Slim Odds on 2009-02-05
~/bin is **NOT** in the PATH by default. Why would it be? That directory does not even exist by default.

the default **interactive **shell is bash
the default "command interpreter" is sh which is a symlink to dash

I'd still like to know why you have to type "bash" at all.

---

### Post by mcduck on 2009-02-05
> **Slim Odds said:**
> ~/bin is **NOT** in the PATH by default. Why would it be? That directory does not even exist by default.

the default **interactive **shell is bash
the default "command interpreter" is sh which is a symlink to dash

I'd still like to know why you have to type "bash" at all.

Yes, it is. Just try it yourself. Create the directory, log out and back again and it will work. Or take a look in ~/.profile, which adds ~/bin to path if the directory exists.

---

### Post by Slim Odds on 2009-02-05
> **mcduck said:**
> Yes, it is. Just try it yourself. Create the directory, log out and back again and it will work. Or take a look in ~/.profile, which adds ~/bin to path if the directory exists.

Ok, but like I said, it does not exist by default.

---

### Post by jerome1232 on 2009-02-05
> **Slim Odds said:**
> Ok, but like I said, it does not exist by default.

That explains why it's not in the path for my other system, ~/bin doesn't exist for the user I checked on. I created the folder and re-ssh'd in and it was in the path.

I guess I should've rephrased my answer to that it is in the path by default if ~/bin exists.

> Dash is the default shell for system itself, but Bash is used as user login shell by default.

Thanks for clarifying that for me I was getting confused as to whether it was dash or bash :)

---

### Post by maybeway36 on 2009-02-06
With so many startup files it gets confusing :)

---

