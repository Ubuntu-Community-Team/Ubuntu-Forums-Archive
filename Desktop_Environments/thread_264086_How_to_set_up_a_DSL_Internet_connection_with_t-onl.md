---
title: "How to set up a DSL Internet connection with t-online and keep it alive"
date: 2006-09-24
forum: Desktop Environments
---

### Post by ulriks on 2006-09-24
I have had a few problems setting up my Internet connection  with my provider t-online. You may think you need a telephone number since you're using a DSL modem, but you don't...

I think I got it sussed now... here's it what I did.

You need:
pppd
pppoeconf
knemo
A directory in your PATH

Configureing the connection:
Open a terminal and
```
sudo pppoeconf
```
It is pretty straight forward and I used all the defaults

Still in the terminal, the connection can now be started with

```
sudo pon dsl-provier
```

and closed with

```
poff
```

To check that the connection really is working, ping google or something else which should be up:

```
ping 66.102.9.99
```

(before you close the connection)

Here is my resulting dsl-provider file from the pppoeconf
```

# Configuration file for PPP, using PPP over Ethernet
# to connect to a DSL provider.
#
# See the manual page pppd(8) for information on all the options.

##
# Section 1
#
# Stuff to configure...

# MUST CHANGE: Uncomment the following line, replacing the user@provider.net
# by the DSL user name given to your by your DSL provider.
# (There should be a matching entry in /etc/ppp/pap-secrets with the password.)

# Use the pppoe program to send the ppp packets over the Ethernet link
# This line should work fine if this computer is the only one accessing
# the Internet through this DSL connection. This is the right line to use
# for most people.
#pty "/usr/sbin/pppoe -I eth0 -T 80 -m 1452"

# An even more conservative version of the previous line, if things
# don't work using -m 1452...
#pty "/usr/sbin/pppoe -I eth0 -T 80 -m 1412"

# If the computer connected to the Internet using pppoe is not being used
# by other computers as a gateway to the Internet, you can try the following
# line instead, for a small gain in speed:
#pty "/usr/sbin/pppoe -I eth0 -T 80"

# The following two options should work fine for most DSL users.

# Assumes that your IP address is allocated dynamically
# by your DSL provider...
noipdefault
# Try to get the name server addresses from the ISP.
usepeerdns
# Use this connection as the default route.
# Comment out if you already have the correct default route installed.
defaultroute

##
# Section 2
#
# Uncomment if your DSL provider charges by minute connected
# and you want to use demand-dialing.
#
# Disconnect after 300 seconds (5 minutes) of idle time.

#demand
#idle 300

##
# Section 3
#
# You shouldn't need to change these options...

#hide-password
lcp-echo-interval 20
lcp-echo-failure 3
# Override any connect script that may have been set in /etc/ppp/options.
connect /bin/true
noauth
persist
mtu 1492

# RFC 2516, paragraph 7 mandates that the following options MUST NOT be
# requested and MUST be rejected if requested by the peer:
# Address-and-Control-Field-Compression (ACFC)
noaccomp
# Asynchronous-Control-Character-Map (ACCM)
default-asyncmap

plugin rp-pppoe.so eth0
user "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx@t-online.de"

```

Starting the connection from the terminal was annoying to me, and this is where Knemo comes in
It needs to be started from K-menu -> System Settings -> Network Monitor

Since I also find that a tad silly (though there are good reasons) I simply left the 'Hide icon then not connected' unchecked. I also removed all other interfaces but the 'ppp0'.

It is possible to add context menus (those menus that pop up on right click) in Knemo, and this feature is what will be used for connecting and disconnection  using Knemo

Here's howto:
Go to 'Configure Knemo...' and select the interface
Check 'Display custom entries in context menu'
Click on add (the small document with a star)
Add appropriate text in the 'Menu text' and 'Command' fields. Being able to write anything is a little bit tricky, and when you're done writing, press enter - otherwise the text is not saved...

If one wants to connect to the Internet an entry could look like:
'Root': Checked
'Menu text': Connect
'Command': pon dsl-provider

