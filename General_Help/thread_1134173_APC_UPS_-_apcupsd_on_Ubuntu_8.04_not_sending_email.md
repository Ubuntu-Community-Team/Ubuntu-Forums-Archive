---
title: "APC UPS - apcupsd on Ubuntu 8.04 not sending emails"
date: 2009-04-23
forum: General Help
---

### Post by trileru808 on 2009-04-23
Hello, I have an Ubuntu 8.04 server running a samba domain and I have the computer attached to a APC UPS. I installed apcupsd via apt-get. The software runs smooth, it detects the powerouts and acts accordingly (it shuts down the computer when 3 mins of power remaining) but it doesn't notify me via email. Thing is I use ssmtp, i configured it good, modified the onbattery and offbattery scripts, they work when i call them via ./ or sh but not on power loss. they even work when i try "./apccontrol onbattery" or "./onbattery" . I receive the email. but they won't work when the power goes out or in again. What can I do?

permissions are ok, script files look like this:
onbattery:

#!/bin/sh
#
# This shell script if placed in /etc/apcupsd
# will be called by /etc/apcupsd/apccontrol when the UPS
# goes on batteries.
# We send an email message to root to notify him.
#
ssmtp [email]bob@mydomain.com[/email] < a

exit 0

"a" file:

To: [email]bob@mydomain.com[/email]
From: [email]sambaups@mydomain.com[/email]
Subject: Power Alert

The Samba Server power supply is out!!!


I don't know what to do, i tryed almost everything. Any ideea is wellcome. Thanks guys and have a nice day

---

