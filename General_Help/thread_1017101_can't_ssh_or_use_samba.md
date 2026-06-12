---
title: "can't ssh or use samba"
date: 2008-12-20
forum: General Help
---

### Post by Davez69gto on 2008-12-20
The other day i realized that i cannot ssh into my computer or use my samba shares anymore.  I don't know if it was after i updated or after i installed wine.  I don't see how wine could affect it but it is the only thing i can think of.  I know my samba shares are set up correctly b/c i was using them just fine until the other day when everything went crazy.  The weird thing is that at the same time i could no longer ssh into my computer.  I can ssh out w/o a problem and all my other internet apps work just fine.  

I'm currently running Ubuntu 8.04.  This is currently on my desktop which is a intel pentium duo 2.5Gh w/ 1gb ram. Hope someone can help.    

Thanks
Dave

---

### Post by pytheas22 on 2008-12-20
Can you ssh localhost and your local IP address?

Can you open your local samba shares (i.e., the ones on the Ubuntu machine in question) over samba from the same machine?

Is there anything between your Ubuntu machine and the other machines from which you've tried to access it?  Since you've made no changes on Ubuntu's end that should have affected this, I'm wondering if some proxy has started blocking the samba and ssh services.

---

### Post by Davez69gto on 2008-12-20
I was able to ssh into my computer from the localhost.  i.e. ssh localhost and everything worked well.  I checked from another computer and that still doesn't work.  I believe i'm using dolphen when i checked the smb shares of course smb:/// i even tried smb:///localhost just to check and that doesn't work.  I also restarted my samba server just to be sure that it was up and running.

---

### Post by Davez69gto on 2008-12-20
forgot to mention that i cannot view any shares that are on other computers either.  I have a server in the house that shares files.  I know it's up and can ssh into it can read it's files from other computers just not this one.

---

### Post by StevenHarper on 2008-12-20
Just out of interest if you open nautails as super user does it work?

```
sudo nautails
```

---

### Post by Davez69gto on 2008-12-20
forgot to mention that i cannot view any shares that are on other computers either.  I have a server in the house that shares files.  I know it's up and can ssh into it can read it's files from other computers just not this one.

---

### Post by Davez69gto on 2008-12-20
It opened a window and this is what came up in the terminal

Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:21421): WARNING **: Unable to add monitor: Operation not supported
seahorse nautilus module shutdown

---

### Post by Davez69gto on 2008-12-20
forgot to mention that i cannot view any shares that are on other computers either.  I have a server in the house that shares files.  I know it's up and can ssh into it can read it's files from other computers just not this one.

---

### Post by pytheas22 on 2008-12-20
This still sounds strange.  There's no proxy between between your Ubuntu machine and the other computers in your house, right?

You might also want to install Firestarter or Uncomplicated Firewall to make sure that iptables isn't blocking anything--it's possible that an application you installed starting blocks or ports or something without your realizing it.  You can install these programs with:
```

sudo apt-get install firestarter ufw
```

They provide nice graphical frontends for monitoring your iptables policies.  Is everything open?

Also, can you ssh into your local IP address?  In other words, if your IP address is 192.168.1.2, does it work if you type:
```

ssh user@192.168.1.2
```

---

### Post by Davez69gto on 2008-12-20
forgot to mention that i cannot view any shares that are on other computers either.  I have a server in the house that shares files.  I know it's up and can ssh into it can read it's files from other computers just not this one.

---

### Post by Davez69gto on 2008-12-20
i checked and i can ssh w/ the whole name@198.1.1.1 stuff.  That works fine.  I also already had firestarter installed just not running. 

I just ran firestarter and when i tried to get in i saw my lappy's ip come up and i could allow it in.  So that prob means that my firewall is blocking everyone.  How would i fix that and open it up?

---

### Post by Davez69gto on 2008-12-20
forgot to mention that i cannot view any shares that are on other computers either.  I have a server in the house that shares files.  I know it's up and can ssh into it can read it's files from other computers just not this one.

---

### Post by pytheas22 on 2008-12-20
> I just ran firestarter and when i tried to get in i saw my lappy's ip come up and i could allow it in. So that prob means that my firewall is blocking everyone. How would i fix that and open it up?

Make sure that port 22 (the ssh port) is open to all users, or to the list of IP addresses that you want to connect to it.  Do the same for the samba port, which I think is 139 but you should double-check.
> 
forgot to mention that i cannot view any shares that are on other computers either. I have a server in the house that shares files. I know it's up and can ssh into it can read it's files from other computers just not this one.

Do you keep posting this on purpose?  Again, you should check the firewall to make sure that connections are allowed both in and out on the samba port.

---

### Post by Davez69gto on 2008-12-20
Nevermind.  I just shut off the firewall.  I thank all of your for your help.

---

### Post by monkeyking on 2008-12-21
> **pytheas22 said:**
> 
Do you keep posting this on purpose?  

I was thinking the same,
strange behavior indeed

---

