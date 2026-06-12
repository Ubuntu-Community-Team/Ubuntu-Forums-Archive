---
title: "Who is using the caches and why?"
date: 2013-02-17
forum: Desktop Environments
---

### Post by RuralHunter on 2013-02-17
I'm on ubuntu 12.10 64bit desktop with all latest updates installed. This happens 2 times today: swap usage increased very quickly in around 10 mins and finally OOM killer killed nautilus and compiz. I tried to close all memory consuming apps such as firefox and some java applications during the swap usage increasing but it didn't help. everything backed to normal after nautilus and compiz were killed and restarted.

I have 10G mem and swap. Here is some monitoring stats after I closed all mem consuming apps:
```
$ free
             total       used       free     shared    buffers     cached
Mem:      10153356   10014728     138628          0      59044    8340668
-/+ buffers/cache:    1615016    8538340
Swap:     10394620    5513340    4881280

```

The used buffers in above command is only between 2-3G even when all those mem consuming apps running.
vmstat during swap usage increasing(after above free command) and OOM killer involved:
```
$ vmstat 3
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 1  0 6195628 146832  57348 8266692    0  163    53   177   96   35  3  1 94  2
 0  0 6195628 146060  57364 8267000    0    0     0    24  312 1271  2  0 97  0
 0  0 6195628 146708  57364 8266768    0    0     0     0  312 1295  2  0 98  0
 1  0 6195280 130380  57324 8352768  203   91   203   115  346 1492  2  1 96  1
 0  2 6391060 108504  56628 8341460  203 65484   203 65484  578 1850  2  5 72 22
 0  0 6477120 148904  56628 8273208    0 28687     0 28729  460 1584  2  3 78 18
 2  0 6477120 147048  56644 8274984    0    0     0    21  311 1278  2  0 97  1
 0  0 6477120 145512  56644 8276800    0    0     0     0  288 1099  2  0 98  0
 0  0 6477120 149840  56668 8272972    0    0     0    27  321 1303  2  1 97  1
 0  0 6477120 148536  56668 8274696    0    0     0     0  302 1207  2  0 98  0
 0  3 6637500 154308  56188 8270224  181 53605   181 53651  559 1806  1  5 56 38
 1  5 6794972 100764  55020 8358472 5611 60509  5739 60553 1060 6308  8  8 52 32
 0  7 7031576 108548  53160 8341936    0 78868     0 78868  803 3543  4  8 19 68
 0  0 7165184 145832  53040 8294944    0 44536     0 44572  590 2165  3  4 48 45
 0  0 7165184 142092  53056 8317988    0    0     0    25  318 1369  2  1 97  1
 0  0 7165184 140480  53080 8319436    0    0     0    32  299 1145  2  0 97  1
 1  0 7165184 130632  53080 8329084    0    0     0     0  314 1451  2  1 97  0
 0  0 7165184 214616  53108 8330756    0    0    11    52  330 1583  2  1 96  1
 6  1 7373984 114896  52860 8407668    0 69600     0 69600  775 4490  6  8 68 18
 0  4 7571660  99568  52344 8454592    0 65893     0 65936  912 3216  4  7 39 50
 1  0 7721532 144212  52108 8371276    0 49956     0 49976  554 1921  2  5 52 42
 0  0 7721532 142372  52140 8372900    0    0     0    48  280 1200  2  0 97  1
 0  2 7878884 146332  52072 8360132    0 52451     0 52465  634 2243  3  5 70 22
 3  0 7881240 149948  52096 8364120    0  785     0   813  329 1186  2  0 83 15
 0  0 7881240 148404  52096 8365912    0    0     0     0  290 1163  2  0 97  0
 0  1 7971040 124144  52072 8378652    0 29933     0 29963  430 1776  2  3 94  1
 0  3 8108848 100328  51948 8454660  203 46157   203 46171  631 2419  3  5 67 25
 0  2 8288572 148256  51856 8374564    0 59911   395 59931  565 1630  3  5 40 51
 3  3 8387692 125216  52600 8461100    0 37153  1097 37340  665 2817  9  5 49 36
 1  0 8494804 159912  52792 8413428    0 35737  1221 36033  618 1832  5  4 41 50
 0  0 8494332 287000  52808 8535316    0    0   608    40  409 1863  3  1 92  3
 0  1 8589812 134724  52592 8644832    0 31827     0 31831  401 1553  5  4 90  2
 0  0 8589812 135980  52608 8645044    0    0     0    20  306  909  2  1 91  7
 0  0 8589812 133860  52628 8646488    0    0     8    25  263  990  2  0 97  1
 0  0 8589812 145872  52540 8674968    0    0    33     0  349 14584  4  3 94  0
 1  0 8589812 149716  52556 8670804    0    0     0    37  216  928  1  1 97  1
 0  0 8589812 149716  52556 8670804    0    0     0     0  164  642  1  1 98  0
 0  0 8589812 149716  52580 8670792    0    0     0    28  196  879  1  1 97  1
 0  0 8589812 150136  52612 8670308    0    0     0    73  264 1237  3  1 95  1
 0  0 8589812 151452  52612 8668960    0    0     0     0  271 1235  2  2 96  0
 0  2 8750484 147564  52152 8633480  168 53756   168 54943  468 1199  1  5 50 43
 0  3 8959004 134548  50452 8649604    0 69513    99 69539  739 2807  5 10 48 37
 1  1 9044340 152364  50440 8642244    0 28445    57 28489  374  906  1  5 54 40
 0  4 9107872 114360  50660 8712148    0 21177   600 21183  486 2959  6  4 71 18
 4  4 9270288 114520  49152 8722336    0 54181    28 54221  816 2667  7  9 37 47
 0  5 9486360 127692  48576 8661256    0 71981    17 72000  699 15501  4 10 31 55
 1  1 9592240 127836  48544 8677404    0 35292   244 35317  591 1983  6  5 56 33
 0  0 9641408 175712  48504 8634276    0 16391   556 16429  313  764  1  3 75 21
 0  0 9641408 167924  48504 8642168    0    0     0     0  324 1555  6  1 93  0
 0  0 9732140 133196  48464 8698588  181 30384   181 30408  505 1469  6  5 88  1
 0  0 9857272 146880  48424 8671884    0 41711     0 41771  521 1540  4  6 71 19
 0  0 9857272 138820  48424 8680148    0    0     0     0  148  552  1  1 98  0
 0  0 9857272 138200  48440 8680676    0    0     0    24  166  510  1  1 98  1
 0  3 10028960 130260  47076 8689800    0 57229     0 57252  639 2343  8  8 62 23
 0  0 10069828 149512  47100 8722420    0 13623     0 13663  317  874  1  3 62 34
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 1  0 10069828 141700  47116 8730648    0    0     0    24  202  683  1  2 97  0
 0  0 10069828 141700  47116 8730672    0    0     0     0  238 12991  2  4 94  0
 1  0 10201296 120612  47104 8694096    0 43821     0 43849  429 1406  1  6 82 10
 0  3 10371380 100428  46648 8733276    0 56696     0 56704  556 2050  3  8 76 13
 0  3 10394620 111740   1684 8807168    0 7747  2389  7837 2177 2661  3  6 34 56
 0  2 10394620 121080    232 8800532    0   16  5943    41  492 1439  1  2 58 38
 0  1 10394620 122844    616 8811820    0    0  4951     0  358  929  1  1 52 46
 0  1 10394620 123712    624 8810328    0    0   157    35  224  885  1  1 73 25
 0  1 10394620 125944    620 8808488    0    0    69    27  240  976  1  2 73 24
 0  1 10394620 127680    620 8806212    0    0    43     0  208  795  1  1 73 24
 0  1 10394620 129044    420 8805792    0    0   344    28  212  771  1  2 73 25
 0  1 10394620 130408    420 8803748    0    0     0     0  182  606  1  1 74 25
 0  1 10394620 131524    444 8802412    0    0    48    29  219 12184  1  3 72 23
 0  1 10394620 133508    468 8800920    0    0     0    28  194  687  1  1 73 25
 0  1 10394620 132764    468 8801676    0    0   776     4  274 1079  1  2 72 26
 0  1 10394620 134872    492 8800084    0    0     0    29  198  681  1  2 73 25
 0  1 10394620 137228    336 8797676    0    0     0    17  183  613  1  2 74 24
 0  1 10394620 138220    352 8796164    0    0     0    24  196  664  1  2 73 24
 0  1 10394620 138096    280 8796880    0    0   647    28  222  730  1  2 73 25
 2  6 10394620 117512    220 8820076    0    0  7204    12  409 1053  1  2 64 33
 0  9 10394620 116536    216 8820680    0    0 11164    15  395  535  0  0 62 37
 1  7 10394620 117280    212 8820100    0    0 10485    36  283  482  0  0 57 43
 0  9 10394620 118644    220 8818836    0    0 10253    35  274  550  0  0 60 39
 0  6 10394620 116412    216 8821152    0    0 10679    15  363  494  0  0 62 38
 0  5 10394620 119636    224 8817560    0    0  9813    25  299  537  0  0 60 40
 0  5 10394620 114040    380 8822712    0    0  7719    27  265  840  1  1 59 39
 0  9 10394620 117396    212 8820916    0    0  7879    39  293  661  0  0 57 42
 0  8 10394620 116900    208 8821128    0    0 10004     7  264  463  0  0 65 35
 0  7 10394620 116404    216 8821836    0    0  9519    32  307  474  0  0 59 40
 0  7 10394620 117272    216 8820760    0    0  9124    15  305  569  0  0 59 40
 0  7 10394620 124092    224 8814280    0    0  6595    17  266  531  0  0 61 39
 0  4 10394620 104036    216 8834084    0    0  6376    28  356  864  1  1 59 39
 0  5 10394620 105864    212 8831884    0    0  9900    16  281  481  0  0 64 35
 0  7 10394620 117132    220 8821440    0    0  8477    31  232  540  0  0 63 37
 0  5 10394620 109940    212 8829108    0    0  7676    21  378  770  0  1 62 36
 0  6 10394620 107296    216 8833820    0    0  8353    45  263  746  0  1 67 32
 0  5 10394620 104896    208 8835884    0    0  9529    23  297  648  0  0 72 28
 0  4 10394620 122544    224 8816776    0    0  7757    31  162  450  0  0 71 28
 0  6 10394620 114580    212 8825800    0    0  8595     4  215  722  0  1 65 34
 0  5 10394620 111592    208 8829508    0    0  7597    40  167  552  0  0 68 32
 1 10 10394620 123832    216 8815756    0    0  8868    21  245  947  0  2 68 31
 1  5 10394620 117324    216 8823244    0    0  8352    17  173  574  0  1 61 38
 0  7 10394620 124224    208 8815804    0    0  8501    39  191  719  0  1 66 33
 0  8 10394620 114160    204 8826488    0    0  9309     7  246  520  0  0 66 34
 0  3 10394620 101048    228 8840052    0    0  8497    28  328  695  0  1 56 43
 0  6 10394620  99696    228 8841460    0    0  8991    33  393  991  0  1 68 31
 0  6 10394620  99536    212 8841756    0    0  9857    17  380 1206  0  0 72 28
 0 10 10394620  99356    216 8841456    0    0  9607    31  375 1417  0  1 68 32
 0  7 10394620  99548    212 8841712    0    0  7337    45  380 1262  0  0 65 35
 0  7 10394620  99816    212 8841496    0    0  6148    57  292 1039  0  1 69 31
 2 11 10394620 111088    212 8829388    0    0  6571     5  269  921  0  1 66 33
 0  6 10394620 107484    228 8833828    0    0  4564    23  230 1088  0  1 59 40
 0 17 10394620 113880    208 8826752    0    0  6055    25  195  640  0  0 61 39
 0 10 10394620 107288    212 8833028    0    0  5965    19  214  670  0  0 44 56
 0  7 10394620 107564    224 8833568    0    0  5613    29  195  657  0  0 52 47
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 1 11 10394620 109716    232 8829660    0    0  6057    15  200  732  0  0 63 37
 0  9 10394620 107712    236 8833652    0    0  6869    24  198 1194  0  0 62 37
 0 12 10394620 112384    204 8828152    0    0  7356    47  316 1315  1  1 60 38
 0 12 10394620 113680    204 8826688    0    0  7543     3  231  679  0  0 67 33
 0  7 10394620  99904    220 8840924    0    0  5964    32  191  583  0  0 62 38
 0  9 10394620 112292    208 8828388    0    0  6088    17  222  808  0  0 58 41
 1  8 10394620 107468    208 8833704    0    0  6216    39  255  713  1  2 63 34
 0 10 10394620  99976    224 8839932    0    0  5884    19  259 1092  0  1 53 46
 0  6 10394620 107716    224 8833452    0    0  6241     7  213  686  0  0 65 35
 0  9 10394620  99764    232 8841384    0    0  7068    23  254 1151  0  1 67 32
 0 10 10394620  99872    224 8841304    0    0  6332    27  296  931  0  0 65 34
 0  9  21220 8927804    600 163188    0    0  7209    33  490 1316  0  7 40 53
 0 21   1760 8937956   1240 154272  276    0  3888    40  207  911  0  0 68 32
 0  5   1748 8938924   1988 153040    0    0  5180    21  194 1273  1  1 48 50
 0  2   1748 8915940   3400 173544    0    0  4284     0  279 9247  4  2 61 33
 2  2   1748 8897472   4972 184308    0    0  3953   216  467 3150  4  2 69 25
 0  1   1748 8874084   7192 200584    0    0  5977   297  483 3148  4  1 72 23
 1  0   1748 8666764  10140 381604    0    0  4813    20  482 6266  6  3 70 21
 0  1   1748 8618408  14604 406808    0    0  5375    41  457 3520  4  2 71 23
 0  1   1748 8588056  15912 423880    0    0  6492    40  481 2863  3  1 73 22
 0  0   1748 8520288  16620 484624    0    0  1177    75  525 3176  9  2 76 13
 0  0   1748 8515004  16636 489548    0    0    55    41  273 1148  2  1 95  2
 0  0   1748 8502296  16660 494296    0    0   237    37  529 3150  9  1 85  4
 1  0   1748 8507388  16680 488732    0    0     1   117  384 2111  4  1 93  2
 0  0   1748 8507280  16680 488700    0    0     0     3  328 1868  2  1 97  0
 0  0   1748 8507352  16704 488356    0    0     0    28  291 1147  4  1 93  2
 0  0   1748 8516000  16704 479716    0    0     0     0  275 1036  3  1 96  0
 0  0   1748 8515884  16732 480152    0    0   104    29  299 1633  2  1 95  1

```I want to know who is using the mem cache and what files are in the cache so I can troubleshoot further when it happens again.

