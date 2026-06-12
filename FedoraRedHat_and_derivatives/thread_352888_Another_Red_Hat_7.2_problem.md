---
title: "Another Red Hat 7.2 problem"
date: 2007-02-03
forum: Fedora/RedHat and derivatives
---

### Post by ardvark71 on 2007-02-03
Hi everyone...

I'm back yet again with another problem that, compared to the last one, I'm afraid will be much harder to fix and will need your help with.

Background:

A friend of mine gave me a generic system (an older Chaintech Super Socket 7 motherboard, AMD K6-III 333 mhz [don't see many of those processors around,] 256 MB's of memory and a 20 GB Seagate HD) that in turn, I am giving someone else. I can't afford Windows 98 or ME so I put RH 7.2 on for this individual, instead, mainly because it has worked well for me in the past with older systems and it's what I had on hand. Ubuntu brought it to a near crawl.

The Problem:

Last night, the dialup internet connection worked fine, now it doesn't. I've narrowed it down to a problem with Red Hat. I've tried two different modems, made sure the connection is ok with my system and that my ISP wasn't having any problems and checked a couple three basic settings in the OS but to no avail. 

It dials up and connects just fine (and stays connected) but transmissions stop after a few bytes and it is like I wasn't connected at all. All the browsers gave "cannot locate" messages immediately and I cannot ping anyone. I typed in "ifconfig" to see what it would say and it did list an error but I don't know enough with Linux to find out what that error is, let alone how to fix it.

While I realize this is with Red Hat, not Ubuntu, I figured this would be a general Linux problem that someone here could help me through. Besides, I'm already a member here, I don't want to go through the hassle of registering somewhere else.:biggrin: 

Best Regards...

---

### Post by puccaso on 2007-02-03
hi there
i have a serious question
you are aware redhat 7.2 is like using windows 3.1 ? lol

get ubuntu
or even go get fedora
i get that the specs are pretty lowend but
ubuntu will fair much greater
or get xubuntu, much better then what ur using
or fluxbuntu - very pretty looking

or get elive!

---

### Post by ardvark71 on 2007-02-04
> **puccaso said:**
> 
i have a serious question
you are aware redhat 7.2 is like using windows 3.1 ? lol


Nah, more like Windows 95 ;) 

You might have noticed where I said Ubuntu almost brings it to a crawl and Xubuntu is WAY too basic but I will have to look into fluxbuntu, elive or and some of the others. The trick is getting the CD's. I used RH 7.2 because it's what I have, along with Mandrake 8.2 (which didn't do too well with the system,) Lycoris and Tiny Linux (neither of which I used), not counting my copies of Ubuntu and Kubuntu 5.10 and 6.06.

Best Regards...

---

### Post by ardvark71 on 2007-02-04
Anyone?

---

### Post by noalternative on 2007-02-05
> **ardvark71 said:**
> Nah, more like Windows 95 ;) 

It was produced in 2001 so it is more like Windows 2000.  

