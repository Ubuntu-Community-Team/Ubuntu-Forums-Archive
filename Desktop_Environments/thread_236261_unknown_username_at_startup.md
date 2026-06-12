---
title: "unknown username at startup"
date: 2006-08-14
forum: Desktop Environments
---

### Post by cyclone on 2006-08-14
I installed the os and everything went fine but during install it never asked for a username only a password and comp name.When the system boots i cant logon cause i dont know username is there a default? Im sure this is a simple problem but i feel kinda stupid i have reinstalled twice for this problem.:D

---

### Post by jordilin on 2006-08-14
> **cyclone said:**
> I installed the os and everything went fine but during install it never asked for a username only a password and comp name.When the system boots i cant logon cause i dont know username is there a default? Im sure this is a simple problem but i feel kinda stupid i have reinstalled twice for this problem.:D

No, you must provide an initial username in the installation. There's no default username. Take a look at the following tutorial made by aysiu:
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by cyclone on 2006-08-14
Im new to ubuntu and have checked cd for errors and it is fine the link u sent me is not the same version i have.Call me dumb but there is no option to make a username in install only a password and comp name.I already wiped out my xp trying to duel bootonly to get a error 17 message and the fixmbr didnt work either.Anyways i guess ill have to go back to mandrake or suse since this isnt working for me.:sad:

---

### Post by Ramses de Norre on 2006-08-14
There is no default and you must have set one.. But you can retrieve it anyway, in grub choose recovery mode and when booted do ```
ls /home/
``` the output of this command should reveal all usernames on the system (so that should be only yours). Then do ```
init 2
``` to boot the pc normally and log in whith the username you just got and your password you have set.

PS: you didn't install with root account enabled or something, did you?

---

### Post by cyclone on 2006-08-14
I did a clean install and have done 3 times now.It never asked me ever for a username only a hostname and password not once in 3 installs i have seen a username.

---

### Post by cyclone on 2006-08-14
btw i am installing in oem version i hope this is correct im reinstalling again and it never asked me to set a username only a hostname and password.

---

### Post by PaulHeth on 2006-08-23
I'm having exactly the same problem.  So it's not just you.  I'll let you know if I come up with a fix.

Cheers, Paul.

---

### Post by PaulHeth on 2006-08-23
So it turns out to be quite simple.  When using the OEM version the username is [COLOR="Red"]oem[/COLOR] and whatever password you entered during the installation.  The computer name is not a factor.

However it seems a compbination of factors make this situation a common one.  The largest I believe is that the only way to install on a machine with less than 192 mb of ram is to use the confusing eom installation.

Just my 2 cents.

Thanks,
- Paul.

---

### Post by mcduck on 2006-08-24
You shouldn't use the OEM install. It provides no benefits when installing on your own computer, but it makes the installl process more complex.

The OEM install is for computer manufacturers who wish to sell computers with Ubuntu preinstalled. It allows you to install Ubuntu, log in as 'oem' do some configurations and customizations you want and then when you log out log out the 'oem' user is removed (I believe you need to rome some special command for this). Now when the customer first boots the machine it will ask for username&password and create the actual user.

The normal install will ask you for your username&password and create your actual user during the install.

I know using OEM installs for windows is very common as they cost much less than the full license, but as Ubuntu is free anyway there is no reason not to use the normal install :)

---

### Post by mcduck on 2006-08-24
> **PaulHeth said:**
> 
However it seems a compbination of factors make this situation a common one.  The largest I believe is that the only way to install on a machine with less than 192 mb of ram is to use the confusing eom installation.
No, it's not. You can do normal install with the Alternative-CD. It's the first option in the boot menu. :)

---

### Post by hraposo on 2006-08-24
Try to do that ctr+alt+backspace keys. If the grfical mode is disable you can do that: 
sudo passwrd root
enter a password to root
then type
su
enter the password root
and:
startx
you login as root
go to system>admistration>users and groups
then you can add a user and to do login as  this new user.

---

### Post by hraposo on 2006-08-24
Sorry, the line command is
sudo passwd root

---

### Post by hraposo on 2006-08-24
Sorry, the line command is
sudo passwd root

---

