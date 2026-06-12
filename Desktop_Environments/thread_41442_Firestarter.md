---
title: "Firestarter"
date: 2005-06-13
forum: Desktop Environments
---

### Post by trivialpackets on 2005-06-13
Rather than start jumping distros, I tried to day to jump window managers.  Installed Kubuntu, all in all very nice, and nice additions to software.  But I can't locate my icon for Firestarter?  Any ideas?

---

### Post by philipacamaniac on 2005-06-13
Not all GNOME apps will automatically show up on the KMenu (I think it happens when an app doesn't follow the FreeDesktop.org standards, or something.

Anyway, simply going to K-Menu --> Run --> firestarter   should get you going. You can easily add entries to the K-Menu by right clicking the K-Menu icon and selecting "Edit menu"

EDIT: There are also a few KDE-based firewalls out there. You might try Guarddog.

---

### Post by lovebug356 on 2005-06-13
Can you start Firestarter from login without giving the root password?

---

### Post by arjaybe on 2005-06-13
The firewall starts automatically when you boot.  You need root permissions to run the configuration GUI.

---

### Post by trivialpackets on 2005-06-13
[QUOTE=arjaybe]The firewall starts automatically when you boot.  You need root permissions to run the configuration GUI.[/QUOTE]
 I'll try guard dog when I get home.  Thanks for the advice.

---

### Post by raven on 2005-06-25
[QUOTE=arjaybe]The firewall starts automatically when you boot.  You need root permissions to run the configuration GUI.[/QUOTE]

2 questions if anybody can help

1Q-How can I run firestarter or dogguard
the gui of firestarter will ask me the sudo pass
and guarddog ask me the sudo pass
upon log in KDE

2Q-where is the startup files of those 2 programs ?

I checked in autostart for system and for user
no sign for neither firestarter or dogguard

---

### Post by cwaldbieser on 2005-06-26
As stated above, firestarter or guarddog, if installed correctly, *should* start automatically when your system boots without asking you for a password.  This is not exactly a normal program that you would expect to see running in your process list.  What actually happens is something like this:
1) System starts booting.
2) Firestarter script at /etc/firestarter/firestarter.sh is invoked.
3) Your firewall settings are read from a config file and loaded into the kernel ip tables.  From this point on, the kernel is actually in charge of accepting or rejecting packets.
4) The rest of the system starts up.

The GUI pieces are just tools you can use to view the current settings and to change them.  The firewall is still in effect, even if the GUI is not.  You can verify this at the command line by typing:

```
$ sudo iptables -n -L
```

You should see a lot of gobbledygook that represents your firewall rules.  If you don't have a firewall running, you would probably just see:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```
which are just rules that say to let all traffic pass through (i.e. no firewall).

The GUI is just a really easy to use tool that writes all the rules for you.  You need to enter your password to start it up, though, because it is an administrative tool.  The idea is if you are not going to be administering the box, you don't really need a tool that can potentially be alterning settings with the firewall.

So to answer your question, you can't really run the GUIs as non-root users.  I think it would be nice to be able to see the status information without necessarilly being able to change anything without having to enter a password, but I am not sure what the technical requirements for that would entail.

Does that help or make any more sense?

---

### Post by dresnu on 2005-06-26
Here's how to start the firestarter gui at gnome/kde startup anyway:
[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

---

### Post by raven on 2005-07-02
[QUOTE=cwaldbieser]As stated above, firestarter or guarddog, if installed correctly, *should* start automatically when your system boots without asking you for a password.  This is not exactly a normal program that you would expect to see running in your process list.  What actually happens is something like this:
1) System starts booting.
2) Firestarter script at /etc/firestarter/firestarter.sh is invoked.
3) Your firewall settings are read from a config file and loaded into the kernel ip tables.  From this point on, the kernel is actually in charge of accepting or rejecting packets.
4) The rest of the system starts up.

The GUI pieces are just tools you can use to view the current settings and to change them.  The firewall is still in effect, even if the GUI is not.  You can verify this at the command line by typing:[/QUOTE]


