---
title: "Ubuntu stuck at startup!"
date: 2007-02-01
forum: Desktop Environments
---

### Post by dkokelley on 2007-02-01
The last thing I remember was trying to play a DVD... 

So here's the situation: Ubuntu locked up after trying to see if I could manage to play a DVD on it. I searched and found a few solutions for DVD playback, but they didn't work. I figured that possibly logging out and back in would fix this, so I logged out, to be greated by an Ubuntu login screen with no words or buttons. I was stuck there, so I held the power button down on my laptop to shut 'er down and then restart. After starting back up, the system worked fine up until the screen that says "ubuntu" or "kubuntu" in my case (though I really only use Ubuntu and was using Ubuntu when this problem started) and has that little bar underneath that "loads," As soon as the bar reaches the end nothing happens. I would wait for several minutes and nothing would happen. I will gladly provide any information needed to help figure this thing out (just tell me what to do!). I am fairly new to Ubuntu (3 days old now, after dipping my feet in the water a while back with 6.06). The version of Ubuntu not working right now is 6.10.

I reinstalled 6.06 from the live CD I was sent on a separate partition so that I could check the forums for possible solutions. I also was hoping that I could get some information off of the other HD partition, but when I navigate to the hard drive and try to open it I get this error message: 

"Unable to mount the selected volume.
error: device /dev/sda1 is not removable
error: could not execute pmount"

I figured worst case I could salvage my information from that partition (and move it to an external hard drive), and reinstall from the live CD then do all my updates again. But now it seems that's not even an option. I would really appreciate any help on this. Thanks.

---

### Post by bwhite82 on 2007-02-03
Are you able to boot with the "Failsafe option"? (Can't remember if that is the correct term) If so, then more than likely it is a graphics problem, you would need to reconfigure your xorg.conf file. Anytime I make changes in the xorg.conf that aren't compatible with my card, on that "load bar" it always freezes right at the end with a green line going through my screen.

Not sure that that is the problem for you, simply trying to help you out.

---

### Post by dralnu on 2007-02-03
check your logfiles from the other install. If it is a problem with X, chances are it will show up in your Xorg.log files.

I would try to boot into a CLI personally, and make sure I have a working system, but I don't know how much of a pain that would be to do with Ubuntu honestly (read a manual somewhere to try and stop it from going into rl5).

Or you could just make a tar/bz2 backup of your settings/home dir, and reinstall. Copy the archive to a CD/DVD (depending on what is avalible and whatnot).

---

