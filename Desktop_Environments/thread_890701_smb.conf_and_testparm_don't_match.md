---
title: "smb.conf and testparm don't match"
date: 2008-08-15
forum: Desktop Environments
---

### Post by PatricC999 on 2008-08-15
I'm using ubuntu 8.04 and am trying to configure samba.  However, whenever I change smb.conf and then use testparm to make sure everything is alright, some of the lines just don't show up in testparm.  At first I just used the config file that samba installs with but when I tried to change my workgroup name, the workgroup line in testparm disappeared.  I even went with the barebones minimum example in the samba docs and it doesn't work right.  Here is my smb.conf:

```
# Global parameters
  [global]
  workgroup = WORKGROUP
  netbios name = HOBBIT
  security = user
  [data]
  comment = Data
  path = /export
  read only = Yes
  guest ok = Yes
```

And this is the testparm output:
```
Load smb config files from /etc/samba/smb.conf
Processing section "[data]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        netbios name = HOBBIT

[data]
        comment = Data
        path = /export
        guest ok = Yes

```

The samba docs show that every line should show up in testparm and samba isn't working at all even with the very simple config file.  Thank you for any help.

Edit: Also if anyone could help me with another samba thing, I'm setting up this computer as a file server for my roommates and myself.  I have one group of folders that I want everyone to be able to see and add to and then each person have their own home folder available only to them.  When I tried setting it up before I could only get myself to log in to view files from my windows box and no other user was able to even log in.

---

### Post by Maineac54 on 2010-09-26
Has any one got an answer to this problem?  I have the same issue on a Debian Linux server.

---

### Post by sikander3786 on 2010-09-26
Here is the result of testparm from a default samba config file.

```

[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

```

I don't see workgroup showing up in there anywhere. :-)

Are you using Ubuntu or Kubuntu 8.04? I see both of them being mentioned in your post.

That testparm result is not a problem. What is the actual problem? You can't connect from other PCs? What happens then? And can you ping from other PCs to your Samba PC?

If you want to, you can also use system-config-samba, the gui for configuring Samba. It shows up under System > Administration > Samba and takes care of the configuration file itself. I have been using it for quite some time for now and works for me.

---

### Post by shutdown -h now on 2011-02-01
I have exactly the same problem on Slackware 13 with samba 3.2.15. It doesn't print a few commands in testparm and it also fails to use them, e.g.: 'security = user', 'map to guest = Never', 'guest ok = No'

smb.cfg:
```
#       netbios name = Slackbox
        name resolve order = bcast host lmhosts wins
        server string = Server
        log file = /var/log/samba.%m
        max log size = 50
        dns proxy = No
        hosts deny = ALL
        hosts allow = 192.168.1., 127.
        security = User
        encrypt passwords = Yes
        local master = Yes
        preferred master = Yes
        os level = 65
        use client driver = Yes
        map to guest = Never
        guest ok = No
```testparm:
```
[global]
        workgroup = VERREIJT
        server string = Server
        log file = /var/log/samba.%m
        max log size = 50
        name resolve order = bcast host lmhosts wins
        os level = 65
        preferred master = Yes
        dns proxy = No
        hosts allow = 192.168.1., 127.
        hosts deny = ALL
        use client driver = Yes
```Does anyone know the answer to this? It's a big problem because this way I am not able to prevent guest users and everyone can access files from other users.

---

### Post by Morbius1 on 2011-02-01
testparm is an interpreter. It simulates what will happen if you actually run smb.conf. It also won't list things that are there by default.

For example. Let's say you explicitly list "security = user" in your smb.conf. "security = user" is the default so when you run testparm it won't list it.

If you wan't to see all the parameters set as the default then run the following command:
```
testparm -sv
```When you do you will see an item:
"security = USER"

---

