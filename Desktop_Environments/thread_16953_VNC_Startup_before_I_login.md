---
title: "VNC Startup before I login?"
date: 2005-02-24
forum: Desktop Environments
---

### Post by slaya on 2005-02-24
Hello, I would like VNC to start before I login to my account. Is this possible without having to login with SSH first and turning VNC on?

I would like to let everyone know that I am totally new to Linux too.

Thanks

---

### Post by cwaldbieser on 2005-02-27
Well, yes and no.  I haven't been able to find a way to get vino (which comes pre-installed in Warty I think?) to do what you're asking.  VNC is normally a kind of remote-control for an existing session, and when no one is logged in, there is no session to remote control.

However, there are VNC packages for Linux that act more like remote desktop on Windows.  They create a fake session that the user remote controls, so it's like you remotely log into a new session when you use it instead of controlling an existing user's session remotely.

With that kind of VNC, you can have it start up at boot time using the normal Sys V startup stuff.  Since you are new to Linux though, you might not be totally familiar with that either, so I will try to elaborate on both a little.

Fire up the synaptic package manager and search for VNC.  You will probably see a bunch of interesting VNC related software that you can read about, but you are interested in getting a VNC server that creates the fake displays.  vncserver or tightvncserver might be good choices (I haven't done this in a while, so you ought to read the descriptions to make sure!).

After you install the software, you can test it out by running the vnc server from the command line-- for example:

```
$ tightvncserver
$ ps -Al | grep vnc

```

The first command runs the tightvncserver (which might ask you to specify a password users need to enter when connecting to the server-- make up whatever you like).  The second command should print out the process ID and name of the process that is running the vnc server.  You can try connecting from another computer now, and you should be able to connect to the fake session.

At this point, you want to know how to auto-start the server when the system boots.  This is not too hard, but it does involve the peculiar concept of runlevels.

When the default Ubuntu system starts up, it starts at runlevel 2.  There are a total of runlevels 0-6, but 0 and 6 are reserved for single-user and reboot mode.  When the system boots, it looks in /etc/rc#.d, where the # is the runlevel number.  If you look in /etc/rc2.d, you should see a bunch of kooky looking file names like S20inetd.  These files are symbolic links to scripts that are run at boot time.  The "S" at the beinning of the link has some special meaning, but I forget what it is at the moment.  The number following it determines what order the scripts are executed in.  You want your own stuff to be executed later, so you will probably want to create a link with a name like "S99local".

For example, I'd create a text file, /etc/init.d/rc.local that looks like this:

```
#!/bin/bash

tightvncser
```

Next, I make the script executable, and create the link:

```
$ chmod o+x /etc/init.d/rc.local
$ ln -s /etc/init.d/rc.local /etc/rc2.d/S99local
```

So now when the system starts, it looks in /etc/rc2.d, finds the link S99local pointing to /etc/init.d/rc.local and runs it.  That script runs tightvncserver.

Now you are probably wondering, OK, but how do I set the password non-interactively.  For that you have to read the man pages on your vnc server.  I am guessing there is probably a setting you can tweak in /etc/vnc.conf or some file like that.

Hope that helps!

---

### Post by slaya on 2005-03-02
Hrm, that works when I login and start it but when I reboot and don't login it says connection refused.

Thanks for the reply though

---

### Post by cwaldbieser on 2005-03-02
Hmm, maybe there is some reason that the script fails on startup?  Is there anything useful in /var/log/syslog after you reboot (or if you type dmesg at the prompt)?

You could also try having the startup script append some messages to a file so you could see if it was running correctly.  

For example:

```
#!/bin/bash

echo "Before call to tightvncserver" >> /home/username/mylogfile.txt
tightvncser
echo "After call to tightvncserver" >> /home/username/mylogfile.txt
```

---

### Post by slaya on 2005-03-02
[QUOTE=cwaldbieser]Hmm, maybe there is some reason that the script fails on startup?  Is there anything useful in /var/log/syslog after you reboot (or if you type dmesg at the prompt)?

You could also try having the startup script append some messages to a file so you could see if it was running correctly.  

For example:

```
#!/bin/bash

echo "Before call to tightvncserver" >> /home/username/mylogfile.txt
tightvncser
echo "After call to tightvncserver" >> /home/username/mylogfile.txt
```[/QUOTE]

Hey,

Just to make it clear, and rule out this possibilty for it not working, I have "tightvncserver" without quotes in my rc.local file and not "tightvncser".

Anyways, it does echo "Before call to tightvncserver", and "After call to tightvncserver", but when I try to connect I recive a connection refused error.

If I SSH into the server and type "tightvncserver" without quotes in terminal it starts fine. So i'm not sure why it's not working.

Also, nothing usefull in syslog.

Being illiterate in Linux doesn't help either  :sad:

---

### Post by cwaldbieser on 2005-03-02
Sorry about the typo.

Here is a thought-- I think the system runs as root during the bootup process.  Maybe the tightvncserver program is not in root's path.  Try including the the full path to the tightvncserver.  You can get it by typing
```

$ type tightvncserver
```

At the prompt.  (Mine is /usr/bin/tightvncserver).

Then change the script to use the absolute path:

```
#!/bin/bash

#Uncomment the next line to try sleeping for a bit.  
#Sometimes that gives other processes a chance to spin up.
#sleep 5

/usr/bin/tightvncserver
```

---

### Post by slaya on 2005-03-03
[QUOTE=cwaldbieser]Sorry about the typo.

Here is a thought-- I think the system runs as root during the bootup process.  Maybe the tightvncserver program is not in root's path.  Try including the the full path to the tightvncserver.  You can get it by typing
```

$ type tightvncserver
```

At the prompt.  (Mine is /usr/bin/tightvncserver).

Then change the script to use the absolute path:

```
#!/bin/bash

#Uncomment the next line to try sleeping for a bit.  
#Sometimes that gives other processes a chance to spin up.
#sleep 5

/usr/bin/tightvncserver
```[/QUOTE]

Hey, it's okay about the type :)

Actually, I did try using the absolute path, a friend of mine told me about that. Unfortunately, it didn't work.

I've been messing around trying to change things, but nothings worked so far, i'll keep trying though.

Thanks

---

### Post by crmanski on 2005-05-13
Since the vnc server you want to  connect to should be running under your account and not root how about changing the original script to something like...

#!/bin/bash

su yourusername
/usr/bin/tightvncserver

---

### Post by fbarcenas on 2008-03-05
I've read this and I still don't get it..  could you just make a step by step for vncserver and one for tight vnc, that way it's less confusing?

I have vncserver already installed, I just need to know how to make it work on bootup (i.e. without logging in)

Thanks.:KS

preferably with stuff i can just cut an paste unto the command line. Thanks.

---

### Post by shockwaver on 2008-03-05
One option open to you is to use the built in XDMCP (X display management control protocol)  that allows for remote logging in to an x server. Basically, when you connect you'll get your standard login window, and you log in as normally. And it runs as soon as X starts.

To enable XDMCP:
It's fairly easy to set up. If you are using Gnome, you go to System->Administration-Login Window. Click the remote tab, and choose Style: Plain. THIS IS IMPORTANT. THERE IS A BUG WITH GNOME THAT WILL REFUSE CONNECTIONS IF THIS IS NOT PLAIN - At least that is what I found when I was researching it.

You didn't mention how you wanted to log in to this server though, so there are a couple of options, if you are going to log in from windows check out this:
[http://geekravings.blogspot.com/2008/02/howto-xdmcp-with-windows-xp.html]("http://geekravings.blogspot.com/2008/02/howto-xdmcp-with-windows-xp.html")

If you are logging in from another linux machine, you have two main ways you can do it:
When you first go to log in (or you use user switching) there is an option (under options) for "Remote Login by XDMCP". Opening that up will show you a list of all the servers on your local network it detected. If yours is there, great, if not you'll need to add the ip of your server to the box, hit add and connect.

Alternatively, you can use the Terminal Server Client:
```
sudo apt-get install tsclient xnest
```
Open that up, enter your server IP, and choose XDMCP as the protocol. If all goes well, a window will pp-up with your login screen.
The advantage to the TSC is that you can set the display size of the window that will come up and be able to use your existing session on your local machine as well as the remote session on your server.

---

### Post by djbon2112 on 2008-07-09
The problem has something to do with HOME not being set when root. I'm trying to fix this myself, but I need to know what "HOME" should point to for the main user.

EDIT: Got it working. Add the following line to /etc/rc.local

```
su --commmand=tightvncserver - <username>
```

---