---

### Post by ali abry on 2013-02-17
check
```
  /var/log/syslog
```
in there theres information that what program cause this. maybe theres memory leak in one of the program you run.
also you can run command like this in background and check its out put at the time when that problem happens .
```
 $ top -b -d 3 >> system-monitor.txt
```
number 3 is a delay between updates.

---

### Post by RuralHunter on 2013-02-17
> **ali abry said:**
> check
```
  /var/log/syslog
```in there theres information that what program cause this. maybe theres memory leak in one of the program you run.
also you can run command like this in background and check its out put at the time when that problem happens .
```
 $ top -b -d 3 >> system-monitor.txt
```number 3 is a delay between updates.

thanks. forgot to paste the OOM killing log in syslog:
```

Feb 17 17:21:36 rh-ubt kernel: [25884.678738] Out of memory: Kill process 2119 (nautilus) score 3 or sacrifice child
Feb 17 17:21:36 rh-ubt kernel: [25884.678740] Killed process 2119 (nautilus) total-vm:1043340kB, anon-rss:42424kB, file-rss:19656kB
Feb 17 17:21:36 rh-ubt kernel: [25884.696166] Out of memory: Kill process 4425 (compiz) score 2 or sacrifice child
Feb 17 17:21:36 rh-ubt kernel: [25884.696168] Killed process 4425 (compiz) total-vm:1355928kB, anon-rss:52776kB, file-rss:4092kB


```

