---
title: "Setting up multiple application desktop environment"
date: 2008-04-16
forum: Desktop Environments
---

### Post by brendan6 on 2008-04-16
I do a bit of web development and have to start several programs before i can start to work.

Startup process:
[LIST]
[*]fire up terminal and do cd rails/Website; ruby script/server
[*]startup firefox and point it to [http://localhost:3000/](http://localhost:3000/)
[*]switch to desktop #2
[*]start up netbeans, open my project folder in nautilus and open a terminal in the projects directory
[*]switch to desktop #3
[*]open mysql query browser and mysql administrator
[/LIST]

Lots of things to do...and im very lazy :p Any way I can script something to do all that in 1 press?

---

### Post by PurposeOfReason on 2008-04-16
I believe most of that could be accomplished in a simple bash script. I'm not sure on the workspaces though. If they are always on that workspace then maybe devilspie could manage that part of the aspect.

---

### Post by brendan6 on 2008-04-16
Ok im starting to write the script...first problem:

i execute the command:

ruby ~/rails/Website/script/server

...well it starts a server alright, but i dont know where it started.  I know it started because i can point firefox to it.  How do I force it to open a new terminal and THEN start the server to i can stop it with Ctrl+C?

Also...i have a list of programs that are supposed to start, bu the next program down the list only start after the program above it exits.

```
#!/bin/sh
#
#launch.sh
#
#
ruby ~/rails/Atlashomes/script/server
firefox http://localhost:3000/
sh /usr/local/netbeans-6.0.1/bin/netbeans
nautilus ~/rails/Atlashomes
```

---

### Post by brendan6 on 2008-04-16
Ok, i figured out me second problem...just putting an ampersand (&) at the end starts it as a background process.

so...

```
firefox http://localhost:3000/ &
sh /usr/local/netbeans-6.0.1/bin/netbeans &
nautilus ~/rails/Atlashomes &
```

..accomplishes that part, but i still cant figure out how to run the server in an open terminal window (and how to open a new terminal window with a script)

---

### Post by daengbo on 2008-04-16
Change
ruby ~/rails/Atlashomes/script/server
to
xterm -e ruby ~/rails/Atlashomes/script/server

That'll run the xterm starting the server in it.

Best of luck!

---

### Post by daengbo on 2008-04-16
Oh, yeah, and you don't need to write a script. Just add the programs to Preferences > Sessions > Startup Programs.

---

