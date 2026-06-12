---
title: "Moving from Ubuntu to Fedora 9?"
date: 2008-05-13
forum: Fedora/RedHat and derivatives
---

### Post by quadomatic on 2008-05-13
Any advice for moving from Ubuntu to Fedora 9? I'm really pissed off about Ubuntu's consistent problems with wireless drivers. Hardy Heron has been the worst thus far.

---

### Post by Antman on 2008-05-13
> **quadomatic said:**
> Any advice for moving from Ubuntu to Fedora 9? I'm really pissed off about Ubuntu's consistent problems with wireless drivers. Hardy Heron has been the worst thus far.
If you have a nvidia card and need 3d support, you may want to wait a little bit since nVidia hasn't created an updated driver that supports the Xserver 1.5 that Fedora 9 has. Other than that, F9 is great for me so far.

---

### Post by msutton86 on 2008-05-13
If you have nvidia definitely don't do it.  If you don't I say do it up!  I just installed fedora 9, and everything worked.  Literally.  Besides it just working the performance is 10x better.  It boots up in half the time ubuntu did, and all the programs load faster!  Fedora is not as n00b friendly though.  So be prepared to work a tad bit.  Man pages will be your friend.

---

### Post by igknighted on 2008-05-13
If you use broadcom, I would highly recommend it (again, except if you have an nvidia card).  For some reason the b43 and bcm43xx drivers in Ubuntu get terrible performance compared to what the b43 driver gets in Fedora, and you are correct, the gap seems to be widening.  b43 in Hardy is almost worthless, and my laptop spends 90% of its time within 20ft of the router.  In Fedora, by contrast (thats F9 back through F7 at least, thats as long as I've had this machine), the b43/bcm43xx have always worked almost on par with the windows drivers.  I've never had a complaint.

---

### Post by quadomatic on 2008-05-14
Thanks for the advice. I finished downloading f9 just now. I'm trying it out in VirtualBox real quick before I fully install it on my machine.

I use ATI so the nVidia issues shouldn't be a problem...though ATI comes with a whole bunch of problems in Linux.

---

### Post by shuttleworthwannabe on 2008-05-14
> **quadomatic said:**
> Thanks for the advice. I finished downloading f9 just now. I'm trying it out in VirtualBox real quick before I fully install it on my machine.

I use ATI so the nVidia issues shouldn't be a problem...though ATI comes with a whole bunch of problems in Linux.

Not to create more problems for you, but have you tried the new mandriva spring one 2008.1 GNOME; it really does the trick very well. Best Gnome based OS I have ever tried, IMO. Give it a try; ATI driver automagically installed and setup perfectly

---

### Post by agim on 2008-05-14
Checking out fedora 9 now. I am asking on their forums too, do you know how to look at their available packages. Something like synaptic?

---

### Post by mthei on 2008-05-14
If you're looking for something specific, you can use the command-line by typing "yum search *package-name*", or look in the "add/remove software" option in the menu. Usually it's under applications, but in F9, I believe it's under the administration menu. It looks similar to the "add/remove" menu in Ubuntu, but nowhere near as nice as Synaptic, but I think you can install Synaptic as well.

---

### Post by dca on 2008-05-16
The livna repo is slow, so I hope you weren't planning on installing any multimedia codecs or anything...

---

### Post by dca on 2008-05-16
> **agim said:**
> Checking out fedora 9 now. I am asking on their forums too, do you know how to look at their available packages. Something like synaptic?

'System -> Administration -> Add/Remove Software'
 
It closer resembles the add/remove in Ubuntu or more so Mandriva than Synaptic...

---

### Post by SunnyRabbiera on 2008-05-18
Well if ubuntu was bad fedora is probably no better, as normally its hardware detection is shabby.
Mandriva 2008.1 might be a good option though, the latest mandys have been rock solid.

---

### Post by karellen on 2008-05-18
you could also install yumex, a nice frontend for yum
" yum install yumex" ;)

---

### Post by Antman on 2008-05-18
> **SunnyRabbiera said:**
> Well if ubuntu was bad fedora is probably no better, as normally its hardware detection is shabby.
Mandriva 2008.1 might be a good option though, the latest mandys have been rock solid.
I'm curious, when was the last time you have used Fedora??

---

### Post by SunnyRabbiera on 2008-05-18
Fedora 7&8, if things have improved I would really like to know.
and please note I use the term "usually" not "all the time"

---

### Post by quadomatic on 2008-05-20
I tried Fedora and liked it...until I realized I couldn't install ATI drivers since ATI hadn't released drivers supporting the 2.6.25 kernel yet (which rly isn't Fedora's fault). Then I decided to change the resolution on my screen, and now it flickers and I can't change it back.

---

### Post by konungursvia on 2008-05-20
The wireless driver issue is a general Linux one, not directly ubuntu-related, I believe. It's one of the last few things we are learning to do as well as or better than the Windows people. Everything else, we do much better. 

As for Fedora, I don't want to rip it, but I tried it at Fedora 8, and found the package manager far far inferior to the debian-based distros. I couldn't stand not seeing the progress moving, and not seeing the estimated time, or number of packages, and the thing hung there for over 24 hours before completing. 

Just my two cents. I'll only be interested in Debian-based distros for now.

---

### Post by Antman on 2008-05-20
> **konungursvia said:**
> 
As for Fedora, I don't want to rip it, but I tried it at Fedora 8, and found the package manager far far inferior to the debian-based distros. I couldn't stand not seeing the progress moving, and not seeing the estimated time, or number of packages, and the thing hung there for over 24 hours before completing. I agree that F8 default gui for Yum (pirut) was BAD...
luckily Yumex came to the rescue. Also F9's default gui for yum is better than pirut, but I think yumex is still available for people that prefer it.

