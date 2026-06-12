---
title: "Ubuntu 8.04 Firefox"
date: 2008-04-24
forum: Desktop Environments
---

### Post by sorfrena on 2008-04-24
Hi all,

I just installed ubuntu 8.04 and I find firefox 3b5 really good...but it is not still supported a lot: my favourites addons do not work, eg google browser just to say one.
Is there any way to go back to firefox 2?

Thanks all

---

### Post by KOTAPAKA on 2008-04-24
Yep uninstall firefox 3 and install firefox 2 either apt-get/aptitude or via synaptic.

---

### Post by rhc on 2008-04-24
Or you can close extension security control option of Firefox,
so most of your addons will work.

---

### Post by bjorntj on 2008-04-24
Or you can disable the compatibility check... :)

Go to "about:config" and create a new boolean entry "extensions.checkCompatibility" set to "false". This will disable the compatibility check and you can install any extension...



BTJ


Edit: Hmmm.... rhc just beat me.... :-|

---

### Post by rhc on 2008-04-24
> **bjorntj said:**
> Or you can disable the compatibility check... :)

Go to "about:config" and create a new boolean entry "extensions.checkCompatibility" set to "false". This will disable the compatibility check and you can install any extension...



BTJ


Edit: Hmmm.... rhc just beat me.... :-|

I didn't write howto.
You beat me infact.

---

### Post by bjorntj on 2008-04-24
Ok then... :)

---

### Post by jonboy99 on 2008-04-24
Unfortunately disabling the check still doesn't let google browsersync work, which is the deal breaker for me - back to firefox 2 for now.

However it isn't in the repos - only firefox 3 (final release of hardy).  Where can I get it from?

---

### Post by Whisperwind on 2008-04-24
Ahoy,

Take a look at the following link, thats about as far as it goes installing firefox 2 again, after removing firefox b5.

[http://ubuntuforums.org/showthread.php?t=702915](http://ubuntuforums.org/showthread.php?t=702915)

Maybe it doesnt help, er.

I think though the executable inside the linux 'tar' archive can just be run and it imports your b5 details if theres anything left, ofcourse.

Cya.

Edit: Me I like b5, YouPlayer works, and of course fluxbox and beta 5 are a match made in performance heaven :D

---

### Post by jonboy99 on 2008-04-24
Well, browser sync won't install now i've installed firefox 2 either.  Ah well, i'll stick with dapper for now.

---

### Post by jonboy99 on 2008-04-24
Ok, i've got my toys back in the pram now.  It appears that 'remove all' from synaptic does nothing of the kind as far as firefox is concerned.
No extensions would install - some would say they were not compatible with version 2 of firefox despite being what they were designed for, and all the others would come up with an installlocation error in the error console after attempted installation.

First I did a 'complete removal' (haha) of anything firefox related in synaptic. 
I then had to manually delete the hidden .mozilla folder in my home folder, and then with a 'sudo nautilus' manually deleted 2 firefox folders (firefox and firefox addons i think) in the /usr/lib directory.  

I then reinstalled firefox 2 using synaptic and all has been well since.

Maybe that extremely helpful chap who runs psychocats.net should have a new section entitled 'installing old firefox'.  ;)

---

### Post by Bytor on 2008-04-24
I just want to know who the dummy was who decided upon putting a beta version of a major program like a browser into a what is supposed to be a Long Term Support release of Ubuntu? Especially when most add-ons don't yet work for FFX 3.

Somebody wasn't thinking. :-P

---

### Post by sorfrena on 2008-04-25
Go to "about:config" and create a new boolean entry "extensions.checkCompatibility" set to "false". This will disable the compatibility check and you can install any extension...
-->

Can you tell me how to do this pleas?


Any ways bytor, I really agree with you. I am personally thinking in going back to 7.10...I find this release too premature, it seems like a beta, not an official release.
Brightness problems with my laptop, installation of vmware didn't work as usual, repositories seem not to be ready ye, firefox addons...
I think it's a great distribution, but it still needs some time, that's all: for example I found great a thing: hardy heron recognized all alone my webcam bulti-in laptop, without any driver. This is a proof of the great effort spent...but I think in a couple of months, or less, we'll be able to enjoy much more all this. Moreover ubuntu wants to replace vista...and generally microsoft in personal desktops, so I think this things will be all solutioned really soon, because the average user to which ubuntu aims, doesn't want all these little problems...that a linuxer can handhe, but him not.
Just personal thought :-)

Any ways...how do I do this: 
Go to "about:config" and create a new boolean entry "extensions.checkCompatibility" set to "false". This will disable the compatibility check and you can install any extension...
-->
where is the about:config file?

Thanks all

---

### Post by mac_john on 2008-04-25
After downgrading to Firefox 2 any extension worked, neither I was able to uninstall them or reinstall them.

I created a new profile, and reinstalled all from scratch, copying preferences from the old profile.

This guide help me a lot:

[http://support.mozilla.com/en-US/kb/Recovering+important+data+from+an+old+profile](http://support.mozilla.com/en-US/kb/Recovering+important+data+from+an+old+profile)

---

