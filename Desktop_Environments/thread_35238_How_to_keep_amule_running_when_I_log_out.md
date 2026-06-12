---
title: "How to keep amule running when I log out?"
date: 2005-05-18
forum: Desktop Environments
---

### Post by dierre on 2005-05-18
Hello...

I was wondering whether there is a way to keep amule running even when I log out from gnome. Some kind of the "screen" equivalent for gnome, I mean.

Thank you in advance, and have a nice day!

Francesco

---

### Post by gandonov on 2005-05-18
You can use:

```
# nohup COMMAND [ARG] &
    nohup: appending output to `nohup.out'
#

```
Notes:
[list]The **&** sign is mandatory (for background-ing);[/list]
[list]Standard uotput is redirected to *nohup.out*;
[/list]

---

### Post by rwabel on 2005-05-18
> **gandonov]You can use:

```
# nohup COMMAND [ARG] &
    nohup: appending output to `nohup.out'
#

```
Notes:
[list]The **&** sign is mandatory (for background-ing) said:**
> 
[list]Standard uotput is redirected to *nohup.out*;
[/list]
 never heard of that. Can you explain me a bit more how that should work when you leave gnome?
The only idea I've is to use the daemon (amuled) but then you only have the commandline or the webgui to control amule

---

### Post by gandonov on 2005-05-18
So, the main problem is that when you quit your session(Gnome) - all your applications will be terminated! 
Technicaly: When you kill your parent process - all children will be terminated!
With exeption:  ;-) All processes that ware started with *nohup*

**Simple description:**
** 1**. Start application in background:
[FONT=Courier New][COLOR=Navy]   nohup amule [some_options] &
   [1] **2283**[/COLOR][/FONT]   [COLOR=DarkGreen]<---- ProcessID[/COLOR]

** 2**. (Optional) Just FYI
[FONT=Courier New][COLOR=Navy]   ps -ef |grep amule
   user      **2283**   579 99 13:27 pts/0    00:00:09 amule some_options[/COLOR][/FONT]

** 3**. quit Gnome.

** 4**. Login agian.

** 5**. Chech your application:
[FONT=Courier New][COLOR=Navy]   ps -ef |grep amule
   user      2283   **1**    99 13:27 pts/0    00:10:15 amule some_options[/COLOR][/FONT]

Please note that PPID (Parent ProcessID) is **[COLOR=Red]1[/COLOR]** (init process)!
Your application will continiue to work until next reboot (or to successful end)

You can use *nohup *for Backup,  downloads, etc...  :)


George
P.S. Sorry for my english

---

### Post by rwabel on 2005-05-18
> **gandonov]So, the main problem is that when you quit your session(Gnome) - all your applications will be terminated! 
Technicaly: When you kill your parent process - all children will be terminated!
With exeption:   said:**
> [color=Navy]   nohup amule [some_options] &
   [1] **2283**[/color][/font]   [color=DarkGreen]<---- ProcessID[/color]

** 2**. (Optional) Just FYI
[font=Courier New][color=Navy]   ps -ef |grep amule
   user      **2283**   579 99 13:27 pts/0    00:00:09 amule some_options[/color][/font]

** 3**. quit Gnome.

** 4**. Login agian.

** 5**. Chech your application:
[font=Courier New][color=Navy]   ps -ef |grep amule
   user      2283   **1**    99 13:27 pts/0    00:10:15 amule some_options[/color][/font]

Please note that PPID (Parent ProcessID) is **[color=Red]1[/color]** (init process)!
Your application will continiue to work until next reboot (or to successful end)

You can use *nohup *for Backup,  downloads, etc...  :)


George
P.S. Sorry for my english
 very interesting, I've to test that. And that's also working for gui programs? so when I quit gnome and restart my amule is still running and downloading?

a daemon is easy to put in startup, so it will be started even if you don't log to gnome or another window manager.

but I'll check out your method and see if that really works.

p.s. where do you come from?

---

### Post by gandonov on 2005-05-18
I have not expiriance with *amule*. Maybe there is a better way to work with it.

I'm using *nohup* with terminal-based commands(noGUI).
For graphical apps is tricky to catch the GUI again ;-)

But I think that *nohup* is very usefull.
I know this command from SUN Solaris. In Solaris' version thare are lot of options for *nohup*.

---

### Post by dierre on 2005-05-18
> **gandonov]So, the main problem is that when you quit your session(Gnome) - all your applications will be terminated! 
Technicaly: When you kill your parent process - all children will be terminated!
With exeption:   said:**
> 

** 5**. Chech your application:
[FONT=Courier New][COLOR=Navy]   ps -ef |grep amule
   user      2283   **1**    99 13:27 pts/0    00:10:15 amule some_options[/COLOR][/FONT]

Please note that PPID (Parent ProcessID) is **[COLOR=Red]1[/COLOR]** (init process)!
Your application will continiue to work until next reboot (or to successful end)

You can use *nohup *for Backup,  downloads, etc...  :)


George
P.S. Sorry for my english

Thanks... what I was looking for is: is there a way to reattach the GUI to gnome when I log in back again? For text consoles "screen -r" does that nicely, and you can even start a text-application on a machine, detach it, log in from another machine through ssh and reattach it. Simply lovely. :-)
Is there something like that for the GUI as well?

Thank you!

---

### Post by infinito on 2005-05-18
Maybe you should try **MLdonkey**, which is suppossed to be run on daemon mode (as well as non daemon, if you like).

Some links:
* [MLdonkey Official Website](http://www.mldonkey.net/)
* [MLdonkey World](http://mldonkey.berlios.de/)
* [SpiralVoice cores (2.5.3x series)](http://ftp.berlios.de/pub/mldonkey/spiralvoice/)
* [Knocker cores (2.5.16x series)](http://mldonkey.dyndns.info/)
* [Sancho GUI to view daemon info](http://sancho-gui.sourceforge.net/)
* apt-cache show mldonkey-server

Works great. Has support for several protocols (edonkey, overnet, kadmelia, soulseek, filetp, kazaa, bittorrent...) all in the same app.

Hope you like it!

---

### Post by gandonov on 2005-05-18
[QUOTE=dierre]... what I was looking for is: is there a way to reattach the GUI to gnome when I log in back again? For text consoles "screen -r" does that nicely, and you can even start a text-application on a machine, detach it, log in from another machine through ssh and reattach it. Simply lovely. :-)

Is there something like that for the guy as well?
[/QUOTE]
Hi,

VNC can detach a single app. You could edit the ~/.vnc/xstartup file and take the window manager call out of there and just replace it with a single application. 
You'll need an SSH client on your local machine that can do port forwarding, and of course sshd on the machine you want to connect to.


But if you want to access previously started GUI application on the same machine, you can try: 
[FONT=Courier New][COLOR=Navy]  nohup vnc GUI_app &[/COLOR][/FONT]

Good luck!  :)

---

### Post by sciurus on 2005-05-19
[QUOTE=gandonov]
I'm using *nohup* with terminal-based commands(noGUI).
For graphical apps is tricky to catch the GUI again ;-)
[/QUOTE]

Perhaps if the use of nohup is combined with xmove?

---

