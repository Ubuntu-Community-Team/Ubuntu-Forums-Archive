---
title: "problem seems related to docker and dns"
date: 2020-07-11
forum: Debian
---

### Post by massrb on 2020-07-11
I seem to have a problem very similar to what is described here:

[https://medium.com/@faithfulanere/solved-docker-build-could-not-resolve-archive-ubuntu-com-apt-get-fails-to-install-anything-9ea4dfdcdcf2](https://medium.com/@faithfulanere/solved-docker-build-could-not-resolve-archive-ubuntu-com-apt-get-fails-to-install-anything-9ea4dfdcdcf2)


When I run a make command that kicks of docker-compose build, some of the apt-get install fail:

[COLOR=#1D1C1D][FONT=Slack-Lato]Failed to fetch [/FONT][/COLOR][http://deb.debian.org/debian/pool/main/p/python-defaults/python-minimal_2.7.13-2_amd64.deb]("https://slack-redir.net/link?url=http%3A%2F%2Fdeb.debian.org%2Fdebian%2Fpool%2Fmain%2Fp%2Fpython-defaults%2Fpython-minimal_2.7.13-2_amd64.deb")[COLOR=#1D1C1D][FONT=Slack-Lato]  400  Bad Request[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]E: Failed to fetch [/FONT][/COLOR][http://deb.debian.org/debian/pool/main/p/python-defaults/libpython-stdlib_2.7.13-2_amd64.deb]("https://slack-redir.net/link?url=http%3A%2F%2Fdeb.debian.org%2Fdebian%2Fpool%2Fmain%2Fp%2Fpython-defaults%2Flibpython-stdlib_2.7.13-2_amd64.deb")[COLOR=#1D1C1D][FONT=Slack-Lato]  400  Bad Request[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]E: Failed to fetch [/FONT][/COLOR][http://security.debian.org/debian-security/pool/updates/main/i/icu/libicu57_57.1-6+deb9u4_amd64.deb]("https://slack-redir.net/link?url=http%3A%2F%2Fsecurity.debian.org%2Fdebian-security%2Fpool%2Fupdates%2Fmain%2Fi%2Ficu%2Flibicu57_57.1-6%2Bdeb9u4_amd64.deb")[COLOR=#1D1C1D][FONT=Slack-Lato]  400  Bad Request [IP: 151.101.128.204 80][/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]E: Failed to fetch [/FONT][/COLOR][http://security.debian.org/debian-security/pool/updates/main/i/imagemagick/libmagickcore-6.q16-3_6.9.7.4+dfsg-11+deb9u8_amd64.deb]("https://slack-redir.net/link?url=http%3A%2F%2Fsecurity.debian.org%2Fdebian-security%2Fpool%2Fupdates%2Fmain%2Fi%2Fimagemagick%2Flibmagickcore-6.q16-3_6.9.7.4%2Bdfsg-11%2Bdeb9u8_amd64.deb")[COLOR=#1D1C1D][FONT=Slack-Lato]  400  Bad Request [IP: 151.101.128.204 80][/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]E: Failed to fetch [/FONT][/COLOR][http://security.debian.org/debian-security/pool/updates/main/e/exim4/exim4-config_4.89-2+deb9u7_all.deb]("https://slack-redir.net/link?url=http%3A%2F%2Fsecurity.debian.org%2Fdebian-security%2Fpool%2Fupdates%2Fmain%2Fe%2Fexim4%2Fexim4-config_4.89-2%2Bdeb9u7_all.deb")[COLOR=#1D1C1D][FONT=Slack-Lato]  400  Bad Request [IP: 151.101.128.204 80][/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]E: Failed to fetch [/FONT][/COLOR][http://security.debian.org/debian-security/pool/updates/main/e/exim4/exim4-daemon-light_4.89-2+deb9u7_amd64.deb]("https://slack-redir.net/link?url=http%3A%2F%2Fsecurity.debian.org%2Fdebian-security%2Fpool%2Fupdates%2Fmain%2Fe%2Fexim4%2Fexim4-daemon-light_4.89-2%2Bdeb9u7_amd64.deb")[COLOR=#1D1C1D][FONT=Slack-Lato]  400  Bad Request [IP: 151.101.128.204 80][/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]E: Failed to fetch [/FONT][/COLOR][http://security.debian.org/debian-security/pool/updates/main/o/openldap/libldap-common_2.4.44+dfsg-5+deb9u4_all.deb]("https://slack-redir.net/link?url=http%3A%2F%2Fsecurity.debian.org%2Fdebian-security%2Fpool%2Fupdates%2Fmain%2Fo%2Fopenldap%2Flibldap-common_2.4.44%2Bdfsg-5%2Bdeb9u4_all.deb")[COLOR=#1D1C1D][FONT=Slack-Lato]  400  Bad Request [IP: 151.101.128.204 80][/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]ERROR: Service 'vets-api' failed to build: The command '/bin/bash -c apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y     dumb-init clamav clamdscan clamav-daemon imagemagick pdftk curl poppler-utils libpq5 vim' returned a non-zero code: 100[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]make: *** [Makefile:94: rebuild] Error 1

If I do similar installs outside of docker, it seems fine. 

my /etc/resolve.conf has  [/FONT][/COLOR]127.0.0.53


I am fairly baffled

---

### Post by deadflowr on 2020-07-11
*Thread moved to **Debian***

---

### Post by TheFu on 2020-07-13
Are you trying to use a docker container like a full OS?  If so, that isn't their purpose. Compiling, linking, installing stuff while inside a docker container isn't a best practice.

Probably should mention what version of debian is being used too since python recently deprecated python 2.x completely. Probably need to be on an older Debian release.

 /etc/resolve.conf  isn't a config file that gets used by any Unix system. That's a typo, right?

---

