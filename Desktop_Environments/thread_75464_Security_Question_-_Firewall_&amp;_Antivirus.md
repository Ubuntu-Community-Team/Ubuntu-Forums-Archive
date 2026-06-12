---
title: "Security Question - Firewall &amp; Antivirus"
date: 2005-10-13
forum: Desktop Environments
---

### Post by imad_b on 2005-10-13
Several questions on this:

**Is it needed?**
I know it's probably a crazy question.
My immediate answer would be yes of course.

But then I have read a few threads on the internet where linux users say it's not necessary.
I was looking through the Linux Format magazine (Oct 2005), and they were quite serious about the whole issue, saying YES, Linux users should have antivirus and firewalls installed.

**Do Ubuntu users have any personal recommendations on firewalls & antivirus?**
On my XP system I use Bitdefender, which had firewall, antivirus, spam filters etc.  I was quite happy with them.
I noticed they have a Linux flavour as well.

**Has anyone used Bitdefender for Linux?**

I installed Firestarter & Aegis Virus Scanner via the Add Applications, and they installed ok.....BUT I can't find them :???: 
They are not in Applications>System Tools.
**Does anyone know where they could be?**

Thanks for your help.

---

### Post by drummer on 2005-10-13
[QUOTE=imad_b]**Does anyone know where they could be?**[/QUOTE]
If you've just installed them, try running in a terminal ```
killall gnome-panel
``` and the applications should appear there, if not, you can run them by pressing Alt-F2 and typing the application name to run it. Firestarter should just be 'firestarter' (without quotes) but if there's a warning saying you're not running it as root, close it and run 'gksudo firestarter'.

Should be the same for the antivirus program, I'm just not sure what the command is to run it.. perhaps 'avs'

Hope that helps

---

### Post by pear-i on 2005-10-13
as for a more permanent solution -- once you try those above commands fire up smeg (menu editor) and add them to your applications menu

---

### Post by cfa on 2005-10-13
Is it needed?

yes if you use some typical server services like apache,ftp .... 


Has anyone used Bitdefender for Linux?

yes , nothing special about it , it's ok

BTW you could also look for some cool stuff like amavis, firehol ....
in order to be more protected if you want ...

:p

---

### Post by RAOF on 2005-10-13
[QUOTE=cfa]Is it needed?

yes if you use some typical server services like apache,ftp .... 
[/QUOTE]
Unless you're doing something reasonably advanced (like only allowing ftp connections from specific ips/subnets/whatever), a firewall in front of these will just let everything through to these services.  It has to, becuase you're presumably running these services so that you can access them from the outside world :)

Ubuntu (IIRC) by default doesn't have any ports listening, so it is entirely secure from that sort of remote attack.

The reason why a regular user might want a firewall is to block **outgoing** traffic.

---

### Post by Ferio on 2005-10-14
I've installed Aegis Virus Scanner with my brand new Breezy Badger's Add & Remove Programs feature, but it's not shown in my Accesories menu even if I kill the panel, though it's shown in my SMEG, any idea about why this could be?

---

### Post by Ferio on 2005-10-16
I just patched it by adding a new entry to the menu and deselecting the good one. Not a solution, but it works.

---

### Post by anil_robo on 2005-10-18
I have downloaded aegis virus scanner thru synaptics on Breezy.
The command to run it is "aegis-virus-scanner" without quote marks.
When I run it through Terminal, the virus scanner starts and says there's a new update available. It asks for downloading the new update (yes/no). I click yes, and another terminal window pops up, asking me the password. I enter the password, a lot of things happen on screen (I presume they have updated my definitions), and then the second terminal window closes.

Then, when I look at the first terminal window (from where I launched the scanner), I get the following error code:

(gnome-terminal:3194): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:3194): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

Now, all said and done, I have the following questions:

1. Is Aegis Virus Scanner installed correctly?
2. Has it been able to update the virus definitions?
3. How do I make sure it *works*?
    (...without infesting my system with a test virus... )

Thanks!

---

### Post by bluck on 2005-10-18
[QUOTE=RAOF]Unless you're doing something reasonably advanced (like only allowing ftp connections from specific ips/subnets/whatever), a firewall in front of these will just let everything through to these services.  It has to, becuase you're presumably running these services so that you can access them from the outside world :)

Ubuntu (IIRC) by default doesn't have any ports listening, so it is entirely secure from that sort of remote attack.

The reason why a regular user might want a firewall is to block **outgoing** traffic.[/QUOTE]

i cant agree with you.  lets say an attacker finds an exploit in your webserver application, enabling him console access with the privileges of your webserver's running user,  he can then use that to open another server on a different port. a place to plant his "nasties" to retrieve from zombied machines elsewhere.  or a place for his nasties to do attacks on other machines, spam via php scripts, the list goes on.

a firewall is to regulate the flow of traffic both in and out.  you open the ports you need to open and everything else is blocked.  your firewall, is also best if thats all it does, rather than firewall software on your desktop machine.

---

### Post by patrick295767 on 2005-10-19
[QUOTE=bluck]i cant agree with you.  lets say an attacker finds an exploit in your webserver application, enabling him console access with the privileges of your webserver's running user,  he can then use that to open another server on a different port. a place to plant his "nasties" to retrieve from zombied machines elsewhere.  or a place for his nasties to do attacks on other machines, spam via php scripts, the list goes on.

a firewall is to regulate the flow of traffic both in and out.  you open the ports you need to open and everything else is blocked.  your firewall, is also best if thats all it does, rather than firewall software on your desktop machine.[/QUOTE]


Hi !!

I am newbie... after reading your post, which firewall would you recommand me to  use ? 

(I used looong long time sygate firewall (port blocker and app blocking) in windows ...)

Thank you very much for your help, 

Patrick

---

### Post by .Danny on 2005-10-19
I've installed Firestarter earlier today, but when I run it it's giving me a error.

```
Failed to start the firewall

The device eth0 is not ready.

Please check your network settings and make sure your Internet connection is active.
```

Obviously it's active since I'm on IRC and surfing around on websites.. so where's the catch? :rolleyes:

---

### Post by manicka on 2005-10-19
[QUOTE=Lord Death]I've installed Firestarter earlier today, but when I run it it's giving me a error.

```
Failed to start the firewall

The device eth0 is not ready.

Please check your network settings and make sure your Internet connection is active.
```

Obviously it's active since I'm on IRC and surfing around on websites.. so where's the catch? :rolleyes:[/QUOTE]

what type of connection do you have?

---

### Post by .Danny on 2005-10-20
[QUOTE=manicka]what type of connection do you have?[/QUOTE]

A DSL connection over PPPoE on eth0. Starts on startup.

---

### Post by bluck on 2005-10-21
[QUOTE=patrick295767]Hi !!

I am newbie... after reading your post, which firewall would you recommand me to  use ? 

(I used looong long time sygate firewall (port blocker and app blocking) in windows ...)

Thank you very much for your help, 

Patrick[/QUOTE]

well, like i mentioned, its better to have a separate device dedicated to the firewall role.  for the average home user, one of those "broadband routers" is good enough, provided you take the time to set it up (change the passwords, the default name, disable remote config). 
feel free to message me directly if you have questions on that. :)

personally, i use an older PC running OpenBSD for my firewall...  not really a newbie project... :)

---

