---
title: "iptables firewall question"
date: 2006-01-30
forum: Desktop Environments
---

### Post by SHOWE on 2006-01-30
Hello,

I have just changed distro from fedora.
I decided to use a firewall script to keep the bad guys out as that's what I did in fedora.
Anyway, I was using the following script:-
#!/bin/sh
#
# Author: Martti Kuparinen <martti.kuparinen@iki.fi>
#
# $Id: firewall,v 1.3 2005/11/25 09:50:43 martti Exp $
#

if [ -r /lib/lsb/init-functions ]; then
    . /lib/lsb/init-functions
fi

firewall_start()
{
#---------------------------------------------------------------
# Initialize all the chains by removing all the rules
# tied to them
#---------------------------------------------------------------
    iptables --flush

#---------------------------------------------------------------
# If a packet doesn't match one of the chain rules, then
# The policy should be to drop it
#---------------------------------------------------------------
#iptables --policy INPUT DROP
#iptables --policy OUTPUT DROP
#iptables --policy FORWARD DROP
# Create chain which blocks new connections, except if coming from inside.
#create new table block
        iptables -N block
#append a rule to block that accepts packets that are from exchanges already in existance
        iptables -A block -m state --state ESTABLISHED,RELATED -j ACCEPT
#append a rule to block that first logs then accepts packets
#from eth1 with tcp protocol directed to ports 22 and 8080
        iptables -A block -p tcp -i eth1 --dport 22 --sport 1024:65535 -j LOG --log-prefix "ssh connect:"
        iptables -A block -p tcp -i eth1 --dport 22 --sport 1024:65535 -j ACCEPT
iptables -A block -p tcp -i eth1 --dport 8080 --sport 1024:65535 -j LOG --log-prefix "web connect:"
        iptables -A block -p tcp -i eth1 --dport 8080 --sport 1024:65535 -j ACCEPT
    # Allow everything on the loopback network
    iptables -A block -i lo -j ACCEPT

    # Allow incoming ICMP echo request and errors
    iptables -A block --protocol icmp --icmp-type echo-request -j ACCEPT
    iptables -A block --protocol icmp --icmp-type destination-unreachable
 -j ACCEPT
  # Jump to that chain from INPUT and FORWARD chains.
        iptables -A INPUT -j block
        iptables -A FORWARD -j block
        iptables -A OUTPUT -j block

}

firewall_stop()
{
    # Flush all rules
    iptables -F INPUT
    iptables -F OUTPUT
    iptables -F FORWARD

    # Default policies
    iptables -P INPUT   ACCEPT
    iptables -P OUTPUT  ACCEPT
    iptables -P FORWARD ACCEPT
}

firewall_status()
{
    iptables -L
}

case "$1" in
    start)
        log_begin_msg "Starting firewall..."
        firewall_start
        log_end_msg 0
        ;;

    stop)
        log_begin_msg "Stopping firewall..."
        firewall_stop
        log_end_msg 0
        ;;

    status)
        log_begin_msg "Firewall Status..."
        firewall_status
        log_end_msg 0
        ;;

    restart)
      log_begin_msg "Restarting firewall..."
        firewall_stop
        firewall_start
        log_end_msg 0
        ;;

    *)
        echo "Usage: $0 {start|stop|restart|status}"
        exit 1
esac

The above did not work.
I could not contact the loopback interface or anything in the outside world which was referred from the dns (e.g.ping [www.google.com](www.google.com) did not work, but I could ping the ip address of google.)

So, I modified the script as follows:

#!/bin/sh
#
# Author: Martti Kuparinen <martti.kuparinen@iki.fi>
#
# $Id: firewall,v 1.3 2005/11/25 09:50:43 martti Exp $
#

if [ -r /lib/lsb/init-functions ]; then
    . /lib/lsb/init-functions
fi

