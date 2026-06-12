---
title: "Ubuntu or Debian?"
date: 2007-02-25
forum: Debian
---

### Post by Darklighter137 on 2007-02-25
Hi guys!  I love my Ubuntu install, but I am wondering about Debian.  Is it more stable or reliable than Ubuntu?  Is it easier to setup and maintain for newbies?  In short, please tell me--from the perspective of someone who has used Ubuntu--what Debian is like.

---

### Post by aysiu on 2007-02-25
> **Darklighter137 said:**
> Hi guys!  I love my Ubuntu install, but I am wondering about Debian.  Is it more stable or reliable than Ubuntu? Yes, it is.  > Is it easier to setup and maintain for newbies? Easier to set up? No. Easier to maintain? About the same. > In short, please tell me--from the perspective of someone who has used Ubuntu--what Debian is like. Debian is focused on stability with infrequent releases. It is not intended to make sensible defaults. It makes the user understand what's being installed *or* installs a "default" desktop, which usually has a lot more applications than you need.

If stability is what you want, you want Debian. If you can handle a little instability and want frequent releases and an "easy" installation, Ubuntu is for you.

---

### Post by Darklighter137 on 2007-02-25
Thank you for the clarification. =)

---

### Post by Rodneyck on 2007-02-25
I was a long time Ubuntu/Kubuntu user and have switched to Sidux, which is Debian Sid made stable. I love it. It is so much faster than Kubuntu, probably the fastest distro I have tried, and installation was a breeze. It is also very stable.

[http://www.sidux.com/Article116.html](http://www.sidux.com/Article116.html)

---

### Post by stokedfish on 2007-02-25
Pure debian sid for a desktop is a joke, I'm afraid.

Sure, Sidux is great at the beginning. But do a few dist-upgrades and you'll see what i mean...  ;)

---

### Post by stokedfish on 2007-02-25
If you don't know what I mean, there ya go:

[http://www.sidux.org/PNphpBB2-viewforum-f-29-sid-df40d97a9d8d3429590cbf12ea68d601.html](http://www.sidux.org/PNphpBB2-viewforum-f-29-sid-df40d97a9d8d3429590cbf12ea68d601.html)

So, you have a choice:

a) not do any upgrades and have an unsecure and not up-to-date system
b) do upgrades and sooner or later run into the typical sid upgrade problems

You'll go back to Ubuntu or another stable distro soon, trust me.

---

### Post by Rodneyck on 2007-02-25
> **stokedfish said:**
> If you don't know what I mean, there ya go:

[http://www.sidux.org/PNphpBB2-viewforum-f-29-sid-df40d97a9d8d3429590cbf12ea68d601.html](http://www.sidux.org/PNphpBB2-viewforum-f-29-sid-df40d97a9d8d3429590cbf12ea68d601.html)

So, you have a choice:

a) not do any upgrades and have an unsecure and not up-to-date system
b) do upgrades and sooner or later run into the typical sid upgrade problems

You'll go back to Ubuntu or another stable distro soon, trust me.

I have done a few dist-upgrades and everyting is fine and stable. I suggest you read many of those posts more carefully. Most of those people are upgrading/crossing over from from pure debian, Kanotix or a beta release through scripts (h2 scripts.) The recommended way to install and use Sidux is from the final livecd.

Statement from one of the developers..."Please be aware that the cross-grade path from Etch netinstall and Kanotix was a temporarily solution, and is not supported officially by sidux any more since we published our own release. "

I can point to many threads here on Ubuntu of people having nightmare problems upgrading to Edgy...reporting Edgy as unstable. The best way of upgrading Edgy is reinstalling from the livecd of Edgy.

I suggest you actually give the Sidux livecd a try before generalizing through a few forum posts.

---

### Post by stokedfish on 2007-02-25
Sorry, double post...see below.

---

### Post by stokedfish on 2007-02-25
> **Rodneyck said:**
> I have done a few dist-upgrades and everyting is fine and stable.
Sure, after a few days it's still stable.

> **Rodneyck said:**
> I suggest you read many of those posts more carefully. Most of those people are upgrading/crossing over from from pure debian, Kanotix or a beta release through scripts (h2 scripts.) The recommended way to install and use Sidux is from the final livecd.
Of course, this causes additional problems, but it's not the real issue.

> **Rodneyck said:**
> I can point to many threads here on Ubuntu of people having nightmare problems upgrading to Edgy...reporting Edgy as unstable. The best way of upgrading Edgy is reinstalling from the livecd of Edgy.
As I said, this is not what I'm talking about.

On sid you will run into problems WITHIN a release cycle. If you don't believe me, try this: Get the latest Kanotix, do a fresh install, then do an upgrade or dist-upgrade...and BANG your system is broke and not usable anymore...

(technically, there are no release cycles for sid anyway)

It will be exactly the same with your system in the long run, that's sid.

> **Rodneyck said:**
> I suggest you actually give the Sidux livecd a try before generalizing through a few forum posts.
Naw, I don't have to, it's the same for all sid-based distros...

So you think sidux has some magic tricks to avoid the sid upgrade breakages? Well, you're wrong.

Sidux = pure Deban SID = still in development (and it will always be) = not suitable for a desktop system!

It's essentially the same as Kanotix, it just has another name and got pimped a little bit.

Kano was right when he said pure sid is not suitable for the desktop...but yeah, you will see soon enough.

---

