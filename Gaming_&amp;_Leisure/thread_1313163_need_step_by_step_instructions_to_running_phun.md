---
title: "need step by step instructions to running phun"
date: 2009-11-03
forum: Gaming &amp; Leisure
---

### Post by rk_marie on 2009-11-03
I'm very new to Ubuntu and am having a lot of trouble getting Phun to work. I downloaded it from phunland.com and after I clicked on the download then clicked on the folder I had two options, "phun" or "phun.bin". The "phun" one had the following message:


#!/bin/sh

LD_LIBRARY_PATH="./lib:${LD_LIBRARY_PATH}" ldd phun.bin | grep "not found" > /dev/null 2>&1

if [ "$?" -eq "0" ]; then
  cat << _EOF_
  There are missing dependencies.
  Please make sure that all the required libraries are installed.
  Missing:
_EOF_
  LD_LIBRARY_PATH="./lib:${LD_LIBRARY_PATH}" ldd phun.bin | grep "not found" 
else
  LD_LIBRARY_PATH="./lib:${LD_LIBRARY_PATH}" ./phun.bin $@
fi


and then the "phun.bin" one said that it couldn't perform the operation. I'm a complete beginner I need simple step by step instructions, I know how to open the terminal but I don't know many commands. Also, I'm sure that I downloaded the newest Linux version, 32 bit. I have Ubuntu 9.04, I'm in the process of downloading 9.10. Thank you.

---

### Post by nadian on 2009-11-24
the easiest way is to go to:
[http://old.getdeb.net/release/4553](http://old.getdeb.net/release/4553)
(it's not in new repositories but still in the old one)
click download phun
then open downloaded package - or if using firefox it will install itself once downloaded if you click install now button
and you should find it under applications / games
have phun!

---

