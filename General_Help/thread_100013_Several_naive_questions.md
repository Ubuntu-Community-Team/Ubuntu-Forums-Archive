---
title: "Several naive questions?"
date: 2005-12-06
forum: General Help
---

### Post by trytrytry on 2005-12-06
Hi All,

I installed the Ubuntu 5.10 and am happy with it. Now I have several naive questions. I did search the forum and also checked the FAQ guide but didn't find the exact answer.

Question 1: How to find out what processes (or services) are running (like Ctr+Alt+Del in Windows)?

Question 2: How to find out my machine's IP address?

Question 3: I installed ssh and openssh-server, but I don't know how to config the ./etc/ssh/ssh_config and sshd_config so that I can login into this machine from another Windows-running computer using SSH secure shell.

Question 4: (Continue from above) Can I use the address like "abc.def.com" to SSH to my Ubuntu machine instead of the real IP address? Do I need to do something to the ssh_config and sshd_config?

Question 5: How to lauch an installed program? I did install a bunch of softwares using Synaptic Package Manager and sudo apt-get install, but I didn't notice where they got installed and don't know which command I should type in the console to lauch them?

Question 6: I partitioned a FAT32 disk to share with my windows, but I find I can't delete the files or folders in it once I entered it through computer -> file system -> ***. I tried to use "sudo chown -R username:user *" and "sudo chmod -R a+rw" but still no-go.


I am a brand newbie to Linux and Ubuntu and any of your ideas are very helpful. Many thanks ahead!

---

### Post by Bachstelze on 2005-12-06
1) Applications > System Tools > System Monitor

You can also use Automatix to install the Ctrl+Alt+Del shortcut (and lots of other useful things)

5) You should find them somewhere in the Applications menu.

6) run "sudo gedit /etc/fstab" and find the line where your fat partition infos are. On the mount parameters, replace "defaults" with this :

```
rw,user,auto,gid=100,uid=1000,umask=002,iocharset=utf8,codepage=850
```

save the file and run "sudo mount -a", voil&#224; :)

---

### Post by dave9191 on 2005-12-06
[QUOTE=trytrytry]
Question 1: How to find out what processes (or services) are running (like Ctr+Alt+Del in Windows)?[/QUOTE]

If you go to your keyboard shortcut (System > Prefrances) there is an option in there for showing the task list. You can bind that to ctrl + alt + del or Ctrl + Esc (which i find easier even after using windows for 10 years).

> Question 2: How to find out my machine's IP address?

There are several graphical ways of doing this. But I don't use them so I'll be vague. In the applications > system tools you can find a networking tool that should tell you. I think the task manager can tell you as well. And you can add an applet to the panel for networking which will tell you when clicked. 

Or you can open a terminal and type "ifconfig" and that will list all your network configuration. eth0 is usually your ethernet and eth1 a wifi card, but that depends on your system config. 

> Question 3: I installed ssh and openssh-server, but I don't know how to config the ./etc/ssh/ssh_config and sshd_config so that I can login into this machine from another Windows-running computer using SSH secure shell.

You should be able to start the ssh server and just ssh into your machine without having to change any settings. Try typing sshd into a command line to start it. or possibly "sudo /etc/init.d/ssh start".

> Question 4: (Continue from above) Can I use the address like "abc.def.com" to SSH to my Ubuntu machine instead of the real IP address? Do I need to do something to the ssh_config and sshd_config?

You would need to own the def.com domain and you would setup the subdomain abc to redirect to your IP. This is not a setting on your linux box, but with your domain name provider. 

> Question 5: How to lauch an installed program? I did install a bunch of softwares using Synaptic Package Manager and sudo apt-get install, but I didn't notice where they got installed and don't know which command I should type in the console to lauch them?

Most apps will appear somewhere in the application menu. If not you will need to know the command to start the program. 

Hope this helps 

--
Dave

---

### Post by trytrytry on 2005-12-06
[QUOTE=HymnToLife]

6) run "sudo gedit /etc/fstab" and find the line where your fat partition infos are. On the mount parameters, replace "defaults" with this :

```
rw,user,auto,gid=100,uid=1000,umask=002,iocharset=utf8,codepage=850
```

save the file and run "sudo mount -a", voilà :)[/QUOTE]


Works like a charm! Thanks a lot!

---

### Post by Gray. on 2005-12-06
Most times if you installed a program using the "sudo apt-get install <name>" then you can start it by just typing that <name> in a terminal. Or you could add it to the Applications Menu using System Tools > Applications Menu Editor.

---

### Post by trytrytry on 2005-12-07
[QUOTE=dave9191]
You should be able to start the ssh server and just ssh into your machine without having to change any settings. Try typing sshd into a command line to start it. or possibly "sudo /etc/init.d/ssh start".

Many thanks for your detailed answers. I use your "ifconfig" and dif find my IP address (e.g., 123.456.789.000), but I still can't ping or SSH my Ubuntu machine from my laptop (running winxp pro). When I typed ping 123.456.789.000, I was told "Request timed out". When I lauch SSH secure shell and typed 123.456.789.000 with my login name, I was told the "The host 123.456.789.000 is unreachable".

In addition, I ran the command "sshd" in Ubuntu and found "sshd re-exec requires execution with an absolute path". I also tried "sudo /etc/init.d/ssh start" and got the message:                                                                                                              " * Starting OpenBSD Secure Shell server...                               [fail]"

Can anyone take a look at my problems and any of your ideas are very welcomed? Thanks ahead.

---

### Post by RAOF on 2005-12-07
Actually, I think that installing the ssh-server automatically starts it as the final part of the install (and sets it so that it starts automatically with each reboot).  Since it's already running, trying to start it again with /etc/init.d/ssh start will fail.

---

### Post by dave9191 on 2005-12-07
You should be able to ping your computer anyway unless you have enabled a firewall. 

And try 

/etc/init.d/ssh stop
/etc/init.d/ssh start

If its all running ok, then you should be able to test it by ssh-ing to the linux machine from the linux machine. 

ssh myuserName@localhost

If you can login that way, then the ssh server is running. If you can't access it from the windows box, then there are some network issues along the way. 

--
Dave

---

