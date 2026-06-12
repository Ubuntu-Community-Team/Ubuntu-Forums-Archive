---
title: "Moblock is not running on Ubuntu 9.04"
date: 2009-06-22
forum: General Help
---

### Post by memor2000 on 2009-06-22
Hi,

I'm using Ubuntu 9.04 server edition.
I have installed moblock with this commands:

To add Moblock in your sources it is necessary:
1 – import the keys, using Terminal
[COLOR=#0000FF]gpg –keyserver keyserver.ubuntu.com –recv-keys 9C0042C8[/COLOR]
[COLOR=#0000FF]gpg –export –armor 9C0042C8 | sudo apt-key add -[/COLOR]
2 – import the source on the Software Sources
[COLOR=#0000FF]deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) jaunty main[/COLOR]
[COLOR=#0000FF]deb-src [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) jaunty main[/COLOR]
3 – install Moblock (using Terminal)
[COLOR=#0000FF]sudo aptitude update[/COLOR]
[COLOR=#0000FF]sudo aptitude install moblock blockcontrol

[COLOR=Black]After the configuration I try to start moblock[/COLOR] [COLOR=Black]and, with [COLOR=Blue]blockcontrol status[/COLOR] command, I receive the message "* moblock is not running".

Here my log:

[I]2009-06-22 04:09:29 PM CEST Begin: blockcontrol start
Problematic daemon status: 1
 * moblock is not running
adsl@anacleto:/var/log$ sudo blockcontrol stop
 * Stopping IP block daemon moblock                                                                              [ OK ]
adsl@anacleto:/var/log$ cat blockcontrol.log
2009-06-22 04:09:29 PM CEST Begin: blockcontrol start
Problematic daemon status: 1
 * moblock is not running
2009-06-22 04:10:03 PM CEST Begin: blockcontrol stop
Stopping blockcontrol.watchdog.
Deleting iptables ...
iptables v1.4.1.1: Couldn't load target `blockcontrol_in':/lib/xtables/libipt_blockcontrol_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.1.1: Couldn't load target `blockcontrol_out':/lib/xtables/libipt_blockcontrol_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.4.1.1: Couldn't load target `blockcontrol_fw':/lib/xtables/libipt_blockcontrol_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
                                                                                                                 [fail]
 * There occured some errors during the deletion of the iptables rules.
 * The most common reason for this is that they did not exist, because moblock
 * was not running. In this case you don't have to worry.
 * But if moblock was running there is some problem. Most probably you have
 * installed another firewall application that did delete the iptables rules.
 * A "blockcontrol restart" will then fix the situation.
Executing /etc/blockcontrol/iptables-custom-remove.sh ...                                                        [ OK ]
Stopping moblock .../sbin/start-stop-daemon: warning: failed to kill 4661: No such process
                                                                                                                 [ OK ]
2009-06-22 04:10:03 PM CEST End: blockcontrol stop
[/I]
[/COLOR]
[COLOR=Black]And this is [COLOR=Blue]blockcontrol status[/COLOR] output after [COLOR=Blue]blockcontrol start[/COLOR] command:
[I]
Current IPv4 iptables rules (this may take a while):

Chain INPUT (policy ACCEPT 9182 packets, 3421K bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 9172 packets, 1387K bytes)
 pkts bytes target     prot opt in     out     source               destination

Please check if the above printed iptables rules are correct!

 * moblock is not running[/I]


Please help me. Thank you[/COLOR].
[/COLOR]

---

### Post by jre on 2009-06-22
Somehow there´s a pid file (this indicates that the moblock daemon is running), which shouldn´t be there. I don´t know why, and if your problems persist, we should dig into this.

For a short solution just remove it:
```
sudo rm /var/run/moblock.pid
```

Please give feedback,
- if this helped
- if the problem occured later again

---

### Post by memor2000 on 2009-06-22
Thank you very much for your help.
I haven't /var/run/moblock.pid file.
Now, when I try to start blockcontrol, it freeze on starting:

[I]adsl@anacleto:/var/run$ sudo blockcontrol start
 * Starting IP block daemon moblock[/I]


Only with ctrl+c I can unlock it, but, in any case, the message is always the same (* moblock is not running). :-(

Any other suggestions?

Thanks a lot

ps: I don't know if it can help, but I'm using command line, so I didn't install mobloquer.

---

### Post by jre on 2009-06-23
Please check what happens during the start. Follow live the logfile:
```
tail -f /var/log/blockcontrol.log
``` when you do the "start".

Prbably it just does the initial blocklist download, which takes some time. This will happen either during installation (when you keep the daily cron job for the automatic blocklist update enabled), or before the first start (when you have disabled it)

---

### Post by memor2000 on 2009-06-24
This is the ```
tail -f /var/log/blockcontrol.log
``` output:

```
2009-06-24 09:28:17 AM CEST Begin: blockcontrol start
Building blocklist... Updating Short... ... failed! Trying without timestamping ... *  Error 9: Short not available. Aborting!
 * To fix this manually download Short and save it as /var/spool/blockcontrol/Short/downloaded/Short
```I googled, but i was unable to find anything about Short :(

Thanks a lot

---

### Post by jre on 2009-06-26
I guess something in your /etc/blockcontrol/blocklists.list is wrong. There must only be URLs in this file and comments (which have to start with a hash "#"). So check this file and add a hash before this "short" line.

This is the current file as I ship it:
[http://moblock-deb.svn.sourceforge.net/viewvc/moblock-deb/blockcontrol/blockcontrol/blocklists.list?revision=410](http://moblock-deb.svn.sourceforge.net/viewvc/moblock-deb/blockcontrol/blockcontrol/blocklists.list?revision=410)

---

### Post by memor2000 on 2009-06-29
Thank you very much for your help.
I replaced my /etc/blockcontrol/blocklists.list with yours (the original I think) and now I have a similar initial problem. Blockcontrol is not running.....


This is the present situation:

```
adsl@anacleto:/var/log$ sudo blockcontrol start
 * Starting IP block daemon moblock                                                

adsl@anacleto:/var/log$ sudo blockcontrol status
Current IPv4 iptables rules (this may take a while):

Chain INPUT (policy ACCEPT 19 packets, 1729 bytes)
 pkts bytes target     prot opt in     out     source               destination    

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination    

Chain OUTPUT (policy ACCEPT 17 packets, 2017 bytes)
 pkts bytes target     prot opt in     out     source               destination    

Chain blockcontrol_fw (0 references)
 pkts bytes target     prot opt in     out     source               destination    
    0     0 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 92

Chain blockcontrol_in (0 references)
 pkts bytes target     prot opt in     out     source               destination    
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80
    0     0 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 92

Chain blockcontrol_out (0 references)
 pkts bytes target     prot opt in     out     source               destination    
    0     0 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 92

Please check if the above printed iptables rules are correct!

 * moblock is not running

adsl@anacleto:/var/log$ sudo blockcontrol stop
 * Stopping IP block daemon moblock                                         [ OK ] 
```And this is the log after the operations above:

```

adsl@anacleto:/var/log$ cat blockcontrol.log
2009-06-29 06:30:38 PM CEST Begin: blockcontrol start
Inserting iptables ...
iptables v1.4.1.1: invalid port/service `http' specified
Try `iptables -h' or 'iptables --help' for more information.
                                                                            [fail]
2009-06-29 06:31:07 PM CEST Begin: blockcontrol stop
Stopping blockcontrol.watchdog.
Deleting iptables ...
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
                                                                            [fail]
 * There occured some errors during the deletion of the iptables rules.
 * The most common reason for this is that they did not exist, because moblock
 * was not running. In this case you don't have to worry.
 * But if moblock was running there is some problem. Most probably you have
 * installed another firewall application that did delete the iptables rules.
 * A "blockcontrol restart" will then fix the situation.
Executing /etc/blockcontrol/iptables-custom-remove.sh ...                   [ OK ]
Stopping moblock ...                                                        [ OK ]
2009-06-29 06:31:07 PM CEST End: blockcontrol stop
adsl@anacleto:/var/log$
```

---

