---
title: "SOLUTION to Rhythmbox's BUG"
date: 2006-05-10
forum: Desktop Environments
---

### Post by tseliot on 2006-05-10
I had a problem with certain wma files and I had to uninstall "gstreamer0.10-pitfdll".

Moreover certain mp3s made Rhythmbox crash. The solution is to install Rhythmbox 0.9.4.1:

Here are the packages:
[http://people.ubuntu.com/~seb128/deb/rhythmbox_0.9.4.1-0ubuntu1_i386.deb]("http://people.ubuntu.com/~seb128/deb/rhythmbox_0.9.4.1-0ubuntu1_i386.deb")
[http://people.ubuntu.com/~seb128/deb/rhythmbox-dbg_0.9.4.1-0ubuntu1_i386.deb]("http://people.ubuntu.com/~seb128/deb/rhythmbox-dbg_0.9.4.1-0ubuntu1_i386.deb")


I suggest you to install it because that version won't be included in Ubuntu Dapper.

Here is the link to the Bugzilla session in which I received help.

P.S. the guys of launchpad.net are really on the ball.

---

### Post by groggyboy on 2006-05-30
Thanks!  It solved my problems!

---

### Post by ssam on 2006-05-30
[QUOTE=tseliot]
I suggest you to install it because that version won't be included in Ubuntu Dapper.[/QUOTE]

it will be backported pretty quick i imagine

---

### Post by tseliot on 2006-05-31
[QUOTE=ssam]it will be backported pretty quick i imagine[/QUOTE]
I hope so

---

### Post by petervdv on 2006-06-02
this solved my problem   thank you !!

---

### Post by nevin on 2006-06-02
fixed mine too., thanks

---

### Post by nero_86 on 2006-06-02
My problem is solved!!!
Thank you !! :D :D

---

### Post by tseliot on 2006-06-03
Hey guys, Arnieboy told me that this new package will be available on the next release of Automatix

---

### Post by blue_thunder on 2006-06-03
Have you guys had any problem connecting to other users with Rhythmbox's DAAP software?

I can connect to some people I see on my network, but not others...and not merely because they're password protected--it just doesn't connect to them.

I'm open to any ideas.

---

### Post by DillPill on 2006-06-04
im new to this stuff how do i install this?

-thanks

---

### Post by tseliot on 2006-06-04
[QUOTE=DillPill]im new to this stuff how do i install this?

-thanks[/QUOTE]
Download the packages then open Terminal or Konsole and type:
```
cd path_in_which_you_put_the_packages
sudo dpkg -i *.deb
```

---

### Post by Laterix on 2006-06-04
OOPS: Never mind.

---

