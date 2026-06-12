---
title: "Firefox 2.0.0.6 on Dapper - is this possible?"
date: 2007-08-29
forum: Desktop Environments
---

### Post by xp_newbie on 2007-08-29
Niether Update Manager nor Package Manager list Firefox 2.0 as being event available... Is there really no way to run Firefox 2.0 on Dapper (Ubuntu 6.06)? If so, why?

If not, what is the proper way of making it available in Synaptic Package Manager and updateable via Update Manager?

Thanks,
Alex

---

### Post by bmorency on 2007-08-29
> **xp_newbie said:**
> Niether Update Manager nor Package Manager list Firefox 2.0 as being event available... Is there really no way to run Firefox 2.0 on Dapper (Ubuntu 6.06)? If so, why?

If not, what is the proper way of making it available in Synaptic Package Manager and updateable via Update Manager?

Thanks,
Alex


I'm not sure of a way to have it in synaptic but you can just download it from [http://www.mozilla.com ]("http://www.mozilla.com") and extract the file. it should be ready to run when you extract it. you will have to make a menu item manually though.

---

### Post by sumguy231 on 2007-08-30
It's possible alright, it's just not in the Dapper repositories. Read this for detailed instructions:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by FuturePilot on 2007-08-30
Ubuntuzilla.
Download the appropriate .deb here
[http://sourceforge.net/project/showfiles.php?group_id=202789&package_id=241580]("http://sourceforge.net/project/showfiles.php?group_id=202789&package_id=241580")
Install it by double clicking on it.
Then put this in a terminal and follow the directions
```
ubuntuzilla.py -a install -p firefox
```
Then enjoy!:)

---

