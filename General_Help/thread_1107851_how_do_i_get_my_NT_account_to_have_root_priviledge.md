---
title: "how do i get my NT account to have root priviledges"
date: 2009-03-27
forum: General Help
---

### Post by lithiumKid1976 on 2009-03-27
Hi 
im using 8.10
i have joined my machine to the domain.
i can sucessfully loging using my NT account, 

but when i open a terminals i get

*id: cannot find name for group ID xxxxxxxxx*

and when i try to set the time and date, or users and groups i get the following

[I]"the configuration could not be loaded."
"you are not allowed to access the system configuration"[/I]

if any one can help me on this id appreciate it.
Regards
Damien

---

### Post by aeiah on 2009-03-27
you should probably google for confirmation, but you probably need to add your user and group to the system and set them to have the same privs as a default user, with access to sudo too.

---

### Post by albandy on 2009-03-27
what are you using, winbind or likewise?

---

### Post by lithiumKid1976 on 2009-03-27
Hi
Its likewise i installed.

Regards
Damien

---

### Post by albandy on 2009-03-27
Don't use likewise form repositories, it's buggy. unistall and download it from likewise page
when installed you need to assign privilegies to your domain user to do administrative task, so log in as your local user and do 
sudo adduser domain\\user adm
sudo adduser domain\\user admin
sudo adduser domain\\user [........]

---

### Post by wydileie on 2009-03-27
I actually have the same problem and the 

```
sudo adduser domain\\username admin
```

does not work. I added my domain account to few of the groups, but when I type id to see my groups, none of the ones I added myself to actually show up. I tried adding my Active Directory given group names and numbers to the sudoers file, which works for the names, but sometimes the names do not get passed. When that happens I still have the group numbers but the group numbers do not work in the sudoers file. Example of what I tried:

```
%<group_number> ALL=(ALL) ALL
```

Edit:
The top code does work, actually. I was using the wrong form for my username. However this still does not solve my problem because my ultimate goal is to have the ability to remove people's ability to sudo on their box, or change their sudo permissions if need be. To do that easily I need to be able to have a sudoers file based on my Windows group name or more preferably group numbers so I don't have to change it on every box individually.

---

### Post by lithiumKid1976 on 2009-03-27
> **albandy said:**
> Don't use likewise form repositories, it's buggy. unistall and download it from likewise page
when installed you need to assign privilegies to your domain user to do administrative task, so log in as your local user and do 
sudo adduser domain\\user adm
sudo adduser domain\\user admin
sudo adduser domain\\user [........]



Hi.
i uninstalled it using the terminal and the software updater.
then i installed the software from the website, and the join domain command ran succesfully.


but, when trying to log on with my nt account i get a "authentication failed" error

tried it with my account and the domain account, both couldnt connect. any ideas?
Thanks
damien

---

### Post by wydileie on 2009-03-27
Most likely your time sync is off and you can't authenticate through Kerberos, which I assume you are using. 

As a quick fix you can go run:
```
sudo /usr/sbin/ntpdate <your_server_address>
``` which should update your clock for you right away. 

To fix it permanently, go to your local account and go to the time and date settings in the Administrator menu. Set it to update automatically.

Then open a text editor on /etc/default/ntpdate and find the following lines of code and replace the example server name with your domain server. Also make sure the NTPDATE_USE_NTP_CONF is set to no since you are specifying your own server.

```
# servers to check
NTPSERVERS="win2k3.example.com"
# additional options for ntpdate
NTPOPTIONS="-u"
```

Once you are done with that, it should automatically sync periodically and should allow you to log in to your other account. 

Also, just make sure when you are trying to log in using your domain name you are doing DOMAIN\username and not just the username.

---

### Post by lithiumKid1976 on 2009-03-27
> **wydileie said:**
> Most likely your time sync is off and you can't authenticate through Kerberos, which I assume you are using. 

As a quick fix you can go run:
```
sudo /usr/sbin/ntpdate <your_server_address>
``` which should update your clock for you right away. 

To fix it permanently, go to your local account and go to the time and date settings in the Administrator menu. Set it to update automatically.

Then open a text editor on /etc/default/ntpdate and find the following lines of code and replace the example server name with your domain server. Also make sure the NTPDATE_USE_NTP_CONF is set to no since you are specifying your own server.

```
# servers to check
NTPSERVERS="win2k3.example.com"
# additional options for ntpdate
NTPOPTIONS="-u"
```

Once you are done with that, it should automatically sync periodically and should allow you to log in to your other account. 

Also, just make sure when you are trying to log in using your domain name you are doing DOMAIN\username and not just the username.



thanks for your reply, ive carried out all the instructions above, but am still getting the "authentication failed" error....

---

### Post by albandy on 2009-03-27
could you paste the command used to join the domain? I'm thinking that something was not uninstalled, the likewise from original page installs in /opt

---

### Post by lithiumKid1976 on 2009-03-31
Hi

sorry about the delay in replying

the command i used was

sudo /opt/likewise/bin/domainjoin-gui join Institute/Administrator

this fired up the likewise GUI program, and from here i was able to join this machine to the domain. i checked under active directory, and the machine is listed there.

but it still gives me the "authentication failed" error when trying to log on.
Regards
Damien

---

### Post by albandy on 2009-03-31
do a tgz of your /etc/pam.d and attach it here, I need to see if likewise made the required modifications.

it's possible that the previous likewise installation modified it, so if this is the case you should uninstall likewise, restore pam.d files (you can restore it from another ubuntu installation) and reinstall likewise.

---

### Post by lithiumKid1976 on 2009-03-31
ok. i hope this is correct ...

---

### Post by albandy on 2009-03-31
if got likewise running in my machine and working, I'll send you my pam.d files. Simply replace it, now I'm at home.

---

### Post by albandy on 2009-04-02
Here it is:

---

### Post by lithiumKid1976 on 2009-04-07
the new version of likewise (5249) sorted this issue.
i no longer get that error when using the terminal or other apps.

---

