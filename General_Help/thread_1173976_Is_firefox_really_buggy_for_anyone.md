---
title: "Is firefox really buggy for anyone?"
date: 2009-05-30
forum: General Help
---

### Post by ittiam on 2009-05-30
I have been having some issues with firefox since the last upgrade to 3.0.10. 

1) The firefox window just greys out with the only option being to force quit
2) Even when you close the firefox window properly and try to open it again, it says firefox process already running. I have to do a pkill firefox.
3) The address bar sometimes fails to autofill addresses.

All the above problems I have been seeing consistently.

Anyone else seeing the same thing?

---

### Post by geraldvillorente on 2009-05-30
I also experiencing the same problem...

---

### Post by vishy1618 on 2009-05-30
It almost seems like someone is sabotaging firefox in linux(that was a joke, with all due respect). But this is simply too much. There are many bugs in Firefox in ubuntu that make it a pain to use (want to right click on a link anyone?) I sincerely hope that we can do something to make it better, and help the Firefox team build a better firefox for linux.

---

### Post by shankru85 on 2009-05-30
Hmmm.... Firefox runs smooth for me in Ubuntu.. 

I had a lot of such problems mentioned above in MS Windows Firefox. I tried disabling a lot of plugins that i had installed as per my friend's advice and it did the trick. 

Last resort would be to uninstall Firefox and install it freshly again and have the number of unwanted plugins as minimal as possible.

Hope this helps! :D

---

### Post by Volt9000 on 2009-05-30
> **vishy1618 said:**
> It almost seems like someone is sabotaging firefox in linux(that was a joke, with all due respect). But this is simply too much. There are many bugs in Firefox in ubuntu that make it a pain to use (want to right click on a link anyone?) I sincerely hope that we can do something to make it better, and help the Firefox team build a better firefox for linux.

Just as an aside-- to fix that right-click problem, install FireGestures. I know it's a silly workaround, having to install an extension, but it does two things:

1) It fixes the stupid right-click bug
2) It lets you use mouse gestures, which are actually very nice

---

### Post by vishy1618 on 2009-05-30
Thanks for the Firefox fix. It seems to work, but I really dont like mouse gestures. Anyways, thanks.

---

### Post by Yellow Pasque on 2009-05-30
A lot of people seem to have "grey-window" issues with Flash, especially when using proprietary video drivers (and/or running 32-bit Flash on a 64-bit browser using nspluginwrapper). I like the flashblock extension, because you then load only the Flash stuff you want to see.

Also, try running FF from the terminal and/or seeing if you have the same problem in safe mode
```
firefox -safe-mode
```

---

### Post by ActiveFrost on 2009-05-30
> **vishy1618 said:**
> Thanks for the Firefox fix. It seems to work, but I really dont like mouse gestures. Anyways, thanks.

As far as I know ( saw it posted somewhere else ), you can disable all mouse gesture options ( and use it as a /hotfix/, not /addon/ ) ;)

---

### Post by xavierp94 on 2009-05-30
I get the right bug and the firefox is still running bug too!

---

### Post by Tipped OuT on 2009-05-30
Everything is fine and dandy for me. Maybe because most of you use proprietary graphic card drivers and I use open source?

---

### Post by ActiveFrost on 2009-05-30
> **Tipped OuT said:**
> Everything is fine and dandy for me. Maybe because most of you use proprietary graphic card drivers and I use open source?

Nvidia & ATI - both gives me this "right-click bug" and flash plugin problems, so .. what you mean by saying "open source drivers" ?

---

### Post by vishy1618 on 2009-05-30
> **ActiveFrost said:**
> As far as I know ( saw it posted somewhere else ), you can disable all mouse gesture options ( and use it as a /hotfix/, not /addon/ ) ;)

How do you do that?

---

### Post by Tipped OuT on 2009-05-30
> **ActiveFrost said:**
> Nvidia & ATI - both gives me this "right-click bug" and flash plugin problems, so .. what you mean by saying "open source drivers" ?

I don't know, because people always have these problems, and I don't, none of the above problems listed in previous posts apply to me. And I see one of the users are using a proprietary graphics card driver.

My card is pretty old, and open source, so I would think 6 years was enough to prefect and correct the issues with my driver.

Or do you not know what an open source driver is?

---

### Post by ActiveFrost on 2009-05-30
> **vishy1618 said:**
> How do you do that?

