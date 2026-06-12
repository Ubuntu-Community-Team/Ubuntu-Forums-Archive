---
title: "whats this about?"
date: 2006-02-16
forum: Desktop Environments
---

### Post by linuxden on 2006-02-16
Hey all, whats this about, look at the description of the kernel update i get given in this update??

---

### Post by towsonu2003 on 2006-02-16
I'm not sure whether this is a gimp joke or someone busted the repos... I'd prefer #1

---

### Post by linuxden on 2006-02-16
dude defo not a gimp joke!!!! I still have it waiting for download..... going out to grab a bite to eat and can take another screen shot with time...

Man am confused....

edit: just voted for win modems outa the box... Man my laptop needs help when am away from home eth0 network...

---

### Post by towsonu2003 on 2006-02-16
pm one of the forum moderators. also specify the output of ```
cat /etc/apt/sources.list
```and of course, don't do an upgrade. I'd still prefer this to be a joke, or it's gonna make its way to digg.com or even slashdot. ;)

PS. thanks for the vote :)

---

### Post by LordBug on 2006-02-16
[QUOTE=towsonu2003]pm one of the forum moderators. also specify the output of ```
cat /etc/apt/sources.list
```and of course, don't do an upgrade. I'd still prefer this to be a joke, or it's gonna make its way to digg.com or even slashdot. ;)

PS. thanks for the vote :)[/QUOTE]
Given Digg's love affair with Ubuntu of late, I'd expect to see it there before the day is out. :)

Back on topic, I do hope that's some sort of hoax.  I don't like to think about borked repos.

---

### Post by carlosqueso on 2006-02-16
security.ubuntu.com appears to be down......could that be the reason?

---

### Post by Florob on 2006-02-16
LOL, this is the "release codename" and it's pretty straight forward, too.
soyuz had kept 2.6.12-10.27 to get in the repos so they reuploaded it as 2.6.12-10.28. Nothing dangerous.

---

### Post by christhemonkey on 2006-02-16
Just had a quick look around security.ubuntu.com
it didnt look down to me?

---

### Post by heimo on 2006-02-16
To me it looks like package maintainer had some trouble uploading and expressed his feeling on changelog.
```
zless /usr/share/doc/linux-image-2.6.12-10-386/changelog.Debian.gz
```

---

### Post by carlosqueso on 2006-02-16
[QUOTE=christhemonkey]Just had a quick look around security.ubuntu.com
it didnt look down to me?[/QUOTE] It had been...back up now :D

---

### Post by nalmeth on 2006-02-16
Um, yeah, I wouldn't like to see this when updating the kernel either. It looks very fishy, and I'm suprised the maintainer wouldn't anticipate that.

---

### Post by linuxden on 2006-02-16
So guys nothing to worry about or what? 

Am still confused as to why the maintainer would write that in the description of the kernel... 

Anyways if someone can clarify if its a hoax/busted repository or simply a maintainer goofing around....

---

### Post by Florob on 2006-02-16
[QUOTE=ubuntulifestyle]So guys nothing to worry about or what? 

Am still confused as to why the maintainer would write that in the description of the kernel... [/QUOTE]
It is not the description it is the changelog and as heimo said he probably wrote it to get rid of his frustration. You might have noticed there are also changes listed below this statements.
[QUOTE=ubuntulifestyle]Anyways if someone can clarify if its a hoax/busted repository or simply a maintainer goofing around....[/QUOTE]
IMHO this is just a maintainer "goofing around".

---

