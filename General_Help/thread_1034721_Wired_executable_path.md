---
title: "Wired executable path"
date: 2009-01-09
forum: General Help
---

### Post by jackyang on 2009-01-09
I'm totally new to Ubuntu. May be this is a stupid question. please forgive me:)

I installed mysql in /usr/local/mysql. When I want to run mysql, I had to do:
```
cd /usr/local/mysql 
sudo bin/mysqld_safe --user=mysql &
```
This will success.
But when I do this:
```
cd /usr/local/mysql/bin
sudo mysqld_safe --user=mysql &
```
This will fail.
Why this happen? Can anyone explain to me?

---

### Post by mssever on 2009-01-09
> **jackyang said:**
> I'm totally new to Ubuntu. May be this is a stupid question. please forgive me:)

I installed mysql in /usr/local/mysql. When I want to run mysql, I had to do:
```
cd /usr/local/mysql 
sudo bin/mysqld_safe --user=mysql &
```This will success.
But when I do this:
```
cd /usr/local/mysql/bin
sudo mysqld_safe --user=mysql &
```This will fail.
Why this happen? Can anyone explain to me?
If you don't provide a directory component in a program name, the shell will search for an executable by that name in the directories listed in $PATH (type echo $PATH to see the current $PATH). By default, $PATH doesn't contain the current directory. If you provide a directory component (i.e., there's at least one slash in the name), then the $PATH search is skipped. So, this will work: ```
cd /usr/local/mysql/bin
sudo ./mysqld_safe --user=mysql &
```

EDIT: In case you didn't already know this, . refers to the current directory and .. refers to the parent directory.

---

### Post by hypotheses on 2009-01-09
To solve this, adding /usr/local/mysql/bin to $PATH will do the trick. 
I sometimes just create a symbolic link in /usr/bin pointing it to some other software installed in it's own directory

---

### Post by jackyang on 2009-01-09
> **mssever said:**
> If you don't provide a directory component in a program name, the shell will search for an executable by that name in the directories listed in $PATH (type echo $PATH to see the current $PATH). By default, $PATH doesn't contain the current directory. 

This makes a lot of sense. Thanks :)
So, I'm thinking about why ubuntu does not add a . in $PATH, which in my opinion is more practical.

---

### Post by mssever on 2009-01-09
> **jackyang said:**
> This makes a lot of sense. Thanks :)
So, I'm thinking about why ubuntu does not add a . in $PATH, which in my opinion is more practical.
I don't know the official reason, but I do know that there are security implications that make it unwise to put . in your $PATH.

First, consider the case where the dot is at the beginning. Suppose you're in some directory and you issue an ls to list the files in that directory. Now, suppose someone else has put an executable file in that directory named ls. You'll end up running their ls, not the ls you expected. And their ls could do who knows what. Plus, there's a convenience issue: You could inadvertently cover up a command.

If you put the dot at the end of your $PATH, that's much better since executables in the current directory won't ever cover up anything in any other part of the $PATH. But there's still a potential issue. Suppose you type sl by mistake, instead of ls. You could again be vulnerable.

In my opinion, the best policy is to only have the directories where you expect to find executables in your $PATH so that you can ensure that random stuff doesn't get crammed into those directories. For exceptional cases, either give the path to the executable, or create a symlink to it somewhere on your $PATH (such as in /usr/local/bin). I also maintain a directory below my home directory for various executables I create (I call mine $HOME/bin), and I place it at the front of my $PATH so that if I want to override something I can.

Keep in mind, too, that if a package installs an executable that's not on the default $PATH, then the developers or packagers didn't intend for that executable to be run directly for some reason. Maybe there's a wrapper you should run, instead. Read the documentation before circumventing the packaging.

EDIT: By the way, I just re-read your initial post, and I was wondering why this issue came up in the first place. If you had installed MySQL the official way (through Synaptic, or using sudo aptitude install mysql, etc.), then everything would be properly placed on your $PATH for you. Generally it's best to use packaged versions of software when possible. Of course, it's possible that you have a good reason for installing MySQL the way you did. If so, then feel free to ignore this advice, provided you made an informed decision when you installed it.

---

### Post by jackyang on 2009-01-09
Thanks so much for these information. Actually I just want to read some mysql source code and I'm trying to work on this code to develop my project. So I used the source code to install it. 
Indeed, you're right about the security issue about adding . in the $PATH. I used to work on Windows and be more used to the Windows way of doing things. But I had to admit that it is because of these security considerations that Linux gains more advantages in defending from virus or other threats.

Today I found another interesting thing. After I added path "/usr/local/mysql/bin" into my /etc/environment, execute mysqld_safe will fail because of permission denied. But when I execute "sudo mysqld_safe" it will say command not found. I think may be this because when I use sudo shell will look for command in root's PATH, not mine. Is this right? Where can I add my path to root user's PATH?

---

### Post by mssever on 2009-01-09
> **jackyang said:**
> Indeed, you're right about the security issue about adding . in the $PATH. I used to work on Windows and be more used to the Windows way of doing things.Actually, Windows puts even less in the PATH than Linux does. And many programs are quite sensitive to the current directory, forcing you to cd to the program's directory before running it.

> Today I found another interesting thing. After I added path "/usr/local/mysql/bin" into my /etc/environment, execute mysqld_safe will fail because of permission denied. But when I execute "sudo mysqld_safe" it will say command not found. I think may be this because when I use sudo shell will look for command in root's PATH, not mine. Is this right? Where can I add my path to root user's PATH?
Adding the path to /etc/environment should work, provided that you logout and back in to commit the change. But it's not the best way to do that. It's better to edit your ~/.bashrc and put your $PATH modifications in there. That way, they only apply to you. sudo copies your PATH to root whenever it's needed. I have the following code in my ~/.bashrc, which you can modify as needed:
```
if [[ $PATH =~ $HOME/bin ]]; then : # : is a no-op in bash, equivalent to Python's pass
else export PATH="$HOME/bin:$PATH"
fi
```

You can test your $PATH thus:
```
. ~/.bashrc   # source .bashrc to pick up the changes
echo $PATH
sudo echo $PATH
```

---

### Post by jackyang on 2009-01-09
Thanks!
Although you are right that windows put even less in PATH, but actually in command line, windows will look for a command first in the current folder. I thought this would be an security issue.

Yes, I searched a lot on topic "add environment variable to path", and found there's many ways. I thought the "/etc/environment" way is more Ubuntu style, because it's only appear in Ubuntu. Why add it to ~/.bashrc will be better? Is there a difference?

I just found that after you have set up mysql startup script successfully in init.d, the script will add its bin folder to PATH for you. There's no need to add it yourself :)

---

### Post by mssever on 2009-01-09
> **jackyang said:**
> Yes, I searched a lot on topic "add environment variable to path", and found there's many ways. I thought the "/etc/environment" way is more Ubuntu style, because it's only appear in Ubuntu. Why add it to ~/.bashrc will be better? Is there a difference?/etc/environment applies to every user on the system. .bashrc applies to the current user and overrides system-wide settings. So unless you specifically want to make system-wide settings, it's best to put stuff in ~/.bashrc.

> I just found that after you have set up mysql startup script successfully in init.d, the script will add its bin folder to PATH for you. There's no need to add it yourself :)
I meant to ask earlier: given that you were working with /usr/local/mysql/bin, does that mean that you used /usr/local/bin as the --prefix argument to ./configure? When specifying the prefix, don't include the program name. Just give /usr/local or whatever. Also, did you run make install before starting to muck about? I'm asking because the installation process should automatically place the executable in your PATH if you set the prefix right.

---

### Post by jackyang on 2009-01-10
> /etc/environment applies to every user on the system. .bashrc applies to the current user and overrides system-wide settings. So unless you specifically want to make system-wide settings, it's best to put stuff in ~/.bashrc.
Thanks. Yes, this makes sense.
> I meant to ask earlier: given that you were working with /usr/local/mysql/bin, does that mean that you used /usr/local/bin as the --prefix argument to ./configure? When specifying the prefix, don't include the program name. Just give /usr/local or whatever. Also, did you run make install before starting to muck about? I'm asking because the installation process should automatically place the executable in your PATH if you set the prefix right.
No, I installed it in my home folder and create a symbolic link mysql in /usr/local. This folder is recommended by mysql's document as a default folder in its startup script. Yes, I ran make install. But I did not place executable in my PATH. I think it only add it in its startup script I think it's a much safer solution.

---

