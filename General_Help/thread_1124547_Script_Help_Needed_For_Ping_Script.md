---
title: "Script Help Needed For Ping Script"
date: 2009-04-13
forum: General Help
---

### Post by gbxfan on 2009-04-13
I have a ping script I use on an old Open Step box (I guess its closely related to Mac OS X) and it runs fine, but now I build a system as a backup with Ubuntu 8.10 client and the script needs to be adapted a bit. Can anyone see where how this needs to be done? The script starts and assigns the variables, but chokes on the ping portion of it which I think is syntax related

There are a few places where the end of the line is missing due to my copy and paste, but the main ping part that's broke is all there. I am hoping there is a substitution or something obvious I need to make throughout the script that will make it work again. Thanks!

Script
#!/bin/sh
# establish the data directory
# function to ping the server.  
# if the server doesn't respond, find out if it is because the network
# leading to it is down.
# optionally specify the number of pings to send.  default is 1.
# if more than one ping is sent, a response to any of the packets is
# considered up.  down is only 100% packet loss.
sping()
{
  NAME=$1
  IP=$2
  ROUTER=$3
  if [ -n "$4" ]; then 
    COUNT=$4
  else
    COUNT=1
  fi
  if ping $IP 56 $COUNT | grep -s "100% packet loss"; then
    if ping $ROUTER 56 $COUNT | grep -s "100% packet loss"; then
      echo "$NAME $IP $ROUTER (down because route to it is down)"
      echo "$NAME $IP $ROUTER (down because route to it is down)" 1>&2
    else
      echo "$NAME $IP $ROUTER (down although route to it is up)"
      echo "$NAME $IP $ROUTER (down although route to it is up)" 1>&2
    fi
  else
    echo "$NAME $IP $ROUTER (up)"
    echo "$NAME $IP $ROUTER (up)" 1>&2
  fi
}

# function to send the email notification with high or low importance
notify()
{
  echo "\n\nThis message sent by cron script /admin/scripts/crons/ping_servers.n
  echo "Subject: RCP server stats\nImportance: $1 \n\n" | cat - /tmp/$SCRIPTNAMm
  cat /tmp/$SCRIPTNAME.serverlist.upagain /tmp/$SCRIPTNAME.serverlist.wentdown r
}

# make a list of servers that were down last time this script was run
touch /admin/scripts/crons/$SCRIPTNAME.serverlist.down  /admin/scripts/crons/$Sn
cp  /admin/scripts/crons/$SCRIPTNAME.serverlist.down  /admin/scripts/crons/$SCRn

# ping all the servers and accumulate a retry list
echo pinging all the servers and accumulating a retry list
>/tmp/$SCRIPTNAME.serverlist.retry
while read NAME IP ROUTER
do
  sping $NAME $IP $ROUTER | grep "(down" >>/tmp/$SCRIPTNAME.serverlist.retry
done</tmp/$SCRIPTNAME.serverlist


# wait before retrying the down servers
if [ -s /tmp/$SCRIPTNAME.serverlist.retry ]; then
  echo waiting before retrying the down servers
  sleep 10
else
  echo no servers down
  exit
fi

# ping all the down servers with more packets to make sure they are down
echo retrying down servers with more packets
> /admin/scripts/crons/$SCRIPTNAME.serverlist.down
while read NAME IP ROUTER OTHER
do
  sping $NAME $IP $ROUTER 5 | grep "(down" >> /admin/scripts/crons/$SCRIPTNAME.n
done</tmp/$SCRIPTNAME.serverlist.retry

# look for differences
# in this section, we are looking for what servers just went down,
#  which ones just came back up, and which ones are still down from before
echo lists of recent downs and returns, and servers that remain down 
>/tmp/$SCRIPTNAME.serverlist.wentdown
>/tmp/$SCRIPTNAME.serverlist.stilldown
>/tmp/$SCRIPTNAME.serverlist.upagain
while read NAME IP ROUTER
do
  WASDOWN=`grep -w $NAME  /admin/scripts/crons/$SCRIPTNAME.serverlist.downlastr`
  ISDOWN=`grep -w $NAME  /admin/scripts/crons/$SCRIPTNAME.serverlist.down`
  if [ -n "$WASDOWN" -a -n "$ISDOWN" ]; then
    echo "$ISDOWN (still down)" >>/tmp/$SCRIPTNAME.serverlist.stilldown
  fi
  if [ -n "$WASDOWN" -a -z "$ISDOWN" ]; then
    echo "$NAME $IP $ROUTER (up again)" >>/tmp/$SCRIPTNAME.serverlist.upagain
  fi
  if [ -z "$WASDOWN" -a -n "$ISDOWN" ]; then
    echo "$ISDOWN (just went down)" >>/tmp/$SCRIPTNAME.serverlist.wentdown
  fi
done</tmp/$SCRIPTNAME.serverlist
# cat /tmp/$SCRIPTNAME.serverlist.upagain /tmp/$SCRIPTNAME.serverlist.wentdown n

# if there are servers that just went down or came back up, notify
#  with high importance
if [ -s /tmp/$SCRIPTNAME.serverlist.upagain -o -s /tmp/$SCRIPTNAME.serverlist.wn
  echo notifying of servers that are up again or just now down
  notify high
# if there is no new news, but servers are still down from before,
#  notify only once per day, with low importance
elif [ -s /tmp/$SCRIPTNAME.serverlist.stilldown ]; then
  if [ "`date | awk '{print $4}' | awk -F: '{print $1}'`" -eq 11 ]; then
    if [ ! -f /tmp/$SCRIPTNAME.stilldownsent ]; then
      touch /tmp/$SCRIPTNAME.stilldownsent
      echo notifying once today of servers that are still down from before
      notify low
    fi
  else
    echo not time for daily notification of servers that are still down
    if [ -f /tmp/$SCRIPTNAME.stilldownsent ]; then 
      rm /tmp/$SCRIPTNAME.stilldownsent
    fi
  fi
else
  echo no notification to make
fi

---

### Post by defaultusername on 2009-04-13
gbxfan,

Linux-flavored ping requires the -c switch to specify $COUNT.

---