### Post by carlosqueso on 2006-02-16
it seems to be a maintainer upset at launchpad.....this: [http://ubuntuforums.org/showthread.php?t=130908](http://ubuntuforums.org/showthread.php?t=130908) coincides with the release date and the version numbering, so I think you should be okay.

---

### Post by linuxden on 2006-02-16
[QUOTE=Florob]It is not the description it is the changelog and as heimo said he probably wrote it to get rid of his frustration. You might have noticed there are also changes listed below this statements.

IMHO this is just a maintainer "goofing around".[/QUOTE]

Still Not going to update quite yet, gonna need a little more convincing than that...

Isnt this suspicious? Does anyone else feel its unsafe to update?

And above all does everyone else get this update available to them??

How could we go about getting confirmation from Ubuntu.com??

---

### Post by Florob on 2006-02-16
If you have to do it just go to #ubuntu-devel and ask Ben Collins about it.

---

### Post by nalmeth on 2006-02-16
If you do talk to ubuntu-devel, please post what's up with this.

If it were me, I would not update until I knew. If the frustration was vented in a way that did not look like a lot of email's that we all get from time to time, it might be different.

---

### Post by towsonu2003 on 2006-02-16
I wouldn't update it either. too fishy and unprofessional. that's the kernel, not some firefox extension. I don't see the updates yet, so I can't act. But if that description appears in my update-notifier, I will file a bug, contact a forum staff, and send a link to this thread in the mailing list. 

I can't use chat.... firewall of isp blocks anything you can think of. 

Let us know what's going on -thanks

PS. It's so tempting to put this in digg argh <- joke.

---

### Post by jobezone on 2006-02-16
Unfortunately, this reasoning, that looking professional means it's ok, goes right into what Kevin Mitnick says of social engineering.

---

### Post by linuxden on 2006-02-16
[QUOTE=towsonu2003]I wouldn't update it either. too fishy and unprofessional. that's the kernel, not some firefox extension. I don't see the updates yet, so I can't act. But if that description appears in my update-notifier, I will file a bug, contact a forum staff, and send a link to this thread in the mailing list. 

I can't use chat.... firewall of isp blocks anything you can think of. 

Let us know what's going on -thanks

PS. It's so tempting to put this in digg argh <- joke.[/QUOTE]

Will take care of it tomorrow... I have to spend my evenings with gf and not Linux... Otherwise i get into trouble... lmao!!!

Its fishy and i personally dont want to update anything this strange... It is the Kernel....

Anyways have a nice evening all...

---

### Post by Florob on 2006-02-16
Maybe somebody would finaly explain to me what is so "fishy" about this? I really don't get you...

---

### Post by Lord Illidan on 2006-02-16
[quote=jobezone]Unfortunately, this reasoning, that looking professional means it's ok, goes right into what Kevin Mitnick says of social engineering.[/quote]

Agreed, but again, when it something as crucial as your kernel, you don't want any joking around, I am sure..

---

### Post by towsonu2003 on 2006-02-16
here I go: **bug report** [https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/31698](https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/31698)
I was too lazy to do the rest. 

What's so fishy about this is that the chanelog of your prospective kernel is screaming "Mommy Mommy"... I don't want some "kid"ding kernel in my system. Even MS doesn't do that with its kernels... 

I agree with the Mitnick comment, but the phishing scams started with erronuously written emails. Now they use similar domain names, valid certificates, correct grammar, and look-a-like emailing format. Things has to start from somewhere in order to develop.

The first OS  X virus for instance it is fishy, poorly written, and very simple. But yet, it is a first... And search wikipedia for the first fishy Windows virus (too many) ;)

---

### Post by Florob on 2006-02-16
So I just asked on #ubuntu-devel and (suprisingly) they told me it was a developer attempting to be funny.
> 
(23:08:09) Florob: Sorry, to bother all of you, but could somebody possibly clear up the issue in the following forum thread, which keeps people from updating: [http://ubuntuforums.org/showthread.php?t=131445](http://ubuntuforums.org/showthread.php?t=131445)
(23:09:43) Seveas: Florob, it's an attempt of one of the developers to be funny &#12484;
(23:09:50) janimo hat den Raum verlassen (quit: "Download Gaim: http://gaim.sourceforge.net/").
(23:10:04) ogra hat den Raum verlassen (quit: "Leaving").
(23:10:18) HiddenWolf: Florob: it says "my previous upload did not work, so let's do it again"
(23:10:36) HiddenWolf: Florob: where "did not work" means "did not hit the archive"
(23:10:41) Florob: I know that and posted it but nobody wants to believe it ;)

---

### Post by linuxden on 2006-02-16
[QUOTE=Florob]Maybe somebody would finaly explain to me what is so "fishy" about this? I really don't get you...[/QUOTE]

