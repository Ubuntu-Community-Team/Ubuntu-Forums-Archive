---
title: "Why I don't use Ubuntu"
date: 2005-03-23
forum: Desktop Environments
---

### Post by gnosis on 2005-03-23
Having installed ubuntu about 5-6 times and each time not being able to upgrade Firefox to a currect version that actually works.  What is up with 0.9.3? that one is long dead and doesn't even load pages anymore.  Tried to hijack 1.0.1 from debian with same results, I had to Ubunttheass and reinstall a distro that truly works, Debian.  Bye bye, hope you get stuff fixed and good luck.

gnosis

---

### Post by wylfing on 2005-03-23
What is so hard about downloading and installing directly from the mozilla.org web site? Or what's so hard about grabbing the warty backport version? Or what's so hard about installing hoary instead of warty?

There are really a lot of different ways to handle this. Perhaps you would do better to ask for advice rather than make disparaging remarks.

---

### Post by gnosis on 2005-03-23
What is so hard about including a working version in a "supported" distro?

gnosis

---

### Post by valadil on 2005-03-23
Nothing hard about including a working version.  It just takes time.  You wouldn't want them to release a new version of something the day it came out just to have to release more updates if something went wrong.  If you care that much about having the highest version numbers on all your programs, then compile those programs yourself the day they come out or just find an unofficial repo for the impatient.

Much as I love Debian it's going to be even slower about getting you the newest version of apps.

---

### Post by george29 on 2005-03-23
I know nothing about Linux and i've still managed to follow a How to guide and update firefox.  and the version that was on the cd image i burnt and installed from worked. (I'm using Warty 4.1)
as wylfing said why not ask? and at the same time use google and read some of the how to's that people take the time and effort to write to help people (like myself) make the move to a new distro (or as in my case from windows to linux) easier.

Personally i think it's great, I'm still learning how to do things, but given time i think the dual boot that i'm using with XP will probably disappear completely.

I don't expect to know everything straight away or for things to work without a hitch they never have done in windows either! but at least in linux with a small amount of effort on my part, and some help from those who know more than me, i can fix things and feel that i'm learning something as i go along, and then in turn help others - after all isn't that part of the UBUNTU ethos? (in some convoluted fashion  :smile: )

George

---

### Post by gw90se on 2005-03-23
Why make your first post a good-bye one instead of asking some of these fine folk for help? 

This is my first true Linux experience and I figured out how to upgrade my Firefox in the first night. Good How-to' and good online help make the difference.

---

### Post by gnosis on 2005-03-23
So why isn't this included in the security updates?

These are the security fixes since 0.9.3:

Fixed in 0.10.0 (aka PR)

86  	 Malicious POP3 server III (245066, 226669)  	critical / moderate  	remote execution  	 Responses from a malicious POP3 mail server can trigger heap overruns that can be exploited to run arbitrary code.  	Gael Delalleau  	2004-08-17

87  	 non-ascii hostname heap overrun (256316)  	critical / high  	remote execution  	 A link with a non-ascii hostname can cause a heap buffer overrun that could potentially be exploited to run arbitrary programs.  	Mats Palmgren, Gael Delalleau  	2004-08-24

88  	 javascript: link dragging (250862)  	critical / moderate  	cross-domain scripting, possibly remote execution  	 javascript; links dragged onto another frame or page allows an attacker to steal or modify sensitive information from other sites. The user could be convinced to drag obscurred links in the context of a game or even a fake scrollbar. If the user could be convinced to drag two links in sequence into a separate window (not frame) the attacker would be able to run arbitrary programs.  	Jesse Ruderman  	2004-08-26

89  	 BMP integer overflow (255067)  	critical / high  	heap overrun  	 extremely wide BMP images trigger an integer overflow, leading to heap overruns that are potentially exploitable to run arbitrary code. Workaround: Disable images.  	Gael Delalleau  	2004-08-27

