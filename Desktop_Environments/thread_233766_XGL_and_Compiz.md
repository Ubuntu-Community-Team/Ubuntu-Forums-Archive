---
title: "XGL and Compiz"
date: 2006-08-10
forum: Desktop Environments
---

### Post by chedabob on 2006-08-10
[http://www.tectonic.co.za/view.php?id=916&page=2](http://www.tectonic.co.za/view.php?id=916&page=2)

so basically, i followed that guide, and Compiz and XGL work fine, BUT, they are really old plugins. scale doesnt have all its features, and i cant get Water to run (cos its not installed). 

Where can i download these from? Cos everytime I update, or follow another guide, it just messes up really badly. Ive reinstalled ubuntu 7 or 8 times over the past 3 days, following various guides. So far this guide is the only one that works, but id like all the features.

Thanks

---

### Post by skymt on 2006-08-10
You say you've followed the guides, but it "messes up really badly." You don't say how it messes up, so I can't tell you how to fix it.

Also, the guides are based on what worked for someone. I'd say maybe they aren't working for you because the recent versions with fancy new features just *don't work* on your system. There's a reason the version number is so low. It's because it isn't done yet. Be patient. In six months to a year, everyone will have XGL (or AIGLX or whatever) and be happy.

---

### Post by bulldog on 2006-08-10
Don't know if you did use this one.
[http://www.compiz.net/viewtopic.php?id=652](http://www.compiz.net/viewtopic.php?id=652)

Have it installed and it works like a charm.
I use the CGWD-themer and themes too.
All very nice and up to date.

Maybe you should look around on this forum and see if there is anything you like.
[http://www.compiz.net/viewforum.php?id=5](http://www.compiz.net/viewforum.php?id=5)

Much info and you can post your questions and problems.

---

### Post by crackseller on 2006-08-10
Do you mind telling me how you got it working with cgwd. I try to use it in xfce but it doesn't seem to work, maybe cuz all guides are for gnome(?). Thanks in advance!

---

### Post by chedabob on 2006-08-10
on most of the guides, it didnt work at all. gnome would load, but i wouldnt have any features.

on some of the guides, it did the same, but it was either really slow, or i had awful tearing.

on some of them, id do a reboot, ready to load it up, and then just churned some xserver error in my face.

will there be a time in the future, where XGL will be as simple as selecting the package in Synaptic, then it works, or will it always need configuration?

cos if so, then i may wait for a while, sticking with the one ive got. im just gettin a bit annoyed havin to reinstall ubuntu over and over when it messes up, because most of the time, it overwrites the default Gnome configuration, so easiest fix is a reinstall.

i really wanna use XGL, because in my opinion, it makes working faster. no longer do i have to cycle through all my desktops to find "X", i can just rotate the cube and see it. and the "Konspose" function makes having multiple windows on screen . Mainly the only extra features i wanted were water (cos it looked so damn cool) and Scale, because currently i only have the Konspose feature.

---

### Post by chedabob on 2006-08-10
could you point me to a good guide for configuring XGL and Compiz with Gnome, and a radeon 9200se? 

and when should i install this? before or after i install flgrx? before or after i do a full update?

would it be worth me getting the latest LTS cd? and trying from there?

---

### Post by bulldog on 2006-08-11
On the compiz forums you should definitly find info on how to install with an ATI-card.
And you must install your video drivers first and before or after an update should not matter.
But it works the best with a nVidia-card is what I've been told.

To use CGWD with gnome you must make a change in you start script.
I use the python script and all you need to do is subscibed on the compiz forums.

def start_compiz():
	os.system("killall gnome-window-decorator")
	gobject.spawn_async(['cgwd'], \
			     flags=gobject.SPAWN_SEARCH_PATH)
	gobject.spawn_async(['compiz', '--replace', 'gconf'], \
			  flags=gobject.SPAWN_SEARCH_PATH)
------------------------------------------------------------
About CGWD,
Add these lines to your sources.list:

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

Do sudo apt-get update and now should CGWD and CGWD-themes appear in your synaptic just search on CGWD and you'l find it.

If you want more info just ask and I tell you everything I know about it.
But as I said,the most important info is on the compiz forums.

---

### Post by chadk on 2006-08-11
Also, just browse to [http://xgl.compiz.info/](http://xgl.compiz.info/) for some good info.

---

### Post by chedabob on 2006-08-11
i dunno which one to follow though, because of all the guides ive used, most of them just mess up and i end up doing a reinstall.

the current version ive got is a bit buggy, like new firefox windows are a bit too wide, until you click them. 

i got another version running earlier on, but when i tried to update to CGWD from gnome-window-decorator, it just failed miserably.

---

### Post by chedabob on 2006-08-11
im sat in a clean install right now, so if someone points me to a guide that works with Gnome and Ati Radeon 9200, ill have a go.

Edit:

Right, i just tried this guide

[http://www.compiz.net/topic-389-1.html](http://www.compiz.net/topic-389-1.html)

and its really slow. Is this cos of my graphics card, because i run at 1440x900?

---

