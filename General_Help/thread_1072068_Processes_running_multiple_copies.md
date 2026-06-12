---
title: "Processes running multiple copies"
date: 2009-02-17
forum: General Help
---

### Post by sircurmudgeon on 2009-02-17
First time posting since previously I've always managed to find an answer just by searching. This is a great community. (which is why I chose ubuntu)

No such luck this time. I'm running intrepid on 2 machines. The problem appears only on my server, so I'm stuck trying to figure out why.

It runs fine for a bit after a restart, but then I get errors telling me I have too many processes running. Right after it boots, it starts up each process multiple times.

System specs:
AMD Sempron 2800+
1Gb RAM
ATI Mach64 Rage II+

The only things I've added to intrepid on this machine are a ventrilo server, and a web-server. It's primary function is a file server connected to a windows dominated network. It also serves a small webpage for external access (nothing special, mainly so I can find stuff, or I can just send links to local users for file downloads).

I've also added tightVNC so I can access it headless from windows machines. What confuses me is that ALL processes are starting mulitple copies, and continue doing so until the machine just becomes un-usable and must be rebooted.

help?

---

### Post by heindsight on 2009-02-17
Well it's normal to have multiple instances of some processes. I would guess that you have one rogue process somewhere that is forking too many children.

Could you post the output of
```
ps -eF
```

---

### Post by sircurmudgeon on 2009-02-17
What I see is things that don't need to run 8+ times... really annoying since it caps out my memory and swapfile. Takes 30 seconds or more to get a termial :(