90  	 Buffer overflow when displaying VCard (257314)  	critical / high  	remote execution  	 A stack buffer overrun in VCard display routines could be exploited to run arbitrary code supplied by the attacker. Workaround: Disable in-line display of attachments, don't open VCard attachments.  	Georgi Guninski  	2004-08-30

93  	 "Send page" heap overrun (258005)  	critical / moderate  	remote execution  	 The "send page" function can overrun the heap on very long links. With compelling content that people will want to forward to all their friends and the right link this could be used to execute arbitrary code.  	Georgi Guninski  	2004-09-07

Fixed in 0.10.1

94  	Downloading link deletes files  	high / high  	dataloss  	 Firefox simplifies the task of saving files by automatically using a filename based on the original link. A specific link format triggers a bug in this feature and can cause the deletion of files in the download directory. An attacker would need to convince a victim to click the "Save" button to download a file from their site.
Workaround: Cancel unexpected file save prompts and any from untrusted sites. When saving files, right-click on the link and select "Save link as" from the context menu. 	Alex Vincent 	2004-09-29

Fixed in 1.0

MFSA 2005-05  Input stealing from other tabs
MFSA 2005-07  Script-generated event can download content without prompting
MFSA 2005-09  Browser responds to proxy auth request from non-proxy ssl server
MFSA 2005-12  javascript: Livefeed bookmarks can steal private data

Fixed in 1.0.1

MFSA 2005-21  Overwrite arbitrary files downloading .lnk twice
MFSA 2005-26  Cross-site scripting by dropping javascript: link on tab
MFSA 2005-27  Plugins can be used to load privileged content
MFSA 2005-28  Unsafe /tmp/plugtmp directory exploitable to erase user's files
MFSA 2005-29  Internationalized Domain Name (IDN) homograph spoofing

I'm sorry, but this is not acceptable if you claim to have a "supported" version.  Firefox is the default web-browser in Ubuntu and you are 5 versions behind on security updates if you include the 1.0.2 that just came out.  Sure you can fiddle and tweak stuff to jerry-rig it to work, but why when the distro this enhances already has the updates and they work flawlessly.

I might come across coarsley, but someone gotta say this.  You want to have a "supported" distro with "security updates for 18 months" one might expect the default browser to at least have an update to PR or perhaps even the release 1.0.

gnosis

---

### Post by Buffalo Soldier on 2005-03-23
A person that's either never heard or doesn't understand the quote "*a whole that is greater than the sum of its parts*".

Sometimes yes, by having the all the best components you'll have the best system.

But most of the time you have to build using component that is not the best and greatest on it's own.. but component that works well with others to create the best system.

And that (best system) also is different from each and every person.

Just because what you're looking for in the a distro is the latest FireFox, doesn't mean Ubuntu doesn't work for others.

I mean it's allright by me if you were to come in here asking how to get the latest FireFox, get your answer, then you're still unsatisfied, and just professionally say this is not what you're looking for and leave nicely.

But what you did was like trying to get on people's nerve.

Anyway, thanks for giving Ubuntu a try. Sorry it didn't work out for you. I'm sure you will find what you're looking for elsewhere. Bye.

---

### Post by gnosis on 2005-03-23
Is it really too much to ask for a working version of the default browser?  It is afterall probably the most used piece of software on any computer other than the kernel and supporting software.  If all you can come back with is knee-jerk defense of your distro and not seeing it objective there is yet another reason not to use Ubuntu.  So is it too much to ask, a web browser that loads a web page? Should a new user of Ubunto have to wade through how-to's and usergroups to get their default install to work?  Is this what is expected?  I can understand if you need Obscure V0.82.5Beta2.5 to work, but the default web browser, come on?

gnosis

---