Personally, I use yum via commandline as I was so used to Sidux forcing me to use apt via the cli. ;)

---

### Post by shuttleworthwannabe on 2008-05-21
> **quadomatic said:**
> I tried Fedora and liked it...until I realized I couldn't install ATI drivers since ATI hadn't released drivers supporting the 2.6.25 kernel yet (which rly isn't Fedora's fault). Then I decided to change the resolution on my screen, and now it flickers and I can't change it back.

This is the primary reason why I keep away from bleeding edge distro's: gives me bleeding hemarrhoids!:lolflag:

Opensuse 11 beta 3 and Fedora 9 are no go zones for me as I also have ati card that is not yet supported; I beleive nvidea is also in the same position.

---

### Post by eagleton on 2008-05-21
One nice feature of Fedora is that you get infos on updated packages in Package Kit - what bugs were fixed, what new features are introduced. I haven't seen this in Synaptic yet.

---

### Post by igknighted on 2008-05-23
> **konungursvia said:**
> The wireless driver issue is a general Linux one, not directly ubuntu-related, I believe. It's one of the last few things we are learning to do as well as or better than the Windows people. Everything else, we do much better. 

As for Fedora, I don't want to rip it, but I tried it at Fedora 8, and found the package manager far far inferior to the debian-based distros. I couldn't stand not seeing the progress moving, and not seeing the estimated time, or number of packages, and the thing hung there for over 24 hours before completing. 

Just my two cents. I'll only be interested in Debian-based distros for now.

Nope, the wireless issues are specific to Ubuntu.  BCM43XX and B43 work perfectly with every distro I use (Mandriva, Fedora, OpenSuse, etc.) but are worthless only with Ubuntu.  They were OK (not great) in 7.10, but with Hardy they are worthless.  At least for my card.

As for the issues with "fedora's package manager", you are judging all RPM based distro's by one GUI to one distro's package manager.  And one that everyone who uses Fedora admits sucks and recommends better alternatives (read: yumex).  In fact, Fedora 9 uses packagekit which is likely to replace synaptic in Ubuntu, so heads up.  As for the time, remember that (a) there are deltaRPMs and other plugins that will greatly speed updates up, and (b) fedora updates _everything_, as it tries to stay bleeding edge.  So of course updates will take longer than Ubuntu.  Try using Debian Sid, updates will take far longer than ubuntu too, even tho it is debian.

---

### Post by RedDwarf on 2008-05-25
> **shuttleworthwannabe said:**
> Opensuse 11 beta 3 and Fedora 9 are no go zones for me as I also have ati card that is not yet supported; I beleive nvidea is also in the same position.
openSUSE has a great support. And I don't mean at their forums you always get an answer in 4 minutes max... I mean you get GOOD answers (and bugs get fixed and so...)

For nVidia...
[http://en.opensuse.org/Bugs:Most_Annoying_Bugs_11.0_dev](http://en.opensuse.org/Bugs:Most_Annoying_Bugs_11.0_dev)
> NVIDIA driver doesn't compile. Workaround: check here for a patch. No patching required if 173.08 Beta drivers are used.

For ATI:
[http://lists.opensuse.org/opensuse-factory/2008-05/msg00466.html](http://lists.opensuse.org/opensuse-factory/2008-05/msg00466.html)

So no problems at all with nVidia or ATI in Fedora 9. And since six days ago openSUSE Build Service added support for Fedora 9 you also have my great and untested (in Fedora) packages: [http://download.opensuse.org/repositories/home:/RedDwarf/Fedora_9/](http://download.opensuse.org/repositories/home:/RedDwarf/Fedora_9/) ;-)

---

### Post by shuttleworthwannabe on 2008-05-28
RedDwarf, not to be rude ofsorts, but the post you linked me up for ATI in OpenSuse 11 beta 3 does not have a workaround for installation of ATI-drivers. 

[Edit: I got to follow that thread, and it seems more complicated than I am used to; also found out that ATI just released a driver for the new kernels]. 

Somewher I read that the ATI-drivers do not work with the latest linux kernel 2.6.25.x
well I guess I will wait for the goldmaster version to com eout next month, and then try OpenSuse 11.
Oh, BTW, why does it not come with bullet-proof X like Ubuntu does: In ubuntu I did not even install the ati-drivers (i really do not need 3d rendering right  nwo) and everything just works fine off the x-server in ubuntu hardy.
thanks
S

---

### Post by fyrestrtr on 2008-05-29
Fedora 9 is great -- lots of cutting edge stuff. Personally I love the theme and the startup progress system -- I call it *system* because compared to the bar in Ubuntu, its a giant leap forward.

The fonts in Fedora are also better looking and render quite well on my laptop.

Why I switched back from Fedora to Ubuntu:

1. I simply cannot stand RPM/yum. The most archaic package system ever. I have used everything from Gentoo to FreeBSD to Debian. apt wins hands down (second is ports).

2. SELinux. Can't be bothered with it.

3. No support for my nvidia card. I don't need it for the desktop cube, but geez, the delay in scrolling firefox or large documents in OO killed me. Till that is done, I'm not going back.

There are some great point in Fedora:

1. Theme. Winner over the we-can't-pick-a-color-other-than-brown/orange that is Ubuntu; by the way, this also includes the cursor which is very slick.
2. Font rendering (as I mentioned)
3. Startup process
4. Network Manager supports GSM cards

Thankfully my system is well supported in Linux (Go IBM!) so I don't have problems with wireless and such.

---

### Post by Antman on 2008-05-30
> **fyrestrtr said:**
> 
Thankfully my system is well supported in Linux (Go IBM!) so I don't have problems with wireless and such.
+1 IBM Laptops rock.... :guitar:

---

