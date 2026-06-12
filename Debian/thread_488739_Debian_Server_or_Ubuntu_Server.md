---
title: "Debian Server or Ubuntu Server"
date: 2007-06-30
forum: Debian
---

### Post by thenetduck on 2007-06-30
Hi
   My first choice of server was Ubuntu because I use it on my desktop and I feel like it has made some really good progress in the Linux community. I know a little bit about linux but when it comes to server stability and security I'm no very well educated. 
   
   Is Debian's server a more stable, faster and secure release? or is Ubuntu? Also, if I install Debian instead of Ubuntu are the security updates going to mess up my system eventually? I have heard either way but would like a system that I am never going to have to reboot and will be very very up todate with security patches and updates. Thanks you all for your good comments,

The Net Duck

---

### Post by kerry_s on 2007-06-30
if you want up to date, then go debian. ubuntu locks the version once it's released, so it only gets security updates, meaning some apps get old real quick. but even with debian it's no picnic, you would be grabbing from testing(lenny) and unstable(sid) which still leaves a chance something can go wrong. in most cases old is better, because there very stable and well tested.

so to round things up,
 if you know your going to want up to date, go debian, you have the option of selective upgrades just by adding the other repos or you can update the entire system.

if your just going to stick with what you got, go ubuntu for as long as you can stand, but it only offers dist-upgrades for newer.

hope that made sense, i need more coffee. ;)

---

### Post by juxtaposed on 2007-06-30
Debian for everything :)

---

### Post by deepclutch on 2007-07-01
Debian Rocks!

---

### Post by Pobega on 2007-07-01
> **kerry_s said:**
> if you want up to date, then go debian. ubuntu locks the version once it's released, so it only gets security updates, meaning some apps get old real quick. but even with debian it's no picnic, you would be grabbing from testing(lenny) and unstable(sid) which still leaves a chance something can go wrong. in most cases old is better, because there very stable and well tested.

so to round things up,
 if you know your going to want up to date, go debian, you have the option of selective upgrades just by adding the other repos or you can update the entire system.

if your just going to stick with what you got, go ubuntu for as long as you can stand, but it only offers dist-upgrades for newer.

hope that made sense, i need more coffee. ;)

That isn't exactly true, there is always Debian stable, which is like Ubuntu 6.06 except it gets security updates much more frequently for a larger array of programs.

