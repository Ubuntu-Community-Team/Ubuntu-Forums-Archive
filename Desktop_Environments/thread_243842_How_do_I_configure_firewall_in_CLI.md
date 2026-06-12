---
title: "How do I configure firewall in CLI?"
date: 2006-08-25
forum: Desktop Environments
---

### Post by anil_robo on 2006-08-25
I just finished installing Ubuntu server on an ancient computer (Pentium 166MHz with 64MB RAM). I have installed apache on it, and want to run local websites through it on my intranet. Now the question is, how do I configure the firewall in pure CLI to open port 80?

I searched on the forums as well as on google - couldn't find the answer. Please help.

P.S.: I can't install any fancy softwares on it because of low end system config, and extremely limited HD space (just 1GB HD, 50% of which is full already) ;)

---

### Post by Bachstelze on 2006-08-25
Have you tried accessing your webserver without configuring iptables at all ? It should work with the default config.

---

### Post by anil_robo on 2006-08-25
I type apache in terminal and press enter.

It says httpd.conf is missing. Let me create it first... but I know Ubuntu comes with all ports closed by default... so I'm sure I'm gonna need to open port80 manually.

---

### Post by az on 2006-08-25
> **anil_robo said:**
> I type apache in terminal and press enter.

It says httpd.conf is missing. Let me create it first... but I know Ubuntu comes with all ports closed by default... so I'm sure I'm gonna need to open port80 manually.

Apache is already running once you installed it, and every time you reboot.

And you do not need to "open" a port.  An open port is one that has something listening on it.  When apache starts, it listens on that port and so the port is "open".

By default, nothing listens to the network.  In this case, nothing was listening on port 80 until you installed apache.

---

### Post by anil_robo on 2006-08-25
Okay, now I'm in trouble because I'm using CLI for the first time.

I think everything used to be set up automatically in Ubuntu... but why can't I see a /var/www directory? And why isn't there a default httpd.conf set up automatically?

Where is the default location of apache? Where are its config files stored? Where is cgi-bin supposed to be? And finally, what is the httpdocs directory? :confused:

---

### Post by az on 2006-08-25
> **anil_robo said:**
> Okay, now I'm in trouble because I'm using CLI for the first time.

I think everything used to be set up automatically in Ubuntu... but why can't I see a /var/www directory? And why isn't there a default httpd.conf set up automatically?

Where is the default location of apache? Where are its config files stored? Where is cgi-bin supposed to be? And finally, what is the httpdocs directory? :confused:

How did you install apache?  Did you install apache2 (newer and better thanapache, the old version)

You need to install the apache2-doc package to get the documentation.

All the settings for apache2 are in /etc/apache2

There is a default config set up and the /var/www directory should be there.  Are you sure it is installed?

---

### Post by anil_robo on 2006-08-25
Oops... I installed apache (1) instead of apache2! What a nerd I have become!

I dumped Ubuntu earlier this year in favor of studies... and now I see how much I lost! I'm installing apache2 now. Will keep asking questions here! :) Thanks folks

---

### Post by anil_robo on 2006-08-25
I have installed apache2 now. And I see that it neatly placed everything in /etc/apache2 directory, started listening on port80, and told me that /var/www directory is where my files should be. I see apache2 installation is a lot more user-friendly than apache1.

---

### Post by oddchild on 2007-10-31
I think I am having a firewall conflict with my Httpd 

it worked fine for about a month, but then stopped. It displays pages when I look at localhost, but when I look from outside the computer, it does not display.

I have been working on it via vnc since it is far away. is there anyway that i could have accidently closed the port, when i went to 7.10?

Thanks

---

