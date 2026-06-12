---
title: "Firefox slowness"
date: 2005-10-14
forum: Desktop Environments
---

### Post by nix4me on 2005-10-14
There is definately a new slowness in Firefox.

Not sure what is going on but it seems to be a bit slower in Breezy.

Clicking from another window to Firefox is even a little slow in the transition.  Loading pages is also slower.

nix

---

### Post by manicka on 2005-10-14
have you disabled ipv6

enter about:config into the address bar

enter 'ipv6' in the filter

then toggle ipv6 disable to true

---

### Post by erikpiper on 2005-10-14
Along with ipv6, fasterfox is sweet

[http://fasterfox.mozdev.org/](http://fasterfox.mozdev.org/)

The installation instructions are valid on linux. Try it. You'l like it! (The site will explain what it does.)

---

### Post by nix4me on 2005-10-15
Its still slow compared to IE

---

### Post by oldlucky on 2005-10-15
Try this it should help.

Tip 1.
open a terminal enter:
cd /etc/modprobe.d/
sudo gedit aliases
change this : alias net-pf-10 ipv6
to this : alias net-pf-10 off

reboot your computer. 

Tip 2.

type about:config in your firefox browser

find this :  

network.dns.disableIPv6 (set it to true)
network.http.pipelining (set it to true)
network.http.pipelining.maxrequests (set it to 10)
network.http.proxy.pipelining (set it to true)

Then right click anywhere select (make > integer) enter this name

nglayout.initialpaint.delay 
and set its value to 0.

Restart firefox.

This should help a little i do this to all my computers
and it seems to help my browsing speeds.

Cheers oldlucky

---

### Post by ameerirshad on 2005-10-16
[QUOTE=nix4me]There is definately a new slowness in Firefox.

Not sure what is going on but it seems to be a bit slower in Breezy.
[/QUOTE]

Slow, slower, stalled................... blank!

I would love to know why!

---

### Post by justaguynpc on 2005-10-16
[QUOTE=ameerirshad]Slow, slower, stalled................... blank!

I would love to know why![/QUOTE]

How do I load Web site faster in Mozilla Firefox?

       1.

          Applications &#8594; Internet &#8594; Firefox Web Browser
       2.

          In the Navigation toolbar URL field enter about:config .
       3.

          Use the Filter field to change the following parameters:
              * network.dns.disableIPv6 - Set the Value parameter to true.
              * network.http.pipelining - Set the Value parameter to true.
              * network.http.pipelining.maxrequests - Set the Value parameter to 8.
              * network.http.proxy.pipelining - Set the Value parameter to true. 
       4.

          Restart Mozilla Firefox

---

### Post by nix4me on 2005-10-16
That stuff does little if anything to help.

Install Galeon and Epiphany and you will see that they are a little faster.  I haven't tried Opera yet.

nix

---

### Post by bionnaki on 2005-10-16
[QUOTE=oldlucky]Try this it should help.

Tip 1.
open a terminal enter:
cd /etc/modprobe.d/
sudo gedit aliases
change this : alias net-pf-10 ipv6
to this : alias net-pf-10 off

reboot your computer. 
[/QUOTE]

what does this do?

---

### Post by phend-one on 2005-10-16
[QUOTE=bionnaki]what does this do?[/QUOTE]

I think that disables ipv6 for any connections out of linux, not just firefox. That's just a guess though...:confused:

---

### Post by fishfork on 2005-10-16
[QUOTE=nix4me]There is definately a new slowness in Firefox.[/QUOTE]

There's a bug open about this at:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=15534](http://bugzilla.ubuntu.com/show_bug.cgi?id=15534)

I actually noticed this in Hoary as well. I found the official mozilla.org build much more responsive. If you want to try installing it, I've put a few tips on the wiki page here:
[https://wiki.ubuntu.com/LowEndSystemSupport](https://wiki.ubuntu.com/LowEndSystemSupport)

---

### Post by lupo on 2005-10-17
Here is my solution for the problem:
Download the firefox-installer from the [mozilla homepage]("http://download.mozilla.org/?product=firefox-1.0.7&os=linux&lang=en-US").
Next backup your existing firefox installation by copying the firefox-folder:
```
cd /usr/lib/
sudo cp -R  mozilla-firefox mozilla-firefox_backup

```
Change into the directory where you saved the installer-file.
Extract the installer with the following command:
```
tar xfz firefox-1.0.7.installer.tar.gz
```
Now we just have to run the installer as root and install firefox where the ubuntu-firefox version is currently installed:
```
cd firefox-installer
sudo ./firefox-installer
```
Choose in the dialog "usr/lib/mozilla-firefox" as installation path.
Confirm the question, if the currently firefox-installation should be deleted.
Now we have a fast firefox again and all plugins will still work :D 
Greets
 Lupo

---

### Post by fishfork on 2005-10-17
[QUOTE=lupo]install firefox where the ubuntu-firefox version is currently installed[/QUOTE]
I'd be a bit wary of doing this. What happens when the update manage comes out with a new version of firefox? I would suggest installing the new version to /opt/firefox or similar, and changing the symlink /usr/bin/firefox to point to it (you could use dpkg-divert to do it properly). I haven't tried this, but will soon.

---

### Post by lupo on 2005-10-17
[QUOTE=fishfork] What happens when the update manage comes out with a new version of firefox?[/QUOTE]

Simple answer: nothing happens ;) 
It's not the first time I installed the original firefox version over the excisting ubuntu-version. At Hoary time I've done it, because I needed the DOM-Inspector whose package was not compatible with the firefox package in the repository. :???: 
With the dist-upgrade from Hoary to Breezy I got the original (slower) ubuntu firefox version back. I think it's just a file replacement ;)

---

### Post by fishfork on 2005-10-17
Well if it works your way, fair enough. But in general it's a bad idea to change stuff in /usr/bin and /usr/lib yourself - these should be handled by the package manager. When Firefox 1.0.8 turns up in the repositories, it will either overwrite your custom version or come up with a load of errors.

---

### Post by Orodreth on 2005-10-17
I've got exactly the same problem. Firefox is extremely slow. Opera's 10 times faster, but I can't get plugins to work there...

---

### Post by mcpish on 2005-10-17
Wow, I just tried out that Opera browser based on the comments here.  You guys are right.. that browser is extremely fast.  I really like it.  
It's not in synaptec but I was very pleased to see that they actually have a Ubunty 5.10 specific deb file for download.

---

### Post by ameerirshad on 2005-10-17
Well actually, I got Opera installed and it is indeed much faster. However, sometimes one "need" firefox as Opera is thus secure that it doesn't support some feature (as richtext editing in for example Gmail!).......

The problem is, Firefox is not only slow, it makes my whole system block! It is thus annoying, makes me feel like I run that legacy OS called windows (anyone still remember that from back in the days?) :confused:

---

### Post by artnay on 2005-10-17
If you're willing to use software marked as beta, go on and grab the latest Deer Park build from [here]("http://www.mozilla.org/projects/firefox/"). It's a lot faster than 1.0.x builds. And it's not even vulnerable to the latest 1.0.7 exploit. Although all available extensions won't work while using 1.5b2, it's quite smooth. After 1.5 gets officially released, I really hope there's no requests to use Epiphany as a default browser in the next Ubuntu release (Dapper). And remember to backup your .mozilla directory in case you try the latest release!

---

### Post by Mr Frosti on 2005-10-17
I use Firefox extensively, and I got curious and tried Firefox 1.5 beta. This seems to be a lot faster than the current release of Firefox with instant response on the Back / Forward buttons, and a lighter, faster UI. Also, the Fasterfox extension just goes to speed it up that much more. Give it a shot I am glad to be running the beta - it hasn't crashed once.

---

### Post by fishfork on 2005-10-17
[QUOTE=artnay]If you're willing to use software marked as beta, go on and grab the latest Deer Park build from [here]("http://www.mozilla.org/projects/firefox/").[/QUOTE]
If you're going to do this, try the instructions I've put on the wiki [here](https://wiki.ubuntu.com/LowEndSystemSupport). Suggestions for improvements welcome. (Or edit it and add them yourself.)

---

### Post by HermanAB on 2005-10-17
Firefox uses the somewhat buggy Webmonky Javascript engine.  Try disabling Javascript and see whether the offending web sites work better.

I have learned to keep Javascript OFF until I happen to reach a site that absolutely must have it.  On those sites, it generally works, since the webmasters know what they are doing.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by dngpng on 2005-10-18
i've read the wiki and i'm wondering if i do as what it said, would my old profile still be available for the ubuntu version of firefox? (seems impossible)

---

### Post by fishfork on 2005-10-18
[QUOTE=dngpng]i've read the wiki and i'm wondering if i do as what it said, would my old profile still be available for the ubuntu version of firefox? (seems impossible)[/QUOTE]
I've found that the ubuntu version of firefox is sufficiently different to the mozilla version that I had problems using the same profile.  This is why the wiki says to rename the old profile.  You can of course try without renaming it, but you may have problems! You have been warned.

---

### Post by BIGtrouble77 on 2005-10-18
I've done everything to get firefox to speed up.  Some of the hacks seem to work, others don't.  Javascript/ajax pages are the worst by far.  I also tried v1.5 and while it's faster, it's still a dog.

Opera 8.5 is amazing.  It's not quite as compatible as firefox, but it's getting much closer.  It's 10x faster than firefox and behaves better, overall.  I have to install like 20 extensions to get really basic stuff working.(like a side panel)

---

### Post by dngpng on 2005-10-18
[QUOTE=fishfork]I've found that the ubuntu version of firefox is sufficiently different to the mozilla version that I had problems using the same profile.  This is why the wiki says to rename the old profile.  You can of course try without renaming it, but you may have problems! You have been warned.[/QUOTE]

ya, i've noticed that it's better to backup the old profile and i want to know if i could still use that renamed profile for my ubuntu version of firefox?

---

### Post by Rumpty on 2005-10-19
I deleted Mozilla Firefox in Synaptic, installed the .gz file of Firefox 1.0.7, and didn't bother renaming my profile. All seems to run ok, but then my Firefox installation is basic i.e. no extensions. Using Hoary here still, hope it is not a cardinal sin posting in the Breezy forum.

Anyway, I do think Firefox is now more "responsive". I wonder why?

---

### Post by dngpng on 2005-10-19
[QUOTE=Rumpty]I deleted Mozilla Firefox in Synaptic, installed the .gz file of Firefox 1.0.7, and didn't bother renaming my profile. All seems to run ok, but then my Firefox installation is basic i.e. no extensions. Using Hoary here still, hope it is not a cardinal sin posting in the Breezy forum.

Anyway, I do think Firefox is now more "responsive". I wonder why?[/QUOTE]


Seems they were talking about Firefox 1.5b

---

### Post by ameerirshad on 2005-10-23
[QUOTE=artnay]It's a lot faster than 1.0.x builds. And it's not even vulnerable to the latest 1.0.7 exploit. Although all available extensions won't work while using 1.5b2, it's quite smooth.[/QUOTE]
It's not only that my Firefox is slow...... it crashes as well, it stalls it gives all kind of Windows deja vu's, like a system that is running slower and slower and eventually stalls. It makes me feel weary to leave my computer on for more than three days running Linux! Under Hoary I left my computer on for 3 weeks, downloading a shitload of movies and music discographies, email and many other things that demand a lot of my CPU and memory, no problem.

Running aMule right now, and checking the System Monitor makes me aware how much memory it uses. Today, my computer stalled when I tried to use Beagle........ that's my problem, I don't think it's Firefox, it does the same under Epiphany (it doesn't however do it under Opera, so I guess it's the Gecko engine not working properly under Breezy).... but again, sorry folks, all the support given here doesn't solve my problem.... because I guess my problem is not so much Firefox as well as it is Breezy:???:

---

