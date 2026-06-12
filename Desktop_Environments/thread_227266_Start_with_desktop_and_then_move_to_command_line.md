---
title: "Start with desktop and then move to command line"
date: 2006-08-01
forum: Desktop Environments
---

### Post by andrewheard on 2006-08-01
Hi,
I'd like to set up an Ubuntu or an Xubuntu web/ssh/privoxy server. I have a crappy old 300MHz computer with 64MB of RAM that I'd like to do this with. What I wanted to know is if its possible to configure the server with a graphical environment like Gnome or Xfce and then to not startup X by default thereafter. Once I've got everything set up, its not like it needs to be running Gnome for serving webpages. Would the specs I listed be fine for this kind of server? It would be 2-3 users using it at once.

---

### Post by ardchoille on 2006-08-01
I feel that it would be much more to your advantage to learn how to set everything up via command line.. don't even use X at all. The reason I say that is that, it may take a little more time, but the things you will learn will have a lasting effect on your Linux experiences in the future. The person who introduced me to Linux made me use it from command line, she didn't even allow me to install a graphical desktop until my 6th month using Linux.

Today, when I want to do something, I use the knowledge I gained from that.. I can do almost everything from cli and there are weeks at a time that I log into tty1 and don't even use x. I use screen sessions with irssi, mutt, elinks, bash, midnight commander, mpg123 and other apps.

Sure, it's nice to have a full desktop at times, but if X were to refuse to start, I won't be totally lost.

Just some friendly advice :)

---

### Post by Ramses de Norre on 2006-08-01
Disabling gdm to start up will disable X being started I think, I also have a  binary x11-common which is loaded on runlevel two, this might trigger Xorg too. You can try it out and disable x11-common if necessary.

And you will indeed learn a lot when you set your system up with cli only but that's pretty hard when you're new to the command line, so unless you've got friends with a lot of linux knowledge or good books I would go for X.

---

### Post by ardchoille on 2006-08-01
Well, yes, if you know you have an easier way to do things, then there is no incentive to learn another way.

---

### Post by afbase on 2006-08-01
This will install:
    *  Web Server: Apache 2.0
    * Database Server: MySQL 5.0
    * Mail Server: Postfix
    * DNS Server: BIND9
    * FTP Server: proftpd
    * POP3/IMAP: I will use Maildir format and therefore install Courier-POP3/Courier-IMAP.
    * Webalizer for web site statistics

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)



------------------------------
[https://help.ubuntu.com/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/ubuntu/serverguide/C/index.html)

That should go to the server guide. I believe all commands in both links are given in command lines.  

Good Luck.

By the way, if you are a linux noob, just dive right into command line.  GET YOUR FEET WET!! I'm still a noob and I prefer CLI over GUI any day

---

### Post by nihilocrat on 2006-08-01
After installing all your services with apt-get, all you really need to know how to do from the command line is copy/move/delete files, move around in directories, change ownership/permissions, and edit config files (I find nano to be the easiest-to-use cli text editor). It would be very worthwhile to learn all of these things, and they're really not that complicated if you take them one at a time.

If you have absolutely zero cli experience (c'mon, you used DOS in the 90's all the time because none of the cool games ran on Windows, right?) I would suggest starting with the 'cd' and 'ls' commands, then move on to 'cp', 'mv', 'rm', and then finally stuff like 'chown' and 'chmod'. You don't need to memorize all the possible command-line arguments for them, that's what '<command> --help' and 'man <command>' are for.

---

### Post by andrewheard on 2006-08-01
Well I'm fairly comfortable with the command line but I just like having the GUI to fall back on. I could just try and do it with the command line and then if I get stuck I could just install Gnome then.

---

### Post by andrewheard on 2006-08-01
> **nihilocrat said:**
> 
If you have absolutely zero cli experience (c'mon, you used DOS in the 90's all the time because none of the cool games ran on Windows, right?) 

Fortunately I never used DOS. I was like 5 when Windows 3.1 came out. I do have experience using the command line though. Its almost necessary to get the full experience out of desktop linux even. Sometimes I even need to bring out the Terminal on my Mac. 

What I'm not used to though is having nothing but a command line. Normally I'm just using a Terminal window. Except when I made a typo in my Xorg.conf file and then had to use the joe text-editor to fix it.

Thanks for all the replies.

---

### Post by stanz on 2006-08-01
Hi All...
another page, to add to afbase's comment, is also on ["howtoforge".]("http://www.howtoforge.com/lamp_installation_ubuntu6.06")
It adds GUI help & instructions with Ubuntu's LAMP server, 
but I think it'll work anywhere!?
Please let me know how this goes for ya, ~ as I'm trying to learn this also...
It's First time for me and without someone here helping.. :(

---

### Post by stanz on 2006-08-01
Doubled post...somehow?

---

### Post by fragos on 2006-08-01
CLI and GUI are almost a religious argument.  What I found that worked well for me is to start with the GUI for configuring and use the CLI to examine.  You get your feet wet with CLI without learning the hard way that to set this I have to set that.  I now use both for setting configurations but take no shame in also using a GUI.  The best tool is always the one you can and do use.  Neither tool is superior 100% of the time but knowing one help you understand the other.

---

### Post by fragos on 2006-08-01
CLI and GUI are almost a religious argument.  What I found that worked well for me is to start with the GUI for configuring and use the CLI to examine.  You get your feet wet with CLI without learning the hard way that to set this I have to set that.  I now use both for setting configurations but take no shame in also using a GUI.  The best tool is always the one you can and do use.  Neither tool is superior 100% of the time but knowing one help you understand the other.

---

### Post by andrewheard on 2006-08-01
So far I've been able to get Apache2 with PHP4, SSH, FTP and Privoxy installed and working all using the command line. Now I can just hide the old crap PC in the basement and SSH to it from my Mac. I also need to say thanks to afbase because that link you sent was very helpful. Now all I need to install is Perl for some CGIProxy action.

---