---

### Post by RuralHunter on 2013-02-18
It still happens. This is the top output ordering by memory usage:
```

$ top

top - 14:49:31 up  4:49,  2 users,  load average: 0.36, 0.30, 0.30
Tasks: 195 total,   1 running, 193 sleeping,   0 stopped,   1 zombie
%Cpu(s):  0.2 us,  0.0 sy,  0.0 ni, 99.8 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  10153356 total,  9963548 used,   189808 free,    41276 buffers
KiB Swap: 10394620 total,  6311492 used,  4083128 free,  9107588 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND                                                                                                                                        
 1126 root      20   0  335m 130m  98m S   0.0  1.3   3:32.63 Xorg                                                                                                                                           
 4810 rhunter    20   0 1416m  79m  29m S   0.3  0.8   1:05.66 compiz                                                                                                                                         
 2062 rhunter    20   0 1007m  56m  22m S   0.0  0.6   0:05.42 nautilus                                                                                                                                       
 4736 rhunter    20   0  748m  47m  22m S   0.0  0.5   0:26.34 qterm                                                                                                                                          
 2281 rhunter    20   0  374m  42m  13m S   0.0  0.4   0:00.77 gnome-screensav                                                                                                                                
 2015 rhunter    20   0  695m  38m 4424 S   0.0  0.4   0:02.55 gnome-settings-                                                                                                                                
 2316 rhunter    20   0  487m  35m 3496 S   0.0  0.4   0:01.17 ubuntuone-syncd                                                                                                                                
 1066 root      20   0  264m  30m 5828 S   0.0  0.3   0:00.01 lightdm                                                                                                                                        
 2115 rhunter    20   0  408m  23m 9644 S   0.0  0.2   0:05.37 python                                                                                                                                         
 2174 rhunter    20   0  540m  22m 9572 S   0.0  0.2   0:05.83 unity-panel-ser                                                                                                                                
 2367 rhunter    20   0  693m  16m 2772 S   0.0  0.2   0:00.23 unity-lens-phot                                                                                                                                
 1861 root      20   0  362m  16m 3192 S   0.0  0.2   0:02.65 python                                                                                                                                         
 2541 rhunter    20   0  534m  16m 7972 S   0.0  0.2   0:14.73 gnome-terminal                                                                                                                                 
 2425 rhunter    20   0  601m  13m 3792 S   0.0  0.1   0:00.16 unity-scope-vid                                                                                                                                
 2427 rhunter    20   0  454m  11m 2436 S   0.0  0.1   0:00.11 unity-scope-gdo                                                                                                                                
 2373 rhunter    20   0  433m  11m 3272 S   0.0  0.1   0:00.17 unity-lens-vide                                                                                                                                
 2361 rhunter    20   0  411m 9908 2900 S   0.0  0.1   0:00.56 unity-applicati                                                                                                                                
 2197 rhunter    20   0  465m 9640 3256 S   0.0  0.1   0:00.10 signon-ui                                                                                                                                      
 2063 rhunter    20   0  515m 9360 3700 S   0.0  0.1   0:00.13 nm-applet                                                                                                                                      
 2164 rhunter    20   0  314m 8956 5384 S   0.0  0.1   0:01.45 gtk-window-deco                                                                                                                                
 3552 root      20   0 97192 8312 1516 S   0.0  0.1   0:00.03 system-service-                                                                                                                                
 2455 rhunter    20   0  400m 8028 3776 S   0.0  0.1   0:00.42 update-notifier                                                                                                                                
 2108 rhunter    20   0  394m 7404 4104 S   0.0  0.1   0:02.56 bamfdaemon                                                                                                                                     
 2061 rhunter    20   0  436m 7400 3312 S   0.0  0.1   0:00.06 bluetooth-apple                                                                                                                                
 2295 rhunter    20   0  239m 7240 3292 S   0.0  0.1   0:01.14 zeitgeist-fts                                                                                                                                  
 2177 rhunter    20   0  421m 7056 3020 S   0.0  0.1   0:02.54 hud-service                                                                                                                                    
 2371 rhunter    20   0  829m 6832 2688 S   0.0  0.1   0:00.10 unity-shopping-                                                                                                                                
 1837 root      20   0  180m 6564 1172 S   0.0  0.1   0:03.26 fail2ban-server                                                                                                                                
 1941 rhunter    20   0  389m 6456 3564 S   0.0  0.1   0:00.21 gnome-session                                                                                                                                  
 2257 rhunter    20   0  509m 6400 2484 S   0.0  0.1   0:00.15 goa-daemon                                                                                                                                     
 2208 rhunter    20   0  483m 6240 3288 S   0.0  0.1   0:00.06 indicator-print                                                                                                                                
 2158 rhunter    20   0  425m 6188 3192 S   0.0  0.1   0:00.08 telepathy-indic                                                                                                                                
 2127 rhunter    20   0  140m 6000 3572 S   0.0  0.1   0:00.22 ibus-engine-pin                                                                                                                                
 2152 rhunter    20   0  316m 5736 3144 S   0.0  0.1   0:00.05 notify-osd                                                                                                                                     
 2064 rhunter    20   0  450m 5612 2972 S   0.0  0.1   0:00.07 gnome-fallback-                                                                                                                                
 2068 rhunter    20   0  306m 5504 2976 S   0.0  0.1   0:00.05 polkit-gnome-au                                                                                                                                
 2207 rhunter    20   0  581m 5388 2900 S   0.0  0.1   0:00.15 indicator-datet                                                                                                                                
 2117 rhunter    20   0  210m 4696 3080 S   0.0  0.0   0:00.48 ibus-x11                                                                                                                                       
 2232 rhunter    20   0  965m 4596 2600 S   0.0  0.0   0:00.04 evolution-sourc                                                                                                                                
 2280 rhunter    20   0  406m 4576 3032 S   0.0  0.0   0:00.09 zeitgeist-datah                                                                                                                                
 2287 rhunter    20   0  338m 4524 3280 S   0.0  0.0   0:00.64 zeitgeist-daemo                                                                                                                                
 2369 rhunter    20   0  321m 4524 2564 S   0.0  0.0   0:00.05 unity-music-dae                                                                                                                                
 2078 rhunter    20   0  209m 4476 2776 S   0.0  0.0   0:00.07 gvfs-udisks2-vo                                                                                                                                
 2363 rhunter    20   0  474m 4284 2852 S   0.0  0.0   0:00.07 unity-files-dae                                                                                                                                
 2085 root      20   0  335m 4268 2708 S   0.0  0.0   0:01.85 udisksd                                                                                                                                        
 2203 rhunter    20   0  532m 4228 2648 S   0.0  0.0   0:00.06 indicator-sound                                                                                                                                
  914 root      20   0  240m 4220 2888 S   0.0  0.0   0:00.25 NetworkManager                                                                                                                                 
 2191 rhunter    20   0  322m 4180 2756 S   0.0  0.0   0:00.04 mission-control                                                                                                                                
  921 root      20   0  191m 4088 2652 S   0.0  0.0   0:00.26 polkitd                                                                                                                                        
 1930 rhunter    20   0  370m 4020 3144 S   0.0  0.0   0:00.04 gnome-keyring-d                                                                                                                                
 2365 rhunter    20   0  681m 4004 2656 S   0.0  0.0   0:00.03 unity-gwibber-d 

```

