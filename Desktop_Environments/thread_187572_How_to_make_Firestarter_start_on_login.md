---
title: "How to make Firestarter start on login"
date: 2006-06-03
forum: Desktop Environments
---

### Post by MikkelMJ on 2006-06-03
Hi. I've installed the Firestarter firewall and would like the config-icon to be in the systray automaticaly when I log in. According to this guide ([http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)) I need to ad "username ALL= NOPASSWD: /usr/sbin/firestarter" to /etc/sudoers file, and then add the command "sudo /usr/sbin/firestarter --start-hidden" to Gnome's startup sessions. But it doesn't work. It still wants a password. When I write "sudo /usr/sbin/firestarter --start-hidden" in a terminal, then enter my password when promted for it, it starts without problems. So I guess it's the "NOPASSWD" part that I've done wrong. I've tried every possible combination. I've got the user mikkel, who's a member of the admin group. Now it looks like this:

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: /usr/sbin/firestarter --start-hidden

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

I've also tried:
%admin ALL=(ALL) ALL
%admin ALL=(ALL) NOPASSWD: /usr/sbin/firestarter
%admin ALL=(ALL) ALL

and

%admin ALL=(ALL) NOPASSWD:/usr/sbin/firestarter

and

%admin ALL=ALL NOPASSWD: /usr/sbin/firestarter

and replacing %admin, with mikkel. And adding and removing "--start-hidden" to the end of the lines. In the Gnome startup sessions, I've tried:

sudo /usr/sbin/firestarter --start-hidden

and

sudo firestarter --start-hidden

But nothing works? It worked perfectly under Debian. Why can't I get it to stop promting for a password? I've even tried:

%admin ALL=(ALL) ALL
mikkel ALL=(ALL) NOPASSWD: /usr/sbin/firestarter

---

### Post by sudomania4 on 2006-06-03
This won't help you much, but i have the same problem, so it's not just you. If you find a solution, please post it.

---

### Post by roots on 2006-06-03
you might want to have a look here:

[http://www.ubuntuforums.org/showthread.php?t=26483](http://www.ubuntuforums.org/showthread.php?t=26483)

good luck!



cheers,
roots

---

### Post by bullgr on 2006-06-03
My friend, i try the same, but after i search the forum, i read there is any need for a firewall.

Ubuntu comes with iptables (firewall) build in the kernel.
All incomming port are closed by default.
The outcomming are open (it supposed you know what you do).

So, you dont need firestarter.
Note that when you do a bad setup you can open a unecesary hole in you system. And there is a problem in a few webpages... when i has the firewall enable, the webpage could not load and after i disable the firewall all was ok.

---

### Post by roots on 2006-06-03
[QUOTE=bullgr]
So, you dont need firestarter.
[/QUOTE]

as i've understood, firestarter is not much more than a gui frontend for iptables. it can help you find out who's trying to intrude  and to configure iptables in an easy way.

> 
And there is a problem in a few webpages... when i has the firewall enable, the webpage could not load and after i disable the firewall all was ok.

this is true, but only affects let's say 1 out of 100 web pages.



cheers,
roots

---

### Post by peter07 on 2006-06-03
>  This won't help you much, but i have the same problem, so it's not just you. If you find a solution, please post it. 

I have the same problem, firestarter doesn't start on login, and even I've changed sudoers I still need to enter the password. Any ideas ?

---

