---
title: "Removing sudo changes"
date: 2005-04-29
forum: Desktop Environments
---

### Post by Gowator on 2005-04-29
I want the sudo to work like normal instead of the way it works in Ubunbtu ...
When I am prompted for the password how can I get rid of it asking for my password and instead ask for the root password.  

I don't like running as root which is effectively what I am doing at the moment since 
sudo passwd root will change my root password!  

Is there an easy way to do this or do I need to remove the Ubuntu packages and replace them with standard debian? 
If so is there a compatible version of unstable or testing?

edits:
I have 2x Ubuntu installs I run next to my woody server but unless I can fix this I will need to go back to Debian testing installs on the workstations as I will not use a distro that does not respect the wishes of the progammers and this has obviously bastardised Gnome and KDE.

---

### Post by codejunkie on 2005-04-29
sudo passwd root then enter root password  just enables the root account then it is like other normal linux distros you type su and enter the root password like debian, slack, suse to disable it again type sudo passwd -l root that switches back to the way a default ubuntu install set's up root access.

---

### Post by Gowator on 2005-04-29
erm except I can still (or anyone with my user password can still) sudo passwd root


I already have a root password (that took about 3 seconds to work out I guess someone trying to comprimise by box might take less) but now when I try and do admin tasks in Gnome or KDE it asks for my password NOT the root password.  

I wahnt top need the root password (which is longer and way more complex) instead of my user password which is shorter...  when I do a serious admin task, not open a root terminal by typing my password, its a 'hackers' dream!  

I guess I can try and work it out from the source code but so far it loks like Ubuntu have hacked Gnome and KDE to do this, in which case its a distro that doesn't repect programmers wishes like Suse.

---

### Post by codejunkie on 2005-04-29
then remove /etc/sudoers that should make it to where only root can make system wide changes.

after you remove the sudoers file you'll have to edit the system/administration menu items like gksudo /usr/sbin/synaptic to gksu /usr/sbin/synaptic or manully launch them with alt+F2 gksu synaptic.

---

### Post by Gowator on 2005-04-29
OK..thanks, that's what I needed :D

Its a bit worrying that the distro comes with a pre-installed rootkit...

---

### Post by odix on 2005-04-29
If you install ubuntu in expert mode, you are able to disable sudo.

odiX

---

### Post by Gowator on 2005-04-29
Ill bear that in mind next install if I keep with Ubuntu.  

Have to say the intial attraction is dropping off with security holes like this though...

---

### Post by Juergen on 2005-04-29
The Ubuntu developers prefer using sudo to having newbies login as root all the time...

You can read their thoughts about it here:
[http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

Look at the paragraph 'Misconceptions'

---

### Post by Gowator on 2005-04-29
> Isn't sudo less secure than su? 
The basic security model is the same, and therefore these two systems share their primary weaknesses. Any user who uses su or sudo must be considered to be a privileged user. If that user's account is compromised by an attacker, the attacker can also gain root privileges the next time the user does so. The user account is the weak link in this chain, and so must be protected with the same care as root. On a more esoteric level, sudo provides some features which encourage different work habits, which can positively impact the security of the system. sudo is commonly used to execute only a single command, while su is generally used to open a shell and execute multiple commands. The sudo approach reduces the likelihood of a root shell being left open indefinitely, and encourages the user to minimize their use of root privileges.  

I disagree... unless users are forced to make another account for web access etc. then they are vulnerable to their user account being comprimised and the root password activated.  
Further they are unaware of the account .... and unaware of its purpose...

some apps's are deliberatly made not to run with root permission (gtkrelm and gtk-gnutella) come to mind for every good reason ... this bypassed that security and for say gtk-gnutella the security of the network.  

Unfortunately gtk-gnutella runs with Ubuntu !

---

