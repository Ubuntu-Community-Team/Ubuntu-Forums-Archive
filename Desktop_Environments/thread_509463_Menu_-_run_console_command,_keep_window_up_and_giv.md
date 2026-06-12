---
title: "Menu - run console command, keep window up and give terminal input"
date: 2007-07-25
forum: Desktop Environments
---

### Post by ragecyr on 2007-07-25
so my example will be Backtrack... (even though its KDE)
when you select a program from the menu, say nmap it opens the terminal and does nmap --help.
prints the parameters and then gives you the prompt.  The KDE menu editor says it does this via nmap;sudo -s


now to gnome and ubuntu

i want to run a command line program, but NOT HAVE THE WINDOW CLOSE, and get a prompt at the end. so like
applications>custom>nmap
(pops up a terminal)
nmap v#.#
-h    this help command
-v    version
-p    ports

me@mybox:~#



as of now if you just do 'application in terminal' and command of 'nmap' once it runs nmap, it closes the window.  you can set terminal to not close after it runs a command, but then you dont get a terminal at the end its just a useless box.  
I have tried
nmap;sudo -s     (There was an error creating the child process for this terminal)
nmap; sudo -s    (see above)
gnome-terminal -e 'nmap' (just closes the window when done)
nmap & (runs command then closes window)



anyone know how to do this?

---

### Post by ragecyr on 2007-07-30
bump?

you cant tell me NO ONE has tried to make a menu item like this

---

### Post by AnRa on 2007-07-30
You can run a script like this:
```
#!/bin/sh
nmap
sudo -s

```

---

### Post by ragecyr on 2007-07-30
AnRa -

this does work, except fot the fact i have a custom .bashrc that clears the screen and puts my own stuff.

So thats my fault to your way of doing it.  Although i dont wanna make 20+ scripts, it will work for now. 

is there any other way other than sudo -s?

---

### Post by AnRa on 2007-07-30
I used "sudo -s" because you mentioned it, in the next example I use Bash. You may use a script like this to avoid making 20+ of them:
```
#!/bin/sh
$1
bash
```Then you just have to run something like: "/path/to/script/scriptname *program*".

---

### Post by Nythain on 2007-07-30
im a little rusty but
gnome-termininal -e nmap &
or &&
should also do the trick

---

### Post by ragecyr on 2007-07-31
> **Nythain said:**
> im a little rusty but
gnome-termininal -e nmap &
or &&
should also do the trick

i though i remembered something like this, so i gave it a try

application: gnome-terminal -e nmap &&
(nothing happens)

application in terminal: gnome-terminal -e nmap &&
(opens one window, pops a second terminal window open, both close)

application in terminal: gnome-terminal -e nmap &
(opens window then closes it)

applicaiton in terminal: "gnome-terminal -e nmap &&"
(There was an error creating the child process for this terminal)





so i do remember something like this, but can't figure out exactly what it is.  possibly a kde thing (i used bt in the past)

---

### Post by ragecyr on 2007-07-31
> **AnRa said:**
> I used "sudo -s" because you mentioned it, in the next example I use Bash. You may use a script like this to avoid making 20+ of them:
```
#!/bin/sh
$1
bash
```Then you just have to run something like: "/path/to/script/scriptname *program*".

gave this a try, opened a window, nothing in it, then popped a small second window with nothing in it.
nothing ran that i can see.  although i do like this style of just doing one menu.mnu file and launching it with parameters being passed.

Thanks for the try!

---

### Post by nashjc on 2007-08-06
I've been having a similar problem mounting a remote drive with sshfs. I want to set this up for someone else with a menu item. As an application, it appears to do nothing. Now I've set up a bash script (in /usr/local/bin accessible to all users on the client machine -- there's only my wife and I who have access to this machine). This script does the sshfs mount, runs a "mount" command to check it is mounted, then sleeps for 10s. Running this from the menu as an "Application in terminal" item leaves the disk mounted for -- you guessed it -- 10 s. I've now made the script wait for an input, and that may be OK, but a bit ugly. 

Anyone know an elegant solution to this? And indeed it looks like the original question has not yet got a nice solution.

JN

---

### Post by ragecyr on 2007-08-06
i got the script to work that is posted above.  i had a modified .bashrc that cleared the text on a window open and showed some custom data.  once i made it not clear and just write the data to the screen it was fine.  

as for your issue, see if teh mount command can be daemonized (simmilar to nessusd -D).  THat would solve the problem.  If not, i'm not familiar enough with the mounting of sshfs commands to really solve this.


another thing you may try is just mounting all the time (which i assume you dont want), or making the file open when gnome/kde opens and set the permissions on the file just for the people who should use it.  That will definitely work as i have a script i run on login that if the window were to close, id lose my desktop (it runs compiz --replace -blablabla).

---

### Post by nashjc on 2007-08-06
You are correct -- I don't want to mount all the time, as I've found that sometimes the user confuses the remote and local directories and then we lose the master copy!

It seems that the menu item launches the command, but then closes it when it closes. I seem to be able to hold it going by requesting input via a "read $tmp", after which process closes and there is an unmount, which actually saves a separate unmount. However, I'd like to understand the processes and be able to code to obtain what I want without tricks.

Thanks for quick reply.

I recommend sshfs -- it does not require root privileges to access remote drive for which a remote user has an account. I use passwordless ssh key. As "mary" I can do

sshfs  john@faroffmachine:/a_directory  /localmedia/mountpointx 

which gives mary access through the mount point to the remote files.

JN

---

### Post by madm0nk on 2008-07-22
How is this solved? I didn't see any answer to the original question aside from running a bash script, which doesn't really seem to convenient. Is there no way to do this in gnome?

---

### Post by ragecyr on 2008-07-23
nope, never a solution. sorry to disappoint!

---

