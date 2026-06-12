---
title: "ubuntu and remote desktop use"
date: 2013-10-25
forum: Desktop Environments
---

### Post by bmullan2 on 2013-10-25
I thought I'd post this as an fyi.

For an ubuntu remote desktop capability I've traditionally used x2go (x2go.org).   After having tried NX, neatx, FreeNX and others, I found x2go to be:
[LIST]
[*]simple to install
[*]sound/audio, printing and local file share worked out of the box
[*]it is actively developed.
[/LIST]

I stopped using NX because the close sourced it and although you can get a free 2 desktop version for personal use that seemed limited.
FreeNX was ok but audio was always a  problem for me to get working correctly as well as just the configuration seemed a bit complex and I thought it would turn off some users.
Neatx - seems to have been more or less abandoned.

With the advent of Unity & Gnome3 and thus 3d desktop acceleration ... all traditional remote desktop approaches (vnc, NX, x2go etc etc) all failed to work.

While Unity-2d or gnome-session-fallback were still available that could still be solved though by installing/using those.

However, with Ubuntu 13.10 and I assume moving forward it appeared to me that my choice was to install a desktop more compatible with the traditional remote desktop applications (again vnc, nx, x2go etc).
So xfce, lxde and a few other choices still work really well as remote desktop "server" machines.

I have also recently started experimenting with Guacamole (guac-dev.org) and their HTML5 browser based remote desktop.

I've gotten it working pretty well but am still struggling with how to get the audio/sound working.   But although I know what the problem is I'm still trying to figure out how to fix it.   Note that others have already gone beyond this with Guacamole.

So here's some how-to in a nutshell information for installing x2go and also for Guacamole.    

Note: any easy way to test this is either with an Ubuntu Server image installed in a KVM VM or in an LXC container then use the "host" machine as your client to log into the VM/container's desktop.

[SIZE=4]_**x2go (see [www.x2go.org]("http://www.x2go.org"))**_[/SIZE]

Install Ubuntu Server in VM/container and log into it.

# add a non-3d desktop of your choice (xfce or lxde are easy to use)
# for xfce
**$ sudo apt-get install xubuntu**
# for lxde
**$ sudo apt-get install lxde**

# with a non-3d desktop installed next install x2go server

# add the x2go ppa if you want to use the latest ... but I believe x2go is already in the ubuntu repositories so you should not have to do the following
[B]$ sudo add-apt-repository ppa:x2go/stable
$ sudo apt-get update
$ sudo apt-get install xgoserver x2goserver-xsession[/B]

When that installation is complete I've found that on Ubuntu if you are going to use a login/password scheme for x2go you need to edit/change 2 lines in /etc/ssh/sshd_config[INDENT][I][FONT=arial]# Change to yes to enable challenge-response passwords (beware issues with[/FONT]
[FONT=arial]# some PAM modules and threads)[/FONT]
[FONT=arial]ChallengeResponseAuthenticatio[/FONT][FONT=arial]n no[/FONT]

[FONT=arial]# Change to no to disable tunnelled clear text passwords[/FONT]
[FONT=arial]#PasswordAuthentication yes[/FONT][/I][/INDENT]

# In the above lines of the sshd_config ***change***
# ChallengeResponseAuthentication yes
# and 
# uncomment PasswordAuthentication so it is set to yes

# Save the edit and restart ssh:
**$ sudo service sshd restart**

# lastly... for x2go ... any user wanting to remote desktop to "this" Ubuntu Desktop 'server' needs to be a member of the x2gouser "group"
# don't forget to do this for at least yourself

**$ sudo adduser myname x2gouser**

# note you will have to do this for any other user you add later.

# that's it for the server side ... although on the x2go website there are a lot more sophisticated server side setups you can take advantage of such as LDAP etc

# installing the x2go client is even easier
# again assuming for your test purposes the "host" OS is your client, again you will either need to use the x2go already in the Ubuntu repositories or you can add the x2go PPA as shown above 

# so on the host in a terminal...

**$ sudo apt-get install x2goclient**

# that's it.

# get the IP address of your VM (use ifconfig) 

# from the Unity DASH search of x2go and launch the x2go client

# when the gui appears create a new session profile (click the box in upper left corner)
# enter the IP address of the x2go server
# select which "desktop" environment you will be using (xfce or lxde from this example) and save the profile
# note:   there are several other tabs you should look at if you want to specify other things like different window size (default is 800x600) etc.
# this will create a profile box on the right side of the x2go client menu
# double click on that box
# x2go will prompt you about accepting the connection that you will have to accept
# if you've done everything correctly... in about 3-4 seconds you should see your remote desktop appear.

# x2go is very fast and as you will see sound, printing, sharing directorys etc all just work.

# NOTE:   I've used x2go with Ubuntu Desktop "servers" on Amazon's cloud alot and the performance is very good.

# FINALLY...   if your Clients machines are UBUNTU ... x2go offers an x2goplugin capability that allows you to just use a Browser (I've tested Firefox, Opera and Chrome) as the remote desktop client
# To use this DOES require one extra installation on the "client" OS/machine

