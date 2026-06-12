---
title: "&quot;Where Fedora went wrong&quot; interesting take on ESR's recent rant."
date: 2007-03-24
forum: Fedora/RedHat and derivatives
---

### Post by Adamant1988 on 2007-03-24
[ Link here ](http://www.oreillynet.com/linux/blog/2007/03/where_fedora_went_wrong.html)

[quote=Article]... ESR’s scatter shot attack on Fedora was wrong in more ways than I care to comment about here. Chromatic did a nice job of attacking the rant on several key points. He also pointed out quite correctly that ESR’s accomplishments as an Open Source activist didn’t make his changing distributions newsworthy.

The reason I’m not simply ignoring ESR is that he did point out a real problem with Fedora Core, one which I also noted in my review of Fedora Core 5 last year. When upgrading a system with yum or pup I ended up with upgrades that couldn’t be run because of dependency issues. ESR ran into a more serious example of the same problem: an automated upgrade breaking significant parts of his system due to similar dependency issues...[/quote]

Thoughts?

---

### Post by halfvolle melk on 2007-03-24
> **Adamant1988 said:**
> Thoughts?
It adds nothing.
> Nope, the problem isn&#8217;t in the code. That&#8217;s the disturbing part of the story, the real piece of news, that everyone seems to be ignoring.
and then fail to address what **is** the problem.

---

### Post by karellen on 2007-03-24
the problem **is** yum. and the repos. and how yum handles the dependencies

---

### Post by igknighted on 2007-03-24
> **karellen said:**
> the problem **is** yum. and the repos. and how yum handles the dependencies

This is a debate that has been had countless times before... many people LOVE yum.  I prefer it to the debian tools because it has more options.  Then again, speed is of no concern to me when it comes to installing software.  I want the most options so I can tune it as I want.  Yes, I also use Gentoo and very much like compiling specifically for my system, but as far as binary package installation goes, I like yum better than apt.

The point: It's all preference.  I wont try to convince you to love yum, so don't try to tell me that apt is better.  You like it?  Great, use it.  It is fast, I'll give it that.  I'll use yum anyways for the reasons stated above.

To the topic of this thread... I do not see a problem with Fedora.  It has some work to do if it wants to compete for the same users as Ubuntu, but go to their forums and browse around... they market as an intermediate distro, and in that light it is tremendous.  You get more control, more frequent updates of software to stay current, and more troubles from time to time because of those first two.  Example: kernels in Fedora are updated constantly.  Edgy and FC6 were released around the same time.  Edgy has gone from 2.6.17-10 kernel to 2.6.17-11.  Fedora has gone from 2.6.18-whatever(i forget the initial one) and now has a 2.6.20-something kernel.  With many updates in between.  Imagine the outrage from the Ubuntu community if Ubuntu did this and everyone's wireless and nvidia/ati graphics broke every time?  In Fedora this is the norm.  Not a flaw, but a different approach.  For many its not the approach they want... **don't bash Fedora and say it sucks, simply smile and say no thanks, not for me**.

---

### Post by Shay Stephens on 2007-03-24
> **Adamant1988 said:**
> [ Link here ](http://www.oreillynet.com/linux/blog/2007/03/where_fedora_went_wrong.html)



Thoughts?
I don't use fedora.  Tried it about a year and a half ago, but it didn't work on my laptop.  Ubuntu did, I have not cared too much about any other distro since then.  So for me it's "Fedora? Who cares?"

---

### Post by karellen on 2007-03-24
> **igknighted said:**
> This is a debate that has been had countless times before... many people LOVE yum.  I prefer it to the debian tools because it has more options.  Then again, speed is of no concern to me when it comes to installing software.  I want the most options so I can tune it as I want.  Yes, I also use Gentoo and very much like compiling specifically for my system, but as far as binary package installation goes, I like yum better than apt.

The point: It's all preference.  I wont try to convince you to love yum, so don't try to tell me that apt is better.  You like it?  Great, use it.  It is fast, I'll give it that.  I'll use yum anyways for the reasons stated above.

To the topic of this thread... I do not see a problem with Fedora.  It has some work to do if it wants to compete for the same users as Ubuntu, but go to their forums and browse around... they market as an intermediate distro, and in that light it is tremendous.  You get more control, more frequent updates of software to stay current, and more troubles from time to time because of those first two.  Example: kernels in Fedora are updated constantly.  Edgy and FC6 were released around the same time.  Edgy has gone from 2.6.17-10 kernel to 2.6.17-11.  Fedora has gone from 2.6.18-whatever(i forget the initial one) and now has a 2.6.20-something kernel.  With many updates in between.  Imagine the outrage from the Ubuntu community if Ubuntu did this and everyone's wireless and nvidia/ati graphics broke every time?  In Fedora this is the norm.  Not a flaw, but a different approach.  For many its not the approach they want... **don't bash Fedora and say it sucks, simply smile and say no thanks, not for me**.

I want speed and reliabilty. and huge repos like those of debian/ubuntu. and I don't have time nor patience to compile programs myself or to hunt and fix yum casual errors. with apt-get/aptitude I **never** had any problems when installing software. with yum I had. so you see....for me the choice is simple ;). and all is about choice, that's the beauty of gnu/linux :)

---

### Post by rai4shu2 on 2007-03-25
> **halfvolle melk said:**
> and then fail to address what **is** the problem.

From the article:

> The problem is insufficient testing and just plain sloppy repository management. What Fedora’s repository managers are really lacking is attention to detail.

The yum speed issues are being sorted out for FC7, from what I've seen on the dev mailing lists.

---

### Post by karellen on 2007-03-25
I will definitely give FC7 a try :)

