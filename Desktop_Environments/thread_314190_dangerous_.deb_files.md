---
title: "dangerous .deb files"
date: 2006-12-07
forum: Desktop Environments
---

### Post by stansaraczewski on 2006-12-07
Last night I attempted to install TOra from sourceforge.net and ended up having to reinstall my Ubuntu system. 

I've installed a number of .deb files and felt comfortable watching the messages scroll then I started noticing that directories completely unrelated were being deleted for some reason - when the messages finally stopped I tried to open a terminal window and got an error. The reboot stopped at a blank brown screen.

That's when I realized what had happened and started rebuilding. 

Not that big of a deal, a recent install without too much work to recreate.

SO - what happened ? Is there a way to 'dry run' a .deb file ?

I've lost a bit of trust here...

BTW - the file is tora_1.3.21-1_debian.i386.deb

---

### Post by loell on 2006-12-07
this problem should better be address directly in tora project , 
as for dangerous deb files, well we will see this frequently in the future , just make sure you know your trusted sources.

ofcourse deb package compatibility is also an issue if you try to install deb package not specifically built for ubuntu

---

### Post by stansaraczewski on 2006-12-07
It was a .deb file... should not have deleted directories at any rate even if it wasn't compatible. Yes, should be directed there. My next step.

BTW - isn't sourceforge a trusted site ?

I was using a mirror site on the west coast - and did not pay attention to which one.

---

### Post by Qew on 2006-12-07
From man dpkg:

       --no-act | --dry-run | --simulate
              Do  everything  which  is  supposed to be done, but don&#8217;t
              write any changes. This is used to see what would  happen
              with  the  specified  action,  without actually modifying
              anything.

              Be sure to give --no-act before the action-parameter,  or
              you  might  end up with undesirable results.  (e.g.  dpkg
              --purge foo --no-act will first  purge  package  foo  and
              then try to purge package --no-act, even though you prob&#8208;
              ably expected it to actually do nothing)

---

### Post by loell on 2006-12-07
> **stansaraczewski said:**
> 

BTW - isn't sourceforge a trusted site ?

I was using a mirror site on the west coast - and did not pay attention to which one.

yes mostly they can be trusted, but packaging can be  assigned to any people too, who had some  interest with the project , probably the developers did not test the deb package, because most likely his distribution is rpm base, maybe he just accepted the deb package without verifying from other users.

---

