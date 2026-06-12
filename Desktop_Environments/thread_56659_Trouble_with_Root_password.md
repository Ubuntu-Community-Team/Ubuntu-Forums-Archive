---
title: "Trouble with Root password"
date: 2005-08-13
forum: Desktop Environments
---

### Post by carytid9 on 2005-08-13
I've just installed Kubuntu Hoary on a Dell Latitude 600 laptop.  All appeared to go well until I tried to access the Network Settings, which called for Administrative permissions. That meant using the "root" password.  Access was denied "Incorrect password".  I then tried a number of other settings requiring the "root" password, with exactly the same result.

I then used "su" on a Terminal. and the same password was accepted.

OK, ReInstall, I thought, with special care on root password entry, but the result was exactly the same.

I've been using Linix for quite a while, mostly with KDE, but this has never happened before with other distros, including Ubuntu.  I've no idea where to go from here, so some help would be welcome.

Paul

---

### Post by Zelut on 2005-08-13
ubuntu doesn't set a root password by default.  If you need to run with administrator priveledges (ie; network settings, etc) it'll prompt you for the password, as you mentioned.  You can use your password for this and it'll grant you priveledges for that session.

The default password for this field is the same as the original account that you setup during installation.  It will not work with additional accounts/passwords unless they have been added to the sudoers file.

If you would like to create a default 'root' password you can find instructions at [www.ubuntuguide.org](www.ubuntuguide.org) .

---

### Post by yaye on 2005-08-13
[QUOTE=carytid9]I've just installed Kubuntu Hoary on a Dell Latitude 600 laptop.  All appeared to go well until I tried to access the Network Settings, which called for Administrative permissions. That meant using the "root" password.  Access was denied "Incorrect password".  I then tried a number of other settings requiring the "root" password, with exactly the same result.

I then used "su" on a Terminal. and the same password was accepted.

OK, ReInstall, I thought, with special care on root password entry, but the result was exactly the same.

I've been using Linix for quite a while, mostly with KDE, but this has never happened before with other distros, including Ubuntu.  I've no idea where to go from here, so some help would be welcome.

Paul[/QUOTE]

As a long time Linux user, I was also puzzled.  I came across the solution thorough a Google search that led me here:

[http://www.ubuntuforums.org/showthread.php?t=31053](http://www.ubuntuforums.org/showthread.php?t=31053)

You may want to add your thoughts to the discussion.

Ian

---

### Post by usergentoo on 2005-08-14
I had this same problem. My default password didnt work.
So I gave one to root.
do this
sudo passwd root
after that it worked fine

Ive been using linux since the late 90's and found this to be a odd situation.

---

### Post by guitard00d on 2005-08-14
What I don't understand is why the two machines I installed Kubuntu on both have the same random problem when trying to access something in Kcontrol that requires administrative access. Meaning, I enter the password (and I know I'm entering it correctly) but Kcontrol reverts back to the Kcontrol info screen rather than loading the desired Kcontrol module in administrative mode. If this is a bug in KDE 3.4.0 I'll be glad when Kynaptic can download a patched version that fixes the problem. I've never had this problem with any other version of KDE on any Linux distro.

---

### Post by carytid9 on 2005-08-14
All the suggested solutions appear to assume the Gnome Desktop, not KDE.  We are talking about Kubuntu!  On attempting to use sudo, I have the message "<user name> is not in the sudoers file. This incident will be reported" (!).  Successful attempt at reentering a root password on terminal (after using "su"), but no success with KControl.

Paul

---

### Post by usergentoo on 2005-08-14
The above is how I fixed my problem and I use kubuntu.
When you type
```
sudo passwd root
```
it will ask for your user password then it will ask to enter a new password wich will be for root the it will ask to confirm it.

Goto control panel and use this new password.
just copy and paste this into terminal
it is passwd not password

---

### Post by yaye on 2007-04-13
> **carytid9 said:**
> All the suggested solutions appear to assume the Gnome Desktop, not KDE.  We are talking about Kubuntu!  On attempting to use sudo, I have the message "<user name> is not in the sudoers file. This incident will be reported" (!).  Successful attempt at reentering a root password on terminal (after using "su"), but no success with KControl.


For KDE root login, enable root login ( sudo passwd root ) and follow the instructions here:

[http://kim.biyn.com/Linux/How_to_enable_root_logins_in_kde_on_suse](http://kim.biyn.com/Linux/How_to_enable_root_logins_in_kde_on_suse)

It refers to Suse, but it works for Kubuntu also.

---

### Post by scottdizzle on 2007-04-14
> sudo passwd root

That worked for ubuntu. It wasn't taking my password for the user I just created til I did that and set a root pass. Thanks for the tips guys.

---

