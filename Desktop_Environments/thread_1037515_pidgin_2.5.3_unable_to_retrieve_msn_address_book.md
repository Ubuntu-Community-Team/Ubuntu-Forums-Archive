---
title: "pidgin 2.5.3 unable to retrieve msn address book"
date: 2009-01-11
forum: Desktop Environments
---

### Post by d4v1dv00 on 2009-01-11
hi there,

the problem just happened as of today with the constant unable to connect via MSN of message: unable to retrieve msn address book

any help please?

thanks

---

### Post by adamlau on 2009-01-11
Received the same 2.5.3 error. Waiting it out is all I can suggest. Perhaps MSN is now using TLS, compiling with GnuTLS support may resolve the issue. Then again, it may not. A network, or protocol issue, or both are the likely culprits. A few more days and continued outage reports will give us a better idea of what occurred and what needs to be done to establish a connection proper.

---

### Post by jniebles on 2009-01-11
same problem here. i'm using version 2.5.2

---

### Post by Bios Element on 2009-01-11
Same problem. What a shock. The Empire of Microsoft has declared war again. >.>

---

### Post by DukeTech on 2009-01-11
Same here using 2.52. Interestingly, aMSN still works.

---

### Post by esc1 on 2009-01-11
Same issue. Was wondering if it was just going to be an issue of changing server and port...

---

### Post by DNvCross on 2009-01-11
well it's definitely not specific to Ubuntu.  My fedora 10 box just came down with this problem.

---

### Post by cooldudei06 on 2009-01-11
Also started getting this problem today, both on Pidgin 2.5.2 and 2.5.3. Can log in fine using Windows Live Messenger on Windows.

---

### Post by paranoid_humanoid on 2009-01-11
same issue, started a couple of hours ago. emesene works, but pidging not.

---

### Post by Dask8r on 2009-01-11
> **paranoid_humanoid said:**
> same issue, started a couple of hours ago. emesene works, but pidging not.

Yup Emesene works fine for me also.

---

### Post by d4v1dv00 on 2009-01-11
does this issue will haunting pidgin for ever? do we still wish to see this problem from time to time?

something must be done. but i dont have the qualification to point how.

---

### Post by dcrawl on 2009-01-11
This seems to be some kind of error between Pidgin and MSN as my Windows XP install, using 2.5.3, and 8.10 install, using 2.5.2 are both receiving the same error that everyone else is, hopefully it won't last too long, as I'd hate to have to switch away from Pidgin.

---

### Post by robertyou on 2009-01-11
same problem here LOL..
anyone has any idea if it's just temporary or not?

---

### Post by Delvien on 2009-01-11
My best guess is that Microsoft has found a way to block ApplicationId? again.

