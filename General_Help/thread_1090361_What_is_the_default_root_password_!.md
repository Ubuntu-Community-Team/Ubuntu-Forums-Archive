---
title: "What is the default root password ?!?"
date: 2009-03-08
forum: General Help
---

### Post by fa355115 on 2009-03-08
Hi there !

I have installed ubuntu and created during the installation procedure my user.
I'd like to run the gconf command, but it tells it is not found.
So I was thinking about running a find command as root "sudo root" ... but it asks for the root password .

I have not set it during installation - is there a default one ?

Thank you !

---

### Post by yeats on 2009-03-08
You'll want to take a look at this page:

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

But since it's against forum policy to instruct you how to do this, you're on your own if you want to login as root anyway.  In 99% of all cases, sudo will suffice.

Good luck.

---

### Post by other guy on 2009-03-08
The root is not enabled as far as I know. I assume you understand why it is disabled by default. And understand for sure the reason you want to run as root. Not much is needed beyond the sudo levels. So usually that is plenty enough permissions. It is far safer than going full root.


To enable the root.

```
$sudo passwd root
```

Then type the password  you want. I would highly suggest if you do not know. Make it tough and not the same as the sudo account.

I would highly suggest also. When you are done using the root, to disable it once again. 

```
sudo passwd -l root
```

---

### Post by Dayylin on 2009-03-08
See above lol

Brian aka Dayylin

---

### Post by other guy on 2009-03-08
> **Dayylin said:**
> See above lol

Brian aka Dayylin

You had some valid points and ways to accomplish it. In your original post.

The part about making the root password memorable was great advice. I didn't mention that. Figured I would expand on your point. 

One neat thing about Linux. There is more than one way to do things. The way you suggested is just as valid as what I suggested. Just a little more GUI action for those who like that route.

---

### Post by Chibone on 2009-03-08
Just in case it needs to be said, **be careful when running any command as root!**

My opinion - there's no point in enabling root except if you want to login as root.  Just make a strong user password.  Pretty much anything I want to do as root can be done with sudo.

I think the command you were looking for based on what you wrote in your first post is "gconf-editor".
You can run any command as root by typing "sudo" before the command.

---

### Post by yeats on 2009-03-08
I'm feeling the need to direct everyone to this:

[http://ubuntuforums.org/showthread.php?t=716201]("http://ubuntuforums.org/showthread.php?t=716201")

I didn't realize this topic was against forum policy myself until someone directed me to it.

---

### Post by other guy on 2009-03-08
> **chrissharp123 said:**
> I'm feeling the need to direct everyone to this:

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

I didn't realize this topic was against forum policy myself until someone directed me to it.


Now I feel bad. I wish I would of known that was policy. I would of went at it in another angle.

---

### Post by DeMus on 2009-03-08
> **fa355115 said:**
> Hi there !

I have installed ubuntu and created during the installation procedure my user.
I'd like to run the gconf command, but it tells it is not found.
So I was thinking about running a find command as root "sudo root" ... but it asks for the root password .

I have not set it during installation - is there a default one ?

Thank you !

Don't open up your system by logging in as root. It will be as open as every Windows system and that is just what Linux does not want to be.
Whenever you have to do something which requires root permission, type sudo and then the instruction or name of the program you want to start. The system will then ask you for a password. This is YOUR password, the one you typed during installation, and which belongs to your account. The account you made during installation is granted root permissions when needed.
Now you can perform root tasks for 15 minutes. Then the password is disabled again automatically.

---

### Post by calrogman on 2009-03-08
> **Chibone said:**
> You can run any command as root by typing "sudo" before the command.

I am using iptables to connect my Xbox 360 to the intertubes through my laptop (router on other side of house, £50 for a wifi adapter is ridiculous) and need to enable IP forwarding every boot, "sudo echo 1 > /proc/sys/net/ipv4/ip_forward" doesn't cut it, and I need to use "sudo su" to login as root before I can enable IP forwarding.  So not *every* command can be run as root with sudo.

---

### Post by DeMus on 2009-03-08
> **calrogman said:**
> I am using iptables to connect my Xbox 360 to the intertubes through my laptop (router on other side of house, £50 for a wifi adapter is ridiculous) and need to enable IP forwarding every boot, "sudo echo 1 > /proc/sys/net/ipv4/ip_forward" doesn't cut it, and I need to use "sudo su" to login as root before I can enable IP forwarding.  So not *every* command can be run as root with sudo.

This might help you:

Create a file called "forwarding" in /etc/init.d:
```
sudo gedit /etc/init.d/forwarding
```
And paste this in there:
echo 1 > /proc/sys/net/ipv4/ip_forward

Save and close, then run 
```
sudo update-rc.d forwarding defaults 99 01
sudo cp /etc/rc5.d/forwarding /etc/rc.local/forwarding
sudo chmod +x /etc/rc.local/forwarding
```
and you should be set.

This way the system is performing the task for you (as root) without you having to log in as root.

---

### Post by Dayylin on 2009-03-08
Umm <slaps self in head> didn't realize that. Thank you for pointing it out.

> **chrissharp123 said:**
> I'm feeling the need to direct everyone to this:

[http://ubuntuforums.org/showthread.php?t=716201]("http://ubuntuforums.org/showthread.php?t=716201")

I didn't realize this topic was against forum policy myself until someone directed me to it.

---

