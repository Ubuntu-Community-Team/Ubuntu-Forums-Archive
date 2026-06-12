---
title: "Can't get upstart to run job on system reboot"
date: 2009-05-04
forum: General Help
---

### Post by dwesner on 2009-05-04
I'm new to Ubuntu and I'm trying to figure out how to get a job to kick off at system startup as I used to do through inittab.  After a lot of reading and Googling, I've added a file to the /etc/event.d directory with the following contents:

   # ldm
  start on ldm
  start on startup
  start on runlevel 2
  start on runlevel 3
  start on runlevel 4
  start on runlevel 5
   
  pre-start script
          exec /bin/su -c '/usr/local/ldm/ldm-6.7.0/bin/ldmadmin clean' -- ldm
  end script
   
  respawn
  exec /bin/su -c '/usr/local/ldm/ldm-6.7.0/bin/ldmadmin start' -- ldm  
    [COLOR=#1F497D][FONT=&quot]  
[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]I figure some of the "start on" commands are not necessary, however, now when I enter the following command after restarting, ldm gets kicked off and seems to be running just fine:[/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  /etc/event.d $ sudo initctl emit ldm
  ldm
  ldm (start) waiting
  ldm (start) starting
  ldm (start) pre-start, process 6121
  ldm (start) spawned, process 6141
  ldm (start) post-start, (main) process 6141
  ldm (start) running, process 6141     
  [COLOR=#1F497D][FONT=&quot] [/FONT][/COLOR]
  [COLOR=#1F497D][FONT=&quot]So that seems to tell me that the script is coded correctly, since upstart can interpret it when I manually issue the execute job command through initctl.  Unfortunately, it still isn't starting automatically at reboot and I'm stuck in understanding what I've missed.  

Anyone have any ideas? [/FONT][/COLOR]

---

### Post by rmyoung on 2009-08-16
Did you ever work out a solution to this, I am having the same issue trying to the dropbox service. My script is similar:
> start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5
stop on shutdown
respawn

script
  cd /home/dropbox
  exec sudo -H -u dropbox ./.dropbox-dist/dropbox
end script 
The service doesn't start when the system boots but runs OK if I manually run the **/etc/event.d/dropbox** script via the **initctl start dropbox** command.

---

### Post by lswb on 2009-08-16
Hi, I am not familiar with the command you are trying to run, so this may be off base, but it occurrs to me that it may be too early in the boot process for it to run from an event.d script. Most services are still started in the sysv style through the /etc/rcx.d links to /etc/init.d scripts. If you put your command in the file /etc/rc.local it will be called after all init scripts have been run.

---

### Post by rmyoung on 2009-08-20
I tried adding it to rc.local but it doesn't seem to start at startup either. If I manually run rc.local it starts fine. I also have some other init.d scripts which aren't starting at startup, but work fine manually.

Is it possible to log the startup process so I can see what is going wrong?

---

### Post by lswb on 2009-08-20
dwesner & rmyoung,

I just noticed that you are using su and sudo in the commands you are trying to run. The init scripts and event.d scripts are run as root, sudo and/or su should not be used. There are no users logged on at the time the scripts are run to su or sudo anything.

dwesner, what is ldm? I googled and found that that name used for several different programs, including amongst others a login manager like gdm or xdm, some kind of "Logical Disk Manager" service, and "Local Data Manager"

rmyoung, you can log your own script by just echoing statements to a file, or if you look at some the /etc/init.d scripts, and the contents of /lib/lsb/init-functions, you can see how the bootup logging to usplash or the console is done. I don't think  the latter will work from event.d scripts, though. I am not familiar with dropbox, but after a quick google it appears that it requires networking to be up and running, is this correct? The event.d scripts start before networking, which is still started in the init.d sequence. If you are using Network Manager to manage your networks, you probably don't have a network up until someone has logged in.

---

