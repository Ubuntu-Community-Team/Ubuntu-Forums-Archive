---
title: "(REQ) Un-Serv'd"
date: 2006-04-03
forum: Desktop Environments
---

### Post by andril on 2006-04-03
Hello all, I am desperate need of help replacing my Win OS (s) and completely going with Ubuntu. But I need to Serv - I am currently running the following apps:

DNS2GO (dns server)
Merak Email Server
G6FTP Server
Xeneo Web Server

and I am tired of the Win viruses and headaches.](*,)  I just want to sit back and sip the Ubuntu with you all. Can some one provide the app counterparts and walkthroughs for the linux versions (FTP,MAIL,DNS & HTTP)? I would greatly appreciate any type of help with this task. I am looking very forward to hearing from you guys/gals on this. Thanks In Advance.

---

### Post by frio on 2006-05-09
I just got dns2go working on my Ubuntu server that WAS windows... I'm pretty proud of it since I'm a relative noobe to Linux... Anyway, here goes.

I thought it was going to be pretty straight forward since you can download Linux packages from the Deerfield site... [http://www.deerfield.com/download/dns2go/linux/index.htm]("http://www.deerfield.com/download/dns2go/linux/index.htm")

I tried using INSTALL.sh as described in their installation help section. It did not work so I decided to place the files on the system manually using the INSTALL.sh script as a go by as to where they should go. I didn't follow it exactly since some of the locations do not seem to follow Ubuntu convention.

That all went ok until I tried to run it as a DAEMON in the background. It would hang the system during boot until CTRL-C was pressed. Per their directions, it seems that the compiled binary does not run in the background. After some fiddling (and a lot of reading) I was able to get it to work just as other system services do.

What I did was to look over some other working scripts in /etc/init.d and then copy one that seemed simple enough to modify. This is what I came up with, and it actually worked.

FILE: /etc/init.d/dns2go
```
#
!/bin/sh
#
# Start/stops the dns2go daemon.
# Frio
# 09May06

DAEMON=/usr/bin/dns2go

RUN_MODE="daemons"

. /lib/lsb/init-functions

# See if the daemon is there
test -x $DAEMON || exit 0

case "$1" in
    start)
               log_begin_msg "Starting the DNS2GO daemon..."

               start-stop-daemon --start --background --oknodo --exec $DAEMON -- run

               log_end_msg $?
        ;;

    stop)
               log_begin_msg "Stopping the DNS2GO daemon..."

               start-stop-daemon --stop --oknodo --exec $DAEMON

               log_end_msg $?
        ;;

    restart|force-reload)
               log_begin_msg "Restarting the DNS2GO daemon..."

               start-stop-daemon --stop --oknodo --exec $DAEMON
               sleep 2
               start-stop-daemon --start --background --oknodo --exec $DAEMON -- run

               log_end_msg $?
        ;;
    *)
               log_success_msg "Usage: /etc/init.d/dns2go {start|stop|restart|force-reload}"
        exit 1
        ;;
esac

exit 0


``` 
You'll want to change DAEMON=/usr/bin/dns2go if you located the bin in the location specified by the instllation instructions (/usr/local/bin). Also, don't forget to create a "link to shell script" in /etc/rcS.d/ that points to /etc/init.d/dns2go. I named mine S71dns2go to make sure it starts up after all the networking stuff does. Also, make sure to set logging in the /etc/dns2go.conf file to a file on your system (I used /var/log/dns2go/dns2go.log) since there will not be anywhere to view the output. I'm not sure what would happen if a log file was not specified.

Hope this helps...

---

### Post by andylev on 2006-05-14
I am new to all this and would appreciate some help, Which of the deerfield downloads do i use? Which platform will work?
Thanks

---

### Post by frio on 2006-05-14
The one I used was the [Debian 2.2 tarball]("http://www.deerfield.com/download/dns2go/linux/thanks.htm?dlid=28&profileid=8&productid=103&url=http://ftp1.deerfield.com/pub/dns2go/linux/dns2go-2.0.tar.gz&bp=0")

When the INSTALL.sh script didn't work, I looked at all the others and as best I could tell, there was no difference.

---

