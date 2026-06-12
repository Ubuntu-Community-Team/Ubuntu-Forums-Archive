---
title: "How to change over from KDE to GNOME"
date: 2006-09-12
forum: Desktop Environments
---

### Post by yoghurt on 2006-09-12
Hi I have a newbie question. I've downloaded and installed Kubuntu couple of months ago, but now I've realized I don't really like the graphics style of things + bunch of guides and documentation is written mainly with GNOME in mind.

Therefore, if I want to change from KDE to GNOME, what are the options/steps that need to be taken?

- is it better to remove KDE, then install GNOME?
- or re-install the whole Ubuntu?
- install GNOME, but keep KDE in place?

I'm wondering which of the three alternatives is the best; time/work wise?

Furthermore, I know how to reinstall the whole thing (oddly enough :D), but if I wanted to install GNOME in addition to KDE I'd have to do something like this?

```
sudo apt-get install ubuntu-desktop
```?

---

### Post by bigken on 2006-09-12
sudo apitutude install ubuntu-desktop then you have both worlds and to clean up any kubuntu icons from the applications list use alcarte menu editor :wink:

---

### Post by BerlinOliver on 2006-09-12
HI,

it is equal how you do it. 

sudo apt-get install ubuntu-desktop 

is one possibility which is easy and fast to do. There are no problems in this way. I did it the same. And you can choose your default desktop. (You also can do this with synaptic)

---

### Post by Stolie on 2006-09-12
**Haha, got beaten twice..**

You may actually want to use aptitude to install the ubuntu-desktop, because in my experience, aptitude takes care of dependencies better than apt-get. So, if I were to do this, I might do it something like this:

sudo aptitude install ubuntu-desktop

then:

sudo aptitude remove kubuntu-desktop

Now keep in mind that some time down the line, you may need something like the QT libraries, or something like that. Maybe also you would decide to go back to the KDE environment. It's really up to you whether or not you want to keep KDE in place..

Hope that helped!

---

### Post by kwalo on 2006-09-12
In case you want to remove kubuntu, use [this](http://www.psychocats.net/ubuntu/puregnome.php) tip.

---

### Post by yoghurt on 2006-09-12
Thanks a lot people, I'm definitely going to give it a shot! Just one other question though; would I need to do some changes to graphics card driver(s) when changing the environment?

---

### Post by Bagnaj97 on 2006-09-12
You wont need to edit your graphics card drivers. There's no harm in having both KDE and Gnome installed at once if you have the disc space, and you can choose which to use at the login screen.

---

### Post by yoghurt on 2006-09-12
Sounds good then... THANKS TO YOU ALL FOR SUGGESTIONS AND ADVICES!

---

