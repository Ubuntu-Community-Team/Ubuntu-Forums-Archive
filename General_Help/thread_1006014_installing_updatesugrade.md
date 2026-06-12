---
title: "installing updates/ugrade"
date: 2008-12-08
forum: General Help
---

### Post by arvsr1988 on 2008-12-08
hey is there a command to install updates through the terminal in ubuntu 8.04?? and how about upgrading to ubuntu 8.10?? will the apt-get upgrade dist do the work or do i have to download ubuntu 8.10 first?

---

### Post by taurus on 2008-12-08
A few methods, [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading).

---

### Post by HotShotDJ on 2008-12-08
> **arvsr1988 said:**
> hey is there a command to install updates through the terminal in ubuntu 8.04??```
sudo apt-get update
sudo apt-get upgrade
```> **arvsr1988 said:**
> and how about upgrading to ubuntu 8.10??```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by arvsr1988 on 2008-12-08
i did sudo apt-get update but it only updates the list of packages... it doesnt install the updates.... even though there was information on the taskbar that said some 8 updates were available...

---

### Post by HotShotDJ on 2008-12-08
> **arvsr1988 said:**
> i did sudo apt-get update but it only updates the list of packages... it doesnt install the updates.... even though there was information on the taskbar that said some 8 updates were available...You need to execute BOTH commands listed in that code bock.  You didn't run the second one:  sudo apt-get upgrade

The same holds true with the second code block for upgrading to 8.10.  First "sudo apt-get update" and then "sudo apt-get dist-upgrade"

---

### Post by arvsr1988 on 2008-12-08
done..thanks!! will have to try next time updates are available..

---

