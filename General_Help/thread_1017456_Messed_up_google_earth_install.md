---
title: "Messed up google earth install?"
date: 2008-12-21
forum: General Help
---

### Post by ecom on 2008-12-21
help. i installed google earth by following this guide:

[http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/](http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/)

it installed it and i was able to run it the first time. everything worked correctly the first time. and the earth appeared.

but after i closed google earth and ran it again, all i see is a black screen. the earth didnt appear.

and there is an icon on my desktop with a lock symbol on it. 

help. i think it wont work bcoz it doesnt think i'm admin, but i am admin.

---

### Post by vanadium on 2008-12-21
Change the owner of the google config files from root to yourself:

```

sudo chown -R $USER:$USER ~/.config/Google

```

It is a mistake of Google to let users launch the application from the install program. The install program runs with root permissions. When Google Earth is launched from within the instal program,  it has root permissions as well. A subsequent time, it is is run with user permissions and cannot access the config files anymore.

Probably, just deleting ~/.config/Google (as root) would also work.

---

### Post by ecom on 2009-01-03
i solved the problem by typing:

sudo googleearth

but is this a proper solution? i mean, every time i wanna use google earth, just open the terminal and type "sudo googleearth"

---

### Post by ecom on 2009-01-17
ok fine. 3 weeks have elapsed and i guess my solution and vanadium's solution are both correct.

---

### Post by poodoopealeoaph on 2011-03-10
well you are right with typing sudo googleearth but you can save yourself a little time by right clicking the launcher, going to properties, then changing the "command" line to sudo googleearth. that way the launcher will just execute that line when you click it. The other way is to rightclick your top panel and select "create launcher" then fill in the correct information.

---

### Post by catlover2 on 2011-03-10
that would have to be "gksudo googleearth" because just 'sudo' only works with the command line.

---

### Post by Omar11 on 2011-03-28
how I got google earth is that you download lsb-core 4.0 by ubuntu software, then you download the .deb file from the google earth website and right click, and open it with ubuntu software centre. After that, install it and you should see google earth in **Applications->Internet->Google earth**
Hav funz
[SIZE="2"]P.S. I would download all lsb systems except the mail lsb systems.[/SIZE]

---

### Post by Omar11 on 2011-03-28
Btw, you are using a non-supported ubuntu os, you should rather upgrade, or, stick to windows or mac.

---