Sorry, can't help you with this - haven't tried this trick by myself ( though, I'll let you know if I will find that thread ).

> **Tipped OuT said:**
> I don't know, because people always have these problems, and I don't, none of the above problems listed in previous posts apply to me. And I see one of the users are using a proprietary graphics card driver.

My card is pretty old, and open source, so I would think they 6 years was enough to prefect and correct the issues with my driver.

Or do you not know what an open source driver is?

I have one Nvidia card ( which is .. umm, 4 or 5 years old ) & a few months old ATI card ! Now, on 8.04 and 8.10 versions none of these cards can handle flash and right click ( we are talking only about Firefox ), BUT - on 9.04 ( which is my current version ), Nvidia card seems to be working ( in the meaning of "I haven't seen any bugs as in previous versions" ).

ATI driver is open-source ( it should be so ), Nvidia is not .. so, on 9.04 Ubuntu, non-free driver works better than open-source. Looks like it's all about "who you are", not "what you have" ? :D

---

### Post by trench.me on 2009-05-30
**All that are responding to this thread:** Please include versions and if you are using Ubuntu's Firefox (which is written to be Ubuntu-specific) or if you have installed Mozilla's Firefox (in a manner like the one [described here]("http://www.psychocats.net/ubuntu/firefox")).

Also make sure your Ubuntu distro info is up-to-date on your profiles, or include it in your comment.

For the record, [this is the only real bug I'm experiencing]("http://ubuntuforums.org/showthread.php?t=1168885"). I do know the writer of Twitterfox is a more than a bit upset with Ubuntu's Firefox. 

And for what it's worth **[vishy1618]("http://ubuntuforums.org/member.php?u=559609")**, I might have nodded when you mentioned sabotage. :)

---

### Post by Tipped OuT on 2009-05-30
> **ActiveFrost said:**
> Sorry, can't help you with this - haven't tried this trick by myself ( though, I'll let you know if I will find that thread ).



I have one Nvidia card ( which is .. umm, 4 or 5 years old ) & a few months old ATI card ! Now, on 8.04 and 8.10 versions none of these cards can handle flash and right click ( we are talking only about Firefox ), BUT - on 9.04 ( which is my current version ), Nvidia card seems to be working ( in the meaning of "I haven't seen any bugs as in previous versions" ).

ATI driver is open-source ( it should be so ), Nvidia is not .. so, on 9.04 Ubuntu, non-free driver works better than open-source. Looks like it's all about "who you are", not "what you have" ? :D

I use an ATI Mobility Radeon 9100/9000 IGP. Either way, no problems for me. :p

Maybe I'm just lucky. :D



PS: I have the latest version of Firefox (what ever that may be). I always stay up to date. With the ABP extension.

---

### Post by xavierp94 on 2009-05-30
The real annyoing problem is with the drivers for my graphics card. I using the following card:
```
nVidia Corporation GeForce 8400M GS (rev a1)

```I'm having issues with buttons disappearing in openoffice unless I refresh the display with the 180 driver. Though the 180 driver works well considering I'm facing the right click bug. I tried changing my driver to 173 so after I restart I open openoffice and it works perfect! Now I open firefox and its very slow and buggy it has almost all the bugs that you all are reporting! I'm really annoyed by this. I guess I have no other choice till Nvidia fixes these problems.

Here is the thread about firefox being slow:
[http://ubuntuforums.org/showthread.php?p=7372656#post7372656](http://ubuntuforums.org/showthread.php?p=7372656#post7372656)

Here is the thread about open office not working:
[http://ubuntuforums.org/showthread.php?t=1168243](http://ubuntuforums.org/showthread.php?t=1168243)


I'm getting the same problems  as this problem:
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/213872](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/213872)

My bug report on launchpad.
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/381946]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/381")
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/381952](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/381952)

---

### Post by ittiam on 2009-05-30
As mentioned in one of the posts before, I thought flash could cause the grey window (causing to force quit). But I have seen grey window even when not running flash. Konqueror, peace!

---

### Post by justingwilson on 2009-05-31
YES YES YES. I need help with this. I have ALL the problems listed in this forum. Some1 must get to the bottom of this. 

I have ubuntu 9.04 (8.10 worked SOOOOOO much smoother and awesome)

And ya. - Justin

---

### Post by MegaNinjaDeth on 2009-06-01
it works fine for me.
Sometimes when I start up firefox. it will say firefox process is already running. I start it up again and it works.

@tipped out
Not everyone has an old video graphics card or chipset thats fit for open source. =(

My old laptop that I gave away, had was an HP pavilion ZV something
It had that ATI mobility Radeon 9000/9001 IGP chipset.
I hated that chipset. I remember I had to use a special tool to extract the R300 drivers from Catalyst 3.65.
the last catalyst that had that driver.

---

### Post by martini1179 on 2009-06-01
> **ittiam said:**
> 
3) The address bar sometimes fails to autofill addresses.


I have the above problem with Firefox (using Ubuntu's version, but without Ubufox) on Jaunty. 

Mine also randomly closes and takes up almost twice as much memory than it does under Vista with approx the same amount of open tabs.

---

### Post by randytan on 2009-06-01
I experience the graying out thingie (usually with a lot of tabs or windows open) and the right click thingie (it comes out after a few right clicks). 

Are there patches for this issue? What causes it?

It would be nice if we can get rid of these quirks.

---

### Post by trench.me on 2009-06-03
To all experiencing the graying out issue in Firefox 3.0.* - 

Watch the following Known Bug reports: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/238606](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/238606) and [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/246450](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/246450)

Try out [Martin]("https://bugs.launchpad.net/%7Elodp")'s suggested fix toward the end of the second link.

```
apt-get remove flashplugin-nonfree
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz)
tar zxvf libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
mv libflashplayer.so ~/.mozilla/plugins/libflashplayer.so

```

I haven't experienced the bug so I've obviously not tried the above "fix". 

However, I do have an alternative personal suggestion. Install Firefox 3.5 Beta 4. [http://www.mozilla.com/en-US/firefox/all-beta.html](http://www.mozilla.com/en-US/firefox/all-beta.html) I should be ashamed of resorting to recommending a version change as a bug fix, but it would seem there aren't many other alternatives. Plus, I've been using the FF3.5b4 long enough that I personally have the confidence to recommend it to general users (even though the page says it's not for general users). I'd also be interested in seeing if the gray-bug carries over to the new version. (Fairly confident that it will not.)

Also worth a look - see the beta's *known issues* before jumping right in: [http://www.mozilla.com/en-US/firefox/3.5b4/releasenotes/#issues](http://www.mozilla.com/en-US/firefox/3.5b4/releasenotes/#issues)

(Again, other than the previously mentioned PNG issue, I've experienced no problems with F3.5b4 whatsoever.)

---

