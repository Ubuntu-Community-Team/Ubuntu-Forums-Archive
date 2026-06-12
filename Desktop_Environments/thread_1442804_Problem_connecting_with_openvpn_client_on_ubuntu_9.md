---
title: "Problem connecting with openvpn client on ubuntu 9.04"
date: 2010-03-30
forum: Desktop Environments
---

### Post by Pro_D on 2010-03-30
I have a working openvpn server service installed on my server now.  The server is bridged with dhcpd giving out IP addresses (separate pool from the lan clients).  Server is 9.04.  Openvpn is from repositories.

In windows I can use the windows openvpn GUI client to connect to this server just fine and once connected can browse computer shares (windows type) as well as ssh and so forth.

Problem is when I use the same configuration files in ubuntu 9.04 (on my laptop, desktop environment) either it fails to connect or the computer basically becomes unresponsive (CPU in system monitor on toolbar shows 100% usage on IOwait (nearly black color of blue).  I generally have ctrl-alt-F1 (and wait a while) log in in text mode (slowly) and do a command line reboot as the gui just won't respond in a reasonable time (sometimes as much as 10 seconds to respond to a single click).

Not really sure what to look at in this case...
I used network manager to import the ovpn file and to do the connection. I installed the openvpn network manager package to do this btw.

my client.ovpn file:
----
### Client configuration file for OpenVPN



# Specify that this is a client

client



# Bridge device setting

dev tap



# Host name and port for the server (default port is 1194)

# note: replace with the correct values your server set up

remote <my.dyndns.com.addr> <my port>
float



# Client does not need to bind to a specific local port

nobind





# Keep trying to resolve the host name of OpenVPN server.

## The windows GUI seems to dislike the following rule. 

##You may need to comment it out.

resolv-retry infinite



# Preserve state across restarts

persist-key

persist-tun



# SSL/TLS parameters - files created previously

ca ca.crt

cert client.crt

key client.key



# Since we specified the tls-auth for server, we need it for the client

# note: 0 = server, 1 = client

tls-auth ta.key 1



# Specify same cipher as server

cipher BF-CBC



# Use compression

comp-lzo



# Log verbosity (to help if there are problems)

verb 3

----

I can't post my server config atm as I am not in my server network and am running linux on my laptop right now (no ssh from outside world, on purpose).

Any suggestions what to look at next?  Again, it works perfectly fine in windows on my laptop, just not ubuntu.

---