> **ardvark71 said:**
> You might have noticed where I said Ubuntu almost brings it to a crawl and Xubuntu is WAY too basic but I will have to look into fluxbuntu, elive or and some of the others. The trick is getting the CD's. I used RH 7.2 because it's what I have, along with Mandrake 8.2 (which didn't do too well with the system,) Lycoris and Tiny Linux (neither of which I used), not counting my copies of Ubuntu and Kubuntu 5.10 and 6.06..

Having said that, I have used Red Hat 7.3 just in the last year or so and it was much more basic than xubuntu.  Have [you seen xubuntu]("http://shots.osdir.com/slideshows/slideshow.php?release=753&slide=3&title=xubuntu+6.10+screenshots") since breezy badger?  There has been a big improvement.  It looks almost like gnome in regular ubuntu. You could do a server install with breezy, than update to dapper, then install the xubuntu-desktop. Just change all the breezy repositories to dapper repositories in /etc/apt/sources.list.  

Fluxbox the window manager in fluxubuntu is much more basic/barebones than xfce.

---

### Post by noalternative on 2007-02-05
> **ardvark71 said:**
> I typed in "ifconfig" to see what it would say and it did list an error but I don't know enough with Linux to find out what that error is, let alone how to fix it.


Could you paste the results for us.

Just highlight them in your terminal and use the middle click botton to paste them into your post!

---

### Post by ardvark71 on 2007-02-05
> **noalternative said:**
>  Have [you seen xubuntu]("http://shots.osdir.com/slideshows/slideshow.php?release=753&slide=3&title=xubuntu+6.10+screenshots") since breezy badger?  There has been a big improvement.  It looks almost like gnome in regular ubuntu.

Wow, I stand corrected! Do they have a disk of this yet? I don't have the means to burn one myself. 

Give me a bit to transfer the information from that system to mine...

Thanks!

---

### Post by noalternative on 2007-02-05
> **ardvark71 said:**
> Wow, I stand corrected! Do they have a disk of this yet? I don't have the means to burn one myself. 

Give me a bit to transfer the information from that system to mine...

Thanks!

No they don't ship disks like ubuntu, but you can install it with apt-get by doing a server install of regular ubuntu, upgrading to dapper, then installing the xubuntu-desktop via apt-get.

---

### Post by ardvark71 on 2007-02-05
Well, I have the ifconfig information but there is no option to cut and paste, so I have no way of getting it here. Let's just say at this point I would love to have a nice little chat with the folks at Red Hat who designed this charming little OS. Or is there something I'm missing?

What I can tell you from what I saw is that there is communication taking place as the number of sent and received packets keeps growing every successive "ifconfig" command. I don't understand what the heck is going on!

Thanks!

---

### Post by noalternative on 2007-02-05
> **ardvark71 said:**
> Well, I have the ifconfig information but there is no option to cut and paste, so I have no way of getting it here. Let's just say at this point I would love to have a nice little chat with the folks at Red Hat who designed this charming little OS. Or is there something I'm missing?

What I can tell you from what I saw is that there is communication taking place as the number of sent and received packets keeps growing every successive "ifconfig" command. I don't understand what the heck is going on!

Thanks!

You don't have to have cut and paste.  Just highlight it and that is a cut, use the middle button and that is a paste.  Try it.  You'll see.

---

### Post by pistcivet on 2007-02-05
"Damn Small Linux" runs a 2.4 kernel and should work pretty well on that hardware.
Puppy Linux would also be a good one to try, it was made with dial-up users in mind.

I haven't used Redhat 7.2, but I remember RH9.
It was terribly buggy (PPP was always crashing and knocking me off line).
Good luck!

---

### Post by ardvark71 on 2007-02-05
> **noalternative said:**
> You don't have to have cut and paste.  Just highlight it and that is a cut, use the middle button and that is a paste.  Try it.  You'll see.

Where is the middle button? If you mean the mouse, there is none. 

Best Regards...

---

### Post by ardvark71 on 2007-02-05
> **pistcivet said:**
> "Damn Small Linux" runs a 2.4 kernel and should work pretty well on that hardware.
Puppy Linux would also be a good one to try, it was made with dial-up users in mind.

I haven't used Redhat 7.2, but I remember RH9.
It was terribly buggy (PPP was always crashing and knocking me off line).
Good luck!

Thanks! I will keep all of this in mind if I can't get RH working.

Best Regards...

---

### Post by ardvark71 on 2007-02-05
> **ardvark71 said:**
> Where is the middle button? If you mean the mouse, there is none. 

Best Regards...

If the middle button is emulated, where would the key be and/or where would the settings be to change this?

Thanks!

---

### Post by noalternative on 2007-02-06
> **ardvark71 said:**
> If the middle button is emulated, where would the key be and/or where would the settings be to change this?

Thanks!

With [two buttons]("http://groups.google.com/group/comp.os.linux.x/browse_thread/thread/c9f54a9697c3108f/ad7fc96724b8fadf?lnk=st&q=linux+cutting+and+pasting+from+xterm&rnum=8&hl=en#ad7fc96724b8fadf") press the left and the right buttons at the same time to paste.

---

### Post by ardvark71 on 2007-02-06
> **noalternative said:**
> With [two buttons]("http://groups.google.com/group/comp.os.linux.x/browse_thread/thread/c9f54a9697c3108f/ad7fc96724b8fadf?lnk=st&q=linux+cutting+and+pasting+from+xterm&rnum=8&hl=en#ad7fc96724b8fadf") press the left and the right buttons at the same time to paste.

Ah, there we go! Wasn't used to that one;) 

The results:

[root@localhost root]# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:17188 (16.7 Kb)  TX bytes:17188 (16.7 Kb)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:207.173.13.63  P-t-P:209.210.58.194  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:623 (623.0 b)  TX bytes:629 (629.0 b)

[root@localhost root]# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:17188 (16.7 Kb)  TX bytes:17188 (16.7 Kb)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:207.173.13.63  P-t-P:209.210.58.194  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:677 (677.0 b)  TX bytes:683 (683.0 b)

[root@localhost root]# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:17188 (16.7 Kb)  TX bytes:17188 (16.7 Kb)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:207.173.13.63  P-t-P:209.210.58.194  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:731 (731.0 b)  TX bytes:741 (741.0 b)

I put in the command three times to show you that there seems to be traffic but why none of the applications can access the connection is beyond me. :confused: Although, on second look, I'm sure all those error messages have something to do with it. Of the few times I've entered the ifconfig command, some would give errors, others not.

Thanks!

---

### Post by noalternative on 2007-02-07
Ok, I admit I don't see anything there, so I posted this info to some redhat newsgroups and these were the answers that I came up with.

from [google groups.]("http://groups.google.com/group/comp.os.linux.misc/browse_frm/thread/41a686d49111790/8dded5bfd1598e92?tvc=1&q=noalternative#8dded5bfd1598e92")

---

### Post by ardvark71 on 2007-02-07
> **noalternative said:**
> Ok, I admit I don't see anything there, so I posted this info to some redhat newsgroups and these were the answers that I came up with.

from [google groups.]("http://groups.google.com/group/comp.os.linux.misc/browse_frm/thread/41a686d49111790/8dded5bfd1598e92?tvc=1&q=noalternative#8dded5bfd1598e92")

Thank you so much for that effort, I appreciate it! :)  I will save Patrick's response and get back with you on some answers to his questions. The only thing I remember doing  between "then and when the problem appeared" was I uninstalled the rpm version of flash player 9 and installed the tar.gz versions of 7 and 9. I don't see how that would have affected the entire system's ability to interact with the connection.

