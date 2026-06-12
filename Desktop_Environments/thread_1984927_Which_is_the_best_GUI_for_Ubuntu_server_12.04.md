---
title: "Which is the best GUI for Ubuntu server 12.04"
date: 2012-05-22
forum: Desktop Environments
---

### Post by Pally1 on 2012-05-22
That looks good and has all the functionality?

---

### Post by lykwydchykyn on 2012-05-22
What functionality do you want it to have?

---

### Post by QIII on 2012-05-22
And are you going to administer it remotely using a remote desktop?

---

### Post by Pally1 on 2012-05-22
Its needs to work as a file server and maybe a website server, administration most likely will not be remote.

---

### Post by lykwydchykyn on 2012-05-22
Basically, Ubuntu server is not designed to by managed via GUI.

You can install a desktop, any one you want, doesn't matter.  But you won't get any kind of server configuration GUI whatsoever; it doesn't exist on Ubuntu.

Having said that, there are some options if you don't want to tackle the command line:

 - Samba (which you'd most likely use for file serving) has a web-based GUI called SWAT which you can install

 - There are cpanel-like interfaces for web server administration, some commercial, others not.  I don't have much experience with them, personally.

 - There is Webmin, a web-based configuration system.  I have been told it isn't recommended for Ubuntu anymore because of compatibility issues, but I use it personally and haven't experienced problems.  YMMV.

 - If you want a slick, GUI-driven server system powered by Ubuntu, check out Zentyal.  

 - If you want something with desktop-based server configuration GUIs a-la Windows server, Ubuntu is not your distro.  Check out Suse, RedHat, or ClearOS.

---

### Post by QIII on 2012-05-22
I run an Ubuntu server with a GUI and administer it remotely using NOMACHINE NX because it also runs some distributed scientific applications that have GUI front ends. 

True there is no unified GUI administration tool, but it can be done in pieces.

---

### Post by lykwydchykyn on 2012-05-22
> **QIII said:**
> 
True there is no unified GUI administration tool, but it can be done in pieces.

I don't know of a single example of a desktop-based GUI you can install in Ubuntu to configure a web server.  If you do, please share.

There is gsambad for configuring Samba, but every time I've tried it I ended up with a broken Samba configuration.

---

### Post by QIII on 2012-05-22
You can securely administer your server via remote desktop using  NOMACHINE NX (which is SSH2 compliant, but only 1024 bit keys if you use version 3.5.  4.0 is a beta and I had some disturbing malfunctions with it.), and then set  it up as a Lamp server graphically (in terms of using the remote desktop, if not the tools themselves) using something like these  instructions or others.  One would have to be very careful about security, of  course.  Not something I'd want to do.

NOMACHINE would get you talking to your server graphically as if you were sitting at it.  NOMACHINE has barfed on me with XFCE and GNOME shell.  Works well with KDE and Unity.  You also need to be sure to use something like denyhosts, don't use password logins, lock down iptables, etc.

[]("http://www.howtogeek.com/howto/42480/how-to-turn-your-home-ubuntu-pc-into-a-lamp-web-server/[/URL")[Lamp Server]("http://www.howtogeek.com/howto/42480/how-to-turn-your-home-ubuntu-pc-into-a-lamp-web-server/")
Edit:  Bah!  Sorry.  That had the wrong link.  Fixed now.


Like I said, "in pieces".  And, like I said, the level of effort securing the whole thing is not something I'd be interested in.  I'm paranoid enough just with SSH, which I also use to talk to that machine while I'm on the road.

---

