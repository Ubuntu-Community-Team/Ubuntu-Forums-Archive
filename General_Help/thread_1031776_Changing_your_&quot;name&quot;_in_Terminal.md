---
title: "Changing your &quot;name&quot; in Terminal?"
date: 2009-01-05
forum: General Help
---

### Post by NCSmokeEater on 2009-01-05
Hi guys, I have a quick question. I've been running Ubuntu Intrepid for a few weeks and I've loved every minute of it. I want to change the name that pops up in my terminal but I can't figure out how to do so.

Right now it says "john@john-laptop", so I created a new user with the same access priv. as my default account and let's say it's called "ubuntuuser". 

It shows up in terminal as "ubuntuuser@john-laptop".

How do I go about changing the suffix that reads "john-laptop" for either of my user accounts? Google didn't help any and I've tried doing it on my own but I can't find the option anywhere.

Any help would be muchhhh appreciated!

Thanks!

---

### Post by Titan8990 on 2009-01-05
There is two things that need to be changed, /etc/hostname and /etc/hosts. Always make backups of config files before changing them, just in case something goes wrong. 

To make the backups:

```
sudo cp /etc/hostname /etc/hostname.BAK
sudo cp /etc/hosts /etc/hosts.BAK
```

To change your computers name, edit /etc/hostname and change it to whatever you would like:

```
sudo nano /etc/hostname
```


This file will only contain your current computer name "john-laptop."

Next, you need to edit /etc/hosts to reflect the changes:

```
sudo nano /etc/hosts
```

Again, replace "john-laptop" with your new computer name.

---

### Post by Ahadiel on 2009-01-05
> **NCSmokeEater said:**
> Hi guys, I have a quick question. I've been running Ubuntu Intrepid for a few weeks and I've loved every minute of it. I want to change the name that pops up in my terminal but I can't figure out how to do so.

Right now it says "john@john-laptop", so I created a new user with the same access priv. as my default account and let's say it's called "ubuntuuser". 

It shows up in terminal as "ubuntuuser@john-laptop".

How do I go about changing the suffix that reads "john-laptop" for either of my user accounts? Google didn't help any and I've tried doing it on my own but I can't find the option anywhere.

Any help would be muchhhh appreciated!

Thanks!
That's your computer's hostname. To change it,
```
sudo hostname -v *newhostname*
```
You'll also have to add the appropriate line to /etc/hosts
```
127.0.0.1 *newhostname*
```

---

### Post by the_squircle on 2009-01-05
The part after the @ symbol is the computer name. To change it, go to Applications -> Accessories -> Terminal. Once in the terminal, type (without the quotes) "gksudo gedit /etc/hosts /etc/hostname" and press return. Enter the root password, and change 'john-laptop' to your new desired name, save both, exit gedit, reboot, and everything should be changed. :)

---

### Post by Ahadiel on 2009-01-05
Oops, double post.

---

### Post by NCSmokeEater on 2009-01-05
Figured it out myself...

Run the following command in terminal.
```
gksudo gedit /etc/hostname 
```

Type in your admin password.

A host-name file will open. Change the existing host-name in the file and click save.

Exit all open windows and reboot.


Your host-name has been changed. :D




I didn't think anyone would reply that fast! Thanks a lot for the help but I managed to figure it out on my own (had to think about it but trial and error actually worked haha). Thanks again for the help though, I really appreciate it. Obviously you guys are on the ball haha Keep it and I appreciate it!

---

### Post by Titan8990 on 2009-01-05
You can easily run into issues if you do not change /etc/hosts to reflect the changes you made.

---

### Post by NCSmokeEater on 2009-01-05
> **Titan8990 said:**
> You can easily run into issues if you do not change /etc/hosts to reflect the changes you made.

I just changed it to make sure. Thanks for the warning.

---

### Post by bodhi.zazen on 2009-01-05
How to change your prompt :

[http://www.yolinux.com/HOWTO/Bash-Prompt-HOWTO.html](http://www.yolinux.com/HOWTO/Bash-Prompt-HOWTO.html)

---