Thanks!

---

### Post by ardvark71 on 2007-02-07
Hi noalternative...

Ok, here we go...

"And those "settings" were ... what?"

I took a second look at the firewall and ppp and modem settings in kppp. No changes were made.

"If you can ping by address but not by FQDN, then that indicates a name resolution problem."

That may be the case from the results I found listed below.

"What exactly is the result of "ping 209.210.58.194", the other end of your ppp?"

[root@localhost root]# ping 209.210.58.194
PING 209.210.58.194 (209.210.58.194) from 207.173.13.50 : 56(84) bytes of data. 64 bytes from 209.210.58.194: icmp_seq=0 ttl=254 time=147.747 msec
64 bytes from 209.210.58.194: icmp_seq=1 ttl=254 time=139.773 msec
64 bytes from 209.210.58.194: icmp_seq=2 ttl=254 time=169.925 msec
64 bytes from 209.210.58.194: icmp_seq=3 ttl=254 time=199.775 msec
64 bytes from 209.210.58.194: icmp_seq=4 ttl=254 time=129.768 msec
64 bytes from 209.210.58.194: icmp_seq=5 ttl=254 time=169.777 msec
64 bytes from 209.210.58.194: icmp_seq=6 ttl=254 time=189.767 msec
64 bytes from 209.210.58.194: icmp_seq=7 ttl=254 time=139.768 msec
64 bytes from 209.210.58.194: icmp_seq=8 ttl=254 time=169.525 msec
64 bytes from 209.210.58.194: icmp_seq=9 ttl=254 time=199.779 msec
64 bytes from 209.210.58.194: icmp_seq=10 ttl=254 time=139.782 msec
64 bytes from 209.210.58.194: icmp_seq=11 ttl=254 time=169.777 msec
64 bytes from 209.210.58.194: icmp_seq=12 ttl=254 time=199.783 msec
64 bytes from 209.210.58.194: icmp_seq=13 ttl=254 time=139.782 msec
64 bytes from 209.210.58.194: icmp_seq=14 ttl=254 time=169.790 msec
64 bytes from 209.210.58.194: icmp_seq=15 ttl=254 time=198.351 msec
64 bytes from 209.210.58.194: icmp_seq=16 ttl=254 time=139.773 msec
64 bytes from 209.210.58.194: icmp_seq=17 ttl=254 time=169.774 msec
64 bytes from 209.210.58.194: icmp_seq=18 ttl=254 time=199.784 msec
64 bytes from 209.210.58.194: icmp_seq=19 ttl=254 time=229.866 msec
64 bytes from 209.210.58.194: icmp_seq=20 ttl=254 time=149.933 msec

