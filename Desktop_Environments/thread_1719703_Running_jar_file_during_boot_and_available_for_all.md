---
title: "Running jar file during boot and available for all users"
date: 2011-04-02
forum: Desktop Environments
---

### Post by blackfalcon03 on 2011-04-02
I have a jar file which runs as the server with a GUI in my machine and if that starts up i can control my machine with the client in my android phone through LAN. Manually everything works fine if i login and start the server.

What I want to do

1) The server(jar file) should be started at boot
2) This should be available to all users irrespective of who is logged in and if multiple users are logged in simultaneously.

What I have already tried

1) I have tried to add this to the Startup Applications but it does not work always due to some reason after switching between users but even if it works thats not the solution i need because these settings are for a specific user and works after login

2) I tried adding this to rc.local file, but does not work when i login with any user, not sure why. I also tried putting them into all the runlevels (rc*.d folders), but nothing seems to be working. I am not quite sure if i understand how these methods work but when i did boot the server was not there.

3) Manually if i run the jar and switches the user with the first user still logged in, then the server is as good as not running for the second, but if i try to run the jar again, it fails because there is already a process which is running but for first user. If I switch back to first user i have the server.


The Files

1) I have the jar file to execute in /usr/local/bin/
2) I have a shell script in /etc/init.d/ which executes the java - jar command
3) I have the links to rc*.d for all runlevels for the above script

Nothing in the above seems to be working. I just need one process running for all the users, but i never could see the server starting on startup. If I manually start the server its only available to the user who started it. Can you give me a better solution...

---

### Post by mister_p_1998 on 2011-04-05
I would think, if it needs to start regardless of the logged on user, you would need to run it as root for a start (sudo crontab -e) Although the problem would be, could any user be able to access the program? or just root? Maybe any user could access it as sudo ? dunno give it a try, I do know that the only way to start it for any user, is as root, unless you put it in every single users startup. Does the program have a GUI interface? if so you need to start it in cron with the following prefix in my eg for TED:

45 0 * * 1,2,3,4,5 export DISPLAY=:0 && /usr/bin/java -jar /home/steve/Ted/ted.jar

Good luck
Steve

---

### Post by Vijayakumar c s on 2011-08-23
hello 
To run an application during logging   for all users ,you just need to create one startup file in /etc/xdg/autostart.
this will work for all users who loggin in gnome.for those who login in terminal,create one shell script to run that application in /etc/profile.d directory

---

### Post by Vijayakumar c s on 2011-08-23
:guitar:> **Vijayakumar c s said:**
> hello 
To run an application during logging   for all users ,you just need to create one startup file in /etc/xdg/autostart.
this will work for all users who loggin in gnome.for those who login in terminal,create one shell script to run that application in /etc/profile.d directory



[email]-vijayakumarcs@gmail.com[/email]

---

