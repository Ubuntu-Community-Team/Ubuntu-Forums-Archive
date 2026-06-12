---
title: "An interesting freezing issue"
date: 2009-04-09
forum: General Help
---

### Post by sparo007 on 2009-04-09
So I'm running intrepid on an HP dv6000t laptop.  My issue is that the laptop locks up when I'm using the wireless on campus (at my university).  The interesting thing is though, it only does it when I'm in one, specific classroom.  The computer works just fine on my network at home and everywhere else on campus.  In fact, I have a class just across the hall from said room, and the computer works without any problems at all.

Another weird thing was that up until about a month ago, the access point never required a username and password to login.  Normally when accessing the school's wireless network, you had to login using your username and password, but not when I was in the room (though I did in the room across the hall).  I thought it might be some rogue access point designed to steal sensitive information, but since I never do anything sensitive on my laptop I used the network anyways.  

But, like I said, that was a month ago, and now the access point does act like it does everywhere else on campus and asks for the information to log on (and just to make sure it was legit I used an incorrect username and password and it rejected it).  

As for the lock up, it completely freezes the computer, and causes the caps lock light to blink continuously.  I can't seem to pass any commands to the kernel and the only option is to hold down the power button to do a reset.  If I turn off the wireless via the switch on the laptop, and don't attempt to access the internet, the laptop will run just fine throughout the class.  It locks up about every 15 minutes, however it varies greatly, sometimes it can go almost the whole class without freezing, sometimes it only goes 5 minutes.  I thought it might be caused by firefox, but the computer will freeze even when not actively using the internet.

The most frustrating thing about the whole situation is that the girl next to me is using vista and having no issues at all.  I'm being mocked by a computer running vista! That should never, ever happen.

I've looked up all the other issues involving the caps lock blinking, and they all seem to point to hardware issues.  I'm not sure if that is the case with mine since the laptop seems to work just fine everywhere else.  In terms of signal strength, it is usually at least %50.

It's not really that big of an issue since I'm almost done with the class, but I was wondering if anyone might know how to fix this so I won't have to deal with this in the future.

Thanks,
sparo007

---

### Post by paradigm2 on 2009-04-09
> **sparo007 said:**
> So I'm running intrepid on an HP dv6000t laptop.  My issue is that the laptop locks up when I'm using the wireless on campus (at my university).  The interesting thing is though, it only does it when I'm in one, specific classroom.  The computer works just fine on my network at home and everywhere else on campus.  In fact, I have a class just across the hall from said room, and the computer works without any problems at all.

Another weird thing was that up until about a month ago, the access point never required a username and password to login.  Normally when accessing the school's wireless network, you had to login using your username and password, but not when I was in the room (though I did in the room across the hall).  I thought it might be some rogue access point designed to steal sensitive information, but since I never do anything sensitive on my laptop I used the network anyways.  

But, like I said, that was a month ago, and now the access point does act like it does everywhere else on campus and asks for the information to log on (and just to make sure it was legit I used an incorrect username and password and it rejected it).  

As for the lock up, it completely freezes the computer, and causes the caps lock light to blink continuously.  I can't seem to pass any commands to the kernel and the only option is to hold down the power button to do a reset.  If I turn off the wireless via the switch on the laptop, and don't attempt to access the internet, the laptop will run just fine throughout the class.  It locks up about every 15 minutes, however it varies greatly, sometimes it can go almost the whole class without freezing, sometimes it only goes 5 minutes.  I thought it might be caused by firefox, but the computer will freeze even when not actively using the internet.

The most frustrating thing about the whole situation is that the girl next to me is using vista and having no issues at all.  I'm being mocked by a computer running vista! That should never, ever happen.

I've looked up all the other issues involving the caps lock blinking, and they all seem to point to hardware issues.  I'm not sure if that is the case with mine since the laptop seems to work just fine everywhere else.  In terms of signal strength, it is usually at least %50.

It's not really that big of an issue since I'm almost done with the class, but I was wondering if anyone might know how to fix this so I won't have to deal with this in the future.

Thanks,
sparo007

I believe a freeze with the caps lock key blinking (is num lock blinking too?) indicates a kernel panic.

Have you checked your syslog (right after resetting) to see if it indicates a hint to the problem?

```

tail -n 500 /var/log/messages | less

```

(the above command will read the default syslog and show the last 500 lines one page at a time)

This could be hardware, but it might also be temp related (how you lay the laptop down or the temp of the room).  It might also have to so with the wireless adapter.... if syslog indicates that you might want to try a different driver possibly.

---

### Post by sparo007 on 2009-04-09
I have not tried that.  I've got the class tomorrow so I'll try it then.  And, if I can do it before the computer freezes, try to post the results here.  Thanks.

---

### Post by sparo007 on 2009-04-10
Alright, so I tried that command and have 16 pages worth of information.  What should I be looking for?

---

