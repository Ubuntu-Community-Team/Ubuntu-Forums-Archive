---
title: "FreeMind, Can anyone get this running in Ubuntu?"
date: 2006-09-23
forum: Desktop Environments
---

### Post by locoHost on 2006-09-23
Has anyone been able to get FreeMind running in Ubuntu? I'm still pretty new to Linux so obviously I can't. I followed the Debian install instructions at the FreeMind site. Didn't work. Added the deb lines to my sources.list file and ran the apt-get lines as instructed. Got an error like: Couldn't find 'freemind' or 'experimental'... something... Have you seen this? What is the fix?

Your advice will be -greatly- appreciated :-)

---

### Post by sarhento_lobo on 2006-09-23
i've had freemind running on my machine (dapper) for about half a year now. can you give any specific details? e.g., the error messages/output? also would help if you can post your sources.list and the url of where you got the instructions to set up.

---

### Post by RikoW on 2006-09-23
I just downloaded the binary package "for any operating system", unpack it, move the extracted directory somewhere, e.g. /opt.

then you can start freemind with:

```
java -jar  $path_to_freemind/freemind/lib/freemind.jar

```

Obviously, you need to replace *$path_to_freemind* with the proper path :)

You can create a script or an alias for the above command to make it easier to start (or create a launcher).

Hope that helps!

             Riko

---

