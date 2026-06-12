---
title: "Script"
date: 2009-01-20
forum: Desktop Environments
---

### Post by ientzy on 2009-01-20
Hello
I want to make a script for change user from normal user to user with root access for sudo.
I need the for the mount command.Anyone know what is wrong with this script?
```
#!/bin/bash -x
#Mount samba filesystems
echo "Mount samba filesystems"
name=<user with root access>
word=<root pass>
echo $word>/home/flg/word
su $name</home/flg/word
echo "Next sudo su"
sudo -u $name</home/flg/word
echo "Next mount"
mount -t cifs //192.168.0.120/Public /mnt/public2 -o username=$USERNAME,password=$PASSWD,iocharset=utf8,file_mode=0777,dir_mode=0777
echo "Finish"

```

---

### Post by snova on 2009-01-20
I tried redirecting a file containing a password into su, and it didn't work:

```
snova@sanctuary:~$ su snova < tmp
su: must be run from a terminal
```

Also, this line won't have the effect you want:

```
sudo -u $name</home/flg/word
```

Since sudo requires a command to run. Even if you had it run a shell or something, the rest of your script would continue to run as your user, not as the other user, because neither command can magically change the user the shell is running under. They start a new one. ;)

---

### Post by FireJet on 2009-01-21
What you need is two scripts, the first one will run the second as the root access user. And sudo won't authenticate using a file by default, you have to use the -S flag. 

So, something like this:

script1.sh
```

#!/bin/bash -x
echo "Mount samba filesystems"
name=<user with root access>
word=<root pass>
echo $word>/home/flg/word
sudo -S -u $name script2.sh < /home/flg/word

```

script2.sh
```

#!/bin/bash -x
echo "Next mount"
sudo -S mount -t cifs //192.168.0.120/Public /mnt/public2 -o username=$USERNAME,password=$PASSWD,iocharset=utf8,file_mode=0777,dir_mode=0777 < /home/flg/word
echo "Finish"

```

---

### Post by ientzy on 2009-01-21
> **FireJet said:**
> What you need is two scripts, the first one will run the second as the root access user. And sudo won't authenticate using a file by default, you have to use the -S flag. 

So, something like this:

script1.sh
```

#!/bin/bash -x
echo "Mount samba filesystems"
name=<user with root access>
word=<root pass>
echo $word>/home/flg/word
sudo -S -u $name script2.sh < /home/flg/word

```

script2.sh
```

#!/bin/bash -x
echo "Next mount"
sudo -S mount -t cifs //192.168.0.120/Public /mnt/public2 -o username=$USERNAME,password=$PASSWD,iocharset=utf8,file_mode=0777,dir_mode=0777 < /home/flg/word
echo "Finish"

```

Thanks, is ok this script but i need a script to change from normal user to user with root access.I try to make another script(script1.sh) and move the other to script2.sh and script3.sh

script1.sh
```
#!/bin/bash -x
echo "Mount samba filesystems"
name=<user with root access>
word=<password>
echo $word>/home/flg/word
gnome-terminal -t bash su $name < script2.sh /home/flg/word
```

script2.sh
```
#!/bin/bash -x
echo $word>/home/flg/word
sudo -S -u $name script3.sh < /home/flg/word
```

and script3.sh

```
#!/bin/bash -x
echo "Next mount"
sudo -S mount -t cifs //192.168.0.120/Public /mnt/public2 -o username=$USERNAME,password=$PASSWD,iocharset=utf8,file_mode=0777,dir_mode=0777 < /home/flg/word
echo "Finish"
```

Is open a new terminal but don`t ask any password, just open and that is all.How i can make to open the new terminal and continue with script2.sh but using a user with access to root. I use the first script is ok, but i must to change in sudoers and give him access and i don`t want this, i want just 1 user with root access. I need this script to make automatic mount to a share from a NT server when users from domain NT ar login to workstations with ubuntu OS. This is my final and hard step, so please help me with this script or any else idea.Thanks.

---

