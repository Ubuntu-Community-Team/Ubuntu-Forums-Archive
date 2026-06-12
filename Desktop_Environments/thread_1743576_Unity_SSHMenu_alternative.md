---
title: "Unity SSHMenu alternative"
date: 2011-04-29
forum: Desktop Environments
---

### Post by int19 on 2011-04-29
Hi there,

With natty/unity I've lost my handy SSH menu applet which I can use to quickly open connections to various hosts.  I've tried:

[http://castrojo.tumblr.com/post/4536294249/more-quicklists](http://castrojo.tumblr.com/post/4536294249/more-quicklists)
But it seems I have to log out and back in again each time I add a host to the .desktop file for them to show up in the context menu.  (and if I uncheck keep in launcher, I never have the option to add it again unless I rename my custom launcher)

I also tried just adding a new menu and launcher under System Settings -> Main Menu, but they aren't appearing in dash either.  Any good solutions?

Thanks!!!

---

### Post by v912485 on 2011-04-30
Same here. I cannot live without my SSHMenu!

Regards,
Allan

---

### Post by ffeingol on 2011-05-01
Add me to the list.  I'm a Linux admin with roughly 50 server in SSHMneu.  I'd really hate to have to back out 11.04.

---

### Post by Pimmelorus on 2011-05-02
Ah yes, the ssh menu I miss greatly. Please, could someone recommend or create a unity replacement?

Bye, Pim

---

### Post by robbie75 on 2011-05-02
Same problem for me.

For the moment I invoke sshmenu by typing in the unity launcher and a little windows with SSHMENU inside shows up so I can connect to my hosts but that's only a work around...

---

### Post by jjcv on 2011-05-02
I have created a profile for each host I connect to in The Terminal.  I can then open a terminal to that host from an existing terminal with File | Open Terminal | "Term_Name"

1. Open a Terminal and click on File | New Profile

2. Type in a Name for the Profile such as the host you connect to.

3. Up pops a screen to edit for the host.  Go to the "Title and Command" Tab

4.  Tick on "Update login record when command is launched"

5.  Tick on "Run a custom command instead of my shell.

6.  In the "Custom command" box add something like:  

   ssh -o ServerAliveInterval=30  hostname.example.com --title=Hostname
   
7.  Close

Repeat for all the hosts you want....

This is the only way I have found to deal with the non-sshmenu option.  Not as clean but it works for me.

---

### Post by toff72 on 2011-05-11
i have create a ssh launcher.desktop


[Desktop Entry]
Version=1.0
Name=Remote Servers
Comment=Login to my servers
Exec=gnome-terminal --disable-factory --sm-client-disable --class=remoteserver -x ssh -t cible.fr
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=utilities-terminal
StartupNotify=true
StartupWMClass=RemoteServers
X-Ayatana-Desktop-Shortcuts= ***_100 entries._***. ... . .. . . . . .;

[first Shortcut Group]
Name=SSH to first
Exec=gnome-terminal --disable-factory --sm-client-disable  --class=remoteserver -x ssh -t 1.2.3.4
TargetEnvironment=Unity



...
100 times
...
[last  Shortcut Group]
Name=SSH to last
Exec=gnome-terminal --disable-factory --sm-client-disable  --class=remoteserver -x ssh -t 1.2.3.42
TargetEnvironment=Unity




but it unusable and ugly ... there is too much servers


any ideas?

---

### Post by huhubaer on 2011-05-12
I hope the sshmenu developers will change te app to run using unity.

For a workaround look at [http://sshmenu.sourceforge.net/dev/hackers_guide.html](http://sshmenu.sourceforge.net/dev/hackers_guide.html)

It's not the best solution but you can use your existing config. ;)

St.

---

### Post by kinap on 2011-05-15
i'm not upgrading my work desktop to 11.04 unless i find a replace ment to sshmenu and the one that handles rdp session (don't know the name of that one)

---

### Post by Aenima99x on 2011-05-15
> **kinap said:**
> i'm not upgrading my work desktop to 11.04 unless i find a replace ment to sshmenu and the one that handles rdp session (don't know the name of that one)

Terminal server client works fine for RDP in Natty.

---

### Post by anilg on 2011-05-19
Hello all,

I felt your pain too. So I went ahead and wrote a small utility that behaves pretty much like sshmeny, but with appindicator menus.

[http://www.gulecha.org/2011/05/19/sshlist-an-appindicatorunity-replacement-for-sshmenu/](http://www.gulecha.org/2011/05/19/sshlist-an-appindicatorunity-replacement-for-sshmenu/)

Have fun!

---

### Post by ForbanFr on 2011-06-23
Hi,

There is another alternative: Remmina. It's a RDP/SSH connection manager (like putty connection manager on Windows). Works fine on my Ubuntu 11.04.

Hope this helps :)

---

### Post by phoolish on 2011-07-25
I took anilg's original idea and updated it.

I added a settings window to update from a gui, but you can still the .sshlist file.
Added title option, so you can name your ssh host command.

[https://github.com/lphilbrook/sshlist](https://github.com/lphilbrook/sshlist)

---

### Post by anilg on 2011-07-29
Thanks phoolish! And further modified to support sshmenu configuration.
[http://www.gulecha.org/2011/07/29/sshplus-a-sshmenu-compatible-appindicator/](http://www.gulecha.org/2011/07/29/sshplus-a-sshmenu-compatible-appindicator/)

---

### Post by rompe on 2011-09-18
For those wanting to switch from SSHMenu to Remmina, I have created a simple Python script that converts your SSHMenu configuration to Remmina configuration files. It converts the whole folder structure and recreates it under a "SSHMenu" folder in Remmina. There's also an easy rollback option. Find the script here:

[sshmenu_to_remmina.py]("http://blog.rompe.org/convert-sshmenu-to-remmina-configuration")

Rest in peace, SSHMenu!

---

### Post by wladyx on 2011-10-14
> **anilg said:**
> Thanks phoolish! And further modified to support sshmenu configuration.
[http://www.gulecha.org/2011/07/29/sshplus-a-sshmenu-compatible-appindicator/](http://www.gulecha.org/2011/07/29/sshplus-a-sshmenu-compatible-appindicator/)

I use a modified SSHPlus that allows folders, but it doesn't show an icon on 11.10 anymore.

[https://gist.github.com/1189327#comments](https://gist.github.com/1189327#comments)

Does anyone know what modifications must be made to the script?
Thanks for any suggestions.

---

### Post by Yadda on 2012-06-24
Hello

I've ported SSHMenu to Python/Gtk3. It's available at [https://github.com/MasslessParticle/pySSHMenu](https://github.com/MasslessParticle/pySSHMenu)

It reads your old SSHMenu configuration file so migration should be a snap.

---

