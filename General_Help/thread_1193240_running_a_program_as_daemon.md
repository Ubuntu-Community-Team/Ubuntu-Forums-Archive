---
title: "running a program as daemon"
date: 2009-06-21
forum: General Help
---

### Post by rohitreborn on 2009-06-21
Hi,

I have been trying to run a shell script (which in turn calls a Java program) as a daemon.

The shell script by itself runs fine but when I attempt to run it as daemon via

daemon command it won't execute.

I setup 

daemon --name=yserver  --errlog=/tmp/yserver.err --output=/tmp/yserver.log -b /tmp/yserver.dbg -d 2 bin/java/com/yserver/YServerTest

the err logs show 

yserver: client (pid 25812) exited with 1 status


the output file remains empty.

---

### Post by blueridgedog on 2009-06-21
Another option would be to install xinetd and setup it to run your script.

---

### Post by paperplate9 on 2009-06-21
Does your script "exit" at all? If you're a daemon, you shouldn't exit. I'm not sure but if you started child processes those processes might get killed once exiting. If that's the problem, grab the pid of the command you executed and wait for that new process to exit before you exit.

---

### Post by Copernicus1234 on 2009-06-21
You should be able to run it using the nohup command. It will start whatever program you want and run it in the background, even after you log off.

---

### Post by paperplate9 on 2009-06-21
> **Copernicus1234 said:**
> You should be able to run it using the nohup command. It will start whatever program you want and run it in the background, even after you log off.

True.

I guess the real question is why is he trying to run his script as a daemon?

---