### Post by lordofkhemenu on 2005-03-23
[QUOTE=gnosis]Is it really too much to ask for a working version of the default browser? It is afterall probably the most used piece of software on any computer other than the kernel and supporting software. If all you can come back with is knee-jerk defense of your distro and not seeing it objective there is yet another reason not to use Ubuntu. So is it too much to ask, a web browser that loads a web page? Should a new user of Ubunto have to wade through how-to's and usergroups to get their default install to work? Is this what is expected? I can understand if you need Obscure V0.82.5Beta2.5 to work, but the default web browser, come on?

gnosis[/QUOTE]
/me grows tired of gnosis and slips in to [Artie Lange mode]...
Waaah, I want Linux to do everything for me, waaah. I don't want to have to learn to read and do things for myself...waaaah.[/Artie Lange mode]
*Knee- jerk reaction*? Dude, go back and look at your first post and your subsequent responses to those who tried to help you *despite* your pissant attitude...

---

### Post by Buffalo Soldier on 2005-03-23
[QUOTE=gnosis]... If all you can come back with is **knee-jerk** defense of your distro and not seeing it objective there is yet another reason not to use Ubuntu.  So is it too much to ask, **a web browser that loads a web page?**...[/QUOTE]
[list]
[*] **knee-jerk** - ahem :) hello... first post
[*] **a web browser that loads a web page?** - it's not version 1.x but it can load a webpage
[/list]
No developer would want to distribute crappy distribution. I'm sure they tried their best to incorporate it. If it ain't there... please believe it wasn't intentionally to screw users.

Been using Warty since november 2004 till a few weeks ago. FireFox 0.9 served me well.

Suggestion:[list=a]
[*] Keep using 0.9
[*] If on Warty use backport
[*] Upgrade to Hoary-Preview
[*] Leave gracefully
[/list]
But instead you've decided to leave ungracefully.

---

### Post by Buffalo Soldier on 2005-03-23
[QUOTE=gnosis]Having installed ubuntu about 5-6 times and each time not being able to upgrade Firefox to a currect version that actually works.  What is up with 0.9.3? that one is long dead and **doesn't even load pages anymore**.  Tried to hijack 1.0.1 from debian with same results, I had to Ubunttheass and reinstall a distro that truly works, Debian.  Bye bye, hope you get stuff fixed and good luck.

gnosis[/QUOTE]It doesn't load webpages? Meaning it fails to load a website? Only gives you blank empty pages? Are you sure you've setup your network settings?

---

### Post by Buffalo Soldier on 2005-03-23
[QUOTE=gnosis]What is so hard about including a working version in a "supported" distro?

gnosis[/QUOTE]What do you mean by a working version? Version 0.9x doesn't work? It doesn't load any pages for you?

---

### Post by corefile on 2005-03-23
I don't agree with his tone, nor do I agree with his choice of words; However if in fact ( cause I've never installed warty) Firefox is broken AND if this is the default browser then that is an issue that can not be blown off with "read a howto, or use backports". I really like Ubuntu Hoary so far, and that is why I hope that the developers take an app being broken that is one of the most used for a desktop distro and that is the default one at that a little more serious then "read a howto". We should be able to expect that one of the most widely used default apps would at least work. And I don't mean it will work if you make it, it should just work period. There is a certian amount of quality that I would at least hope we can agree on. Regardless of gnosis'  poor way of expressing it.

---