By checking 'Root', the command we want to execute is executed as root (and one needs to be root to use pon or poff)

I noticed, that my connection was a bit unstable at times, so I wrote a small script to check for connection.

There are three 'sections' in the script: one to start the connection and set up the cronjob, one to close the connection and remove the cron job, and one to check if the connection is still there (that the interface is up to be precise) and open the connection if it was not closed by the user

The script must be run as root.

This is what my context menu entries in Knemo look like:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=16241&stc=1&d=1159092785[/IMG]

'Root': Checked
'Menu text': Connect
'Command': interconnect start

'Root': Checked
'Menu text': Disconnect
'Command': interconnect stop

And this is the script (I called it interconnect, but you can give it any name you want):
```

#!/bin/sh
# interconnect
# Usage
# To start the internet connection: interconnect start
# To stop the internet connection: interconnect stop
# To check (and react) if the connection is not open: interconnect check
#
# Connects to the internet, and keep the connection alive until the connection is terminated by the user
DATESTAMP=`date`
HOMEDIR="/home/ulriks/"
LOGFILE=$HOMEDIR"interconnect.log"
TMPCHECKFILE="/tmp/internet"
CRONJOB="/etc/cron.d/pppoeinternet"

# Check if the script is being run as root exit if it is not.
if [ "$UID" -ne "0" ]
then
  echo "[ERROR] This script must be run as root"
  exit 1
fi

# Start the connection
if [ "$1" == "start" ]; then
  # Start the pppoe internet connection
  pon dsl-provider
  # Using a cron job to check the connection every 5 minutes
  # The output is appended to the logfile
  # If you feel that every 5 minutes is not often enough, simply remove the '/5' part
  # If you feel every 5 minutes is overkill, replace 5 with whatever number of minutes you
  # think appropriate. Trying to check more than once a minute will not work, as the cron
  # daemon is only invoked every minute
  echo "*/5 * * * * root /home/ulriks/bin/interconnect check >> $LOGFILE"  > "$CRONJOB"
  echo "$DATESTAMP - New connection started :-D" >> "$LOGFILE"
  # Restarting cron should not be needed, but if it makes you happy,
  # just uncomment the following line
  #/etc/init.d/cron restart
fi

# Close the connection
if [ "$1" == "stop" ]; then
  # Remove the cron job. If we didn't, the connection would be restarted in 5 minutes
  rm "$CRONJOB"
  # Restarting cron should not be needed, but if it makes you happy,
  # just uncomment the following line
  #/etc/init.d/cron restart
  # End all pppoe internet connections - this is in case we start more then one interface
  poff -a
  echo "$DATESTAMP - Interface brought down by user"  >> "$LOGFILE"
  echo "-------------------------------------------"  >> "$LOGFILE"
fi

# Check to see if the connection is still open
# if it is open, we do nothing. Otherwise we make a note of it and reconnect
if [ "$1" == "check" ]; then
  # Reset the PPPOE var
  PPPOE=""
  # Execute the ifconfig command, get the line containing 'ppp' and extract the first
  # part of it (the interface, usually 'ppp0'
  PPPOE=$( /sbin/ifconfig -a | grep 'ppp' | awk '{print $1}' )

  if [ -n "$PPPOE" ]; then
    # The $PPPOE var is not empty, which means the interface is up
    echo -n ""
    # For debugging purposes
    #echo "$DATESTAMP - Status: Interface still up ($PPPOE)"
  else
    # The $PPPOE var is empty. The interface is down
    # Lets make a note of that and try to bring it up
    echo "$DATESTAMP - Status: Interface down, attempting to bring it up again ($PPPOE)"
    #poff
    pon dsl-provider
  fi
  # Set the owner of the log file, to the user
  chown ulriks.ulriks $LOGFILE
fi

```

To use the script, simply paste it into a plain text file using your favourite text editor such as kate, and save it in a directory which is in your PATH, and make it executable by
```
chmod +x [filename]
```

There is of course no guarantee that I haven't done something silly. Also, I am far from being a master of bash, so there may be better ways to keep the connection alive.

---

