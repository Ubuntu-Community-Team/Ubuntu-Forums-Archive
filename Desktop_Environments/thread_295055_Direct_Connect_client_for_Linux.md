---
title: "Direct Connect client for Linux?"
date: 2006-11-07
forum: Desktop Environments
---

### Post by Freddy on 2006-11-07
Is there any good DC clients for Linux out there, I've tried both Valknut and DCgui but had some hazzles against the new modern dc++ clients out there. 

I thought of installing the console based LDCC but saw that the latest update of that was in mid 2004 so I don't know if that one will work against dc++ either.

A couple of months back, I tried out the Linux DC++ beta, but it was way to early to use at a daily bases, how is it now? Atleast I saw that it was updated at a regual basis so maybe it has improved since my last try.

So my question is. 
How is LDCC against modern clients, useable?
How is todays version of Linuc DC++, useable ?

Thanks for any help.   /// Freddan

---

### Post by jazzgossen on 2006-11-07
I don't think Linux DC++ has improved much in the last few months, but I have been using it all year long, and I like it (except for the fact that you can't do multi-user downloads). I say try it again.

---

### Post by Freddy on 2006-11-07
Okey thanks I'll try that client again cause I don't use DC for any downloading so I have no worries there :-). 

I really would like a opinion on LDCC to or any other console based direct connect client, I need to know if they are up to speed with the more modern clients used in XP.

Thanks again for your answer.   /// Freddan

---

### Post by Freddy on 2006-11-08
A shameless bump :-).

---

### Post by ububaba on 2007-01-03
> **Freddy said:**
> A shameless bump :-).

I have used DC++ in Windows earlier. I have done everything "right" as earlier but Linux DC++ 
would not start downloading. Apparently I don't get connected. Any idea about this failure?:???:

---

### Post by detectiveinspekta on 2007-04-22
I just tested dcgui at a lan. Nothing really works. Its all show really.

Use valknut.

---

### Post by Dominus Suus on 2007-04-25
Valknut doesn't seem to work at all on my machine (and might actually be messing up my internet connection).  I'd check the developer's website for documentation but the site doesn't exist.  If Valknut is working on your machine, could you explain how, please?

---

### Post by Jaxilian on 2007-04-25
Info taken from Ubuntu guide at [http://ubuntuguide.org](http://ubuntuguide.org)

How to install File share utility (LinuxDC++) 
```

wget -c http://easylinux.info/uploads/linuxdcpp.tar.gz
sudo tar zxvf linuxdcpp.tar.gz -C /opt
gksudo gedit /usr/share/applications/linuxdcpp.desktop

```

Insert the following lines into the new file 
```

[Desktop Entry]
Encoding=UTF-8
Name=LinuxDC++
Exec=linuxdcpp
Terminal=false
Type=Application
StartupNotify=true
Icon=/opt/linuxdcpp/pixmaps/linuxdcpp.png
Categories=Application;Network;

```
Save the edited file 

You'll find the application under:
Applications -> Internet -> LinuxDC++

P.S! This was for Edgy, but will probably work under Feisty as well.

---

### Post by stokedfish on 2007-04-25
I never had any problems with linuxdcpp. It works like a ******* charme.

Compile, configure your shares, set up your dyndns with ddclient, forward the ports, done!        :)

---

### Post by Jaxilian on 2007-04-25
> **flodis said:**
> Info taken from Ubuntu guide at [http://ubuntuguide.org](http://ubuntuguide.org)

How to install File share utility (LinuxDC++) 
```

wget -c http://easylinux.info/uploads/linuxdcpp.tar.gz
sudo tar zxvf linuxdcpp.tar.gz -C /opt
gksudo gedit /usr/share/applications/linuxdcpp.desktop

```

Insert the following lines into the new file 
```

[Desktop Entry]
Encoding=UTF-8
Name=LinuxDC++
Exec=linuxdcpp
Terminal=false
Type=Application
StartupNotify=true
Icon=/opt/linuxdcpp/pixmaps/linuxdcpp.png
Categories=Application;Network;

```
Save the edited file 

You'll find the application under:
Applications -> Internet -> LinuxDC++

P.S! This was for Edgy, but will probably work under Feisty as well.

I tried this on my own computer now that I have 7.04 and it doesnt work. I know it worked in ubuntu 6.10. 
I get error> Could not launch menu item. failed to execute child process linuxdcpp, no such file or directory

any know what is wrong?It starts if I doubeclick on the file directly /opt/linuxdcpp/linuxdcpp, but not through the shortcut

---

### Post by Dominus Suus on 2007-04-26
Our friends over at Debain have compiled a linuxdcpp.deb file at [http://packages.debian.org/unstable/net/linuxdcpp](http://packages.debian.org/unstable/net/linuxdcpp) .  It installed without incident on my Kubuntu Fiesty.  Perhaps someone at MOTU would like to add it to our repositories?

---

### Post by Jaxilian on 2007-04-26
ok why can't i start my application?

My /usr/share/applications/linuxdcpp.desktop looks like this:

```

[Desktop Entry]
Encoding=UTF-8
Name=LinuxDC++
Comment=Direct Connect Client
Exec=linuxdcpp
Path=/opt/linuxdcpp/
Terminal=false
Type=Application
StartupNotify=true
Icon=/opt/linuxdcpp/pixmaps/linuxdcpp.png
Categories=Application;Network;

```

I get error:
```

There was an error launching the application.
details: Failed to execute child process
"linuxdcpp"(no such file or directory)

```

If I go to the path where it is I find it and I can start it by doubleclicking on it......weird!!

---

### Post by Jaxilian on 2007-04-26
SOLVED

needed to change this:
```

Exec=linuxdcpp
Path=/opt/linuxdcpp/

```

to:
```

Exec=/opt/linuxdcpp/linuxdcpp
Path=/opt/linuxdcpp/

```

---

### Post by Xappe on 2007-04-26
Steven Sheehy, one of the main developers of linuxdc++, has actually created a nice howto here on the forums on how to install linuxdc++ from CVS. I would recommend that way of installing the program, since it is very easy to keep it up to date...

[http://ubuntuforums.org/showthread.php?t=193984&highlight=steven+sheehy]("http://ubuntuforums.org/showthread.php?t=193984&highlight=steven+sheehy")

---

### Post by s_spiff on 2007-05-03
thanks for this howto, some of please msg kliz on the x64 on adding this to the list of howto's works great!

---

### Post by ChiaJesus on 2007-05-03
I use DC++ under Wine. Works fabulously.

---

### Post by kosson on 2008-05-06
I use StrongDC++ 2.12 under Wine and it seems to me that is faster than windows environment.
Works like a charm

---

