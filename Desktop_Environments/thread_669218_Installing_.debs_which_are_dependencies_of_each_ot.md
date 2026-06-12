---
title: "Installing .debs which are dependencies of each other?"
date: 2008-01-16
forum: Desktop Environments
---

### Post by Starcraftmazter on 2008-01-16
Hello.

I want to have the absolute latest version of kvirc running. Luckily, they supply debian files kvirc and kvirc-data.

The problem is, that both files are dependencies of each other. If I try to install them ignoring dependencies, it doesn't quite work.

Does anyone know how to install files in situations like these?


Thanks!

---

### Post by meindian523 on 2008-01-16
Use Synaptic/Add/Remove or apt-get.It's usually that the app has a dependency app-data,so install app-data first in case you can't find kvirc using the package manager outlined above.

---

### Post by Starcraftmazter on 2008-01-16
> **meindian523 said:**
> Use Synaptic/Add/Remove or apt-get.It's usually that the app has a dependency app-data,so install app-data first in case you can't find kvirc using the package manager outlined above.

Where exactly in Synaptic? Note that these packages conflict with the ones in the Ubuntu repos, and are downloaded manually.

---

### Post by meindian523 on 2008-01-16
Then it's preferable to install the ones in the Ubuntu repos.And about where exactly in Synaptic,there's a search function which just begs to be used.

---

### Post by meindian523 on 2008-01-16
If you are installing kvirc just because it's a IRC client,I would recommend Gaim(aka Pidgin),it's already installed by default and all you have to do is create an account.

---

### Post by Starcraftmazter on 2008-01-16
> **meindian523 said:**
> Then it's preferable to install the ones in the Ubuntu repos.And about where exactly in Synaptic,there's a search function which just begs to be used.

I think you probably misunderstood me. When I said where in Synaptic, I was not referring to the ones in the repos, but the ones I downloaded.

And if course it's preferred that I use the ones in the repos, but if I was content with that, I would not have made this thread.

And I already use kvirc, the problem is that Ubuntu 7.10 repos have the 3.2.4 version, and I was the latest cvs, which is past 3.2.6.

---

### Post by meindian523 on 2008-01-16
Manually downloaded debs won't show up in Synaptic until they are installed.
Gdebi package manager also does a fine job of handling dependencies,that can be launched by just double clicking your deb and input your password and that's that.

---

### Post by SeaJey on 2008-01-16
Open terminal, cd to the dir, where your .debs are, print ```
sudo dpkg -i *.deb 
```

---

### Post by meindian523 on 2008-01-16
Yeah,that's the CLI version of it.

---

### Post by Starcraftmazter on 2008-01-16
Thanks, done.

---

### Post by meindian523 on 2008-01-17
Ok,please mark the thread as solved.

---