You dont find updating your kernel to a kernel with that kind of message in the changes fishy??

 "MOMMY MOMMY! Soyuz eated my previous upload!! MOMMYYYYY!!!!!"

    aka: "The let reupload 10.27 and hope.."

I find it absolutely fishy and will not update until it has been clarified...
Unfortunatetly i dont have time tonight... am already escaping every 15 minutes to check for posts in this topic...

---

### Post by Lord Illidan on 2006-02-16
I agree 100% with the previous post. There is nothing wrong with joking, but I'd like people to be serious when it concerns critical updates like system updates. A message is enough to get anyone suspicious.

---

### Post by towsonu2003 on 2006-02-16
[QUOTE=Lord Illidan]I agree 100% with the previous post. There is nothing wrong with joking, but I'd like people to be serious when it concerns critical updates like system updates. A message is enough to get anyone suspicious.[/QUOTE]
in bug report [https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/31698](https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/31698) it seems developers are pretty okay with jokes. I will be expecting teh next kernel to "be dancing with joy" (in caps if possible) ;)

---

### Post by jobezone on 2006-02-16
The point is, if your computer got hacked, or ubuntu's servers did, and you got a professional-looking changelog like this:

> linux-image-2.6.*.* (ubuntu1) breezy; urgency=low

  * Sync with Debian.
  * debian/control:
    - updated the Build-Depends for grub and lilo.

 -- António Variações <antvari@canonical.com>  Fri,  17 Feb 2006 00:03:06 +0200

you would be confident to install it, not knowing it was a trojan/whatever. But it will never be safe if you stick to this principle. In fact, we all take a leap of faith on ubuntu's ability to safeguard it's servers, and if one day those safeguards crack, you won't notice it through the changelog. 

