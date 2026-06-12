---
title: "root password"
date: 2005-12-15
forum: General Help
---

### Post by dudds on 2005-12-15
What is the root password for an installation? I cannot get to administrator mode for example to setup my network configuration. When asked for a password the only one I put in is the one for my user account then I get the error message "Conversation with su failed"

It's really frustrating!! I also cannot su to root as it appears I don't know the password.....and wasn't asked to input one during the normal install process.

I then reinstalled using the following command "linux debconf/priority=medium" which allowed me to add the root user, but still I cannot get the "administrator mode" access working with the network configuration GUI. I only managed it this time by being able to su to root and then run the ifup command.

I'm probably doing something real dumb, as I have installed ubuntu / kubuntu over the past couple of days which has worked. The wierd thing was that it seemed to stop when I closed my laptop the other day and when it came out of standby/hibernation I had all these wierd problems which caused me to reinstall.

Things have not been the same since and I can't work out why.

---

### Post by 23meg on 2005-12-15
The root account is disabled by default. You should prefer using sudo instead. You can manually enable the root account with ```
sudo passwd root
```

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by aysiu on 2005-12-15
Did you do an expert install? If so, that's part of the problem.
A regular install will give you one user with sudo privileges.
You should be able to just put your user password in and get administrative privileges temporarily.

---

### Post by 23meg on 2005-12-15
It could help if you posted the content of your /etc/hosts file.

---

### Post by dudds on 2005-12-16
I worked out a solution to my problem, but I don't really know if this is the right solution or not. I added my user account to the /etc/sudoers file and now when I click on the "Administrator Mode" button I don't even have to enter a password. I also added my user account to the sudo section of the /etc/group file.

Not sure what these files are doing as I have only installed Kubuntu a couple of days ago, but hey it works.

It the reason that the "Administrator Mode" stopped working because I reinstalled the system and used a new user account, but didn't delete/reformat the /home partition when I did the reinstall.

grrr very frustrating.

---

### Post by dudds on 2005-12-16
I now have the system working as I did the first time I installed. I have my account in the /etc/sudoers file and have removed it from the /etc/group file sudo section.

Now when I press the "Administrator Mode" button I am asked to enter my password.

---

