---
title: "How do I really install Flash in Ubuntu 8.04?"
date: 2008-12-26
forum: General Help
---

### Post by mjpatey on 2008-12-26
Hi, all!

I'm troubleshooting a problem in Ubuntu 8.10, and as part of it, I'm trying to get the Flash plugin for Firefox working in 8.04..  I've copied libflashplayer.so to ~/.mozilla/plugins (I had to create the /plugins directory, as it didn't exist).

I also tried installing it from the terminal (sudo apt-get install adobe-flashplugin), and it showed as already having been installed.

The problem is, it isn't functional; indeed, when I go to about:plugins in Firefox, it doesn't show up on the list.

Should I be placing the libflashplayer.so file in another directory?  I'm obviously missing something, I just can't figure out what.

One other bit of info:  the Ubuntu 8.04 install I'm using for this is running on a virtual machine (32-bit) in Virtualbox.  Virtualbox itself is running on 64-bit hardware, inside my 64-bit Ubuntu 8.10 install.

Thanks for any light you can shed!

-Mark

---

### Post by mjpatey on 2008-12-26
OK, I just did a little more research and found the newer package name for installing Flash is "flashplugin-nonfree" and not "adobe-flashplugin".  I removed the /plugins directory that I'd created, and installed flashplugin-nonfree, and voila!  Flash works!  It's Flashplayer 9, though.

The issue I've been having is that on Ubuntu 8.10, I can't seem to get certain Flash content to work, in Firefox or any other browser.  Most content works, but not all.  So I was trying to see if it would work on 32-bit 8.04 instead of my usual 64-bit 8.10.  Maybe my issue in 8.10 is that I'm using a Beta version of Flash 10?

---

### Post by Monotoko on 2008-12-26
all you need to use is:
```
sudo apt-get install ubuntu-restricted-extras
```
and leave it to do its thing, it will install not only flash, but java etc as well

---

### Post by kelean on 2008-12-26
I had trouble installing the flash player plug-in.  Went to the adobe site and downloaded the new flash player 10 and installed it with gdebi installer and what do you know it works great.

---

### Post by ju2wheels on 2008-12-26
Theres a 64bit beta version of Flash out but you have to remove the flash install by the repositories and install it by hand. It is IMHO much much more stable than the one in the repositories and you get the added benefit that it is 64bit flash.

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) Grab the Linux tar file at the bottom. Make sure to remove the flashplugin-nonfree package and i believe nswrapper from the repositories first.

I would also recommend running the following command, and removing any occurences of it or replacing them with the downloaded file:
```

locate libflashplayer.so

```

For Firefox, just extract that downloaded file to: /usr/lib/mozilla/plugins/

Restart Firefox and you should be all set.

---

### Post by SonnHalter on 2008-12-26
could just go get ultamatix. linux newb's best friend

---

### Post by ramjedi on 2008-12-26
Install the plug-in using the Synaptic Package Manager in System>Administration>Synaptic Package Manager.

---

### Post by AlexBellisBrown on 2008-12-27
Ditto, now that flash is in the repos, i recommend getting it from there. Easy, and in just a few clicks. :)

---

### Post by oldos2er on 2008-12-27
> **SonnHalter said:**
> could just go get ultamatix. linux newb's best friend

 Use of ultamatix isn't supported or encouraged.

---

### Post by mohawk82 on 2008-12-27
I could not get the one in the repository to work.

The version that I downloaded from Adobe works fine. (10.0.15.3-1)

Just my $0.02

Norman881

---

### Post by mjpatey on 2008-12-27
Thanks for all the replies.  I actually just installed ubuntu-restricted-extras and all is well!

On my "actual" (non-virtual) install, which is 8.10, I've been using the 64-bit Flash 10 Beta for some time now, and it's been great.  It just doesn't seem to play certain content for me, i.e. Word Challenge, a Facebook game.  So I tried playing the game in my virtual install of 8.04, and ran into the endless loop of Firefox "helping" me install the Flash player over and over without any results.

So I simply removed libflashplayer.so (v.10 beta) from my main install and installed ubuntu-restricted-extras, and all's well!

Thanks again for all the replies and discussion.  I haven't used locate or slocate in ages!  I'd forgotten how useful they can be.  :-)

-Mark

---

### Post by mjpatey on 2008-12-27
P.S.:  Yes, stay away from any of those auto-install-everything scripts.  Maybe you can trust them, maybe you can't.

---

