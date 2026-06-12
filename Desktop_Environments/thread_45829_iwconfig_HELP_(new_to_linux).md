---
title: "iwconfig HELP (new to linux)"
date: 2005-07-01
forum: Desktop Environments
---

### Post by jaross on 2005-07-01
ok, so, I just got UBUNTU. I installed DAMN SMALL Linux just to see if i could use linux with all my hardware. I have no problem with getting even my wireless card to work. all I did was open the controll panel thing on the desktop and click iwconfig. there was a simple box that had text boxes for the ssid, wep key, CHANNEL and I think that may have been it. my internet worked as soon as i hit ok...

So I kind of want somthing a little more substancial then damn small, becuase my sister is going to be surfing the internet and stuff and it would be nice to have somthing with Gnome.

So, I just finished installing Ubuntu. I put in all the info for my wireless car as it promped me. the internet doesnt work. cant even get to my routers address. Im almost positive that it is becuase I need to input what channel im running my router on -becuase I had the same problem on DAMN SMALL, until I put in the channel. so, i go into terminal, and type in "iwconfig eth0 channel 10" and I get:

"Error for wireless request "set frequency" (8B04) :
SET failed on device eth0 ; Operation not supported."

during installation it never asked me what channel to go on.

so Im assuming I dont need ndiswrapper becuase my interent worked fine withought it on damn small (ya damn small had it in that controll pannel I went into for iwconfig, but I never used ndiswrapper in damn small and it reconised my wireless card and worked fine.


help please.


Just figured out what it is going. as soon as I change my router to channel 9, my linux machine changes to channel 8. and so on, it just keeps changing to one lower then what I have set. how do I fix this?

---

### Post by mohaham on 2005-07-01
what wireless card do u have..
type lsmod on the terminal and see if its driver module has been loaded
is yes then post ur "/etc/networks/interface"  file here..

---

### Post by jaross on 2005-07-01
it is a linksys wmp11.  but aarently I would asume that it is an older version that works with linux because it worked fine in damn small.

ill update once i do what you said though.  ill have to put that file on a cd because obviously I cant get on the Internet with that machine.

---

### Post by jaross on 2005-07-01
what exactly am i looking for when I put lsmod into the terminal?

I looked in device manager.  unless "prism 2.5 wavelan chipset" is it, its not there.  (im assuming that is it, sure sounds like it)

---

### Post by jaross on 2005-07-01
ok i got it working, but this is a stupid question.  how do I get to my new install of firefox 1.0.4?  I searched for files and all that stuff but when I click on firefox through the menues, it opens 1.0.2.

---

### Post by varunus on 2005-07-02
Well, the best way to do it is to enable the backports repository (it contains new software that has proven to be stable, such as Firefox 1.0.4).  Then, use Synaptic to get the newest Firefox.

To do this, go to Synaptic, go to Settings->Repositories, click add, choose Custom, and type the following:
```

deb http://ubuntu-backports.mirrormax.net/hoary-backports main universe multiverse restricted
```

You may also want to add the Hoary Extras repository, to do this, do the same thing, but type:
```

deb http://ubuntu-backports.mirrormax.net/hoary-extras main universe multiverse restricted
```

Good luck.

---