# the steps are documented on the x2go.org website under the "Advanced" section:   [http://wiki.x2go.org/doku.php/wiki:advanced:x2goplugin](http://wiki.x2go.org/doku.php/wiki:advanced:x2goplugin)
# after moving the example x2goplugin.html to /var/www I've found that the only 2 config changes I usually have to make is
# server = "localhost"   changing localhost to the IP address of the server
# command = "XFCE"    changing this to whatever Desktop I am using (XFCE, LXDE)

# After doing that and restarting the web server you can log in from your "client" using a web browser and get your remote desktop

          **http://<your x2goserver IP>/x2goplugin.html**


[SIZE=4]_**Guacamole ([www.guac-dev.org]("http://www.guac-dev.org"))**_[/SIZE]

# There are alot of HTML5 remote desktop applications popping up but almost all of them or oriented to Windows.   Guacamole however is focused on Linux.
# Guacamole still has some work to do (my perspective) but it is still a very good application and the performance is also quite good (although not as good as x2go).

# The benefit of Guacamole is that you do NOT have to install _any_ client side application to make a connection and the Client can be any OS (windows, Mac or Linux)

# Guacamole gives you the choice of using only VNC or RDP (note: x2go supports IP and RDP)

# The general installation instructions on the guac-dev.org website are pretty good.
# for Ubuntu there is a PPA which makes the installation of the Desktop "server" reasonably simple although 

# so again assuming you are testing this out on a VM or an LXC container... again assuming you've installed an Ubuntu Server image

# as with x2go you will need a NON-3d desktop so again install xfce or lxde (shown above) or I've also installed and used Mate (because its gnome2 based)

# add the Guacamole PPA (this is documented on the guac-dev site: [http://guac-dev.org/doc/gug/installing-guacamole.html#idp99200](http://guac-dev.org/doc/gug/installing-guacamole.html#idp99200))

[B]$ sudo add-apt-repository ppa:guacamole/stable
$ sudo apt-get update[/B]

# install the guacamole server components

**$ sudo apt-get install guacamole-tomcat**

# Now Ubuntu's repositories already have FreeRDP and xrdp present but to get a full desktop experience using Guacamole I've found it works best if I'm using the latest/greatest of those.
# Building & installing xrdp, x11rdp, freerdp can be a bit challenging for most people but there is a site called ScaryGliders (not sure where the name came from) that has a terrific pair of
# scripts that automates the entire Build/Install for these 3 apps (xrdp, x11rdp, freerdp).

#  Follow the instructions here:  [http://scarygliders.net/2013/07/25/x11rdp-o-matic-version-3-now-released/](http://scarygliders.net/2013/07/25/x11rdp-o-matic-version-3-now-released/)

# there are basically only 3 things to do (4 if you don't already have GIT installed on the "server" machine so make sure you $ sudo apt-get install git before you start)
[B]
$ git clone [https://github.com/scarygliders/X11RDP-o-Matic.git](https://github.com/scarygliders/X11RDP-o-Matic.git)[/B]
**$ cd X11RDP-o-Matic**

# NOTE:  the following command can take 15-20 minutes to download, compile & install the above 3 apps depending on your machine so be patient
**$ sudo ./X11rdp-o-matic.sh --justdoit**

# when the above is complete you need to use the Scaryglider script to create user "session" profiles which Guacamole will utilize

**$ sudo ./RDPsesconfig.sh**

# from the menu presented pick the desktop (xfce or lxde in our example)

# that's it for the ScaryGliders work so back to Guacamole to finish up
# to use RDP you need to install a couple other components.   Note you can use VNC with Guacamole but performance is not as good as RDP

**$ sudo apt-get install libguac-client-ssh0 libguac-client-rdp0**

# After this is done the last step is to edit the /etc/guacamole/user-mapping.xml file
# in this file "insert" a section for allow use of RDP w/your login ID and PWD
# note as with x2go there are more advanced setups such as LDAP support etc but refer to the guac-dev website for that.   For our example test the following is enough.

[INDENT]<authorize user="*yourLoginID*" password="*your password*">[/INDENT]
[INDENT]   <connection name="Put a Unique Name here">[/INDENT]
[INDENT]       <protocol>rdp</protocol>[/INDENT]
[INDENT]       <param name="hostname">*localhost*</param>[/INDENT]
[INDENT]       <param name="port">3389</param>[/INDENT]
[INDENT]   </connection>
</authorize>[/INDENT]
[INDENT]
[/INDENT]
# after you save the changes to this file restart the Tomcat6 web server

**$ sudo service tomcat6 restart**

# go to your host OS and start a browser and plugin the following:

**http://<IP address of your VM or container>:8080/guacamole.html**

# you will be presented with an initial login screen .. enter your login ID and password and in about 3-4 seconds you should get your xfce or lxde desktop display.

# again I will tell you that I've not gotten audio to work yet but I assume its just my being a dolt but anyone that gets that also working please post how you did it.

I hope this is helpful for some of you.

---

### Post by matt_fussell2 on 2014-05-14
I followed the instructions located here for guacamole, however I am receiving and error from tomcat telling me the /guacamole.html resource is not available. RPD works like a charm, except there is no sound. Any suggestions? If you need any outputs, just let me know and I'll get them posted.

---

### Post by matt_fussell2 on 2014-05-15
x2go seems to be working amazingly well, except that sound isn't currently working for me. I started with ubuntu server 12.04 running in an esxi vm. I used lxde for the desktop. I've installed pulseaudio and alsa, added my user to the 'pulse' group, and verified it using the 'groups' command. Is there something I'm missing to get sound working? This is literally the last hurdle to get a distributed desktop environment up and running.

---

### Post by matt_fussell2 on 2014-05-15
My desktop client is running ubuntu 14.04 ... would that make a difference?

---

### Post by matt_fussell2 on 2014-05-19
I came back to this to continue working out why the sound wasn't working  - I started with a new 'server' machine on a physical box running  Ubuntu 14.04. Again, x2go worked well, and again, there was no sound. I  looked for similar issues related to x2go since I eliminated other  environmental variables. The package that turned out to be key in  getting sound to work was to install paprefs to enable the sound  configuration to be 'piggy-backed' off the initial ssh connection.

```
sudo apt-get install paprefs
```

After doing this on both machines, sound works for both media playback and for skype. Thanks for the guide, though I would still be interested in getting your thoughts on the guacamole setup.

---

### Post by matt_fussell2 on 2014-05-29
One last item of note that I found - starting from Ubuntu 13.04, selecting the default LXDE option on the x2go client will cause the 'logout' function on the remote machine to fail, resulting in the session being endlessly maintained and necessitating termination each time you attempt to reconnect to the server. To fix this, instead select 'Custom Desktop' and enter the following command string:
```
ck-launch-session startlxde
```

'Logout' will now close the remote connection.

---

### Post by paul142 on 2014-06-02
This is good information. Thanks for sharing. :)