There is already in debian unstable some basic gpg support for apt, and more is to be added in the future (and used by ubuntu, I'm sure). How it works, I don't know...

---

### Post by towsonu2003 on 2006-02-16
[QUOTE=jobezone]
There is already in debian unstable some basic gpg support for apt, and more is to be added in the future (and used by ubuntu, I'm sure). How it works, I don't know...[/QUOTE]
This is getting a little frustrating for me. So I'll try to be brief. I have four interrelated perspectives on this:

1. From now on, end users will not be alarmed by unexplained anomalities in apt-get. They will think that it's another joke from the developers. This is a security hole right there. The fact that no one came up with a way to exploit it does not mean that it cannot be exploited. 

2. The Linux kernel is a very serious business. Maintaining a distro that appeals to *so* many people is even more serious. The Ubuntu kernel isn't being uploaded to some unknown server so that a couple of linux geeks can laugh at it. It is being downloaded and used by end users, who expect the product they are using to be maintained with the **utmost seriousness** with an emphasis on **perfection**. This argument is very simple. 

3. What this incident thought me is that Ubuntu has a group of developers who are being supported by a rich guy who isn't supervising them close enough and thus they are in such a relaxed state of mind that they are "joking around" with the core of their own project. Their voluntary status is, at this point, irrelevant. To me, the fact that my update-notifier is sitting in the corner of my desktop with a remark "mommy, someone ate my previous upload" is simply unacceptable. I cannot install a kernel knowing that its maintainer is not taking his / her job seriously. 

4. A maintainer who does not take her job seriously, but takes it for granted, is a security hole waiting to be exploited. 

A side note: Keeping in mind that MS Windows tend to be of lower quality than Linux, if we saw this during an automatic Windows update, we would be discussing this in Slashdot. I see no difference, other than number of end users.

---

### Post by cwaldbieser on 2006-02-16
[QUOTE=towsonu2003]This is getting a little frustrating for me. So I'll try to be brief. I have four interrelated perspectives on this:

1. From now on, end users will not be alarmed by unexplained anomalities in apt-get. They will think that it's another joke from the developers. This is a security hole right there. The fact that no one came up with a way to exploit it does not mean that it cannot be exploited. 

2. The Linux kernel is a very serious business. Maintaining a distro that appeals to *so* many people is even more serious. The Ubuntu kernel isn't being uploaded to some unknown server so that a couple of linux geeks can laugh at it. It is being downloaded and used by end users, who expect the product they are using to be maintained with the **utmost seriousness** with an emphasis on **perfection**. This argument is very simple. 

3. What this incident thought me is that Ubuntu has a group of developers who are being supported by a rich guy who isn't supervising them close enough and thus they are in such a relaxed state of mind that they are "joking around" with the core of their own project. Their voluntary status is, at this point, irrelevant. To me, the fact that my update-notifier is sitting in the corner of my desktop with a remark "mommy, someone ate my previous upload" is simply unacceptable. I cannot install a kernel knowing that its maintainer is not taking his / her job seriously. 

4. A maintainer who does not take her job seriously, but takes it for granted, is a security hole waiting to be exploited. 

A side note: Keeping in mind that MS Windows tend to be of lower quality than Linux, if we saw this during an automatic Windows update, we would be discussing this in Slashdot. I see no difference, other than number of end users.[/QUOTE]

Wouldn't a simple way to verify this have been to check the md5 hash?  apt-get normally does this for you automatically, but you can go to [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")
and verify the md5 hash there against the last bit from 
```

$ sudo apt-get --print-uris <package>

```

As for the developers having a bit of fun-- it seems like it was pretty innocuous.  Kinda like the April Fools splash screen they did once.

Everybody needs a good laugh once in a while.  This doesn't seem like it was excessive, and in the worst case, the folks who were on their toes and noticed just delayed getting a kernel update for a few hours.

I have to say that the joke was also pretty mild compared to some office humor I have seen.

---

### Post by jobezone on 2006-02-17
[QUOTE=towsonu2003]
A side note: Keeping in mind that MS Windows tend to be of lower quality than Linux, if we saw this during an automatic Windows update, we would be discussing this in Slashdot. I see no difference, other than number of end users.[/QUOTE]

You're probably right (well, _I_ wouldn't be discussing it. It would be funny and interesting, but pretty wortheless to discuss, other than to say, "there are still some hackers inside Microsoft!")

This is one feature(bug?) of free software development I enjoy, but I see your point of lowering our standards for aceptable behaviour of update-manager.

But it still is solely based on a humorous _but_ informative changelog (even if it wasn't that funny :) usually typical outside linux kernel packages, and hell, even pretty much typical inside the kernel's development.

---

### Post by Florob on 2006-02-17
[QUOTE=towsonu2003]This is getting a little frustrating for me. So I'll try to be brief. I have four interrelated perspectives on this:

1. From now on, end users will not be alarmed by unexplained anomalities in apt-get. They will think that it's another joke from the developers. This is a security hole right there. The fact that no one came up with a way to exploit it does not mean that it cannot be exploited. [/QUOTE]
So what if somebody exploits such a theoretical hole and doesn't put jokes in the packages? This point is not valid at all.
[QUOTE=towsonu2003]
2. The Linux kernel is a very serious business. Maintaining a distro that appeals to *so* many people is even more serious. The Ubuntu kernel isn't being uploaded to some unknown server so that a couple of linux geeks can laugh at it. It is being downloaded and used by end users, who expect the product they are using to be maintained with the **utmost seriousness** with an emphasis on **perfection**. This argument is very simple.[/QUOTE]
I personally don't want it to be maintained with utmost seriousness. Of course I don't want them to not take their work serious etc., but this doesn't meen they may never make a joke when talikng to somebody, writing changelogs etc. It doesn't worsen package quality or anyting.
[QUOTE=towsonu2003]3. What this incident thought me is that Ubuntu has a group of developers who are being supported by a rich guy who isn't supervising them close enough and thus they are in such a relaxed state of mind that they are "joking around" with the core of their own project. Their voluntary status is, at this point, irrelevant. To me, the fact that my update-notifier is sitting in the corner of my desktop with a remark "mommy, someone ate my previous upload" is simply unacceptable. I cannot install a kernel knowing that its maintainer is not taking his / her job seriously.[/QUOTE]
Jokeing or expressing anger doesn't have anything to do with taking your job seriously. If it did I personally don't know anybody who takes his job seriously.

[QUOTE=towsonu2003]4. A maintainer who does not take her job seriously, but takes it for granted, is a security hole waiting to be exploited.[/QUOTE]
Good that there are no such maintainers.

[QUOTE=towsonu2003]
A side note: Keeping in mind that MS Windows tend to be of lower quality than Linux, if we saw this during an automatic Windows update, we would be discussing this in Slashdot. I see no difference, other than number of end users.[/QUOTE]
Another side note:
An exploit like this is actually not possible, because all packages are GPG signed and the signatures to check their validity are installed on your system with the Install CD.

---

### Post by Irony on 2006-02-17
I get that Mommy message as well! Probably okay as my sources list is the official one;

[PHP]#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## Backports
#deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse[/PHP]

---

### Post by linuxden on 2006-02-17
[QUOTE=Florob]So what if somebody exploits such a theoretical hole and doesn't put jokes in the packages? This point is not valid at all.[/QUOTE]

No your right someone could just crack into the repository and not put such a blatant joke on the kernel and then people would download automaticaly without questioning it. 

But that doesnt excuse anything, the kernel is the kernel !! You seem to enjoy the fact that some people felt worried to install the packge...

When i download an update for the core of my OS, i expect it to be as serious as any other OS, M$, Mac os X, Solaris, etc etc...( not necessarily in that order!)

> I personally don't want it to be maintained with utmost seriousness. Of course I don't want them to not take their work serious etc., but this doesn't meen they may never make a joke when talikng to somebody, writing changelogs etc. It doesn't worsen package quality or anyting.

Isn't that a contradiction?? You dont want them to be serious when maintaining, but dont want them to be not serious when working...?? Mmmmm...

Oh and of course the Maintainers should be able to joke when talking!!

lmao!!

But IMHO when writting changelogs they should keep some kind of formality...

> another side note:
An exploit like this is actually not possible, because all packages are GPG signed and the signatures to check their validity are installed on your system with the Install CD.

So in other words a newly developped package that did not exist when i installed my Ubuntu/Debian, can not be installed because it doesnt not have a pre-installed GPG key on my computer??

Thats far fetched... For sure GPG can stop someone from tinkering with the Official kernel, the same as checksums but it doesnt stop someone uploading another package with malicious intent...

Anyways the bottom line is that there seems to be 2 schools here the ones that dont mind taking blatant risks with their computers ie instaling a non serious package, and the ones that need to be conned into installing a bogus but real looking package (ie minus the joke)

 I myself would prefer the ubuntu Maintainers to stay serious with the changelog, Just my 2 cents...

---

### Post by Florob on 2006-02-17
> **ubuntulifestyle]No your right someone could just crack into the repository and not put such a blatant joke on the kernel and then people would download automaticaly without questioning it. 

But that doesnt excuse anything, the kernel is the kernel !! You seem to enjoy the fact that some people felt worried to install the packge...[/QUOTE]
I'm not really enjoying it, but I have to admit I had a good laugh when I read the initial post, because it is IMHO really way too paranoid. (Not meant offensive)

[QUOTE=ubuntulifestyle]
When i download an update for the core of my OS, i expect it to be as serious as any other OS, M$, Mac os X, Solaris, etc etc...( not necessarily in that order!)

Isn't that a contradiction?? You dont want them to be serious when maintaining, but dont want them to be not serious when working...?? Mmmmm...[/QUOTE]
More or less, I think they can/should have fun and joke while developing (so basically on meetings, irc, while coding, etc), but they shouldn't have a "oh let's just try it this way it might work" unserious attitude, that towsonu2003 fears.
[QUOTE=ubuntulifestyle]
Oh and of course the Maintainers should be able to joke when talking!!

lmao!!

But IMHO when writting changelogs they should keep some kind of formality...[/QUOTE]
Well, they do as I said before there is a normal changlog below this "suspicious" lines, but I can't find a reason to not come up with funny release names to put in the ChangeLog. This is done in so many places/projects. Besides people thinking something got hacked (a thing I personally had never thought of). But you can't force deveopers to not do it, because some people are a bit paranoid (which is a good thing to be when using a computer, so this is more me not being paranoid enough  said:**
> 
So in other words a newly developped package that did not exist when i installed my Ubuntu/Debian, can not be installed because it doesnt not have a pre-installed GPG key on my computer??
No, gpg signing is done on a per developer base (or may be per repository base, can't remember which) not on a per package base (which wouldn't be possible anyway).

[QUOTE=ubuntulifestyle]
Thats far fetched... For sure GPG can stop someone from tinkering with the Official kernel, the same as checksums but it doesnt stop someone uploading another package with malicious intent...[/QUOTE]
Of course someone could (assuming an exploitable whatever) upload a malicious package, but he can't have the privat key of a developer, so apt (this is not only apt-get, but all tools dealing with packages) will complain and give you at least a warning that installing this package is insecure.

Disclaimer: This is my understanding of the working of apt. It may contain errors or misinformation, but I think it's correct.

---

### Post by jobezone on 2006-02-17
[QUOTE=ubuntulifestyle]
Anyways the bottom line is that there seems to be 2 schools here the ones that dont mind taking blatant risks with their computers ie instaling a non serious package, and the ones that need to be conned into installing a bogus but real looking package (ie minus the joke)[/QUOTE]

Well, I'm on a third school, where people take *real* precautions so their system s are not breached/modified, and that their sources.list contain only oficial or otherwise trusted repository lines.

And then take faith that ubuntu people won't screw up :) which has happened to me once when update-manager upgraded my linux (in Hoary times, and it made the system unbootable).

---

### Post by linuxden on 2006-02-17
Jobe, 

I'd put you in the 2nd school... You are taking precautions, but you could get conned into updating something fishy... (we all can...)

But hey if a 3rd school is cool, then why the heck not??

lol

---

### Post by Irony on 2006-02-19
I've updated the kernel and it all works fine.

---

### Post by towsonu2003 on 2006-02-19
[QUOTE=Irony]I've updated the kernel and it all works fine.[/QUOTE]
I thought it would start screaming "mommy towsonu ate my kernel" in one hour intervals but it doesn't :(
[/sarcasm]

---

### Post by linuxden on 2006-02-19
Towsonu,

Yours didnt scream at all?? What dissappointment!!! Mine was screaming all night ... :goofy:

---

### Post by linuxden on 2006-02-19
Oh and to close the thread, Fabio Massimo Di Nitto has answered the launchpad....

Fabio Massimo Di Nitto:

> "If the changelog does not report changes, is because there are none.

A reupload because the infrastructure did fail is normal operation.

And no i was not drunk at all. Repos are not hacked."

Closed??

---

### Post by towsonu2003 on 2006-02-19
as long as they are not drunk,
[quote=ubuntulifestyle]Closed??[/quote]closed to me... although I'm open to more jokes on this. 


Though I'm intrigued that I downloaded 45MB in dialup for no changes :confused: [quote=Fabio Massimo Di Nitto]If the changelog does not report changes, is because there are none[/quote]S/he possibly means there was no change from 1st upload to 2nd upload. :rolleyes:

---

### Post by linhgb on 2006-02-26
We have a lot of systems here running Ubuntu and I really don't appreciate this kind of humour (it's not even funny, even if it weren't in the kernel changelog). I want to read about the actual **changes**  in the changelog, not someone biatching about something nobody else outside his loop gets. If you want to post your funny comments, start a blog and write whatever you like there.

---

### Post by linuxden on 2006-02-26
The thread was Dead... Also are you using Ubuntu for a major network?? What field do you work in?? A few Hundred Ubuntu workstations... WOW!!!! I would love to see that!!!

---

### Post by linhgb on 2006-02-26
Sorry to dig it up, but it's only 6 days old, and the message is still there, so to me it's not quite dead yet.

As for the many Ubuntu systems, they are for lab machines and scientific workstations at a university department. Other departments here also have heaps of Ubuntu machines.

Don't get me wrong, I'm all for a bit of fun. For example, I enjoy the quirky messages that GAIM has for their update RSS feed. However, when it comes to changelogs, I need real, useful info there, and especially with a core component - hell it doesn't get any more serious than the kernel! - I'd like to see some professionalism. 

So please, remove that stupid message.

---

### Post by towsonu2003 on 2006-02-26
[QUOTE=linhgb]
So please, remove that stupid message.[/QUOTE]
You are gonna have to refer back to the bug report, reopen it, and comment on it... they don't look here...

---

