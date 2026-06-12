---
title: "Ventrilo Linux client (Spux)"
date: 2009-03-29
forum: Gaming &amp; Leisure
---

### Post by svek on 2009-03-29
Heya all,

Not sure if this is the right forum to post this in but hope it is, was the one that looked best.
Although Ventrilo through Wine works I know there's more than me who would love to see a native ventrilo client for Linux, some of us just dont have the option to tell others to use something else for voice chat.
There's a project that started a while ago to make a native client and the author of it just decided to make it open source and is looking for developers to get things moving faster.
If you're interested in a native Ventrilo client for Linux then have a look at [http://www.spuxproject.net/](http://www.spuxproject.net/) , the project just moved to this site from using a forum before.

I'm not a part of the development team but just a user who'd love a native client and hopefully others are as well.

---

### Post by hikaricore on 2009-03-29
About time.  :)

---

### Post by u235sentinel on 2009-03-30
> **svek said:**
> {snip}
 and the author of it just decided to make it open source and is looking for developers to get things moving faster.
If you're interested in a native Ventrilo client for Linux then have a look at [http://www.spuxproject.net/](http://www.spuxproject.net/) , the project just moved to this site from using a forum before.

I'm not a part of the development team but just a user who'd love a native client and hopefully others are as well.

I know it's been said but it's about time!

I've been bugging these guys for months along with many other's on their forums.  I've even contacted their sales to find out more about their software.  I didn't even mention I was interested in the Linux client and they still didn't respond.  So I was thinking they were just going out of business and have been telling my friends to switch to teamspeak.  It's free, works on all platforms and it works great.

Maybe someday these guys will get a clue.  From the sounds of it they understand there is a demand.

---

### Post by Naiki Muliaina on 2009-03-30
Woot! I detest teamspeak, always had better luck with mumble and ventrillo, so vent coming to linux is yays! ^^

---

### Post by Ben Crisford on 2009-03-30
Nice, how can I get involved with the development then?

---

### Post by u235sentinel on 2009-03-30
> **Ben Crisford said:**
> Nice, how can I get involved with the development then?

[http://ventinux.net/viewtopic.php?f=6&t=27](http://ventinux.net/viewtopic.php?f=6&t=27)

Here is what I found on their forum

*I am currently looking for developers to help out with the development of the Spux. You may view the source through the Subversion repository posted on the new website. But if you want to join the team email me at **msierks@sierktech.net**. We can always use your help even If your not a C++ developer, just contact me if you are interested.*

I'll download it in a bit.  I'm not a developer but seek to learn all I can.  Might be something fun for me to grow into :D

---

### Post by svek on 2009-03-30
The guy at [http://www.spuxproject.net](http://www.spuxproject.net) is still setting things up with the new website for it, there is a repository up there as well.
Last I heard from him (before the move to the new forums) he said he had the protocol figured out and was rewriting the code from C into C++.
If you're interested then see if you can get in touch with him either by email (if he got it sorted yet) or by the forum over there or by a pm on the same forum.
Havent seen the code myself so not sure how it looks but from what I heard last time it's definitely in a very early stage.

[http://svn.spuxproject.net/svn/spux/trunk/](http://svn.spuxproject.net/svn/spux/trunk/)

---

### Post by msierks on 2009-03-31
Yes the code is in its early stages, and I haven't had much time to work on it since University finals are coming up. Also I mistakenly posted my email wrong, I forgot the "s" in "sierkstech" probably due to lack of sleep :(. so just to clarify things it is [email]msierks@sierkstech.net[/email]. We need developers especially for these early stages. 

Thank you for the interest

---

### Post by Vadi on 2009-04-01
Great stuff. I do hope there will be a gtk+ interface available.

---

### Post by Rumbl3 on 2009-04-01
hawt very hawt! lol
I love my vent.

---

### Post by msierks on 2009-04-03
Vadi, join the development team and find out... and yes GTK+ will be used over anything else.

---

### Post by darkknight045 on 2009-07-15
I'd like to bump this thread, I think this is a great effort and I'm looking to get involved as a tester.

My ubuntu PC is currently out of action(AC Adaptor destroyed by ambitious puppy) but when I get up and running I would be more than glad to pitch in.

---

### Post by cahumphrey on 2009-07-28
I am another semi-frusterated Vent user that would love to contribute to the efforts of this application. I don't have any programming experience, but would be very happy to help test and hunt for bugs.

What are the first steps in getting involved?

---

### Post by samh785 on 2009-07-29
Hopefully now I won't have to hear only one person at a time like what happens when using the windows version of vent through wine. :D

---

### Post by doorknob60 on 2009-07-29
Very nice. I just compiled it and the GUI works fine. I'll test the actual functionality of it once Zybez will send me my login info -.- I'll also consider making an Arch PKGBUILD for it :) EDIT: DONE! [http://aur.archlinux.org/packages.php?ID=28861](http://aur.archlinux.org/packages.php?ID=28861)

---

### Post by selvage on 2009-07-30
this is awesome

---

### Post by epitaph on 2009-07-30
For giggles I tried to compile it on Jaunty but it says it cannot find ALSA.

```
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 0.22... not present.
checking for snd_ctl_open in -lasound... no
configure: error: Cannot find alsa: Is it installed?
```

---

### Post by cahumphrey on 2009-07-31
I feel like an idiot asking, but what exactly is involved in trying to compile/install/use Spux.

I have browsed around on [http://svn.spuxproject.net/svn/spux/trunk/](http://svn.spuxproject.net/svn/spux/trunk/) but I am not sure how to proceed. 

After reading a few SVN + ubuntu, and beginner's guide to SVN articles I am sufficiently overwhelmed.

Any chance I could get a helpful nudge in the right direction? Do I first need an SVN client? If yes, how do I 'checkout' the Spux code once I have an SVN client.

Thanks! :D

---

### Post by cahumphrey on 2009-07-31
Holy smokes - with 9.04 64-bit I not only got it to compile but I even managed to run the app!

I found this thread to be extremely helpful:
[http://www.spuxproject.net/forums/index.php?topic=28.0](http://www.spuxproject.net/forums/index.php?topic=28.0)

epitaph I was having the same error as you but after installing libasound2-dev I was able to compile.

Wow this is great, can't wait to try it out!

---

### Post by cahumphrey on 2009-07-31
Okay I am home now and have started playing around with Spux.

I loaded a vent server onto my machine, and have begun playing around with Spux.

If speak from my wife's PC while connected with Spux I get the following error:

```

terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check

```

---

### Post by nielsek on 2009-08-07
bump

---

### Post by Ben Crisford on 2009-09-19
Hey everyone!  Just to let you know, spux now has twitter!

[http://twitter.com/spuxproject](http://twitter.com/spuxproject)

I will be maintaining this on behalf of the spux team.  Its a great way to keep up to date with spux news/release information if your interested.

So please, support spux, and +follow!

Cheers,
Ben :)

---

### Post by nielsek on 2010-04-07
Spux seems kinda dead so if your looking for a native client, you should check out Mangler!
[URL="http://www.mangler.org"]
http://www.mangler.org[/URL]

---

