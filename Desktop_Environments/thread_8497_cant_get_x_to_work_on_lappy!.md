---
title: "cant get x to work on lappy!"
date: 2004-12-17
forum: Desktop Environments
---

### Post by munkymonkjr on 2004-12-17
hi...

i installed ubuntu 4.1 Warty Warthog x86-64 on my 258kao but x doesnt start. i took pics of error messages so maybe i can get some help.

my lappy specs (if it matters):
uniwill 258kao
15.4" wxga      <---this might have something to do with the problem
ati 9700 128mb    <--coupled with this...why is ati so anti linux?
hitachi 7k60 (60gb 7200rpm)
AMD Atholon 64 3200+ Clawhammer
24x CD-RW/DVD Slimline

my distro:
Ubuntu Linux 4.10 Warty Warthog x86-64

my problem: x doesn't start.

error messages (in order): (5megapixel....56k warning)
Picture #1: [http://home.comcast.net/~therussian89/ubuntu1.JPG](http://home.comcast.net/~therussian89/ubuntu1.JPG)
(yes..my lappy is a widescreen)

Picture #2: [http://home.comcast.net/~therussian89/ubuntu2.JPG](http://home.comcast.net/~therussian89/ubuntu2.JPG)
(first error message...selected <Yes>)

Picture #3: [http://home.comcast.net/~therussian89/ubuntu3.JPG](http://home.comcast.net/~therussian89/ubuntu3.JPG)
(the basic error message....selected <OK>)

Picture #4: [http://home.comcast.net/~therussian89/ubuntu4.JPG](http://home.comcast.net/~therussian89/ubuntu4.JPG)
(same as above...diff angle...could be easier to read)

Picture #5: [http://home.comcast.net/~therussian89/ubuntu5.JPG](http://home.comcast.net/~therussian89/ubuntu5.JPG)
(would i like to see more errors....<Yes>)

Pucture #6: [http://home.comcast.net/~therussian89/ubuntu6.JPG](http://home.comcast.net/~therussian89/ubuntu6.JPG)
(more detailed error message...i think)

Picture #7: [http://home.comcast.net/~therussian89/ubuntu7.JPG](http://home.comcast.net/~therussian89/ubuntu7.JPG)
(same as 6...diff viewing angle)

Picture #8: [http://home.comcast.net/~therussian89/ubuntu8.JPG](http://home.comcast.net/~therussian89/ubuntu8.JPG)
(so it wants to disable my x now eh? selected <Yes>)

Picture #9: [http://home.comcast.net/~therussian89/ubuntu9.JPG](http://home.comcast.net/~therussian89/ubuntu9.JPG)
(it reads: "Ubuntu 4.10 "Warty Warthog lappy ttyt lappy login:")

Picture 10: [http://home.comcast.net/~therussian89/ubuntu10.JPG](http://home.comcast.net/~therussian89/ubuntu10.JPG)
(more errors after i try "startx" command)

Picture 11: [http://home.comcast.net/~therussian89/ubuntu11.JPG](http://home.comcast.net/~therussian89/ubuntu11.JPG)
(zoomed into the bottom of error in picture 10)


so...any suggestions on how i get it working?

or perhaps someobody can recommend a distro that works out of the box (ie...no tweaking) with Linksys WPA11 ver.3 802.11b wifi card?

thanks.

---

### Post by daniels on 2004-12-18
Please file a bug at [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com) with the full output of /etc/X11/xorg.conf and /var/log/XFree86.0.log.  Select 'xserver-xfree86' as the component.

---