---

### Post by Paul_Davison on 2015-04-12
> **bmullan2 said:**
> I thought I'd post this as an fyi.

...

[SIZE=4]_**Guacamole ([www.guac-dev.org]("http://www.guac-dev.org"))**_[/SIZE]

# There are alot of HTML5 remote desktop applications popping up but almost all of them or oriented to Windows.   Guacamole however is focused on Linux.
# Guacamole still has some work to do (my perspective) but it is still a very good application and the performance is also quite good (although not as good as x2go).

...

# go to your host OS and start a browser and plugin the following:

**http://<IP address of your VM or container>:8080/guacamole.html**

# you will be presented with an initial login screen .. enter your login ID and password and in about 3-4 seconds you should get your xfce or lxde desktop display.


I actually found that the URL required is:

**http://<IP address of your VM or container>:8080/guacamole**

note: without the .html suffix

Plus another useful tip for obfuscation or if something else uses port 8080...
If you want to change the default port, this is set in the file: /etc/tomcat6/server.xml

Search for: Connector port="8080" and change to whatever port you want

At the time of writing, this is found on line 71 (version 0.8.3 in the repository)

I've found guacamole runs pretty quickly.

---

### Post by bmullan2 on 2016-01-09
I've just finished a project integrating guacamole, mysql, nginx, xrdp and also LXD/LXC containers all using ubuntu 15.10 (but same scripts work on 15.04 and so far on 16.04 alpha) for the server/host.

The xrdp was built using scaryglider's great script (saving a ton of complicated work) but resulted in xrdp v 0.9.0  .DEB file versus the Ubuntu repositories very old xrdp v 0.6.0.
The guacamole is version 0.9.8 vs the guacamole in the Ubuntu repositories which is again a pretty old v 0.8.3.

The mysql provides a database for maintaining user and connections configuration info.    So you don't need the .xml config file that the simple guacamole install uses and also because you can then use the really nice Guacamole Admin web interface to 
manage users & connections to "servers" ...  in my case "servers" were the actual Host/Server plus the 2 LXD/LXC containers.

Nginx is used to support use of HTTPS (TLS) instead of the just HTTP.   So the user connectivity to the Server providing the Desktop Environment (DE) is all encrypted.

I'm using LXD/LXC because not only is it awesome technology but because on the Server/Host I could install many different containers which may or may not have the same DE.   By default my scripts only create 2 LXC containers CN1 and CN2.

CN1 has Ubuntu-Mate installed in it and CN2 has Xubuntu/XFCE4 installed in it.   The Host/Server also gets Ubuntu-Mate DE installed.

*Note:  Neither Unity nor Gnome3 as far as I know can be used with any of the remote desktop software I am aware of whether that be NX, x2go or Guacamole for technical reasons.*

Anyway, in testing on AWS EC2 cloud and on Digital Ocean cloud servers the entire installation including server & 2 containers takes about 20-30 minutes.

So far in my testing the scripts work fine and install everything correctly on ubuntu 15.04, 15.10 and in 1 test on an Ubuntu 16.04 alpha server & I've repeated the installs using cloud servers perhaps 20 times now with no failures.

I'm trying to figure out where to put the documentation & scripts though as I'm not familiar with github other than as a end-user not a programmer.


I'm trying to fig

---

