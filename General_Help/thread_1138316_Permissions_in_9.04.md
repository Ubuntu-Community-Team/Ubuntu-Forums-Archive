---
title: "Permissions in 9.04"
date: 2009-04-26
forum: General Help
---

### Post by And1945 on 2009-04-26
hI,

I just wanted to know why it is that I have to spend such a long time looking for stuff I can not find.

Since my search didnt really return anything, i suppose i am the only one with this problem.

During install of 9.04 I created a user, because that is what it wants you to. The problems is, he has permission to do absolutely bobkiss. The password I gave it during install unlocks somethings, but it wont allow me to create a damn folder in /var/www/ ... what gives? Isnt there some command that just copies root permissions to my user?

---

### Post by spiderbatdad on 2009-04-26
```
sudo -i
```will give you a root terminal session to create files and directories in the root file system. If you prefer to work graphically, run ```
gksu nautilus
```beware of permissions when you are done. Generally files in /var/www are owned by www-data and a member of the same group, not root, nor $user. Alternatively, change the directory apache looks for to something like ~/my_www, and edit directories and files as yourself.

---

### Post by And1945 on 2009-04-26
Thanks, but that is just a tempoary fix. I go to school, where we learn to make websites, so its kinda frustrating, that I dont have root access to EVERYTHING.

It feels like having a babysitter. I dont remember the "permissions" beeing so brutal in 8.10.

Would it help if I was to add myself to all excisting groups on my computer?

---

### Post by spiderbatdad on 2009-04-26
the permissions have not changed. users always have to use sudo for commands requiring root permission, or sudo -i to start a root session...this is the ubuntu security model. becoming root should be a familiar procedure for anyone authoring apache config files.

It wouldn't help to add yourself to all groups as the root password is locked by default...so you would not have a login to that account. Please stick with sudo to avoid breaks in forum policy or seek advice on root passwords elsewhere.

---

### Post by ugriffin on 2009-04-26
EDIT: Nvm... above makes my answer obsolete and silly.

---

### Post by luisfpg on 2009-04-26
Or, in this specific case, you could change the /var/www ownership to your user.
Supposing your user is bob, run:
*sudo chown bob:bob /var/www*

Another tip to make it even easier to work afterwards is to make a link for it in your home, so you don't need to always navigate to that folder:
*ln -s /var/www $HOME*

---

### Post by And1945 on 2009-04-26
I wasnt aware that root passwords where a slight infringement of forum rules. I apologize for that.

The reason why i am asking these things, is because I cant recall having such "problems" with this.

If the following question is against forum rules, please ignore it.
There is no way to acquire constant root access from a standard user account without having to use 'sudo su' in terminal?

> **luisfpg said:**
> Or, in this specific case, you could change the /var/www ownership to your user.
Supposing your user is bob, run:
*sudo chown bob:bob /var/www*

Another tip to make it even easier to work afterwards is to make a link for it in your home, so you don't need to always navigate to that folder:
*ln -s /var/www $HOME*

I will look into this. Thank you. Might scratch my itch.

---

### Post by danwood76 on 2009-04-26
There is a way but you shouldnt need to do it.

To make a file you can edit your web pages in just make a symbolic link in the /var/www folder to a folder in  your home.
Or if you are familiar with configuring apache change the config files to point there.

You should never have to use root permissions in your everyday computing, the security is set like that for a reson.
The more you use sudo the more chance of breaking your system.

---

### Post by And1945 on 2009-04-26
> **danwood76 said:**
> There is a way but you shouldnt need to do it.

To make a file you can edit your web pages in just make a symbolic link in the /var/www folder to a folder in  your home.
Or if you are familiar with configuring apache change the config files to point there.

You should never have to use root permissions in your everyday computing, the security is set like that for a reson.
The more you use sudo the more chance of breaking your system.

That about breaking Ubuntu, I knew. It just annoys me, because i feel im using more time with permissions than actual work.

I suppose that's it... that's my problem I guess :)

But an option, a button somewhere that gives you full root for 1 min or so, and then returns... that might be more time efficient.

---

### Post by danwood76 on 2009-04-26
sudo gives you this function!

---

### Post by spiderbatdad on 2009-04-26
to clarify: using sudo does not break your system. issuing destructive commands as root can do that.

---

### Post by And1945 on 2009-04-27
@danwood

i know what sudo does.

Okay, so i just have to chmod things via terminal... oki dokes. Still beats Windows.

---

