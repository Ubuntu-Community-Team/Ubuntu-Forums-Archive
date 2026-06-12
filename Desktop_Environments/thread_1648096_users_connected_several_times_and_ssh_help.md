---
title: "users connected several times and ssh help"
date: 2010-12-18
forum: Desktop Environments
---

### Post by lucacerone on 2010-12-18
Dear all,
I could configure my computer with Ubuntu 10.04 so that I can remotely access through ssh.
Just as a curiosity today I run the "users" command on the remote
machine and I noticed that my
user seems to be connected more than once.

That is the output of "users" is something like

myuser myuser myuser myuser

Is this normal? I think I might depend because sometimes
I didn't close the connection through the "exit" command,
but I simply closed the terminal.
How can I now "drop" the connections that I no longer use?

Also can you give some good suggestions to configure
ssh so that is reliable and safe?
Thanks a lot in advance,
Cheers, -Luca

---

### Post by ajgreeny on 2010-12-18
If you use the *users* command in terminal on your desktop system, it will show two users always, so when you are logged in with ssh to another computer, perhaps there are two from each OS showing.  I have no real idea about this, but just throw it in as a possibility, having never tried it out.

For extra security there is a good ubuntu community document which may help.
[SSH/OpenSSH/Configuring]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring") 
Have a look at that and see if it gives you any clues.

Forwhat it's worth to you, I have sshd on my main machine but have it stop at boot time by adding the line ```
service ssh stop
``` to my /etc/rc.local file.  Then when I want to use it, I quickly start it using an alias in terminal of "ssh+" (sudo service ssh start).  I stop it once I have finished as well using another alias, "ssh-" (sudo service ssh stop).  This increases swecurity as it means I only have the ssh server running when I really need it.

In my **/etc/ssh/sshd_config** file I still have **PasswordAuthentication yes**, but I use a non-standard port, reduce **LoginGraceTime** to 20 secs, have set a **MaxAuthTries** **3**, and have only myself and my wife as allowed users with **AllowUsers name1 name2**.  I have also set it to use **Protocol 2** only instead of 1 and 2.

Similarly in the **/etc/ssh/ssh_config** file I have set the same non-standard port to be used, and also allow only protocol 2.

I know there are more secure ways to use ssh, particularly if you want it always on, but for the few times a month I seem to need it, this is quite enough for me, and it works without problems, either using the terminal, or the bookmarks I have saved, depending on exactly what I want to do.

---

### Post by lucacerone on 2010-12-18
I just noticed that on your local machine
if you try "users" answers your name as many times
as many open terminal there are plus one (i guess is the
"normal" login).
So I'm not so scared to see a few times my username,
probably I just left some terminal window open in my 
remote machine, 
but still I'd like to know why users tells your username 
a few times and why this can be useful.
Thanks a lot for your answers,
Cheers, -Luca

---

