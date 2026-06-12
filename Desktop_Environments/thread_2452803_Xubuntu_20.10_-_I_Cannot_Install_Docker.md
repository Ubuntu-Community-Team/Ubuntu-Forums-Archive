---
title: "Xubuntu_20.10 - I Cannot Install Docker"
date: 2020-10-28
forum: Desktop Environments
---

### Post by jt3222 on 2020-10-28
Hello,

When I try to install Docker, I get the following errors:

$ sudo apt update

Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) groovy InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) groovy-updates InRelease             
Hit:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) groovy-backports InRelease           
Hit:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) groovy-security InRelease              
Ign:6 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) groovy InRelease           
[COLOR=#ff0000]Err:7 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) groovy Release
  404  Not Found [IP: 13.226.94.89 443]
Reading package lists... Done
E: The repository 'https://download.docker.com/linux/ubuntu groovy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.[/COLOR]
N: See apt-secure(8) manpage for repository creation and user configuration details.

$ sudo apt install docker-ce
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package docker-ce is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

[COLOR=#ff0000]E: Package 'docker-ce' has no installation candidate

[/COLOR]Thank you,

John...[COLOR=#ff0000][/COLOR]

---

### Post by ActionParsnip on 2020-10-28
[https://download.docker.com/linux/ubuntu/dists/](https://download.docker.com/linux/ubuntu/dists/)
The source doesn't support Groovy and should be removed

Docker is in the default repos
[https://packages.ubuntu.com/groovy/docker](https://packages.ubuntu.com/groovy/docker)

So I have no idea why you are adding additional sources. You could have just ran
```

sudo apt update
sudo apt install docker

```

and docker would have installed.........

---

### Post by jt3222 on 2020-10-28
Thanks friend, I was following instructions from a website and it worked in version 20.04. So the issue that I ran into is because the Docker repo does not support 20.10/Groovy yet?

---

### Post by CelticWarrior on 2020-10-28
> **jt3222 said:**
> So the issue that I ran into is because the Docker repo does not support 20.10/Groovy yet?

Exactly.

---

### Post by ActionParsnip on 2020-10-30
Remove the package source you added then install just as you would any other package

---

### Post by jt3222 on 2020-10-30
It worked, thanks.

---

