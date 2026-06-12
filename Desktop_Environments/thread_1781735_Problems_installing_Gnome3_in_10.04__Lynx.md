---
title: "Problems installing Gnome3 in 10.04 / Lynx"
date: 2011-06-13
forum: Desktop Environments
---

### Post by akelsall on 2011-06-13
Hello, I'm trying to install gnome3 on Lucid Lynx / 10.04 and have tried several methods, but none work. I've tried the following:

sudo add-apt-repository ppa:gnome3-team/gnome3
gksu apt-get update
gnome-shell --replace

When I run the second command, I get this error message at the end:

> Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


When I do the last command, I get this:

> hiker@eno:~$ gnome-shell --replace
Panel leaving: a new panel shell is starting.

(gnome-panel:3098): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion `global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed

(mutter:8062): Clutter-WARNING **: The actor 'BigBox' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:8062): Clutter-WARNING **: The actor 'searchEntry' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:8062): Clutter-WARNING **: The actor 'BigBox' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:8062): Clutter-WARNING **: The actor 'dash' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:8062): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:8062): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended
Window manager warning: Log level 16: IA__g_object_set_valist: construct property "type" for object `ShellEmbeddedWindow' can't be set after construction
Window manager warning: Log level 16: IA__g_object_set_valist: construct property "type" for object `ShellEmbeddedWindow' can't be set after construction
Window manager warning: Log level 16: IA__g_object_set_valist: construct property "type" for object `ShellEmbeddedWindow' can't be set after construction
Window manager warning: Log level 16: IA__g_object_set_valist: construct property "type" for object `ShellEmbeddedWindow' can't be set after construction


I also tried:

sudo apt-get build-deb gnome-shell
sudo apt-get install gnome-shell
gnome-shell --replace

Same issue as above. Any idea what's happening?

Thanks,

Andy

---

### Post by mister_playboy on 2011-06-13
Right now the process is failing at the download packages step, so you'd need to insure the PPA you chose is actually online.  Where did you find these instructions?

Why exactly do you want to do this, anyway?  Running an older LTS release inherently means you aren't worried about the latest stuff.  Mixing new and old tends to break things.;)

---

### Post by akelsall on 2011-06-14
I want to play around with Gnome3 to see what it can do (so I can compare it to Unity when I upgrade to 11.04) Why wouldn't Gnome3 run properly on 10.04? 

I did multiple searches and tried a few of the suggestions to install Gnome3, but none worked :(

Thanks,

Andy

---

### Post by collisionystm on 2011-06-14
Just run natty in virtualbox or vmware player. Then you can break it as many times as you want!

---

### Post by FormatSeize on 2011-06-14
If you want to do a quick (or long) comparison of GNOME3 and Unity, I would find Live CDs of each and toy around with them as opposed to trying to install GNOME3 on top of something that it isn't native to. 
 
You could break your system, you could get a skewed view of what Unity and GNOME3 are capable of, or you may not have all the features that each one has going about trying to install it onto your current system. 
 
Also, how would you go about uninstalling it? With VirtuaBox or a Live CD, you don't have to worry about any of that.

---

### Post by 23dornot23d on 2011-06-14
Good advice - or a live Dvd even ..... have you tried this one out for Ubuntu but just
put together by some enthusiastic passionate people .....  [**LINK**]("http://ubuntuforums.org/showthread.php?t=1754198")

---

