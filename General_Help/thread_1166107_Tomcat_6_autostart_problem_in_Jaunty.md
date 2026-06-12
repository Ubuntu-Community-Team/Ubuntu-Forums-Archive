---
title: "Tomcat 6 autostart problem in Jaunty"
date: 2009-05-21
forum: General Help
---

### Post by sarikan on 2009-05-21
Hi, 
I've followed all the instructions here: 
[http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/) which seems to be copied by millions of other pages on the web. 
Unlike everyone else however, I can't get it to work. I can start tomcat using the created start script after I log into desktop, but it does not start up automatically. 
Where should I look for to see the problem? Which log can give me some clues. This has taken an incredible amount of time, and I hope you can help me to deal with my frustration :) I just want to start tomcat on startup that's all!!

Kind regards
Seref

---

### Post by michaelrepucci on 2009-05-22
I'm having the exact same problem. Can anyone help?

---

### Post by sarikan on 2009-05-22
Hi there, 
Just to let you know, by using 
sudo ln -sf /bin/bash /bin/sh I've managed to fix the problem. Keeping everything else the same, this uses bash instead of dash, which seems to be the default. 
However, I am seeing some stability problems when I use the auto started Tomcat. Starting it from the desktop works fine though. 
Are we the only ones having these problems? 

Kind regards
Seref

---

### Post by michaelrepucci on 2009-05-22
Hey Seref, thanks for the tip! That does seem to do the trick. Though it does make me a bit nervous. I'm no bash/dash nor Ubuntu expert, but changing the default shell would seem to me to be a big deal. I tried just changing the lines in the script from sh to bash, but that, oddly, didn't work.

I am a bit surprised that we do seem to be the only ones with this problem, at least based on the Googling I did. And I was rather stuck, since I couldn't find any startup error logs anywhere to give me something to go on. There must be such logs, but I don't know where to find them. How'd you discover the link to bash/dash?

As for stability, I don't notice any at first glance, and I'm only using this for development purposes, but if I notice it later, I'll reply to this thread. Thanks for the help!

:) Michael

---

### Post by sarikan on 2009-05-22
I needed this for a serious setup, actually it will be used in a live cd that I'll be distributing. I've setup hardy instead of jaunty, and the same process works without a problem in hardy. 
People seem to be getting happier with every release of ubuntu, but I am getting more frustrated as I keep facing these kind of problems. Skype becomes broken due to improvements in sound, my web cam does not work with 8.1, but it was working with 8.04, etc. I had problems with openldap too. It is great to see Ubuntu going forward, but it would be a shame if we loose the strong aspects while trying to win the desktop :)

---

### Post by michaelrepucci on 2009-05-27
Yeah, I can see how this could be frustrating. I can't imagine what little bug allows it to work in hardy but not jaunty.

I also tried switching all the declarations in the $CATALINA_HOME/bin scripts from #!/bin/sh to #!/bin/bash and leaving the /bin/sh symlink as is, but this didn't seem to do the trick. I'm a bit amazed that this didn't work, but I guess I don't really understand shells and startup. Any insight? I'm still a bit worried about redirecting /bin/sh to /bin/bash instead of /bin/dash. Should I not be worried?

---

### Post by mooseman089 on 2009-07-20
Has anyone found a solution to this yet? I just set up tomcat and after a reboot apache gives me a 503 error but if I manually restart tomcat its fine.

---

### Post by michaelrepucci on 2009-07-21
Well, sarikan's suggestion above of switching the default shell from dash to bash (sudo ln -sf /bin/bash /bin/sh) does seem to work. But I chose instead to use a different startup script.

For some reason that I don't understand, the startup scripts installed by the Ubuntu Tomcat6 package don't seem to autostart. (There are other strange differences too, about which I've posted: [http://ubuntuforums.org/showthread.php?t=1166384](http://ubuntuforums.org/showthread.php?t=1166384).) If I use, instead, a script similar to what's described here ([http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/):]("http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/%29:")

```

#!/bin/sh
#
# Tomcat6 Servlet Engine Manager
#
# description: Provides start, stop, and restart commands for the Tomcat6 servlet engine.
# processname: tomcat6
# pidfile: /var/run/tomcat6.pid

# See http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/

export CATALINA_HOME=/usr/share/tomcat6
export CATALINA_BASE=/var/lib/tomcat6
export JAVA_HOME=/usr/local/java

case $1 in
start)
   sh $CATALINA_HOME/bin/startup.sh
   ;;
stop)
   sh $CATALINA_HOME/bin/shutdown.sh
   ;;
restart)
   sh $CATALINA_HOME/bin/shutdown.sh
   sh $CATALINA_HOME/bin/startup.sh
   ;;
esac
exit 0

```Then it seems to autostart and work as I'd like. Hope that helps!

---

### Post by faizan_comsian on 2009-07-22
hi!
i am fail to do:
$ ./startup.sh
bash: ./startup.sh: No such file or directory

I need to start tomcat plz help me out

---

