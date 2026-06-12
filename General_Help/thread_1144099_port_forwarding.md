---
title: "port forwarding"
date: 2009-04-30
forum: General Help
---

### Post by gauravforyouall on 2009-04-30
HI... 
i want to configure my ubuntu 8.10 as server, 
i tried using apache and hfs, which both were working fine for me
in windows.
Although in local system both are still working fine but no one is able to connect from external world.

they get time out, i have configure my ports also in my router but still doesnt seem to help... how to solve i want to run application on port 80 only....

---

### Post by prem1er on 2009-04-30
By default that port is open on ubuntu. Are you using iptables to block connections?

---

### Post by Monotoko on 2009-04-30
I would say its something to do with your router, what sorta router are you using?

---

### Post by gauravforyouall on 2009-04-30
no i am not using anything :( i mean i didnt configure it that was pre configured i dont know i actually installed ubuntu ultimate 2.1 i installed firestarter as someone suggested it, ran it and disabeleed firewall but again didnt help

---

### Post by gauravforyouall on 2009-04-30
i am using MTNL T-KD-318-EUI, and i have configure it properly for my windows box ,and same settings i am usingfor ubuntu, except ip address which was 
192.168.1.5
in windows
and 192.168.1.3 in linux ....

---

### Post by prem1er on 2009-04-30
Firestarter is used to block specific ports from being used.  What exactly did you do with firestarter?

---

### Post by cariboo on 2009-04-30
Make sure you server has a static ip address, as if you use dhcp, the ip address could change every time you reboot.

---

### Post by Monotoko on 2009-04-30
The IP changes?!? Are ubuntu and windows on the same computer?
That sounds very odd for me....they usually share the same internal IP address.

and this may sound like a daft question, but you arent giving the people the internal IP (192.168...) are you? i once made that mistake a long time ago

---

### Post by gauravforyouall on 2009-04-30
no.. i am giving my external ipp and i am updating my ip also on dyndns. so i need not worry about that. ya both are on same pc actuall i have dual boot machine, i used hfs in windows to share files but in ubuntu i am not able to use that... so.. and static local ip of my pc is 192.168.1.3 and after i configured my router properly running
[http://192.168.1.3](http://192.168.1.3)
in my browser shows it works
but when i ask someone else to click on
[http://59](http://59)..... my ip address
it wont. work

---

### Post by gauravforyouall on 2009-04-30
i didnt do anything as i told my frnd ask me to install it run it and click on disable firewall i did that much only :| please help guys it is very tough to mail each and everyfile when we have softwares like hfs or apache which can make me help maintain file sharing server

---

### Post by prem1er on 2009-04-30
Post results of this.

```
sudo netstat -lp
```

---

### Post by gauravforyouall on 2009-04-30
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:domain                *:*                     LISTEN      4932/dnsmasq    
tcp        0      0 localhost:ipp           *:*                     LISTEN      5142/cupsd      
tcp6       0      0 [::]:www                [::]:*                  LISTEN      5556/apache2    
tcp6       0      0 [::]:domain             [::]:*                  LISTEN      4932/dnsmasq    
udp        0      0 *:domain                *:*                                 4932/dnsmasq    
udp        0      0 *:bootpc                *:*                                 4794/dhclient   
udp        0      0 *:45406                 *:*                                 4908/avahi-daemon: 
udp        0      0 *:mdns                  *:*                                 4908/avahi-daemon: 
udp6       0      0 [::]:domain             [::]:*                              4932/dnsmasq    
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     337318   4067/dbus-daemon    @/tmp/dbus-grleYPxxgB
unix  2      [ ACC ]     STREAM     LISTENING     15741    5248/hald           @/var/run/hald/dbus-32nrH2eVSc
unix  2      [ ACC ]     STREAM     LISTENING     15118    4888/dbus-daemon    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     18069    6031/dbus-daemon    @/tmp/dbus-XzxAsLqAg2
unix  2      [ ACC ]     STREAM     LISTENING     15738    5248/hald           @/var/run/hald/dbus-9faFMfLEq7
unix  2      [ ACC ]     STREAM     LISTENING     16698    5327/bluetoothd     /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     15163    4908/avahi-daemon:  /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     16714    5327/bluetoothd     @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     17000    5418/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     17827    5956/gnome-keyring- /tmp/keyring-ikdLkz/socket
unix  2      [ ACC ]     STREAM     LISTENING     17833    5956/gnome-keyring- /tmp/keyring-ikdLkz/ssh
unix  2      [ ACC ]     STREAM     LISTENING     16999    5418/X              @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     17839    5956/gnome-keyring- /tmp/keyring-ikdLkz/socket.pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     18108    6034/pulseaudio     /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     18112    6034/pulseaudio     /tmp/pulse-gaurav/native
unix  2      [ ACC ]     STREAM     LISTENING     18161    6039/gconfd-2       /tmp/orbit-gaurav/linc-1797-0-7dafb43c77b8c
unix  2      [ ACC ]     STREAM     LISTENING     18453    6037/gconf-helper   /tmp/orbit-gaurav/linc-1795-0-30dffa189b55a
unix  2      [ ACC ]     STREAM     LISTENING     18503    6046/seahorse-agent /tmp/seahorse-MHJ94o/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     18538    5969/x-session-mana /tmp/.ICE-unix/5969
unix  2      [ ACC ]     STREAM     LISTENING     18556    5969/x-session-mana /tmp/orbit-gaurav/linc-1751-0-36cca33e61168
unix  2      [ ACC ]     STREAM     LISTENING     18632    6046/seahorse-agent /tmp/orbit-gaurav/linc-179e-0-5506472b9c1d2
unix  2      [ ACC ]     STREAM     LISTENING     19021    6126/compiz.real    /tmp/orbit-gaurav/linc-17ee-0-2e2b9dda250c0
unix  2      [ ACC ]     STREAM     LISTENING     18792    6064/gnome-settings /tmp/orbit-gaurav/linc-17b0-0-77944cd717386
unix  2      [ ACC ]     STREAM     LISTENING     19112    6138/gnome-screensa /tmp/orbit-gaurav/linc-17f5-0-1942ce8c2df
unix  2      [ ACC ]     STREAM     LISTENING     19181    6140/gtk-window-dec /tmp/orbit-gaurav/linc-17fc-0-109ec214446f7
unix  2      [ ACC ]     STREAM     LISTENING     19350    6141/gnome-panel    /tmp/orbit-gaurav/linc-17fd-0-40d9e44f244ee
unix  2      [ ACC ]     STREAM     LISTENING     19431    6142/nautilus       /tmp/orbit-gaurav/linc-17fe-0-40d9e44fc4400
unix  2      [ ACC ]     STREAM     LISTENING     19446    6145/bonobo-activat /tmp/orbit-gaurav/linc-1801-0-10d5c619ce239
unix  2      [ ACC ]     STREAM     LISTENING     19557    6161/trashapplet    /tmp/orbit-gaurav/linc-1811-0-5aa17ca7a63b8
unix  2      [ ACC ]     STREAM     LISTENING     19740    6172/mixer_applet2  /tmp/orbit-gaurav/linc-181c-0-493bd32eda2d5
unix  2      [ ACC ]     STREAM     LISTENING     19876    6179/fast-user-swit /tmp/orbit-gaurav/linc-1823-0-2748b55aee5a6
unix  2      [ ACC ]     STREAM     LISTENING     20325    6191/nm-applet      /tmp/orbit-gaurav/linc-182f-0-1812a1e6cb26a
unix  2      [ ACC ]     STREAM     LISTENING     20421    6187/update-notifie /tmp/orbit-gaurav/linc-182b-0-1da729d6dd3b1
unix  2      [ ACC ]     STREAM     LISTENING     20429    6209/gnome-power-ma /tmp/orbit-gaurav/linc-182d-0-1da729d6e0a9a
unix  2      [ ACC ]     STREAM     LISTENING     20582    6214/notification-d /tmp/orbit-gaurav/linc-1846-0-7b4db3d03f21f
unix  2      [ ACC ]     STREAM     LISTENING     20753    6196/cli            /tmp/orbit-gaurav/linc-1834-0-139732833f6
unix  2      [ ACC ]     STREAM     LISTENING     21407    6249/evolution-data /tmp/orbit-gaurav/linc-1869-0-2892832099160
unix  2      [ ACC ]     STREAM     LISTENING     21477    6254/evolution-exch /tmp/orbit-gaurav/linc-186e-0-71714b8639bd
unix  2      [ ACC ]     STREAM     LISTENING     89474    6034/pulseaudio     /tmp/pulse-gaurav/cli
unix  2      [ ACC ]     STREAM     LISTENING     15529    5190/chipcardd4     /var/run/chipcard/chipcard.comm
unix  2      [ ACC ]     STREAM     LISTENING     21850    6297/evolution-alar /tmp/orbit-gaurav/linc-1899-0-2249f0bcecbaa
unix  2      [ ACC ]     STREAM     LISTENING     65909    8489/rhythmbox      /tmp/orbit-gaurav/linc-2129-0-7842223ad3bf6
unix  2      [ ACC ]     STREAM     LISTENING     90771    9540/firefox        /tmp/orbit-gaurav/linc-2544-0-399800989886e
unix  2      [ ACC ]     STREAM     LISTENING     109298   11290/kdeinit4: kde /tmp/ksocket-gaurav/kdeinit4__0
unix  2      [ ACC ]     STREAM     LISTENING     109310   11293/klauncher     /tmp/ksocket-gaurav/klauncherT11293.slave-socket
unix  2      [ ACC ]     STREAM     LISTENING     241977   28751/pidgin        /tmp/orbit-gaurav/linc-704f-0-1391b9644a78
unix  2      [ ACC ]     STREAM     LISTENING     405487   5203/gnome-terminal /tmp/orbit-gaurav/linc-1453-0-5aff2213bcd2b
unix  2      [ ACC ]     STREAM     LISTENING     24806    6640/apache2        /var/run/apache2/cgisock.5556
unix  2      [ ACC ]     STREAM     LISTENING     16876    5409/gdm            /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     14832    4693/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     202490   5142/cupsd          /var/run/cups/cups.sock

---

### Post by Monotoko on 2009-04-30
Now this is just an educated guess but:

```
tcp6 0 0 [::]:www [::]:* LISTEN 5556/apache2 
```

should apache2 be on port 5556??

try getting them to connect through

[http://yourip:5556](http://yourip:5556)

(you may have to forward that port on the router)

---

### Post by gauravforyouall on 2009-04-30
gaurav@Damaged:~$ tcp6 0 0 [::]:www [::]:* LISTEN 5556/apache2
bash: tcp6: command not found
:(

---

### Post by gauravforyouall on 2009-04-30
gaurav@Damaged:~$ sudo apt-get install tcp6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package tcp6
gaurav@Damaged:~$ tcp
bash: tcp: command not found


i did this also means i guess thr is nothing as tcp6 or shld i find deb for that

---

### Post by gauravforyouall on 2009-04-30
any help please

---

### Post by albinootje on 2009-04-30
> **gauravforyouall said:**
> i am using MTNL T-KD-318-EUI, and i have configure it properly for my windows box ,and same settings i am usingfor ubuntu, except ip address which was 
192.168.1.5 in windows
and 192.168.1.3 in linux ....

Since you have a dual-boot, you need to give Linux also 192.168.1.5 as static ip address, otherwise it won't work with your pre-configured router setup.
Or did you point another port than port 80 in your router to port_forward to port 80 of your 192.168.1.3 Linux box ?

---

### Post by gauravforyouall on 2009-04-30
i gave both. that is 192.168.1.5 and 1.3 also and i guess router is working fine, because if i remove 192.168.1.3 entry from my router
and i do
[http://192.168.1.3](http://192.168.1.3)
it gives me error
so i guess part of port forwarding or router setup is correct. .. ..

---

### Post by albinootje on 2009-04-30
> **gauravforyouall said:**
> if i remove 192.168.1.3 entry from my router
and i do
[http://192.168.1.3](http://192.168.1.3)
it gives me error
so i guess part of port forwarding or router setup is correct. .. ..

Okay. What error is it ? Is apache not running properly or not fully configured ? If so, fix that first, test it locally, and then test the port_forwarding by using the external ip address (preferably from outside your LAN).

---

### Post by gauravforyouall on 2009-04-30
It works!

This is output when i type [http://192.168.1.3](http://192.168.1.3)
means apache is working perfectly but no one can seem to access from outer world... is it some firewall settings how do i check for them/that

---

### Post by albinootje on 2009-04-30
> **gauravforyouall said:**
> no one can seem to access from outer world... is it some firewall settings how do i check for them/that

Okay.
As far as I know you can only configure a port_forward for 1 port in a router to 1 ip address.
So please explain what you did exactly in the router ?
Did you point port 80 to 192.168.1.3 or 192.168.1.5 ?
If you pointed it to 192.168.1.5, then you have to use 192.168.1.5 as ip address for your Linux box too!

---

### Post by gauravforyouall on 2009-04-30
but should not that depend on run time? when i am using linux there is no ip 192.168.1.5 in use so my router is pointing to 192.168.1.3 only ..

---

### Post by albinootje on 2009-04-30
> **gauravforyouall said:**
> but should not that depend on run time? when i am using linux there is no ip 192.168.1.5 in use so my router is pointing to 192.168.1.3 only ..

Please give Linux the static ip address 192.168.1.5, and test it with that.
Since you wrote that you have a dual-boot you can safely give Linux 192.168.1.5 as well.

---

### Post by gauravforyouall on 2009-04-30
#	Private IP	Protocol Private Port Public Port	 
1	192.168.1.3	ANY	80	80	
2	192.168.1.3	ANY	8080	8080	
3	192.168.1.3	ANY	443	443	

I deleted 1.5 entry but still not of help


if i type [http://my_external_ip](http://my_external_ip) from my pc
i get login id page of my router ...

---

### Post by Monotoko on 2009-04-30
Alright dude, this wasnt a code you were meant to run, this was a code you posted, a lil snippet i got from it:

tcp6 0 0 [::]:www [::]:* LISTEN 5556/apache2

its on port 5556, not 80

go to [http://yourip:5556](http://yourip:5556)

---

### Post by gauravforyouall on 2009-04-30
ohok

---

### Post by Monotoko on 2009-04-30
I dont know why its installed to that port, and its only an educated guess, may not work, just try to open port 5556 on your router, then see if anyone can connect to it.

---

### Post by gauravforyouall on 2009-04-30
let me try it... as no one is online right now i have to check from proxy ill get back result in just a minute

---

### Post by gauravforyouall on 2009-04-30
Couldn't connect to my_ip_addr:5556: Unknown error


:|

---

### Post by Monotoko on 2009-04-30
Unknown Error?!

What gives that error, the proxy, apache??

---

### Post by gauravforyouall on 2009-04-30
proxy gave that error .. .not apache. webpage not available was the error when external person tried it why is apache repling 
It works! on port 80 if i type
[http://192.168.1.3](http://192.168.1.3) on my pc

---

### Post by Monotoko on 2009-04-30
I'm finding it very odd, my assumption was incorrect then....do you duel-boot with Windows on that system?

---

### Post by gauravforyouall on 2009-04-30
ya i do., how does/can that matter in this context ? can it ? i am ready to remove windows... if it will help

---

### Post by Monotoko on 2009-04-30
Nooo, what i want you to do, is boot into Windows and install WAMPserver2 from here: [http://www.wampserver.com/en/](http://www.wampserver.com/en/)
Disable any firewalls you have running (including the default Windows one) Install it, and it should work from port80.

This is just a test to see if linux is blocking it, or the router is blocking it

---

### Post by gauravforyouall on 2009-04-30
err i keep on using it in windows everyday!!!!!!!!! i use two servers in windows 
on port 80 and 8080,one apache and other HFS.

---

### Post by Monotoko on 2009-04-30
And can people connect to it behind that router?

---

### Post by gauravforyouall on 2009-04-30
yes.. i share lot of files daily over net through my server and host website from my home only

---

### Post by Monotoko on 2009-04-30
Right, the problem is definatly in linux then, looking at what you posted (below) there is no entry for anything on port 80 so nothing is getting through, im not sure of the exact problem though, so you will have to bear with me a mo.


> **gauravforyouall said:**
> Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:domain                *:*                     LISTEN      4932/dnsmasq    
tcp        0      0 localhost:ipp           *:*                     LISTEN      5142/cupsd      
tcp6       0      0 [::]:www                [::]:*                  LISTEN      5556/apache2    
tcp6       0      0 [::]:domain             [::]:*                  LISTEN      4932/dnsmasq    
udp        0      0 *:domain                *:*                                 4932/dnsmasq    
udp        0      0 *:bootpc                *:*                                 4794/dhclient   
udp        0      0 *:45406                 *:*                                 4908/avahi-daemon: 
udp        0      0 *:mdns                  *:*                                 4908/avahi-daemon: 
udp6       0      0 [::]:domain             [::]:*                              4932/dnsmasq    
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     337318   4067/dbus-daemon    @/tmp/dbus-grleYPxxgB
unix  2      [ ACC ]     STREAM     LISTENING     15741    5248/hald           @/var/run/hald/dbus-32nrH2eVSc
unix  2      [ ACC ]     STREAM     LISTENING     15118    4888/dbus-daemon    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     18069    6031/dbus-daemon    @/tmp/dbus-XzxAsLqAg2
unix  2      [ ACC ]     STREAM     LISTENING     15738    5248/hald           @/var/run/hald/dbus-9faFMfLEq7
unix  2      [ ACC ]     STREAM     LISTENING     16698    5327/bluetoothd     /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     15163    4908/avahi-daemon:  /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     16714    5327/bluetoothd     @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     17000    5418/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     17827    5956/gnome-keyring- /tmp/keyring-ikdLkz/socket
unix  2      [ ACC ]     STREAM     LISTENING     17833    5956/gnome-keyring- /tmp/keyring-ikdLkz/ssh
unix  2      [ ACC ]     STREAM     LISTENING     16999    5418/X              @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     17839    5956/gnome-keyring- /tmp/keyring-ikdLkz/socket.pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     18108    6034/pulseaudio     /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     18112    6034/pulseaudio     /tmp/pulse-gaurav/native
unix  2      [ ACC ]     STREAM     LISTENING     18161    6039/gconfd-2       /tmp/orbit-gaurav/linc-1797-0-7dafb43c77b8c
unix  2      [ ACC ]     STREAM     LISTENING     18453    6037/gconf-helper   /tmp/orbit-gaurav/linc-1795-0-30dffa189b55a
unix  2      [ ACC ]     STREAM     LISTENING     18503    6046/seahorse-agent /tmp/seahorse-MHJ94o/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     18538    5969/x-session-mana /tmp/.ICE-unix/5969
unix  2      [ ACC ]     STREAM     LISTENING     18556    5969/x-session-mana /tmp/orbit-gaurav/linc-1751-0-36cca33e61168
unix  2      [ ACC ]     STREAM     LISTENING     18632    6046/seahorse-agent /tmp/orbit-gaurav/linc-179e-0-5506472b9c1d2
unix  2      [ ACC ]     STREAM     LISTENING     19021    6126/compiz.real    /tmp/orbit-gaurav/linc-17ee-0-2e2b9dda250c0
unix  2      [ ACC ]     STREAM     LISTENING     18792    6064/gnome-settings /tmp/orbit-gaurav/linc-17b0-0-77944cd717386
unix  2      [ ACC ]     STREAM     LISTENING     19112    6138/gnome-screensa /tmp/orbit-gaurav/linc-17f5-0-1942ce8c2df
unix  2      [ ACC ]     STREAM     LISTENING     19181    6140/gtk-window-dec /tmp/orbit-gaurav/linc-17fc-0-109ec214446f7
unix  2      [ ACC ]     STREAM     LISTENING     19350    6141/gnome-panel    /tmp/orbit-gaurav/linc-17fd-0-40d9e44f244ee
unix  2      [ ACC ]     STREAM     LISTENING     19431    6142/nautilus       /tmp/orbit-gaurav/linc-17fe-0-40d9e44fc4400
unix  2      [ ACC ]     STREAM     LISTENING     19446    6145/bonobo-activat /tmp/orbit-gaurav/linc-1801-0-10d5c619ce239
unix  2      [ ACC ]     STREAM     LISTENING     19557    6161/trashapplet    /tmp/orbit-gaurav/linc-1811-0-5aa17ca7a63b8
unix  2      [ ACC ]     STREAM     LISTENING     19740    6172/mixer_applet2  /tmp/orbit-gaurav/linc-181c-0-493bd32eda2d5
unix  2      [ ACC ]     STREAM     LISTENING     19876    6179/fast-user-swit /tmp/orbit-gaurav/linc-1823-0-2748b55aee5a6
unix  2      [ ACC ]     STREAM     LISTENING     20325    6191/nm-applet      /tmp/orbit-gaurav/linc-182f-0-1812a1e6cb26a
unix  2      [ ACC ]     STREAM     LISTENING     20421    6187/update-notifie /tmp/orbit-gaurav/linc-182b-0-1da729d6dd3b1
unix  2      [ ACC ]     STREAM     LISTENING     20429    6209/gnome-power-ma /tmp/orbit-gaurav/linc-182d-0-1da729d6e0a9a
unix  2      [ ACC ]     STREAM     LISTENING     20582    6214/notification-d /tmp/orbit-gaurav/linc-1846-0-7b4db3d03f21f
unix  2      [ ACC ]     STREAM     LISTENING     20753    6196/cli            /tmp/orbit-gaurav/linc-1834-0-139732833f6
unix  2      [ ACC ]     STREAM     LISTENING     21407    6249/evolution-data /tmp/orbit-gaurav/linc-1869-0-2892832099160
unix  2      [ ACC ]     STREAM     LISTENING     21477    6254/evolution-exch /tmp/orbit-gaurav/linc-186e-0-71714b8639bd
unix  2      [ ACC ]     STREAM     LISTENING     89474    6034/pulseaudio     /tmp/pulse-gaurav/cli
unix  2      [ ACC ]     STREAM     LISTENING     15529    5190/chipcardd4     /var/run/chipcard/chipcard.comm
unix  2      [ ACC ]     STREAM     LISTENING     21850    6297/evolution-alar /tmp/orbit-gaurav/linc-1899-0-2249f0bcecbaa
unix  2      [ ACC ]     STREAM     LISTENING     65909    8489/rhythmbox      /tmp/orbit-gaurav/linc-2129-0-7842223ad3bf6
unix  2      [ ACC ]     STREAM     LISTENING     90771    9540/firefox        /tmp/orbit-gaurav/linc-2544-0-399800989886e
unix  2      [ ACC ]     STREAM     LISTENING     109298   11290/kdeinit4: kde /tmp/ksocket-gaurav/kdeinit4__0
unix  2      [ ACC ]     STREAM     LISTENING     109310   11293/klauncher     /tmp/ksocket-gaurav/klauncherT11293.slave-socket
unix  2      [ ACC ]     STREAM     LISTENING     241977   28751/pidgin        /tmp/orbit-gaurav/linc-704f-0-1391b9644a78
unix  2      [ ACC ]     STREAM     LISTENING     405487   5203/gnome-terminal /tmp/orbit-gaurav/linc-1453-0-5aff2213bcd2b
unix  2      [ ACC ]     STREAM     LISTENING     24806    6640/apache2        /var/run/apache2/cgisock.5556
unix  2      [ ACC ]     STREAM     LISTENING     16876    5409/gdm            /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     14832    4693/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     202490   5142/cupsd          /var/run/cups/cups.sock

---

### Post by gauravforyouall on 2009-04-30
let me try that also :( but why not hfs is working then, that file server works on the fly in windows and i have read in many posts that that works perfectly with "wine" but not in my case.

---

### Post by Monotoko on 2009-04-30
Okay, do not reinstall Apache2, iv just realized it really wont do much good. Instead run this and post the output

```
sudo iptables --list

```

---

### Post by gauravforyouall on 2009-04-30
Here it is... hope it will help anything
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.1.1          anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.1.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.3          192.168.1.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.1.3          192.168.1.1         udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere

---

### Post by Monotoko on 2009-04-30
Run this, tell me if it works, should make an exception on port 80:

```
iptables -I RH-Firewall-1-INPUT 3 -p tcp -m tcp --dport 80 --tcp-flags SYN,RST,ACK SYN -j ACCEPT
```

---

### Post by gauravforyouall on 2009-04-30
gaurav@Damaged:~$ sudo iptables -I RH-Firewall-1-INPUT 3 -p tcp -m tcp --dport 80 --tcp-flags SYN,RST,ACK SYN -j ACCEPT
iptables: No chain/target/match by that name




:( i never thought it could be too complicated

---

### Post by gauravforyouall on 2009-04-30
should i try flushing iptables?

---

### Post by Monotoko on 2009-04-30
To be honest, i really arnt sure, this a completly new area for me, and when im in a new area, best not to advise others on it before i try and break things myself.

What i would do, is post a new topic asking for help with iptables, you will get people that know about it that way, give them:

```
sudo iptables --list
``` and ```
gaurav@Damaged:~$ sudo iptables -I RH-Firewall-1-INPUT 3 -p tcp -m tcp --dport 80 --tcp-flags SYN,RST,ACK SYN -j ACCEPT
iptables: No chain/target/match by that name
```

and tell them you want it to allow you through port 80 for your webserver

Good luck, hope i helped, sorry i cant be of anymore help

---

### Post by gauravforyouall on 2009-04-30
thanks a lot.. ill google on iptables if i cldnt find anything great ill try posting here again... ill see if iptables could be of help in this case

---

### Post by gauravforyouall on 2009-04-30
yahoooooooooooooo yipiiiiiiiiiiiieeeeeeeeeeeeee
yahoooooooooooo
i have done it
i have done it
i have done it
i have done it
:)
:)
:)
 solution was very dumb
i am dumb i couldnot find it sorry guys wasted lot of time, in firestarter i rightclicked and clicked on accept incoming connections :| dont kill me Monotoko :(

---

