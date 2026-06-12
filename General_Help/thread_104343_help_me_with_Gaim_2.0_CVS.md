---
title: "help me with Gaim 2.0 CVS"
date: 2005-12-15
forum: General Help
---

### Post by ubuntu27 on 2005-12-15
Hello guys and girls !!

I been follwing this guide/How-to to install Gaim 2.0 

[http://ubuntuforums.org/showthread.php?t=100899](http://ubuntuforums.org/showthread.php?t=100899)

Hey guys, I've been following this How-to.
And well, I am stack at step one:

```
ubuntu27@heaven:~$ cvs -d ':pserver:anonymous@cvs.sourceforge.net:/cvsroot/gaim' login
bash: cvs: command not found

```

What should I do now? 
It's says CVS command not found ::(

I want to have Gaim 2.0 because Christmas is coming and I will need to use webcam ans stuff.

---

### Post by RAOF on 2005-12-15
You need to get the cvs program.  Just run in a console
```
sudo apt-get install cvs
``` and you're away.

---

### Post by ubuntu27 on 2005-12-15
Thank you RAOF :)

now another problem :( 

In the How-To it says:

Run the following commands in a directory that you have write access to (such as your home directory):

```
cvs -d ':pserver:anonymous@cvs.sourceforge.net:/cvsroot/gaim' login
(Just hit enter for the password)
```

And I got this:

```
ubuntu27@heaven:~$ cvs -d ':pserver:anonymous@cvs.sourceforge.net:/cvsroot/gaim' login
Logging in to :pserver:anonymous@cvs.sourceforge.net:2401/cvsroot/gaim
CVS password:
cvs [login aborted]: end of file from server (consult above messages if any)

```

I hit enter without writting anythign when asked about password. And it says that it was aborted. What to do? Did they (Gaim group) created a password now?

---

### Post by RAOF on 2005-12-15
That looks like a connection-type error.  Maybe too many people are trying to get the CVS :)

I'd just try the same thing again, after waiting a while.

---

### Post by ubuntu27 on 2005-12-17
[QUOTE=RAOF]That looks like a connection-type error.  Maybe too many people are trying to get the CVS :)

I'd just try the same thing again, after waiting a while.[/QUOTE]

Thank you!
Now I've installed without anyt problems :)

Now my last question (I hope):
Is the Gaim 2.0 BETA the same as Gaim 2.0 CVS ?

---

