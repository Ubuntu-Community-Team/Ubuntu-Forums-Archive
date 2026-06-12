---
title: "problems installing slimserver on Breezy"
date: 2005-10-21
forum: Desktop Environments
---

### Post by aubuti on 2005-10-21
I'm trying to install the slimserver software for the first time on Breezy, mostly to try it out (using their Java client) before shelling out the money for a squeezebox2. Here's what I've done:

1. download the tarball from [http://www.slimdevices.com/su_downloads.html](http://www.slimdevices.com/su_downloads.html)
2. unpack the files, figure out that I don't want to do it all manually
3. download the rpm from the same source as (1)
4. convert .rpm to .deb via
   fakeroot alien -d --fixperms slimserver-6.1.1-1.noarch.rpm 
   sudo alien -i slimserver_6.1.1-2_all.deb
That seemed to put things where they were supposed to go.
5. tried to run server via
   sudo /usr/local/slimserver/slimserver.pl --daemon --audiodir /media/hdb5/music

and got the error message:
The following messages failed to load: DBD::SQLite XML::Parser HTML::Parser Compress::Zlib

To download and compile them, please run: /usr/local/slimserver/Bin/build-perl-modules.pl

6. When I do that, I get a slew of errors, which I won't reproduce here, but along the lines of:

/usr/lib/perl/5.8/CORE/reentr.h:71:20: error: pwd.h No such file or directory
...
/usr/lib/perl/5.8/CORE/reentr.h:771: error: syntax error before âint32_tâ
...

[I'll post the whole thing if that will help.]

I have gcc, make, and perl.

Any ideas? I'm perfectly willing to go back to square one if need be.

Thanks in advance.

-Ken

---

### Post by matthewn on 2005-10-21
Looks to me like you're missing perl-related packages that slimserver is depending on. I had to deal with similar issues when I first installed slimserver on my own Ubuntu box. (Caveat: I'm still on hoary.) You can probably concentrate on this part of the error: "The following messages failed to load: DBD::SQLite XML::Parser HTML::Parser Compress::Zlib"

A few 'apt-cache search' commands turn up the following packages that you might try installing via 'sudo apt-get install' or Synaptic:

libdbd-sqlite3-perl
libxml-parser-perl
libhtml-parser-perl
libcompress-zlib-perl

Also: I have found it easier to download the .tar.gz slimserver packages rather than the rpm. Untar it to /usr/local/slimserver, and then create the following as /etc/init.d/slimserver:

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

Now you can '/etc/init.d/slimserver start' and such to control the slimserver service.

I hope this helps.

---

### Post by aubuti on 2005-10-21
Thanks for the response. I'm not there yet, but think I'm getting closer. Now when I try to launch the slimserver on the command line I get the following error message:

Had to create DBI::_dbistate unexpectedly at /usr/lib/perl/5.8/DynaLoader.pm line 245.
Segmentation fault

What next? Sorry for having to be led through this, but I haven't spent much time with Linux yet. Thanks.

---

### Post by matthewn on 2005-10-21
Hmm. Unsure. That's a different sort of error; I'm uncertain whether it is cropping up due to a missing package. Do you have libdbi-perl installed?

---

### Post by aubuti on 2005-10-21
Yes, libdbi-perl is installed.

---

### Post by matthewn on 2005-10-21
Sorry to say, I'm not sure how to help at this point. :(

---

### Post by aubuti on 2005-10-21
Well, thanks for getting me closer.  I hope it's just another step or two.

FYI, I tried scrapping what I had installed from the .deb (converted from .rpm) and inserted the contents from the tarball, but same outcome.

Thanks again.

---

### Post by aubuti on 2005-10-21
I should be more careful about writing these things down (or increase the scroll buffer in my terminal....) so that I can leave a trail for others, but it's working now. Based on something I saw in another thread I installed libexpat1-dev, and then re-ran /usr/local/slimserver/Bin/build-perl-modules.pl. 

Got quite a few warnings, mostly about pointer targets differing in signedness, plus some about needing the AppConfig module, but in the end it worked. And now I can see why it gets good reviews, even before getting the SqueezeBox2 itself.

Thanks again for your help.

---

### Post by matthewn on 2005-10-22
OK, upgraded to breezy and ended up with the same error as you. The libdbd-sqlite packages in breezy just don't play nice with Slimserver.

To fix:

# sudo apt-get remove libdbd-sqlite3-perl
# sudo /usr/local/slimserver/Bin/build-perl-modules.pl

---

### Post by robmoore on 2005-10-22
I was never able to get the build-perl-modules.pl script to work, but I was able to get slimserver to run by executing mv CPAN/DBI.pm CPAN/DBI.pm.old. FWIW, there's some details on this at [http://forums.slimdevices.com/showthread.php?t=14748](http://forums.slimdevices.com/showthread.php?t=14748).

---

### Post by mlmurray on 2005-10-22
[QUOTE=aubuti]Thanks for the response. I'm not there yet, but think I'm getting closer. Now when I try to launch the slimserver on the command line I get the following error message:

Had to create DBI::_dbistate unexpectedly at /usr/lib/perl/5.8/DynaLoader.pm line 245.
Segmentation fault

What next? Sorry for having to be led through this, but I haven't spent much time with Linux yet. Thanks.[/QUOTE]

I had the exact same problem.  Just go to the CPAN directory under the Slimserver directory and do the following:  ```
mv DBI.pm DBI.pm.old
```.
I think Breezy's version of perl (5.8.7) conflicts somehow.  Anyway, this worked for me.

Good luck.

---

### Post by freelsjd on 2006-03-04
There is now a sources.list entry for slimserver (still not official) here


# slimserver
#
deb [http://debian.slimdevices.com](http://debian.slimdevices.com) stable main


Then you just enter

sudo apt-get update
sudo apt-get install slimserver

all the dependencies are also installed.

---

### Post by wookieman on 2006-05-07
[QUOTE=mlmurray]I had the exact same problem.  Just go to the CPAN directory under the Slimserver directory and do the following:  ```
mv DBI.pm DBI.pm.old
```.[/QUOTE]

Doesn't work for me :-(

[QUOTE=freelsjd]```
# slimserver
#
deb http://debian.slimdevices.com stable main


Then you just enter

sudo apt-get update
sudo apt-get install slimserver
```[/QUOTE]

Doesn't work for me :-(

[QUOTE=matthewn]The libdbd-sqlite packages in breezy just don't play nice with Slimserver.
```

To fix:

# sudo apt-get remove libdbd-sqlite3-perl
# sudo /usr/local/slimserver/Bin/build-perl-modules.pl
```[/QUOTE]

Doesn't work for me :-( I get the following error...
```

Can't exec "make": No such file or directory at /usr/local/slimserver/SlimServer_v6.2.2/Bin/build-perl-modules.pl line 208, <STDIN> line 3.
Can't stat blib: No such file or directory
 at /usr/local/slimserver/SlimServer_v6.2.2/Bin/build-perl-modules.pl line 281
Couldn't find a valid dynamic library for Compress-Zlib-1.33.tar.gz - something is wrong. Exiting!

```

Any ideas ? Anyone ?

---

