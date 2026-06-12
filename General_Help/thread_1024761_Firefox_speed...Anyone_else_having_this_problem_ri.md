---
title: "Firefox speed...Anyone else having this problem right now?"
date: 2008-12-29
forum: General Help
---

### Post by mariane_08 on 2008-12-29
I just installed Intrepid on my laptop. Everythings worked pretty slick... Except.. for one thing, Firefox!

It seemed to be running slower on Intrepid than before on Hardy. It varies between different websites of course but it definetly takes longer to load webpages than it did under Hardy. If I understand correctly Hardy has Firefox 2 on its install disk and Intrepid has FF3? I did a side by side comparison with my desktop which still has Hardy on and this confirmed my observation (sure the specs arnt quite the same but this confirms my laptop observation)

I tried this to see if it helped: 
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)
It may have helped a bit but TBH it still way slower that it was before under Hardy.

Anyone else having this problem right now? AND how do I get it running faster? Mozilla's goes on about FF£ being faster and better and I cant believe it really is inferior to FF2 so what  am I doing wrong?

I suppose I could revert back to Hardy or install FF2 back into Intrepid if everything else fails. Any ideas?

---

### Post by xJoo Unitx on 2008-12-29
> **mariane_08 said:**
> I just installed Intrepid on my laptop. Everythings worked pretty slick... Except.. for one thing, Firefox!

It seemed to be running slower on Intrepid than before on Hardy. It varies between different websites of course but it definetly takes longer to load webpages than it did under Hardy. If I understand correctly Hardy has Firefox 2 on its install disk and Intrepid has FF3? I did a side by side comparison with my desktop which still has Hardy on and this confirmed my observation (sure the specs arnt quite the same but this confirms my laptop observation)

I tried this to see if it helped: 
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)
It may have helped a bit but TBH it still way slower that it was before under Hardy.

Anyone else having this problem right now? AND how do I get it running faster? Mozilla's goes on about FF£ being faster and better and I cant believe it really is inferior to FF2 so what  am I doing wrong?

I suppose I could revert back to Hardy or install FF2 back into Intrepid if everything else fails. Any ideas?

I'm not sure if you're looking to change something IN firefox, but there are tips all over the internet about how to speed firefox up.  I use this one, it works pretty well.
[http://rahulhackingarticles.wetpaint.com/thread/773173/cool+mozilla+tricks+just+try+them+out?t=anon](http://rahulhackingarticles.wetpaint.com/thread/773173/cool+mozilla+tricks+just+try+them+out?t=anon)

---

### Post by ajcham on 2008-12-29
Actually Hardy used the Firefox 3.0 beta, not FF2.

---

### Post by Cracauer on 2008-12-29
The urlclassifier problem?

What's the largest file in your profile?

---

### Post by mariane_08 on 2008-12-29
> **xJoo Unitx said:**
> I'm not sure if you're looking to change something IN firefox, but there are tips all over the internet about how to speed firefox up.  I use this one, it works pretty well.
[http://rahulhackingarticles.wetpaint.com/thread/773173/cool+mozilla+tricks+just+try+them+out?t=anon](http://rahulhackingarticles.wetpaint.com/thread/773173/cool+mozilla+tricks+just+try+them+out?t=anon)

I assume I need to change something in Firefox since the rest of the installation is working nicely. I'll take a look at your tip..Thanks 

"ajcham  .....  Actually Hardy used the Firefox 3.0 beta, not FF2."

I stand corrected! 

"Cracauer  ....  	The urlclassifier problem?"
What's the largest file in your profile?"

Sorry I not quite sure what you're asking? 

Thanks

---

### Post by utnubuuser on 2008-12-29
Hi -- I find some pages to be very slow.  --To the degree that I have to hit the reload button to actually get a page to finish loading.  -- This is only for some pages though.  I found FF2 to be way faster.  -- Too bad it's not in the Intrepid Ibex repos.

---

### Post by mariane_08 on 2008-12-29
> **utnubuuser said:**
> Hi -- I find some pages to be very slow.  --To the degree that I have to hit the reload button to actually get a page to finish loading.  -- This is only for some pages though.  I found FF2 to be way faster.  -- Too bad it's not in the Intrepid Ibex repos.

OK I've tried pretty much everything, all the tweaks, launching FF in safe mode etc etc. I even did a side by side this evening with someone else. There seems to be nothing I can do to get anywhere near the speed I got using Hardy. (whatever version that was? I thought it was FF2, someone tells me its ff3 beta....whatever..) Either way it was running very nicely and fast under Hardy. I dont blame Intrepid for this but Firefox 3

Unless someone can convince me otherwise, and I'm open to any thoughts you may have, I'll probably revert tomorrow.

My first preference would be to use FF2 here on Intrepid. How do I replace FF3 with FF2. It may not be in the repository but I can downlaod it right. What procedure to swap on efor the other should I follow? I'm a little new to this.

Failing the above I can just wipe Intrepid completely and go back to Hardy which I was more than happy with until I did this upgrade (downgrade?) over the weekend. Once again it not hardy which is the problem. And Firefox is fine too with everything else, its just the length of time loading the webpages

PLEASE send me any thoughts on all of above O:)

---

### Post by kjamo36 on 2008-12-29
Go to Edit
Preferences
Advance Icon
Network tab
Settings
Select- No proxy


After that u should be flying

---

### Post by Cracauer on 2008-12-29
> **mariane_08 said:**
> 

"Cracauer  ....  	The urlclassifier problem?"
What's the largest file in your profile?"

Sorry I not quite sure what you're asking? 

Thanks

This forum has at least one thread every three weeks where somebody discovers that his Firefox performance has been shot to hell by the urlclassifier. I wanted you to do a search :)

