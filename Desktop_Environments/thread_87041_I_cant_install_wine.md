---
title: "I cant install wine"
date: 2005-11-07
forum: Desktop Environments
---

### Post by kolobaki on 2005-11-07
Well.I try to install wine.
I follow the instructions:
[COLOR="Black"]sudo nautilus[/COLOR] and then i add in source list theese:

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

After [COLOR="Black"]sudo apt-get update[/COLOR]
and then [COLOR="Black"]sudo apt-get install wine[/COLOR].

The setup is starting but during setup it says [COLOR="Red"]Impossible the transshipment of certain files, perhaps if you tryed with apt-get update to--fix-missing;[/COLOR]
I use it again but nothing.I have the ubuntu breezy 5.10
Can help me anyone?
Thanks!!

---

### Post by RawMustard on 2005-11-07
Breezy has wine in it's own repositories.  All I did was type sudo apt-get install wine
Then I just typed wine in the terminal and it set up my fake c drive.  Is there a special reason you're using another repo?

---

### Post by aysiu on 2005-11-07
I concur. Follow the directions in my sig. Then ```
sudo apt-get update
sudo apt-get install wine
``` It's better to use Ubuntu repositories when possible.

---

### Post by manicka on 2005-11-07
The version of wine at winehq is the latest beta release and solves many bugs that are present in version available in the the breezy repos.

Try the instructions here

[http://doc.gwos.org/index.php/Wine](http://doc.gwos.org/index.php/Wine)

---

