---
title: "Error 530 when trying to connect to my ftp"
date: 2009-03-25
forum: General Help
---

### Post by jasballz on 2009-03-25
I had an anonymous user on IRC try to connect to my laptop via vsftpd. I'm trying to host Buddhabuntu Beta I on an ftp IP address and he got error 530 / permsission denied. My netstat output and vsftpd output:


 Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:9091                  *:*                     LISTEN     
tcp        0      0 *:51413                 *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0     51 jonathan-laptop.l:41299 ppp-79-111-65-251:42000 ESTABLISHED
tcp        0      0 jonathan-laptop.l:43009 static.unknown.ch:49156 ESTABLISHED
tcp        0      0 jonathan-laptop.l:38460 66-215-51-52.dhcp:26406 ESTABLISHED
tcp        0      0 jonathan-laptop.l:49323 cm31.psi160.maxon:29520 ESTABLISHED
tcp        0      0 jonathan-laptop.l:34711 82.131.69.93.cabl:11500 ESTABLISHED
tcp        0      0 jonathan-laptop.l:58537 bartol.freenode.ne:ircd ESTABLISHED
tcp        0      0 jonathan-laptop.l:37546 S010600e04cbb4674:42151 ESTABLISHED
tcp        0  13032 jonathan-laptop.l:55321 201-236-40-136.sta:9090 ESTABLISHED
tcp        0  39472 jonathan-laptop.l:37422 FL1-118-111-19-40:24538 ESTABLISHED
tcp        0    374 jonathan-laptop.l:50729 115-64-124-131.tp:47053 ESTABLISHED
tcp        0      0 jonathan-laptop.l:45713 a91-153-122-150.e:50071 ESTABLISHED
tcp        0      0 jonathan-laptop.l:39880 clarke.freenode.ne:8001 ESTABLISHED
tcp        0     17 jonathan-laptop.l:47982 bd66aa75.virtua.c:41978 ESTABLISHED
tcp        0  54808 jonathan-laptop.l:50137 c213-100-17-197.s:52280 ESTABLISHED
tcp        0      0 jonathan-laptop.l:48198 122-49-177-233.ip:54268 ESTABLISHED
tcp        0      0 jonathan-laptop.l:34755 c-24-16-218-154.h:64180 ESTABLISHED
tcp        0      0 jonathan-laptop.l:51053 202-189.106-97.ta:26816 ESTABLISHED
tcp        0      0 jonathan-laptop.l:57787 99-156-87-121.ligh:6881 ESTABLISHED
tcp        0      0 jonathan-laptop.l:47139 ip68-231-3-145.ph:49152 ESTABLISHED
...
unix  3      [ ]         STREAM     CONNECTED     12597    
unix  3      [ ]         STREAM     CONNECTED     12590    /tmp/orbit-jonathan/linc-c48-0-fc94ba58b438
unix  3      [ ]         STREAM     CONNECTED     12589    
unix  3      [ ]         STREAM     CONNECTED     12577    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12576    
unix  3      [ ]         STREAM     CONNECTED     12575    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     12574    
unix  3      [ ]         STREAM     CONNECTED     12573    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     12572    
unix  3      [ ]         STREAM     CONNECTED     12570    /tmp/.ICE-unix/2974
unix  3      [ ]         STREAM     CONNECTED     12569    
unix  3      [ ]         STREAM     CONNECTED     12571    /tmp/orbit-jonathan/linc-c48-0-fc94ba58b438
unix  3      [ ]         STREAM     CONNECTED     12568    
unix  3      [ ]         STREAM     CONNECTED     12546    /tmp/orbit-jonathan/linc-c48-0-fc94ba58b438
unix  3      [ ]         STREAM     CONNECTED     12545    
unix  3      [ ]         STREAM     CONNECTED     12539    /tmp/orbit-jonathan/linc-cc4-0-79f6b43f96ba3
unix  3      [ ]         STREAM     CONNECTED     12538    
unix  3      [ ]         STREAM     CONNECTED     12540    /tmp/orbit-jonathan/linc-cc1-0-41903416ec291
unix  3      [ ]         STREAM     CONNECTED     12537    
unix  3      [ ]         STREAM     CONNECTED     12541    /tmp/orbit-jonathan/linc-cbb-0-74375a4ea4935
unix  3      [ ]         STREAM     CONNECTED     12536    
unix  3      [ ]         STREAM     CONNECTED     12542    /tmp/orbit-jonathan/linc-cba-0-23db56b1943a9
unix  3      [ ]         STREAM     CONNECTED     12535    
unix  3      [ ]         STREAM     CONNECTED     12543    /tmp/orbit-jonathan/linc-cbe-0-1a5bd9d384f3c
unix  3      [ ]         STREAM     CONNECTED     12534    
unix  3      [ ]         STREAM     CONNECTED     12544    /tmp/orbit-jonathan/linc-cc8-0-1b3d1a0f840bd
unix  3      [ ]         STREAM     CONNECTED     12533    
unix  2      [ ]         DGRAM                    12520    
unix  3      [ ]         STREAM     CONNECTED     12281    /tmp/orbit-jonathan/linc-cd4-0-3520d46ed1c06
unix  3      [ ]         STREAM     CONNECTED     12280    
unix  3      [ ]         STREAM     CONNECTED     12277    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     12276    
unix  4      [ ]         STREAM     CONNECTED     12271    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     12270    
unix  3      [ ]         STREAM     CONNECTED     12269    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12268    
unix  3      [ ]         STREAM     CONNECTED     12046    @/dbus-vfs-daemon/socket-LVJFWgNE
unix  3      [ ]         STREAM     CONNECTED     12045    
unix  3      [ ]         STREAM     CONNECTED     12044    @/dbus-vfs-daemon/socket-0AIyJTth
unix  3      [ ]         STREAM     CONNECTED     12043    
unix  3      [ ]         STREAM     CONNECTED     12035    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     12034    
unix  3      [ ]         STREAM     CONNECTED     12032    /tmp/orbit-jonathan/linc-cc1-0-41903416ec291
unix  3      [ ]         STREAM     CONNECTED     12031    
unix  3      [ ]         STREAM     CONNECTED     12030    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     12029    
unix  3      [ ]         STREAM     CONNECTED     12027    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     12026    
unix  3      [ ]         STREAM     CONNECTED     12025    /tmp/orbit-jonathan/linc-cc1-0-41903416ec291
unix  3      [ ]         STREAM     CONNECTED     12024    
unix  3      [ ]         STREAM     CONNECTED     12021    /tmp/orbit-jonathan/linc-c4b-0-e11c6a825cd2
unix  3      [ ]         STREAM     CONNECTED     12020    
unix  3      [ ]         STREAM     CONNECTED     12016    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12015    
unix  3      [ ]         STREAM     CONNECTED     11992    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11991    
unix  3      [ ]         STREAM     CONNECTED     11990    /tmp/orbit-jonathan/linc-cbb-0-74375a4ea4935
unix  3      [ ]         STREAM     CONNECTED     11989    
unix  3      [ ]         STREAM     CONNECTED     11988    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     11987    
unix  4      [ ]         STREAM     CONNECTED     11985    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11984    
unix  3      [ ]         STREAM     CONNECTED     11983    /tmp/orbit-jonathan/linc-cbb-0-74375a4ea4935
unix  3      [ ]         STREAM     CONNECTED     11982    
unix  3      [ ]         STREAM     CONNECTED     11979    /tmp/orbit-jonathan/linc-c4b-0-e11c6a825cd2
unix  3      [ ]         STREAM     CONNECTED     11978    
unix  3      [ ]         STREAM     CONNECTED     11974    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11973    
unix  3      [ ]         STREAM     CONNECTED     11969    /tmp/orbit-jonathan/linc-cc4-0-79f6b43f96ba3
unix  3      [ ]         STREAM     CONNECTED     11968    
unix  3      [ ]         STREAM     CONNECTED     11967    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     11966    
unix  4      [ ]         STREAM     CONNECTED     11964    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11963    
unix  3      [ ]         STREAM     CONNECTED     11962    /tmp/orbit-jonathan/linc-cc4-0-79f6b43f96ba3
unix  3      [ ]         STREAM     CONNECTED     11961    
unix  3      [ ]         STREAM     CONNECTED     11958    /tmp/orbit-jonathan/linc-c4b-0-e11c6a825cd2
unix  3      [ ]         STREAM     CONNECTED     11957    
unix  3      [ ]         STREAM     CONNECTED     11953    /tmp/orbit-jonathan/linc-cba-0-23db56b1943a9
unix  3      [ ]         STREAM     CONNECTED     11952    
unix  3      [ ]         STREAM     CONNECTED     11951    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     11950    
unix  4      [ ]         STREAM     CONNECTED     11948    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11947    
unix  3      [ ]         STREAM     CONNECTED     11946    /tmp/orbit-jonathan/linc-cba-0-23db56b1943a9
unix  3      [ ]         STREAM     CONNECTED     11945    
unix  3      [ ]         STREAM     CONNECTED     11942    /tmp/orbit-jonathan/linc-c4b-0-e11c6a825cd2
unix  3      [ ]         STREAM     CONNECTED     11941    
unix  3      [ ]         STREAM     CONNECTED     11937    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11935    
unix  3      [ ]         STREAM     CONNECTED     11936    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11932    
unix  3      [ ]         STREAM     CONNECTED     11929    /tmp/orbit-jonathan/linc-cc8-0-1b3d1a0f840bd
unix  3      [ ]         STREAM     CONNECTED     11928    
unix  3      [ ]         STREAM     CONNECTED     11927    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     11926    
unix  3      [ ]         STREAM     CONNECTED     11923    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11922    
unix  3      [ ]         STREAM     CONNECTED     11921    /tmp/orbit-jonathan/linc-cbe-0-1a5bd9d384f3c
unix  3      [ ]         STREAM     CONNECTED     11920    
unix  3      [ ]         STREAM     CONNECTED     11919    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     11918    
unix  3      [ ]         STREAM     CONNECTED     11916    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11915    
unix  3      [ ]         STREAM     CONNECTED     11913    /tmp/orbit-jonathan/linc-cbe-0-1a5bd9d384f3c
unix  3      [ ]         STREAM     CONNECTED     11911    
unix  3      [ ]         STREAM     CONNECTED     11908    /tmp/orbit-jonathan/linc-c4b-0-e11c6a825cd2
unix  3      [ ]         STREAM     CONNECTED     11907    
unix  3      [ ]         STREAM     CONNECTED     11912    /tmp/orbit-jonathan/linc-cc8-0-1b3d1a0f840bd
unix  3      [ ]         STREAM     CONNECTED     11903    
unix  3      [ ]         STREAM     CONNECTED     11900    /tmp/orbit-jonathan/linc-c4b-0-e11c6a825cd2
unix  3      [ ]         STREAM     CONNECTED     11899    
unix  3      [ ]         STREAM     CONNECTED     11894    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11893    
unix  3      [ ]         STREAM     CONNECTED     11892    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11891    
unix  3      [ ]         STREAM     CONNECTED     11594    @/dbus-vfs-daemon/socket-5pOof9dz
unix  3      [ ]         STREAM     CONNECTED     11593    
unix  3      [ ]         STREAM     CONNECTED     11592    @/dbus-vfs-daemon/socket-qIgMF3Zf
unix  3      [ ]         STREAM     CONNECTED     11591    
unix  3      [ ]         STREAM     CONNECTED     11586    @/dbus-vfs-daemon/socket-8RoRMkk8
unix  3      [ ]         STREAM     CONNECTED     11585    
unix  3      [ ]         STREAM     CONNECTED     11584    @/dbus-vfs-daemon/socket-LWQggkNA
unix  3      [ ]         STREAM     CONNECTED     11583    
unix  3      [ ]         STREAM     CONNECTED     11580    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11579    
unix  3      [ ]         STREAM     CONNECTED     11575    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11574    
unix  3      [ ]         STREAM     CONNECTED     11573    /tmp/orbit-jonathan/linc-c48-0-fc94ba58b438
unix  3      [ ]         STREAM     CONNECTED     11572    
unix  3      [ ]         STREAM     CONNECTED     11571    /tmp/orbit-jonathan/linc-caa-0-6efa209d2ccb
unix  3      [ ]         STREAM     CONNECTED     11570    
unix  3      [ ]         STREAM     CONNECTED     11569    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11568    
unix  3      [ ]         STREAM     CONNECTED     11565    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11564    
unix  3      [ ]         STREAM     CONNECTED     11556    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11555    
unix  3      [ ]         STREAM     CONNECTED     11552    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11551    
unix  3      [ ]         STREAM     CONNECTED     11549    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11548    
unix  3      [ ]         STREAM     CONNECTED     11533    @/dbus-vfs-daemon/socket-MrgGvdIv
unix  3      [ ]         STREAM     CONNECTED     11532    
unix  3      [ ]         STREAM     CONNECTED     11534    @/dbus-vfs-daemon/socket-WAlYTjtn
unix  3      [ ]         STREAM     CONNECTED     11531    
unix  3      [ ]         STREAM     CONNECTED     11524    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11523    
unix  3      [ ]         STREAM     CONNECTED     11519    @/dbus-vfs-daemon/socket-yXhVCcUy
unix  3      [ ]         STREAM     CONNECTED     11518    
unix  3      [ ]         STREAM     CONNECTED     11520    @/dbus-vfs-daemon/socket-d90r4rCB
unix  3      [ ]         STREAM     CONNECTED     11517    
unix  3      [ ]         STREAM     CONNECTED     11512    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11511    
unix  3      [ ]         STREAM     CONNECTED     11508    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11507    
unix  4      [ ]         STREAM     CONNECTED     11486    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11485    
unix  3      [ ]         STREAM     CONNECTED     11484    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11483    
unix  3      [ ]         STREAM     CONNECTED     11482    /tmp/orbit-jonathan/linc-caa-0-6efa209d2ccb
unix  3      [ ]         STREAM     CONNECTED     11481    
unix  3      [ ]         STREAM     CONNECTED     11480    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     11479    
unix  4      [ ]         STREAM     CONNECTED     11477    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11476    
unix  3      [ ]         STREAM     CONNECTED     11475    /tmp/orbit-jonathan/linc-caa-0-6efa209d2ccb
unix  3      [ ]         STREAM     CONNECTED     11474    
unix  3      [ ]         STREAM     CONNECTED     11473    /tmp/orbit-jonathan/linc-c4b-0-e11c6a825cd2
unix  3      [ ]         STREAM     CONNECTED     11470    
unix  3      [ ]         STREAM     CONNECTED     11466    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11465    
unix  3      [ ]         STREAM     CONNECTED     11317    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11316    
unix  3      [ ]         STREAM     CONNECTED     11254    /tmp/orbit-jonathan/linc-c48-0-fc94ba58b438
unix  3      [ ]         STREAM     CONNECTED     11253    
unix  3      [ ]         STREAM     CONNECTED     11250    /tmp/orbit-jonathan/linc-c4b-0-e11c6a825cd2
unix  3      [ ]         STREAM     CONNECTED     11249    
unix  3      [ ]         STREAM     CONNECTED     11246    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11245    
unix  3      [ ]         STREAM     CONNECTED     11215    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11214    
unix  3      [ ]         STREAM     CONNECTED     11190    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11189    
unix  3      [ ]         STREAM     CONNECTED     11188    /tmp/orbit-jonathan/linc-c64-0-db501aed865f
unix  3      [ ]         STREAM     CONNECTED     11187    
unix  3      [ ]         STREAM     CONNECTED     11184    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     11183    
unix  3      [ ]         STREAM     CONNECTED     11179    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11178    
unix  3      [ ]         STREAM     CONNECTED     11176    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11175    
unix  3      [ ]         STREAM     CONNECTED     11166    /tmp/orbit-jonathan/linc-c59-0-58f74585a2ee3
unix  3      [ ]         STREAM     CONNECTED     11165    
unix  3      [ ]         STREAM     CONNECTED     11162    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     11161    
unix  3      [ ]         STREAM     CONNECTED     11156    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11155    
unix  3      [ ]         STREAM     CONNECTED     11152    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11151    
unix  3      [ ]         STREAM     CONNECTED     11148    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11147    
unix  3      [ ]         STREAM     CONNECTED     11137    /tmp/orbit-jonathan/linc-c49-0-69edb92c69079
unix  3      [ ]         STREAM     CONNECTED     11136    
unix  3      [ ]         STREAM     CONNECTED     11133    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     11132    
unix  3      [ ]         STREAM     CONNECTED     11128    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11127    
unix  3      [ ]         STREAM     CONNECTED     11121    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11120    
unix  3      [ ]         STREAM     CONNECTED     11119    /tmp/orbit-jonathan/linc-c51-0-68bf5f7352702
unix  3      [ ]         STREAM     CONNECTED     11118    
unix  3      [ ]         STREAM     CONNECTED     11115    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     11114    
unix  3      [ ]         STREAM     CONNECTED     11112    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11111    
unix  3      [ ]         STREAM     CONNECTED     11110    /tmp/.ICE-unix/2974
unix  3      [ ]         STREAM     CONNECTED     11109    
unix  3      [ ]         STREAM     CONNECTED     11105    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11104    
unix  3      [ ]         STREAM     CONNECTED     11100    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11099    
unix  3      [ ]         STREAM     CONNECTED     11092    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11091    
unix  3      [ ]         STREAM     CONNECTED     11090    /tmp/orbit-jonathan/linc-c50-0-68bf5f733a814
unix  3      [ ]         STREAM     CONNECTED     11089    
unix  3      [ ]         STREAM     CONNECTED     11086    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     11085    
unix  3      [ ]         STREAM     CONNECTED     11083    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     11082    
unix  3      [ ]         STREAM     CONNECTED     11081    /tmp/.ICE-unix/2974
unix  3      [ ]         STREAM     CONNECTED     10893    
unix  3      [ ]         STREAM     CONNECTED     10889    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10888    
unix  3      [ ]         STREAM     CONNECTED     10818    /tmp/orbit-jonathan/linc-c4e-0-1d9e03ed7524
unix  3      [ ]         STREAM     CONNECTED     10817    
unix  3      [ ]         STREAM     CONNECTED     10814    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     10813    
unix  3      [ ]         STREAM     CONNECTED     10809    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10808    
unix  3      [ ]         STREAM     CONNECTED     10806    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     10805    
unix  3      [ ]         STREAM     CONNECTED     10804    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10803    
unix  3      [ ]         STREAM     CONNECTED     10673    /tmp/.ICE-unix/2974
unix  3      [ ]         STREAM     CONNECTED     10672    
unix  3      [ ]         STREAM     CONNECTED     10670    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10669    
unix  3      [ ]         STREAM     CONNECTED     10597    /tmp/.ICE-unix/2974
unix  3      [ ]         STREAM     CONNECTED     10596    
unix  3      [ ]         STREAM     CONNECTED     10595    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     10594    
unix  3      [ ]         STREAM     CONNECTED     10592    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     10591    
unix  3      [ ]         STREAM     CONNECTED     10590    /tmp/orbit-jonathan/linc-c47-0-3e093f415440b
unix  3      [ ]         STREAM     CONNECTED     10589    
unix  3      [ ]         STREAM     CONNECTED     10586    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     10585    
unix  3      [ ]         STREAM     CONNECTED     10577    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     10576    
unix  3      [ ]         STREAM     CONNECTED     10574    /tmp/orbit-jonathan/linc-c48-0-fc94ba58b438
unix  3      [ ]         STREAM     CONNECTED     10573    
unix  3      [ ]         STREAM     CONNECTED     10570    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     10569    
unix  3      [ ]         STREAM     CONNECTED     10567    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     10566    
unix  3      [ ]         STREAM     CONNECTED     10562    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10561    
unix  3      [ ]         STREAM     CONNECTED     10557    @/tmp/.X11-unix/X0
unix  23     [ ]         STREAM     CONNECTED     10556    
unix  3      [ ]         STREAM     CONNECTED     10527    /tmp/.ICE-unix/2974
unix  3      [ ]         STREAM     CONNECTED     10526    
unix  3      [ ]         STREAM     CONNECTED     10374    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     10373    
unix  3      [ ]         STREAM     CONNECTED     10284    /tmp/orbit-jonathan/linc-b91-0-383dc77f3f1f1
unix  3      [ ]         STREAM     CONNECTED     10283    
unix  3      [ ]         STREAM     CONNECTED     10280    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     10279    
unix  3      [ ]         STREAM     CONNECTED     10276    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     10275    
unix  3      [ ]         STREAM     CONNECTED     10263    /tmp/orbit-jonathan/linc-c01-0-a3f396b36575
unix  3      [ ]         STREAM     CONNECTED     10262    
unix  3      [ ]         STREAM     CONNECTED     10259    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     10258    
unix  3      [ ]         STREAM     CONNECTED     10250    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     10249    
unix  3      [ ]         STREAM     CONNECTED     10242    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10241    
unix  3      [ ]         STREAM     CONNECTED     10156    /tmp/orbit-jonathan/linc-bf0-0-536813cbba9cb
unix  3      [ ]         STREAM     CONNECTED     10155    
unix  3      [ ]         STREAM     CONNECTED     10152    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     10151    
unix  4      [ ]         STREAM     CONNECTED     10145    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     10144    
unix  3      [ ]         STREAM     CONNECTED     10142    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10141    
unix  3      [ ]         STREAM     CONNECTED     10138    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     10137    
unix  3      [ ]         STREAM     CONNECTED     10133    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     10132    
unix  3      [ ]         STREAM     CONNECTED     10091    /tmp/orbit-jonathan/linc-b9e-0-11be31a2678c8
unix  3      [ ]         STREAM     CONNECTED     10090    
unix  3      [ ]         STREAM     CONNECTED     10087    /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     10086    
unix  3      [ ]         STREAM     CONNECTED     10080    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     10079    
unix  3      [ ]         STREAM     CONNECTED     10037    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     10036    
unix  3      [ ]         STREAM     CONNECTED     10034    @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     10033    
unix  3      [ ]         STREAM     CONNECTED     10031    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10030    
unix  3      [ ]         STREAM     CONNECTED     10005    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10004    
unix  3      [ ]         STREAM     CONNECTED     9997     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9996     
unix  3      [ ]         STREAM     CONNECTED     9977     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9976     
unix  3      [ ]         STREAM     CONNECTED     9975     /tmp/orbit-jonathan/linc-be3-0-7dbfca8b747bb
unix  3      [ ]         STREAM     CONNECTED     9974     
unix  3      [ ]         STREAM     CONNECTED     9971     /tmp/orbit-jonathan/linc-be5-0-522e14045de68
unix  3      [ ]         STREAM     CONNECTED     9970     
unix  3      [ ]         STREAM     CONNECTED     9964     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9963     
unix  3      [ ]         STREAM     CONNECTED     9653     @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     9652     
unix  4      [ ]         STREAM     CONNECTED     9638     @/tmp/dbus-Q3Clqrve9B
unix  3      [ ]         STREAM     CONNECTED     9637     
unix  3      [ ]         STREAM     CONNECTED     9598     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9597     
unix  3      [ ]         STREAM     CONNECTED     9584     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9583     
unix  3      [ ]         STREAM     CONNECTED     9582     
unix  3      [ ]         STREAM     CONNECTED     9581     
unix  4      [ ]         STREAM     CONNECTED     9568     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9567     
unix  2      [ ]         DGRAM                    9441     
unix  3      [ ]         STREAM     CONNECTED     9348     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9347     
unix  3      [ ]         STREAM     CONNECTED     9266     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9265     
unix  4      [ ]         STREAM     CONNECTED     8966     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8961     
unix  3      [ ]         STREAM     CONNECTED     8960     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8959     
unix  3      [ ]         STREAM     CONNECTED     7907     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7906     
unix  2      [ ]         DGRAM                    7795     
unix  2      [ ]         DGRAM                    7794     
unix  3      [ ]         STREAM     CONNECTED     7793     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7792     
unix  3      [ ]         STREAM     CONNECTED     7787     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7786     
unix  3      [ ]         STREAM     CONNECTED     7738     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7737     
unix  3      [ ]         STREAM     CONNECTED     7714     
unix  3      [ ]         STREAM     CONNECTED     7713     
unix  2      [ ]         DGRAM                    7711     
unix  3      [ ]         STREAM     CONNECTED     7652     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7651     
unix  2      [ ]         DGRAM                    7648     
unix  3      [ ]         STREAM     CONNECTED     7604     /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     7603     
unix  3      [ ]         STREAM     CONNECTED     7448     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7447     
unix  2      [ ]         DGRAM                    7444     
unix  2      [ ]         DGRAM                    7386     
unix  3      [ ]         STREAM     CONNECTED     7385     /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     7384     
unix  3      [ ]         STREAM     CONNECTED     7376     @/var/run/hald/dbus-S7F1Fe8JBh
unix  3      [ ]         STREAM     CONNECTED     7374     
unix  3      [ ]         STREAM     CONNECTED     7370     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7369     
unix  3      [ ]         STREAM     CONNECTED     7368     @/var/run/hald/dbus-S7F1Fe8JBh
unix  3      [ ]         STREAM     CONNECTED     7357     
unix  3      [ ]         STREAM     CONNECTED     7334     @/var/run/hald/dbus-S7F1Fe8JBh
unix  3      [ ]         STREAM     CONNECTED     7333     
unix  3      [ ]         STREAM     CONNECTED     7331     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7330     
unix  3      [ ]         STREAM     CONNECTED     7186     @/var/run/hald/dbus-S7F1Fe8JBh
unix  3      [ ]         STREAM     CONNECTED     7104     
unix  3      [ ]         STREAM     CONNECTED     7185     @/var/run/hald/dbus-S7F1Fe8JBh
unix  3      [ ]         STREAM     CONNECTED     7094     
unix  3      [ ]         STREAM     CONNECTED     7171     @/var/run/hald/dbus-S7F1Fe8JBh
unix  3      [ ]         STREAM     CONNECTED     7027     
unix  3      [ ]         STREAM     CONNECTED     7165     @/var/run/hald/dbus-S7F1Fe8JBh
unix  3      [ ]         STREAM     CONNECTED     6859     
unix  3      [ ]         STREAM     CONNECTED     6737     @/var/run/hald/dbus-0mkCHm0dzW
unix  3      [ ]         STREAM     CONNECTED     6736     
unix  3      [ ]         STREAM     CONNECTED     6714     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6713     
unix  3      [ ]         STREAM     CONNECTED     6700     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6699     
unix  3      [ ]         STREAM     CONNECTED     6692     
unix  3      [ ]         STREAM     CONNECTED     6691     
unix  3      [ ]         STREAM     CONNECTED     6522     
unix  3      [ ]         STREAM     CONNECTED     6521     
unix  2      [ ]         DGRAM                    6477  

# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
#local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
#write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
#ftpd_banner=Welcome to blah FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
#chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
#
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=ftp
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

check_shell=NO




**Where I'm at right now enables portforwarding tho I am interested in modding so I can remain live at a University Campus with ISP no open ports / encryption / firewall once I'm live here I will mod there

---

### Post by jasballz on 2009-03-25
i am a complete newb to ftp hosting so any help is appreciated.

namaste

---

### Post by LiQuidAiR on 2009-04-26
I'm also getting the same error.  I have ubuntu 8.10 server.  Using VSFTPD.  Under Pam authentication.  I think my issue is a result of how VSFTPD is using PAM.  But I have no idea how to prove this.

Does this match your setup?

What are you system specs?  Maybe we can compare notes and solve this.

---

