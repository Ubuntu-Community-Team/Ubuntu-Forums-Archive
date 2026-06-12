---
title: "Firefox + firebug = slow and sluggish, but only on ubuntu"
date: 2010-12-15
forum: Desktop Environments
---

### Post by mortuk on 2010-12-15
So I am a web developer, and use firefox daily in developing / testing websites, and general browsing. This means I sometimes have a lot of tabs open.

I noticed that firefox would start getting really slow and sluggish, and eventually I would have no choice but to restart it. Now the PC I am using is no slouch so thats not the issue, but I do have firebug open a lot which I suspect is part of the culprit.

Now in my windows environment, I hate to admit but it runs a lot smoother and as it should. Also under ubuntu I now have to run chrome in order to keep some of my mass of tabs on, and chrome even under linux works as you would expect.

Has firefox just become a big bloated mess? Will I have to move over to chrome fulltime or is there something I can do about it? I have done all the usual pipelining tweaks and stuff, and I'm getting desperate!

---

### Post by ingeva on 2010-12-15
> **mortuk said:**
> Now the PC I am using is no slouch so thats not the issue, but I do have firebug open a lot which I suspect is part of the culprit.
Has firefox just become a big bloated mess? Will I have to move over to chrome fulltime or is there something I can do about it? I have done all the usual pipelining tweaks and stuff, and I'm getting desperate!
Well, I removed FireBug and there's no noticeable difference.
However, running it on 9.10 is a different world. If this is important to you,
I suggest you revert to 9.10. I haven't found any advantages with 10.10 yet. Just some new problems.
BTW, 10.04 didn't work at all for me because it didn't understand my wireless keyboard and mouse. No connection to the computer. Removing all BlueTooth software I could find didn't help (I borrowed an old PS/2 keyboard and mouse). :(

With every new revision, they seem to remove more features than they add.
They are replicating Microsoft... :(

Still, it could always be worse. We could still be running Windoze! :)

---

### Post by mortuk on 2010-12-16
Reverting back isn't really an option. I am on 10.04 but this problem has been around for a while

Its probably better now than it has been in the past on 9.04 / 9.10, as before I was plagued with firefox greying out, now it just seems really sluggish like its not registering clicks / changing tabs etc straight away

Might try the FF4 beta and see if its any good, otherwise looks like I will be moving to chrome fulltime :(

---

### Post by ingeva on 2010-12-16
> **mortuk said:**
> Reverting back isn't really an option. I am on 10.04 but this problem has been around for a while

Might try the FF4 beta and see if its any good, otherwise looks like I will be moving to chrome fulltime :(
OK, so there's probably something else causing the problem. I wasn't able to use 10.04 but in 9.10 FF behaves like a charm, and so far 10.10 doesn't have anything I need that I don't have in 9.10.
Good luck to you!
(Oh, BTW, the latest Opera isn't that bad either! :) )

---

### Post by cbarron on 2010-12-16
I run Firefox and Firebug in 10.10 with no problem at all....not sure why it works well on this laptop but it does, and yes I have had multiple tabs open at once also (I do some design to)

---

### Post by Migrus on 2010-12-17
I used to have problems with firebug causing my firefox process to grow endlessly. When it was using up half my RAM it would also be incredibly slow to use. Disable firebug and the problem went away. This was on 9.04 or 9.10, and also on 10.04. No idea if this is the same as what you are seeing.

What I do now is I have a separate firefox instance and profile ("test") for development work, with firebug enabled. The main firefox is started first and keeps running, then I start the development one using "firefox -no-remote -P test" and can restart that as much as I want without losing my browsing sessions.

For all I know the problem I had might be fixed by now but I am sticking to my setup.

---

### Post by ububaba on 2010-12-17
I do not have firebug on my machine. Have reverted from 10.04 to 9.10. It is so slow that I want to bang my head on the screen or throw away the kbd.
Have cleaned with Bleach etc.

---

### Post by incusor on 2010-12-17
> **mortuk said:**
> So I am a web developer, and use firefox daily in developing / testing websites, and general browsing. This means I sometimes have a lot of tabs open.

I noticed that firefox would start getting really slow and sluggish, and eventually I would have no choice but to restart it. Now the PC I am using is no slouch so thats not the issue, but I do have firebug open a lot which I suspect is part of the culprit.

Now in my windows environment, I hate to admit but it runs a lot smoother and as it should. Also under ubuntu I now have to run chrome in order to keep some of my mass of tabs on, and chrome even under linux works as you would expect.

Has firefox just become a big bloated mess? Will I have to move over to chrome fulltime or is there something I can do about it? I have done all the usual pipelining tweaks and stuff, and I'm getting desperate!
i am experiencing the same .i dont know why this is happenning ?

---

### Post by adsnads.com on 2011-01-23
I noticed Firefox (3.6.13) has been getting very sluggish in recent weeks on my old laptop (512M Ram) with Ubuntu 10.04. Switching between tabs was very very slow. I checked my DSL speed, but switching between tabs is not a DSL speed issue. BTW I do not use Firebug on this machine.

I made some changes and things are humming along pretty good. Here's what I did.

In Firefox - 
Go to Tools -> Clear Recent History ....  Select Time range as Everything.
      I checked Browsing History, Cookies and Cache. I did not check Form & Search History. 
      Then click the Clear Now button.
Then I went to Tools -> Add-ons -> Plugins and Disabled 2 or 3 of the 7 Plugins shown.
Then I went to Tools -> Add-ons -> Extensions and Disabled a bookmark sync program.

Then I restarted Firefox and the sluggish behavior was gone. That was yesterday and today Firefox is still responding immediately. 

I didn't get as far as Tools -> Manage Content Plug-ins but that was my next step. I'm not sure if that would help things, but the list of Plug-ins was pretty long .... about 40 items. Has anybody tried cleaning these out and what were the results ?

---

