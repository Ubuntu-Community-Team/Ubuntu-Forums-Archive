---
title: "Coupon Printer"
date: 2009-03-25
forum: General Help
---

### Post by yedidyah on 2009-03-25
I am using Hardy Heron Kubuntu

I have installed Wine and got Mozilla Firefox working.

I have also tried to install IE 6 to get the activex in Wine. I have NOT been able to use IE (I don't even know how to execute it). 

Using Firefox I went to the following address:
[http://print.coupons.com/CouponWeb/Offers.aspx?pid=13306&zid=iq37&nid=10](http://print.coupons.com/CouponWeb/Offers.aspx?pid=13306&zid=iq37&nid=10)

I selected a coupon and clicked on "print coupons"

The next page:
[http://print.coupons.com/CouponWeb/Install.aspx?pid=13306&zid=iq37&nid=10&pt=tmEGlUdPGT115214512083](http://print.coupons.com/CouponWeb/Install.aspx?pid=13306&zid=iq37&nid=10&pt=tmEGlUdPGT115214512083)

I clicked on Install coupon printer downloaded it and started installing it.

The license agreement comes up but there is no words within the window but there is a radio button to agree or disagree. I clicked on agree.

Wine then wants to install Gecko and clicked on okay.


Then the program puts up a notice:
Failed to register COM (ActiveX) control: C:\windows\CouponPrinter.ocx
Failure in LoadLibrary() (126)

This is what I have ran into time and again.

This time while writing this I opened another firefox window within wine to find the web page references for you to see what I am talking about.

I stopped to think and forgot to start again and couldn't find the original firefox window (which was behind the new window). BUT because of this I tried to install the software again and this time it didn't have the failure message and appeared to install. 

So I went back to the original page and clicked a coupon and tried to print it. It said: "Your coupons are printing we thank you for your patience. Sending coupons to printer... This process may take a few moments. But so far has done nothing.

Nothing was accomplished. I noticed at the end of one of the problem pages that coupons.com works with Internet Explorer, Netscape and AOL.

MY OPINION:
I think the key is to get IE working in Wine or to get some type of activex working with firefox.

IE4Linux cannot work because it works in Linux. The coupon printer works with Windows OS and therefore NEEDS Wine.

I know there are a lot of political issues with this situation: "Write to coupons dot com and ask them why they are prejudiced to linux (I will but that isn't going to help me anytime soon)" "Why ruin linux with IE? (I would LOVE to flee Monopolysoft)" "Why download a coupon printer? what kind of maleware must it have? (they use the software to keep you from downloading too many of the same coupons)"

I am trying to completely migrate to linux and I MUST have this work for my wife or she will be FORCED to return to Monopolysoft. And I AM SICK of the almighty Monopolysoft.

I want to thank you ahead of time for your thoughtful replies.

---

### Post by pytheas22 on 2009-03-25
The .exe installer from Microsoft's website for IE won't work unless you manually hack a lot of things, but if you use the installer from [ies4linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page"), you should have no problems (ies4linux takes care of the tweaking for you).  When it's installed, you can launch it from the Applications>wine menu (and I think possibly also from Applications>Internet).

If this site requires you to use an additional non-browser-based application for printing your coupons, however, and the application won't work well in wine, you might be out of luck.  You could try playing with different settings in wine to see if it makes a difference (for example, set wine to emulate Windows 2000 instead of XP), but there's no guarantee that that would solve the problem.

If you can't get the application to run in wine, you can still always [install Windows in a virtual machine]("http://maketecheasier.com/how-to-install-windows-in-ubuntu-hardy-with-virtualbox/2008/07/02"), then use your virtualized Windows system to print the coupons.

If you have more questions, just ask.

---

### Post by yedidyah on 2009-03-28
Thank you for your help.

I installed my virtual box and set up xp with comodo antivirus.
When I started to install the coupon printer from coupons.com comodo warned the coupon printer was trying to put a virus on my computer so I did a little more homework before installing. 

Coupons.com and Truste are using very deceptive tactics to put serious spyware on people's computers here are the articles:

[http://www.benedelman.org/news/031808-1.html](http://www.benedelman.org/news/031808-1.html)

[http://www.dslreports.com/forum/r20236965-Is-installing-a-Coupon-Printer-safe](http://www.dslreports.com/forum/r20236965-Is-installing-a-Coupon-Printer-safe)

So apart from these reports comodo is catching it as a virus. Therefore I HIGHLY recommend never doing business with these companies until they clean up their warez software.

---

### Post by pytheas22 on 2009-03-29
Yeah, obviously coupons.com is a sketchy site.  But you said in your first post that you didn't want a lecture on why you shouldn't use coupons.com :)

Anyway, I just wanted to point out that VirtualBox gives you the option to take 'snapshots' of your virtual machine's current state, and easily revert to them.  This means that you could do a fresh installation of Windows inside your virtual machine, then take a snapshot before installing the coupons.com malware (the machine needs to be powered off in order to take the snapshot).  This snapshot would represent your machine in a pure, uncompromised state.

After booting your virtual Windows system back up, installing the coupons.com stuff and doing what you need, shut Windows down again.  Before rebooting, tell VirtualBox to revert the image to the snapshot that you took previously (you can't revert while the virtual machine is running).  After reverting, your virtual machine will boot back into its clean state, as if the coupons.com stuff had never been installed, so that you don't have to worry about it spying on you or doing other nasty things.

Of course, a better solution would be refusing to use coupons.com based on its inappropriate policies.  But I wanted to point out the snapshot functionality of VirtualBox in case you weren't aware, because it can be particularly useful in situations like this where you need to use an application that you don't trust and can't uninstall cleanly, but don't want to have to wipe out the entire operating system just to get back to a clean state.

---

### Post by yedidyah on 2009-04-02
pytheas22,

For some reason I didn't get an email from the forums (or I over looked it) concerning this your response. I wish I had because I didn't take the snapshot of my Virtual Machine before I loaded the maleware on my VB.

Is there any precautions I should take to protect wine (or Linux) from from xp VB? The only thing I am sharing with VB is the printer and I have not set VB up on my Samba LAN all computers on the LAN are Linux.

---

### Post by pytheas22 on 2009-04-02
> I wish I had because I didn't take the snapshot of my Virtual Machine before I loaded the maleware on my VB.

You can always reinstall Windows in the VM, or create a new VM, if you like.

> Is there any precautions I should take to protect wine (or Linux) from from xp VB? The only thing I am sharing with VB is the printer and I have not set VB up on my Samba LAN all computers on the LAN are Linux.

Realistically, there's nothing to worry about.  The Windows guest operating system should not be able to do any harm to the Ubuntu host.  In principle it might be possible to exploit some weird bug and attack the host via the guest (there have been proof-of-concept demonstrations of this on VMware), but I've never heard of that happening with VirtualBox, and there's little incentive to the crackers to write an exploit like that (because there aren't too many people out there running Windows on an Ubuntu host in VirtualBox).  So there are really no precautions you need to take.

Also, for various reasons, Windows malware running in wine can't really do anything to Ubuntu (if it runs at all, which is unlikely because most of the Windows bugs that malware attempts to exploit are not implemented in wine), so there's no need to worry about that either.

---

