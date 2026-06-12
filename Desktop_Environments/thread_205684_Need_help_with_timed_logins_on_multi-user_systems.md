---
title: "Need help with timed logins on multi-user systems"
date: 2006-06-28
forum: Desktop Environments
---

### Post by ardchoille on 2006-06-28
I build computers, install a Linux Ubuntu 6.06 and then donate the computers to friends and family - and, at times, businesses. I donated one to a friend who has a large home and rents out the rooms. She has two tennants who "live" on the computer, one of them for sometimes up to 14 hours straight, and her other tennants complain that they cannot use the box. She has tried signup sheets and eviction threats and those didn't help. She has asked me to start a type of "timed logins" setup with the following rules:

1. Each user can login and use the computer for one hour at a time.
2. When that users' time is up, they cannot log back in until two hours have passed.

Now, I realise there may be apps that can easily do this but these computers are usually PII and PIII and they don't operate at the greatest speeds. So, I am wondering if there is a way I can use apps that are already installed (ex: cron, date, etc.) to set this type of thing up for her.

Anyone have any ideas?
Are there any apps in the repos that would do this easier than I can with existing apps?

---

### Post by Maggot on 2006-06-28
After a quick search:
```

4.4.    Root Account
The root account is the most privileged account on a UNIX system. When the administrator
forgot to logout from the system root prompt before leaving the system then the system should
automatically logout from the shell. A special variable in Linux, ‘TMOUT’, must be set in
/etc/profile to use the feature.
Edit the /etc/profile file:
# vi /etc/profile
Add the following lines:
"HISTFILESIZE="
"TMOUT=3600"
 
The value entered for the variable "TMOUT=" is in second and represent 1 hours (60 * 60 =
3600 seconds). By adding the line in /etc/profile, automatic logout after one hour of inactivity
will apply for all users on the system. Setting this variable in user's individual ".bashrc " file will
automatically logout them after a certain time.
After this parameter has been set on the system, re-login is required for the changes to take
effect.
```

They say this is for when in a terminal, so will it work while in a GUI? I don't know.

---

### Post by ardchoille on 2006-06-28
[QUOTE=Maggot]After a quick search:
```

4.4.    Root Account
The root account is the most privileged account on a UNIX system. When the administrator
forgot to logout from the system root prompt before leaving the system then the system should
automatically logout from the shell. A special variable in Linux, ‘TMOUT’, must be set in
/etc/profile to use the feature.
Edit the /etc/profile file:
# vi /etc/profile
Add the following lines:
"HISTFILESIZE="
"TMOUT=3600"
 
The value entered for the variable "TMOUT=" is in second and represent 1 hours (60 * 60 =
3600 seconds). By adding the line in /etc/profile, automatic logout after one hour of inactivity
will apply for all users on the system. Setting this variable in user's individual ".bashrc " file will
automatically logout them after a certain time.
After this parameter has been set on the system, re-login is required for the changes to take
effect.
```

They say this is for when in a terminal, so will it work while in a GUI? I don't know.[/QUOTE]

Does that apply to "inactivity" only?

---

### Post by Maggot on 2006-06-28
Ooppss. Yeah. :-\"

---

### Post by ardchoille on 2006-06-29
Bump

---