### Post by DJ_Max on 2005-03-23
I find it amusing you took the time to install Ubuntu so many times, but never bothered to click the link on these forums.
[http://backports.ubuntuforums.org](http://backports.ubuntuforums.org)

You should fine an updated firefox version since you don't wanna install it the normal way(i.e [www.mozilla.org/](www.mozilla.org/) )

BTW, re-installing an OS will NOT make a .deb package magicly appear in the repository.

---

### Post by gnosis on 2005-03-23
[QUOTE=Buffalo Soldier]It doesn't load webpages? Meaning it fails to load a website? Only gives you blank empty pages? Are you sure you've setup your network settings?[/QUOTE]

Yes, it just spins forever.  Lynx works like a charm as does links, wget, ping and a number of other web applications.  Same issue I've had on two different computers with 0.9.3 using Knoppix, upgrading worked on that distro, but like lordofkhemenu artfully stated on his homepage "Team Ubuntu's efforts to make Ubuntu just plain work...." it doesn't seem to fit the philosophy of Ubuntu.  Don't get me wrong, I'd love to see a linux distro actually make that philosopy happen, perhaps with Hoary it will take another step, but so far Ubuntu is not there.  I've brought this up on the Ubunto forum cause it should be a concern of theirs.  Corefile I give you credit for actually looking at the problem instead of focusing on my more or less skilled words of conveying it.

Sincerely

gnosis

---

### Post by carlc on 2005-03-23
=; I am using firefox 1.0 in warty and it works fine.

---

### Post by corefile on 2005-03-23
I find it amazing that you all are completly ok that the default web browser is broken.  I mean come on, do we really want to have some of the most used apps broken? And the answer is that you have to install something from an unsupported repository. We are not talking about some off the wall seldom used app, we are talking about the default browser, are we really saying its ok for it to be broke and you just gotta RTFM.

---

### Post by Buffalo Soldier on 2005-03-23
[QUOTE=corefile]I don't agree with his tone, nor do I agree with his choice of words; However if in fact ( cause I've never installed warty) Firefox is broken AND if this is the default browser then that is an issue that can not be blown off with "read a howto, or use backports". I really like Ubuntu Hoary so far, and that is why I hope that the developers take an app being broken that is one of the most used for a desktop distro and that is the default one at that a little more serious then "read a howto". We should be able to expect that one of the most widely used default apps would at least work. And I don't mean it will work if you make it, it should just work period. There is a certian amount of quality that I would at least hope we can agree on. Regardless of gnosis'  poor way of expressing it.[/QUOTE]It would be easier if this post started this way :)

First, the default version of FireFox in Warty 4.10 is not broken, insecure nor unstable.

The developers reverted back to 0.9 when FireFox 1.0PR came out.[list]
[*] Why? It was the best solution **at that time**.
[*] What was wrong with 1.0PR at that time? I don't remember the details. But here's what I manage to find now: [http://people.ubuntulinux.org/~mako/ubuntu-traffic/u20041015_08.html#4](http://people.ubuntulinux.org/~mako/ubuntu-traffic/u20041015_08.html#4)
[*] Why didn't they upgrade when the official version of 1.0 was released? I guess that would start breaking things.
[*] Were we vulnerable to all the holes and bugs while running 0.9 when newer version are available? Nope. The version used continue to receive fixes and patches from ubuntu security. As long as you updating and using the main-security repository.[/list]

What I'm trying to say here is what was done was for the best compromise for the situation at that moment.

If running the newly released FireFox 1.0PR or subsequent version was the best thing to be done at the moment... it would have been done.

Rest assured the developers and volunters here are not putting in the latest and greatest component is so that they have the free time to sit on the beach drinking fruit juice :)

---

### Post by Buffalo Soldier on 2005-03-23
[QUOTE=corefile]I find it amazing that you all are completly ok that the default web browser is **broken**.[/QUOTE]Just out of curiosity. What is your definition of broken?