Or tell us what the largest file in your profile is. If the urlclassifier database is large it's that.

---

### Post by mariane_08 on 2008-12-30
[QUOTE=Cracauer;6459123]This forum has at least one thread every three weeks where somebody discovers that his Firefox performance has been shot to hell by the urlclassifier. I wanted you to do a search :)

Or tell us what the largest file in your profile is. If the urlclassifier database is large it's that.[/QUOTE

Well I created a new profile last night but didn't really change much. I cant say that none of these variations or tweaks haven't helped some, but performance is nowhere near what it was.

is this what you mean?

nsUrlClassifierLib.js   /usr/lib/xulrunner-1.9.0.3/components   49.6KB  

nsUrlClassifierListManager.js  /usr/lib/xulrunner-1.9.0.3/components   19.6KB

---

### Post by mariane_08 on 2008-12-30
I don't understand why this is happening. Hardy 8.04 has FF 3 beta 5. Intrepid 8.10 has (I believe) FF 3.0.5. The difference is  amazing. 

If anyone has any other perspectives or ideas I'd sure like to hear them, Imean anything! Otherwise I thinking about trying to remove FF from intrepid and install FF3b5 instead or simply going back to Hardy

Mariane

Laptop: Compaq Presario M2000
AMD turion 64, 1GB RAM

Desktop: Acer L100
AMD athlon 64 3800+, 2GB RAM

---

### Post by SuperSonic4 on 2008-12-30
Try firefox 3.1 beta 2, It's faster than 3.0.5 and isn't such a memory hog although you can only get it from the [**[COLOR="Red"]mozilla site[/COLOR]**]("http://www.mozilla.com/en-US/firefox/all-beta.html")
Plus it has amazon UK in the search bar ;)

---

### Post by zika on 2008-12-30
> **SuperSonic4 said:**
> Try firefox 3.1 beta 2, It's faster than 3.0.5 and isn't such a memory hog although you can only get it from the [**[COLOR=Red]mozilla site[/COLOR]**]("http://www.mozilla.com/en-US/firefox/all-beta.html")
Plus it has amazon UK in the search bar ;)
try nightly, it's even faster ... (at least on my machine ...):[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.2a1pre.en-US.linux-x86_64.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.2a1pre.en-US.linux-x86_64.tar.bz2)


**Update:**

I've stumbled upon the sites ( [http://benjamin.smedbergs.us/blog/20...zilla-central/]("http://benjamin.smedbergs.us/blog/2008-12-18/nightly-testers-needed-for-mozilla-central/") and [http://benjamin.smedbergs.us/blog/tag/shiretoko/](http://benjamin.smedbergs.us/blog/tag/shiretoko/) ) that explained to me what version of FF I'm running. i.e. there are two branches of nightly: a Minefield branch that is totally experimental and is, after this branch, leading toward FF3.2 and on, and a Shiretoko (or 1.9.1 for Gecko) branch that is more stable and leading toward FF 3.1. mind that explanation about how to recognize what version are You running from the title of Your FF window is not correct. In Shiretoko it says: Shiretoko. I've forgot what it says on Minefield, ... all of You that have been using FF dl-ed before Nov. 24th are (via updates) rerouted on a Shiretoko branch. Minefield is branch that lives up to its name ... :wink: You have to enter it on Your own risk ... :smile:

