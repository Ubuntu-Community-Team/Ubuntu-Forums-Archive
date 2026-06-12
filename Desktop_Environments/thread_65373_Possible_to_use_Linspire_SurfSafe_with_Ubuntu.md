---
title: "Possible to use Linspire SurfSafe with Ubuntu?"
date: 2005-09-13
forum: Desktop Environments
---

### Post by spaceballl on 2005-09-13
Hi all! My parents had me set up a computer for my little brother who is 12 years younger than I am, and I of course put Ubuntu on it. Nothing like givin' the little bugger Linux experience at a young age :-). BUT... They want me to install a net blocking filter to just filter out the stuff that probably isn't best for an 11 year old to see (please can we not discuss the morality of blocking websites here, just the implementation). I've heard about DansGuardian, but it is pretty difficult to set up. Linspire has SurfSafe which seems RIGHT up my alley. The only problem is that it is part of their suite. Any way to use it or any way to find a similar product?

I'd even pay for it...

-Kevin

---

### Post by mlomker on 2005-09-13
I saw a number of how-to's on the Dansguardian but I've never set it up.  Is it that difficult?  Doesn't look like there's much out there.  I've seen a number of deals for downloading Linspire for free...maybe you could find one of those codes and go that way?

---

### Post by spaceballl on 2005-09-13
[QUOTE=mlomker]I saw a number of how-to's on the Dansguardian but I've never set it up.  Is it that difficult?  Doesn't look like there's much out there.  I've seen a number of deals for downloading Linspire for free...maybe you could find one of those codes and go that way?[/QUOTE]
Yeah I mean I actually used to work for Lindows so it wouldn't be a problem to get a free copy, but I'm more of an Ubuntu guy so I'd like to stick w/ that. The only problem w/ DansGuardian is that i THINK it filters via IP address. But this computer has a couple logins and I want to make sure that the rest of the accounts don't have any filtering on them. Documentation on dansguardian is pretty sparse...

---

### Post by evilghost on 2005-09-13
My wife is fixing to pop out a kid so I can completely understand where your parents are coming from.  However, because the Internet is a constant evolution of end-user trickery and new pron sites, I would take (and am goin to take) an opposite approach you are.

Instead of relying on software to keep a black-list of those sites serving up nefarious content and scantly clad women I'm going to:

1) Install Privoxy.
2) Block ALL sites.
3) Exclude sites whose content is acceptable.

I believe this is the best approach because it ensures that only explicit site definitions are allowed, such as abckids.com, disney.com, nickelodeon(sp?).com, etc.

I don't have to worry about a [http://images.google.com](http://images.google.com) search gone awry or a google search gone wrong.

I'm not sure what the best approach for you is, but I believe getting away from a rule of "Default Allow" and switching into a role of "Default Deny w/Exceptions" is the way to go and will significantly avoid the chance of a false negative, exposing your little brother to some of the most questionable of content (tubgirl, goatse, etc).

---

### Post by spaceballl on 2005-09-13
I think your approach of blocking ALL sites except for those pre-approved is a good idea for sure. And definitely effective. See the only thing is my little brother is 11 years old and he is a pretty smart little kid. Like he's in every fantasy football league you could believe and checks video game websites daily and I sorta WANT him to be able to explore and learn how to use the internet... I know i'm basically asking for trouble by doing this approach... but I feel like it could work.

I mean I don't even need the absolute elimination of ALL content I just want the nasty stuff gone and most of the bad stuff away. But the whitelist method you're using sounds pretty tempting as well... Will def think about that too.

-Kevin

---

### Post by Hairy_Palms on 2005-09-13
youh the default blacklist all is a good thing but i couldnt figure out will privoxy block all users the same.

---

### Post by xequence on 2005-09-13
Id probably say block the bad ones, not block all and unblock some.

There are much more good sites then bad out there. I really dont know about accual programs to do this though.

---

### Post by evilghost on 2005-09-13
[QUOTE=spaceballl]I think your approach of blocking ALL sites except for those pre-approved is a good idea for sure. And definitely effective. See the only thing is my little brother is 11 years old and he is a pretty smart little kid. Like he's in every fantasy football league you could believe and checks video game websites daily and I sorta WANT him to be able to explore and learn how to use the internet... I know i'm basically asking for trouble by doing this approach... but I feel like it could work.

I mean I don't even need the absolute elimination of ALL content I just want the nasty stuff gone and most of the bad stuff away. But the whitelist method you're using sounds pretty tempting as well... Will def think about that too.

