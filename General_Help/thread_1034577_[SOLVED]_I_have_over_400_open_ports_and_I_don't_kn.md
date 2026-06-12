---
title: "[SOLVED] I have over 400 open ports and I don't know why or how."
date: 2009-01-08
forum: General Help
---

### Post by needsleep on 2009-01-08
I'm running 8.04 and it recently started slowing down. I was just poking around and ran netstat and it showed over 400 ports open.They're opening up automatically on startup. Any insight into what's causing it and how to stop it would be appreciated. I've attached a representative sample of the netstat output. Thanks.

---

### Post by dcstar on 2009-01-08
> **needsleep said:**
> I'm running 8.04 and it recently started slowing down. I was just poking around and ran netstat and it showed over 400 ports open.They're opening up automatically on startup. Any insight into what's causing it and how to stop it would be appreciated. I've attached a representative sample of the netstat output. Thanks.

Firstly, no you didn't.

Secondly, open unix ports are not a problem, only TCP or UDP ports are any issue and only if you have a direct Internet connection.

---

### Post by needsleep on 2009-01-08
My attachment didn.t attach. Here's a sample:

unix  3      [ ]         STREAM     CONNECTED     22467    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     22466    
unix  3      [ ]         STREAM     CONNECTED     22465    /tmp/orbit-dad/linc-19bd-0-623373c46c645
unix  3      [ ]         STREAM     CONNECTED     22464    
unix  3      [ ]         STREAM     CONNECTED     22463    /tmp/orbit-dad/linc-1
996-0-7cbbd55c9263d
unix  3      [ ]         STREAM     CONNECTED     22242    
unix  3      [ ]         STREAM     CONNECTED     22238    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22237    
unix  3      [ ]         STREAM     CONNECTED     22084    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     22083    
unix  3      [ ]         STREAM     CONNECTED     22082    @/tmp/dbus-rwWwiLSFRK
unix  3      [ ]         STREAM     CONNECTED     22081    
unix  3      [ ]         STREAM     CONNECTED     22078    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     22077    
unix  3      [ ]         STREAM     CONNECTED     22063    /tmp/orbit-dad/linc-19bd-0-623373c46c645
a31-0-18a4f6ee910a3
unix  3      [ ]         STREAM     CONNECTED     22039    
unix  3      [ ]         STREAM     CONNECTED     22032    @/dbus-vfs-daemon/socket-akZPMgcS
unix  3      [ ]         STREAM     CONNECTED     15148    @/var/run/hald/dbus-VVe4DK16CA
unix  3      [ ]         STREAM     CONNECTED     15127    
unix  3      [ ]         STREAM     CONNECTED     14995    @/var/run/hald/dbus-7 
bus_socket
unix  3      [ ]         STREAM     CONNECTED     14509    
unix  3      [ ]         STREAM     CONNECTED     14482    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14481    
unix  2      [ ]         DGRAM                    14438

---

### Post by tuxxy on 2009-01-08
I think your getting mistaken with your network TCP and UDP ports and these for system.

---

### Post by amauk on 2009-01-08
All of those are [Unix domain sockets]("http://en.wikipedia.org/wiki/Unix_domain_socket")
and they're nothing to worry about

basically, they're special files on your file system
one program writes to the special file, another reads from it - it's a standard way for 2 processes to pass information between them

You can tell they're Unix domain sockets, as the first entry is "unix"
Internet sockets are different, and the first entry is "tcp"

to filter the results of netstat to only show internet sockets, use
```
netstat --tcp
```

---

### Post by cdtech on 2009-01-08
That's right....
If you use "netstat -l | more" you'll see the actual internet connections:
```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:ipp           *:*                     LISTEN     
udp        0      0 *:47709                 *:*                                
udp        0      0 *:mdns                  *:* 
```

---

### Post by needsleep on 2009-01-08
Thanks

---

### Post by needsleep on 2009-01-08
> **amauk said:**
> All of those are [Unix domain sockets]("http://en.wikipedia.org/wiki/Unix_domain_socket")
and they're nothing to worry about

basically, they're special files on your file system
one program writes to the special file, another reads from it - it's a standard way for 2 processes to pass information between them

You can tell they're Unix domain sockets, as the first entry is "unix"
Internet sockets are different, and the first entry is "tcp"

to filter the results of netstat to only show internet sockets, use
```
netstat --tcp
```

Thanks

---