links are:
- for Shiretoko (I'm using that now) [http://ftp.mozilla.org/pub/mozilla.o...mozilla-1.9.1/]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-1.9.1/") 
- for Minefield (I've abandoned it for now on in order to be a bit safer, but as I can see, I've gave up a bit of speed too) [http://ftp.mozilla.org/pub/mozilla.o...zilla-central/]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/")  or, (most of the times) the same, [http://ftp.mozilla.org/pub/mozilla.o.../latest-trunk/]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/")  

it's easy, since it doesn't include any installing, just extracting. :smile:

---

### Post by cb34 on 2008-12-30
purging all firefox related stuff with synaptic/apt-get, and in my case because i dont use samba or anything like that, i removed winbind, samba, xulrunner 1.9 and xulrunner-1.9-gnome-support after backing up my bookmarks, plugins etc. of course, and also the ~/.mozilla dir with the profiles and settings then i only use tar.gz packages off mozilla's site, make a firefox dir in my ~/bin, and "unzip" there so there's no firefox files all over the machine, and you can run multiple versions of firefox easily from ~/bin/firefox2 ~/bin/firefox-3.0.5 ~/bin/firefox-3.1b2 etc. for example in case you want to for testing purposes like i was doing.. but that's a different thing if you need help with just ask, need to do a couple things for that to work right.. but just by using a fresh install and all in one dir my firefox sped up.. alot. loading it up first time in a session is also really fast now.. also check this out..
[http://ubuntuforums.org/showthread.php?t=1025849](http://ubuntuforums.org/showthread.php?t=1025849)
and also do a search on google for "firefox tweaks" or similar and you'll find alot more tweaks to apply in about:config.. there's at least about 8-10 more things you can do that will affect speed.. gotta dig around.. they're all in the first 10 finds from that google search for sure though. ;)

---

### Post by akelsall on 2008-12-30
mariane_08, I haven't had much luck at all with FF3 (in Ubuntu 8.04 or 8.10). There is a know bug with resizing text (where it takes 20+ seconds to resize and locks up the whole browser), and I've experienced the issue you mentioned.

I had gotten so frustrated with it that I switched to Opera and have not looked back since. I really love the "speed dial" feature of Opera and it's fast!

Andy

---

### Post by mariane_08 on 2008-12-31
> **akelsall said:**
> mariane_08, I haven't had much luck at all with FF3 (in Ubuntu 8.04 or 8.10). There is a know bug with resizing text (where it takes 20+ seconds to resize and locks up the whole browser), and I've experienced the issue you mentioned.

I had gotten so frustrated with it that I switched to Opera and have not looked back since. I really love the "speed dial" feature of Opera and it's fast!

Andy

Thanks Andy! I'm temted to give Opera a try anyway :)

Maiane

---

### Post by linfidel on 2009-01-05
FWIW, I've been getting frustrated with Firefox ever since I upgraded to Intrepid.  It's sometimes slow, and it often completely goes to sleep and doesn't respond at all for 10 - 20 seconds, sometimes much longer.  And not necessarily when it's been running for a while or a lot of pages open.

I tried Opera for a bit, but didn't really like it overall.  Epiphany isn't bad, but still, Firefox is the one I want to use.

I know a lot of people that are having such problems, and I have yet to hear about a solution that works, that doesn't involve switching to another browser.

BTW, if you download a version from Mozilla instead of the "official" Ubuntu version, I believe you will no longer get automatic upgrades and security fixes as they come out, so you will need to do this on your own.

---

### Post by zika on 2009-01-06
i'm sorry, I've lost signal for a short period so there are two posts.

---

### Post by zika on 2009-01-06
>  BTW, if you download a version from Mozilla instead of the "official" Ubuntu version, I believe you will no longer get automatic upgrades and security fixes as they come out, so you will need to do this on your own.I think opposite. if You just extract it in a folder and run it from there. that way You still have original installation and in terms of udates You've changed nothing.

"official" version of Firefox and a new one are living together and sharing the same settings. at one time I had "official", Minefield and Shiretoko living happily together. if I changed something in setting or add-on-s for one all three used it ... now I am down to two. Minefiled is stable and quick. Swifweasel uses its own settings and that makes it great for backup-browser.

---

### Post by sendblink23 on 2009-01-06
Yeah .. Stick.. with  *OPERA* its way faster

---

### Post by Cracauer on 2009-01-06
You need to turn off "block reported attack sites" in the security preferences to get rid of the urlclassifier madness.

Or just delete the file every day.

---

### Post by mariane_08 on 2009-01-06
> **Cracauer said:**
> You need to turn off "block reported attack sites" in the security preferences to get rid of the urlclassifier madness.

Or just delete the file every day.

In Firefox preferences>security I don't see an option to "block attack sites" I just see the 2nd option "tell me if the site I'm visiting is an attack site" Is this what you mean?

---

### Post by linfidel on 2009-01-06
> **zika said:**
> I think opposite. if You just extract it in a folder and run it from there. that way You still have original installation and in terms of udates You've changed nothing.

"official" version of Firefox and a new one are living together and sharing the same settings. at one time I had "official", Minefield and Shiretoko living happily together. if I changed something in setting or add-on-s for one all three used it ... now I am down to two. Minefiled is stable and quick. Swifweasel uses its own settings and that makes it great for backup-browser.
You missed the point - it doesn't help if you update a version of a program that you're not using.  The settings that they are sharing is not what is getting updated, it's the program itself.  So, if there is a security update, you need to go to the Mozilla site to do the update manually, it won't get updated by Ubuntu.

---

### Post by Camilia on 2009-01-06
Yeh, firefox is running slow today. Especilly when it comes downloading pictures. Think of switching to Opera.

---

### Post by zika on 2009-01-07
> **linfidel said:**
> You missed the point - it doesn't help if you update a version of a program that you're not using.  The settings that they are sharing is not what is getting updated, it's the program itself.  So, if there is a security update, you need to go to the Mozilla site to do the update manually, it won't get updated by Ubuntu.
yes it will because its configuration, system-wise, has not been changed.

afterthought: wait a minute, You mean Minefield or Shiretoko would not be updated. that's OK with me since I'm taking care of that. since I'm using all the time ... I've meant FF 3.0.5 will be updated by system.

---

