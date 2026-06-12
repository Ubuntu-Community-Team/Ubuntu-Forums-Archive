---
title: "Firefox broke"
date: 2005-09-25
forum: Desktop Environments
---

### Post by Jvaldezjr on 2005-09-25
I tried to upgrade to 1.0.7 yesterday with Synaptic, and I got some errors after it downloaded. 

```

E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
E: /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support

Preconfiguring packages ...
(Reading database ... 166727 files and directories currently installed.)
Preparing to replace mozilla-firefox 1.0.6-1ubuntu1~5.04ubp1 (using .../mozilla- firefox_1.0.7-0ubuntu0.1_i386.deb) ...
Unpacking replacement mozilla-firefox ...
dpkg: error processing /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_ i386.deb (--unpack):
 trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is  also in package firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace mozilla-firefox-gnome-support 1.0.6-1ubuntu1~5.04ubp1 (usin g .../mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb) ...
Unpacking replacement mozilla-firefox-gnome-support ...
dpkg: error processing /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0 .7-0ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which  is also in package firefox-gnome-support
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb
 /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb

```

Now it didn't install correctly but when I try to run firefox, it just hangs, and the browser never opens.  How do I fix it?

---

### Post by kashms on 2005-09-25
I had the same problem. I first uninstalled the previous version (1.06) and then installed 1.07. That worked.

---

### Post by MBro on 2005-09-25
Same problem for me.  I'm running opera now because of it.  When I try to open firefox firefox-bin eventually just appears in the task list but of course, nothing shows up.  I think it' sjust a bad packageing job.

---

### Post by beerorkid on 2005-09-26
yeah mine is super borked as well.

super bummed, hope it will get fixed soon.

Thought about reinstalling ubuntu, saw forums were down and waited.  Glad I did so hopefully it will work soon.

I have been messing with it fro about 3 hours now. 
Anybody got a fix?
tried the uninstall reinstall, no luck.

---

### Post by wadesmart on 2005-09-26
09262005 1113 GMT-5

After that happened to me I tried again thinking something had happened during the download. But then, I couldnt uninstall Firefox and I couldnt reinstall it. 

You might have seen the post on Planet Ubuntu about removing the mirrormax links. I did that but now I have other updates that wont complete. 

Wade

---

### Post by locque on 2005-09-26
I got it to successfully upgrade today... It was a pain. I had to run

dpkg --purge mozilla-firefox mozilla-firefox-gnome-support ubuntu-desktop

Then I commented out the mirrormax entries in /etc/apt/sources.list

ran: apt-get update && apt-get install mozilla-firefox ubuntu-desktop mozilla-firefox-gnome support 

and voila!!!

---

### Post by mulperi on 2005-09-26
I had exactly the same problems...  after automagic update firefox did not install correctly. Fortunately I had installed Opera (that is actaully very good). After much messing around I noticed that in the synaptic list there are:
firefox 1.06
firefox-gnome-support 1.06
mozilla-firefox 1.07
mozilla-firefox-gnome-support 1.07

So I suppose that was my problem, I had tried to install wrong versions somehow. What I did was:
```
sudo apt-get remove firefox 
sudo apt-get remove firefox-gnome-support
sudo apt-get remove mozilla-firefox 
sudo apt-get remove mozilla-firefox-gnome-support
sudo apt-get install mozilla-firefox 
sudo apt-get install mozilla-firefox-gnome-support
```

...and it worked. Tellme if you manage to get it running.

//mulperi

---

### Post by beerorkid on 2005-09-26
weeeeeeeeeeeeeeeeeeeeeeeeeee

they must have fixed something, cuz when I updated it grabbed a bunch of stuff.

Followed above commands and it worked this time.

thanks.

---

### Post by JimmyBEng on 2005-09-26
[QUOTE=locque]I got it to successfully upgrade today... It was a pain. I had to run

dpkg --purge mozilla-firefox mozilla-firefox-gnome-support ubuntu-desktop

Then I commented out the mirrormax entries in /etc/apt/sources.list

ran: apt-get update && apt-get install mozilla-firefox ubuntu-desktop mozilla-firefox-gnome support 

and voila!!![/QUOTE]
I did the same thing just using synaptic and it fixed the problem for me.

---