firewall_start()
{
#---------------------------------------------------------------
# Initialize all the chains by removing all the rules
# tied to them
#---------------------------------------------------------------
    iptables --flush


# Create chain which blocks new connections, except if coming from inside.
#create new table block
        iptables -N block
#append a rule to block that accepts packets that are from exchanges already in existance
        iptables -A block -m state --state ESTABLISHED,RELATED -j ACCEPT
#appenda rule that allows everything unless it comes from eth1
        iptables -A block -m state --state ESTABLISHED,RELATED,NEW -i ! eth1 -j ACCEPT
#append a rule to block that first logs then accepts packets
#from eth1 with tcp protocol directed to ports 22 and 8080
        iptables -A block -p tcp -i eth1 --dport 22 --sport 1024:65535 -j LOG --log-prefix "ssh connect:"
        iptables -A block -p tcp -i eth1 --dport 22 --sport 1024:65535 -j ACCEPT
iptables -A block -p tcp -i eth1 --dport 8080 --sport 1024:65535 -j LOG --log-prefix "web connect:"
        iptables -A block -p tcp -i eth1 --dport 8080 --sport 1024:65535 -j ACCEPT
    # Allow everything on the loopback network
    iptables -A block -i lo -j ACCEPT

    # Allow incoming ICMP echo request and errors
   iptables -A block --protocol icmp --icmp-type echo-request -j ACCEPT
    iptables -A block --protocol icmp --icmp-type destination-unreachable
 -j ACCEPT
#Log and drop everything else
iptables -A block -j LOG --log-prefix "rejected packet:"
iptables -A block -j DROP
  # Jump to that chain from INPUT and FORWARD chains.
        iptables -A INPUT -j block
        iptables -A FORWARD -j block
        iptables -A OUTPUT -j block

}

firewall_stop()
{
    # Flush all rules
    iptables -F INPUT
    iptables -F OUTPUT
    iptables -F FORWARD

    # Default policies
    iptables -P INPUT   ACCEPT
    iptables -P OUTPUT  ACCEPT
    iptables -P FORWARD ACCEPT
}

firewall_status()
{
    iptables -L
}

case "$1" in
    start)
        log_begin_msg "Starting firewall..."
        firewall_start
        log_end_msg 0
        ;;

    stop)
        log_begin_msg "Stopping firewall..."
        firewall_stop
        log_end_msg 0
        ;;

    status)
        log_begin_msg "Firewall Status..."
        firewall_status
        log_end_msg 0
        ;;

    restart)
      log_begin_msg "Restarting firewall..."
        firewall_stop
        firewall_start
        log_end_msg 0
        ;;

    *)
        echo "Usage: $0 {start|stop|restart|status}"
        exit 1
esac

So, can anyone tell me why the first script does not work ???
cheers !!

---

### Post by SHOWE on 2006-01-31
Sorry, there is a small error int he initial script, which i am sure everybody worked out anyway.

The following 3 lines in the initial non-working script should read as follows:-

# The policy should be to drop it
#---------------------------------------------------------------
iptables --policy INPUT DROP
iptables --policy OUTPUT DROP
iptables --policy FORWARD DROP

i.e. the first step is to set the default policy of the built-in tables to drop.
I really like this way of doing things- it is so much better than oopening everything up then closing it again.

Anyway, if anyone can tell me why this script does not work, I'd be very grateful.
I suspect it has something to do with the way all the service ports default closed in a fresh ubuntu install or else I do not have my resolv.conf set up right. No idea why this would affect a firewall though.

---

### Post by goatflyer on 2006-01-31
can you ping google with your firewall script turned off?  (i.e. standard out of the box ubuntu).

If not then I would check your /etc/resolv.conf

You don't say anything about your eth/internet connection.  Are you using pppoe?

My suggestion would be to get the thing working first, then add your firewall bit by bit.

---

### Post by SHOWE on 2006-02-03
Hi,

Thanks for your reply.
I just noticed there is a security section to this site, so I might repost there if i get a moment.
In any case, everything works fine until I switched the firewall on.
Then I could't reach [www.google.com](www.google.com).
The line in question causing the problem seemed to be:-

 iptables -A block -m state --state ESTABLISHED,RELATED -j ACCEPT

this worked for me in the past on fedora and red hat.
Maybe they changed the iptables specification or else ubuntu has some ports closed or something.

---