"What exactly is the result of: nslookup -sil 209.210.58.194"

[root@localhost root]# nslookup -sil 209.210.58.194
connection timed out; no servers could be reached

"What exactly are the results of : 
    grep "^hosts" /etc/nsswitch.conf 
    diff /etc/resolv.conf /etc/ppp/resolv.conf 
    ls -l /etc/resolv.conf"

[root@localhost root]# grep "^hosts" /etc/nsswitch.conf
hosts:      files nisplus dns
[root@localhost root]#

[root@localhost root]# diff /etc/resolv.conf
diff: missing operand after `/etc/resolv.conf'
diff: Try `diff --help' for more information.

[root@localhost root]# diff /etc/ppp/resolv.conf
diff: missing operand after `/etc/ppp/resolv.conf'
diff: Try `diff --help' for more information.

[root@localhost root]# ls -l /etc/resolv.conf
-rw-r--r--    1 root     root            0 Feb  7 17:37 /etc/resolv.conf

Thanks!

---

### Post by ardvark71 on 2007-02-08
Hi noalternative...

I saw that you added my last post to the Google site. Thank you so much!:)

---

### Post by noalternative on 2007-02-08
You're welcome.  Sinner says you did a typo.

---

### Post by ardvark71 on 2007-02-09
> **noalternative said:**
> You're welcome.  Sinner says you did a typo.

Ok, looking through their responses, I see it's most most likely a resolve.conf issue. I will look into that tonight and let you know what I come up with.

Thanks!

---

### Post by ardvark71 on 2007-02-09
Hi noalternative...

:KS :KS :KS 

It works! YAY!!! Dances with Crows was right on the money! I'm writing this from the system in question now. 

Again, I thank you profusely for the above and beyond effort you made in helping me and I wish to  convey my thanks and gratitude to those on the google site as well.):P 

Best Regards...

---

### Post by ardvark71 on 2007-02-09
Just as a postscript...

While, thanks to you, I was able to get the internet connection working, I decided, after a number of other problems, just to wipe RH 7.2 off the system. The whole thing has been something of a struggle to get working right on this system (mainly stemming from its age, I would assume) and I'm done messing with it!:-x I took your guy's advice and tried to get Xubuntu via Ubuntu but that failed miserably. The machine couldn't handle it. I was getting weird errors trying to log in and when I finally got it to the desktop, it locked up within a few seconds.

Xubuntu, and even fluxbuntu, would be of greater practical value if they would get it on a disc for people, like Ubuntu, Kubuntu and Edubuntu.

Oh, well, I guess this is going to remain a Windows 98 machine whenever I can afford a monstrously overpriced copy.

Best Regards...

---

### Post by noalternative on 2007-02-14
> **ardvark71 said:**
> Just as a postscript...

Xubuntu, and even fluxbuntu, would be of greater practical value if they would get it on a disc for people, like Ubuntu, Kubuntu and Edubuntu.

Oh, well, I guess this is going to remain a Windows 98 machine whenever I can afford a monstrously overpriced copy.

Best Regards...

While you can't get it free, you can order it online really cheap.  Here is a pretty good place.

[http://www.linuxcd.org/view_item.php?&id_version=1784](http://www.linuxcd.org/view_item.php?&id_version=1784)


There is also [feather linux]("http://featherlinux.berlios.de"), which is designed specifically for older hardware.

[http://www.linuxcd.org/caddie.php?&id_version=1131](http://www.linuxcd.org/caddie.php?&id_version=1131)

---

