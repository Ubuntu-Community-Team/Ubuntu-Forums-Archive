---
title: "Subversion and HTTPS bug in Intrepid 8.10 - workaround"
date: 2009-01-21
forum: General Help
---

### Post by 11hjpphty76lkjj on 2009-01-21
I wanted to post this in the open forum so other users could report success and/or updates as the other thread is closed.

The original thread is here: [http://ubuntuforums.org/showthread.php?t=948900](http://ubuntuforums.org/showthread.php?t=948900)

**Issue 1:**

svn: OPTIONS of 'https://xxxxxxxxxx.xxxx.xx/svn/repo': SSL negotiation failed: SSL error: Key usage violation in certificate has been detected. ([https://xxxxxxxxxxx.xxxx.xx]("https://xxxxxxxxxxx.xxxx.xx/"))

This is because in Intrepid, the neon HTTP library, which Subversion uses to talk to HTTP(S) servers, has been built with GNU TLS instead of OpenSSL.

**Issue 2:**

You want to upgrade your subversion to 1.5.x.

**Fix:**

By running this script and/or following the steps: (script also attached)

```

#!/bin/sh
echo "This script will reconfigure subversion to work with certs correctly."
echo "Steps outlined by dcrooke and compiled into this script by Kalosaurusrex"
echo "Please see the ubuntuforums.org thread for more information, questions or help."
echo "http://ubuntuforums.org/showthread.php?p=6057983"
echo ""
echo ""
echo "Please run this script as USER ONLY."
echo ""
echo "Press control-c to quit..else the script will start in 5 seconds."
sleep 5
sudo apt-get update
sudo apt-get autoremove
sudo apt-get install build-essential openssl ssh expat libxyssl-dev libssl-dev libexpat1-dev
cp ~/.subversion/servers ~/servers
sudo apt-get remove subversion
sudo dpkg --purge subversion
wget http://subversion.tigris.org/downloads/subversion-1.5.4.tar.gz
wget http://subversion.tigris.org/downloads/subversion-deps-1.5.4.tar.gz
tar xvfz subversion-1.5.4.tar.gz
tar xvfz subversion-deps-1.5.4.tar.gz
cd subversion-1.5.4/neon/
./configure --prefix=/usr/local --with-ssl --with-pic
make
sudo make install
cd ..
rm -rf neon
./configure --prefix=/usr/local --with-ssl --with-neon=/usr/local
make
sudo make install
cd ..
rm -rf subversion-1.5.4
rm subversion-1.5.4.tar.gz
rm subversion-deps-1.5.4.tar.gz
cp ~/servers ~/.subversion/servers
exit 0

```

**Verify your subversion version:**

Run: 

```
svn --help
```

Output:

```

usage: svn <subcommand> [options] [args]
Subversion command-line client, version 1.5.4.
...
...

```

I have used this script several times and it works great for me.

Hope this helps!

Comments/Suggestions?

---

