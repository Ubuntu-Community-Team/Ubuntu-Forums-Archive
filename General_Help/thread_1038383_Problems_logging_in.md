---
title: "Problems logging in"
date: 2009-01-12
forum: General Help
---

### Post by mcscrwdy25 on 2009-01-12
Hello everyone! I am having problems logging into Ubuntu. I have never been able to log into Ubuntu or any of its derivatives and I cant find anything on the web to help. I have a Dell Dimension 4500s if that helps anything. If anyone knows how to help it would be appreciated!

---

### Post by bodhi.zazen on 2009-01-12
Boot to recovery mode.

This will give you a command line interface, but you will be root.

then

```
ls /home
```

This will give you a list of the username(s) on the system

Then set a new password

```
passwd user_name
```

where user_name is the user you are trying to log in as

Re-boot

If that does not work, can you provide a better description of your issue ?

---

### Post by Muldarfbi on 2009-01-13
I have almost the same problem...when I type ls /home....nothing happens, no letters shows up on the prompt, and my keyboard works fine...

Thanks in advance for the help...
Muldar,  ):P

---

### Post by mcscrwdy25 on 2009-01-14
Sorry I didn't provide a good description of the problem. When I log in my computer freezes. I can still move the mouse but nothing shows up on the screen. (I know I have my user name and password right) When I try the failsafe option an error message pops up and saying it can't be started. Yesterday I got Ubuntu studio to log in, but I think GNOME did not start properly because I only have a top task bar and the only things on it is the time and the "start" menu, in addition I have problems having the computer recognize the internet. Thanks for the help!

---

### Post by Sabayon on 2009-01-14
Did you ever reinstall?

---

### Post by mcscrwdy25 on 2009-01-14
Yea I have tried to reinstall and I got the same thing.

---

### Post by bodhi.zazen on 2009-01-14
> **mcscrwdy25 said:**
> Sorry I didn't provide a good description of the problem. When I log in my computer freezes. I can still move the mouse but nothing shows up on the screen. (I know I have my user name and password right) When I try the failsafe option an error message pops up and saying it can't be started. Yesterday I got Ubuntu studio to log in, but I think GNOME did not start properly because I only have a top task bar and the only things on it is the time and the "start" menu, in addition I have problems having the computer recognize the internet. Thanks for the help!

sounds like a hard ware problem.

Either insufficient RAM or video card incompatibility.

How much RAM do you have ?

What video card ?

---

### Post by relativity1905 on 2009-01-15
He,

I have sometimes the same problem with a Toshiba Satellite and Ubuntu 8.10. Previously I had an old Suse version (can't remember which) installed, without having this problem.
Today it was like the following: Yesterday I used the notebook with an external mouse. Today I wanted to start it using just the touchpad - the problem occured. Then I restarted it but plugged the external mouse in and it worked fine. Could this be a problem with the touchpad driver?

Thanks for your help.

---

### Post by bodhi.zazen on 2009-01-15
> **relativity1905 said:**
> He,

I have sometimes the same problem with a Toshiba Satellite and Ubuntu 8.10. Previously I had an old Suse version (can't remember which) installed, without having this problem.
Today it was like the following: Yesterday I used the notebook with an external mouse. Today I wanted to start it using just the touchpad - the problem occured. Then I restarted it but plugged the external mouse in and it worked fine. Could this be a problem with the touchpad driver?

Thanks for your help.

Sounds like it may be a hardware problem (ie with the touchad). I do not know how to fix it but a google search may help you.

---

