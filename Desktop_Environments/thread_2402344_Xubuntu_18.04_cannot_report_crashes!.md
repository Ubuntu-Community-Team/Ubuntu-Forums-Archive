---
title: "Xubuntu 18.04 cannot report crashes!"
date: 2018-09-28
forum: Desktop Environments
---

### Post by elmarciano18 on 2018-09-28
Hello!

I have a fresh Xubuntu 18.04 installation.
Everytime there is a crash, the whoopsie dialogue appears and I affirm to report the crash report.
But it can't send the report, because there's always this bug:

[IMG]https://image.ibb.co/hFwoSU/whoopsie.png[/IMG]

---

### Post by elmarciano18 on 2018-10-11
Hello? Doesn't anyone care for this? I think it's an essential problem if bug reporting doesn't work.

---

### Post by wildmanne39 on 2018-10-11
I just read that whoopsie is not installed by default in most buntu version but it is in ubuntu, so you might try:

```
sudo apt install --reinstall whoopsie
```
not sure that will help if not you need to check and see if a bug report has been filed against apport if not create a new report, how to do that is here.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by elmarciano18 on 2018-10-15
Hello!

Thank you for helping.
I checked and saw that whoopsie was already installed. I made the reinstall as you suggested anyway.
But the problem remains :(

I'm not even sure what this message mean. Does it mean that the crash report is working, but that it just couldn't save the setting to automatically report without asking in future?
Or doesn't the report work at all?

---

### Post by elmarciano18 on 2018-11-12
Hello!

Still suffering from this.
Does anyone know of this problem?

---

### Post by ncweber on 2019-02-18
I have a fresh install of Xubuntu 18.10 64-bit and I am experiencing the same issue.  No one seems to know and outside of askubuntu and ubuntuforums, I can find no one else asking about this.

---

### Post by elmarciano18 on 2019-02-19
Hello!

I ended up uninstalling whoopsie, because I could not find a solution.
After you wrote I now did a new search and found [this]("https://bugs.launchpad.net/ubuntu/+source/whoopsie-preferences/+bug/1810840").

> whoopsie-preferences is installed by default in Ubuntu, it should probalby be a recommends from apport though



So I now installed whoopsie and whoopsie-preferences - will have to see is that helps.
Still don't get why it takes this long to fix this obvious bug. Of course whoopsie-preferences should be installed by default, when it's used by a default GUI dialog.

---

