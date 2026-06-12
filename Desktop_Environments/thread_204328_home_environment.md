---
title: "home environment"
date: 2006-06-26
forum: Desktop Environments
---

### Post by owen_cook on 2006-06-26
xubuntu
owen@ubuntu:~$ uname -r
2.6.15-25-386


This is the part of the .bash_profile file for a user;

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

This is my bin directory;

owen@ubuntu:~$ ls -la bin
total 136
drwxr-xr-x  2 owen owen  4096 2006-06-19 16:26 .
drwxr-xr-x 47 owen owen  4096 2006-06-27 10:53 ..
-rwxr-xr-x  1 owen owen 86407 2006-06-19 16:25 mksquashfs
-rwxr-xr-x  1 owen owen    15 2006-06-19 13:26 tip
-rwxr-xr-x  1 owen owen 31172 2006-06-19 16:26 unsquashfs
owen@ubuntu:~$

This is what happens when I try to run a command;

owen@ubuntu:~$ mksquashfs
bash: mksquashfs: command not found
owen@ubuntu:~$

Now when I export the path;
owen@ubuntu:~$ export PATH=/home/owen/bin:$PATH
owen@ubuntu:~$ mksquashfs
SYNTAX:mksquashfs source1 source2 ...  dest [options] [-e list of exclude
dirs/files]


Would be grateful for any clues as to why the .bash_profile is not setting the home bin directory.


TIA or apologies if it has been asked before.(I can't find the answer)


Owen

---

### Post by taurus on 2006-06-26
Edit ~/.bashrc and add the following two lines to the end of it.
```

PATH=$PATH:~/bin
export PATH

```
Then, either log out and back in again or run this command at a prompt.
```

source ~/.bashrc

```

---

