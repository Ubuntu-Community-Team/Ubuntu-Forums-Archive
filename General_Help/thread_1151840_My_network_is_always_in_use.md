---
title: "My network is always in use"
date: 2009-05-07
forum: General Help
---

### Post by sarsil on 2009-05-07
Hello! My internet connection is always in use. Ubuntu is downloading sometimes about 17kb/sec, 3kb/sec or sometimes more... But it downloads something everytime. I start to use 9.04 but the problem still on this version too... I didn't set any software to download something or update itself. I close all softwares but the problem still... Both of system monitor and conky writes that the connection is using. Also I open Ubuntu with KDE 4 but the same problem sill here... What should I do to solve the connection problem ? :confused:

---

### Post by sarsil on 2009-05-08
Can anyone helps me ?):P:confused:

---

### Post by cariboo on 2009-05-08
Open an Applications-->Accessories-->Terminal and type:

```
netstat tnlp
```

To check network activity.

---

### Post by greatgreatnathan on 2009-05-08
i am also new to to ubuntu... but shouldnt some packets be be sent and recieved at all times to maintain connection..?? or else the connection might be lost..!!! am i wrong:confused:

---

### Post by sarsil on 2009-05-08
[SIZE=3]netstat tnlp[/SIZE]      (my username is yusuf )