This is what we usually mean by broken -> [http://ubuntuforums.org/showthread.php?t=21774](http://ubuntuforums.org/showthread.php?t=21774)

If it means something that crashes often, won't run, doesn't do what it is supposed to... then I must say the default firefox in Warty is not, because it works.

I think the term you're looking for is "outdated" ?

EDIT: For what it's worth I'm using Epiphany. Nothing against FireFox, just that I'm a sucker for GNOME integration :)

---

### Post by hashimoto on 2005-03-24
Well, maybe this is the IPv6 issue on Warty? Take a look at:[http://ubuntuguide.org/index.html#disableipv6-mozilla](http://ubuntuguide.org/index.html#disableipv6-mozilla)
try it and see if it helps.

---

### Post by swatch123 on 2005-03-24
[QUOTE=Buffalo Soldier]A person that's either never heard or doesn't understand the quote "*a whole that is greater than the sum of its parts*".

Sometimes yes, by having the all the best components you'll have the best system.

But most of the time you have to build using component that is not the best and greatest on it's own.. but component that works well with others to create the best system.

And that (best system) also is different from each and every person.

Just because what you're looking for in the a distro is the latest FireFox, doesn't mean Ubuntu doesn't work for others.

I mean it's allright by me if you were to come in here asking how to get the latest FireFox, get your answer, then you're still unsatisfied, and just professionally say this is not what you're looking for and leave nicely.

But what you did was like trying to get on people's nerve.

Anyway, thanks for giving Ubuntu a try. Sorry it didn't work out for you. I'm sure you will find what you're looking for elsewhere. Bye.[/QUOTE]
 I don't like firefox (mozzula) because It erased my add book sometime and ask u
make some conf when it started.It gives  few Asian language updating.I use Opera instead.

---

### Post by swatch123 on 2005-03-24
On the other hand,I pay higher attention to ubuntu,it is younger but more creative,goes closer to people who are debianers.It is quit good.I learn a few from ubuntu but few from redhat. :o

---

### Post by nocturn on 2005-03-24
[QUOTE=gnosis]Yes, it just spins forever.  Lynx works like a charm as does links, wget, ping and a number of other web applications.  Same issue I've had on two different computers with 0.9.3 using Knoppix
[/quote]

I installed my parent's computer with Ubuntu 4.10 two weeks ago, they run FireFox 0.9.3 and it has not failed one single time.
On my own system, I used the 1.0 backport but 0.9.3 also worked quite well.

When 1.0 was released, Warty was already in feature freeze, thus the newer version could not be added.

I agree that 1.0, 1.0.1 and now 1.0.2 contain some security bugfixes, so they should be included in an update.... This is the only valid point you made, but it is a security consideration, not a functional one.

---

### Post by TjaBBe on 2005-03-24
Firefox 0.9 gives no problem with me either. But whatever, if you think debian solves all of your problems without you having to search and find things out. Go ahead, try it, but don't come whining here if you run into another little problem that isn't instantly solved upon reinstalling.  =;

---

### Post by jdodson on 2005-03-24
i doubt that the entire firefox .9.3 browser is "broken."  what i would surmise is that it either got messed up somehow in you install proccess, or is still configured to use ipv6. that is why it is "spinning" basically by default in warty firefox was set to ipv6 and is DOG slow to load webpages.  [http://www.ubuntuguide.org](http://www.ubuntuguide.org) is your friend on this matter.

as for getting a new version of firefox in warty.  on the forum here is a project called backports.  backports brings the new "development" packages to warty.  they have a recent firefox version for warty. 

basically the reason they don't add every new package to warty is because they have stabalized on warty.  they will only release relevant security updates to programs the security team deems worthy.  so they will not just dump in the latest and greatest.  why would they do this?  stability.  including every new version of any given program makes for a very unstable experience.  if you want the latest packages, try the preview release of hoary.  i am using it now and it rocks.

---

### Post by jdodson on 2005-03-24
[QUOTE=corefile]I don't agree with his tone, nor do I agree with his choice of words; However if in fact ( cause I've never installed warty) Firefox is broken AND if this is the default browser then that is an issue that can not be blown off with "read a howto, or use backports". I really like Ubuntu Hoary so far, and that is why I hope that the developers take an app being broken that is one of the most used for a desktop distro and that is the default one at that a little more serious then "read a howto". We should be able to expect that one of the most widely used default apps would at least work. And I don't mean it will work if you make it, it should just work period. There is a certian amount of quality that I would at least hope we can agree on. Regardless of gnosis'  poor way of expressing it.[/QUOTE]

firefox has never and is not currently broken in warty.

---