But sticking with testing for a server wouldn't be so bad, considering you'd only be using server programs (Apache, PHP5, Exim4, etc.) and usually those programs are thouroughly tested before they are allowed into testing. Just make sure to install apt-listbugs, and wait 3~4 days before installing upgrades (Then all of the bugs should be ironed out and reported, and if the bugs aren't fixed apt-listbugs will warn you).

My vote goes to Debian stable or Debian testing, though. Ubuntu 6.06 LTS isn't really a server platform in my opinion.

---

### Post by az on 2007-07-01
> **kerry_s said:**
> if you want up to date, then go debian. ubuntu locks the version once it's released, so it only gets security updates, meaning some apps get old real quick. but even with debian it's no picnic, you would be grabbing from testing(lenny) and unstable(sid) which still leaves a chance something can go wrong. in most cases old is better, because there very stable and well tested.

Debian and Ubuntu work the same way.  You would not want to run stuff from Debian Testing or Unstable on a production server.

Likewise, you would not want to run things from the developmental version of Ubuntu on a production server.  However, the current stable and supported version of Ubuntu can be more recent than Debian, considering Ubuntu has a six-month release schedule.

To achieve that, they only support a small subset of packages that Debian supports.



> **thenetduck said:**
>   
   Is Debian's server a more stable, faster and secure release? or is Ubuntu? Also, if I install Debian instead of Ubuntu are the security updates going to mess up my system eventually? I have heard either way but would like a system that I am never going to have to reboot and will be very very up todate with security patches and updates. Thanks you all for your good comments,

The Net Duck

I actually think Ubuntu's default server is more lean.  Is it faster or more secure?  I reckon it's the same.

It depends on what you want to do?  If it's a plain LAMP server, use whatever.  Ubuntu's release schedule should not be that much of an advantage there.  If you need packages that only are supported in Debian, then the question is moot.

---

### Post by SkyNet2029 on 2007-07-27
I tried Debian (4.0) on one of the production servers here and my kid managed to break alot of things when he found the Mains Breaker box on our house and did some switchgear yanking.. go easy, (he's 4).. The journal was tossed.. I went with Kubuntu 7.04 and have been missing the debian ever since. I would have to agree with whoever posted 'Debian 4 EVERYTHING!'.  as the rock-solid stability and long uptimes, easily configurable (and much more sane sanity checks ) and loads faster IMHO than an U/Kubuntu derivative.. 

Of particular pain caused to me now is the inability to just grab what i want from a repo without it breaking all sorts of things and tossing me into dependency hell.. Sorry I spilled coffee oon my keyboard last nite and now the(....) does a triple when i hit it...

So, Debian if you need the stability (you do, as hindsight of 'Oh,man... it is down AGAIN @$$~!' really sucks when u know all you had to do was take 6 minutes out of your life, and do a complete debian install.. the choices we make, blah...

The link to my site will be offline for about 2 hours whilst I migrate everything back to some pure Debian goodness.. I have learned the folly of my ways and shall fix them.

---

### Post by MetalMusicAddict on 2007-07-27
This was something I thought hard about recently. I was in a spot to rebuild my home server. While Debian is a fine choice what swayed my decision was the fact that I have 6 other *buntu boxes that connect to it. So for consistencies sake I went a CLI install of Ubuntu-Feisty. Runs headless. Controlled via SSH. Been solid since Feisty was released.

---

### Post by diablo668 on 2007-07-30
I switched to Debian on my home server last weekend after a tip a friend of mine gave me because I was having a weird issue with my raid on my Ubunru 7.04 Server istall

The problem was that i wanted to create a 3rd raid 0 with my hda4 and hb1, but when ever i created a raid partition on hdb it auto joined it in a non-excisting raid1 array with hdc (my dvd rom) and hdd (non excisting in my system. Even with a new install in the partitioner this problem remaind.

With debian 4.0 no problem what so-ever with the raid devices. The only downside to debian thus far is that it's a little bit less noob friendly (after a year messing arround with ubuntu I still feel noob) and requires a bit more input since in the ubuntu install almost everything is already there 

but the debian install feels alot more stable than the ubuntu did so that's a plus

so I'll think I'll stick with debian from now on

---

### Post by ZipoTe on 2007-08-06
I have debian running as server and it makes me feel more confortable. Are the little details that make the difference and when trying debian you notice them. 

So, for server: DEBIAN

---

### Post by Frak on 2007-08-06
Debian 100%, Ubuntu would also work, but Debian's release dates are so far apart, its nearly perfect.
Rock solid.
The only other one I would recommend beyond that is FreeBSD.
Another forum though.

---

### Post by eentonig on 2007-08-06
If you want stable and fast. Go for Debian stable.

If you want bleeding edge, use Debian Sid or Ubuntu.

Personnally, I'd use Debian for any server I install.

---

### Post by coxy on 2007-08-10
I'm the same as the majority; Debian rocks! It is faster and more stable than Ubuntu server and very similar to configure.

I would probably use Debian on everything but it's a nightmare with my laptop so I use Kubuntu instead, which is also awesome!

---

### Post by southernman on 2007-08-10
I've (in the last two days) tried out 3 server installs. Two of the Ubuntu (6.06 LTS and 7.04) as well as Debian Etch (4.0) all following falko's howto guides at HowToForge.

To me, I liked the Debian route best. It just went smoother and held back no packages when running an aptitude upgrade. Ubuntu (oth) kept holding packages back... seemingly random at that.

I use Fiesty on my Desktop (though I may now try Debians Desktop just for kicks), and will be using Debian Etch for my home server.

I can't give you any specific info as to why I choose, other than to say it's based on what I've researched, practiced, and heard scuttle-butt from/about.

Of course a much higher learning curve, you could go with FreeBSD as already been suggested.

---

### Post by stmiller on 2007-08-23
Ubuntu packages are from Debian Unstable. 
Debian Stable is Debian Stable. :)

I also do the Debian Stable server / Ubuntu desktop setup.

---

