---
title: "small problem with add/remove programs"
date: 2006-09-09
forum: Desktop Environments
---

### Post by Zlatan on 2006-09-09
every time i start to use add/remove programs, it shows a pop-up window: 
"The list of available applications is out of date. To reload the list you need a working internet connection."
i suppose this is not normal, becouse my internet connection is working, so application list should be reloaded automatically;)
maybe anyone could help me with this?
thank you

---

### Post by xyz on 2006-09-09
Hello,
Did you enable all the software channels -check them all- in  System > Administration > Software Properties?
Also your repositories: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Check your sources.list:
```
sudo gedit /etc/apt/sources.list 
```
Let us know...

---

### Post by Zlatan on 2006-09-10
i found it. when repositories were from:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
there were problems.
and when i put repositories are from [http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)
the problem is gone.
thank you for your help;]

---

