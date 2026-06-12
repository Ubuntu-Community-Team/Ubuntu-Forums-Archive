---
title: "Steam wont launch Ubuntu 16.04.2 LTS"
date: 2017-05-14
forum: Gaming &amp; Leisure
---

### Post by nanastick on 2017-05-14
i have been searching for a couple of hours to fix the problem. I have  even reinstalled ubuntu but still no joy. This is what I get when I run  steam from the terminal.


keith@keith-MS-7693:~$ steam
Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
[2017-05-14 19:49:20] Startup - updater built Apr 25 2017 22:45:11
[2017-05-14 19:49:20] Verifying installation...
[2017-05-14 19:49:20] Verification complete
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1

I have the latest amd drivers installed for rx480.
Any ideas how to solve this?
Thanks, 
Keith

---

### Post by Perfect Storm on 2017-05-14
Try:
```
Exec=env LC_ALL=C steam $@
```

Are there any othr errors than you posted?

or try:
```
steam -tcp
```

I'm running nvidia card and the refresh is set to 60 in the terminal.

---