Thanx that is very clear,
my issue, I am using guarddog, 
"as an example" let's say I don't want any file transfer protocol to pass
and the ntp time protocol NOT to pass
I save my setting by clicking apply, guarddog do it's script
give the success, I try my FF browser and it is true I can not access the internet
connection refused, that is fine
I reboot the pc, on starting up again, my NTP sync with ubuntu servers will fail
that is fine, I log into my profile, and I can access the internet, even when I check 
the setting in my guarddog http and https are both blocked with an "X"
and still access the internet.
I click apply again , and at that moment it will block me
and that why I asked thinking that maybe it is not starting and I need to do it manually
your help is appreciated
I did remove completly once and reinstall, but same issue

Thanx

---

### Post by cwaldbieser on 2005-07-02
Hmm, I do not currently have Guarddog installed anymore, so I am not sure if there is anything useful in the man pages for it, nor can I poke around and look at the config files on my own PC.

The online help confirms you don't need Guarddog running to protect your computer.

A couple of things to try looking at:
```

$man guarddog
```

Might give you some extra info about config files, boot scripts, etc.

```
$ ls -l /etc/guarddog
$ ls -l /etc | grep guarddog
```

Might be some system wide config files there

```
$ ls -l /etc/rc2.d | grep guarddog
```

This is where I would expect a boot script for guarddog to be to start up the firewall settings.  If it is not there, check

```
$ ls -l /etc/init.d | grep guarddog
```

If the script is here, but not in the runlevel directory you boot up into, then you probably just need to make a symbolic link.

---

### Post by raven on 2005-07-03
Thanx for your help
As you mentioned you do not have guarddog installed
but I will put what I got from the commands you mentioned
maybe it will be usefull and gives you an idea

1-    $ls -l /etc/guarddog 
        ls  /etc/guarddog: No such file or directory

2-    $ ls -l /etc | grep guarddog
        would just give the prompt back no output no error

3-    $ ls -l /etc/rc2.d | grep guarddog
        would just give the prompt back no output no error

4-    $ ls -l /etc/init.d | grep guarddog
         -rwxr-xr-x  1 root root  1192 2004-10-26 22:05 guarddog

---

### Post by cwaldbieser on 2005-07-03
Open the terminal and type:

```
$ sudo ln -s /etc/init.d/guarddog /etc/rc2.d/S20guarddog
```

This creates a symbolic link from the startup script to the runlevel 2 directory.  When Ubuntu boots up, it starts in one of several runlevels and executes the scripts in the corresponding /etc/rc#.d directory.

To verify you boot into runlevel 2, just type:

```
$ runlevel
```
You should get back "N 2".  This is the default runlevel for Ubuntu.

It's somewhat weird, as the startup link should have been created for you during installation.

---

### Post by raven on 2005-07-04
1-  $ sudo ln -s /etc/init.d/guarddog /etc/rc2.d/S20guarddog
done
I saw the link in rc2.d 
link to /etc/init.d/guarddog 
-rwxr-xr-x  1 root root 1192 2004-10-26 22:05 /etc/init.d/guarddog

$ runlevel
N 2

but unfortunatley same issue
on bootup before X, I see guarddog being loaded
and it is making the effect as it will block my synch with ubuntu.ntp.server
I load X, log to my account, for some reason it would loose the settings
and allow all protocols to pass, until I get the GUI, click on "ok: or "apply"
than the effect of the guarddog settings will take effect
NB: I do not change any settings in the GUI,
just click on "ok: or "apply"

---

### Post by cwaldbieser on 2005-07-04
That is strange.  Do you have any other software installed that might also be doing something with Netfilter?  (Netfilter is the part of the kernel that does all the firewall stuff).  What other services do you have running at boot time?
```

$ ls -l /etc/rc2.d
```
should give me an idea of what you are running.

Also, out of curiousity, immediately after you boot, what is the output of

```
$ sudo iptables -n -L
```
this command will show what the kernel thinks the firewall rules currently are.

---

### Post by raven on 2005-07-05
we've got lift off
hey you've got it this time, what it was
I installed firestarter to test and I was sure I uninstalled it
but apperantly I did not
when I used your command
it showed me the firestarter script loaded
so what was happening
upon bootup guarddog loads, will block the ntp time sync
and when I load my profile which
will invoke the firestarter script and replace guarddog script
I disabled firestarter script and guarddog works like it should be
Thank you for your help

---

