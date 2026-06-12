---
title: "Trouble logging in as sudo or root"
date: 2006-11-04
forum: Desktop Environments
---

### Post by JoeS on 2006-11-04
Using Ubuntu Breezy Badger
I tried to log in as root, but when I used ```
sudo passwd root
```I got the following message: > unable to lookup ubuntu via gethostbyname
I also go this response when I used ```
sudo
```
I gave the host name of ubuntu when I installed 

Can anyone tell me whats going on and how to fix this?

Thanks for your help.

---

### Post by FyreBrand on 2006-11-04
I'm not sure exactly what you're trying to do.  When you make an account as you install Ubuntu you login with that accoutn <username> <password>.

This account has the privilege of using sudo to perform administrative actions such as installing software or manipulating the system.

The password of your main account (the one you created at install) is the same password you use to perform sudo operations.

So if you want to use Synaptic to install or remove a package then you will be prompted for the sudo password (which is your main account password).  If you want to perform a command line function as sudo then you will be prompted for this same password.

The root account is disabled by default and there are very few reasons to need this account enabled.  Similarly there is no need to make a permanent account as a super user that you need to login as from the command line.

This is very different from the Red Hat/Fedora environment where one switches to a user with elevated privileges to perform actions.  The sudo way of doing things was very awkward for me when I first changed my OS from FC4 to Ubuntu.

I'm not sure if this is the situation you're in but hey I made a couple of guesses and hoped I hit the mark.  If it doesn't explain it please post back with more info.

---

### Post by taurus on 2006-11-04
> **JoeS said:**
> Using Ubuntu Breezy Badger
I tried to log in as root, but when I used ```
sudo passwd root
```I got the following message: 
I also go this response when I used ```
sudo
```
I gave the host name of ubuntu when I installed 

Can anyone tell me whats going on and how to fix this?

Thanks for your help.
What does your /etc/hosts look like then?

```
more /etc/hosts
```

---

### Post by JoeS on 2006-11-06
> unable to lookup ubuntu via gethostbyname 
I get this message everytime I try to use sudo or root.  I don't even get asked for a password.

I wanted to log in as root because I want to edit a file to change thigs like: the refresh rate, resolution & color settings on my computer.  The refresh rate only goes to 60mhz and can't
find 1024x768.   Also the color isn't good since I reinstalled the OS.

> What does your /etc/hosts look like then?
127.001 localhost

---

### Post by taurus on 2006-11-06
Your /etc/hosts should look something like

```
127.0.0.1 localhost localhost
(if you call your machine localhost...  On mine, I have
127.0.0.1 localhost taurus)
```
So, boot into recovery mode from GRUB menu and edit your /etc/hosts.

```
nano -Bw /etc/hosts
```

---

### Post by JoeS on 2006-11-08
Thanks. I got a command line in recovery mode.  was able to edit /etc/hosts and now can log in as root or sudo.

---

### Post by taurus on 2006-11-08
> **JoeS said:**
> Thanks. I got a command line in recovery mode.  was able to edit /etc/hosts and now can log in as root or sudo.
See how easy it was!  ;)

---

