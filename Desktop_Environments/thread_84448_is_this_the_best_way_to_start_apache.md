---
title: "is this the best way to start apache?"
date: 2005-10-31
forum: Desktop Environments
---

### Post by pabc on 2005-10-31
on compiling apache I left the installation directory as default, ie /usr/local/ meaning I could only do the make install as root.

Now I can only start the service as root.

My machine autologs in to my normal user account and I've given permissions via /etc/sudoers for me to run apache without a sudo password. Finally I added;
'sudo /usr/local/apache2/bin/apachectl start' to the my startup.

'netstat -tap' shows its working.

Are there any obvious problems with this way of doing things? Is there a better way?

Any thoughts appreciated.

P

---

### Post by bdash on 2005-10-31
The best way to start Apache:

```

sudo /etc/init.d/apache start

```

You can control the automatic execution of Apache from System->Administration->Services.

---

### Post by pabc on 2005-10-31
except it doesnt show up in services.

I'm guessing because I installed from source rather than from apt-get it isnt there.

Equally, 'sudo /etc/init.d/apache start' results in command not found

I would have much prefered it to do it via synaptic but apache2 isnt on my breezy CD and I have to net connection yet to get it off one of the other repos.

Strangly apache2-common is on the CD.

P

---

