---
title: "Could someone explain the $PATH to me, please."
date: 2009-04-11
forum: General Help
---

### Post by aaronLund on 2009-04-11
Howdy.

Just installing komodo edit and they mention that I should make sure to "add komodo to your path".

First, what exactly is this "$PATH"?  

Also, if I type "komodo" at the command line (while in my home directory), I'm getting a:
```
bash: komodo: command not found

```

However, if I type "./komodo", it starts fine.

Part of the reason I'm asking is that my komodo icon is gone and I don't have the foggiest idea of how to get it back.  I'd like to just put it in my panel with all of my other apps.  

Is this $PATH thing related to the "Open this with......." option when you right click on a file?  

I ask because sometimes, the app I want is not in that list and I'd like it to be.

Thanks for any advice.

---

### Post by James_Lochhead on 2009-04-11
The $PATH variable points at services, making commands work. For example, if I enter a java path into $PATH it will allow me to use the service that the java points to for the java command.

If you create a symbolic link (lets call it "komodo") in your bin directory that points at whatever launches Komodo you can make a launcher and type "komodo" in the command field, this will allow you to launch the program from the desktop/panel/whatever.

---

### Post by AKviking on 2009-04-11
Here's some more help on $path if you need.
[http://www.faqs.org/docs/Linux-mini/Path.html#s3](http://www.faqs.org/docs/Linux-mini/Path.html#s3)

Otherwise you can try [this]("http://lmgtfy.com/?q=%24path+in+linux").

---

### Post by tommcd on 2009-04-11
Your PATH lists the directories that you can run commands from as a regular user. To see what is in your PATH run in terminal:
```
echo $PATH
```
On my system it returns:
```
tom@ubuntu:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```
To add another directory to your PATH you can edit ~/.bashrc. See post #4 in this thread:
[http://ubuntuforums.org/showthread.php?t=269793](http://ubuntuforums.org/showthread.php?t=269793)

---

### Post by martin_prior on 2009-04-11
As the previous reply states if you type: echo $PATH, your current PATH will be displayed. Your PATH is just a list of the directories that wil be searched to find the program you typed at the command line. In your case komodo.

The fact that typing ./komodo works means that you are currently in the directory where komodo is installed. So type: pwd<return/enter> and your current directory will be displayed. 

for example: pwd
             /home/fred/bin (so therefore komodo is installed in that directory.

To add it to your search PATH type: export PATH=$PATH:/usr/fred/bin:
now type "komodo" and it should be found.

Now you know where komodo is. Right click on the Desktop and select "create launcher". Fill in the boxes: Name is Komodo, command is /usr/fred/bin/komodo, comment is whatever you like, game, word processor ....

Hope that helps

Martin W Prior

---

### Post by aaronLund on 2009-04-11
Thanks, amigos.  All's well now!

---

### Post by defaultusername on 2009-04-11
aaronLund,

PATH is a member of the group of environmental variables. Environmental variables and their values give information about the execution environment. To see a complete list, use "env." To modify values, use "export PATH=x" where x is a colon-separated list of directories. For example, on my system,

> 
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games


If you want a script/binary to execute without typing the full path, make sure your PATH variable is correct.

---

