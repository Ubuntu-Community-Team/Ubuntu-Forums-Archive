---
title: "Problems with polkit"
date: 2020-05-10
forum: Desktop Environments
---

### Post by crono1412 on 2020-05-10
Hey all.  I'm having a big problem with ubuntu desktop environments. I'm running stock ubuntu 19.10, with cinnamon as the environment (which I switched to as part of troubleshooting this issue). The dialog for elevated privileges never appears for anything (system updates, programs that require sudo like gparted).  Ive traced it to the polkit, but haven't had any luck troubleshooting it.  Anytime the polkit agent should pop up, it crashes.  Here's the relevant apport.log

```
ERROR: apport (pid 4655) Sun May 10 09:43:44 2020: called for pid 1213, signal 11, core limit 0, dump mode 1
ERROR: apport (pid 4655) Sun May 10 09:43:44 2020: executable: /usr/lib/policykit-1/polkitd (command line "/usr/lib/policykit-1/polkitd --no-debug")
ERROR: apport (pid 4655) Sun May 10 09:43:44 2020: is_closing_session(): no DBUS_SESSION_BUS_ADDRESS in environment
ERROR: apport (pid 4655) Sun May 10 09:43:44 2020: apport: report /var/crash/_usr_lib_policykit-1_polkitd.0.crash already exists and unseen, doing nothing to avoid disk usage DoS
```

I tried to check the crash dump, but it was all greek to me.  I tried reinstalling everything polkit related, but that didn't get me anywhere.

I also noticed an error with regard to DBUS_SESSION_BUS_ADDRESS not being set, so I chased that for awhile, but I don't think there's actually anything wrong. 

```
echo $DBUS_SESSION_BUS_ADDRESS
unix:path=/run/user/1000/bus

```

which is correct as far as I can tell.  Short of wiping the system and reinstalling, I have no idea how to fix this, and I'd rather not do that. Does anyone have any idea what's going on here, or how to fix it?  Let me know what other info you might need to help me troubleshoot.  Thanks in advance.

---

### Post by crono1412 on 2020-05-13
Does anyone have any ideas?

---

### Post by CelticWarrior on 2020-05-13
Reinstalling will probably be faster than troubleshooting this.

---

### Post by crono1412 on 2020-05-27
Here's the crash dump, if anyone is interested.

[https://drive.google.com/open?id=1lvt9A6oljiBDf9YS8u5OAh4uot1rzOfQ](https://drive.google.com/open?id=1lvt9A6oljiBDf9YS8u5OAh4uot1rzOfQ)

---

### Post by crono1412 on 2020-05-27
Found the problem.  I followed the direction of the post here

[https://unix.stackexchange.com/questions/417906/authentication-is-required-to-create-a-color-profile](https://unix.stackexchange.com/questions/417906/authentication-is-required-to-create-a-color-profile)

About color profiles, and being bugged for a password to create them on every login.  Well, the script there was crashing polkit.  Removing it solved the problem, and I guess the upgrade to 20.04 solved the nagging color profile prompts.

---