Seems not much memory is used by all those apps but the cache and swap keeps increasing quickly. I'm crazy!

---

### Post by RuralHunter on 2013-02-18
One thing to mention, this happened after I created an "Ubuntu One" account. I'm not sure if it's related to it. Does it have any background processes? if yes how to disable it?

---

### Post by rnerwein on 2013-02-18
> **RuralHunter said:**
> One thing to mention, this happened after I created an "Ubuntu One" account. I'm not sure if it's related to it. Does it have any background processes? if yes how to disable it?
hi
the high caching mostely comes from file I/O. UBUNTU one can be a reason for it (depends you give it a lot of space to backup).
the behavior on your system looks for me like a "little" bug. but you can 
1. set your swappiness ( /proc/sys/vm/swappiness) to 10. 
sudo echo 10 > /proc/sys/vm/swappiness
to make this permanent use /etc/sysctl

2. to get your memory back clean up your cache (in a terminal run)
---------------------------------------------------------------------------------------------------------#
sync; sync
     sudo echo 3 > /proc/sys/vm/drop_caches
#      1 --> free pagecaches, 2 --> free dentries and inodes,3 --> free all
#--------------------------------------------------------------------------------------------------------#

the sync command is only to be on the saver side
and send an output of: ps aux (use an attachement)
ciao

