---
title: "MPrime Daemon start-up script"
date: 2005-12-11
forum: Desktop Environments
---

### Post by Anything Generic on 2005-12-11
I'm absolutely new to Linux and wasn't able to find a way to launch MPrime like Prime95 would start up in Windows.  After I found out that start up and daemon were used synonymously I searched for "mprime daemon" in Google and stumbled across a mailing list archive found here: [http://www.mail-archive.com/mersenne@base.com/msg05245.html](http://www.mail-archive.com/mersenne@base.com/msg05245.html)

Here's the steps I followed to achieve this:

1) Download and extract mprime2414.tar.gz (or whatever the latest version is) from [www.mersenne.org](www.mersenne.org) to /opt/mprime/

2) Change to this directory and run the ./mprime -m from xterm to set up the preferences.

3) Now we will want to create a script to have MPrime run in the background at start up.

> sudo gedit /etc/init.d/mprime.sh

In here, we will paste Gareth Randall's code:

> **** Start of mprime.sh ****


#!/bin/sh
#
# mprime.sh     Script to manage "mprime" prime factoring program.
#
# Version:      1.1     11-Nov-2000     Gareth Randall
#

PRIME_BIN_FILE=/home/gareth/mprime/mprime
PRIME_LOG_FILE=/home/gareth/mprime/log/mprime.log
DESC="prime factoring program"
NAME=mprime

if !(test -f $PRIME_BIN_FILE) ; then
   echo "Couldn't find $NAME binary: $PRIME_BIN_FILE" >&2
   exit 1;
fi

case "$1" in
   start)
         if (pidof $PRIME_BIN_FILE > /dev/null ) ; then
            echo "ABORTING: Process with that binary already running!" >&2
            exit 1;
         fi

         echo -n "Starting $DESC: "
         echo -n "START: " >> $PRIME_LOG_FILE
         date >> $PRIME_LOG_FILE

         su gareth -c "$PRIME_BIN_FILE -d >> $PRIME_LOG_FILE &"

         echo "$NAME."
         ;;
   stop)
         echo -n "Stopping $DESC: "

         killall -2 $PRIME_BIN_FILE

         echo -n "STOP : " >> $PRIME_LOG_FILE
         date >> $PRIME_LOG_FILE
         echo "$NAME."
         ;;
   *)
         echo "Usage: $0 {start|stop}" >&2
         exit 1
         ;;
esac

exit 0

**** End of mprime.sh ****


4) Change 
PRIME_BIN_FILE=/home/gareth/mprime/mprime
PRIME_LOG_FILE=/home/gareth/mprime/log/mprime.log

to > 
PRIME_BIN_FILE=/opt/mprime/mprime
PRIME_LOG_FILE=/opt/mprime/prime.log

5) Replace gareth with your own login name.
su gareth -c "$PRIME_BIN_FILE -d >> $PRIME_LOG_FILE &"

> 
su eric -c "$PRIME_BIN_FILE -d >> $PRIME_LOG_FILE &"

6) Save the script

7) We now need to create symlinks to startup directories.  Ubuntu has a built-in program that allows us to do this with ease called update-rc.d

Change to /etc/init.d/ and type:
> sudo update-rc.d mprime.sh defaults

8) Test it out!  Change to /etc/init.d/ and run ./mprime.sh

From xterm, type: ps -A

Is MPrime in the list?? If so, it worked and MPrime will be gobbling up CPU cycles in no time!!  If not, post here and I'll see if I can help you out :)


Thanks to Gareth Randall for allowing me to post his script! :)

---

### Post by Anything Generic on 2005-12-11
Gareth Randell has kindly provided a new edition of his code that includes sleep and logging functionality:

> #!/bin/sh
#
# mprime.sh	Script to manage "mprime" prime factoring program.
#
# Version:	1.2	12-Jan-2003	Gareth Randall
#

PRIME_BIN_FILE=/home/distrib/mprime/mprime
PRIME_LOG_FILE=/home/distrib/mprime/log/mprime.log
DESC="prime factoring program"
NAME=mprime
RUN_AS_USER=distrib


if !(test -f "$PRIME_BIN_FILE") ; then
   echo "Couldn't find $NAME binary: $PRIME_BIN_FILE" >&2
   exit 1;
fi

case "$1" in
   start)
         if (pidof "$PRIME_BIN_FILE" > /dev/null ) ; then
            echo "ABORTING: Process with that binary already running!" >&2
            exit 1;
         fi

         echo -n "Starting $DESC: "
         echo -n "START: " >> "$PRIME_LOG_FILE"
         date >> "$PRIME_LOG_FILE"


#  Explanation of command line below
#  ---------------------------------
#
#  su gareth -c ... &
#  Run the quoted string as user gareth, and drop to background to do it.
#
#  sleep 120;
#  Wait a while before starting the program. This is to allow the CPU time
#  to warm up before the temperature rises further due to floating point
#  activity. The intent is to reduce thermal stress created within the CPU.
#
#  $PRIME_BIN_FILE -d >> $PRIME_LOG_FILE &"
#  Run mprime program with logging option, and do it in background so that
#  the shell which runs sleep and mprime can exit and won't hang around.


         su "$RUN_AS_USER" -c "sleep 120; $PRIME_BIN_FILE -d >> $PRIME_LOG_FILE &" &

         echo "$NAME."
         ;;
   stop)
         echo -n "Stopping $DESC: "

         killall -2 "$PRIME_BIN_FILE"

         echo -n "STOP : " >> "$PRIME_LOG_FILE"
         date >> "$PRIME_LOG_FILE"
         echo "$NAME."
         ;;
   *)
         echo "Usage: $0 {start|stop}" >&2
         exit 1
         ;;
esac

exit 0


---

