---
title: "How to make Firefox use RealPlayer?"
date: 2006-11-05
forum: Desktop Environments
---

### Post by christian.convey on 2006-11-05
I'm running an up-to-date Edgy (6.10), and I've got some of Automatix2's customizations enabled.

When I'm in Firefox I go to this page:
[http://www.npr.org/templates/rundowns/rundown.php?prgId=35](http://www.npr.org/templates/rundowns/rundown.php?prgId=35)

When I click on the link labelled, "Listen to the whole show" (near the top right), the browser goes to a new page which is fully populated by what appears to be an mplayer plugin.

The problem is, I kind of like RealPlayer better for playing Real Audio streams.  I can't figure out how to be given the choice, or at least have Firefox default, to using realplayer.

I've gone to the menu: Edit --> Preferences, and clicked on the Content tab.  Then I click on the button for "Managa..." file types.  The dialog that comes up lists some file types, but not RA/RAM types.  So I'm also confused about why this dialog, which looks designed to offer the control I'm looking for, doesn't show all relevant file types.

Any suggestions?

Thanks,
Christian

---

### Post by apjone on 2006-11-05
firefox > edit > prefrences > downloads (tab) > view & edit actions. 

you can change it in there.

---

### Post by christian.convey on 2006-11-05
I don't see a "Downloads" tab.  When I do Edit > Preferences (in Firefox 2.0, btw), I get these tabs in the dialog that pops up:

Main, Tabs, Content, Feeds, Privacy, Security, Advanced.

Any idea why we have a discrepancy?

---

### Post by mrhelpman on 2006-11-05
You are not the only one who does not have a downloads tab.

I am having the same problems with firefox and realpayer on edgy.  Luckily I still have Dapper on a different machine so I can see that I have firefox 2 setup the same as 1.5.0.7.  They look like they are both confgured the same - same symoblic links between firefox and real player but nothing on the BBC site will play with firefox 2 on edgy.

---

### Post by mrhelpman on 2006-11-05
OK, I have solved the problem on my Edgy now. As others have pointed out in a number of similarly titled threads, the problem I was experiencing was due to totem trying to play the real player streams (.ra) and failing. I looked at the plugins page by entering about:plugins in the url bar and found that the totem pluging trying to play the BBC stream was libtotem-complex-plugin.so. This is configued as a plugin in firefox by placing two symbolic link files in the /usr/lib/firefox/plugins directory that point to the files libtotem-complex-plugin.so and libtotem-complex-plugin.xpt in /usr/lib/totem.

I removed these two symlinks:
$ cd /usr/lib/firefox/plugins/
$ sudo rm libtotem-complex-plugin.so
$ sudo rm libtotem-complex-plugin.xpt 

Dont worry these are not files - they are symbolic links.

Restart firfox and I can view the BBC news videos, listen to live radio  and the listen again streams flawlessly. I hope this helps other hear.

I don't think there is any need to remove any packages, just these two symbolic links.  They can be easily recreated if requred later by :
 
$ sudo ln -s ../../totem/libtotem-complex-plugin.so libtotem-complex-plugin.so

and
$
 sudo ln -s ../../totem/libtotem-complex-plugin.xpt  libtotem-complex-plugin.xpt
$ 


sudo ln -s /usr/lib/totem

---

### Post by mrhelpman on 2006-11-05
> sudo ln -s /usr/lib/totem

Ignore this last line - I dont know where this came from - just dodgy cutting and pasting - sorry !

JT

---

### Post by mdurham on 2006-11-05
I just uninstalled the totem plugin with Synaptic and FF used RealPlayer after that. Since then, no worries.

---

### Post by sam81 on 2006-11-06
Thanks mrhelpman, worked like a charm, the bbc is back streaming on my box!

---

### Post by ron999 on 2007-02-22
Thanks mrhelpman, that worked for me too:D :D

---

### Post by bedake on 2007-02-22
Hey that worked great, thanks!  Though it seems now, when I listen to the BBC radio streams it lags my firefox completely every couple of seconds, any ideas on what this could be?

---

### Post by ron999 on 2007-02-24
It hasn't solved my problem entirely.
I sometimes get the message 'Could not find an appropriate hxplay or replay in the system path to use as an embedded player'.
Is there anything else that I should try?

---

### Post by davidobyrne on 2008-02-20
Ron
Run the Realplayer bin as root.
This will unpack realplayer and also
install the system wide links.

Once you do that firefox will find realplay fine.

hope this helps
David

---

### Post by RayPioli on 2008-04-26
This is driving me crazy. 

I am completely new to the world of linux & ubuntu but trying to push the envelope of my computer understanding.

I cannot get RealPlayer plugin to work despite following these and other instructions meticulously.

I am using:

Newly released Ubuntu 8.04 (includes with Firefox 3 beta)
RealPlayer 11
Flash

Flash player is installed and works fine
Realplayer works in stand alone mode but not as Firefox plugin

Therefore I cannot sites like BBC to work 

Any assistance greatly appreciated

Ray

---

### Post by RayPioli on 2008-04-26
Found Solution to the problem in another post.

copied nphelix.xpt and nphelix.so to /usr/lib/firefox-3.0b5/plugins

Whatever all this means

---

