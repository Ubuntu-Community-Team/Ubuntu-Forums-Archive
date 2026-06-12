---
title: "Gnome 3 broke my Ubuntu 11.04"
date: 2011-05-02
forum: Desktop Environments
---

### Post by Seregwethrin on 2011-05-02
Hi,

I did exactly this tutorial says
[http://news.softpedia.com/news/How-to-Install-GNOME-3-on-Ubuntu-11-04-194085.shtml](http://news.softpedia.com/news/How-to-Install-GNOME-3-on-Ubuntu-11-04-194085.shtml)

But now my Ubuntu 11.04 is stuck at blue-white login screen.

Only User Defined Session and Recovery Console options are available but they are not working as well.

But when I did the Gnome 3 upgrading, it asked for me to remove unused packages and I said yes. About 20 packages removed.

Do I need to reinstall my Ubuntu? Or can I get my old Gnome 2? (Not Unity, I didn't like it.)

---

### Post by flintman on 2011-05-02
This is how i removed from my system after playing around with it
```
> sudo apt-get install ppa-purge
> sudo ppa-purge ppa:gnome3-team/gnome3
```

Hope that helps

---

