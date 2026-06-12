---
title: "$path"
date: 2005-07-15
forum: Desktop Environments
---

### Post by newbie_ubuntu on 2005-07-15
Hi,

I see that currently I have to run executable programs by prefixing them with a ./   
Can someone tell me why this is done?

Also I want to be able to run programs from other folders. I assume that adding them to the $path should help. But the .bashrc file in the root folder doesnt have a $path variable, How do I add it. Please tell me the exact text string that has to be added.

Also, I fail to see the .bash_profile file. Where is this file located on the system?

Thanks,

---

### Post by TheOtherShoe on 2005-07-15
I would guess that the current directory is not in the path by default for security reasons, although I don't know exactly what reasons those are.

The line you want in your .bashrc to change the path is,
```
export PATH=$PATH:/list/of/directories:/seperated/by:~/colons
```
As an example, to include the current directory in the path the line in .bashrc would be,
```
export PATH=$PATH:./
```
Make sure to include $PATH somewhere on the right side of the equals sign or you will replace the list of searched directories instead of adding to it.

And if you want to use .bash_profile, copy it from /etc/skel/.bash_profile to your home directory.

---

### Post by Mike Buksas on 2005-07-15
[QUOTE=TheOtherShoe]I would guess that the current directory is not in the path by default for security reasons, although I don't know exactly what reasons those are.
[/QUOTE]

Having the current directory in the path exposes you to exploits where a common command like 'ls' is subsistuted with a malicious version in the current directory, typically a home directory. So you fire up an xterm, run 'ls' or 'pwd' or whatever, you get the malicious version and something bad happens.

I don't know how serious this exploit is in the grand scheme of things though, since it reqiures an attacter to have enough access to put stuff in your home directory, or to fool a user into installing something there. After awhile, you learn to start typing ./ without even thinking about it, so I've always left it out.

Cheers.

---

### Post by newbie_ubuntu on 2005-07-15
I really dont mind typind the ./ each time.
But say I am in folder with path1, and need to run another program from path2, how do I go about it?

I dont know if the question is framed well enough, but I hope you understood.

Thanks.

---

### Post by TheOtherShoe on 2005-07-15
If you don't mind doing so you can type out the full path of the other program. For example if you want to run /usr/local/bin/sample_prog but /usr/local/bin is not set in your $PATH variable, then you can type,
```
/usr/local/bin/sample_prog
```

---

### Post by Mike Buksas on 2005-07-15
[QUOTE=newbie_ubuntu]I really dont mind typind the ./ each time.
But say I am in folder with path1, and need to run another program from path2, how do I go about it?

I dont know if the question is framed well enough, but I hope you understood.

Thanks.[/QUOTE]

When the program you want to execute isn't in $PATH, you need to give the complete path of the program, instead of just the name of the program. For example, if you want to execute path2/some_code but you're not in path2 then the command invoaction is:

$ path2/some_code

Now paths can either be relative or absolute. Relative paths are "how to get there from here". Absolute paths are like addresses. The entries in $PATH, for example, are absolute paths. Note that they all start with '/'. (Absolute paths can also start with '~/' meaning "my home directory" or with "~user/" meaning "user's home directory".)

For example, you could use "/bin/ls" to run ls since that is it's full path, but you don't need to since "/bin" is in $PATH.

Now, relative paths have two short-cuts: '../' means the parent directory (up one level) and './' means "this directory".

So if you're in /usr you could also use "../bin/ls" to run ls. That means, "go up one level, go into bin and run ls". If you're in /bin you can just say "./ls". (But again, there's no need, since /bin is in $PATH).

So, when you put './' in front of a command, what's you're really doing is supplying the relative path to the command and using the './' shortcut to say "it's right here".

Hope this helps. Feel free to ask for clarification if it doesn't.

Mike

---

### Post by newbie_ubuntu on 2005-07-16
Hi all,
Thanks all of you for taking time and clearing my doubts.
Certainly was ver y helpful.
Thanks

---

