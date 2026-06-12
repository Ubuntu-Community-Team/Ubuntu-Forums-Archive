---
title: "Strange MeMenu Behaviour"
date: 2010-05-03
forum: Desktop Environments
---

### Post by mohshami on 2010-05-03
Hey guys,

I've recently upgraded to Lucid and loving it. Flash and Sound seem to be working properly now (So far). Kudos to the dev team.

Now to my issue, when I set my status to "Offline" using MeMenu, I can't set it to anything else unless I go to Empathy and switch to "Available". This is different from the behaviour in Jaunty.

Thanks :)

---

### Post by thecapsaicinkid on 2010-05-03
Same here, it starts offline on bootup and I have to go into empathy to set it online.

---

### Post by abx_dx on 2010-05-04
yes , i have the same problem, in addition i didn't find empathy icon anywhere so i created a shortcut...

---

### Post by xdevnull on 2010-05-04
Same here.  In addition I don't understand this thing at all.  It seems to not do anything unless I want to change my user information.

Further - the mail icon doesn't do anything but launch gwibber and empathy.  Is it supposed to do more than that?  Do I really need another icon to do that.  

Can someone explain what the functionality is supposed to be.  I have easier ways of launching programs.

---

### Post by Calash on 2010-05-04
The intended behavior of the indicator-messaging app (The mail icon that handles broadcast, chat, and email) is to display un-viewed messages only when evolution is active.  Similarly the indicator-messaging and indicator-me only have function once the applications are started (Evolution, Empathy, and Gwibber).

I agree 100% that this is a counter intuitive setup, however after digging around in Launchpad I found that this is very much the way it was designed.  The best fix I have found is to add Evolution, Empathy, and Gwibber to the startup applications.

---

### Post by mohshami on 2010-05-10
Sorry for the late reply, I didn't get a notification on my email, weird.

Anyways, I don't like the evolution behaviour, but at least it's working.

As for Empathy, even when the client is open, you can't set your status to anything if you're currently offline, you have to go to Empathy, change status there, and then the selection is available.

---

### Post by xdevnull on 2010-05-10
I removed it.  Gwibber runs in the background, I don't IM much and I don't use evolution (I use Thunderbird).  I don't really use the panel anyway - I use docky, so I only have a few things in the panel and leave it hidden to one side.  I guess it seemed like a good idea at some level, and they made a lot out of it, but I'm not impressed with the execution.

---

