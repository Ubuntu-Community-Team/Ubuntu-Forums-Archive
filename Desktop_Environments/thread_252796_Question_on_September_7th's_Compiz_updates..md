---
title: "Question on September 7th's Compiz updates."
date: 2006-09-07
forum: Desktop Environments
---

### Post by turbojugend_gr on 2006-09-07
Well, I had some issues with compiz lately, since the previous updates. The thing is I make it work again, my own way, instead of the one suggested in forums, so I do not have /usr/bin/csm in my pc. You can see my version of solving the problem here: [http://www.ubuntuforums.org/showthread.php?p=1462396#post1462396](http://www.ubuntuforums.org/showthread.php?p=1462396#post1462396)

So I feel like asking, should I update or not? If you have any problem following todays updates, or even if you are enjoying a stable system after them, plz say so!

Plz respond either way ,as I do not wish a FiASCO again on my system, it sad we are afraid to update, I loved the safety feeling ubuntu used to provide me with... I hope it won't take long to come back...:-k

---

### Post by turbojugend_gr on 2006-09-07
Oh i forgto : In order to be more specific I will provide you folks with the list of items for updating, here it is :


compiz          -0.0.13.47-0ubuntu1-
compiz-core     -0.0.13.47-0ubuntu1-
compiz-gnome    -0.0.13.47-0ubuntu1-
compiz-plugins  -0.17-0ubuntu1-
csm             -0.7-0ubuntu1-
libxfont1       -1:1.0.0-0ubuntu3.1


PLZ REPLY, thank you all in advance m8s!

---

### Post by ayoli on 2006-09-07
compiz is quite experiental, so if you want a stable system, use metacity. there's compiz / cgwd /plugins etc updates almost everyday which oftenly break "desktop stability", but after discussions, solutions appears. this is always a bit of work and fear ;)
edit: ve done this update, and only loose visibility of quit menu (i mean when you hit quit in main menu, buttons disconnect, hibernate, reboot, halt,.. aren't visible but are here).

---

### Post by turbojugend_gr on 2006-09-07
OK, I have to admit, I know compiz is experimental ,yet again asking if the last updates are ok is just a precaution, not an insult to us!

So plz, plz tell me your experience with the recent updates, I am just asking if they are ok to download. Sorry if I am  sounding a little bit rude or agressive, that's not my intention, nore my true feelings. Thanx for troubling anyway.


Again plz provide me info of your experience with those updates.:D

---

### Post by PathSpace on 2006-09-07
The upgrade went OK with me, except that I lost my cube top/bottom pictures, and the quit menu doesn't work for me either (it just locks the screen if I click it).  I wouldn't have even noticed the last one if not for ayoli pointing it out though.  :p

---

### Post by turbojugend_gr on 2006-09-07
Thank you for the info m8, I hope somebody else can offer some more info.

If someone experiences the same issue let me now, thank you for bothering anyway.

P.S.: I hope I am not getting you all bored with this one...

---

### Post by ayoli on 2006-09-07
> **PathSpace said:**
> The upgrade went OK with me, except that I lost my cube top/bottom pictures, and the quit menu doesn't work for me either (it just locks the screen if I click it).  I wouldn't have even noticed the last one if not for ayoli pointing it out though.  :p

i didnt lost my top and bottom images.
quit menu works, it just doesnt appear, not visible, you can try a guess clik if you remind buttons positions :p
i've started a [thread]("http://www.ubuntuforums.org/showthread.php?t=252697") about that, but no answers..

---

### Post by frego on 2006-09-07
I'm using compiz.  Has been working well, and I've been successfully keeping up with updates due to all the help on the forums.  Today's (9/7) updates seemed to go well, except, gnome-compiz-manager.  The update manager suggests runnind dist-upgrade.  I tried that, but when I do that, it seems to think it should install compiz-aiglx.  I thought the AIGLX was on alternative to compiz.  I thought you used one or the other, is this true?  
"apt-get dist-upgrade" also tells me it will be holding back gnome-compiz-manager.  I allow it to continue installing compiz-aiglx and get the below error:

 trying to overwrite `/usr/bin/compiz', which is also in package compiz-core
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-aiglx_0.0.13-0gandalfn~dapper1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas on how to straighten out my package manager?  I restarted since taking what I could of today's updates, csm and XGL still seems to be working ok (compiz-start for me).

---

### Post by ayoli on 2006-09-07
gnome compiz manager should be removed since csm replace it.
you can safely uninstall it with:```

sudo aptitude purge gnome-compiz-manager
```
then :
```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by dentaku65 on 2006-09-07
See this:
[http://yep.it/?bnm0t6](http://yep.it/?bnm0t6)

---

### Post by frego on 2006-09-07
Thanks Ayo, that fixed me up!

---

### Post by turbojugend_gr on 2006-09-08
I see, some issues keep, poping up... Sad but since it is experimental it is also propalbe.

Anyway, I 'll keep an eye on this thread, before I go for an update....you see I somewhat of a chicken...lmbao!;) 

Plz post even if you have no issues at all, that's very important too!

Again I feel like thanking you for your time :)

---

### Post by ayoli on 2006-09-08
sept 9th:
update to compiz .48, plugins .20, csm 0.8 and tried out compiz-manager to replace compiz-start script in session startup programs and to have tray icon back, but i has worked once only, then i had to go back and use compiz-start script as startup program. Quit screen/window is still unvisible (even if it's here, i tried a 'guess clik' which has worked) but it's not a big annoyance.
anyway, still work nice.

---

### Post by turbojugend_gr on 2006-09-08
> **ayoli said:**
> sept 9th:
update to compiz .48, plugins .20, csm 0.8 and tried out compiz-manager to replace compiz-start script in session startup programs and to have tray icon back, but i has worked once only, then i had to go back and use compiz-start script as startup program. Quit screen/window is still unvisible (even if it's here, i tried a 'guess clik' which has worked) but it's not a big annoyance.
anyway, still work nice.

You are totally my guy! You 've got the spirit I like! That's it keep posting, I believe many users share the same need for info... Good use of the forums I think...

You know what? After I update my self, in the next or the following 2 updates that should be... I will keep posting my issues, it is nice to know what to expect after an update!

---

### Post by frego on 2006-09-08
This morning I've noticed an issue from Sept 7th compiz updates.  I've lost my title bars on all windows.  I've seen this before, it seems an update usually fixes it.  Or perhaps I have something config'd wrong?

---

### Post by frego on 2006-09-08
OOps, I spoke too soon.  I ran metacity and then compiz-start and now my title bars are back.  No biggee.  Thanks.

---

### Post by ayoli on 2006-09-16
> **turbojugend_gr said:**
> You are totally my guy! You 've got the spirit I like! That's it keep posting, I believe many users share the same need for info... Good use of the forums I think...

You know what? After I update my self, in the next or the following 2 updates that should be... I will keep posting my issues, it is nice to know what to expect after an update!
yeeah, but compiz.net forums are much better for that
btw sept 16th update to compiz .56 raches my compiz. compiz segfault at startup, i had to roll bac to prior version.
compiz thread about this: [http://www.compiz.net/topic-4501-16th-sept-2006-updates-killed-xgl-compiz](http://www.compiz.net/topic-4501-16th-sept-2006-updates-killed-xgl-compiz)

---

### Post by ayoli on 2006-09-16
> **ayoli said:**
> yeeah, but compiz.net forums are much better for that
btw sept 16th update to compiz .56 raches my compiz. compiz segfault at startup, i had to roll bac to prior version.
compiz thread about this: [http://www.compiz.net/topic-4501-16th-sept-2006-updates-killed-xgl-compiz](http://www.compiz.net/topic-4501-16th-sept-2006-updates-killed-xgl-compiz)

fixed few minutes later by another update

---

### Post by turbojugend_gr on 2006-09-19
All rolling in my pc for over a week now, great work devs.

---

