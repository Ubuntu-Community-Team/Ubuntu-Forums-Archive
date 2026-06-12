---
title: "Remove FireFox3 The worlds Slowest Browser"
date: 2009-06-15
forum: General Help
---

### Post by StGeorge on 2009-06-15
Hi all,
I use Firefox2, on my XP and 98se OS's, (as well as Opera, Safari, The World, Sea Monkey, K-Meleon to name but a few I use for Web Developement and Testing). 
The only two Browsers I completely ignore when it comes to Web Developement are I.E., (of course) and Firefox3. I have tried Firefox3 on XP and it is as slow as it is in Linux.

In my 9.04 I wish to remove the 'Worlds Slowest Browser' FireFox3 and replace it with something lighter that works.

I am concerned that it may have an effect on the gnome desktop environment if I get rid of it once and for all. Can anyone enlighten me as to it's importance to gnome if any.

I would also like to know if there are any suggestions as to a good light Linux Browser.

Thanks in advance.

---

### Post by lovinglinux on 2009-06-15
You could install [firefox-3.5](apt:firefox-3.5) [apt-get]. It is in the repositories and it is almost 200% faster than Firefox 3 according to my [Peacekeeper](http://service.futuremark.com/peacekeeper/index.action) benchmarks.

```
sudo apt-get install firefox-3.5
```

It is currently a Beta. It will install side-by-side with Firefox 3.0.11 and will make a copy of your profile to avoid conflicts.

---

### Post by Mirge on 2009-06-15
Firefox 3.5 was faster for me, but caused me way way more problems... freezing up (browser, not comp)... DNS issues, Flash issues.. wasn't worth it to me. That's the nature of a beta release though I suppose. I wish a stable would come out.

---

### Post by StGeorge on 2009-06-15
Problems with Websites seem to me to do with Flash and all the other rubbish people put into sites to make browsing a task and not the supplier of information and communication it was designed for.
Want constant advertising then switch on the telly.

To be honest I still think of 98se as the meanest, and fastest OS. That is why I gave up on FireFox as the version 3's no longer support 98se. It is still my working OS. I still like FireFox 2 though.

I really want FireFox out of my 9.04. It is a serious pain. Fortunately I am running 9.04 inside Portable Ubuntu so I can still use my Firfox2 from Windows while using Linux, (No dual booting here).

Problem is while I am converting this CoLinux image to a 9.04 Server I require Browsing within Linux to check and test Settings and Configuration.

The speed has nothing to do with CoLinux as it is just as slow in a Linux/Windows dual boot I have. In fact the CoLinux is a little faster. But still too slow for me.

The questions remain.

Will removing Firefox3 affect gnome?

What is a fast lite Linux Browser.

---

### Post by Greenwidth on 2009-06-15
> It is still my working OS.

You using 98 on the net? 
Bit of a security worry given they stopped support for it mid '06 isn't it?

---

### Post by t0p on 2009-06-15
> **StGeorge said:**
> Hi all,
I use Firefox2, on my XP and 98se OS's


98... wow... Do you use 98 to surf the internet much?  Do you get pwned much?

> **StGeorge said:**
> 
I would also like to know if there are any suggestions as to a good light Linux Browser.


Depends how light you want to go.  **Epiphany** ain't bad for a graphical browser.  But **lynx** and **w3m** are a lot faster, if graphics aren't important.

---

### Post by StGeorge on 2009-06-15
Never had a Virus.
Never get Spyware.
Get a few Firewall Alerts.
My 98se is mean, clean and twice as fast as my XP or Linux machines.
Beats a Mac on speed, (me and my mate tested it).

Only problem with it is junk web sites with glossy content trying to slow me down, with script and Flash content.

I just close the tab if that happens and blacklist the site.

I'm not a gamer, video junkie, IM'er or any type of interactive internet user.

No Problem, lol.

Thanks for the advice.

Will look at Epiphany, Lynx & w3m.

Still want to know if I can rid Firefox3 from Ubuntu 9.04. Won't be needing it.

---

### Post by Mirge on 2009-06-15
> **StGeorge said:**
> Never had a Virus.
Never get Spyware.
Get a few Firewall Alerts.
My 98se is mean, clean and twice as fast as my XP or Linux machines.
Beats a Mac on speed, (me and my mate tested it).

Only problem with it is junk web sites with glossy content trying to slow me down, with script and Flash content.

I just close the tab if that happens and blacklist the site.

I'm not a gamer, video junkie, IM'er or any type of interactive internet user.

No Problem, lol.

No offense, but that sounds like the most boring Internet experience ever :).

---

### Post by StGeorge on 2009-06-15
lol

yup

But I get things done.

---

### Post by Mirge on 2009-06-15
> **StGeorge said:**
> lol

yup

But I get things done.

At the end of the day, that's all that matters I suppose!

