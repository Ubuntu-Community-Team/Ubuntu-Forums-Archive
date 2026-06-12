---
title: "ZOMG media player acting strange"
date: 2009-05-03
forum: General Help
---

### Post by DouglasAWh on 2009-05-03
I just "installed" zomg from [http://zomg.alioth.debian.org/](http://zomg.alioth.debian.org/) (version .5.8)

However, it does not seem to be working properly.

```

&#9474;Connecting to Last.fm radio                                                                                                                                &#9474;
&#9474;Connecting to Last.fm session 4739844f1216ab49bc29c859aa3614fa                                                                                             &#9474;
&#9474;Tuning to librefm://globaltags/punk...                                                                                                                     &#9474;
&#9474;response=OK                                                                                                                                                &#9474;
&#9474;url=http://libre.fm                                                                                                                                        &#9474;
&#9474;stationname=Libre.fm Punk Tag Radio                                                                                                                        &#9474;
&#9474;lastfm_radio_getplaylist:5: command not found: zomghelper-xspf                                                                                             &#9474;
&#9474;                                                              Either type a menu command or hit 'h' to get some help.

```

Can anybody help me figure out what exactly is going on?  Why is it trying to connect Last.fm when I gave it the command 

```

./zomg -r librefm://globaltags/punk

```
?

Thanks!

---

### Post by DouglasAWh on 2009-05-03
it seems you need the version in the Debian sid repos: [http://packages.debian.org/sid/zomg](http://packages.debian.org/sid/zomg)

I haven't had a chance to test yet, but I will report when I do.

---

