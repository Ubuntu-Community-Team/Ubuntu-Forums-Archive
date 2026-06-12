---
title: "Samba error : Unknown parameter encountered: &quot;SO_RCVBUF&quot;"
date: 2005-11-15
forum: Desktop Environments
---

### Post by Cyril on 2005-11-15
I get the following error when trying to mount a network folder :

Unknown parameter encountered: "SO_RCVBUF"
Ignoring unknown parameter "SO_RCVBUF"

I think this is the relevant section from my /etc/samba/smb.conf :

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

Anyone know why I am getting this error?

---

### Post by fuzzyduck on 2008-03-02
I am having the exact same problem.  i'm trying to stop a stutter in video playback that i'm streaming over the samba server and this seemed like the most appropriate place to adjust this buffer.

the strange thing is that this was commented out in the original smb.conf file so all i had to do is uncomment it.  testparm also doesn't like SO_RCVBUF but has no problems with "Socket option - TCP_NODELAY".

any help would be much appreciated.

thanks

---

### Post by stephen67 on 2008-05-17
This setting is not for the samba.conf file.

As near as I can figure, it is a compile option for the kernel. I have a problem with very slow transfers and I am looking at this. But it is a work in progress.

---

### Post by mileek on 2008-07-03
This IS samba parameter.
Just comment out that line and you are good to go.
Your config file should be:
```
# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
# SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY
```

That parametar should improve speed of your samba server and if you want to include it you should add it as optional parameter for socket options like this:
```
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
```

If you want to work on speed try speed.txt file for samba:
[**Speed.txt**]("http://www.wifi.com.ar/english/doc/samba/Speed.txt")

---