Since I use Firefox, I haven't really investigated the problems involved with removing it... but here's a thread I ran across while searching: [http://ubuntuforums.org/showthread.php?t=647627](http://ubuntuforums.org/showthread.php?t=647627)

---

### Post by StGeorge on 2009-06-15
Thanks Mirge,

Good Link.

---

### Post by Yellow Pasque on 2009-06-15
Unless you're low on disk space, you don't have to get rid of it. Just install and use something different. That said, you can uninstall Firefox. It will remove a few meta-packages, but this is harmless.

My thoughts on lightweight web browsers:
Epiphany - fast with the Webkit backend. Unfortunately, that's not available in the 9.04 repository (though I'm sure there are .deb's or PPA's for it).
Konqueror - awesome browser, but you have to install a bunch of KDE/Qt4 stuff to use it, and most GNOME users don't care for that.
Midori - the few times I've tried it, it hasn't been very stable
Opera - I haven't used it too much myself, but there are a lot of fans in these forums. I've also seen some people rave about Opera 10 beta being really fast.

---

### Post by egalvan on 2009-06-15
> **StGeorge said:**
> My 98se is mean, clean and twice as fast as my XP or Linux machines.

I'm not a gamer, video junkie, IM'er or any type of interactive internet user.



> **Mirge said:**
> No offense, but that sounds like the most boring Internet experience ever :).

No offense taken... :)
I am the same type of Internet user, and I've never been bored.

I read a lot, and I don't need fancy videos to get or keep my attention. ;)
Each cat his own rat, I always say.

As for W98SE, I used it up until last year...
a ruthlessly stripped-down version, courtesy of 98Lite.
A 60meg drive gave plenty of space.
Puppy has replaced it now for daily 'lite' use.


As for not wanting FireFox 3, why not just ignore it?
My Jaunty box is down for now (using the 8GB RAM to test another box)
so I can't test the un-install.

---

### Post by StGeorge on 2009-06-15
Epithany is not for what I am looking for.
The link on the previous page, although dated '07 states that Epithany will install Firefox and a Firefox remove will uninstall Epithany.

I have just installed it but did not bother to try it, I instantly removed it as it took so long to install.

I do use Opera in Windows for Website testing and it seriously fast as long as you get rid of Flash Plugins etc. So might give it a try.

So my choices to look at now are Lynx and Opera.

As for keeping it in without using it. The thing is I am creating a CoLinux Server with GUI, (from a Portable Ubuntu installation):

