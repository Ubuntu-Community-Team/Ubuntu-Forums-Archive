---
title: "&quot;add applications&quot;, updates not starting"
date: 2006-01-03
forum: General Help
---

### Post by msg on 2006-01-03
It says I have system updates, and the icon in the tray is a red circle with an exclamation mark. Also, when I try to run "add applications" it doesnt run

---

### Post by 5-HT on 2006-01-03
Hi, I believe that the update-notifier has the exclamation mark by default.

When you click on it does nothing happen?

In terms of the "add applications", does it prompt you for a password when you click on it?

---

### Post by msg on 2006-01-03
yes, it asks me for a password, and i enter it. at first I was hitting "enter" and it wouldnt do anything, so i waited for the password to time out and then tried clicking "continue", but it still wouldnt load. The same thing happens for "add application".

---

### Post by 5-HT on 2006-01-03
Hmm... I'm quite new to linux myself, so I'm definitely not the best for troubleshooting (will help to the best of my abilities and hoping someone more knowledgeable comes along if that doesn't work), but from what I take of it, there may be either an issue with both progs, or something to do with your password, or gksudo.

If you enter into a terminal, ```
 gksudo synaptic 
``` or ```
 sudo synaptic 
``` on both counts does it prompt you for a password, and if so does it tell you it's an incorrect one, times out, or launches synaptic?

---

### Post by msg on 2006-01-03
It doesnt ask me for a password, but thats probably since i entered it for something else moments before. It does not launch synaptic, and following [www.ubuntuguide.org](www.ubuntuguide.org), it does not launch anthing whenever i enter a command. When i press enter it just goes "msg@ubuntu:~$" like it does when i start it up.

---

### Post by 5-HT on 2006-01-03
About not asking for a password, yeah that's not a great concern as after you enter it once the system will remember it for a limited amount of time.

About your prompt returning after entering that command, unfortunately that's not normal at all.
Usually your prompt shouldn't return until you closed the program you launched with it (unless you put it into the background).

I fear something may be wrong with your system. Did you recently install?

Let's try the complete path to synaptic: /usr/sbin/synaptic

If you enter that in a terminal, does it ever come up?

If not, something seems amiss.

I'd try reinstalling the program, but it seems like you're having a problem with multiple programs relying on apt-get, so at this point I won't be of much help and hope someone else may be of aid.

---

### Post by mcduck on 2006-01-04
you could also try resetting your password, either with Gnome's user manager or with 'passwd username'. That might solve the problem

---

### Post by TryingToQuitMSWin on 2006-01-04
Hi, since I installed Ubuntu a few hours ago and have the same problems with synaptic I thought I' d post here.
It seems that the installation went ok but when I try to use some of the administration tools like synaptic, users and accounts, etc. nothing will happen. 
The dialogue for password opens and if I give the root password the reply is wrong password !!! but if I give the users passwd nothing happens ....
The funny thing is that when I use command prompt to login as root the passwd is accepted!!! 
I also tried to change the passwds for root and user accounts and still nothing changed.
When I launch synaptic nothing happens ... 
Any ideas ?
Should I reinstall ubuntu from scratch ?
Thanks in advance.

---

### Post by mcduck on 2006-01-04
[QUOTE=TryingToQuitMSWin]Hi, since I installed Ubuntu a few hours ago and have the same problems with synaptic I thought I' d post here.
It seems that the installation went ok but when I try to use some of the administration tools like synaptic, users and accounts, etc. nothing will happen. 
The dialogue for password opens and if I give the root password the reply is wrong password !!! but if I give the users passwd nothing happens ....
The funny thing is that when I use command prompt to login as root the passwd is accepted!!! 
I also tried to change the passwds for root and user accounts and still nothing changed.
When I launch synaptic nothing happens ... 
Any ideas ?
Should I reinstall ubuntu from scratch ?
Thanks in advance.[/QUOTE]So you enabled the root account? All admin tools are configured to use sudo instead of root, and setting password for root breaks them. Anyway, there is no reason for using the root account on ubuntu, quite the opposite.. Here's a thread about disabling root: [http://www.ubuntuforums.org/showthread.php?t=111735&highlight=disable+root]("http://www.ubuntuforums.org/showthread.php?t=111735&highlight=disable+root")

---

### Post by TryingToQuitMSWin on 2006-01-04
Yeah I enabled root account only because I was asked to do so during setup ...anyways
I tried to disable rot account as u advised but this didn't solve my problem either.
I am thinking maybe I didn't describe it very well so here it is again:
When I try to use administration tools like users and groups, synaptic, update manager, login screen setup, the first time the passwd dialogue asks me the passwd (and I supply the user account passwd not root) but nothing happens (meaning the application won't start) and the second time, I am not asked for passwd (since the system remembers it I pressume), and I see the "starting users and groups" box in the bottom panel but after a while it just disappears without any other msg ...
This is as much description I can provide ...lol ...I am new to ubuntu and linux in general but I get a possitive vibe from this distro so I hope I won't get dissapointed.
Thnx for ur help

---

### Post by TryingToQuitMSWin on 2006-01-04
Anyway I reinstalled ubuntu and now everything works fine!
Thnx!!

---

### Post by msg on 2006-01-05
my installation was probably messed up, and since i didnt have anything real important on the machine anyway, i just burnt another install cd and reinstalled. It works perfectly now :)

ubuntu rules

---

