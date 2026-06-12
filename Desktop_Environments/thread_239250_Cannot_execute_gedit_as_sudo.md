---
title: "Cannot execute gedit as sudo"
date: 2006-08-19
forum: Desktop Environments
---

### Post by akarimco on 2006-08-19
I just noticed that I can no longer execute gedit along with the sudo command (sudo gedit /etc/somefileiwannachange).  I just now finished installing Ubuntu on my desktop (been on my laptop for some time now with no problems) and getting all of the latest updates and whatnot, and I wanted to switch over to OpenDNS, but I can't change the files without gedit, or rather I don't want to because I like gedit!  Any help?  I'm just starting to get my feet wet with the command line, and I'd hate for this to spoil it!

---

### Post by meng on 2006-08-19
Any luck with gksudo gedit? gksu gedit?

---

### Post by akarimco on 2006-08-19
Nope, and I'm finding that several items in my System/Administration menu aren't working either, like User Settings, which is where I think my mistake may have been made.  I'm basically stuck without any administrator rights at the moment.

---

### Post by taurus on 2006-08-19
What groups do you belong to?  You need to belog to both adm & admin in /etc/group...

```
id
```

---

### Post by akarimco on 2006-08-21
I'm no longer under either of those... it worked at first and then just randomly decided I didn't need admin privelages I guess.  How can I change that if I can't get into any admin settings?

---

### Post by akarimco on 2006-08-21
I figured out what I did... I still don't know how to fix it though.  I initially set up Ubuntu with a user called "desktop" and then later created accounts for me (akarimco) and my roommate (akisho) and deleted "desktop".  Since desktop was the initial login created with the install, it had admin rights, but now it's gone and I don't know what to do!

---

### Post by jackn on 2006-08-21
Restart and choose 'Recovery Mode' from GRUB.

You'll be root, on the console, no GUI.


Before actually carrying out the necessary modifications, backup the file which you're going to modify, /etc/group. 

```
cp /etc/group /etc/group_backup
```


Now changes can be carried out:
```
adduser <user_name> <group_name>
```

In your case, 
```
adduser <user_name> adm
```
```
adduser <user_name> admin
```

When done, 

CTRL-ALT-DEL

in order to reboot with administrative privileges this time around.

Jackn

---

### Post by Lord Illidan on 2006-08-21
Just a question, what is the difference between adm and admin?

---

### Post by ComplexNumber on 2006-08-21
> **akarimco said:**
> I figured out what I did... I still don't know how to fix it though.  I initially set up Ubuntu with a user called "desktop" and then later created accounts for me (akarimco) and my roommate (akisho) and deleted "desktop".  Since desktop was the initial login created with the install, it had admin rights, but now it's gone and I don't know what to do!
basically, you need to add you and your roommate to the list of sudo's(ie the people that can run sudo with admin rights). you can only add them by using /sbin/visudo, so you need to run that command from the commandline as root. but you say that you can't get admin rights, which, as far as my knowledge goes, leaves you a bit stuck. maybe someone else can point you in the right direction. however, once you have found out how to get admin rights, you will have to add yourself to the sudoers list.
when you run /sbin/visudo, that will then bring up a horrendously bad(IMO editor called vi. in visudo, you will see something like "root   ALL=(ALL) ALL"(or something like that. press the 'i' key. this will allow you to enter stuff. immediately below where it says "root ALL=......", write exactly the same, but instead of "root", have your username.then press the ESCAPE key to get out of insert mode. then type "XX". then will save and exit the file. then you can use sudo.

---

### Post by akarimco on 2006-08-21
hroit's method worked like a charm!  Thanks!  Got another problem, so keep an eye our for the new post, lol!

---

### Post by ComplexNumber on 2006-08-21
<accidental double post. please delete>

---

### Post by ComplexNumber on 2006-08-21
> **akarimco said:**
> hroit's method worked like a charm!  Thanks!  Got another problem, so keep an eye our for the new post, lol!
can you use sudo now?

---

### Post by jackn on 2006-08-22
Lord Illidan's question points out to me that I just followed Taurus's advice without finding out for myself what adm and admin meant.

Don't have a definitive answer, but some observations. Would love to learn where the privileges of different groups are listed (They are *not* in the Sys>Admin>Users and Groups GUI menu).

As to what groups one ought to belong to, [psychocats]("http://www.psychocats.net/ubuntu/sudo.php") has a nice page (and site) shedding some light on this:
'The /etc/sudoers file should look the same for every Ubuntu user who hasn't fiddled with it:...
```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```
It basically says anyone who is root can do anything, and anyone in the administrative group (people who can sudo) can do anything (with a password).'

For our purposes, then, and to take psychocats' word for it, belonging to 'admin' basically means being able to 'sudo'.

Indeed, the well-known [RootSudo Ubuntu page]("https://help.ubuntu.com/community/RootSudo"), which explains the sudo policy, says: 

'To add a new user to sudo...
```
sudo adduser $user admin
```
where you replace $user with the name of the user.'

It seems, therefore, that, to grant sudo usage, adding a user to 'admin' will do.

'id', though, tells me that my user belongs to both 'admin' and 'adm'.
As to the adm group, [debian.org ]("http://www.debian.org/doc/manuals/securing-debian-howto/ch12.en.html")says:

'adm: Group adm is used for system monitoring tasks. Members of this group can read many log files in /var/log, and can use xconsole. Historically, /var/log was /usr/adm (and later /var/adm), thus the name of the group....'
And 'The 'adm' group are usually administrators, and this group permission allows them to read log files without having to su.'

Belonging to the 'adm' group adds an additional bit of convenience, namely the perusal of system logs as user. Not belonging to adm would require you to sudo.

Jackn

---