[http://portableubuntu.demonccc.cloudius.com.ar/](http://portableubuntu.demonccc.cloudius.com.ar/) 

The Browser will be left in with relevant bookmarks etc. Also this server will fit onto a 4gb Stick with extra ex3 images as plugin hdd's. The idea being that it can go with you. Space is important because when I have got an image I can pass around it needs to be stripped to the bare.

The 9.04 has in it:

MySQL
phpMyAdmin
PHP5
Apache2
Rkhunter
Binutils
Amavisd-new
SpamAssassin
Clamav
FCGI
suExec
Pear
mcrypt
PureFTPd
Quota
MyDNS
Vlogger
Webalizer
Jailkit
fail2ban
SquirrelMail
SSH Server
NTP
Postfix
Courier
Saslauthd
lamp
ISPConfig 3
Webmin

So I need a decent fast Browser for testing within local host while I finish configuration.

Of to try Lynx 1st:

---

### Post by Yellow Pasque on 2009-06-15
> I have just installed it but did not bother to try it, I instantly removed it as it took so long to install.

It took a long time to install, so you didn't try it? LOL
Again, don't bother with the Epiphany in the 9.04 repo. It uses the mozilla/gecko backend, and the Epiphany team is dropping support for that backend. Try Epiphany with a Webkit backend, like [https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)

---

### Post by blackhawks_fan on 2009-06-15
> **StGeorge said:**
> Never had a Virus.
Never get Spyware.
Get a few Firewall Alerts.
My 98se is mean, clean and twice as fast as my XP or Linux machines.
Beats a Mac on speed, (me and my mate tested it).

Only problem with it is junk web sites with glossy content trying to slow me down, with script and Flash content.

I just close the tab if that happens and blacklist the site.

I'm not a gamer, video junkie, IM'er or any type of interactive internet user.

No Problem, lol.

Thanks for the advice.

Will look at Epiphany, Lynx & w3m.

Still want to know if I can rid Firefox3 from Ubuntu 9.04. Won't be needing it.
Sounds like my internet usage.  I thought I was the only person online that wasn't hooked on IM and social networking.  There is so much on the web besides that junk.  I have however updated my OS through the years.  Commodore 64 w/9600 baud MODEM, WIN 95, NT(both w/dial-up), WIN 2K (the best MS OS IMO), XP, Vista (CRAP!) and now Ubuntu(All w/cable).  Actually Vista is why I have dumped MS altogether I just couldn't put it up with it anymore.  I had been wanting to try Linux again for sometime, I had read a lot about Ubuntu and one weekend just took the plunge.

---

### Post by StGeorge on 2009-06-15
Might look at Epiphany again then. Didn't get into the menu after install so thought what the heck quicker to uninstall it than configure it. Besides I read it was Gecko related while it was being installed.

However I installed 4 Browsers after uninstalling the Epiphany Gecko in under half the time and with 2/3 the MB, yes all 4 under 1 Gecko install.

Arora- Slow but much quicker than FireFox (accepts certificates). So will keep it for Webmin only.

Conkeror- Slow also and I didn't like the look of it.

Galeon-Requires Mozilla, (probably why it did not need all the Mb). Twice as fast as FireFox. Will Uninstall anyway as it is Gecko.

Midori- Fastest of them all, but doesn't accept certificates or import bookmarks, (probably requires plugins). Has a strange blurring behaviour when scrolling. Keep it for now as it is fast. (Webkit Backend).

Those four installed quick and small.

Tried links2, too plain but very quick.

Installed Lynx but it did not get into the Menu so I unistalled it straight after a reboot. No time to hang about configuring Menus and Browsers.

So FireFox goes after tonights backup. Loaded three browsers at once and together they loaded faster than FireFox3 on it's own. What have FireFox done to destroy a great browser?

Still keep my FireFox2 though, have to it's not easy to export 200+ Passwords to another Browser. Besides I still rate it.

As for OS's I cannot understand why anyone would contemplate Windows after the admission of a complete cock up over Vista the most overbloated useless piece of garbage on the Planet. Microsoft must think that we all have time to waste trying out their products only to be told the new release will sort the problems out.

I have only been using XP for a couple of years but still find my 10gb drive with 120 apps and 98se on a 192RAM, pentium III taking up only 6GB in total quicker than any XP or Vista requiring alot more resources.

Ubuntu is fine though. I am still getting used to the command line though. Still using the Terminal to install and uninstall is great. It is all the configuration in Terminal that I have trouble getting my head round at times.

---

### Post by bodhi.zazen on 2009-06-15
> **lovinglinux said:**
> You could install [firefox-3.5]("apt:firefox-3.5") [apt-get]. It is in the repositories and it is almost 200% faster than Firefox 3 according to my [Peacekeeper]("http://service.futuremark.com/peacekeeper/index.action") benchmarks.

```
sudo apt-get install firefox-3.5
```It is currently a Beta. It will install side-by-side with Firefox 3.0.11 and will make a copy of your profile to avoid conflicts.

+1

The new firefox is noticeably faster both on Windows and Fedora (it is default on Fedora 11).

Have not tried it on Ubuntu.

Although it is beta, I have had no problems using it (going on 2 weeks now).

I would also suggest you not remove firefox, no need to really. This is not Windows, lol.

I suggest dillo, I think dillo would be perfect for what you are wanting to do. You may need to patch it for tabbed browsing.

---

### Post by StGeorge on 2009-06-16
Once Positive result.

Removed FireFox and the whole installation speeded up by about 25%.
Strange but I now have 4 Browsers where before I only had one. System going like a train.

Also removed ubuntu-docs, (when was the last time I ever got what I was looking for in Help Files?). Since that removal the system seems to boot quicker.

Just About GNOME to rid myself of next, (why would I want to know about it,I just want it to work).

Kept the 4 Below for now.
Arora.
Dillo.
NetSurf Web Browser.
Midori.

Getting Rid of Firefox has speeded up the Arora Browser too.

Dillo is the fastest but it is Text Based and Keyboard orientated.

Midori is nearly as fast as Dillo and is graphical, but is so fast the scrolling behaviour is blurred.

NetSurf is useful for Web Developement as it shows up flaws in Web Design instantly.

Anyway there's my little review of it all.

Conclusion.

Bin FireFox3 it is Slow, Resource Hungry and Completely unnecessary.

---

### Post by bodhi.zazen on 2009-06-16
If you want a minimal system is it much easier to start with a minimal install and build up then it is to start with a desktop and remove gnome.

That your system runs faster simply because you removed firefox makes no sense on Linux. I believer other browsers are faster, although as has been stated, FF 3.5 pre-release is quite fast.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by lukeiamyourfather on 2009-06-16
> **StGeorge said:**
> To be honest I still think of 98se as the meanest, and fastest OS.

Dude, what are you smoking? The answer is no, removing the browser won't mess up GNOME (its not Windows!). I think the root of the issue is not Firefox though, sounds like you need to upgrade your decade old computer so it won't choke on Flash content.

---

### Post by raminaghrobis on 2009-06-27
Hi, I'm also looking for another browser than firefox. Are there any safety issues with epiphany, opera or midori? Or does it not matter which browser you're using?

---