### Post by Rodneyck on 2007-02-25
stokedfish, you obviously have some insane troll logic and since your refuse to even try Sidux, yet comment so heavily upon it, I do not really count anything you say as valid. It would be like writing a complete review of a movie you have never even seen.

I went to some of the people who have used Kanotix and the developer of Sidux himself, here are some of their comments.

> Obviously if you take a kanotix now and try to upgrade it it will break, there is nothing in the kanotix debian repos currently, so it would just be raw sid.

From the developer of Sidux:
> What we can can promise is: We take care not just to avoid breakage BETWEEN release cycles, but also put immense care into providing a long term upgrade path OVER SEVERAL releases. We have a several huge advantage over $buntu in doing that, one of them not deriving from Debian Sid, but instead sailing Debian Sid waters ourselves.

But the principles of success in sailing are not easy to understand for people who want to build fences and walls.  

and from a Kanotix user..
> True indeed and I and I am sure hundreds of others can attest as this was even how it was with early Kanotix.Even though Kanotix was not 100% pure debian sid like sidux,it still had some great magic and a broken system was not broken long either fixed by debian devs themselves or kanotix devs.In fact,I can say I have learn alot more from those breaks,fixes,and daily dist-upgrades,and am grateful I stuck by and learned.Never once have I had broken pakages or a broken system longer than a day! 

I think the important thing to remember is that ALL distributions can break, nothing is 100% full-proof. I know for a fact that two kernel upgrades from the Ubuntu repos have left my system with a black screen of death, and countless other users as well. I was all over those threads. Besides, learning from those mishaps is what makes one a smarter Linux user.

---

### Post by stokedfish on 2007-02-26
> **Rodneyck said:**
> stokedfish, you obviously have some insane troll logic and since your refuse to even try Sidux, yet comment so heavily upon it, I do not really count anything you say as valid.
Sidux = Debian sid

I've been on pure Debian sid for more than 1,5 years and I know it pretty well. Wether you set it up with sidux, kanotix or any other sid-based live CD simply does not matter - it's still Debian sid!

Is that so hard to understand? Just because it's called Sidux doesn't mean the sid upgrade breakages magically disappear...

Sid has no clean update path and that's why I cannot recommend it for a desktop computer and everyday work.

> **Rodneyck said:**
> It would be like writing a complete review of a movie you have never even seen.
Sid is sid, how you set it up is just cosmetics.

And all the rest is what they call marketing...  ;)

Or do you consider Linux Mint and Edgy two different systems? No, both are Ubuntus...

> Obviously if you take a kanotix now and try to upgrade it it will break, there is nothing in the kanotix debian repos currently, so it would just be raw sid.
That's exactly my point, there ya go...

Sidux is a raw sid as well. 

Just because there's a few packages in the sidux repos doesn't mean it's any different.

And yes, I agree - all distros can break. It's just that sid will break *for sure* and much more often...

Ubuntu normally doesn't break and never did for me.

In my opinion pure sid is essentially nonsense for a desktop system. It's a DEVELOPER system, that says it all.

Anyway, I'll ask you back in a few months. Then we'll see if you still like sidux and how troublesome (or not) it really is for you...

---

### Post by coxc24 on 2007-02-26
My suggestion would be for servers, Debian 3.1 (Sarge) - I think that is the right version number. It is rock solid as a server OS should be.

For a desktop, Kubuntu or Ubuntu - there is no competition.

---

### Post by Rodneyck on 2007-02-26
stokedfish, I see the problem now. You assume Sidux is pure Debian Sid. Had you actually taken the time to investigate instead of making off-the-cuff theories, you would know that statement is false. 

Sidux is not 100% Debian Sid and it is not a Linux Mint port of Ubuntu distribution type. In fact, you probably can not tell me what repos Sidux uses, can you?  That would put a hole in your theory.

I have had Ubuntu break on me many times, like I stated, and so have many others here. I can point you to those threads if you like.  Just remember to backup before doing those kernel updates.  

Sidux is not for everyone, nor is Ubuntu. Sidux is on the cutting-edge. You benefit from its trickle down effect. What we test and use, will be your next-best-thing in in about six months from now, such as the new kernel. If it were not for the developers of Debian Sid and other distributions that modify Debian Sidux, Ubuntu would not exist. The unfortunate thing is that Ubuntu takes, but never gives back to the pool. The linux community gets nothing back from Ubuntu, except an OS where much of its backbone is not really its own. The same can not be said for Debian, and particularly Debian Sid.

Even if Sidux does not work out for me, I will not return to Ubuntu or Kubuntu, they were to slow on my computer, and I have an up-to-date system. Somewhere, there are bottlenecks in speed and I hope the developers fix this in Fiesty. In comparison to Ubuntu, Sidux is extremely fast, as are many other distros I have tested, PCLinuxOS, Gentoo, Foresight Linux, etc.  You can pretend all you want, as it is clear this, Ubuntu, is meant for YOU, most definitely.

---

### Post by stokedfish on 2007-02-26
```
# See sources.list(5) for more information, especialy
# Remember that you can only use http, ftp or file URIs
# CDROMs are managed through the apt-cdrom tool.

# Unstable
deb http://ftp.de.debian.org/debian unstable main contrib non-free
# deb-src http://ftp.de.debian.org/debian unstable main contrib non-free

# Testing
# deb http://ftp.de.debian.org/debian testing main contrib non-free
# deb-src http://ftp.de.debian.org/debian testing main contrib non-free

# Experimental
# deb http://ftp.de.debian.org/debian experimental main contrib non-free
# deb-src http://ftp.de.debian.org/debian experimental main contrib non-free

# sidux
deb http://sidux.com/debian/ sid main contrib non-free firmware fix.main fix.contrib fix.non-free
#deb-src http://sidux.com/debian/ sid main contrib non-free firmware fix.main fix.contrib fix.non-free
```
= 99% Debian sid!

