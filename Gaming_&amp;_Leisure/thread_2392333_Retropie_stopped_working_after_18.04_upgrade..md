---
title: "Retropie stopped working after 18.04 upgrade."
date: 2018-05-19
forum: Gaming &amp; Leisure
---

### Post by jadaube2 on 2018-05-19
i installed Retropie on an Acer Aspire X1935 desktop with 17.10 per the instructions at [https://github.com/RetroPie/RetroPie-Setup/wiki/Debian#install-retropie](https://github.com/RetroPie/RetroPie-Setup/wiki/Debian#install-retropie). It worked perfectly until I upgraded to 18.04, after which I would receive the following error:

/opt/retropie/supplementary/emulationstation/emulationstation: /usr/lib/x86_64-linux-gnu/libcurl.so.4: version `CURL_OPENSSL_3' not found (required by /opt/retropie/supplementary/emulationstation/emulationstation)

Any ideas how to fix this?

---

### Post by thenailedone on 2018-05-21
Seems to be related to libcurl 4 vs 3 - [https://github.com/curl/curl/issues/2433](https://github.com/curl/curl/issues/2433)

Not sure if there is a solution yet, but it doesn't seem so - [https://bugs.launchpad.net/ubuntu/+source/curl/+bug/1754294](https://bugs.launchpad.net/ubuntu/+source/curl/+bug/1754294)

---

