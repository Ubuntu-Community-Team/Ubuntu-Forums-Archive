---
title: "Repositories (new to linux)"
date: 2006-01-15
forum: Desktop Environments
---

### Post by extension on 2006-01-15
I am trying to install Cedega with the WineCvS script but the first thing that you are instructed to do is apt-get a list of dependencies. When I try:

apt-get install libjpeg-devel

I am told that it can not find the package. I am new to linux so I am unsure how to solve this problem. I have searched the web for info on getting this package but am unsure if I should just download it from anywhere or if I need a Kubuntu specific package. Many other packages are also unable to be found. I went into adept and enabled all the repositories that were disabled but this didnt help either.

Thanks

---

### Post by GeneralZod on 2006-01-15
Check out

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

and try

```

sudo apt-get install libjpeg62-dev

```

---

### Post by solarwind on 2006-01-15
you might want to create a root password and using adept

i like adept much better and find it easier to use

---