Browse [http://sidux.com/debian/](http://sidux.com/debian/) if you don't believe me.

The other 1 percent won't save you from breakages, that's for sure.

You can pretend all you want, as it is clear - essentially, you're on pure Debian sid, nothing else.

---

### Post by Rodneyck on 2007-02-26
ROFL... And how did you come about those figures?  You are so sad.

Believe what you want. I equate your spreading of misinformation to the Fox News Channel's reporting for the conservatives in the US. There is no reasoning with this sort of off-sided logic. You make false statements without facts, and you have not even tried the distribution you attack. Which is funny, because you, Ubuntu user, indirectly benefit from everyones hard work and give nothing. Try and grasp that.

Besides, isn't choice really what Linux is all about and why many of us escape from the Microsoft/Apple lock-ins?  Your way of thinking is much like theirs...Ubuntu is the only one, all others are unstable (again, false.) And lets not forget that without Debian Sid, you would be sitting at a black screen right now.  Good luck with that!

:guitar:

---

### Post by stokedfish on 2007-02-26
Would you please refer to my argument above with the sources.list and tell me what exactly makes it NOT a debian sid instead of starting off-topic talk? Thanks. People usually change topic randomly when they run out of arguments...

Looking forward to your explanation why the above is, essentially, no Debian sid. Enlighten me! 

Btw, as a side note - my main distro is not Ubuntu...  ;)

---

### Post by Rodneyck on 2007-02-26
> **stokedfish said:**
> Would you please refer to my argument above with the sources.list and tell me what exactly makes it NOT a debian sid instead of starting off-topic talk? Thanks. People usually change topic randomly when they run out of arguments...

That's rich, you have not supplied one ounce of fact and evaded just about everything with the mantra of Sidux is 100% debian sid, again without backing that statement up.

You can not download pure Sid packages from the repo, many alterations have been made for Sidux (which is why the sidux repo is there), much like you can not do the same from Debian through Ubuntu's repos. If you could, why not just run Debian stable?  Because Ubuntu has made modifications to the packages to fit their needs.

Sidux has this to officially say... "This is the first official sidux release after stabilizing and largely rewriting the distribution framework, further efforts in that direction are ongoing to improve the hardware support/detection and streamline the live operations." You can also refer to my earlier example from one of the main developers himself.

Sidux is Debian Sid modified...to make it stable for use.

Now you have not answered my question. How did you come across those 100% or 99% figures. Please show me where you got these most touted numbers you rely on so heavily. 

Looking forward to your explanation of the numbers, please, oh please.. Enlighten me! 

> **stokedfish said:**
> Btw, as a side note - my main distro is not Ubuntu...  ;)

You have demonstrated to me from your very narrow understanding of either distribution, it really should be your main distro. Ubuntu was meant for you.

---

### Post by stokedfish on 2007-02-26
[COLOR="Red"]**The unstable distribution (sid)**[/COLOR]

