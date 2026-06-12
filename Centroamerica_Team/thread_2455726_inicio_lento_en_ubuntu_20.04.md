---
title: "inicio lento en ubuntu 20.04"
date: 2020-12-26
forum: Centroamerica Team
---

### Post by gmarenzi on 2020-12-26
Hola, buen día y feliz navidad!

Mi ubuntu 20.04 demora muchísmo tiempo en iniciar

Uso una Dell i5 de décima generación, con 8 gb de ram

Los resultados del análisis son los siguientes:


```
german@german-Latitude-3410:~$ systemd-analyze
Startup finished in 6.103s (firmware) + 5.994s (loader) + 5.333s (kernel) + 1min 46.738s (userspace) = 2min 4.171s 
graphical.target reached after 1min 46.560s in userspace
german@german-Latitude-3410:~$ systemd-analyze critical-chain
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @1min 46.560s
&#9492;&#9472;multi-user.target @1min 46.560s
  &#9492;&#9472;snapd.seeded.service @1min 5.988s +3.250s
    &#9492;&#9472;snapd.service @37.999s +27.984s
      &#9492;&#9472;basic.target @37.553s
        &#9492;&#9472;sockets.target @37.553s
lines 1-9...skipping...
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @1min 46.560s
&#9492;&#9472;multi-user.target @1min 46.560s
  &#9492;&#9472;snapd.seeded.service @1min 5.988s +3.250s
    &#9492;&#9472;snapd.service @37.999s +27.984s
      &#9492;&#9472;basic.target @37.553s
        &#9492;&#9472;sockets.target @37.553s
          &#9492;&#9472;snapd.socket @37.552s +594us
            &#9492;&#9472;sysinit.target @37.425s
              &#9492;&#9472;systemd-timesyncd.service @37.217s +208ms
                &#9492;&#9472;systemd-tmpfiles-setup.service @35.460s +1.700s
                  &#9492;&#9472;systemd-journal-flush.service @5.533s +29.926s
                    &#9492;&#9472;systemd-remount-fs.service @4.819s +656ms
                      &#9492;&#9472;systemd-journald.socket @4.811s
                        &#9492;&#9472;-.mount @4.809s
                          &#9492;&#9472;system.slice @4.809s
                            &#9492;&#9472;-.slice @4.809s


```

Muchas gracias
Germán

---

