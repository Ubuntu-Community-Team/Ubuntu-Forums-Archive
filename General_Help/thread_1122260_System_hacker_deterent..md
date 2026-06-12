---
title: "System hacker deterent."
date: 2009-04-10
forum: General Help
---

### Post by gmanigault on 2009-04-10
Questions.   I need some help.  My systems are secure but I am getting tired of the attempts.  Here is what I want to do.  

[LIST]
[*]I would like to have and automated script of sh to scp the intruders /ect/passwd file.
[*]Can that be done?
[*]If so what does the script have to be called to automatically execute?
[*]Does the user have to successfully logon?
[*]If that is not possible can I setup a script to at least get the users IP and scan their system for intimidation?
[/LIST]

My systems are secure and have been online and tested for over 90 days before going live.  Any help would be appreciated? The free testing from uninvited guests is great but I now want to go a step further.  


If that is not possible can I do the following setup a cron job that will scan the syslog periodically for attempts and harvest ip addresses, and email me when a successful logon was achieved?  Thanks. 

Shark

---

### Post by gmanigault on 2009-04-11
[B]NO takers on this one?
[/B]
> **gmanigault said:**
> Questions.   I need some help.  My systems are secure but I am getting tired of the attempts.  Here is what I want to do.  

[LIST]
[*]I would like to have and automated script of sh to scp the intruders /ect/passwd file.
[*]Can that be done?
[*]If so what does the script have to be called to automatically execute?
[*]Does the user have to successfully logon?
[*]If that is not possible can I setup a script to at least get the users IP and scan their system for intimidation?
[/LIST]

My systems are secure and have been online and tested for over 90 days before going live.  Any help would be appreciated? The free testing from uninvited guests is great but I now want to go a step further.  


If that is not possible can I do the following setup a cron job that will scan the syslog periodically for attempts and harvest ip addresses, and email me when a successful logon was achieved?  Thanks. 

Shark

---

### Post by Dr Small on 2009-04-11
Install and configure DenyHosts.

---

### Post by whoop on 2009-04-11
maybe?
```

sudo tail -F /var/log/auth.log | grep sshd

```

Why don't you just use key based authentication and disable all login/password authentication. It's much safer, if you don't count debian's little blunder.

---

### Post by iponeverything on 2009-04-11
> **gmanigault said:**
> Questions.   I need some help.  My systems are secure but I am getting tired of the attempts.  Here is what I want to do.  

[LIST]
[*]I would like to have and automated script of sh to scp the intruders /ect/passwd file.
[/LIST] 
not without having the login and passwd for their machine.
> 
[LIST]
[*]Can that be done?
[/LIST] 
see above
> 
[LIST]
[*]If so what does the script have to be called to automatically execute?
[/LIST] 
running services from xinetd will allow you to follow the service invocation with a command invocation.
> 
[LIST]

[*]Does the user have to successfully logon?
[/LIST] 
no
> 
[LIST]

[*]If that is not possible can I setup a script to at least get the users IP and scan their system for intimidation?
[/LIST] 

yes. but your assuming that its a person. 99% of the time it is an automated script running from what is probably a compromised machine where the owner has no idea what is going on.  You will fill the logs on the machine with your intimidation, get mistaken for person actually compromised the machine -- and you will have the feds in ski masks at your door. (if say, for example this machine has certain things on it)   

If you want to play these games, you should know that stakes are quite high.

> 
My systems are secure and have been online and tested for over 90 days before going live.  Any help would be appreciated? The free testing from uninvited guests is great but I now want to go a step further.  

If that is not possible can I do the following setup a cron job that will scan the syslog periodically for attempts and harvest ip addresses, and email me when a successful logon was achieved?  Thanks. 

Shark

It's easy to roll your own script for this. You could even have your system automatically mail you with every login attempt successful or not.

Again, I caution you against automated retaliation or intimation as you may very easily find yourself the target of something far less benign that a port scan.

---