---

### Post by Adamant1988 on 2007-03-25
I'm going to install FC6 on my laptop today and if it disagrees I'll just Ubuntu-ize it and be done with it

---

### Post by CocoAUS on 2007-03-26
The main problem with Fedora is yum.  It's also the main thing that Fedora fanboys constantly DENY is a problem.  Just another thread over, someone blamed it on slow PCs.  Give me a break!  Admit it, fix it, be done with it.  Then you won't have to keep denying it.

---

### Post by igknighted on 2007-03-26
> **CocoAUS said:**
> The main problem with Fedora is yum.  It's also the main thing that Fedora fanboys constantly DENY is a problem.  Just another thread over, someone blamed it on slow PCs.  Give me a break!  Admit it, fix it, be done with it.  Then you won't have to keep denying it.

d00d, what's your gripe with yum and why does it bother you that much?  Fedora is constantly working on yum to improve it wherever possible, including speed.  The fact is it is slower than apt.  Big deal.  It does other things better than apt.  Should I start a thread bitching about how Debian/Ubuntu sucks because I can't control package architectures as well as with Yum?  Of course not.  Each has strengths and weaknesses.  If Yum doesn't tickle your fancy, all you gotta do is say "Sorry, not for me."  As I said before, I prefer Yum to apt.  I also don't care about speed of install as much as I care about getting it done exactly how I want it.

We know you don't like yum.  Chill.  Others do, and just because it doesn't do exactly what **you** want doesn't make it a bad program.  This is linux, you have options.

EDIT:  FWIW, I am updating my gentoo system on my main PC now... all to change a few cflags/use flags and upgrade a few apps.  It might be done when I wake up tomorrow.  In the grand scheme of things, the speed difference between yum and apt isnt that much.

---

### Post by CocoAUS on 2007-03-26
Funny, I didn't start a thread about yum being slow.  Yet you, as I pointed out most fanboys do, continue to have an allergic reaction to anyone criticizing it.

*sigh*  Enjoy your bliss.

---

### Post by igknighted on 2007-03-27
> **CocoAUS said:**
> Funny, I didn't start a thread about yum being slow.  Yet you, as I pointed out most fanboys do, continue to have an allergic reaction to anyone criticizing it.