-Kevin[/QUOTE]
 No problem, the only problem/fear I have, and I've seen it manifested at work (alas, I am an IT guy) is that the sheer number of adult content-oriented sites that pop-up daily and are seeded via pop-ups, trickery, and search-engine poisoning are incredible.  I've yet to find a single product, either commerical or open-source, that can effectively block all adult/bad sites **without** someone having to baby-sit the block-list almost 24x7.

Keep in mind that it only takes one site to eek past the filter and the entire filter is pretty much worthless.  Once the initial image/sexual act has been displayed on the screen it's all down-hill from there and the damage has been done regardless if the filter is say 99.9999% effective, that .00001% is enough to make the entire filter "ineffective" in the sense that it failed to block the requested content.  I think your parents would appreciate the fact knowing that without any question **all** adult/sexual/bad content is blocked and **only** good content (that you have defined) is allowed versus taking a gamble.

Using the whitelist (DENY-ALL) method is the most logical way to ensure that ALL content is blocked except the content that you have defined is allowable.  Logically it makes sense.  Lets say there's 50 sites your brother frequents.  It's it more logical to block ALL sites and allow 50 sites than make the assumption that the billions of sites out there are correctly categorized and marked as adult/sexual accordingly?  Seems to me I'd rather block billions and enable 50; it just makes sense.

I'm not trying to steer you in either direction, but I've put a great deal of thought into this for my own daughter who is on the way and am biased based on my work-experience and dedication of hobby-time (read as, I'm a big nerd).

Either way, I hope I helped and please keep us updated on the route you decide to take.

---

### Post by t1ny on 2005-09-17
What I did with my daughter when she was younger, and recomend this to everyone.  Treat the internet like a television.  MONITOR THEIR USAGE!

THere's no reason for a young child to have a computer in his bedroom, put it somewhere where you can walk past every now and again and look at the monitor, if your kid is really smart, every few minutes sit down and read things like instant messages, read the web site.  It;s soo easy.

My daughter is now 14 so I no longer worry about what she views on the internet, but I do have her computer connecting through a proxy server just so I can block MSN / Yahoo / etc etc messangers at 11:00 at night (After that she can go to sleep!) ;)

---

### Post by Hairy_Palms on 2005-09-17
seein as theirs the no sex/extremeviolence till after 9pm watershed theirs really not much point in monitoring a TV  whereas theirs no such safeguard on a computer and sex can be found at any time of the day hence the need for filters, also if your child isnt a moron they will close the window when they hear someone coming.

---

### Post by spaceballl on 2005-09-18
Okay while I appreciate the parenting advice... let's keep this to a software discussion :)


... if your daughter knew what was good for her, she'd get some http tunneling software for instant messenger :) :)

---

### Post by slaroy on 2007-02-27
I'd like to get back to the original question: Is it possible to use Linspire SurfSafe with Ubuntu? Or better yet, when will it be ported to Ubuntu? SurfSafe is the ONLY solution that I have found that cannot be bypassed by root. This is a major and important feature, one that many people would like for themselves and for their children: sometimes the sysadmin is the one who needs and wants accountability to the non-technical types in his family. Because Linspire is set to become Ubuntu-based, this should be a really, really easy thing to do for the devels, and it's something I would really like to see. This is one of only two things that are keeping me from migrating completely to Ubuntu and away from Windows XP. (The other less important obstacle is the ability to synch Thunderbird with my PocketPC, but that's another story :))

---

### Post by eric.duveau on 2008-05-26
> **slaroy said:**
> I'd like to get back to the original question: Is it possible to use Linspire SurfSafe with Ubuntu? Or better yet, when will it be ported to Ubuntu? SurfSafe is the ONLY solution that I have found that cannot be bypassed by root. This is a major and important feature, one that many people would like for themselves and for their children: sometimes the sysadmin is the one who needs and wants accountability to the non-technical types in his family. Because Linspire is set to become Ubuntu-based, this should be a really, really easy thing to do for the devels, and it's something I would really like to see. This is one of only two things that are keeping me from migrating completely to Ubuntu and away from Windows XP. (The other less important obstacle is the ability to synch Thunderbird with my PocketPC, but that's another story :))

Surfsafe is not sold any longer. It was powered by Cerberian database but Bluecoat.com (formely Cerberian) would like to produce a similar software call K9 web protection for Ubuntu. I dont know when. But if you want to encourage the development of such a software I suggest to read the following:

_[http://forums.bluecoat.com/viewtopic.php?t=3179]("http://forums.bluecoat.com/viewtopic.php?t=3179")_

---