### Post by spacemonkey on 2005-09-26
I had the same problem, I removed the old version and commented out the backports, and was able to get the new version from the security repos installed, but I still can't run firefox.  When I run it in a terminal, this is what I get:

(firefox-bin:16505): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.


Then nothing happens, it just goes back to the prompt.  Any suggestions?

---

### Post by beerorkid on 2005-09-26
so my wife's just died and I had her do:

```
sudo apt-get remove firefox 
sudo apt-get remove firefox-gnome-support
sudo apt-get remove mozilla-firefox 
sudo apt-get remove mozilla-firefox-gnome-support
sudo apt-get install mozilla-firefox 
sudo apt-get install mozilla-firefox-gnome-support
```

and it did not work, then she rebooted and it did.

so maybe reboot?

---

### Post by scflymedic on 2005-09-26
Hey Beer,
Thanks for the fix, although I did not have to reboot the whole system, just restarted firefox.  Thanks again!
Chuck

---

### Post by wadesmart on 2005-09-26
09262005 1450 GMT-5

What is yelp? When I try to install Firefox it says that it depends upon yelp. 

Also, since all of this stuff begane this weekend, I cant use Synaptic. It just stalls upon start up. 

Wade

---

### Post by wadesmart on 2005-09-26
09262005 1455 GMT-5

How did you deal with this: 
E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox

I tried that purge from below.

Wade

---

### Post by beerorkid on 2005-09-26
I just coppied the code from an earlier post, thanks to mulperi.

I would add make sure you 
apt-get update
before you do the stuff. 

I also got the 
```

E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb: trying to overwrite 
`/var/lib/mozilla-firefox/extensions.d/00classic',
```
before I did an apt-get update

I am sure something has been fixed in the repositories today.  Also comment out the back ports is something that has been mentioned.

---

### Post by wadesmart on 2005-09-26
09262005 1509 GMT-5

Ok. I did update then purge then install and I received this error: 

Errors were encountered while processing:
 /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Wade

---

### Post by agm642 on 2005-09-26
Well, somehow, it worked for me right away... I mean, I simply installed firefox and I had no problems at all. :confused:  [QUOTE=wadesmart]
Also, since all of this stuff begane this weekend, I cant use Synaptic. It just stalls upon start up. [/QUOTE]
I actually could not run anything requing root privileges from the menu, I gave it my password and it just never started, but when I started it from a terminal using sudo, it worked. :confused: I then upgraded all the packages in my system, (including sudo) and it worked...

---

### Post by wadesmart on 2005-09-26
09262005 1539 GMT-5

I tried the purge again this time adding firefox and then that error message went away. However, when it finished installing, when I clicked the icon to start, it did the same thing again -> msg stating its starting and then it crashes. 

Wade

---

### Post by wadesmart on 2005-09-26
09262005 1756 GMT-5

I did everything one more time and then rebooted - per that last post - and that fixed everything.

Thanks everyone here who has the knowledge to help us that dont. 

Wade

---

### Post by orb_nsc on 2005-09-26
[QUOTE=mulperi]I had exactly the same problems...  after automagic update firefox did not install correctly. Fortunately I had installed Opera (that is actaully very good). After much messing around I noticed that in the synaptic list there are:
 (etc)
//mulperi[/QUOTE]

This fix did the trick for me, thanks Mulperi.  But the downtime with Firefox did give me a few days to get reaquainted with the newly free Opera, and I think I'll be using it more from now on.  :)  But at least good ole FF is functional again...

---

### Post by Jvaldezjr on 2005-09-27
[QUOTE=mulperi]I had exactly the same problems...  after automagic update firefox did not install correctly. Fortunately I had installed Opera (that is actaully very good). After much messing around I noticed that in the synaptic list there are:
firefox 1.06
firefox-gnome-support 1.06
mozilla-firefox 1.07
mozilla-firefox-gnome-support 1.07

So I suppose that was my problem, I had tried to install wrong versions somehow. What I did was:
```
sudo apt-get remove firefox 
sudo apt-get remove firefox-gnome-support
sudo apt-get remove mozilla-firefox 
sudo apt-get remove mozilla-firefox-gnome-support
sudo apt-get install mozilla-firefox 
sudo apt-get install mozilla-firefox-gnome-support
```

...and it worked. Tellme if you manage to get it running.

//mulperi[/QUOTE]

This worked for me.  I got error messages while trying the remove commands, however they were removed, and installed properly.

---

