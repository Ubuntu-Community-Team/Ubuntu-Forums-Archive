---
title: "Installation issues with GCCG"
date: 2014-06-07
forum: Gaming &amp; Leisure
---

### Post by Andrew_Miro on 2014-06-07
[FONT=Verdana][COLOR=#000000]Hello, I'm attempting to install GCCG and I cant quite seem to get there. Here's everything from Terminal, I was hoping someone could point me in the right direction to resolve. [/COLOR][/FONT]

[FONT=Verdana][COLOR=#000000]andrew@andrew-Satellite-M110:~/gccg$ mkdir gccg[/COLOR][/FONT]
[COLOR=#000000][FONT=Verdana]andrew@andrew-Satellite-M110:~/gccg$ cd gccg[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]andrew@andrew-Satellite-M110:~/gccg/gccg$ wget [/FONT][/COLOR][http://gccg.sourceforge.net/modules/gccg-core-1.0.10.tgz](http://gccg.sourceforge.net/modules/gccg-core-1.0.10.tgz)
[COLOR=#000000][FONT=Verdana]--2014-06-05 08:46:53-- [/FONT][/COLOR][http://gccg.sourceforge.net/modules/gccg-core-1.0.10.tgz](http://gccg.sourceforge.net/modules/gccg-core-1.0.10.tgz)
[COLOR=#000000][FONT=Verdana]Resolving gccg.sourceforge.net (gccg.sourceforge.net)... 216.34.181.96[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Connecting to gccg.sourceforge.net (gccg.sourceforge.net)|216.34.181.96|:80... connected.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]HTTP request sent, awaiting response... 200 OK[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Length: 22409 (22K) [application/x-gzip][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Saving to: ‘gccg-core-1.0.10.tgz’[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]100%[======================================>] 22,409 --.-K/s in 0.03s [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]2014-06-05 08:46:53 (714 KB/s) - ‘gccg-core-1.0.10.tgz’ saved [22409/22409][/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]andrew@andrew-Satellite-M110:~/gccg/gccg$ tar xzvf gccg-core-1.0.10.tgz[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]./[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]./xml/[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]./xml/gccg-game.dtd[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]./xml/modules.dtd[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]./xml/gccg-set.dtd[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]./xml/installed.xml[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]./decks/[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]./gccg_package[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]./doc/[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]./tools/[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]./tools/launch_client[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]./sounds/[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]./COPYING[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]./scripts/[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]./scripts/common.include[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]./lib/[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]./games.dat[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]./graphics/[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]andrew@andrew-Satellite-M110:~/gccg/gccg$ ./gccg_package install client fonts linux-i386[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]---[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Fetching module list [1] [/FONT][/COLOR][http://gccg.sourceforge.net/modules/available.xml](http://gccg.sourceforge.net/modules/available.xml)
[COLOR=#000000][FONT=Verdana]** GET [/FONT][/COLOR][http://gccg.sourceforge.net/modules/available.xml](http://gccg.sourceforge.net/modules/available.xml)[COLOR=#000000][FONT=Verdana] ==> 200 OK[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]---[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Fetching module list [2] [/FONT][/COLOR][http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml)
[COLOR=#000000][FONT=Verdana]** GET [/FONT][/COLOR][http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml)[COLOR=#000000][FONT=Verdana] ==> 403 Forbidden (1s)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]FAILED: Skipping [/FONT][/COLOR][http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml)
[COLOR=#000000][FONT=Verdana]---[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Fetching module list [3] [/FONT][/COLOR][http://lotrtcgwiki.com/files/gccg/available.xml](http://lotrtcgwiki.com/files/gccg/available.xml)
[COLOR=#000000][FONT=Verdana]** GET [/FONT][/COLOR][http://lotrtcgwiki.com/files/gccg/available.xml](http://lotrtcgwiki.com/files/gccg/available.xml)[COLOR=#000000][FONT=Verdana] ==> 200 OK (1s)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]---[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Fetching module list [4] [/FONT][/COLOR][http://games.phtn.de/gccg/available.xml](http://games.phtn.de/gccg/available.xml)
[COLOR=#000000][FONT=Verdana]** GET [/FONT][/COLOR][http://games.phtn.de/gccg/available.xml](http://games.phtn.de/gccg/available.xml)[COLOR=#000000][FONT=Verdana] ==> 200 OK (1s)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]---[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Fetching module list [5] [/FONT][/COLOR][http://wtactics.org/files/gccg/modules/available.xml](http://wtactics.org/files/gccg/modules/available.xml)
[COLOR=#000000][FONT=Verdana]** GET [/FONT][/COLOR][http://wtactics.org/files/gccg/modules/available.xml](http://wtactics.org/files/gccg/modules/available.xml)[COLOR=#000000][FONT=Verdana] ==> 200 OK[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Fetching [/FONT][/COLOR][http://gccg.sourceforge.net/modules/gccg-l...6-0.9.7.0.1.tgz]("http://gccg.sourceforge.net/modules/gccg-linux-i386-0.9.7.0.1.tgz")
[COLOR=#000000][FONT=Verdana]** GET [/FONT][/COLOR][http://gccg.sourceforge.net/modules/gccg-l...6-0.9.7.0.1.tgz]("http://gccg.sourceforge.net/modules/gccg-linux-i386-0.9.7.0.1.tgz")[COLOR=#000000][FONT=Verdana] ==> 0200 OK (3s)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Fetching [/FONT][/COLOR][http://gccg.sourceforge.net/modules/gccg-client-0.9.7.11.tgz](http://gccg.sourceforge.net/modules/gccg-client-0.9.7.11.tgz)
[COLOR=#000000][FONT=Verdana]** GET [/FONT][/COLOR][http://gccg.sourceforge.net/modules/gccg-client-0.9.7.11.tgz](http://gccg.sourceforge.net/modules/gccg-client-0.9.7.11.tgz)[COLOR=#000000][FONT=Verdana] ==> 500 Status read failed: Connection reset by peer[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ERROR: module 'client' could not be downloaded properly[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Fetching [/FONT][/COLOR][http://gccg.sourceforge.net/modules/gccg-fonts-2.0.tgz](http://gccg.sourceforge.net/modules/gccg-fonts-2.0.tgz)
[COLOR=#000000][FONT=Verdana]** GET [/FONT][/COLOR][http://gccg.sourceforge.net/modules/gccg-fonts-2.0.tgz](http://gccg.sourceforge.net/modules/gccg-fonts-2.0.tgz)[COLOR=#000000][FONT=Verdana] ==> 200 OK (3s)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Installing module linux-i386[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Installing module fonts[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]andrew@andrew-Satellite-M110:~/gccg/gccg$ ./gccg_package status[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]---[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Fetching module list [1] [/FONT][/COLOR][http://gccg.sourceforge.net/modules/available.xml](http://gccg.sourceforge.net/modules/available.xml)
[COLOR=#000000][FONT=Verdana]** GET [/FONT][/COLOR][http://gccg.sourceforge.net/modules/available.xml](http://gccg.sourceforge.net/modules/available.xml)[COLOR=#000000][FONT=Verdana] ==> 200 OK (1s)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]---[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Fetching module list [2] [/FONT][/COLOR][http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml)
[COLOR=#000000][FONT=Verdana]** GET [/FONT][/COLOR][http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml)[COLOR=#000000][FONT=Verdana] ==> 403 Forbidden[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]FAILED: Skipping [/FONT][/COLOR][http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml)
[COLOR=#000000][FONT=Verdana]---[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Fetching module list [3] [/FONT][/COLOR][http://lotrtcgwiki.com/files/gccg/available.xml](http://lotrtcgwiki.com/files/gccg/available.xml)
[COLOR=#000000][FONT=Verdana]** GET [/FONT][/COLOR][http://lotrtcgwiki.com/files/gccg/available.xml](http://lotrtcgwiki.com/files/gccg/available.xml)[COLOR=#000000][FONT=Verdana] ==> 200 OK (1s)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]---[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Fetching module list [4] [/FONT][/COLOR][http://games.phtn.de/gccg/available.xml](http://games.phtn.de/gccg/available.xml)
[COLOR=#000000][FONT=Verdana]** GET [/FONT][/COLOR][http://games.phtn.de/gccg/available.xml](http://games.phtn.de/gccg/available.xml)[COLOR=#000000][FONT=Verdana] ==> 200 OK[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]---[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Fetching module list [5] [/FONT][/COLOR][http://wtactics.org/files/gccg/modules/available.xml](http://wtactics.org/files/gccg/modules/available.xml)
[COLOR=#000000][FONT=Verdana]** GET [/FONT][/COLOR][http://wtactics.org/files/gccg/modules/available.xml](http://wtactics.org/files/gccg/modules/available.xml)[COLOR=#000000][FONT=Verdana] ==> 200 OK[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]============================================================[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]STATUS OF MODULES[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]============================================================[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Module | Installed | Available | Status | Src[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]------------------------------------------------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]client | | v0.9.7.11 | - | [1][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]coc | | v0.2 | - | [4][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]coc-decks | | v0.1 | - | [4][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]coc-official-sets | | v0.1 | - | [4][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]coc-server | | v0.1 | - | [4][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]core | v1.0.10 | v1.0.10 | OK | [1][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]darwin-i386 | | v0.9.6.0 | - | [1][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]dev-tools | | v2.0 | - | [4][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]fonts | v2.0 | v2.0 | OK | [1][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]fonts-windows | | v2.0 | - | [4][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]linux-i386 | v0.9.7.0.1| v0.9.7.0.1| OK | [1][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]linux-x86_64 | | v0.9.7.0 | - | [1][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]lotr | | v1.2.0 | - | [3][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]nr | | v1.2 | - | [4][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]nr-decks | | v1.0 | - | [4][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]nr-official-sets | | v1.0 | - | [4][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]nr-server | | v1.1 | - | [4][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]nr-virtual-sets | | v1.0 | - | [4][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]server | | v0.9.7.11 | - | [1][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]source | | v0.9.7.9 | - | [1][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]windows32 | | v0.9.7.0 | - | [1][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]wt | | v0.0.1 | - | [5][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]============================================================[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]andrew@andrew-Satellite-M110:~/gccg/gccg$ ./gccg_package install mtg[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]---[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Fetching module list [1] [/FONT][/COLOR][http://gccg.sourceforge.net/modules/available.xml](http://gccg.sourceforge.net/modules/available.xml)
[COLOR=#000000][FONT=Verdana]** GET [/FONT][/COLOR][http://gccg.sourceforge.net/modules/available.xml](http://gccg.sourceforge.net/modules/available.xml)[COLOR=#000000][FONT=Verdana] ==> 200 OK[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]---[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Fetching module list [2] [/FONT][/COLOR][http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml)
[COLOR=#000000][FONT=Verdana]** GET [/FONT][/COLOR][http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml)[COLOR=#000000][FONT=Verdana] ==> 403 Forbidden (1s)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]FAILED: Skipping [/FONT][/COLOR][http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml)
[COLOR=#000000][FONT=Verdana]---[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Fetching module list [3] [/FONT][/COLOR][http://lotrtcgwiki.com/files/gccg/available.xml](http://lotrtcgwiki.com/files/gccg/available.xml)
[COLOR=#000000][FONT=Verdana]** GET [/FONT][/COLOR][http://lotrtcgwiki.com/files/gccg/available.xml](http://lotrtcgwiki.com/files/gccg/available.xml)[COLOR=#000000][FONT=Verdana] ==> 200 OK (1s)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]---[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Fetching module list [4] [/FONT][/COLOR][http://games.phtn.de/gccg/available.xml](http://games.phtn.de/gccg/available.xml)
[COLOR=#000000][FONT=Verdana]** GET [/FONT][/COLOR][http://games.phtn.de/gccg/available.xml](http://games.phtn.de/gccg/available.xml)[COLOR=#000000][FONT=Verdana] ==> 200 OK[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]---[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Fetching module list [5] [/FONT][/COLOR][http://wtactics.org/files/gccg/modules/available.xml](http://wtactics.org/files/gccg/modules/available.xml)
[COLOR=#000000][FONT=Verdana]** GET [/FONT][/COLOR][http://wtactics.org/files/gccg/modules/available.xml](http://wtactics.org/files/gccg/modules/available.xml)[COLOR=#000000][FONT=Verdana] ==> 200 OK (1s)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]andrew@andrew-Satellite-M110:~/gccg/gccg$ ./Mtg[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]bash: ./Mtg: No such file or directory[/FONT][/COLOR]




I notice it says: "[COLOR=#000000][FONT=Verdana]Fetching module list [2] [/FONT][/COLOR][http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml)
[COLOR=#000000][FONT=Verdana]** GET [/FONT][/COLOR][http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml)[COLOR=#000000][FONT=Verdana] ==> 403 Forbidden (1s)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]FAILED: Skipping [/FONT][/COLOR][http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml)"

Not sure what this means.. Any ideas what I'm doing wrong?

[COLOR=#000000][FONT=Verdana]Thanks in advance  :)[/FONT][/COLOR]

---

### Post by dannyboy79 on 2014-06-07
when you ran this command
```
./gccg_package install client fonts linux-i386
```
you can see that it errored on the following lines
Fetching module list [2] [http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml)
** GET [http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml) ==> 403 Forbidden (1s)
FAILED: Skipping [http://www.reneploetz.de/gccg/available.xml\](http://www.reneploetz.de/gccg/available.xml\)
Fetching [http://gccg.sourceforge.net/modules/...t-0.9.7.11.tgz](http://gccg.sourceforge.net/modules/...t-0.9.7.11.tgz)
** GET [http://gccg.sourceforge.net/modules/...t-0.9.7.11.tgz](http://gccg.sourceforge.net/modules/...t-0.9.7.11.tgz) ==> 500 Status read failed: Connection reset by peer
ERROR: module 'client' could not be downloaded properly
so clearly you can't continue with the tutorial IF previous steps failed. Maybe it's a matter of just retrying, maybe your network just messed up.

---

### Post by richmondster on 2014-06-15
i don't know any of this but it seems pretty interesting.

---