```
matt      9134     1  0   780   448   0 06:05 ?        00:00:00 /usr/bin/dbus-la
matt      9143  9102  0  4391  4000   0 06:05 ?        00:00:00 /usr/bin/seahors
matt      9146     1  0  1994  2568   0 06:05 ?        00:00:00 /usr/lib/libgcon
matt      9148     1  0  1388  1812   0 06:05 ?        00:00:00 /usr/lib/gvfs/gv
matt      9151  9102  0  3479  2976   0 06:05 ?        00:00:00 /usr/lib/gnome-s
matt      9157  9102  0  3869  5528   0 06:05 ?        00:00:00 /usr/bin/metacit
matt      9180  9102  0  8493 14604   0 06:05 ?        00:00:01 gnome-panel
matt      9182  9102  0 12171 14020   0 06:05 ?        00:00:01 nautilus --no-de
matt      9184     1  0  8113  2676   0 06:05 ?        00:00:00 /usr/lib/bonobo-
matt      9192     1  0  1427  2048   0 06:05 ?        00:00:00 /usr/lib/gvfs/gv
matt      9194     1  0  1390  1564   0 06:05 ?        00:00:00 /usr/lib/gvfs/gv
matt      9197     1  0  5760  7360   0 06:05 ?        00:00:00 /usr/lib/gnome-a
matt      9199     1  0  3498  2284   0 06:05 ?        00:00:00 /usr/lib/gvfs/gv
matt      9203     1  0  1388  1884   0 06:05 ?        00:00:00 /usr/lib/gvfs/gv
matt      9207     1  0  6448  9080   0 06:05 ?        00:00:00 /usr/lib/fast-us
matt      9210     1  0 11157 10204   0 06:05 ?        00:00:00 /usr/lib/gnome-a
matt      9234  9102  0  3854  4508   0 06:05 ?        00:00:00 tracker-applet
matt      9243  9102  0  7811  7980   0 06:05 ?        00:00:00 /usr/lib/evoluti
matt      9244  9102  0  6295  9408   0 06:05 ?        00:00:00 update-notifier
matt      9247  9102  0  6367  7084   0 06:05 ?        00:00:00 python /usr/shar
matt      9249  9102  0  7947  2188   0 06:05 ?        00:00:00 trackerd
matt      9251     1  0  5987  6500   0 06:05 ?        00:00:00 gnome-power-mana
matt      9255     1  0   779  1188   0 06:05 ?        00:00:00 /usr/lib/gamin/g
matt      9262     1  0  3312  1636   0 06:05 ?        00:00:00 Xtightvnc :16 -d
matt      9274     1  0   461   436   0 06:05 ?        00:00:00 /bin/sh /home/ma
matt      9277  9274  0  6155  4944   0 06:05 ?        00:00:00 x-session-manage
matt      9308     1  0   726   968   0 06:05 ?        00:00:00 //bin/dbus-daemo
matt      9309     1  0   780   448   0 06:05 ?        00:00:00 /usr/bin/dbus-la
matt      9323  9277  0  4394  4000   0 06:05 ?        00:00:00 /usr/bin/seahors
matt      9327     1  0  1935  2684   0 06:05 ?        00:00:00 /usr/lib/libgcon
matt      9329     1  0  1388  1928   0 06:05 ?        00:00:00 /usr/lib/gvfs/gv
matt      9333  9277  0  3479  3080   0 06:06 ?        00:00:00 /usr/lib/gnome-s
matt      9339  9277  0  3869  5660   0 06:06 ?        00:00:00 /usr/bin/metacit
matt      9364  9277  0 18754 15024   0 06:06 ?        00:00:01 gnome-panel
matt      9366  9277  0 14202 14124   0 06:06 ?        00:00:00 nautilus --no-de
matt      9368     1  0  8113  2676   0 06:06 ?        00:00:00 /usr/lib/bonobo-
matt      9375     1  0  5525  2292   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt      9378     1  0  1390  1564   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt      9380     1  0  9645  2528   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt      9386     1  0  5759  7484   0 06:06 ?        00:00:00 /usr/lib/gnome-a
matt      9391     1  0 12563  9728   0 06:06 ?        00:00:00 /usr/lib/fast-us
matt      9395     1  0 11163 10460   0 06:06 ?        00:00:00 /usr/lib/gnome-a
matt      9400     1  0  1388  1884   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt      9422  9277  0  3854  4720   0 06:06 ?        00:00:00 tracker-applet
matt      9432  9277  0  7811  8316   0 06:06 ?        00:00:00 /usr/lib/evoluti
matt      9433  9277  0  6295 13048   0 06:06 ?        00:00:00 update-notifier
matt      9437  9277  0  6368  7688   0 06:06 ?        00:00:00 python /usr/shar
matt      9438  9277  0  7691  2188   0 06:06 ?        00:00:00 trackerd
matt      9441     1  0  5987  6764   0 06:06 ?        00:00:00 gnome-power-mana
matt      9448     1  0  3339  1672   0 06:06 ?        00:00:00 Xtightvnc :17 -d
matt      9462     1  0   461   436   0 06:06 ?        00:00:00 /bin/sh /home/ma
matt      9465  9462  0  6155  4840   0 06:06 ?        00:00:00 x-session-manage
matt      9497     1  0   726   968   0 06:06 ?        00:00:00 //bin/dbus-daemo
matt      9498     1  0   780   448   0 06:06 ?        00:00:00 /usr/bin/dbus-la
matt      9507  9465  0  4391  4000   0 06:06 ?        00:00:00 /usr/bin/seahors
matt      9510     1  0  1935  2732   0 06:06 ?        00:00:00 /usr/lib/libgcon
matt      9512     1  0  1388  1928   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt      9515  9465  0  3479  3076   0 06:06 ?        00:00:00 /usr/lib/gnome-s
matt      9521  9465  0  3869  5552   0 06:06 ?        00:00:00 /usr/bin/metacit
matt      9548  9465  0 18760 14980   0 06:06 ?        00:00:01 gnome-panel
matt      9550  9465  0 14202 14028   0 06:06 ?        00:00:00 nautilus --no-de
matt      9552     1  0  6064  2676   0 06:06 ?        00:00:00 /usr/lib/bonobo-
matt      9559     1  0  5525  2316   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt      9562     1  0  1390  1564   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt      9564     1  0  7596  2552   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt      9569     1  0  5760  7360   0 06:06 ?        00:00:00 /usr/lib/gnome-a
matt      9577     1  0 12578  9600   0 06:06 ?        00:00:00 /usr/lib/fast-us
matt      9584     1  0  1388  1884   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt      9588     1  0 11014  9760   0 06:06 ?        00:00:00 /usr/lib/gnome-a
root      9619  5424  0   461   432   0 06:06 ?        00:00:00 /bin/sh -c nice 
root      9620  9619  0   441   432   0 06:06 ?        00:00:00 run-parts --repo
matt      9627  9465  0  3854  4728   0 06:06 ?        00:00:00 tracker-applet
matt      9638  9465  0  7811  8184   0 06:06 ?        00:00:00 /usr/lib/evoluti
matt      9644  9465  0  6288 12916   0 06:06 ?        00:00:00 update-notifier
matt      9650  9465  0  6369  7600   0 06:06 ?        00:00:00 python /usr/shar
root      9652  9620  0   461   460   0 06:06 ?        00:00:00 /bin/sh /etc/cro
matt      9654  9465  0  7691  2188   0 06:06 ?        00:00:00 trackerd
matt      9657     1  0  5987  6704   0 06:06 ?        00:00:00 gnome-power-mana
matt      9664     1  0  3313  1656   0 06:06 ?        00:00:00 Xtightvnc :18 -d
matt      9682     1  0   461   436   0 06:06 ?        00:00:00 /bin/sh /home/ma
matt      9685  9682  0  6155  4948   0 06:06 ?        00:00:00 x-session-manage
matt      9719     1  0   726   964   0 06:06 ?        00:00:00 //bin/dbus-daemo
matt      9720     1  0   780   448   0 06:06 ?        00:00:00 /usr/bin/dbus-la
matt      9729  9685  0  4391  4000   0 06:06 ?        00:00:00 /usr/bin/seahors
matt      9735     1  0  1937  2588   0 06:06 ?        00:00:00 /usr/lib/libgcon
matt      9739     1  0  1388  1932   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt      9742  9685  0  3479  3080   0 06:06 ?        00:00:00 /usr/lib/gnome-s
matt      9748  9685  0  3869  5660   0 06:06 ?        00:00:00 /usr/bin/metacit
matt      9773  9685  0 18788 15252   0 06:06 ?        00:00:01 gnome-panel
matt      9775  9685  0 14199 14116   0 06:06 ?        00:00:00 nautilus --no-de
matt      9777     1  0  8113  2676   0 06:06 ?        00:00:00 /usr/lib/bonobo-
matt      9790     1  0  5525  2280   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt      9796     1  0  1390  1564   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt      9803     1  0  5759  7848   0 06:06 ?        00:00:00 /usr/lib/gnome-a
matt      9806     1  0  9645  2500   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt      9812     1  0  1388  1884   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt      9822     1  0 12578  9692   0 06:06 ?        00:00:00 /usr/lib/fast-us
matt      9827     1  0 11014 10136   0 06:06 ?        00:00:00 /usr/lib/gnome-a
root      9844  9652  0   444   356   0 06:06 ?        00:00:00 sleep 1482
matt      9864  9685  0  3854  4720   0 06:06 ?        00:00:00 tracker-applet
matt      9873  9685  0  7811  8312   0 06:06 ?        00:00:00 /usr/lib/evoluti
matt      9874  9685  0  6295 13044   0 06:06 ?        00:00:00 update-notifier
matt      9878  9685  0  6367  7684   0 06:06 ?        00:00:00 python /usr/shar
matt      9881  9685  0  7691  2188   0 06:06 ?        00:00:00 trackerd
matt      9887     1  0  5987  6824   0 06:06 ?        00:00:00 gnome-power-mana
matt      9894     1  0  3313  1644   0 06:06 ?        00:00:00 Xtightvnc :19 -d
matt      9910     1  0   461   436   0 06:06 ?        00:00:00 /bin/sh /home/ma
matt      9914  9910  0  6155  4936   0 06:06 ?        00:00:00 x-session-manage
matt      9945     1  0   726   960   0 06:06 ?        00:00:00 //bin/dbus-daemo
matt      9946     1  0   780   448   0 06:06 ?        00:00:00 /usr/bin/dbus-la
matt      9955  9914  0  4394  4000   0 06:06 ?        00:00:00 /usr/bin/seahors
matt      9958     1  0  1933  2596   0 06:06 ?        00:00:00 /usr/lib/libgcon
matt      9960     1  0  1388  1932   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt      9964  9914  0  3479  3072   0 06:06 ?        00:00:00 /usr/lib/gnome-s
matt      9970  9914  0  3869  5648   0 06:06 ?        00:00:00 /usr/bin/metacit
matt      9995  9914  0 18740 14964   0 06:06 ?        00:00:01 gnome-panel
matt     10002  9914  0 12408 14096   0 06:06 ?        00:00:01 nautilus --no-de
matt     10004     1  0  8113  2676   0 06:06 ?        00:00:00 /usr/lib/bonobo-
matt     10015     1  0  5525  2268   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt     10020     1  0  1390  1564   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt     10023     1  0  7596  2592   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt     10030     1  0  5759  7868   0 06:06 ?        00:00:00 /usr/lib/gnome-a
matt     10043     1  0 12562  9684   0 06:06 ?        00:00:00 /usr/lib/fast-us
matt     10046     1  0 11046 10132   0 06:06 ?        00:00:00 /usr/lib/gnome-a
matt     10056     1  0  1388  1884   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt     10089     1  0  1387  1884   0 06:06 ?        00:00:00 /usr/lib/gvfs/gv
matt     10102  9914  0  3854  4668   0 06:06 ?        00:00:00 tracker-applet
matt     10112  9914  0  7811  8288   0 06:06 ?        00:00:00 /usr/lib/evoluti
matt     10114  9914  0  6294 11232   0 06:06 ?        00:00:00 update-notifier
matt     10117  9914  0  6368  7660   0 06:06 ?        00:00:00 python /usr/shar
matt     10119  9914  0  7947  2188   0 06:06 ?        00:00:00 trackerd
matt     10123     1  0  5987  6776   0 06:06 ?        00:00:00 gnome-power-mana
matt     10141     1  0  3306  1672   0 06:06 ?        00:00:00 Xtightvnc :20 -d
matt     10156     1  0   461   436   0 06:06 ?        00:00:00 /bin/sh /home/ma
matt     10161 10156  0  6155  4884   0 06:06 ?        00:00:00 x-session-manage
matt     10194     1  0   726   968   0 06:07 ?        00:00:00 //bin/dbus-daemo
matt     10195     1  0   780   448   0 06:07 ?        00:00:00 /usr/bin/dbus-la
matt     10204 10161  0  4391  4000   0 06:07 ?        00:00:00 /usr/bin/seahors
matt     10207     1  0  1957  2904   0 06:07 ?        00:00:00 /usr/lib/libgcon
matt     10211     1  0  1388  1932   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     10215 10161  0  3479  3076   0 06:07 ?        00:00:00 /usr/lib/gnome-s
matt     10224 10161  0  3869  5596   0 06:07 ?        00:00:00 /usr/bin/metacit
matt     10252 10161  0 16701 15000   0 06:07 ?        00:00:01 gnome-panel
matt     10254 10161  0 12154 14076   0 06:07 ?        00:00:00 nautilus --no-de
matt     10256     1  0  8113  2676   0 06:07 ?        00:00:00 /usr/lib/bonobo-
matt     10268     1  0  5525  2272   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     10275     1  0  1390  1564   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     10278     1  0  7596  2540   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     10288     1  0  5536  7752   0 06:07 ?        00:00:00 /usr/lib/gnome-a
matt     10290     1  0  1388  1884   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     10307     1  0 12831  9716   0 06:07 ?        00:00:00 /usr/lib/fast-us
matt     10310     1  0 11019 10128   0 06:07 ?        00:00:00 /usr/lib/gnome-a
matt     10358 10161  0  3854  4716   0 06:07 ?        00:00:00 tracker-applet
matt     10368 10161  0  7811  8312   0 06:07 ?        00:00:00 /usr/lib/evoluti
matt     10369 10161  0  6284 13020   0 06:07 ?        00:00:00 update-notifier
matt     10373 10161  0  6368  7672   0 06:07 ?        00:00:00 python /usr/shar
matt     10374 10161  0  7691  2188   0 06:07 ?        00:00:00 trackerd
matt     10384     1  0  5987  6796   0 06:07 ?        00:00:00 gnome-power-mana
matt     10398     1  0  3308  1648   0 06:07 ?        00:00:00 Xtightvnc :21 -d
matt     10413     1  0   461   436   0 06:07 ?        00:00:00 /bin/sh /home/ma
matt     10420 10413  0  6155  4960   0 06:07 ?        00:00:00 x-session-manage
matt     10451     1  0   726   960   0 06:07 ?        00:00:00 //bin/dbus-daemo
matt     10452     1  0   780   448   0 06:07 ?        00:00:00 /usr/bin/dbus-la
matt     10463 10420  0  4394  4000   0 06:07 ?        00:00:00 /usr/bin/seahors
matt     10468     1  0  1936  2544   0 06:07 ?        00:00:00 /usr/lib/libgcon
matt     10474     1  0  1388  1932   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     10478 10420  0  3479  3076   0 06:07 ?        00:00:00 /usr/lib/gnome-s
matt     10486 10420  0  3869  5652   0 06:07 ?        00:00:00 /usr/bin/metacit
matt     10514 10420  0 18778 15424   0 06:07 ?        00:00:01 gnome-panel
matt     10516 10420  0 14203 14112   0 06:07 ?        00:00:00 nautilus --no-de
matt     10518     1  0  8113  2676   0 06:07 ?        00:00:00 /usr/lib/bonobo-
matt     10534     1  0  5525  2288   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     10538     1  0  1390  1564   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     10544     1  0  5759  7868   0 06:07 ?        00:00:00 /usr/lib/gnome-a
matt     10548     1  0  7596  2540   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     10553     1  0  1388  1884   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     10582     1  0 12831  9708   0 06:07 ?        00:00:00 /usr/lib/fast-us
matt     10585     1  0 11017 10140   0 06:07 ?        00:00:00 /usr/lib/gnome-a
matt     10618 10420  0  3854  4716   0 06:07 ?        00:00:00 tracker-applet
matt     10630 10420  0  7811  8316   0 06:07 ?        00:00:00 /usr/lib/evoluti
matt     10632 10420  0  6295 13048   0 06:07 ?        00:00:00 update-notifier
matt     10638 10420  0  6368  7688   0 06:07 ?        00:00:00 python /usr/shar
matt     10640 10420  0  7691  2188   0 06:07 ?        00:00:00 trackerd
matt     10642     1  0  5987  6816   0 06:07 ?        00:00:00 gnome-power-mana
matt     10655     1  0  3313  1656   0 06:07 ?        00:00:00 Xtightvnc :22 -d
matt     10683     1  0   461   436   0 06:07 ?        00:00:00 /bin/sh /home/ma
matt     10687 10683  0  6155  4888   0 06:07 ?        00:00:00 x-session-manage
matt     10721     1  0   726   960   0 06:07 ?        00:00:00 //bin/dbus-daemo
matt     10723     1  0   780   448   0 06:07 ?        00:00:00 /usr/bin/dbus-la
matt     10735 10687  0  4391  4000   0 06:07 ?        00:00:00 /usr/bin/seahors
matt     10738     1  0  1959  2840   0 06:07 ?        00:00:00 /usr/lib/libgcon
matt     10740     1  0  1388  1932   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     10746 10687  0  3479  3076   0 06:07 ?        00:00:00 /usr/lib/gnome-s
matt     10754 10687  0  3869  5668   0 06:07 ?        00:00:00 /usr/bin/metacit
matt     10778 10687  0 18786 15428   0 06:07 ?        00:00:01 gnome-panel
matt     10783 10687  0 14458 14108   0 06:07 ?        00:00:00 nautilus --no-de
matt     10785     1  0  8113  2676   0 06:07 ?        00:00:00 /usr/lib/bonobo-
matt     10809     1  0  5525  2292   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     10813     1  0  1390  1564   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     10820     1  0  7596  2544   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     10825     1  0  1388  1884   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     10827     1  0  5759  7772   0 06:07 ?        00:00:00 /usr/lib/gnome-a
matt     10857     1  0 12569  9696   0 06:07 ?        00:00:00 /usr/lib/fast-us
matt     10860     1  0 11017 10128   0 06:07 ?        00:00:00 /usr/lib/gnome-a
matt     10899 10687  0  3854  4724   0 06:07 ?        00:00:00 tracker-applet
matt     10910 10687  0  7811  8308   0 06:07 ?        00:00:00 /usr/lib/evoluti
matt     10915 10687  0  6295 13040   0 06:07 ?        00:00:00 update-notifier
matt     10918 10687  0  6369  7688   0 06:07 ?        00:00:00 python /usr/shar
matt     10923 10687  0  7691  2188   0 06:07 ?        00:00:00 trackerd
matt     10927     1  0  5987  6808   0 06:07 ?        00:00:00 gnome-power-mana
matt     10941     1  0  3307  1656   0 06:07 ?        00:00:00 Xtightvnc :23 -d
matt     10968     1  0   461   436   0 06:07 ?        00:00:00 /bin/sh /home/ma
matt     10973 10968  0  6155  4952   0 06:07 ?        00:00:00 x-session-manage
matt     11005     1  0   726   964   0 06:07 ?        00:00:00 //bin/dbus-daemo
matt     11006     1  0   780   448   0 06:07 ?        00:00:00 /usr/bin/dbus-la
matt     11015 10973  0  4394  4000   0 06:07 ?        00:00:00 /usr/bin/seahors
matt     11018     1  0  1935  2716   0 06:07 ?        00:00:00 /usr/lib/libgcon
matt     11020     1  0  1388  1932   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     11030 10973  0  3479  3076   0 06:07 ?        00:00:00 /usr/lib/gnome-s
matt     11041 10973  0  3869  5660   0 06:07 ?        00:00:00 /usr/bin/metacit
matt     11071 10973  0 18777 15364   0 06:07 ?        00:00:01 gnome-panel
matt     11075 10973  0 12154 14068   0 06:07 ?        00:00:00 nautilus --no-de
matt     11077     1  0  8113  2676   0 06:07 ?        00:00:00 /usr/lib/bonobo-
matt     11092     1  0  5525  2280   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     11095     1  0  1390  1564   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     11100     1  0  7852  2548   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     11105     1  0  1388  1884   0 06:07 ?        00:00:00 /usr/lib/gvfs/gv
matt     11109     1  0  5759  7836   0 06:07 ?        00:00:00 /usr/lib/gnome-a
matt     11146     1  0 12575  9716   0 06:07 ?        00:00:00 /usr/lib/fast-us
matt     11149     1  0 11046 10124   0 06:07 ?        00:00:00 /usr/lib/gnome-a
matt     11191 10973  0  3854  4724   0 06:08 ?        00:00:00 tracker-applet
matt     11206 10973  0  7811  8304   0 06:08 ?        00:00:00 /usr/lib/evoluti
matt     11207 10973  0  6284 13036   0 06:08 ?        00:00:00 update-notifier
matt     11210 10973  0  6369  7684   0 06:08 ?        00:00:00 python /usr/shar
matt     11211 10973  0  7691  2716   0 06:08 ?        00:00:00 trackerd
matt     11213     1  0  5987  6780   0 06:08 ?        00:00:00 gnome-power-mana
matt     11232     1  0  3313  1808   0 06:08 ?        00:00:00 Xtightvnc :24 -d
matt     11257     1  0   461   436   0 06:08 ?        00:00:00 /bin/sh /home/ma
matt     11260 11257  0  6155  4996   0 06:08 ?        00:00:00 x-session-manage
matt     11290     1  0   726   956   0 06:08 ?        00:00:00 //bin/dbus-daemo
matt     11291     1  0   780   448   0 06:08 ?        00:00:00 /usr/bin/dbus-la
matt     11304 11260  0  4391  4008   0 06:08 ?        00:00:00 /usr/bin/seahors
matt     11308     1  0  1963  3228   0 06:08 ?        00:00:00 /usr/lib/libgcon
matt     11310     1  0  1388  1932   0 06:08 ?        00:00:00 /usr/lib/gvfs/gv
matt     11321 11260  0  3479  3632   0 06:08 ?        00:00:00 /usr/lib/gnome-s
matt     11328 11260  0  3869  5856   0 06:08 ?        00:00:00 /usr/bin/metacit
matt     11356 11260  0 29021 15728   0 06:08 ?        00:00:01 gnome-panel
matt     11360 11260  0 12153 15512   0 06:08 ?        00:00:00 nautilus --no-de
matt     11362     1  0  8113  2684   0 06:08 ?        00:00:00 /usr/lib/bonobo-
matt     11377     1  0  5525  2316   0 06:08 ?        00:00:00 /usr/lib/gvfs/gv
matt     11381     1  0  1390  1564   0 06:08 ?        00:00:00 /usr/lib/gvfs/gv
matt     11387     1  0  7596  2536   0 06:08 ?        00:00:00 /usr/lib/gvfs/gv
matt     11392     1  0  1388  1884   0 06:08 ?        00:00:00 /usr/lib/gvfs/gv
matt     11394     1  0  5759  8240   0 06:08 ?        00:00:00 /usr/lib/gnome-a
matt     11429     1  0 12569  9720   0 06:08 ?        00:00:00 /usr/lib/fast-us
matt     11436     1  0 11017 10060   0 06:08 ?        00:00:00 /usr/lib/gnome-a
matt     11479 11260  0  3854  4728   0 06:08 ?        00:00:00 tracker-applet
matt     11489 11260  0  7811  8312   0 06:08 ?        00:00:00 /usr/lib/evoluti
matt     11490 11260  0  6290 13024   0 06:08 ?        00:00:00 update-notifier
matt     11494 11260  0  6369  7688   0 06:08 ?        00:00:00 python /usr/shar
matt     11496 11260  0  7691  3332   0 06:08 ?        00:00:00 trackerd
matt     11498     1  0  5987  6808   0 06:08 ?        00:00:00 gnome-power-mana
matt     11519     1  0  3304  2128   0 06:08 ?        00:00:00 Xtightvnc :25 -d
matt     11528     1  0   461   436   0 06:08 ?        00:00:00 /bin/sh /home/ma
matt     11534 11528  0  6155  4952   0 06:08 ?        00:00:00 x-session-manage
matt     11571     1  0   726   956   0 06:08 ?        00:00:00 //bin/dbus-daemo
matt     11572     1  0   780   448   0 06:08 ?        00:00:00 /usr/bin/dbus-la
matt     11587 11534  0  4391  4000   0 06:08 ?        00:00:00 /usr/bin/seahors
matt     11597     1  0  1937  2744   0 06:08 ?        00:00:00 /usr/lib/libgcon
matt     11599     1  0  1388  1932   0 06:08 ?        00:00:00 /usr/lib/gvfs/gv
matt     11608 11534  0  3479  3080   0 06:08 ?        00:00:00 /usr/lib/gnome-s
matt     11616 11534  0  3869  5652   0 06:08 ?        00:00:00 /usr/bin/metacit
matt     11647 11534  0 18723 15196   0 06:08 ?        00:00:01 gnome-panel
matt     11651 11534  0 12152 14084   0 06:08 ?        00:00:00 nautilus --no-de
matt     11653     1  0  8113  2676   0 06:08 ?        00:00:00 /usr/lib/bonobo-
matt     11669     1  0  5525  2272   0 06:08 ?        00:00:00 /usr/lib/gvfs/gv
matt     11673     1  0  1390  1564   0 06:08 ?        00:00:00 /usr/lib/gvfs/gv
matt     11681     1  0  1388  1884   0 06:08 ?        00:00:00 /usr/lib/gvfs/gv
matt     11686     1  0  5533  7696   0 06:08 ?        00:00:00 /usr/lib/gnome-a
matt     11689     1  0  7596  2552   0 06:08 ?        00:00:00 /usr/lib/gvfs/gv
matt     11714     1  0 12569 10788   0 06:08 ?        00:00:00 /usr/lib/fast-us
matt     11719     1  0 11017 10284   0 06:08 ?        00:00:00 /usr/lib/gnome-a
matt     11769 11534  0  3854  5144   0 06:08 ?        00:00:00 tracker-applet
matt     11778 11534  0  7811  8304   0 06:08 ?        00:00:00 /usr/lib/evoluti
matt     11779 11534  0  6286 13052   0 06:08 ?        00:00:00 update-notifier
matt     11787 11534  0  6369  7736   0 06:08 ?        00:00:00 python /usr/shar
matt     11790 11534  0  7691  2860   0 06:08 ?        00:00:00 trackerd
matt     11793     1  0  5987  6800   0 06:08 ?        00:00:00 gnome-power-mana
matt     11816     1  0  3310  2000   0 06:08 ?        00:00:00 Xtightvnc :26 -d
matt     11842     1  0   461   436   0 06:08 ?        00:00:00 /bin/sh /home/ma
matt     11846 11842  0  6155  4936   0 06:08 ?        00:00:00 x-session-manage
matt     11881     1  0   726   964   0 06:08 ?        00:00:00 //bin/dbus-daemo
matt     11882     1  0   780   448   0 06:08 ?        00:00:00 /usr/bin/dbus-la
matt     11893 11846  0  4391  4000   0 06:08 ?        00:00:00 /usr/bin/seahors
matt     11899     1  0  1964  2976   0 06:08 ?        00:00:00 /usr/lib/libgcon
matt     11902     1  0  1388  1932   0 06:08 ?        00:00:00 /usr/lib/gvfs/gv
matt     11913 11846  0  3479  3076   0 06:08 ?        00:00:00 /usr/lib/gnome-s
matt     11922 11846  0  3869  5640   0 06:08 ?        00:00:00 /usr/bin/metacit
matt     11962 11846  0 18764 16608   0 06:08 ?        00:00:01 gnome-panel
matt     11966 11846  0 12225 16296   0 06:08 ?        00:00:01 nautilus --no-de
matt     11968     1  0  8113  2880   0 06:08 ?        00:00:00 /usr/lib/bonobo-
matt     11983     1  0  5525  2596   0 06:08 ?        00:00:00 /usr/lib/gvfs/gv
matt     11987     1  0  1390  2172   0 06:08 ?        00:00:00 /usr/lib/gvfs/gv
matt     12000     1  0  1388  1984   0 06:08 ?        00:00:00 /usr/lib/gvfs/gv
matt     12016     1  0  5533  7892   0 06:08 ?        00:00:00 /usr/lib/gnome-a
matt     12018     1  0  7596  2540   0 06:08 ?        00:00:00 /usr/lib/gvfs/gv
matt     12032     1  0 12575 10012   0 06:08 ?        00:00:00 /usr/lib/fast-us
matt     12036     1  0 11017 10868   0 06:08 ?        00:00:00 /usr/lib/gnome-a
matt     12093 11846  0  3854  4788   0 06:08 ?        00:00:00 tracker-applet
matt     12109 11846  0  7811  8696   0 06:08 ?        00:00:00 /usr/lib/evoluti
matt     12112 11846  0  6296 13100   0 06:09 ?        00:00:00 update-notifier
matt     12115 11846  0  6369 10068   0 06:09 ?        00:00:00 python /usr/shar
matt     12117 11846  0  7691  4076   0 06:09 ?        00:00:00 trackerd
matt     12119     1  0  5987  7744   0 06:09 ?        00:00:00 gnome-power-mana
matt     12136     1  0  3312  4460   0 06:09 ?        00:00:00 Xtightvnc :27 -d
matt     12165     1  0   461   436   0 06:09 ?        00:00:00 /bin/sh /home/ma
matt     12172 12165  0  6156  5604   0 06:09 ?        00:00:00 x-session-manage
matt     12221     1  0   726  1008   0 06:09 ?        00:00:00 //bin/dbus-daemo
matt     12222     1  0   780   508   0 06:09 ?        00:00:00 /usr/bin/dbus-la
matt     12247 12172  0  4394  5252   0 06:09 ?        00:00:00 /usr/bin/seahors
matt     12254     1  0  1957  4728   0 06:09 ?        00:00:00 /usr/lib/libgcon
matt     12259     1  0  1388  2128   0 06:09 ?        00:00:00 /usr/lib/gvfs/gv
matt     12297 12172  0  3479  3628   0 06:09 ?        00:00:00 /usr/lib/gnome-s
matt     12310 12172  0  3869  6076   0 06:09 ?        00:00:00 /usr/bin/metacit
matt     12364 12172  0 14614 15556   0 06:09 ?        00:00:01 gnome-panel
matt     12368 12172  0 12153 15476   0 06:09 ?        00:00:00 nautilus --no-de
matt     12371     1  0  8113  3044   0 06:09 ?        00:00:00 /usr/lib/bonobo-
matt     12389     1  0  5525  2316   0 06:09 ?        00:00:00 /usr/lib/gvfs/gv
matt     12393     1  0  1390  1564   0 06:09 ?        00:00:00 /usr/lib/gvfs/gv
matt     12406     1  0  5547  2532   0 06:09 ?        00:00:00 /usr/lib/gvfs/gv
matt     12410     1  0  1388  1884   0 06:09 ?        00:00:00 /usr/lib/gvfs/gv
matt     12413     1  0  5758  8476   0 06:09 ?        00:00:00 /usr/lib/gnome-a
matt     12426     1  0 12569  9712   0 06:09 ?        00:00:00 /usr/lib/fast-us
matt     12429     1  0 11017 10144   0 06:09 ?        00:00:00 /usr/lib/gnome-a
matt     12502 12172  0  3854  4732   0 06:09 ?        00:00:00 tracker-applet
matt     12519 12172  0  7811  8860   0 06:09 ?        00:00:00 /usr/lib/evoluti
matt     12522 12172  0  6296 13252   0 06:09 ?        00:00:00 update-notifier
matt     12529 12172  0  7691  9264   0 06:09 ?        00:00:00 trackerd
matt     12544     1  0  5987  6940   0 06:09 ?        00:00:00 gnome-power-mana
matt     12550     1  0  3501  5636   0 06:09 ?        00:00:00 Xtightvnc :28 -d
matt     12573     1  0   461   436   0 06:09 ?        00:00:00 /bin/sh /home/ma
matt     12577 12573  0  6156  4904   0 06:09 ?        00:00:00 x-session-manage
matt     12628     1  0   725   884   0 06:09 ?        00:00:00 //bin/dbus-daemo
matt     12629     1  0   780   448   0 06:09 ?        00:00:00 /usr/bin/dbus-la
matt     12638 12577  0  4394  4008   0 06:09 ?        00:00:00 /usr/bin/seahors
matt     12642     1  0  1388  1824   0 06:09 ?        00:00:00 /usr/lib/gvfs/gv
matt     12647     1  0  1966  3452   0 06:09 ?        00:00:00 /usr/lib/libgcon
matt     12675     1  0  7298  1732   0 06:09 ?        00:00:00 /usr/lib/gvfs//g
matt     12770 12577  0  3479  2976   0 06:09 ?        00:00:00 /usr/lib/gnome-s
matt     12778 12577  0  4629  7184   0 06:09 ?        00:00:00 /usr/bin/metacit
matt     12816 12577  1 18773 17244   0 06:09 ?        00:00:01 gnome-panel
matt     12818 12577  0 16231 19776   0 06:09 ?        00:00:00 nautilus --no-de
matt     12824     1  0  8113  2828   0 06:09 ?        00:00:00 /usr/lib/bonobo-
matt     12839     1  0  1327  1564   0 06:09 ?        00:00:00 /usr/lib/gvfs/gv
matt     12842     1  0  1316  1812   0 06:09 ?        00:00:00 /usr/lib/gvfs/gv
matt     12859     1  0  7596  2636   0 06:09 ?        00:00:00 /usr/lib/gvfs/gv
matt     12862     1  0  5759 10288   0 06:09 ?        00:00:00 /usr/lib/gnome-a
matt     12871     1  0  1388  2200   0 06:09 ?        00:00:00 /usr/lib/gvfs/gv
matt     12927     1  0 12575 12296   0 06:09 ?        00:00:00 /usr/lib/fast-us
matt     12930     1  0 11019 14740   0 06:09 ?        00:00:00 /usr/lib/gnome-a
matt     12982 12577  0  3854  5312   0 06:09 ?        00:00:00 tracker-applet
matt     12992 12577  0  7811  8308   0 06:09 ?        00:00:00 /usr/lib/evoluti
matt     12993 12577  0  6879 11052   0 06:09 ?        00:00:00 update-notifier
matt     13004 12577  0  7659  2772   0 06:09 ?        00:00:00 trackerd
matt     13022     1  0  3517  4048   0 06:09 ?        00:00:00 Xtightvnc :29 -d
matt     13041     1  0   461   436   0 06:09 ?        00:00:00 /bin/sh /home/ma
matt     13049 13041  0  6155  5132   0 06:09 ?        00:00:00 x-session-manage
matt     13103     1  0   780   448   0 06:09 ?        00:00:00 /usr/bin/dbus-la
matt     13104     1  0   726   756   0 06:09 ?        00:00:00 //bin/dbus-daemo
matt     13112 13049  0  4391  4656   0 06:09 ?        00:00:00 /usr/bin/seahors
matt     13120     1  0  1388  2096   0 06:09 ?        00:00:00 /usr/lib/gvfs/gv
matt     13123     1  0  1959  2996   0 06:09 ?        00:00:00 /usr/lib/libgcon
matt     13144 13049  0  3479  2976   0 06:09 ?        00:00:00 /usr/lib/gnome-s
matt     13152 13049  0  4626  7100   0 06:09 ?        00:00:00 /usr/bin/metacit
matt     13193 13049  1 18765 15476   0 06:10 ?        00:00:01 gnome-panel
matt     13195 13049  0 18352 18816   0 06:10 ?        00:00:01 nautilus --no-de
matt     13197     1  0  8113  2724   0 06:10 ?        00:00:00 /usr/lib/bonobo-
matt     13218     1  0  1327  1564   0 06:10 ?        00:00:00 /usr/lib/gvfs/gv
matt     13223     1  0  1316  1552   0 06:10 ?        00:00:00 /usr/lib/gvfs/gv
matt     13249     1  0  1388  1884   0 06:10 ?        00:00:00 /usr/lib/gvfs/gv
matt     13255     1  0  5533  8980   0 06:10 ?        00:00:00 /usr/lib/gnome-a
matt     13260     1  0  7596  2536   0 06:10 ?        00:00:00 /usr/lib/gvfs/gv
matt     13271     1  0 10511 12704   0 06:10 ?        00:00:00 /usr/lib/fast-us
matt     13277     1  0 11019 12316   0 06:10 ?        00:00:00 /usr/lib/gnome-a
matt     13350 13049  0  3854  5024   0 06:10 ?        00:00:00 tracker-applet
matt     13363 13049  0  7811  9556   0 06:10 ?        00:00:00 /usr/lib/evoluti
matt     13364 13049  0  6878 14520   0 06:10 ?        00:00:00 update-notifier
matt     13372 13049  0  7947  6616   0 06:10 ?        00:00:00 trackerd
matt     13425     1  0  3535  8976   0 06:10 ?        00:00:00 Xtightvnc :30 -d
matt     13448     1  0   461   436   0 06:10 ?        00:00:00 /bin/sh /home/ma
matt     13455 13448  0  6156  5156   0 06:10 ?        00:00:00 x-session-manage
matt     13496     1  0   693   836   0 06:10 ?        00:00:00 //bin/dbus-daemo
matt     13497     1  0   780   448   0 06:10 ?        00:00:00 /usr/bin/dbus-la
matt     13511 13455  0  4394  4052   0 06:10 ?        00:00:00 /usr/bin/seahors
matt     13515     1  0  1967  3544   0 06:10 ?        00:00:00 /usr/lib/libgcon
matt     13517     1  0  1388  1820   0 06:10 ?        00:00:00 /usr/lib/gvfs/gv
matt     13538 13455  0  3479  3160   0 06:10 ?        00:00:00 /usr/lib/gnome-s
matt     13545 13455  0  4629  9052   0 06:10 ?        00:00:00 /usr/bin/metacit
matt     13580 13455  1 18770 16708   0 06:10 ?        00:00:01 gnome-panel
matt     13585 13455  0 22377 17524   0 06:10 ?        00:00:00 nautilus --no-de
matt     13589     1  0  6064  2828   0 06:10 ?        00:00:00 /usr/lib/bonobo-
matt     13607     1  0  1327  1816   0 06:10 ?        00:00:00 /usr/lib/gvfs/gv
matt     13609     1  0  1316  1568   0 06:10 ?        00:00:00 /usr/lib/gvfs/gv
matt     13627     1  0  7596  2664   0 06:10 ?        00:00:00 /usr/lib/gvfs/gv
matt     13655     1  0  5536  7804   0 06:10 ?        00:00:00 /usr/lib/gnome-a
matt     13658     1  0  1388  1884   0 06:10 ?        00:00:00 /usr/lib/gvfs/gv
matt     13664     1  0 12828 11660   0 06:10 ?        00:00:00 /usr/lib/fast-us
matt     13687     1  0 11019 14860   0 06:10 ?        00:00:00 /usr/lib/gnome-a
matt     13737 13455  0  3854  5416   0 06:10 ?        00:00:00 tracker-applet
matt     13751 13455  0  7811  9724   0 06:10 ?        00:00:00 /usr/lib/evoluti
matt     13752 13455  0  6879 14304   0 06:10 ?        00:00:00 update-notifier
matt     13764 13455  0  7659  9844   0 06:10 ?        00:00:00 trackerd
matt     13786     1  0  3505  6884   0 06:10 ?        00:00:00 Xtightvnc :31 -d
matt     13810     1  0   461   496   0 06:10 ?        00:00:00 /bin/sh /home/ma
matt     13815 13810  0  6156  5628   0 06:10 ?        00:00:00 x-session-manage
matt     13856     1  0   693   980   0 06:10 ?        00:00:00 //bin/dbus-daemo
matt     13857     1  0   780   572   0 06:10 ?        00:00:00 /usr/bin/dbus-la
matt     13869 13815  0  4394  5488   0 06:10 ?        00:00:00 /usr/bin/seahors
matt     13874     1  0  1388  2136   0 06:10 ?        00:00:00 /usr/lib/gvfs/gv
matt     13876     1  0  1963  4380   0 06:10 ?        00:00:00 /usr/lib/libgcon
matt     13897 13815  0  3479  3628   0 06:10 ?        00:00:00 /usr/lib/gnome-s
matt     13905 13815  0  4626  9672   0 06:10 ?        00:00:00 /usr/bin/metacit
matt     13946 13815  1 18767 18108   0 06:10 ?        00:00:01 gnome-panel
matt     13948 13815  1 16303 21736   0 06:10 ?        00:00:01 nautilus --no-de
matt     13954     1  0  8113  3472   0 06:10 ?        00:00:00 /usr/lib/bonobo-
matt     13968     1  0  1327  1824   0 06:10 ?        00:00:00 /usr/lib/gvfs/gv
matt     13973     1  0  1316  1812   0 06:10 ?        00:00:00 /usr/lib/gvfs/gv
matt     14003     1  0  1388  2204   0 06:10 ?        00:00:00 /usr/lib/gvfs/gv
matt     14008     1  0  7596  2708   0 06:10 ?        00:00:00 /usr/lib/gvfs/gv
matt     14011     1  0  5533  9484   0 06:10 ?        00:00:00 /usr/lib/gnome-a
matt     14034     1  0 12569 13184   0 06:10 ?        00:00:00 /usr/lib/fast-us
matt     14040     1  0 11019 14872   0 06:10 ?        00:00:00 /usr/lib/gnome-a
matt     14132 13815  0  3854  4604   0 06:10 ?        00:00:00 tracker-applet
matt     14147 13815  0  7811  9640   0 06:10 ?        00:00:00 /usr/lib/evoluti
matt     14149 13815  0  6879 15336   0 06:10 ?        00:00:00 update-notifier
matt     14153 13815  0  7659 10188   0 06:10 ?        00:00:00 trackerd
matt     14204     1  0  3507  9728   0 06:10 ?        00:00:00 Xtightvnc :32 -d
matt     14229     1  0   461   496   0 06:10 ?        00:00:00 /bin/sh /home/ma
matt     14233 14229  0  6156  5624   0 06:10 ?        00:00:00 x-session-manage
matt     14286     1  0   693  1012   0 06:10 ?        00:00:00 //bin/dbus-daemo
matt     14287     1  0   780   576   0 06:10 ?        00:00:00 /usr/bin/dbus-la
matt     14299 14233  0  4391  5492   0 06:10 ?        00:00:00 /usr/bin/seahors
matt     14304     1  1  1968  4872   0 06:10 ?        00:00:00 /usr/lib/libgcon
matt     14306     1  0  1388  2132   0 06:10 ?        00:00:00 /usr/lib/gvfs/gv
matt     14334 14233  0  3479  3636   0 06:10 ?        00:00:00 /usr/lib/gnome-s
matt     14340 14233  0  4628  9680   0 06:10 ?        00:00:00 /usr/bin/metacit
matt     14382 14233  1 18702 18232   0 06:10 ?        00:00:00 gnome-panel
matt     14387 14233  1 18280 22240   0 06:10 ?        00:00:00 nautilus --no-de
matt     14392     1  0  8113  3512   0 06:10 ?        00:00:00 /usr/lib/bonobo-
matt     14411     1  0  1327  1820   0 06:11 ?        00:00:00 /usr/lib/gvfs/gv
matt     14414     1  0  1316  1812   0 06:11 ?        00:00:00 /usr/lib/gvfs/gv
matt     14426     1  0  5758 10400   0 06:11 ?        00:00:00 /usr/lib/gnome-a
matt     14428     1  0  7596  2708   0 06:11 ?        00:00:00 /usr/lib/gvfs/gv
matt     14442     1  0  1388  2200   0 06:11 ?        00:00:00 /usr/lib/gvfs/gv
matt     14471     1  0 12575 13276   0 06:11 ?        00:00:00 /usr/lib/fast-us
matt     14481     1  0 11017 14944   0 06:11 ?        00:00:00 /usr/lib/gnome-a
matt     14559 14233  0  3854  5372   0 06:11 ?        00:00:00 tracker-applet
matt     14576 14233  0  7811  9892   0 06:11 ?        00:00:00 /usr/lib/evoluti
matt     14579 14233  0  6846 14344   0 06:11 ?        00:00:00 update-notifier
matt     14580 14233  0  7680 16664   0 06:11 ?        00:00:00 /usr/bin/python
matt     14587 14233  0  7659  9980   0 06:11 ?        00:00:00 trackerd
matt     14619     1  0  3522  9952   0 06:11 ?        00:00:00 Xtightvnc :33 -d
matt     14650     1  0   461   496   0 06:11 ?        00:00:00 /bin/sh /home/ma
matt     14661 14650  0  6156  5624   0 06:11 ?        00:00:00 x-session-manage
matt     14704     1  0   693  1060   0 06:11 ?        00:00:00 //bin/dbus-daemo
matt     14707     1  0   780   652   0 06:11 ?        00:00:00 /usr/bin/dbus-la
matt     14716 14661  0  4394  5712   0 06:11 ?        00:00:00 /usr/bin/seahors
matt     14719     1  0  1388  2136   0 06:11 ?        00:00:00 /usr/lib/gvfs/gv
matt     14721     1  1  1966  4896   0 06:11 ?        00:00:00 /usr/lib/libgcon
matt     14740 14661  0  3479  3628   0 06:11 ?        00:00:00 /usr/lib/gnome-s
matt     14749 14661  0  4628  9684   0 06:11 ?        00:00:00 /usr/bin/metacit
matt     14778 14661  1 18713 18212   0 06:11 ?        00:00:00 gnome-panel
matt     14787 14661  1 18280 22240   0 06:11 ?        00:00:00 nautilus --no-de
matt     14791     1  0  8113  3524   0 06:11 ?        00:00:00 /usr/lib/bonobo-
matt     14808     1  0  1327  1824   0 06:11 ?        00:00:00 /usr/lib/gvfs/gv
matt     14810     1  0  1316  1808   0 06:11 ?        00:00:00 /usr/lib/gvfs/gv
matt     14819     1  1 23032 23124   0 06:11 ?        00:00:00 gnome-terminal
matt     14822     1  0  7596  2704   0 06:11 ?        00:00:00 /usr/lib/gvfs/gv
matt     14830     1  0  5537  9508   0 06:11 ?        00:00:00 /usr/lib/gnome-a
matt     14833     1  0  1388  2200   0 06:11 ?        00:00:00 /usr/lib/gvfs/gv
matt     14856     1  0 12570 13276   0 06:11 ?        00:00:00 /usr/lib/fast-us
matt     14860     1  0 11019 14944   0 06:11 ?        00:00:00 /usr/lib/gnome-a
matt     14927 14661  0  3854  5412   0 06:11 ?        00:00:00 tracker-applet
matt     14940 14661  0  7811  9892   0 06:11 ?        00:00:00 /usr/lib/evoluti
matt     14941 14661  0  6846 14472   0 06:11 ?        00:00:00 update-notifier
matt     14998 14661  0  7680 16676   0 06:11 ?        00:00:00 /usr/bin/python
matt     15002 14661  0  7691 10184   0 06:11 ?        00:00:00 trackerd
matt     15051     1  0  3313  9640   0 06:11 ?        00:00:00 Xtightvnc :34 -d
matt     15103     1  0   461   496   0 06:11 ?        00:00:00 /bin/sh /home/ma
matt     15106 15103  0  6155  5624   0 06:11 ?        00:00:00 x-session-manage
matt     15134     1  0   693   956   0 06:11 ?        00:00:00 //bin/dbus-daemo
matt     15135     1  0   780   652   0 06:11 ?        00:00:00 /usr/bin/dbus-la
matt     15164 15106  0  4391  5704   0 06:11 ?        00:00:00 /usr/bin/seahors
matt     15179     1  0  1388  2128   0 06:11 ?        00:00:00 /usr/lib/gvfs/gv
matt     15184     1  1  1909  4640   0 06:11 ?        00:00:00 /usr/lib/libgcon
matt     15281 14819  0   727   760   0 06:11 ?        00:00:00 gnome-pty-helper
matt     15282 14819  0  1422  3048   0 06:11 pts/0    00:00:00 bash
root     15388     2  0     0     0   0 06:11 ?        00:00:00 [pdflush]
matt     15556 15106  0  3479  3636   0 06:11 ?        00:00:00 /usr/lib/gnome-s
matt     15562 15106  0  3881  6428   0 06:11 ?        00:00:00 /usr/bin/metacit
matt     15611 15106  8 12531 18116   0 06:11 ?        00:00:00 gnome-panel
matt     15614 15106  8 14179 22132   0 06:12 ?        00:00:00 nautilus --no-de
matt     15616     1  1  8113  3508   0 06:12 ?        00:00:00 /usr/lib/bonobo-
matt     15656     1  0  1327  1824   0 06:12 ?        00:00:00 /usr/lib/gvfs/gv
matt     15660     1  0  1316  1812   0 06:12 ?        00:00:00 /usr/lib/gvfs/gv
matt     15676     1  0  7596  2716   0 06:12 ?        00:00:00 /usr/lib/gvfs/gv
matt     15693     1  0  1388  2208   0 06:12 ?        00:00:00 /usr/lib/gvfs/gv
matt     15697     1  2  5533  9476   0 06:12 ?        00:00:00 /usr/lib/gnome-a
matt     15734     1  4  8471 13264   0 06:12 ?        00:00:00 /usr/lib/fast-us
matt     15750     1  7 11017 14944   0 06:12 ?        00:00:00 /usr/lib/gnome-a
matt     15805 15282  0   686  1004   0 06:12 pts/0    00:00:00 ps -eF


```

Appreciate the quick reply :D

---

### Post by heindsight on 2009-02-17
It looks to me as if the problem is related to tightVNC. It seems you have a lot (looks like 34) VNC sessions running simultaneosly, each of which is running a full gnome session.

I've never used tightVNC, so I'm not sure how you'd go about doing it, but you need to reduce the number of VNC sessions you're running.

---

### Post by sircurmudgeon on 2009-02-17
you were right. hmmm. guess I need another option. Thanks :D

---

