---
title: "Can someone translate this batch file for me? Trying to run a .bat on Linux Mint 17"
date: 2014-06-18
forum: Gaming &amp; Leisure
---

### Post by colby4 on 2014-06-18
I am trying to run a Runescape private server.. I tried Wine, however, it did not work. I have seen suggestions for translation. Can anyone do so for me?

Thanks,
-Colby

RUN.BAT:
```

@echo off
Title Client
cd ./bin/
START java -Xmx200m client 30 0 lowmem members 32
exit

```

---

### Post by Kirboosy on 2014-06-18
Welcome to the forums! You shouldn't need wine for this as Runescape is just launching off a Java instance. Make sure you have [Java installed]("https://help.ubuntu.com/community/Java") on your system otherwise it won't work.

Something like this would work for a script.

startup.sh
```

#/bin/bash
cd ./bin/
java -Xmx200m client 30 0 lowmem members 32
fi

```

You should be able to run it manually by hand. The script is just automatically kicking off the server. So if you run the commands independently it should work. Also if there is an issue with the "script" you will know where its breaking.

Hope that helps!
~Caboose
PS I found this guide. Hopefully it helps [Running your RSPS on Linux Server (Ubuntu)]("http://www.rune-server.org/runescape-development/rs2-server/tutorials/313304-running-your-rsps-linux-server-ubuntu.html")

---

