---
title: "Can't install Slimserver. Help."
date: 2006-07-08
forum: Desktop Environments
---

### Post by Panik on 2006-07-08
I have been having a hell of a time trying to install slimserver.  I used the slimserver repository "deb [http://debian.slimdevices.com/](http://debian.slimdevices.com/) stable main", and although it runs, it is so buggy that I can't stand it.  They do not have a Stable repository yet.

So I decided to try and install the stable version at [www.slimdevices.com](www.slimdevices.com) following the below steps from this thread ([http://www.ubuntuforums.org/showthread.php?t=80047&highlight=slimserver)](http://www.ubuntuforums.org/showthread.php?t=80047&highlight=slimserver)).

Steps I followed (I'm a newb, please help if you can):

1) download Perl Source Code (tar.gz) from [http://www.slimdevices.com/su_downloads.html](http://www.slimdevices.com/su_downloads.html)

2) untar to /usr/local/slimserver

3) Created the following /etc/init.d/slimserver

#######################################
#!/bin/sh
# slimserver init script for Debian Linux

DAEMON=/usr/local/slimserver/slimserver.pl
PIDFILE=/tmp/slimserver.pid
LOGFILE=/tmp/slimserver.log
USER=root
SLIMSERVER_OPTS=""

test -x ${DAEMON} || exit 0

case "$1" in
start) echo -n "Starting Slimserver: "
HOME=/home/$USER
start-stop-daemon --start --quiet --exec $DAEMON \
--chuid ${USER} -- --daemon --diag \
--prefsfile=/etc/slimserver.conf --pidfile=${PIDFILE} \
--logfile=${LOGFILE} ${SLIMSERVER_OPTS}
echo "done"
;;

stop) echo -n "Stopping Slimserver: "
start-stop-daemon --stop --quiet --user ${USER} --pidfile ${PIDFILE} --retry 5
echo "done"
;;

force-reload|restart) $0 stop
$0 start
;;

*) echo "Usage: $0 {start|stop|restart|force-reload}"
exit 1;
;;

esac

exit 0
#######################################

4) sudo /usr/local/slimserver/Bin/build-perl-modules.pl

5) Tried to start slimserver vie "sudo /etc/init.d/slimserver start" and received the following:

Starting Slimserver: Can't locate Slim/Utils/Misc.pm in @INC (@INC contains: /usr/local/slimserver/CPAN/arch/5.8.7/i486-linux-gnu-thread-multi /usr/local/slimserver/CPAN/arch/5.8.7/i486-linux-gnu-thread-multi/auto /usr/local/slimserver/CPAN/arch/5.8/i486-linux-gnu-thread-multi /usr/local/slimserver/CPAN/arch/5.8/i486-linux-gnu-thread-multi/auto /usr/local/slimserver/CPAN/arch/i486-linux-gnu-thread-multi /usr/local/slimserver/lib /usr/local/slimserver/CPAN /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/local/slimserver/slimserver.pl line 265.
BEGIN failed--compilation aborted at /usr/local/slimserver/slimserver.pl line 265.
done


I am at an absolute loss.  I wish it was just a little easier for a newb.  PLEASE HELP!

---

### Post by Panik on 2006-07-08
Bump.  HELP!  Need it for a party.

---

### Post by andyman on 2006-07-09
Sorry I cant be much help, but have you tried the linux section on the slimdevices.com forum?  they're pretty helpful there.

---

### Post by Panik on 2006-07-09
Thanks, I have tried there.  They helped me get it running (although I am still having trouble with the start up script).  The trick was to use the latest nightly build 6.3.1.  I guess it solved some of the bugs that I was running into with dapper.  I am not running the 6.5bl on the repository.  I downloaded the tar from the beta/pre release section.

---

