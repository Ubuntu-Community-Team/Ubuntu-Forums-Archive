---
title: "ubuntu 9.04, startup scripts and tomcat 6.0.20"
date: 2009-06-16
forum: General Help
---

### Post by dumb.coder on 2009-06-16
Hi All,

  I am having some questions regarding the startup scripts in rc?.d dirs. Today I was trying to install tomcat 6.0.20 on my Jaunty Jakalope box. I was able to run it from bash. Also I created startup script in init.d. Till here everything went fine. After this, I tried to put the sript as a startup script. Here are the things I tried and the results..

1. created link K99tomcat in rc1.d and S99tomcat in rc2.d. Rebooted and the server was not started automatically.

2. removed old links and tried "update-rc.d tomcat defaults". Rebooted and the server didn't start at boot :(.

3. removed old links "update-rc.d -f tomcat remove" and created new links "update-rc.d tomcat start 99 2 3 4 5 . stop 99 0 1 6 .". Rebooted and server yet didn't start at boot :,(.

4. again removed old links and tried "update-rc.d tomcat start 99 2 3 4 5 S . stop 0 1 6 .". Now rebooted and voila it started properly.

Now my questions are these. 
What I did wrong in initial 3 steps? 
Also why the service started when I put it in rcS.d and why not in runlevel 2 3 4 5? 
Is it the recommended way of adding scripts to startup or is there any other recommended way?

I am not very clear regarding rcS.d. Can somebody explain me the significance of this directory? I tried googling this, but didn't get any satisfactory links.

Regards,
Dumb Coder

---

### Post by apedraza on 2009-06-27
Thank you, Thank you, Thank you.

I've been beating myself over the head trying to fix tomcat autostart...

---

### Post by draygen on 2009-07-08
This is also the case in Ubuntu 8.04.. 

 I'm working on a Virtual Appliance which will have tomcat in it .. and it took me days, but I finally realized that tomcat will only start during boot if the startup script is in /etc/rcS.d .. When the start-up script is in /etc/rc2.d - The script doesnt give any errors, and the tomcat logs do not indicate any problems .. its like the process just poofs.

Does anyone have an explanation as to why this is? I was thinking that maybe its because the tomcat script tries to run as a user other then root (with a su $TOMCAT_USER -c $CATALINA_HOME/bin/startup.sh) but I changed it to root and had the same problem.

 draygen

---

### Post by draygen on 2009-11-16
shameless /bump ;)

Does anyone have any insight on this? It would be great if I could get Tomcat to autostart in the runlevel scripts :(

---

### Post by mc-rpg on 2009-11-27
Thank you. This does it for me.

---

