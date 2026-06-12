---
title: "How do I make myself a ROOT user."
date: 2009-04-17
forum: General Help
---

### Post by Epidemic_HardyBoy on 2009-04-17
I am trying to use zenmap but it says I cannot because I am not root.

---

### Post by lisati on 2009-04-17
The recommended way for the Ubuntu family of Linux distros is with ```
**sudo** <command-name>
```
You will be asked for your password: just use the same one as you use your main Ubuntu userid. Don't worry if it doesn't show, this is normal.

---

### Post by Epidemic_HardyBoy on 2009-04-17
I figured that, but I want to be able just to type

"Nmapfe" in the terminal and it to come up, not "sudo nmapfe" then my password.

---

### Post by mb_webguy on 2009-04-17
The root account is disabled in Ubuntu as a security measure.  While it is possible to enable the root account, doing so would make your system less secure.  Furthermore, it is against forum policy to discuss the means to do so.

---

### Post by SuperSonic4 on 2009-04-17
If it's a GUI app try ```
gksu <app>
```

---

### Post by Klaz168 on 2009-04-17
sudo su -

---

### Post by Flareside on 2009-04-17
switch over to a non-n00b linux distribution

---

### Post by jowilkin on 2009-04-17
Against forum policy to discuss something?  That's not very democratic...

You can setup sudo so that certain commands (or all commands) can be run with "sudo <command>" without typing the password.  This is done by editing the /etc/sudoers file.  The recommended way to do this is to run the command visudo, which ironically you will need to use sudo to run.  So the command is "sudo visudo", which will bring up a text editor showing the /etc/sudoers file.  There should be a line in there that says 

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

This is the line allowing you to use sudo (assuming you are a member of the admin group.  You can make it so that you can use sudo without a password by changing that to:

%admin ALL=NOPASSWD: ALL

It would probably be better to only allow certain commands to be run without a password.  To do this you can put in a line like

username ALL=NOPASSWD: /path/to/program

Finally you can switch to the root user by using "sudo -i".  But of course be very careful what you type once you've done this.  One wayward command and you can cause serious damage.

---

### Post by Flareside on 2009-04-17
be carefule jowilkin, what you just posted violates the forum's policy because it undermines Ubuntu's security

---

### Post by jowilkin on 2009-04-17
I did not violate forum policy according to the moderators.

---

### Post by Klaz168 on 2009-04-17
> **Flareside said:**
> be carefule jowilkin, what you just posted violates the forum's policy because it undermines Ubuntu's security

how so? did he just exploit canonical?

---

### Post by cariboo on 2009-04-17
jowilkin, has not violated forum policy, he has not told the OP how to enable the root account. The instruction he gave just allow the user to use sudo without having to enter a password. The user still has to use sudo to run an application as root.

Jim

---

### Post by Xgen on 2009-04-17
One way is to create aliases of any command that you wish to use. They can be added to your ~/.bashrc file OR (recommended) create a ~/.bash_aliases file to keep track of aliases or add future ones. In the .bashrc file find the lines:

[I]# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

[COLOR="Red"]#[/COLOR]if [ -f ~/.bash_aliases ]; then
[COLOR="Red"]#[/COLOR]    . ~/.bash_aliases
[COLOR="Red"]#[/COLOR]fi[/I]

...and remove the red hashes that I highlighted and save the file. Create a ".bash_aliases" file in your home folder and add the lines (e.g.):

*alias abc="sudo abc"*

A few other ones that I use are:

[I]alias reboot='sudo reboot'
alias restart='sudo /etc/init.d/gdm restart'
alias start='sudo /etc/init.d/gdm start'
alias stop='sudo /etc/init.d/gdm stop'[/I]

Note: Some are already in the .bashrc file, and can be unhashed or  optionally copied to your bash_aliases file.

---

### Post by sunlitlaz on 2009-04-17
> **Flareside said:**
> switch over to a non-n00b linux distribution

Gee, that's a helpful post.

---

### Post by alfplayer on 2009-04-18
sudo -i

---

### Post by -kg- on 2009-04-18
As Klaz168 pointed out:

```
sudo su
```

will give you temporary access to your account as root.  Once you exit the terminal (or, I believe, any GUI app that you launch as root) this is basically reset (I don't know if the timer is reset at this point) and you're back to normal.

Unless you have multiple commands that you need to run as root, I don't see what the problem is with typing four extra letters in front of your commands (well, that and your password after the first command.  After that first command you will not need to retype your password until after the timer expires).  That's way better than leaving those commands open for a hacker or malware to exploit.

I know there are virtually no virus', worms, or trojans written and current for the Linux OS, but that doesn't mean that there never will be, and if you leave commands open for use without knowing your password, you're setting yourself up and opening the door wide for them.

Just my humble opinion.

---

### Post by jeremy1138 on 2009-04-19
> **cariboo907 said:**
> jowilkin, has not violated forum policy, he has not told the OP how to enable the root account. The instruction he gave just allow the user to use sudo without having to enter a password. The user still has to use sudo to run an application as root.

Jim

I don't see anything in the Ubuntu Forums Code of Conduct that forbids showing how to enable the root account.  Am I missing something?  I've been using Linux Mint (which is a great Ubuntu based distro by the way) for a few weeks now and, if I remember correctly, it gives you the option of enabling the root account when you install.  I've also used multiple other Linux distros since I first started using Linux in 2007.  While I admit that I am a fairly new Linux user and I don't know it all, I disagree heartily with the notion that these forums, or any others of it's type for that matter, should restrict what can and cannot be discussed in terms of the use of the Linux distro in question.  The obvious exception would be commands that are meant to cause damage to another user's computer/software provided under the guise of help.  Well, that's my opinion anyway; I could be totally wrong.

---

### Post by sisco311 on 2009-04-19
> **jeremy1138 said:**
> I don't see anything in the Ubuntu Forums Code of Conduct that forbids showing how to enable the root account.  Am I missing something? 

[thread=716201]New forum policy on log-in-as-root tutorials.[/thread]

EDIT: Ironically, Zenmap is a GUI for nmap (Security Scanner).

---

### Post by jeremy1138 on 2009-04-19
> **sisco311 said:**
> [thread=716201]New forum policy on log-in-as-root tutorials.[/thread]

EDIT: Ironically, Zenmap is Security Scanner.

My argument stands but thanks for pointing that out.  Can we get that policy added to the Ubuntu Forums Code of Conduct so that people can find it without having to search the forums for possible additions to the Code of Conduct?  I wasn't aware that I had to search for addenda to the Code of Conduct so I'm sure there are plenty of others who also aren't aware.

---

### Post by Vaphell on 2009-04-19
jeremy, it's true discussing stuff shouldn't be forbidden
people are reluctant to share that info because especially in help forums many beginners ask this question simply to avoid hassle. They are 'lazy' and try to copy their windows habits to linux because they don't know any better. Problem is that when they learn that permanent root is an easy way to avoid hassle, they are going to ruin their system sooner or later. Well, maybe it would be valuable lesson, but they can lose some important data and of course linux will be to blame :)

in short - if you can't find such potentially dangerous information by yourself, probably it's too early for you to know :)

---

### Post by OldManRiver on 2009-04-27
V,

Yes and No on "Linux will get the blame".  Yes the novice will think that, but all experienced users will know "just user error".

Once someone really learns/knows howto on Linux, then the finger pointing goes away and the real quest for knowledge begins.

OMR

---

