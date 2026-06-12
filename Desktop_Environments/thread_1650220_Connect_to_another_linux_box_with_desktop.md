---
title: "Connect to another linux box with desktop"
date: 2010-12-21
forum: Desktop Environments
---

### Post by darkdesire on 2010-12-21
From an UBUNTU environment (10.10) I would like to connect to connect to another linux machine (Redat) and get a KDE or GNOME desktop working environment. From Windows I can use Exceed to do this but what is the best method with UBUNTU?

---

### Post by ajgreeny on 2010-12-21
NFS or ssh, depending on what you want to do.

If you want the boxes always connected, NFS is probably the way to go, but for the occasional connection to copy a few files, ssh may be enough.

Read up on both and come back again if necessary.

For my own computers I use ssh.
For extra security there is a good ubuntu community document which may help.
[SSH/OpenSSH/Configuring]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring") 
Have a look at that and see if it gives you any clues.

For what it's worth to you, I have openssh-server on my main machine but have sshd stop at boot time by adding the line
     ```
service ssh stop 
```
 to my /etc/rc.local file.  Then when I want to use it, I quickly  start it using an alias in terminal of "ssh+" (sudo service ssh start).   I stop it once I have finished as well using another alias, "ssh-"  (sudo service ssh stop).  This increases security as it means I only  have the ssh server running when I really need it.

In my **/etc/ssh/sshd_config** file I still have **PasswordAuthentication yes**, but I use a non-standard port, reduce **LoginGraceTime** to 20 secs, have set a **MaxAuthTries** **3**, and have only myself and my wife as allowed users with **AllowUsers name1 name2**.  I have also set it to use **Protocol 2** only instead of 1 and 2.

Similarly in the **/etc/ssh/ssh_config** file I have set the same non-standard port to be used, and also allow only protocol 2.

I know there are more secure ways to use ssh, particularly if you want  it always on, but for the few times a month I seem to need it, this is  quite enough for me, and it works without problems, either using the  terminal, or the bookmarks I have saved, depending on exactly what I  want to do.

---

### Post by Danny Darko on 2010-12-21
> **darkdesire said:**
> From Windows I can use Exceed to do this but what is the best method with UBUNTU?

Do you use XDMCP? Sounds like it if you get a full desktop through Exceed.

---

### Post by darkdesire on 2010-12-24
thanks for the replies. Yes I believe exceed uses xdmp and from Windows I get the full redhat working environment desktop. It is very useful to have a connection like this and have both a fully working Windows and Linux desktop environment on one screen. Now I have Ubunui I would like to have the same functionality. I have ssh which is also very good to have one or two connections but I find that a full desktop env has lots of benefits. 

Any other ideas
Cheers

---

