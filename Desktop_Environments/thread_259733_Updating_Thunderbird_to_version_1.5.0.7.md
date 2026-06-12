---
title: "Updating Thunderbird to version 1.5.0.7"
date: 2006-09-17
forum: Desktop Environments
---

### Post by sjpritch25 on 2006-09-17
I use this command to update Firefox
```
gksudo firefox
```

What is the code to update Thunderbird????

I tried ```
gksudo thunderbird
```

However, that didn't work.  


Thanks in advance.

---

### Post by blontz29 on 2006-09-18
Try this...

```
gksudo mozilla-thunderbird
```

---

### Post by darkali on 2006-09-18
> **blontz29 said:**
> Try this...

```
gksudo mozilla-thunderbird
```

I tried that but thunderbird said there were no updates available.

I have 1.5.0.5 from repos.

---

### Post by blontz29 on 2006-09-18
I followed the instructions here to install Firefox and Thunderbird from Mozilla

[https://help.ubuntu.com/community/FirefoxNewVersion]("https://help.ubuntu.com/community/FirefoxNewVersion")

I followed the link on that page that has the scripts to automate the installation.  You can find that page here...

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5")

Hope this helps.

---

### Post by sjpritch25 on 2006-09-18
Yeah that didn't work for me either.  It wanted to setup Thunderbird.  Anyways, i believe the last update i recieved for Thunderbird was through automatic updates, so i will just wait.  Thanks.

---

### Post by blontz29 on 2006-09-19
When you do the the gksudo for Thunderbird, it seems as though you are setting up Thunderbird.  You just have to cancel everything until you are into the program.  Then "Check For Updates".  After it completes, quit and restart Thunderbird.  It will be the newest version.

---

