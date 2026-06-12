---
title: "root login problem"
date: 2005-01-05
forum: Desktop Environments
---

### Post by Humboldt on 2005-01-05
I started the root console and there write gedit, to open the gedit editor. (I was going to edit a file in /etc, and needed root previliges) When hitting enter this message appeared, and the system froze.

"(gedit:5044): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."

I could not leave the console with exit afterwards, and the desktop kind of froze. I had to reboot. This also happens when I use the sudo command. Whats wrong?

Thanks for any help?

---

### Post by Bart Van on 2005-01-05
[QUOTE=Humboldt]I started the root console and there write gedit, to open the gedit editor. (I was going to edit a file in /etc, and needed root previliges) When hitting enter this message appeared, and the system froze.

"(gedit:5044): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."

I could not leave the console with exit afterwards, and the desktop kind of froze. I had to reboot. This also happens when I use the sudo command. Whats wrong?

Thanks for any help?[/QUOTE]
 I think you'd better start gedit in a *normal* console using ```
sudo gedit
```, at least that's what I do and never had any problems. It also gives you root privileges for that gedit-session...

And doing sudo in a root console doesn't seem a good idea either (or did I get you wrong?), but I'm rather newbie myself...

---

### Post by Humboldt on 2005-01-05
I also did sudo in a normal terminal - just like you - but with the same result. In other words - either I do the sudo command in a normal terminal OR open a root terminal - I got the same result.

---

### Post by wallijonn on 2005-01-05
If you [COLOR=Blue]Applications -> System Tools -> Root Terminal[/COLOR], Right click, [COLOR=Blue]Properties[/COLOR], is the command [COLOR=Red]gksudo /usr/bin/x-terminal-emulator[/COLOR]?

You may want to start SPM and install: [COLOR=Blue]gksu[/COLOR]

Then see if the problem persists. If it does then try SPM'ing [COLOR=Blue]xserver-common[/COLOR] and if that doesn't work, [COLOR=Blue]xserver-xfree86[/COLOR]

If you can do your wanted task, then ignore the warning message. But that warning should not hang your system, not allow you to close the terminal or root terminal, etc. It will all depend on the function being initiated. Just make sure that you are using the [COLOR=Blue]sudo[/COLOR] command.

---

### Post by Humboldt on 2005-01-05
Thanks for your tips. I have found out that my problem seems to have to do with my firewall. I have Firestarter installed. When I installed Firestarter I followed the Howto at: <http://www.ubuntuforums.org/showthread.php?t=7812&highlight=firestarter>

I am on a broadband connection and online all the time. When I logg in as root I use the firewall for disconecting (i.e. block network traffic) from the network and the internet. But it seems as for some reason, that I do not know about, this also make it impossible to launch gedit, nautilus and other programs. Anybody who knows why?

---

### Post by wallijonn on 2005-01-06
Did you open a root terminal and type [COLOR=Red]sudo gedit /usr/sbin/firestarter.config[/COLOR] (or whatever the firestarter config file is?)  

humboldt ALL=(ALL) ALL
humboldt ALL=NOPASSWD: /usr/sbin/firestarter
<exit gedit>

[quote=Humbolt]When I log in as root...[/quote]
?

---

### Post by Humboldt on 2005-01-07
Yes, I did all that. My firewall are, for what I know, correct configured in the way it is described in the HOWTO. The problem seems to be, if I for a moment block all internet traffic, that I that way also block the possibility to open a program like gedit or nautilus by typing the sudo command followed by program name in a console. To avoid missunderstandings I should also explain that it is no problem to open gedit or nautius in a "normal" way, i.s. in a user grapical mode - even in the firewall is blocking all internet traffic. It is ONLY when I try to open them with the sudo command from a consol this is a problem.

I guess this has nothing to do with "missconfiguration" - I think it is a unforseen sideeffect of the way the fireall works and is configured - but I do not know for sure and I would like to know more exact why this problem occurs.

---

### Post by roms on 2005-01-10
Hello,
 i have the same problem but i have no firewall installed.

When i enter gedit command (sudo or root) i have the error message above, but the window open however. 
so i modify few registers but when i want to save i have an error message:
"impossible d'enregistrer le fichier « file:///proc/asound/card0/codec97#0/ac97#0-0+regs »." :cry: 

In english : impossible to save this file

thanks for tour answer

---

### Post by fng on 2005-01-10
Could you try another editor like 'vim' or 'bluefish'.
Does the error occor also?

---

### Post by Humboldt on 2005-01-10
I have not bluefish installed, but I found that I actually could do "sudo vim" and open VIM. This also worked in a root console. VIM opens in a terminalwindow however, and not in it&#347; own separate grapical window like gedit and nautilus. 
Since I wrote my first question I have also upgraded firestarter to version 1.0. This time I have not made acces to firestarter as normal user possible.(As described in the HOWTO mentioned above.) The problem described above are the same however,

---

### Post by fng on 2005-01-10
gvim is a GUI-version for vim
sudo apt-get install gvim
sudo apt-get install bluefish

---

### Post by fng on 2005-01-10
vim-gnome seems to be the GUI version of vim : sudo apt-get install vim-gnome
bluefish : sudo apt-get install bluefish

---

