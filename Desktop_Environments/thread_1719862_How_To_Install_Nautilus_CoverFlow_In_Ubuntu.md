---
title: "How To Install Nautilus CoverFlow In Ubuntu"
date: 2011-04-02
forum: Desktop Environments
---

### Post by erik09 on 2011-04-02
I very like it 
Please help me install it 
I'm a new . Thank so much

[IMG]http://i989.photobucket.com/albums/af20/tuan10/CoverFlow.png[/IMG]

---

### Post by Enigmapond on 2011-04-02
A simple google would have done the trick.. :)

[http://www.omgubuntu.co.uk/2010/02/how-to-install-nautilus-coverflow-in-ubuntu/](http://www.omgubuntu.co.uk/2010/02/how-to-install-nautilus-coverflow-in-ubuntu/)

Cheers!

Oh & Welcome to the forum.. :)

---

### Post by jonbwilson on 2011-04-02
> **Enigmapond said:**
> A simple google would have done the trick.. :)

[http://www.omgubuntu.co.uk/2010/02/how-to-install-nautilus-coverflow-in-ubuntu/](http://www.omgubuntu.co.uk/2010/02/how-to-install-nautilus-coverflow-in-ubuntu/)

Cheers!

Oh & Welcome to the forum.. :)

FYI, the links in that article are broken. I've been looking around on Google for about 15 minutes now and there isn't really anything super helpful out there I could find. I'm interested in installing it now, too :)

---

### Post by jonbwilson on 2011-04-02
Ok, if you're using Ubuntu 10.10, coverflow, or clutterview, is already installed with Nautilus-Elementary.  You just need to activate it.  Check this out:

[http://gbutola.wordpress.com/2010/10/16/enable-clutter-view-in-nautilus-elementary/]("http://gbutola.wordpress.com/2010/10/16/enable-clutter-view-in-nautilus-elementary/")

Assuming you already have Nautilus-Elementary installed:

Open terminal and type&#8230;

```
gksu gedit /etc/environment
```

You'll be asked for your admin password, then a text editor will come up. Add this line to the end of the doc:

```
export CLUTTER_VBLANK=none
```

Save the doc and close it.  Log in and log out.

Now open up your documents folder or your home folder or whatever, then press F4.  You should now be able to use coverflow. 

Hope this works for you.

---

