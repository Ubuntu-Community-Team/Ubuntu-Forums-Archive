---
title: "How to run a script on logout?"
date: 2006-03-19
forum: Desktop Environments
---

### Post by mmcmonster on 2006-03-19
Is there a simple way to run a script every time a particular user logs out?

I already have the particular script written.  I just need it to run whenever a particular individual logs out.  Basically I want to make sure any files he adds to a particular directory are readable/writeable by everyone else (it's a shared Photo directory).

---

### Post by art on 2006-03-19
Put them $HOME/.bash_logout

---

### Post by mmcmonster on 2006-04-08
That doesn't seem to work.

I basically want to create a shared directory, in which people can edit each others work without any problems.  I added the execute bit to the chmod so that any directories can be traversed by everyone (I don't know a better way :-( ).

Here is the contents of my ~/.bash_logout file:
```

chmod -R a+rwx /home/shared/
touch /home/shared/.last_logged_in

```

Anyway, the script should create the file /home/shared/.last_logged_in, but it doesn't.  I guess that's a good enough proof that the script doesn't ever run.  (/home/shared is a+rwx, by the way)

---

### Post by mmcmonster on 2006-04-13
Any ideas?  This is starting to bug me. :-(

---

### Post by Ramses de Norre on 2006-04-13
Did you make the .bash_logout file executable too?

---

### Post by mmcmonster on 2006-04-14
I just checked, and the .bash_logout file is a+rx.  It still doesn't work.

I tried doing a ". .bash_logout", to make sure the script runs, and that isn't the problem (It runs fine when called explicitly).

Any other ideas?  Anyone manage to get .bash_logout to run?

(I can't even get it to run when closing a terminal window. :-( )

---

### Post by mmcmonster on 2006-04-17
Just to reiterate: Can anyone confirm that their ~/.bash_logout file gets executed on logout?

---

### Post by jrib on 2006-04-17
man bash:
```
When  a  login  shell  exits, bash reads and executes commands from the file ~/.bash_logout, if it exists.
```

So it only gets executed for login shells.  I assume you want to perform an action everytime you logout of gnome instead.

I don't know how to do this, but some googling turned up this:
[http://archive.lug.boulder.co.us/Week-of-Mon-20001030/006266.html](http://archive.lug.boulder.co.us/Week-of-Mon-20001030/006266.html)
[http://mail.gnome.org/archives/desktop-devel-list/2003-October/msg00360.html](http://mail.gnome.org/archives/desktop-devel-list/2003-October/msg00360.html)

I read the first thread through and it didn't seem to work for the user, the second one was a bit long... Hope that works for you

---

### Post by panki on 2006-12-12
did you guys managed to get this working?

---

### Post by budhe888 on 2007-05-27
Not sure if you guys have resolved this yet, but I was able to get a gnome logout script to work by placing my commands in

```

/etc/gdm/PostSession/Default

```

Hope this helps.

---

### Post by maxmundus on 2008-07-07
I think it would be right to add the following line to /etc/gdm/PostSession/Default :

$HOME/.bash_logout

This will make script to execute .bash_logout , that is different and customizible
for each user ;)

This works for me.

P.S Hope this will be added native in the next Ubuntu release.

---

