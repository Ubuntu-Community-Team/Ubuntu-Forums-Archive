---
title: "APT issues (new user)"
date: 2006-08-14
forum: Desktop Environments
---

### Post by guitodd on 2006-08-14
I'm fairly new to Linux.. Installed 6.06lts and managed to enter a bad url into APT when I was trying to get BlueFish.  Now this bad address crashes APT and doesn't show up in the repository index in the APT gui...  However, when I find the actual repository index file and open it.. I can see my bad line.

I can remove the line.. but it needs 'root' to resave it.  My understanding is that I cannot be root in Ubuntu?  Any ideas on how I can fix this?  With this bad address.. Synaptic won't check any repositories and shuts down.

---

### Post by njzillest on 2006-08-14
sudo gedit /etc/apt/sources.list

This will bring up a text file of the repositories.

If that doesnt work, change the password of root by 
sudo passwd root

then log into root by
su root

once in root, follow the first steps (gedit sources.list)

repost the sourcelist so i can help you.

---

### Post by ajgreeny on 2006-08-14
Use your chosen text editor (eg gedit) as root to edit your /etc/apt/sources.list file by typing into a terminal:-

gksudo gedit /etc/apt/sources.list

This will ask you for your own password, not the root password as there isn't one by default.  Enter your own pw and then edit out the line that is faulty, save the file and try synaptic again.  All should be well.

You should look up the relevant pages of the wiki to see how sudo is used in ubuntu instead of root logins.  Have a read of:-
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Ramses de Norre on 2006-08-14
Don't set a root password! Instead you need to use sudo, the index file you're talking about should be /etc/apt/sources.list, so if you now edit it with ```
gedit /etc/apt/sources.list
``` you can do this as root with ```
sudo gedit /etc/apt/sources.list
```
When you're asked for a password you need to type in your user password (and you wont see any characters but that's normal ;)).

---

### Post by guitodd on 2006-08-14
Great! Thanks guys.  I wish I had the machine at work so I could try it.  But I think this is the ticket.  I plan on just deleting the goofy line and assume it will be fine after that.  I'll let everybody know this evening.

Thanks again!

---

### Post by ajgreeny on 2006-08-14
You should really use *gksudo gedit* and not just *sudo gedit* to open a gui application such as gedit, in gnome as root; although in this case it does no harm, using sudo can cause problems.  Sudo is really for root use of terminal utilities, not gui programs.  In kde you should use *kdesu kate* for the same situation.

---

### Post by guitodd on 2006-08-16
Thanks everyone for the replies.. It worked just fine and soon I was back to entering more mis-spelled URLs!!:shock: 

Thanks,
Todd

[www.logoseye.com](www.logoseye.com)

---

