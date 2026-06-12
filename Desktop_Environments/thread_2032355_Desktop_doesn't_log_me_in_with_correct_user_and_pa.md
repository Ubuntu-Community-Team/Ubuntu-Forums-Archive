---
title: "Desktop doesn't log me in with correct user and password"
date: 2012-07-23
forum: Desktop Environments
---

### Post by naveenurs on 2012-07-23
Hi,

I installed 12.04 LTE server on my desktop. After that I installed ubuntu-desktop on top of it. Now, I have a strange problem.

I provide the correct credentials and hit enter. However, it will not log me in. It goes back to the login screen. When I use the credentials at command line I am able to login without any issues.

How do I figure out what is wrong? Where will it log the warnings / errors related to Unity desktop?

I tried logging in using the "Guest" user id. That worked.

---

### Post by steeldriver on 2012-07-23
sounds like it is authenticating OK but for some reason cannot start your desktop session - sometimes this is because of an ownership / permissions issue with your .Xauthority file

when logged in as yourself at the console / virtual terminal do

```
ls -l ~/.Xauthority
```and if it's owned by root then

```
sudo rm ~/.Xauthority
```and then try again

If that's not the issue then the place to start looking would probably be the greeter log, /var/log/lightdm./x-0-greeter.log

---

### Post by naveenurs on 2012-07-23
Thanks!

The ~/.Xauthority was owned by root. The greeter.log didn't show much. So, I thought let me remove the ~/.Xauthority file and see what happens.

Once I removed, I got the following:
Could not update ICEauthority file /home/naveenurs/.ICEauthority

I changed its permission to 777. Once this was done, it started telling me that I didn't have the proper permissions on  ~/.config directory. So, I gave it a 777 as well. With this, it has started working.

I did these changes blindly without understanding what .Xauthority, .ICEauthority files represent along with .config. 

Can you please tell me what these files are and what security threat am I open to by opening these to the world?

---

### Post by steeldriver on 2012-07-23
I didn't mention ~/.ICEauthority because I've never been sure what it does, but afaik you can delete (sudo rm) that one as well if it becomes root owned - that's probably better than leaving it root owned but giving it rwx permissions

both files are supposed to be owned by the session user (you) and -rw------ i.e. mode 600

---

### Post by naveenurs on 2012-07-23
Thanks! Looks like something had got messed up. So, I created another SA account and then dropped the original account that I had created at the time of installation. 

The new SA works without any issues. Thanks again!!!

---

