---
title: "CANT Login as root...."
date: 2005-12-28
forum: Desktop Environments
---

### Post by tron_gr on 2005-12-28
why i cant login as root?
Can anyone tell me how can i disable this security setting?


thanks
Dimitris

---

### Post by Pablo_Escobar on 2005-12-28
Take a look at wiki - good place to look for an info:
[https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin]("https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin")

But You shouldn't log in as a root because that option is not safe, it always better to work as a normal user and issue a sudo command or enable the root and work with su -

---

### Post by daschl on 2005-12-28
[QUOTE=Pablo_Escobar]Take a look at wiki - good place to look for an info:
[https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin]("https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin")

But You shouldn't log in as a root because that option is not safe, it always better to work as a normal user and issue a sudo command or enable the root and work with su -[/QUOTE]

sudo for normal text-based apps
sudo su or sudo -s for permanent root-access
and gkusdo for graphical apps (i.e. nautilus)

and i also agree with pablo_escobar here

---

### Post by ibook-linux on 2005-12-28
I know it is supposed to be safer but it bugs me when I can't be root.

I do not mind using the sudo command in the terminal but in the GUI I run into all sorts of problems with the file permissions. For some reason the run as root prompt within gnome never works right for me. I am a newbi so maybe there is another way I am supposed to do it but I don't know any other way. If I want to create or modify a file that is not in my home I have to log in as root do what I want then log back out. 

Every other linux system has you log in as root just to do a quick change then log out. I do not see the big deal.

---

### Post by Pablo_Escobar on 2005-12-28
ibook-linux - but that compromises the whole idea Linux is based on - user with limited powers.

To alter some files just use sudo gedit .....
A comfortable way is to apt-get a **mc** and in terminal sudo mc -> from there You can copy, rename, move files with root powers WHILE not running the whole system as root.

---

### Post by aysiu on 2005-12-28
[QUOTE=ibook-linux]
I do not mind using the sudo command in the terminal but in the GUI I run into all sorts of problems with the file permissions.[/QUOTE] Alt-F2 ```
gksudo nautilus
```

---

### Post by d11wtq on 2005-12-28
[QUOTE=ibook-linux]I know it is supposed to be safer but it bugs me when I can't be root.

I do not mind using the sudo command in the terminal but in the GUI I run into all sorts of problems with the file permissions. For some reason the run as root prompt within gnome never works right for me. I am a newbi so maybe there is another way I am supposed to do it but I don't know any other way. If I want to create or modify a file that is not in my home I have to log in as root do what I want then log back out. 

Every other linux system has you log in as root just to do a quick change then log out. I do not see the big deal.[/QUOTE]

I'm not following this...

Are you saying you can;t even log on as root in command line such as the framebuffer?  I don't see an issue with doing that provided you're not networked or you're just making a quick change.

Anyways... to log in as root you just need to:
```

sudo passwd

```

Then you can create the root password and log in.  You still can't log into GNOME as root though... that would be pure silly IMO.  Make sure any new users you create with useradd are in the wheel group too... it's much more sensible to use the su command to gain root level access.

---