*sigh*  Enjoy your bliss.

Call me a fanboy all you want if it makes you feel better, but I'm hardly a fanboy of any distro.  I don't even have a Fedora install right now.  3 Ubuntu, a Sabayon, Sidux, Gentoo and SAM are all the OS's on my various computers/hard drives.  I used to use Fedora until a few weeks ago I got a new mobo for that computer and fedora didn't like it too much.  So yeah, I'm a Fedora fanboy.  The fact of the matter is that for my uses I prefer yum to apt.  End of story.  It just really frustrates me when people tell half the story like this.  Yes, its slow, but it does other things better.  If there was a thread to the opposite effect on fedoraforum.org I would probably stick up for apt... Both are good, but lets tell the whole truth here people.

---

### Post by Hendrixski on 2007-03-27
> **igknighted said:**
> This is a debate that has been had countless times before... many people LOVE yum.  I prefer it to the debian tools because it has more options.  Then again, speed is of no concern to me when it comes to installing software.  I want the most options so I can tune it as I want.  Yes, I also use Gentoo and very much like compiling specifically for my system, but as far as binary package installation goes, I like yum better than apt.

The point: It's all preference.  I wont try to convince you to love yum, so don't try to tell me that apt is better.  You like it?  Great, use it.  It is fast, I'll give it that.  I'll use yum anyways for the reasons stated above.

To the topic of this thread... I do not see a problem with Fedora.  It has some work to do if it wants to compete for the same users as Ubuntu, but go to their forums and browse around... they market as an intermediate distro, and in that light it is tremendous.  You get more control, more frequent updates of software to stay current, and more troubles from time to time because of those first two.  Example: kernels in Fedora are updated constantly.  Edgy and FC6 were released around the same time.  Edgy has gone from 2.6.17-10 kernel to 2.6.17-11.  Fedora has gone from 2.6.18-whatever(i forget the initial one) and now has a 2.6.20-something kernel.  With many updates in between.  Imagine the outrage from the Ubuntu community if Ubuntu did this and everyone's wireless and nvidia/ati graphics broke every time?  In Fedora this is the norm.  Not a flaw, but a different approach.  For many its not the approach they want... **don't bash Fedora and say it sucks, simply smile and say no thanks, not for me**.

That's a good point.  Fedora is not for me because I dont care so much about the nuclear arms race of kernel upgrades.  And as a long time debian user, RPM based distros are just awkward for me, don't feel right.  But it is a personal preference.  I'm sure someone will tell me that Ubuntu sucks because it's not as 1337 or something.
 (well, not here, but some of my Gentoo friends, ya know).

---

### Post by Peter Mount on 2007-03-28
We studied Fedora in my IT course. Because of this I had a bias towards Fedora when choosing a distro of Linux to run on my confusor. 

My change to Kubuntu came about after I had problems with being forced to use the latest version of LAMP for version of Fedora I was running. My web host uses PHP4.x and MySQL 4.x etc while the version of Fedora I was using would only let me put on PHP5 etc.

I could have put in the effort to learn to recompile the version of LAMP that I need but I noticed that pre-exisiting packages exist for Ubuntu. As I'm running a business I really need quick access to something that "just works". So that's why I'm now using Kubuntu.

I was sorry to stop using Fedora as I'd spent so much time with it. I hope they can learn something from this example as Fedora has so much to offer. 

In the mean time I have no compelling reason to change from Kubuntu so I'll be using it for some time yet.

---

### Post by seshomaru samma on 2007-03-29
I think fedora is great
The yum bit is not that important , you can install apt on Fedora if you wish , or smart

I use Ubuntu more because I'm not that experienced with Linux and I can get more answers in the Ubuntu forums ,if something goes wrong.

---

### Post by rai4shu2 on 2007-03-29
The thing that will really help Fedora is the delta RPM project. Hopefully that'll be ready to go before Fedora 7.

---