[http://www.debian.org/releases/unstable/](http://www.debian.org/releases/unstable/)

> **Rodneyck said:**
> That's rich, you have not supplied one ounce of fact and evaded just about everything with the mantra of Sidux is 100% debian sid, again without backing that statement up.
Not true - the above sources.list is a fact.

And everyone who takes a look at it and even has the slightest idea of debian will come to the conclusion that sidux is essentially sid, and nothing else.

> **Rodneyck said:**
> You can not download pure Sid packages from the repo
Yeah, of course...

[http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) unstable

= pure debian sid!

And this is in the sources.list, which means it's also what will be installed on your system - sid.

You can, of course, further refuse to see this, but it won't make it any less real...

> **Rodneyck said:**
>  many alterations have been made for Sidux (which is why the sidux repo is there)
Have you even taken a look at that repo?

All I see are non-free drivers and a different kernel...

And now, tell me - how should this make sid stable? You know that the developers of debian sid just laughed and turned away when the sidux guys said they want to make sid stable, right? Well, I guess if anyone knows if it's possible or not, that's not you or me, but the sid devs themselves...

> **Rodneyck said:**
> Because Ubuntu has made modifications to the packages to fit their needs.
Of course, but there's one fundamental difference that you don't want to see:

Ubuntu doesn't have the sid unstable source in the sources.list!

And as long this source is in there your system will break regularly when you do upgrades...

> **Rodneyck said:**
> Sidux has this to officially say... "This is the first official sidux release after stabilizing and largely rewriting the distribution framework, further efforts in that direction are ongoing to improve the hardware support/detection and streamline the live operations." You can also refer to my earlier example from one of the main developers himself.
Sure, hardware support, no doubt...but your system will still break in the long run when you do upgrades.

Fact is: Non of the sidux packaes avoids upgrade breakages, so it's essentiallya debian sid with a few kernel patches thrown in.

> **Rodneyck said:**
> Sidux is Debian Sid modified...to make it stable for use.
Debian sid will never be stable for use. Developer systems are not meant to be stable, very simple.

> **Rodneyck said:**
> Now you have not answered my question. How did you come across those 100% or 99% figures. Please show me where you got these most touted numbers you rely on so heavily.
Of course, the 99% are a guess. But what does it matter if it's 92% or 99% or whatever? The very essential thing here will still be true - as long as [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) unstable is in your sources.list, you will end up with an unstable system. 

Believe it, don't believe it, I don't care. But you will.

> **The code name for Debian's development distribution is "sid", aliased to "unstable"**. Most of the development work that is done in Debian, is uploaded to this distribution. This distribution will never get released; instead, packages from it will propagate into testing and then into a real release.

Please note that security updates for "unstable" distribution are not managed by the security team. Hence, "unstable" does not get security updates in a timely manner. For more information please see the Security Team's FAQ.

**"sid" is subject to massive changes and in-place library updates. This can result in a very "unstable" system which contains packages that cannot be installed due to missing libraries, dependencies that cannot be fulfilled etc. Use it at your own risk!**
[http://www.debian.org/releases/unstable/](http://www.debian.org/releases/unstable/)

Sid will never be stable (by its very definition) nor will it ever get security updates...

Not stable + no security updates = not suitable for a desktop system in a productive environment!

And the very same applies to Sidux...

---

### Post by Rodneyck on 2007-02-26
First off, Debian Sid is not really meant to be a full-fledge operating distribution on its own, it is a testing ground. Packages are pulled from it, tested, modified and then eventually trickled down into Debian stable, and feeding from it, at the bottom of the list, Ubuntu with their modifications if need be and other distributions.

Sidux is sailing the waters by changing Sid, pulling from the repos of the testing, and with having their repo in the source.list modifies many of the Debian Sid packages to make them stable, as I have pointed out before. This is their goal. This is not a hard concept to grasp, at least for other people.

I was correct and finally you admitted it about the 100%/99% figures and most of what you are saying, you are guessing.  I think this is really all it boils down to. You have no facts to back up what you are saying so it is a mute point to continue trying to convince you.

I really have nothing more to say that I haven't already said. Again, no distribution, even the one you are using (and I am guessing is is probably Microsoft) is 100% stable, which really puts a knife in your theory. 

Adios!

---

### Post by stokedfish on 2007-02-26
> **Rodneyck said:**
> Sidux is sailing the waters by changing Sid, pulling from the repos of the testing, and with having their repo in the source.list modifies many of the Debian Sid packages to make them stable, as I have pointed out before. This is their goal. This is not a hard concept to grasp, at least for other people.
They'd have to replace virtually all the sid repo to make it stable and at the end it would be a new distribution not based on sid anymore.

I thought this to be very obious and easy to grasp, at least for other people.

> **Rodneyck said:**
> I was correct and finally you admitted it about the 100%/99% figures and most of what you are saying, you are guessing.  I think this is really all it boils down to. You have no facts to back up what you are saying so it is a mute point to continue trying to convince you.
Basically, you refuse to believe the very experts - the sid devs...they know the very best that sid is not and will never be stable and they stated this various times. Of course, you're free to keep your arrogance and think you know about this better then the creators of sid themselves.

> **Rodneyck said:**
> I really have nothing more to say that I haven't already said.
Yep, same here.

Someone who refuses to believe in what experts say (I don't mean my opinion but the one of the sid devs) and thinks he knows better than the very people behind a distro that is the foundation of Ubuntu, Sidux and a whole lot of others, is not worth to discuss with anyway...

Adios!

---

### Post by Rodneyck on 2007-02-26
Yes, best to end on a good note.

Oh btw, it appears I am not the only one recommending Sidux...

> **stokedfish said:**
> Try sidux.

But to be honest - I can't recommend Debian SID for the desktop...

However, that's for you to find out.

Found here...
[http://www.ubuntuforums.org/showthread.php?t=369561&page=2](http://www.ubuntuforums.org/showthread.php?t=369561&page=2)

=D>

---

### Post by Kateikyoushi on 2007-02-27
Why is it better than let's say debian with testing repos ?

---

### Post by Rodneyck on 2007-02-27
> **Kateikyoushi said:**
> Why is it better than let's say debian with testing repos ?

Is your question, why is Sidux better than Debian Sid (testing)? If so, then it is because debian testing repos are unstable packages, not ready for public use because, well they are being tested. Sidux has reworked many of these packages and made them stable for their purpose. In doing so, it is not really Debian Sid anymore, at least not pure Sid. 

They have a minis and full livecd if you want to check it out. Again, it is a super fast and stable system, plus cutting-edge stuff that ubuntu won't see for another six months. Don't let naysayers scare you into trying different distributions, they have their own agenda. That is the beauty of linux, it is all open and free, so have it.

:)

---

### Post by Kateikyoushi on 2007-02-27
Thanks for the answer I am off to DL the livedisc for a spin. I am curious how fast it is.

---

### Post by benuski on 2007-02-27
I've been using sid for a couple weeks now, and I must say, its a lot of fun.  Its my main OS for my laptop that I keep all my college work on.  Yes, I do backups, and I do have a backup OS partition, but I really haven't had any problems with Sid yet.  I kinda like the fact that it is continuously updated, and not just updated through releases.  I've also liked living on the edge, always download the newest betas/alphas of Ubuntu/Debian, so having Sid was just the next logical step.  But I have't had a huge break yet.

---

### Post by Kateikyoushi on 2007-02-28
Seems it doesn't like firewire dvd so it must wait for a while till I can install it, a pity i was really curious but don't really have the time to figure out what went wrong, not that this is new gentoo was the same.

---

### Post by zubrug on 2007-03-16
tried sidux today, nice distro, very fast (xfce like).
I am going to play with it over the next couple of day's, it looks very promising, forum is small but seems quite friendly.

---

### Post by SlCKB0Y on 2007-03-16
> **stokedfish said:**
> 

Sidux = pure Deban SID = still in development (and it will always be) = not suitable for a desktop system!

It's essentially the same as Kanotix, it just has another name and got pimped a little bit.

Kano was right when he said pure sid is not suitable for the desktop...but yeah, you will see soon enough.

With debian SID you just have to have some understanding of what is going on. This means knowing a little bit about debian/linux and checking before upgrading just to make sure nothing is majorly broken.

Oh, and if things do break, it requires the ability to read in order to fix it and/or the patience to wait for a fix to be released.

Nobody is making you be on the bleeding edge, especially since you seen like a newbie.

I ram debian SID for a very long time with only minimal problems. About the same as im getting with running pre beta feisty.

---

### Post by richbarna on 2007-04-02
I am running Debian Sid and Ubuntu Feisty side by side. I have installed the same software, both have E17 desktop and both are updated every week (if there are updates)

I have no breakage reports whatsoever. However, I know how to fix the breakage when it happens, and would not recommend either to a new user. 

I would however recommend Debian Etch as probably the best desktop distro I have used. (This is a personal opinion based on what works for me)

I am very impressed with Feisty, although my main systems will always be Debian; (Sarge, Etch, Sid) including my server.

I dislike the fact that people still refer to Debian as being difficult to install, it isn't. It's no different from 100 other distro's I have tested. This doesn't do Debian justice.

I recommend more (6 months or more) new users try it to dispell the myth.

---

### Post by karellen on 2007-04-02
I've never used debian, so I honestly don't know. I heard only good things about debian (stability, huge repos, large and friendly community). but that's what I encounter here with ubuntu...so I'll stay with my edgy (so far :D)

---

### Post by finferflu on 2007-04-12
Ubuntu has abandoned my far too many times, and I had to reinstall it in moments when I rather had to write my essays. It might have been my fault, I installed too much stuff, perhaps, but I think there's some junk stuff going around Ubuntu (meaning non ufficial packages), that endangers your system's stability and you don't even realise it. Of course it's your fault if you decide to install it. Yet, when you see packages being thrown here and there, it's hard to resist the temptation to grab one. On the other side, apart from security, I find Ubuntu too overloaded with things I don't need (anymore, perhaps), and it's too slow for my taste. Therefore I have made my switch to Debian Etch (taking advantage of the recent stable release), and built it from ground up, so to speak. I've installed the base system, with no X, and then installed gnome-base, so that I could and can select what I actually need and when I need it. A good way to keep it light and very customised. 
The reason why I still like Ubuntu a lot is its wide support, and these forums. If I ever have a problem, 80% (if not more) of the times I can solve it on Ubuntu. New apps are packaged for Ubuntu (and not for Debian sometimes). 
So I will use Debian for my everyday productivity, as something I can really rely upon, and I'll wait for Ubuntu Studio for fancy productivity.

In conclusion, that's the way I see it: Debian is austere, Ubuntu is fancy!

---

### Post by rplantz on 2007-04-18
> **finferflu said:**
> Yet, when you see packages being thrown here and there, it's hard to resist the temptation to grab one. On the other side, apart from security, I find Ubuntu too overloaded with things I don't need (anymore, perhaps), and it's too slow for my taste.
...
In conclusion, that's the way I see it: Debian is austere, Ubuntu is fancy!

I have the same general impression. I installed Feisty several weeks ago and have continued to upgrade through the latest release candidate. As might be expected in any similar situation, there have been a few problems. (No complaint from me since it was clearly labeled as pre-release.)

During all the fun with Ubuntu nearing release, I neglected my Debian installation. I upgraded it to the latest Etch yesterday. (Not a fresh install, just upgrade.) Although I do not have any numbers to prove it, Debian has always _seemed_ faster to me than Ubuntu.

My hardware is reasonable -- amd 3200+, abit nf8 motherboard, nvidia fx5200 128MB graphics, and 1 GB RAM.

Ubuntu is really good, but there's just something about Debian that _feels_ better to me. Since I like living on the bleeding edge, I'll probably give Sid a try. I'm going to read more about Sidux to see if that's a good way to work into Sid.

---

### Post by mrfelker on 2007-04-19
I have both installed in a RAID 1 configuration.  Debian 4.0 just released and of course Feisty Fawn.
Ubuntu is easier to setup because you have to know more computing to setup Debian.  Debian does not have the pretty Windows type boot screen.  Debian is totally Open Source - even Firefox is called Iceweasel because they don't want to use any copyright software.  Although Ubuntu is "built" on Debian the main thing that's alike is the install program (with Debian you only have a text install).  Both OS's are very stable.  There are more things to say but I need to get back to configuring Feisty now.

---

### Post by bwhite82 on 2007-04-19
>  (with Debian you only have a text install)

Not true. They do have a graphical installer now, you just won't see it as an option at the boot screen, you have to type in either , installgui or expertgui (advanced users). Debian doesn't tend to advertise things, they just spell everything out in the release notes and expect you to read them and I personally have zero problems with that.

---

### Post by deanlinkous on 2007-04-19
> **mrfelker said:**
>   even Firefox is called Iceweasel because they don't want to use any copyright software.  Has nothing to do with that. It has to do with being able to modify it and still call it firefox and mozilla said 'no' to that.

---

### Post by Pobega on 2007-04-21
> **stokedfish said:**
> Pure debian sid for a desktop is a joke, I'm afraid.

Sure, Sidux is great at the beginning. But do a few dist-upgrades and you'll see what i mean...  ;)

Debian Sid for the desktop is equally as stable as Ubuntu's Feisty release. Ubuntu is based on Debian's unstable branch, so I don't know how you could say this.

Sidux, however, it's a Debian fork. It's basically an attempt to make a community solely behind the desktop use of Sid, without worrying about server stability.

If you want to stability, ease-of-use, and up to date packages try out Debian Testing (Lenny at the moment), it's what I use for my home computer (I use Sid on everything else) and I'm extremely happy with it; No complaints.

---

### Post by rai4shu2 on 2007-04-21
I used Debian Etch for about a week, and I think the difference is the way everything is configured. There's really not much difference in stability (that mostly has to do with hardware and what drivers you use, really). Ubuntu is like Debian with some really great default configuration.

---

### Post by Rodneyck on 2007-04-21
Sidux is going through rough waters right now because all the cutting-edge releases are dropping into play due to Etch's release and the removing of the freeze that was in place. With the help of their wonderful devs and du-fixes scripts which help capture all the unstable stuff, I have not had one problem and finally Sidux is becoming more cutting-edge than Fiesty. 

There are issues currently with ATI drivers and the new xorg, but this an ATI problem in general, not Sidux/Debian's or xorg's.  Ubuntu w/Fiesty reworked/customized the xorg 7.2 for their own purpose, so that is why they are not experiencing any problems atm with ATI drivers.

Side note...ATI sucks and this is why I have always supported Nvidia.

---

### Post by Pobega on 2007-04-21
> **Rodneyck said:**
> Sidux is going through rough waters right now because all the cutting-edge releases are dropping into play due to Etch's release and the removing of the freeze that was in place. With the help of their wonderful devs and du-fixes scripts which help capture all the unstable stuff, I have not had one problem and finally Sidux is becoming more cutting-edge than Fiesty. 

There are issues currently with ATI drivers and the new xorg, but this an ATI problem in general, not Sidux/Debian's or xorg's.  Ubuntu w/Fiesty reworked/customized the xorg 7.2 for their own purpose, so that is why they are not experiencing any problems atm with ATI drivers.

Side note...ATI sucks and this is why I have always supported Nvidia.

Yeah, this is going to be the toughest time Sidux will ever have to face. Their first actual "upgrade", when coming out of a freeze. Hopefully Sidux doesn't fall apart like other Sid clones.

---

### Post by bg11 on 2007-04-22
I started with knoppix, which was amazingly easy to install.  The hardware detection was like nothing I'd seen before, but it kept breaking every apt upgrade, the 3D video drivers were such a pain to install!  Then I came across kanotix, which had a great community who would give you a heads up if there were any problems with apt upgrading.
  The best parts about kanotix was that it was at the bleeding edge and it had funky scripts that made life a hell of a lot easier, installing video drivers became easier than taking a wee!  I could finally play GTA San Andreas using cedega on linux!!!  There was even a script which helped you upgrade and avoid any dodgy packages, brilliant!
But then, sadly, it all ended, the people behind kanotix fell apart, money issues didn't help the ideological differences between them.  That's when I tried ubuntu.

Ubuntu was more difficult to install than kanotix, though I did eventually get it to work.  Ubuntu was definitely slower.  An old laptop I have refuses to load anything except win98, knoppix and kanotix (have not tried sidux on it yet)!  Every other linux live cd distro failed to run, including ubuntu, mepis, pclinux, fedora, dsl, puppy, and others!

My kanotix partition still runs fine, I upgraded just last week with no problems at all even though it's the 2004 install, how's that for stability?  I guess I'll install sidux on my kanotix partition at some point though, because kanotix looks dead, it's once vibrant forums now seem like that of a ghost town, very sad really.

Ubuntu is ok for newbs and will provide a good stepping stone to linux for windows users, but some people will want to drive a ferrari rather than a volvo. :)

---

### Post by finferflu on 2007-04-22
> **bg11 said:**
> 
Ubuntu is ok for newbs and will provide a good stepping stone to linux for windows users, but some people will want to drive a ferrari rather than a volvo. :)

That's exactly how I see it.

---

### Post by plb on 2007-04-23
Ubuntu isn't just for newbs. It's also for people who want things to "just work." I've been using Linux since 1999 so I don't really consider myself a newb.

---

### Post by finferflu on 2007-04-23
> **plb said:**
> Ubuntu isn't just for newbs. It's also for people who want things to "just work." I've been using Linux since 1999 so I don't really consider myself a newb.
Let's say it's for people who like less customisation, like newbies (which are limited to fewer options, because of their limited knowledge).

---

### Post by plb on 2007-04-23
In a sense I suppose. I mean, anyone could just pick and choose what they like in ubuntu same as debian... you just need to know what you're doing. But have you tried etch? it defaults to a nice customized GNOME desktop if you want it too.

---

### Post by finferflu on 2007-04-23
> **plb said:**
> In a sense I suppose. I mean, anyone could just pick and choose what they like in ubuntu same as debian... you just need to know what you're doing. But have you tried etch? it defaults to a nice customized GNOME desktop if you want it too.
Yes, Etch is my primary OS (at times, since Feisty is too nice :D), and it's quite sweet. But it's not as loaded as Ubuntu. Also when I went through a high customisation, I ended up installing it. If you leave Ubuntu as much intact as possible, it will never abandon you, but if  you start customising it, you're gonna have to reinstall it. At least this is my experience. Debian looks more like a platform, that can become whaterver you wish, but there's still a long way for me before I can review it properly.

---

### Post by GSF1200S on 2007-04-23
> **aysiu said:**
> Yes, it is.   Easier to set up? No. Easier to maintain? About the same.  Debian is focused on stability with infrequent releases. It is not intended to make sensible defaults. It makes the user understand what's being installed *or* installs a "default" desktop, which usually has a lot more applications than you need.

If stability is what you want, you want Debian. If you can handle a little instability and want frequent releases and an "easy" installation, Ubuntu is for you.

I know this is an old post, but Ubuntu is simply not unstable. Ive had ONE freeze, and its because I messed up and this was in BETA stages. I understand how you rate Debian more stable than Ubuntu, but that isnt to say Ubuntu is unstable. 

What exactly is meant that you can use more advanced/ newer apps with Ubuntu? I mean you still use the debian platform.. what makes Ubuntu more advanced?

---

### Post by bwhite82 on 2007-04-27
It depends on your definition of "advanced". A lot of people's definition is "newer package versions". If that is the case, then yes, Ubuntu is more advanced because it releases every 6 months, based off of Debian's unstable branch. However, what is* really* disputed is, "Is Debian more stable than Ubuntu?" Again, it has to do with one's definition. If you take the *releases* of both distros and compared them at doing the same tasks, Debian will more than likely win because it is more stable. But, Debian will contain older and highly-tested packages to obtain this stability. Whereas, Ubuntu is at a disadvantage because it is using, less-tested, and generally more unstable packages.

Now, if you compare the *latest and greatest* of both distros, then Ubuntu will win. This would be comparing Debian Sid and Ubuntu Feisty. I would never recommend installing Sid, you WILL have problems. But, with some trepidation, I can reasonably recommend installing Feisty because Ubuntu has done *more* testing on these unstable packages than Debian has on the same unstable packages.

With all that was said above, you cannot reasonably compare these two excellent distros. They both have different goals. If you want *stability* then go with Debian Etch or Lenny, I assure you that it won't let you down. If you want the *latest and greatest* you should go with whatever is the latest flavor of Ubuntu.

---

### Post by plb on 2007-04-27
> **Soldierboy said:**
> It depends on your definition of "advanced". A lot of people's definition is "newer package versions". If that is the case, then yes, Ubuntu is more advanced because it releases every 6 months, based off of Debian's unstable branch. However, what is* really* disputed is, "Is Debian more stable than Ubuntu?" Again, it has to do with one's definition. If you take the *releases* of both distros and compared them at doing the same tasks, Debian will more than likely win because it is more stable. But, Debian will contain older and highly-tested packages to obtain this stability. Whereas, Ubuntu is at a disadvantage because it is using, less-tested, and generally more unstable packages.

Now, if you compare the *latest and greatest* of both distros, then Ubuntu will win. This would be comparing Debian Sid and Ubuntu Feisty. I would never recommend installing Sid, you WILL have problems. But, with some trepidation, I can reasonably recommend installing Feisty because Ubuntu has done *more* testing on these unstable packages than Debian has on the same unstable packages.

With all that was said above, you cannot reasonably compare these two excellent distros. They both have different goals. If you want *stability* then go with Debian Etch or Lenny, I assure you that it won't let you down. If you want the *latest and greatest* you should go with whatever is the latest flavor of Ubuntu.

I ran sid for a LONG time as a desktop without any problems and I know many people who do the same.

---

### Post by bwhite82 on 2007-04-27
> **plb said:**
> I ran sid for a LONG time as a desktop without any problems and I know many people who do the same.

That's great! However, my opinion still stands, I cannot recommend it to be installed. BUT, Debian needs folks to use it to find bugs, so I'm all for the brave that do.

---

### Post by plb on 2007-04-27
Well I'm not running it now. Etch is up to date enough....for now :)

---

### Post by Rodneyck on 2007-04-28
> **plb said:**
> I ran sid for a LONG time as a desktop without any problems and I know many people who do the same.

If you want to run sid, then use Sidux as it is debian sid made stable...I recommend it.

---

### Post by DirtDawg on 2007-06-13
I'm going to drudge this old thread up just to say I've replaced Xubuntu Dapper with Debian Etch on my lil' red imac g3 and I'm most happy with it.

The packages for the notoriously "outdated" desktop are more up to date than Dapper and, even running Gnome, Etch is at least as fast as Xubuntu was. Not to mention, fewer "quirks". 

That said, documentation is not as robust as Ubuntu's. Luckily many Ubuntu tutorials and HOWTOs work fine for Debian.

I recommend at least checking out the live cd.

---

### Post by Hevoos on 2007-06-15
Why compare etch and feisty? I have used debian lenny on the desktop and I have no problems using it, of course feisty uses newer packages but it is not as stable.

---

### Post by angryfirelord on 2007-06-15
The way I see it, Ubuntu fills the gap nicely between Debian Testing and Debian Unstable. The packages aren't very old, but yet it doesn't seems to break easily. Yes, Ubuntu isn't perfect, but it comes pretty close. Kudos to the Debian and Ubuntu devs!

---

### Post by uputer on 2007-06-15
I am not sure where to post this but I had a question regarding the two distros.   I was wondering how much integration one can do with the two.   For e.g., Feisty and Etch.    If you store important info/data/programs in your home directory, can you move or use this data in the other distro?   I am not sure if I am asking this question properly but in other words, I am asking if you have both distros in a partition, how much integration can one use?   I plan on having both so I am interested in the answer.

---

### Post by angryfirelord on 2007-06-15
> **uputer said:**
> I am not sure where to post this but I had a question regarding the two distros.   I was wondering how much integration one can do with the two.   For e.g., Feisty and Etch.    If you store important info/data/programs in your home directory, can you move or use this data in the other distro?   I am not sure if I am asking this question properly but in other words, I am asking if you have both distros in a partition, how much integration can one use?   I plan on having both so I am interested in the answer.

First, the /home directory has to be on its own partition.

Next, some configuration files are stored at /home/your_username, which may conflict with Etch (or any other distro).

---

### Post by webmonkey44 on 2007-06-21
I would say that Debian releases marked stable would beat Ubuntu in stability.

---

### Post by JebusWankel on 2007-06-28
I have a dual boot of Etch and Fiesty, where both share the same /home partition and therefore all the same configuration files. The problems that come up from this setup are mostly minor. The themes switch around in one when I change the theme in the other. The Etch version of gnome uses two buttons where Fiesty's version uses one for log off/switch user and restart/shut down so that leaves a vestigal shutdown button in Fiesty. Debian uses Iceweasel instead of Firefox, so that leaves another vestigal button.

Besides these minor inconveniences, having the two has had some real advantages. The first is that Debian (which I installed second) came basically pre-configured, so that saved a ton of time. I've had Azureus get messed up in Ubuntu and fixed it by consecutively running it in Ubuntu, where it would segfault, then Debian, where it would all but connect, then in Ubuntu again, where it has fixed. I can't explain how it happened, but it made me happy.

IIRC Installing Ubuntu second is better because it will set up Debian in GRUB and automount the Debian partition.

---

### Post by Landser on 2007-06-30
> **Rodneyck said:**
> If you want to run sid, then use Sidux as it is debian sid made stable...I recommend it.

"Made Stable" ??. It's just debian sid (UNstable) with some scripts that prevent update breakage (du-fixes).

And besides, I like GNOME, and the GNOME in sid is broken. So this distro is a no-op for me (or for anyone who likes GNOME, for that matter)

---

### Post by Buffalo Soldier on 2007-07-02
Just installed Debian 4.0 (Etch) last nite. So far I'm loving this experience. I think I can live w/o the compiz and the other bling bling.

The only hiccup during installation was it did not detect my Intel 2200 wireless. Need to connect to the net using wired LAN, download the ipw2200 firmware and copy to a directory, then restart and everything was OK.

The first thing I did after that was to install and configure sudo :P I think I manage to make it run like in Ubuntu.

Nearly all of the app's are a few versions behind Fiesty. But in terms of doing my daily routine it has not become an issue. I think I'm going to give Debian Etch a try for a month, see how thing goes.

Now... where do I download the human icon/theme???....

---

### Post by Malibu Illusion on 2007-07-03
> **Buffalo Soldier said:**
> Now... where do I download the human icon/theme???....

I'd have thought losing that would have been one of the advantages of installing pretty much any other distribution, haha. ^^

I've been using Debian Etch (stable) for a long while on my desktop; it's a great OS, although I'd probably recommend Debian Lenny (testing) to anyone wishing to use it as a desktop platform with more up to date packages.

Take care.

---

### Post by Buffalo Soldier on 2007-07-03
> **Malibu Illusion said:**
> I'd have thought losing that would have been one of the advantages of installing pretty much any other distribution, haha. ^^

I've been using Debian Etch (stable) for a long while on my desktop; it's a great OS, although I'd probably recommend Debian Lenny (testing) to anyone wishing to use it as a desktop platform with more up to date packages.

Take care.
I guess I'm one of those few that loves the brown/orange looks :p

Do you have any real experience with Lenny? How do you rate it's stability against Feisty and Dapper (LTS)?

---

### Post by Malibu Illusion on 2007-07-04
Unfortunately I can't talk from experience in direct relation to the stability against Feisty or Dapper, since I've mainly done the majority of my computing on the "stable" branch which I've found adequate for my own personal needs.  I recognize that a lot of people prefer more bleeding edge packages on their desktop systems though which is why I'd recommend people who are looking for that taking a look at the Lenny line over stable, Debian-wise.

Theoretically speaking, Debian Lenny should be more stable than Ubuntu as the code in that branch has been tested slightly more in comparison with the Debian Sid snapshots that Ubuntu take at 6 monthly intervals of code that potentially has not been debugged yet.  Lenny would have slightly less up-to-date packages but should, in theory, have the stability over Ubuntu which is, essentially, snapshotted absolute bleeding-edge Debian.

---

### Post by andrek on 2007-07-06
I'm a Debian Sid user now. Even if it's called as unstable, it's as stable as feisty fawn, which means it's stable as hell :)
It's way faster than ubuntu, debian's repo are also great. Everything is really similiar.. You don't only use sudo ( but after few tweaks you can.. ). You just have to switch to root ( by typing 'su' and password ).
So.. to be honest, I'd recommend 'unstable' Debian Sid for everyone :)

---

### Post by juxtaposed on 2007-07-06
> Do you have any real experience with Lenny? How do you rate it's stability against Feisty and Dapper (LTS)?

I used lenny for a bit and found it to be stable. Then I used sid and found it to be stable also. But then again, Ubuntu Hoary, Breezy, and Feisty were all stable for me.

Then I switched to etch as I didn't feel like even thinking about updates :P

> ( but after few tweaks you can.. ).

And those tweaks are... Edit /etc/sudoers :)

---