---

### Post by aarons6 on 2013-02-18
i set asside a 2gb partition for swap.. i have 4gb ram.

i often seen a large amount of swap being used and i tracked it down..

ubuntu is setup to use a large part of system ram for hard drive cache and the system will start using the swap partition very early.. 

what i did was set my swappiness to 5.. 
now i can almost fill up my ram before the system decides to swap any to the drive. 

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

they say to use 10 but that is still kinda high.. specially if you have a lot of ram.. you will notice swapping around 25% 

you can even try 0 if you want, that will keep the system from swapping anything until it absolutely has to.

---

### Post by RuralHunter on 2013-02-18
> **rnerwein said:**
> hi
the high caching mostely comes from file I/O. UBUNTU one can be a reason for it (depends you give it a lot of space to backup).
the behavior on your system looks for me like a "little" bug. but you can 
1. set your swappiness ( /proc/sys/vm/swappiness) to 10. 
sudo echo 10 > /proc/sys/vm/swappiness
to make this permanent use /etc/sysctl

I will try to set it to 5 as [[COLOR=#000000]aarons6[/COLOR]]("http://ubuntuforums.org/member.php?u=845835") suggested
> 
2. to get your memory back clean up your cache (in a terminal run)
---------------------------------------------------------------------------------------------------------#
sync; sync
     sudo echo 3 > /proc/sys/vm/drop_caches
#      1 --> free pagecaches, 2 --> free dentries and inodes,3 --> free all
#--------------------------------------------------------------------------------------------------------#

the sync command is only to be on the saver side
and send an output of: ps aux (use an attachement)
ciao
I already tried that with all 3 options(1,2,3) but it didn't have any effect. The cache didn't drop any little and keep increasing still.

---

### Post by RuralHunter on 2013-02-18
changing the swapness didn't help. The problem is still on the cache not the used memory. is there anyway I can see what files are in the cache so I can guess which application is using them? Another observation, the memory releases after I logout and login again.

---

### Post by aarons6 on 2013-02-18
i dont think the swap goes back to 0 once its used.

i noticed that if i run a program that uses swap and close it, the swap is still shown as used.. even tho im sure its not.

i just noticed you have 10gb ram? 

you have to have a memory leak somewhere.. here is my system

             total       used       free     shared    buffers     cached
Mem:       4136852    3740892     395960          0     465176    2096492
-/+ buffers/cache:    1179224    2957628
Swap:      2048280          8    2048272


i have only 4gb ram and my swap file never goes above a few hundred k.

---

### Post by RuralHunter on 2013-02-19
right. I do believe there is something abnormal. I just want to find what it is

---

### Post by rnerwein on 2013-02-19
> **RuralHunter said:**
> right. I do believe there is something abnormal. I just want to find what it is
good morning
i am running 12.04.2 and the command: sudo echo 3 > /proc/sys/vm/drop_caches
this works on my system. after the "echo ...." run: 
 cat  /proc/sys/vm/drop_caches
what's the output ?
about the contes of the cache - i don't know.
but where is your output of: ps uax ? what i see in the top output is only a part of the running tasks.
about swap: if the system don't need parts of the swaped out the stuff it won't will bring it back.
ciao

---

### Post by RuralHunter on 2013-02-19
> **rnerwein said:**
> good morning
i am running 12.04.2 and the command: sudo echo 3 > /proc/sys/vm/drop_caches
this works on my system. after the "echo ...." run: 
 cat  /proc/sys/vm/drop_caches
what's the output ?
about the contes of the cache - i don't know.
but where is your output of: ps uax ? what i see in the top output is only a part of the running tasks.
about swap: if the system don't need parts of the swaped out the stuff it won't will bring it back.
ciao
The top output I pasted is ordered by memory usage. I think the rest is not relevant. about the "echo 3 > /proc/sys/vm/drop_caches", I tried and it works in normal case. but when the problem happens(usually I notice it by the slow down caused by swapping), the command just has no effect.

---

### Post by rnerwein on 2013-02-19
> **RuralHunter said:**
> The top output I pasted is ordered by memory usage. I think the rest is not relevant. about the "echo 3 > /proc/sys/vm/drop_caches", I tried and it works in normal case. but when the problem happens(usually I notice it by the slow down caused by swapping), the command just has no effect.
hi again
the reason that i want to see the output of ps aux is that i want to see if there is may be a runaway kernelthread (huge cpu usage) and there is no memory usage shown by this task - but cpu time.
cheers

---

