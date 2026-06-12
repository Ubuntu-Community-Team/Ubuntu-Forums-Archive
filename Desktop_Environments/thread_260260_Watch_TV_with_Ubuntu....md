---
title: "Watch TV with Ubuntu..."
date: 2006-09-18
forum: Desktop Environments
---

### Post by sha_man on 2006-09-18
I have already a Tv-Card (wintv). What do I need to do in order to watch TV (with Teletext, Zapping, maybe recording, options, etc...) on my Ubuntu Desktop? (If it's amd64-native - even better :D )

Thanks.

---

### Post by reclusivemonkey on 2006-09-18
TV Time is the quickest and easiest way to get a TV card working, but it won't record for you, and I don't think it does teletext. Its not 64 bit either, however it is an excellent app.

[http://tvtime.sourceforge.net/](http://tvtime.sourceforge.net/)

If you want more advanced features, then you may want to look into a PVR solution such as MythTV or Freevo. You can try xawtv as well, and mencoder will record if you want a lo-fi solution. There is a gnome app which grabs tv schedules and will activate another app to record for you but the name escapes me at the moment. HTH

---

### Post by sha_man on 2006-09-18
hey thank you very much!

so all i need is tvtime (i read reviews etc... about it in the meantime like [this one]("http://www.softpedia.com/reviews/linux/tvtime-Review-17876.shtml") - and it seems the best viewer available atm. I also read already about mythtv, but it seems complicated to install etc...

but now my second question: is it enough to install **just**  tvtime and everything should work out of the box or do i need to install drivers (which ones?) etc...?

---

### Post by reclusivemonkey on 2006-09-18
> **sha_man said:**
> hey thank you very much!

so all i need is tvtime (i read reviews etc... about it in the meantime like [this one]("http://www.softpedia.com/reviews/linux/tvtime-Review-17876.shtml") - and it seems the best viewer available atm. I also read already about mythtv, but it seems complicated to install etc...

but now my second question: is it enough to install **just**  tvtime and everything should work out of the box or do i need to install drivers (which ones?) etc...?

You should be ok with just TV Time. With any luck, your card will be recognised by the kernel, and loaded as a V4L device. If you do

```

lspci

```

and its listed there, you should be good to go. TV Time has no dependencies I am aware of.

---

### Post by master_b on 2006-09-18
I personally use Kaffeine as it works with DVB-T ( Digital) cards.

It is also very easy to scan for channels.

Bill

---

### Post by megamaced on 2006-09-19
Yeah I just use Kaffeine as well. All of the others are too damn hard to set up ](*,)

---

### Post by arnabbiswas on 2007-03-09
I tried using TVTime and it did not work for me. As per this post, I was informed that TVTime will not work with ivtv:

[http://www.ubuntuforums.org/showthread.php?t=379806](http://www.ubuntuforums.org/showthread.php?t=379806)

---

