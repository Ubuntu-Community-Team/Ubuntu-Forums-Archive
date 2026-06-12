---
title: "uShare UPnP A/V &amp; DLNA Media Server"
date: 2009-03-07
forum: General Help
---

### Post by linux newb on 2009-03-07
Ok i had this server setup and working for both ps3 and xbox and it was working great when i first set it up and then the movies started laggingthen the sexbox downstairs just doesnt even get the signal anymore. mine did up in my room up until now, and it all started happening when i changed the config file up because the movies started screwin up. this is what i changed.

Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0

to

Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0

USHARE_IFACE=eth1

i did this because my mother board (asus striker 2 formula) supports dual ethernet connections, and in windows with the software and drivers installed there was an option to enable connection teaming to double bandwidth. also wondering if this is possible in linux, but any way my little green globe in my sys tray tells me that both eth0 and eth1 are active, my router tells me only one of the connections is active and the light is continuously blinking, and it shows the other is connected but is a solid light. now i tried this little tweak in the config file and it seemed to work and fix the video lag while streaming to the ps3(i only stream to one machine at a time because it only works that way), but if i try to then stream to the sexbox, it doesnt see it with miy little tweak, i untweak it, ity sees it, but now nothing sees nothing because when i just tried to retweak it today for ps3 and tried to start it up and it said it was ok, ps3 saw it and couldnt access it, tried the sexboxes, same thing saw it, couldnt access it, tried all three untweaked, again same thing. then i noticed something when i stopped the server to edit the conf. file. it gave me these two messages:

when i started up the server:
ron@ron-desktop:~$ sudo /etc/init.d/ushare start
 * Starting uShare UPnP A/V & DLNA Media Server: ushare [ OK ]
ron@ron-desktop:~$

so that looks okay right? look at this

ron@ron-desktop:~$ sudo /etc/init.d/ushare stop
 * Stopping uShare UPnP A/V & DLNA Media Server: ushare
start-stop-daemon: warning: failed to kill 7585: No such process
                                                                                       
ron@ron-desktop:~$

like, did the program just fall apart and stop working? really confused as to why it would just tells me that it started up ok but when i try to shut it down it says that proccess isnt even running.

can anybody help me plz?

---

### Post by linux newb on 2009-03-08
bump

---

### Post by linux newb on 2009-03-11
k well can anybody tell me howto uninstall it?

---

