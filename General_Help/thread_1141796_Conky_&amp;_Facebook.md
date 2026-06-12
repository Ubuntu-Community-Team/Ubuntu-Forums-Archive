---
title: "Conky &amp; Facebook?"
date: 2009-04-28
forum: General Help
---

### Post by Jameshardy88 on 2009-04-28
Hi i've been playing around with conky for a little bit and i was wondering is there a way to use it to perhaps check some of your facebook features e.g. wall messages, inbox, notifications etc?

---

### Post by phinullfermata on 2009-04-28
In short, yes.

Facebook provides an RSS feed of your notifications, which you could use with conky's RSS features.  I looked at it once but didn't try it out.  Let me know if it works :)

Edit: The RSS feed can be located in Inbox->notifications on the bottom of the right sidebar.

---

### Post by shadesofevil on 2009-07-16
There are a couple of ways to go about it I suppose.

[http://kudanai.blogspot.com/2009/07/facebook-inbox-count-for-conkyothers.html](http://kudanai.blogspot.com/2009/07/facebook-inbox-count-for-conkyothers.html)
Is a script to grab the number of unread messages in your facebook inbox:

you can also get some more information about pokes,friend-requests,group-invites,shares and event-invites using the facebook command line application
found at:

[http://www.facebook.com/fbcmd](http://www.facebook.com/fbcmd)

these combined with the RSS should give you all the information you need.

heres a screenshot of my conky before I wrote the inbox script. I haven't worked that into my current one yet

[http://www.flickr.com/photos/kudanai/3095941760/](http://www.flickr.com/photos/kudanai/3095941760/)

---

### Post by Isarii on 2009-09-20
Conky can apparently process RSS feeds on its own.

My code for it: 

```

FACEBOOK${hr 2}
${rss http://www.facebook.com/feeds/notifications<REST OF URL FOR FEED> 1 item_titles 10 }
```This updates every minute, which is as often as possible.

---

