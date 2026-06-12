---
title: "Can't get Apache2 working"
date: 2005-11-30
forum: Desktop Environments
---

### Post by pulpfiction on 2005-11-30
Hello,

So I wanted to install Apache, PHP and MySQL.

I read this wiki and did what it told me to do.

[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

Now there's one problem: I can't access my pages.

I don't know why. I have Apache running, but when I try to acess [http://localhost](http://localhost) it keeps looking looking and looking, and then I get that following message from Firefox: "the operation timed out when attempting to contact 127.0.0.1".

chico@vertigo:/$ ps aux | grep apache
root      9557  0.0  0.9  14196  5028 ?        Ss   17:53   0:00 /usr/sbin/apache2 -k start -DSSL
chico     9558  0.0  0.9  14196  5040 ?        S    17:53   0:00 /usr/sbin/apache2 -k start -DSSL
chico     9559  0.0  0.9  14196  5040 ?        S    17:53   0:00 /usr/sbin/apache2 -k start -DSSL
chico     9560  0.0  0.9  14196  5040 ?        S    17:53   0:00 /usr/sbin/apache2 -k start -DSSL
chico     9561  0.0  0.9  14196  5040 ?        S    17:53   0:00 /usr/sbin/apache2 -k start -DSSL
chico     9564  0.0  0.9  14196  5040 ?        S    17:53   0:00 /usr/sbin/apache2 -k start -DSSL
chico     9572  0.0  0.1   2948   536 pts/0    R+   17:57   0:00 grep apache

Any ideas?

Also, while I'm on it, is there an easy way to start/stop/restart services?

Right now I'm using "/etc/rc1.d/K91apache2 start/stop/restart".

---

### Post by pulpfiction on 2005-12-09
Wow... bump.

---

### Post by amohanty on 2005-12-09
In the apache httpd.conf file what is the IP that you specified it should listen to?
Make sure that your /etc/hosts file has that IP listed pointing to you host, or try to hit:
http://<your ip address>

Better yet post the section of your httpd.conf file where you specify the IP it is listening to and your /etc/hosts file.

AM

---

### Post by pulpfiction on 2005-12-09
My hosts file:

chico@vertigo:~$ cat /etc/hosts
127.0.0.1       localhost.localdomain   localhost       vertigo

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

My httpd.conf has some irrelevant data. I'll post apache2.conf instead:

(...)
# Include ports listing
Include /etc/apache2/ports.conf
(...)

And finally, my ports.conf:

chico@vertigo:/etc/apache2$ cat ports.conf
Listen 8888

I have ports 80 and 8080 blocked by my ISP by default. But yes, I'm trying to access [http://localhost:8888/](http://localhost:8888/) instead.

---

### Post by amohanty on 2005-12-09
does [http://vertigo:8888](http://vertigo:8888) work.

If that doesnt work try:
http://<your ip which you get via ifconfig>:8888

If that doesnt work uncomment this line in your apache2.conf

```
BindAddress *
```

and try the two addresses above again?

Also are you using a router? or is your box directly connected to the dsl/cable modem?

---

### Post by pulpfiction on 2005-12-09
[QUOTE=amohanty]does [http://vertigo:8888](http://vertigo:8888) work.

If that doesnt work try:
http://<your ip which you get via ifconfig>:8888

If that doesnt work uncomment this line in your apache2.conf

```
BindAddress *
```

and try the two addresses above again?

Also are you using a router? or is your box directly connected to the dsl/cable modem?[/QUOTE]

Both IPs didn't work. I noticed something though: by using vertigo/localhost/127.0.0.1 it seems the browser tries to resolv and gives me the error message after some seconds, while using the IP I got from ifconfig I get the same message just after I press enter.

This box is directly connected to the ADSL modem.

I couldn't find that line on my apache2.conf, but still I tried to add to it. It gave me this error message:

chico@vertigo:/etc/apache2$ sudo /etc/rc1.d/K91apache2 restart
 * Forcing reload of web server  (Apache2)... Syntax error on line 395 of /etc/apache2/apache2.conf:
Invalid command 'BindAddress', perhaps mis-spelled or defined by a module not in cluded in the server configuration
                                                                         [fail]

---

### Post by amohanty on 2005-12-10
ok at the terminal try the following:

```
telnet localhost 8888
```

If it connects all you will get is a blank screen, ctrl-c out of it. This is a quick and drity way to verify access, it hits localhost on port 8888.

Also you could you post your apache2.conf and your /etc/hosts and the output of:

```
hostname
```

---

### Post by pulpfiction on 2005-12-11
Ok, it looks like it couldn't connect to my 8888 port:

chico@vertigo:~$ telnet localhost 8888
Trying 127.0.0.1...

chico@vertigo:~$ hostname
vertigo

apache2.conf is attached. My hosts file is some replies above, ports.conf included.

Hope it helps.

---

### Post by amohanty on 2005-12-12
Can you post your httpd.conf and ports.conf.. They dont seem to be attached to previous posts.

AM

---

### Post by pulpfiction on 2005-12-12
chico@vertigo:/etc/apache2$ cat ports.conf
Listen 8888

I'm not on Ubuntu right now so I can't post my httpd.conf, but I'm quite sure there's nothing related to this there. There's only a few comments and one directive.

---

### Post by amohanty on 2005-12-12
actually if that relates to the servername directive, its quite important. post that when you can and we can go from there.

---

### Post by pulpfiction on 2005-12-12
Ok, I was wrong. Actually it's only comments.

chico@vertigo:~$ cat /etc/apache2/httpd.conf
# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

---

### Post by amohanty on 2005-12-12
Well your config files look ok.
Can you post the output of :

> netstat -lp

Basically we want to chech which port is actually open. I am not on my box right now so cant post the extected output.

Also make sure that the httpd or apache2 daemon in /etc/init.d script uses apache2.conf as the configuration file.

Finally in ports.conf change the Listen directive to:
> Listen 127.0.0.1:8888

HTH

---

### Post by pulpfiction on 2005-12-12
chico@vertigo:~$ netstat -lp
(Nem todos os processos puderam ser identificados, informações sobre processos
 de outrem não serão mostrados, você deve ser root para vê-los todos.)
Conexões Internet Ativas (sem os servidores)
Proto Recv-Q Send-Q Endereço Local          Endereço Remoto         Estado       PID/Program name
tcp        0      0 localhost.localdo:32769 *:*                     OUÇA      -
tcp        0      0 localhost.localdo:mysql *:*                     OUÇA      -
tcp        0      0 localhost.localdoma:ipp *:*                     OUÇA      -
tcp6       0      0 *:8888                  *:*                     OUÇA      -
Domain sockets UNIX ativos (sem os servidores)
Proto CntRef Flags       Tipo       Estado        I-Node Rota PID/Program name    Caminho
unix  2      [ ACC ]     STREAM     OUVINDO       9403     -                   /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     OUVINDO       9095     -                   /tmp/.gdm_socket
unix  2      [ ACC ]     STREAM     OUVINDO       10444    -                   /tmp/ssh-rDVneg7300/agent.7300
unix  2      [ ACC ]     STREAM     OUVINDO       10468    7344/gconfd-2       /tmp/orbit-chico/linc-1cb0-0-63624077758e4
unix  2      [ ACC ]     STREAM     OUVINDO       11172    7451/mapping-daemon /tmp/mapping-chico
unix  2      [ ACC ]     STREAM     OUVINDO       10478    7300/x-session-mana /tmp/orbit-chico/linc-1c84-0-6f884fb38d9c3
unix  2      [ ACC ]     STREAM     OUVINDO       10629    7300/x-session-mana /tmp/.ICE-unix/7300
unix  2      [ ACC ]     STREAM     OUVINDO       10638    7347/gnome-keyring- /tmp/keyring-xfMPXQ/socket
unix  2      [ ACC ]     STREAM     OUVINDO       10652    7349/esd            /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     OUVINDO       10671    7353/bonobo-activat /tmp/orbit-chico/linc-1cb9-0-7c91f45d38f13
unix  2      [ ACC ]     STREAM     OUVINDO       10693    7355/gnome-settings /tmp/orbit-chico/linc-1cbb-0-313fbd878b490
unix  2      [ ACC ]     STREAM     OUVINDO       10794    7377/metacity       /tmp/orbit-chico/linc-1cd1-0-51f0f9dcfb20
unix  2      [ ACC ]     STREAM     OUVINDO       10823    7399/gnome-panel    /tmp/orbit-chico/linc-1ce7-0-51472a0c4553
unix  2      [ ACC ]     STREAM     OUVINDO       10843    7403/gnome-volume-m /tmp/orbit-chico/linc-1ceb-0-3786dd8f207c0
unix  2      [ ACC ]     STREAM     OUVINDO       10867    7401/nautilus       /tmp/orbit-chico/linc-1ce9-0-2220c4eb2472
unix  2      [ ACC ]     STREAM     OUVINDO       10892    7409/update-notifie /tmp/orbit-chico/linc-1cf1-0-4c2c066a82119
unix  2      [ ACC ]     STREAM     OUVINDO       10931    7411/wnck-applet    /tmp/orbit-chico/linc-1cf3-0-4c2c066ad891c
unix  2      [ ACC ]     STREAM     OUVINDO       10959    7421/gnome-vfs-daem /tmp/orbit-chico/linc-1cfd-0-587e8767f0a
unix  2      [ ACC ]     STREAM     OUVINDO       12354    8143/gnome-terminal /tmp/orbit-chico/linc-1fcf-0-8c133723a95e
unix  2      [ ACC ]     STREAM     OUVINDO       11144    7449/trashapplet    /tmp/orbit-chico/linc-1d19-0-68cc9d94c3664
unix  2      [ ACC ]     STREAM     OUVINDO       11227    7464/notification-a /tmp/orbit-chico/linc-1d28-0-205dfb8f45a22
unix  2      [ ACC ]     STREAM     OUVINDO       11244    7466/mixer_applet2  /tmp/orbit-chico/linc-1d2a-0-205dfb8f6e4d2
unix  2      [ ACC ]     STREAM     OUVINDO       11261    7462/clock-applet   /tmp/orbit-chico/linc-1d26-0-205dfb8fbfda6
unix  2      [ ACC ]     STREAM     OUVINDO       12198    8075/firefox-bin    /tmp/orbit-chico/linc-1f8b-0-47413cd8c4656
unix  2      [ ACC ]     STREAM     OUVINDO       7638     -                   /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     OUVINDO       7728     -                   @/tmp/hald-local/dbus-3ikEwKvxl5
unix  2      [ ACC ]     STREAM     OUVINDO       9661     -                   /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     OUVINDO       10702    7358/gam_server     @/tmp/fam-chico-
unix  2      [ ACC ]     STREAM     OUVINDO       7712     -                   /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     OUVINDO       10041    -                   /var/run/sdp
unix  2      [ ACC ]     STREAM     OUVINDO       10449    7342/dbus-daemon    @/tmp/dbus-HDLc8zr1wn

It looks like it does use my edited httpd.conf. Notice I'm listening to the custom port I configured 8888.

---

### Post by pulpfiction on 2005-12-12
With the new Listen directive, something strange happens. I can't start Apache.

chico@vertigo:/etc/init.d$ sudo apache2 -k start -DSSL
(99)Cannot assign requested address: make_sock: could not bind to address 127.0.0.1:8888
no listening sockets available, shutting down
Unable to open logs

Maybe that helps.

---

### Post by amohanty on 2005-12-12
how about replacing 127.0.0.1 with you8r box's IP address

---

### Post by pulpfiction on 2005-12-12
Ok, using Listen 201.0.114.133:8888 apache started, but acessing [http://201.0.114.133:8888/](http://201.0.114.133:8888/) gives me the same thing as before with [http://localhost:8888/](http://localhost:8888/). It keeps loading and after some time it times out and gives me the following error message: "the operation timed out when attempting to contact 201.0.114.133".

---

### Post by amohanty on 2005-12-12
Now you woudl want to test if the port is actually accessible from the outside:
> 
suod apt-get install nmap
nmap -vV -sS -p 8888 201.0.114.133

If your ISP blocks servers completely, you should not be able to get a hit back. If you can hit it then post the contents of your apache access log and error log.

HTH

---

### Post by pulpfiction on 2005-12-14
Nothing. :(

chico@vertigo:~$ sudo nmap -vV -sS -p 8888 200.158.155.35

nmap version 3.81 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) )

Also, is it like I don't have any ports open?

chico@vertigo:~$ sudo nmap -vV -sS 200.158.155.35

nmap version 3.81 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) )

---

### Post by amohanty on 2005-12-14
to hit all ports:
> 
sudo nmap -vv -sS -p1,65535 200.158.155.35

HTH

---

### Post by pulpfiction on 2005-12-14
chico@vertigo:~$ sudo nmap -vv -sS -p1,65535 200.158.155.35
Password:

Starting nmap 3.81 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-12-14 23:32 BRST
WARNING:  Could not determine what interface to route packets through to 200.158.155.35, changing ping scantype to ICMP ping only
pcap_open_live: ioctl: No such device
There are several possible reasons for this, depending on your operating system:
LINUX: If you are getting Socket type not supported, try modprobe af_packet or recompile your kernel with SOCK_PACKET enabled.
*BSD:  If you are getting device not configured, you need to recompile your kernel with Berkeley Packet Filter support.  If you are getting No such file or directory, try creating the device (eg cd /dev; MAKEDEV <device>; or use mknod).
SOLARIS:  If you are trying to scan localhost and getting '/dev/lo0: No such file or directory', complain to Sun.  I don't think Solaris can support advanced localhost scans.  You can probably use "-P0 -sT localhost" though.


QUITTING!

---

### Post by amohanty on 2005-12-14
Sorry I was wrong about the syntax, try this:

> sudo nmap -vv -sS -p1-65535 200.158.155.35

needed a - instead of a comma in the ports list. Sorry about that.

AM

---

