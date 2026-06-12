---
title: "root .. sudo .. su oh my"
date: 2005-11-01
forum: Desktop Environments
---

### Post by dtsig on 2005-11-01
I have just installed ubuntu as it was suggeted over fedora 4.

I am trying to move off MS but my job requires that I have access to a programing environment called OpenInsight (no need for anyone here to know anything about it).

It is delivered as a RPM.  In fedora i could just dclick .. it would ask me for roots password (which the installation asks for) and it would install to correct location.

In ubuntu archive manager tries to extract to the folders and it tells me i don't have rights .. 

I have seen several posts about sudu and su and creating a password for sudo etc.  Have tried that.

Why is this such a problem?  How do i get a package installed ??

thanks
dsig

---

### Post by suRoot on 2005-11-01
Try this

```
sudo apt-get install alien

sudo alien "your_rpm_package_name".rpm

sudo dpkg -i "your_brand_new_deb_package_name".deb 
```

The "alien" program will convert an RPM to a DEB, which is debian's version of RPM.

---

### Post by 23meg on 2005-11-01
[edited out]

---

### Post by Nomad64 on 2005-11-01
Sudo is a command that allows you to run a command as the root user. Since you can't login to root in Ubuntu (security reasons), the "sudo" command allows you root-level privlidges for a small period of time.

The sudo password is set when you install Ubuntu. Remember it asking you to enter a password (shortly after asking you to enter a username)? The password you entered there is the sudo password. Obviously, it can be changed after the install using the below command and then entering the password when prompted.
```
sudo passwd root
```

---

### Post by dtsig on 2005-11-01
so .. is it my understanding that to do most anything that requires 'sudo' privileges you have to be at a command line

dtsig

---

### Post by Haegin on 2005-11-01
No need for you to be at the command line. You can use the command line but you can also use a program called gksudo which brings up a pretty text box asking for the root password. All gksudo does is put a pretty GUI face on sudo.

Under other distros such as mandrake you use su. su stands for super user and it means that you temporarially execute all commands with root privilages. Sudo stands for super user do and lets you execute one command with root privilages. If you execute a program using sudo (or gksudo) then that program  acts as if it was run by the root account and gains permissions accordingly. This only lasts until you close the program and only affects that one instance of that program.

For example if I tried running the "Add applications" tool it would pop up a box asking for my root password. If you are creating a menu entry or a launcher which needs root access then you should use "gksudo <program-name>". So to launch synaptic as root the command would be: ```
gksudo synaptic
```

Normally any programs which need root access (synaptic for example) will already be configured to ask for your password using gksudo.

The reason many instructions are given in the form of terminal commands is because every user has a terminal. Not every user uses synaptic for example so telling them to install a program via synaptic isn't very helpful for people who don't have synaptic or for people who don't use synaptic. Anybody can copy a bit of text from a post here into a terminal.

I hope this explains some things.

---

### Post by oswaldkelso on 2005-11-01
[QUOTE=Nomad64]Sudo is a command that allows you to run a command as the root user. Since you can't login to root in Ubuntu (security reasons), the "sudo" command allows you root-level privlidges for a small period of time.

The sudo password is set when you install Ubuntu. Remember it asking you to enter a password (shortly after asking you to enter a username)? The password you entered there is the sudo password. Obviously, it can be changed after the install using the below command and then entering the password when prompted.
```
sudo passwd root
```[/QUOTE]

Thankyou

For some reason I'd not been able to login as root but that command let me setup my root pass word

---

### Post by Haegin on 2005-11-01
I always find I have to type ```
sudo passwd
``` and set my password up "in the terminal" before I can do anything with root privilages. This may be fixed in breezy (I upgraded instead of reinstalling)

---

### Post by paddyg on 2005-11-01
[QUOTE=oswaldkelso]
For some reason I'd not been able to login as root but that command let me setup my root pass word[/QUOTE]

root is disabled, not forbidden.
if you feel you've got to log in as root, you can:

```
sudo gdmsetup
```
security--->allow root to login as gdm

or

system--->administration--->login screen setup--->security--- tick off allow root to login with gdm

of course, that's risky.

---