See: [http://developer.pidgin.im/ticket/6370](http://developer.pidgin.im/ticket/6370)

---

### Post by erickomoto on 2009-01-11
Apparently it is also affecting Adium users as I read in [Mac forums]("http://forums.mactalk.com.au/12/65221-msn-refusing-log-adium.html")

---

### Post by robertyou on 2009-01-12
> **Delvien said:**
> My best guess is that Microsoft has found a way to block ApplicationId? again.

See: [http://developer.pidgin.im/ticket/6370](http://developer.pidgin.im/ticket/6370)

darn.. that would be sad to be so

---

### Post by pinguino13 on 2009-01-12
Same problem here with pidgin 2.5.2. But empathy and emesene work fine.

---

### Post by Poleh on 2009-01-12
yup, confirmed same here on 8.10 x64 and Pidgin 2.5.2

---

### Post by chuuk on 2009-01-12
Yep, same problems here, was working fine until around 2300 GMT, got up this morning and poof. Kopete works fine by the by, if you're looking for an alternative till Pidgin's fixed.

---

### Post by watricky on 2009-01-12
> **Delvien said:**
> My best guess is that Microsoft has found a way to block ApplicationId? again.

See: [http://developer.pidgin.im/ticket/6370](http://developer.pidgin.im/ticket/6370)

Always a possibility - of course they wouldn't admit to that. :P

Better URL is here though: [http://developer.pidgin.im/ticket/8087](http://developer.pidgin.im/ticket/8087)

darkrain42: "No, it is a transient server-side problem that they will resolve at some point."

P.S. Same issue here, running Arch Linux 64 and some of my colleagues running Windows and other Distros (including Ubuntu) also with the same issue. The proprietary Windows Live Messenger seems to be running okay. :/

---

### Post by Sturmeh on 2009-01-12
Same issue here, most say just wait it out.

---

### Post by maggot_brain on 2009-01-12
For the mean time, I'd advise you all to switch to MSN Pecan.  It's an alternative MSN plugin for Pidgin and has less issues and can connect as well.

There is an old version in the repos, I'd recommend the latest version from the official site:

[http://code.google.com/p/msn-pecan/](http://code.google.com/p/msn-pecan/)

Just install it and choose 'WLM' as your protocol in Pidgin.  Adding MSN Pecan doesn't overwrite any of the official MSN support

---

### Post by formol on 2009-01-12
note : i'm connect now to msn with amsn 0.9.7 under ubuntu 8.04.

---

### Post by CloudFX on 2009-01-12
Hi,

I'm just now uploading msn-pecan 0.0.17 to my PPA, for those of you who want to install it, so you don't need to do so manually.  It's a quick build, and will soon be available at [https://edge.launchpad.net/~nick.ellery/+archive](https://edge.launchpad.net/~nick.ellery/+archive).  This will soon be officially uploaded to Ubuntu.

To install, add the following lines to your /etc/sources.list file:

```

deb http://ppa.launchpad.net/nick.ellery/ubuntu jaunty main
deb-src http://ppa.launchpad.net/nick.ellery/ubuntu jaunty main

```

Then enter:

```

$ sudo apt-get update
$ sudo apt-get install msn-pecan

```

The latest version, 0.0.17 will be installed, which fixes the issue at hand.

EDIT:  amd64 and i386 packages have been built in my ppa, and the above process can now be used as a workaround to this issue!

---

### Post by maggot_brain on 2009-01-12
The reason that MSN is not working is due to an issue with the latest version of the protocol MSN uses, MSNP15.  Apparently the official Microsoft client falls back to an older version of the protocol.  Also MSN Pecan uses an older version of the protocol which is why it's working too.  

So it's officially an issue with Microsoft's server.  Proof, if any were needed why proprietary IM protocols are crap and switching to Jabber / XMPP is a good idea.

---

### Post by adamlau on 2009-01-12
Unfortunately,all the contacts I know in Asia use MSN. I do not see that changing in the short term. That said, built and installed 2.5.3 with the only diff from my last build being:

```
--disable-msnp15
```

MSN address book retrieval is now working :) .

---

### Post by cristianrosa on 2009-01-12
Installing the package msn-pecan and modifying the account to use the WLM protocol did the trick for me.
By the way, I read in the homepage of the msn-pecan project that there are certain issues with the pidgin team, so they forked. What kind of issues?

---

### Post by adamlau on 2009-01-12
msn-pecan sounds interesting. Might give it a shot sometime. Disabling MSNP15 supports seems to be working out well, I'll keep this build up and running for now, see how it pans out for the next few weeks ...

---

### Post by pluckypigeon on 2009-01-12
It's probably a deliberate ploy to get Windows Pidgin users to use MSN Messenger and Linux users to use Windows. :-k

I don't blame them to be honest. Hotmail does belong to them =D>

Any Microsoft developer want to let us know what's going on?

---

### Post by adamlau on 2009-01-12
For some odd reason, I trust that Microsoft is currently either improving, or optimizing MSNP15 and the architecture which supports it.

---

### Post by linuxaz on 2009-01-12
Hello,
I had the same issue here with 8.10 and Pidgin.
I installed the Pecan plugin using Synaptic, and changed my account protocol to use WLM.  It now works.

bertman

---

### Post by pluckypigeon on 2009-01-12
> **adamlau said:**
> For some odd reason, I trust that Microsoft is currently either improving, or optimizing MSNP15 and the architecture which supports it.

Exciting ;-)

---

### Post by gurak2005 on 2009-01-12
it works with the pelcan plugin but some contacts are duplicated

---

### Post by SaiHayashi on 2009-01-12
been running emesene since this afternoon and now its down too...
curse on ms

---

### Post by pluckypigeon on 2009-01-12
> **SaiHayashi said:**
> been running emesene since this afternoon and now its down too...
curse on ms

I just tested it and emesene works fine for me.

> **linuxaz said:**
> Hello,
I had the same issue here with 8.10 and Pidgin.
I installed the Pecan plugin using Synaptic, and changed my account protocol to use WLM.  It now works.

bertman


Pecan did **NOT** solve the pidgin problem for me.:-)

Ahwel.:-\"

---

### Post by SaiHayashi on 2009-01-12
> **pluckypigeon said:**
> I just tested it and emesene works fine for me.

i was rejected for 3 hrs i dont know why... but yea it does work now


> **pluckypigeon said:**
> Pecan did **NOT** solve the pidgin problem for me.:-)

Ahwel.:-\"

me neither, added repository for intrepid and it installed 1.16, used repository for jaunty and it complains i dont have latest libpurple0 and perl, which i cant update from the manager

---

### Post by bekind2thenoob on 2009-01-12
Just adding my two cents. Ubuntu 8.10 and Pidgin 2.5.2 unable to connect to my msn account

---

### Post by sco on 2009-01-12
> **SaiHayashi said:**
> i was rejected for 3 hrs i dont know why... but yea it does work now




me neither, added repository for intrepid and it installed 1.16, used repository for jaunty and it complains i dont have latest libpurple0 and perl, which i cant update from the manager
it works for me. You need to change your MSN account settings from MSN protocol to WLM protocol in order to use the pecan plugin.

---

### Post by earthpigg on 2009-01-12
> **sco said:**
> it works for me. You need to change your MSN account settings from MSN protocol to WLM protocol in order to use the pecan plugin.

confirmed that this works. pecan is in the synaptic.

---

### Post by mcduck on 2009-01-12
> **adamlau said:**
> For some odd reason, I trust that Microsoft is currently either improving, or optimizing MSNP15 and the architecture which supports it.

Actually I'm quite sure that they just have some setting that they keep on switching backwards and forwards every couple of months to annoy everybody who's using something else than their own client.. :D

---

### Post by garg on 2009-01-12
I don't see the WLM option in protocols after I install pecan 0.16. I have 2.5.3 compiled from source. :(

Edit: I installed msn-pecan from source too to get it to work. 
Instructions:[http://ubuntuforums.org/showthread.php?t=831339](http://ubuntuforums.org/showthread.php?t=831339)

---

### Post by SomeGuyDude on 2009-01-12
On Arch with Pidgin. The msn-pecan plugin works flawlessly, it's in the AUR.

---

### Post by paranoid_humanoid on 2009-01-12
pecan worked for me too. this is pretty cool! how come i never knew about it before!

---

### Post by gpowers on 2009-01-12
The msn-pecan is 0.16-1, available through the repository. It installs without a hitch, and is visible when you restart Pidgin. Unless I'm forfeiting some functionality with which I'm unaware, I'll probably just leave it WLM until it breaks, again. Readable package notes, below.

Ubuntu 8.10
Pidgin 2.5.2

----
Package: msn-pecan
Priority: extra
Section: universe/net
Installed-Size: 416
Maintainer: Devid Antonio Filoni <d.filoni@ubuntu.com>
Architecture: i386
Version: 0.0.16-1
Replaces: pidgin-msn-pecan
Depends: libc6 (>= 2.4), libglib2.0-0 (>= 2.16.0), libpurple0 (>= 1:2.5.1-0ubuntu1)
Filename: pool/universe/m/msn-pecan/msn-pecan_0.0.16-1_i386.deb
Size: 115708
MD5sum: bcb593a61008cd5e97532bfa4668c64e
SHA1: 4d9efd139a40be015271c910c9800fe197b2d74b
SHA256: e7d0e56a1e900bd90d7d4c92012eb1b7dd90ef80d8825f9c640d068f21b7f499
Description: Alternative MSN protocol plugin for libpurple
 This is an alternative implementation of the MSN protocol plugin for libpurple.
 .
 It's based on the code from 2.2.2 plus a few extras.
 .
 Features include:
  * Support for personal messages
  * Support for offline messaging (read-only)
  * Support for handwritten messages (read-only)
  * Server-side storage for display names (private alias)
  * Partial direct connection support (p2p transfers)
  * Improved network IO (using GIOChannel)
  * Improved error handling
  * Network issues tested with netem
  * GObject usage
Homepage: [http://code.google.com/p/msn-pecan/](http://code.google.com/p/msn-pecan/)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by robertyou on 2009-01-12
wow thanks mate.

---

### Post by robertyou on 2009-01-12
> **pluckypigeon said:**
> I just tested it and emesene works fine for me.




Pecan did **NOT** solve the pidgin problem for me.:-)

Ahwel.:-\"

You might want to check your password..
pecan wouldn't let me sign in with my uber long password ](*,)

I signed in after changing my password shorter

---

### Post by Bonger1901 on 2009-01-12
msn-pecan worked at first, but now all my contacts appear as offline in pidgin.. and emesene doesn't even show any of my contacts.

---

### Post by abh83 on 2009-01-12
The best thing to do is to wait it out. Until then use the following:

msn web messenger: [http://webmessenger.msn.com/](http://webmessenger.msn.com/)
eBuddy: [http://www.ebuddy.com/](http://www.ebuddy.com/) 

or use the following apps found in the repos:

Emesene
aMSN

:)

---

### Post by jordilin on 2009-01-12
I got the same problem, Pidgin unable to connect. I'm using amsn.

---

### Post by pluckypigeon on 2009-01-12
It's fixed now. I think Microsoft sorted the problem.

---

### Post by etlpkby on 2009-01-12
> **pluckypigeon said:**
> It's fixed now. I think Microsoft sorted the problem.

Confirmed!

Now working with 2.5.2 here (8.10 Ibex on x86_64 AMD64 chipset)

):P

---

### Post by paranoid_humanoid on 2009-01-12
This was posted on the pidgin blog about an hour ago:

> Since last evening, we've had an influx of users into #pidgin, trac, and the support mailing list because they're not able to connect to MSN. Initially, we thought this was a server-side issue, because the error message we receive from the server makes it look that way. However, we've come to find that it is actually a minor protocol change in which the server now expects us to send a piece of data we don't send. We are working on a solution. There is no need to send further mail to the support list, open new tickets, or pour into #pidgin.

Again, we know what the problem is and are working to fix it.

[http://theflamingbanker.blogspot.com/2009/01/msn-issues.html](http://theflamingbanker.blogspot.com/2009/01/msn-issues.html)

---

### Post by Bonger1901 on 2009-01-12
Yep it's fixed now!

---

### Post by ShawnMichael on 2009-01-12
Emessene does not have any of my contacts on the list.  Although they are still able to send me messages.  But still I cannot see them on my contact list.  Blah.  

But at least Emessne works on here.  Ive tried amsn and it wont load on my computer.  I tried few others and they dont work on Ubuntu.  So I dont know.  I guess I'll wait it out till then.

---

### Post by miltosk on 2009-01-12
sudo apt-get update
sudo apt-get install msn-pecan

then change service protocol from msn to wlm

thats all!

---

### Post by etlpkby on 2009-01-12
> **miltosk said:**
> sudo apt-get update
sudo apt-get install msn-pecan

then change service protocol from msn to wlm

thats all!

As a ***workaround***, yes.
But the original protocol should be (and has been) fixed.

---

### Post by ShawnMichael on 2009-01-12
how do I change the protocol?

---

### Post by esc1 on 2009-01-12
Working for me again as well.

---

### Post by chuuk on 2009-01-12
Can confirm as well, fixed.

---

### Post by ShawnMichael on 2009-01-12
Pidgin's working now but Emesene still dont work for me.  I still cant add buddies or my contact list is blank.  Oh well

---

