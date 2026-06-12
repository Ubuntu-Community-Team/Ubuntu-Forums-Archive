---
title: "pptp vpn"
date: 2005-10-13
forum: Desktop Environments
---

### Post by kiddyfurby on 2005-10-13
I've been using pptpconfig to setup my vpn connection in Hoary

Now that I've formated my computer and fed it with Breezy,
I have to use another computer to download the debs

Can anyone suggest what debs do I need?

I have pptpconfig,  php-gtk-pcntl,  php-pcntl
but I ran into dependency hell

---

### Post by joakim2 on 2005-10-13
[http://pptpclient.sourceforge.net/howto-debian.phtml](http://pptpclient.sourceforge.net/howto-debian.phtml)

You can ignore the part about "Installing MPPE Support", the rest works flawlessly.

---

### Post by rApJtR on 2005-10-14
You can get your vpn run without pptpconfig.
Just like this 
/etc/init.d/connetc:
```

#!/bin/sh
#

PATH=/bin:/usr/bin:/sbin:/usr/sbin
# Configurations
#

case "$1" in
    start)
        echo -n "Starting pptp"
        if ifconfig|grep ppp &>/dev/null
            then
            echo "[already running]"
        else
            pptp vpn.resnet.cuhk.edu.hk debug name YOUR_USERNAME remotename vpn.resnet.cuhk.edu.hk noipdefault
            echo "."
        fi
        ;;
    stop)
        echo -n "Stopping pptp"
        if ifconfig|grep ppp &>/dev/null
            then
            killall -9 pptp
            echo "."
        else
            echo "[not running]";
        fi
        ;;
    force-reload|restart)
        $0 stop
        $0 start
        ;;
    *)
        echo "Usage: /etc/init.d/connect {start|stop|restart|force-reload}"
        exit 1
esac

exit 0


```


/etc/ppp/options
```

lock
debug
mtu 1000
nobsdcomp
nodeflate
noaccomp
nopcomp
novj
defaultroute
name USERNAME

```
/etc/ppp/pap-secrets, append
```

USERNAME vpn.classnet.cuhk.edu.hk PASSWORD

```

---

### Post by PeaceMessenger on 2005-10-14
I'm trying to get pptpconfig according to
> joakim2
[http://pptpclient.sourceforge.net/howto-debian.phtml](http://pptpclient.sourceforge.net/howto-debian.phtml)
You can ignore the part about "Installing MPPE Support", the rest works flawlessly.

I'm using Synaptic Package manager to get the update.  I added deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./ to my list of repositories.  Then when I get updates or try to install pptpconfig I get a message from Synaptic saying
"Warning! You are about to install software that cannot be authenticated.  Doing this could allow a malicious individual to take control of your system."    

Since that didn't sound good I stopped.  But I do need an easy way to configure a vpn.  Is the warning as dangerous as it sounds or should I ignore the warning?

Also, Is MPPE already in Breezy's kernel?  Joakim said to ignore that part of the instructions, but I need to make sure my vpn is encrpted.  Thanks for helping.

---

### Post by joakim2 on 2005-10-14
Yes, mppe is already included in Breezy. And yes, you can ignore the warning about the unauthenticated packages.

---

### Post by kiddyfurby on 2005-10-14
I've got pptpconfig working by installing those packages with dependencies found on the respos (i went to a hot spot)
however, I m still receiving error message

Looks like a configuration problem to me this time

---

### Post by Vishaakje on 2005-10-15
I'm also trying to set up a VPN connection. I'm using the debian guide. 

```
root@xxxxx# apt-get install pptpconfig
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pptpconfig: Depends: php-pcntl (>= 4.3.7) but it is not installable
              Depends: php-gtk-pcntl (>= 1.0.0) but it is not installable
E: Broken packages

```

Can anybody help me out here?

---

### Post by kiddyfurby on 2005-10-15
you can get the the debs from [http://quozl.us.netrek.org/pptp/pptpconfig/](http://quozl.us.netrek.org/pptp/pptpconfig/)
use dpkg -i *.deb

but you will also need some more stuffs from the respos
libglade...

---

### Post by Vishaakje on 2005-10-17
doesn't seem there's a AMD64 package out there :( 
```

dpkg: error processing php-gtk-pcntl_1-1.0.0-2_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing php-pcntl_4.3.8-2_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 php-gtk-pcntl_1-1.0.0-2_i386.deb
 php-pcntl_4.3.8-2_i386.deb

```

---

### Post by elamericano on 2006-03-28
Thanks rApJtR,

I was trying to get this running without pptpconfig so I could link it to an launch icon in Gnome without getting two gui windows to close.

Your method worked for me, except I had to add another line to pap-secrets:
REMOTENAME USERNAME PASSWORD *

I still have your line too, because that's the way pptpconfig enters it - but pptpd complain about the password if I don't reverse it.

If someone knows a clear presentation of manual VPN setup, I'd sure appreciate a link to it.

Thanks all,

EA

---