[SIZE=1]Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 yusuf-desktop.loc:35618 212.156.13.29:www       TIME_WAIT  
tcp        0      0 yusuf-desktop.loc:50014 fx-in-f113.google.c:www TIME_WAIT  
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ]         DGRAM                    3169     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    3397     @/org/kernel/udev/udevd
unix  2      [ ]         DGRAM                    6264     @/org/freedesktop/hal/udev_event
unix  3      [ ]         STREAM     CONNECTED     14301    
unix  3      [ ]         STREAM     CONNECTED     14300    
unix  3      [ ]         STREAM     CONNECTED     14294    @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     14293    
unix  3      [ ]         STREAM     CONNECTED     14292    /tmp/orbit-yusuf/linc-de1-0-34a1e7bb525b
unix  3      [ ]         STREAM     CONNECTED     14291    
unix  3      [ ]         STREAM     CONNECTED     14288    /tmp/orbit-yusuf/linc-c05-0-5b05ae44436e5
unix  3      [ ]         STREAM     CONNECTED     14287    
unix  3      [ ]         STREAM     CONNECTED     14283    @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     14282    
unix  3      [ ]         STREAM     CONNECTED     14281    /tmp/.ICE-unix/2974
unix  3      [ ]         STREAM     CONNECTED     14280    
unix  3      [ ]         STREAM     CONNECTED     14278    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14277    
unix  3      [ ]         STREAM     CONNECTED     11424    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11423    
unix  3      [ ]         STREAM     CONNECTED     11422    @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     11421    
unix  3      [ ]         STREAM     CONNECTED     11420    @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     11419    
unix  3      [ ]         STREAM     CONNECTED     11418    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11417    
unix  3      [ ]         STREAM     CONNECTED     11377    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11376    
unix  3      [ ]         STREAM     CONNECTED     11375    /tmp/orbit-yusuf/linc-cbb-0-708daffd6747f
unix  3      [ ]         STREAM     CONNECTED     11374    
unix  3      [ ]         STREAM     CONNECTED     11371    /tmp/orbit-yusuf/linc-c05-0-5b05ae44436e5
unix  3      [ ]         STREAM     CONNECTED     11370    
unix  3      [ ]         STREAM     CONNECTED     11365    @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     11364    
unix  3      [ ]         STREAM     CONNECTED     11363    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11362    
unix  3      [ ]         STREAM     CONNECTED     10865    @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     10864    
unix  3      [ ]         STREAM     CONNECTED     10861    /home/yusuf/.pulse/54aa936ddccb2953f89173754a01a9cf:runtime/native
unix  3      [ ]         STREAM     CONNECTED     10860    
unix  3      [ ]         STREAM     CONNECTED     10790    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10789    
unix  3      [ ]         STREAM     CONNECTED     10738    /tmp/orbit-yusuf/linc-c3e-0-504625eb2f0a8
unix  3      [ ]         STREAM     CONNECTED     10737    
unix  3      [ ]         STREAM     CONNECTED     10732    @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     10731    
unix  3      [ ]         STREAM     CONNECTED     10711    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10710    
unix  3      [ ]         STREAM     CONNECTED     10708    /tmp/.ICE-unix/2974
unix  3      [ ]         STREAM     CONNECTED     10707    
unix  3      [ ]         STREAM     CONNECTED     10709    /tmp/orbit-yusuf/linc-c3e-0-504625eb2f0a8
unix  3      [ ]         STREAM     CONNECTED     10706    
unix  3      [ ]         STREAM     CONNECTED     10697    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10696    
unix  3      [ ]         STREAM     CONNECTED     10695    @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     10694    
unix  3      [ ]         STREAM     CONNECTED     10692    /tmp/.ICE-unix/2974
unix  3      [ ]         STREAM     CONNECTED     10691    
unix  3      [ ]         STREAM     CONNECTED     10693    /tmp/orbit-yusuf/linc-c3e-0-504625eb2f0a8
unix  3      [ ]         STREAM     CONNECTED     10690    
unix  3      [ ]         STREAM     CONNECTED     10689    /tmp/orbit-yusuf/linc-c3e-0-504625eb2f0a8
unix  3      [ ]         STREAM     CONNECTED     10688    
unix  3      [ ]         STREAM     CONNECTED     10687    /tmp/orbit-yusuf/linc-c78-0-455ffe049093
unix  3      [ ]         STREAM     CONNECTED     10686    
unix  3      [ ]         STREAM     CONNECTED     10685    /tmp/orbit-yusuf/linc-c72-0-5f909250831d1
unix  3      [ ]         STREAM     CONNECTED     10684    
unix  3      [ ]         STREAM     CONNECTED     10683    /tmp/orbit-yusuf/linc-c7a-0-17b0ed035c26
unix  3      [ ]         STREAM     CONNECTED     10682    
unix  3      [ ]         STREAM     CONNECTED     10681    /tmp/orbit-yusuf/linc-c6d-0-1ab45d7d35b71
unix  3      [ ]         STREAM     CONNECTED     10680    
unix  3      [ ]         STREAM     CONNECTED     10546    /tmp/orbit-yusuf/linc-c43-0-606ff067249a2
unix  3      [ ]         STREAM     CONNECTED     10545    
unix  3      [ ]         STREAM     CONNECTED     10542    /tmp/orbit-yusuf/linc-c05-0-5b05ae44436e5
unix  3      [ ]         STREAM     CONNECTED     10541    
unix  4      [ ]         STREAM     CONNECTED     10538    @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     10537    
unix  3      [ ]         STREAM     CONNECTED     10532    @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     10531    
unix  3      [ ]         STREAM     CONNECTED     10528    @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     10527    
unix  3      [ ]         STREAM     CONNECTED     10463    @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     10462    
unix  3      [ ]         STREAM     CONNECTED     10243    @/dbus-vfs-daemon/socket-9japHObU
unix  3      [ ]         STREAM     CONNECTED     10242    
unix  3      [ ]         STREAM     CONNECTED     10241    @/dbus-vfs-daemon/socket-ebO6fyki
unix  3      [ ]         STREAM     CONNECTED     10240    
unix  3      [ ]         STREAM     CONNECTED     10237    @/dbus-vfs-daemon/socket-7UEI1B48
unix  3      [ ]         STREAM     CONNECTED     10236    
unix  3      [ ]         STREAM     CONNECTED     10235    @/dbus-vfs-daemon/socket-WFlEKpRV
unix  3      [ ]         STREAM     CONNECTED     10234    
unix  3      [ ]         STREAM     CONNECTED     10226    @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     10225    
unix  3      [ ]         STREAM     CONNECTED     10199    /tmp/orbit-yusuf/linc-c72-0-5f909250831d1
unix  3      [ ]         STREAM     CONNECTED     10198    
unix  3      [ ]         STREAM     CONNECTED     10197    /tmp/orbit-yusuf/linc-c05-0-5b05ae44436e5
unix  3      [ ]         STREAM     CONNECTED     10196    
unix  3      [ ]         STREAM     CONNECTED     10194    @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     10193    
unix  3      [ ]         STREAM     CONNECTED     10192    /tmp/orbit-yusuf/linc-c72-0-5f909250831d1
unix  3      [ ]         STREAM     CONNECTED     10191    
unix  3      [ ]         STREAM     CONNECTED     10190    /tmp/orbit-yusuf/linc-c41-0-5f01b195b7f5d
unix  3      [ ]         STREAM     CONNECTED     10187    
unix  3      [ ]         STREAM     CONNECTED     10183    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10182    
unix  3      [ ]         STREAM     CONNECTED     10178    @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     10177    
unix  3      [ ]         STREAM     CONNECTED     10174    /tmp/orbit-yusuf/linc-c78-0-455ffe049093
unix  3      [ ]         STREAM     CONNECTED     10173    
unix  3      [ ]         STREAM     CONNECTED     10172    /tmp/orbit-yusuf/linc-c7a-0-17b0ed035c26
unix  3      [ ]         STREAM     CONNECTED     10171    
unix  3      [ ]         STREAM     CONNECTED     10170    /tmp/orbit-yusuf/linc-c05-0-5b05ae44436e5
unix  3      [ ]         STREAM     CONNECTED     10169    
unix  3      [ ]         STREAM     CONNECTED     10168    /tmp/orbit-yusuf/linc-c05-0-5b05ae44436e5
unix  3      [ ]         STREAM     CONNECTED     10167    
unix  4      [ ]         STREAM     CONNECTED     10165    @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     10164    
unix  3      [ ]         STREAM     CONNECTED     10162    @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     10161    
unix  3      [ ]         STREAM     CONNECTED     10160    /tmp/orbit-yusuf/linc-c78-0-455ffe049093
unix  3      [ ]         STREAM     CONNECTED     10159    
unix  3      [ ]         STREAM     CONNECTED     10156    /tmp/orbit-yusuf/linc-c41-0-5f01b195b7f5d
unix  3      [ ]         STREAM     CONNECTED     10155    
unix  3      [ ]         STREAM     CONNECTED     10154    /tmp/orbit-yusuf/linc-c7a-0-17b0ed035c26
unix  3      [ ]         STREAM     CONNECTED     10153    
unix  3      [ ]         STREAM     CONNECTED     10149    /tmp/orbit-yusuf/linc-c6d-0-1ab45d7d35b71
unix  3      [ ]         STREAM     CONNECTED     10148    
unix  3      [ ]         STREAM     CONNECTED     10147    /tmp/orbit-yusuf/linc-c05-0-5b05ae44436e5
unix  3      [ ]         STREAM     CONNECTED     10146    
unix  4      [ ]         STREAM     CONNECTED     10144    @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     10143    
unix  3      [ ]         STREAM     CONNECTED     10142    /tmp/orbit-yusuf/linc-c6d-0-1ab45d7d35b71
unix  3      [ ]         STREAM     CONNECTED     10141    
unix  3      [ ]         STREAM     CONNECTED     10138    /tmp/orbit-yusuf/linc-c41-0-5f01b195b7f5d
unix  3      [ ]         STREAM     CONNECTED     10136    
unix  3      [ ]         STREAM     CONNECTED     10137    /tmp/orbit-yusuf/linc-c41-0-5f01b195b7f5d
unix  3      [ ]         STREAM     CONNECTED     10133    
unix  3      [ ]         STREAM     CONNECTED     10132    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10131    
unix  3      [ ]         STREAM     CONNECTED     10124    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10123    
unix  3      [ ]         STREAM     CONNECTED     9999     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9998     
unix  3      [ ]         STREAM     CONNECTED     9958     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9957     
unix  3      [ ]         STREAM     CONNECTED     9956     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9955     
unix  3      [ ]         STREAM     CONNECTED     9948     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9947     
unix  3      [ ]         STREAM     CONNECTED     9946     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9945     
unix  3      [ ]         STREAM     CONNECTED     9941     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9940     
unix  3      [ ]         STREAM     CONNECTED     9938     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9937     
unix  3      [ ]         STREAM     CONNECTED     9929     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9928     
unix  3      [ ]         STREAM     CONNECTED     9925     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9924     
unix  3      [ ]         STREAM     CONNECTED     9921     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9920     
unix  3      [ ]         STREAM     CONNECTED     9912     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9911     
unix  3      [ ]         STREAM     CONNECTED     9900     @/dbus-vfs-daemon/socket-Z9RFhKTO
unix  3      [ ]         STREAM     CONNECTED     9899     
unix  3      [ ]         STREAM     CONNECTED     9898     @/dbus-vfs-daemon/socket-gKTjUr69
unix  3      [ ]         STREAM     CONNECTED     9897     
unix  3      [ ]         STREAM     CONNECTED     9892     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9891     
unix  3      [ ]         STREAM     CONNECTED     9888     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9887     
unix  4      [ ]         STREAM     CONNECTED     9866     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9865     
unix  3      [ ]         STREAM     CONNECTED     9864     /tmp/orbit-yusuf/linc-c3e-0-504625eb2f0a8
unix  3      [ ]         STREAM     CONNECTED     9863     
unix  3      [ ]         STREAM     CONNECTED     9862     /tmp/orbit-yusuf/linc-c41-0-5f01b195b7f5d
unix  3      [ ]         STREAM     CONNECTED     9861     
unix  3      [ ]         STREAM     CONNECTED     9858     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9857     
unix  3      [ ]         STREAM     CONNECTED     9845     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9844     
unix  3      [ ]         STREAM     CONNECTED     9843     /tmp/orbit-yusuf/linc-c3f-0-5d3a81acd93dc
unix  3      [ ]         STREAM     CONNECTED     9842     
unix  3      [ ]         STREAM     CONNECTED     9839     /tmp/orbit-yusuf/linc-c05-0-5b05ae44436e5
unix  3      [ ]         STREAM     CONNECTED     9838     
unix  3      [ ]         STREAM     CONNECTED     9822     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9821     
unix  3      [ ]         STREAM     CONNECTED     9819     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9818     
unix  3      [ ]         STREAM     CONNECTED     9817     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9816     
unix  3      [ ]         STREAM     CONNECTED     9815     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9814     
unix  3      [ ]         STREAM     CONNECTED     9811     /tmp/orbit-yusuf/linc-c4a-0-27ecb993f997
unix  3      [ ]         STREAM     CONNECTED     9810     
unix  3      [ ]         STREAM     CONNECTED     9807     /tmp/orbit-yusuf/linc-c05-0-5b05ae44436e5
unix  3      [ ]         STREAM     CONNECTED     9806     
unix  3      [ ]         STREAM     CONNECTED     9802     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9801     
unix  3      [ ]         STREAM     CONNECTED     9738     /tmp/orbit-yusuf/linc-c4d-0-5a17466b38a14
unix  3      [ ]         STREAM     CONNECTED     9737     
unix  3      [ ]         STREAM     CONNECTED     9734     /tmp/orbit-yusuf/linc-c05-0-5b05ae44436e5
unix  3      [ ]         STREAM     CONNECTED     9733     
unix  3      [ ]         STREAM     CONNECTED     9729     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9728     
unix  3      [ ]         STREAM     CONNECTED     9724     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9723     
unix  3      [ ]         STREAM     CONNECTED     9665     /tmp/orbit-yusuf/linc-c49-0-46307b66f015c
unix  3      [ ]         STREAM     CONNECTED     9664     
unix  3      [ ]         STREAM     CONNECTED     9661     /tmp/orbit-yusuf/linc-c05-0-5b05ae44436e5
unix  3      [ ]         STREAM     CONNECTED     9660     
unix  3      [ ]         STREAM     CONNECTED     9655     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9654     
unix  3      [ ]         STREAM     CONNECTED     9799     /tmp/.ICE-unix/2974
unix  3      [ ]         STREAM     CONNECTED     9653     
unix  3      [ ]         STREAM     CONNECTED     9649     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9648     
unix  3      [ ]         STREAM     CONNECTED     9647     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9646     
unix  3      [ ]         STREAM     CONNECTED     9607     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9606     
unix  3      [ ]         STREAM     CONNECTED     9543     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9542     
unix  3      [ ]         STREAM     CONNECTED     9385     /tmp/.ICE-unix/2974
unix  3      [ ]         STREAM     CONNECTED     9384     
unix  3      [ ]         STREAM     CONNECTED     9382     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9381     
unix  3      [ ]         STREAM     CONNECTED     9309     /tmp/.ICE-unix/2974
unix  3      [ ]         STREAM     CONNECTED     9308     
unix  3      [ ]         STREAM     CONNECTED     9306     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9305     
unix  3      [ ]         STREAM     CONNECTED     9303     /tmp/orbit-yusuf/linc-c3e-0-504625eb2f0a8
unix  3      [ ]         STREAM     CONNECTED     9302     
unix  3      [ ]         STREAM     CONNECTED     9299     /tmp/orbit-yusuf/linc-c05-0-5b05ae44436e5
unix  3      [ ]         STREAM     CONNECTED     9298     
unix  3      [ ]         STREAM     CONNECTED     9296     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9295     
unix  3      [ ]         STREAM     CONNECTED     9291     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9290     
unix  3      [ ]         STREAM     CONNECTED     9258     /tmp/.ICE-unix/2974
unix  3      [ ]         STREAM     CONNECTED     9257     
unix  3      [ ]         STREAM     CONNECTED     9256     /tmp/orbit-yusuf/linc-c2a-0-772bd531bbcd
unix  3      [ ]         STREAM     CONNECTED     9255     
unix  3      [ ]         STREAM     CONNECTED     9252     /tmp/orbit-yusuf/linc-c05-0-5b05ae44436e5
unix  3      [ ]         STREAM     CONNECTED     9251     
unix  4      [ ]         STREAM     CONNECTED     9247     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9246     
unix  3      [ ]         STREAM     CONNECTED     9245     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9244     
unix  3      [ ]         STREAM     CONNECTED     9151     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9150     
unix  3      [ ]         STREAM     CONNECTED     9062     /tmp/orbit-yusuf/linc-b91-0-2f1694b185ac1
unix  3      [ ]         STREAM     CONNECTED     9061     
unix  3      [ ]         STREAM     CONNECTED     9058     /tmp/orbit-yusuf/linc-c05-0-5b05ae44436e5
unix  3      [ ]         STREAM     CONNECTED     9057     
unix  3      [ ]         STREAM     CONNECTED     9054     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9053     
unix  3      [ ]         STREAM     CONNECTED     9036     /tmp/orbit-yusuf/linc-c22-0-3d1a2e376f11e
unix  3      [ ]         STREAM     CONNECTED     9035     
unix  3      [ ]         STREAM     CONNECTED     9032     /tmp/orbit-yusuf/linc-c05-0-5b05ae44436e5
unix  3      [ ]         STREAM     CONNECTED     9031     
unix  3      [ ]         STREAM     CONNECTED     9024     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     9023     
unix  3      [ ]         STREAM     CONNECTED     8993     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8992     
unix  3      [ ]         STREAM     CONNECTED     8930     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     8929     
unix  3      [ ]         STREAM     CONNECTED     8925     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     8924     
unix  3      [ ]         STREAM     CONNECTED     8903     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8902     
unix  3      [ ]         STREAM     CONNECTED     8877     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     8876     
unix  3      [ ]         STREAM     CONNECTED     8873     /tmp/orbit-yusuf/linc-b9e-0-4541e23f8ad6a
unix  3      [ ]         STREAM     CONNECTED     8872     
unix  3      [ ]         STREAM     CONNECTED     8869     /tmp/orbit-yusuf/linc-c05-0-5b05ae44436e5
unix  3      [ ]         STREAM     CONNECTED     8868     
unix  3      [ ]         STREAM     CONNECTED     8858     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     8857     
unix  3      [ ]         STREAM     CONNECTED     8822     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     8821     
unix  3      [ ]         STREAM     CONNECTED     8819     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8818     
unix  3      [ ]         STREAM     CONNECTED     8794     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8793     
unix  3      [ ]         STREAM     CONNECTED     8786     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8785     
unix  3      [ ]         STREAM     CONNECTED     8763     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8762     
unix  3      [ ]         STREAM     CONNECTED     8761     /tmp/orbit-yusuf/linc-c03-0-98eaef25299a
unix  3      [ ]         STREAM     CONNECTED     8760     
unix  3      [ ]         STREAM     CONNECTED     8757     /tmp/orbit-yusuf/linc-c05-0-5b05ae44436e5
unix  3      [ ]         STREAM     CONNECTED     8756     
unix  3      [ ]         STREAM     CONNECTED     8750     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8749     
unix  3      [ ]         STREAM     CONNECTED     8567     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     8566     
unix  4      [ ]         STREAM     CONNECTED     8552     @/tmp/dbus-dJFhPXleV3
unix  3      [ ]         STREAM     CONNECTED     8551     
unix  3      [ ]         STREAM     CONNECTED     8512     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8511     
unix  3      [ ]         STREAM     CONNECTED     8498     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8497     
unix  3      [ ]         STREAM     CONNECTED     8496     
unix  3      [ ]         STREAM     CONNECTED     8495     
unix  4      [ ]         STREAM     CONNECTED     8481     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8480     
unix  3      [ ]         STREAM     CONNECTED     8217     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8216     
unix  3      [ ]         STREAM     CONNECTED     8205     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8204     
unix  3      [ ]         STREAM     CONNECTED     7849     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7848     
unix  4      [ ]         STREAM     CONNECTED     7943     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     7838     
unix  3      [ ]         STREAM     CONNECTED     7556     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7555     
unix  3      [ ]         STREAM     CONNECTED     7441     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7440     
unix  3      [ ]         STREAM     CONNECTED     7434     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7433     
unix  3      [ ]         STREAM     CONNECTED     7429     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7428     
unix  3      [ ]         STREAM     CONNECTED     7422     
unix  3      [ ]         STREAM     CONNECTED     7421     
unix  3      [ ]         STREAM     CONNECTED     7348     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7347     
unix  3      [ ]         STREAM     CONNECTED     7159     @/var/run/hald/dbus-URlis4hRY6
unix  3      [ ]         STREAM     CONNECTED     7157     
unix  3      [ ]         STREAM     CONNECTED     7158     @/var/run/hald/dbus-URlis4hRY6
unix  3      [ ]         STREAM     CONNECTED     7147     
unix  3      [ ]         STREAM     CONNECTED     7145     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7144     
unix  3      [ ]         STREAM     CONNECTED     6930     @/var/run/hald/dbus-URlis4hRY6
unix  3      [ ]         STREAM     CONNECTED     6392     
unix  3      [ ]         STREAM     CONNECTED     6259     @/var/run/hald/dbus-2CYDLoHxek
unix  3      [ ]         STREAM     CONNECTED     6258     
unix  3      [ ]         STREAM     CONNECTED     6236     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6235     
unix  3      [ ]         STREAM     CONNECTED     6221     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6220     
unix  3      [ ]         STREAM     CONNECTED     6168     
unix  3      [ ]         STREAM     CONNECTED     6167  [/SIZE]


[SIZE=3]What all that means ?:confused: (I write the command after I close all softwares which uses internet)[/SIZE]

---

