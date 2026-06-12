---
title: "Bash script to install &amp; setup system"
date: 2009-04-06
forum: General Help
---

### Post by KayakJim on 2009-04-06
I need to setup several systems with the same configuration. As such, I would like to create a shell (bash) script that I can run on each system that will automate this process. My stopping point is how do I respond to prompts during package installation?

For example, when installing the MySQL5 package you are prompted for the root user's password. In my script, I would have:
```
# MySQL5
apt-get -y install mysql-server mysql-client libmysqlclient15-dev

```

Is there a way to place the password in the script so that when the install process prompts the entry is made and the script can continue?

---

### Post by kanikilu on 2009-04-06
I haven't tried this myself, but debconf-set-selections seems to be what you are looking for:

[http://ubuntuforums.org/showthread.php?t=677482](http://ubuntuforums.org/showthread.php?t=677482)
[https://answers.launchpad.net/ubuntu/+source/debconf/+question/59163](https://answers.launchpad.net/ubuntu/+source/debconf/+question/59163)

---

