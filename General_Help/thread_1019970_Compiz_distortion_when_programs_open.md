---
title: "Compiz distortion when programs open"
date: 2008-12-23
forum: General Help
---

### Post by tlois on 2008-12-23
I have searched for any posts that address my problem and find none.  I have an eee Box b202 that I have installed 8.10 on and have added compiz, which is running fine except for when a program first opens, I get some distortion- sometimes a lot, sometimes a little.  It does not happen at other times, such as closing, dragging, etc.  It seems to pretty much only happen when I open Firefox and Open Office and sometimes on Picasa,  but does not happen when I open, say, the terminal or other system applications.  It does not happen when I close them. 

Here is my graphics card info:

display:0 UNCLAIMED 
             description: VGA compatible controller 
             product: Mobile 945GME Express Integrated Graphics Controller 
             vendor: Intel Corporation 
             physical id: 2 
             bus info: pci@0000:00:02.0 
             version: 03 
             width: 32 bits 
             clock: 33MHz 
             capabilities: bus_master cap_list 
             configuration: latency=0 
        *-display:1 UNCLAIMED 
             description: Display controller 
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller 
             vendor: Intel Corporation 
             physical id: 2.1 
             bus info: pci@0000:00:02.1 
             version: 03 
             width: 32 bits 
             clock: 33MHz 
             capabilities: bus_master cap_list 
             configuration: latency=0 

I was able to take a picture of it happening, but I do not know how to post it in here.  However, here is a link to an image to someone else's picture.  My problem looks like this, but this person's problem was not the same as mine (it had something to do with mouse over blah blah).

[http://img262.imageshack.us/my.php?image=screenshotlt8.png](http://img262.imageshack.us/my.php?image=screenshotlt8.png)

Sometimes there is more distortion, with dark colors, sometimes less.  

Thanks if anyone has any suggestions.  BTW, if that UNCLAIMED is not the problem, what does that mean?

Editing to say:  I have tried some different programs and watched the system monitor and the programs that cause this to happen (FF and OO) use CPU wildly upon opening, so I think that is the problem.  I tried opening Abiword, a much less power hungry WP program and there was not the distortion, etc. etc.  So.  This little box appears to have some limits.  But very few!! Everything else is lovely.

---

### Post by brudinie on 2009-01-05
Exactly the same issue for me too.

---

### Post by sendblink23 on 2009-01-05
Honestly get used to it.. its pretty normal, and it doesn't really affect anything.. I had it before when I had Ubuntu 8.04


> **tlois said:**
> I have searched for any posts that address my problem and find none.  I have an eee Box b202 that I have installed 8.10 on and have added compiz, which is running fine except for when a program first opens, I get some distortion- sometimes a lot, sometimes a little.  It does not happen at other times, such as closing, dragging, etc.  It seems to pretty much only happen when I open Firefox and Open Office and sometimes on Picasa,  but does not happen when I open, say, the terminal or other system applications.  It does not happen when I close them. 

Here is my graphics card info:

display:0 UNCLAIMED 
             description: VGA compatible controller 
             product: Mobile 945GME Express Integrated Graphics Controller 
             vendor: Intel Corporation 
             physical id: 2 
             bus info: pci@0000:00:02.0 
             version: 03 
             width: 32 bits 
             clock: 33MHz 
             capabilities: bus_master cap_list 
             configuration: latency=0 
        *-display:1 UNCLAIMED 
             description: Display controller 
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller 
             vendor: Intel Corporation 
             physical id: 2.1 
             bus info: pci@0000:00:02.1 
             version: 03 
             width: 32 bits 
             clock: 33MHz 
             capabilities: bus_master cap_list 
             configuration: latency=0 

I was able to take a picture of it happening, but I do not know how to post it in here.  However, here is a link to an image to someone else's picture.  My problem looks like this, but this person's problem was not the same as mine (it had something to do with mouse over blah blah).

[http://img262.imageshack.us/my.php?image=screenshotlt8.png](http://img262.imageshack.us/my.php?image=screenshotlt8.png)

Sometimes there is more distortion, with dark colors, sometimes less.  

Thanks if anyone has any suggestions.  BTW, if that UNCLAIMED is not the problem, what does that mean?

Editing to say:  I have tried some different programs and watched the system monitor and the programs that cause this to happen (FF and OO) use CPU wildly upon opening, so I think that is the problem.  I tried opening Abiword, a much less power hungry WP program and there was not the distortion, etc. etc.  So.  This little box appears to have some limits.  But very few!! Everything else is lovely.

---

### Post by myddewji13 on 2009-01-06
same prob...i posted abt this awhile ago but no one seems to have a solutions

---

### Post by ellalan on 2009-01-06
I used to get the same distortion, I found this tweak for FF and since I made the changes the said distortions doesn't occur anymore.
[http://rahulhackingarticles.wetpaint.com/thread/773173/cool+mozilla+tricks+just+try+them+out?t=anon](http://rahulhackingarticles.wetpaint.com/thread/773173/cool+mozilla+tricks+just+try+them+out?t=anon)

---

### Post by tlois on 2009-01-23
I still have not found any fix for this.  It does not happen on my Dell (8.10), Thinkpad (8.04) or eee701 (Ubuntu eee)- just the eeebox for me, so I really don't think this is normal.  I have just started using Epiphany and Abiword on my eeebox so I don't have to see it.  No, it does not really effect the function of programs, but it is not pleasant to see on a brand new 'puter or when showing off Linux to non-linux users.  

Still love Ubuntu, though.  Thanks for the FF tip too- I set it- may speed up browsing, but did not effect the initial opening distortion.

---

### Post by tlois on 2009-01-23
another interesting thing.  i read that some intel video cards use computer ram rather than bringing their own along.  i am wondering if setting the ram usage higher would help, but i don't know how to do that.  also came across this.  if you scroll down to video and 3d performance (although this is an acer- maybe same would help others).  Still, this is something I do not know how to do.  But both things seem like possible help and I will try over the weekend to figure it out.

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

### Post by Inkululeko on 2009-02-17
Has anyone found a solution? The tweaks for firefox don't really work, the distortions still exist. Is it maybe a problem specific for Ubuntu or does it also occur in other distributions? I will test it maybe with Arch Linux in a few days.

jules

---

### Post by tlois on 2009-02-18
i got it to stop on ff by setting firefox to drop cache on exit.  that fixed firefox at least.  glad to see i am not the only one driven nuts by it!  still love ubuntu, though.

---

