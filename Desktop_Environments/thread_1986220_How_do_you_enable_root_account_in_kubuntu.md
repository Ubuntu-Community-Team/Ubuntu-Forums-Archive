---
title: "How do you enable root account in kubuntu?"
date: 2012-05-24
forum: Desktop Environments
---

### Post by Pally1 on 2012-05-24
This guide does not work

<snip>

last command results in

sh: 1: cannot create /etc/lightdm/lightdm.conf: Directory nonexistent

---

### Post by MG&amp;TL on 2012-05-24
As far as I know, Kubuntu doesn't use LightDM, but KDM instead. You'll need to google a guide for that.

Would like to point out that *sudo* and friends are there for a reason...on your head be it...;)

---

### Post by sisco311 on 2012-05-24
Please check out: 
[uhelp]community/RootSudo[/uhelp]

[thread=716201]Forum policy on log-in-as-root tutorials[/thread] ("old" sticky by [[COLOR=#d40000]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941")).
and
[thread=1486138]Forum policy on log-in-as-root tutorials[/thread] ("new" one by [**[COLOR="DarkRed"]bodhi.zazen[/COLOR]**]("http://ubuntuforums.org/member.php?u=89054"))

Why are you trying to log in to the GUI as root?

---

### Post by Pally1 on 2012-05-24
> **sisco311 said:**
> Please check out: 
[uhelp]community/RootSudo[/uhelp]

[thread=716201]Forum policy on log-in-as-root tutorials[/thread] ("old" sticky by [[COLOR=#d40000]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941")).
and
[thread=1486138]Forum policy on log-in-as-root tutorials[/thread] ("new" one by [**[COLOR=DarkRed]bodhi.zazen[/COLOR]**]("http://ubuntuforums.org/member.php?u=89054"))

Why are you trying to log in to the GUI as root?


So that i can do some very basic things.

Cmon ppl seriously? This is why you are loosing to windows, it takes forever to do something as basic as creating a folder in xampp which takes only two clicks in windows, but with linux its like half an hour only to figure out the god damn command line. Why is it so hard to tell me how to get that damn root account, so what if i destroy the system in some unigainable way, il just reinstall it,and why do oyu care anyway!!!!



sudo -i 
To enable the Root account (i.e. set a password) use: 
sudo passwd root


does not work on kubuntu to

---

### Post by sisco311 on 2012-05-24
> **Pally1 said:**
> So that i can do some very basic things.

Cmon ppl seriously? This is why you are loosing to windows, it takes forever to do something as basic as creating a folder in xampp which takes only two clicks in windows, but with linux its like half an hour only to figure out the god damn command line. Why is it so hard to tell me how to get that damn root account, so what if i destroy the system in some unigainable way, il just reinstall it,and 


You don't need to run the whole GUI (web browser, music player, games...) as root for that, only the file manager. 

```
kdesudo dolphin
```

You can create a launcher for the above command on your desktop if you wish.


> **Pally1 said:**
> 
why do oyu care anyway!!!!


Our goal is to educate new users. To show them how to do some basic thinks in the proper way. ;)


> **Pally1 said:**
> 
sudo -i 
To enable the Root account (i.e. set a password) use: 
sudo passwd root


does not work on kubuntu to

It works, but setting a root password doesn't allow you automatically to log in as root into the GUI. That's true for any major modern Linux distribution.


If you are running a web server, I would strongly suggest you to get familiar with file permissions:
Unix/Linux:
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Windows uses ACLs:
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa374872(v=vs.85).aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa374872(v=vs.85).aspx)

---

### Post by Pally1 on 2012-05-24
kdesudo works only for file creating and stuff, but im using xampp which is in opt, where i need to install Jommla, which needs to write stuff into database constantly, it cant do anything in this setting, you cant even install it since it has no permission to function.


I need root/opt/lampp to work as regular folder with every read/write permission,. Can it be done, if yes, please tell me how.

---

### Post by Pally1 on 2012-05-24
Hello, anyone?

---

### Post by wilee-nilee on 2012-05-24
> **Pally1 said:**
> Hello, anyone?

When you rant and swear it cuts down the interest, just saying. :)

---

### Post by sisco311 on 2012-05-24
> **Pally1 said:**
> kdesudo works only for file creating and stuff, but im using xampp which is in opt, where i need to install Jommla, which needs to write stuff into database constantly, it cant do anything in this setting, you cant even install it since it has no permission to function.


I need root/opt/lampp to work as regular folder with every read/write permission,. Can it be done, if yes, please tell me how.

Your assumption is false. You don't need to login to the GUI as root or make the lampp directory word writable in order to install & set up Joomla.

I don't have much experience with web servers, so I can't help you with that.

Please start a new thread about the issues you are facing while installing Joomla. 

Thread closed.

---

