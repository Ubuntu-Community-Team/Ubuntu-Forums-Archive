---
title: "Gripe about help in the server subforum"
date: 2008-10-08
forum: Forum Feedback &amp; Help
---

### Post by Krupski on 2008-10-08
OK, I'm not a mod or admin. And, I'm a newbie. Sorry if I'm stepping on toes, but here it goes anyway.

I've learned a lot about Linux and Ubuntu here and for that I say thanks to all who helped me.

Now, for my gripe:

I have seen a lot or replies for help with cryptic replies like "see man your-problem" or links to web pages.

Being a LONG time computer user, amateur programmer but Linux newbie, I fully understand how a beginner feels.

Even answers like "Go into Nautilus and do this or that" leaves the newbie scratching his head and saying "huh???".

From personal experience at being a Linux newbie, I respectfully suggest the following step-by-step format when posting "help" replies:

========================== sample ==========================

(1) Show code (if necessary)
(2) EXPLAIN what that cryptic line means.
(3) Highlight important parts of code if appropriate.
(4) Don't assume that the user knows anything (and insert an apology if you think over-simplification might be insulting).

Here's an example of what I mean... how to add a custom message to VSFTPD (example post):

Adding a custom message to VSFTPD is easy. At a terminal, run an editor and edit the '/etc/vsftpd.conf' file:

```

sudo nano /etc/vsftpd.conf

```

This line means "super user do", nano (editor), the file "/etc/vsftpd.conf" which is the configuration file for VSFTPD.

Next, look for the line that looks like this (about 1/2 way down):

```

# You may fully customise the login banner string:
ftpd_banner=

```

Add anything you like as a banner (note ADDITION in red):

```

# You may fully customise the login banner string:
ftpd_banner=[COLOR="Red"]**Linux is awesome!!!**[/COLOR]

```

Save your changes by typing "control-o" in the nano editor.

Exit the editor by typing "control-x".

Taa-daa! That's it!

========================== sample ==========================


So much for my 2 cents!  :)

-- Roger

---

### Post by cdenley on 2008-10-08
Linux newbies have no business running servers. If they don't know what the command "sudo" does, they need to learn more about linux basics before they put a server online. If they don't understand what they are doing, they put themselves, and possibly their users, at risk.

I'm not going to explain every command I post. It would be much more efficient for me to explain how to find out what a command does. Why bother explaining a command when the man page does a much better job? You shouldn't rely on a posters explanation of any commands, anyway. You should never run any commands which you don't understand unless you have researched it from a reliable source, such as the man page.

---

### Post by windependence on 2008-10-08
No offense but if I did that for everyone I help, I would never be able to get to as many people as I do. 

Be glad it's 2008 and not 1998, because back then you would have gotten an "RTFM" with a disgusted attitude, not from me but from most of the Linux community.

It isn't perfect, but it's tons better than it was. Sometimes, I can understand why the "experts" get upset. 90% of my answers are a simple google search. It would be nice if some folks would look first before posting. There's tons of information out there, and it's not hard to find. I could use my (volunteer) time better working on truly difficult problems for people.

-Tim

---

### Post by 47_MasoN_47 on 2008-10-08
I agree with this guy.  Anyway, who says the n00b is running a production server?  Maybe they are just learning how to do it by playing with one at their house.  That's what I did.

Frankly, man pages suck half the time.  They have all this extra crap and are filled with meaningless jargon and cryptic terminology that would give any average person a headache.

I think people are just lazy who post stuff like "look at the readme file."  What a huge load of BS.

It would be awesome to see people post more descriptive and helpful posts like this guy's sample.

[Here's a thread where I asked a question and got a great reply.]("http://ubuntuforums.org/showthread.php?t=869219")  It would be awesome if everyone gave answers like this guy.

---

### Post by patrickballeux on 2008-10-08
Totally agree with Krupski!

Often, solutions are geekie when a simple solution can be provided.  I know people want to help, but you have to make sure that it really helps and that you are not just showing your knowledge.


There is a bad reputation about the linux people about being arrogant.  And some times, sadly, this reputation is true.

Why should a newbie "knows" about man page, or where to look about the information?  He/She is a newbie, so there a learning curve for them and since they often come from the Windows environment, it is harder for them.

If you consider that helping someone on an easy problem is a waste of time and that you would be more useful helping on more complicated issues, then your did not understand the concept of helping.

Don't be blinded by your own glory, think that you can help and educate (nicely) a newbie to become an asset to the linux community.

My 2 cents.

---

### Post by Krupski on 2008-10-08
> **cdenley said:**
> Linux newbies have no business running servers.

I disagree. "Linux newbies" can and should run anything they please.

How is one to learn otherwise?

I started out as a Linux newbie. I don't profess to be an expert, but I have learned an awful lot.

And I started with SERVER... because that's what I wanted to do... convert a home file server from Windows to Linux.

It was rough going, I made lots of mistakes and made a bazillion re-installs.

I posted a ton of questions here and learned a lot. I finally got my system running the way (that I think) I want it... thanks in large part to all the help I received here.

Recalling how lost I was when I started, I know exactly how someone feels when they're told "just read the man page".

To a newbie, that is NO HELP AT ALL.

Many of the things I setup were done by following "simplistic" step-by step instructions until I finally said "Oh! NOW I get it!".

THEN, re-reading man pages makes more sense. Now the "-f" switch actually means something, rather than "what the heck is that?".

My philosophy is either help or refrain from posting... and that's exactly what I do.

I won't waste my time or the original poster's time by saying "read the docs" and clicking "Submit Reply".

Besides, us Linux users should project a more warm, helpful image than the "other guys" in Redmond do... ;-)

Respectfully...

-- Roger

---

### Post by windependence on 2008-10-08
> **patrickballeux said:**
> Totally agree with Krupski!

Often, solutions are geekie when a simple solution can be provided.  I know people want to help, but you have to make sure that it really helps and that you are not just showing your knowledge.

Well, Linux, especially on the SERVER side IS geeky. That's why there is no GUI in the server edition. That certainly does not mean you can't run a server on the desktop edition, in fact, if you are a n00b and want to "play" and learn, you should probably start there anyway.


> **patrickballeux said:**
> There is a bad reputation about the linux people about being arrogant.  And some times, sadly, this reputation is true.

Trust me, this has changed DRAMATICALLY in the last ten years. The problem here is many don't want Linux "dumbed down" to be just another Windoze clone.

> **patrickballeux said:**
> Why should a newbie "knows" about man page, or where to look about the information?  He/She is a newbie, so there a learning curve for them and since they often come from the Windows environment, it is harder for them.

Even I don't use man pages unless I need to remember some switch or something. There are TONS of resources available on the web, many of them are step by step and geared toward new people to Linux. What aggravates me is when they don't even bother looking which is obvious to me when I get a full page of google hits when searching. I mean c'mon, you don't have to be a brainiac to do a simple search.

> **patrickballeux said:**
> If you consider that helping someone on an easy problem is a waste of time and that you would be more useful helping on more complicated issues, then your did not understand the concept of helping.

Well you are referring to my comment about working on difficult problems and you should not be putting words in my mouth. I NEVER said anywhere in my post it was a waste of time to help on simple problems. Read above about people who don't even TRY to look for a solution before posting. 

> **patrickballeux said:**
> Don't be blinded by your own glory, think that you can help and educate (nicely) a newbie to become an asset to the linux community.

My 2 cents.

I am humbled every day by what I DON'T know. Sadly, some people will never be able to have what it takes to be an asset to the Linux community and should probably stick with Windoze.

-Tim

---

### Post by Krupski on 2008-10-08
> **47_MasoN_47 said:**
> I think people are just lazy who post stuff like "look at the readme file."

There are also lazy USERS who can't or won't bother to even Google for the info.

People like that I have little tolerance for.

But, think about a newbie being told "read the man page".

What the heck is a "man page"? Is that different than a "woman page"?

OH... "man" is short for "manual", but what on earth does "-f" mean and why did it fail when I tried "-F"?

Hmmm... case must be important.

How to make a directory? "md"? Nope, that didn't work... what now?

See? THAT is literally how a newbie sees it.

I had the good fortune of "coming up" through computer history from the days of home made wire-wrap and toggle switch computers.

I'm comfortable with them, and new concepts "click" easily.

But, some people only know "point and click Windows".

*WE* need to not only help them, but make them feel comfortable and confident and say "yeah darn it, I CAN learn this".

If we just say "read the man page moron", they will go back to Windows and we'll NEVER see them again!

-- Roger

---

### Post by windependence on 2008-10-08
> **Krupski said:**
> There are also lazy USERS who can't or won't bother to even Google for the info.

People like that I have little tolerance for.

But, think about a newbie being told "read the man page".

What the heck is a "man page"? Is that different than a "woman page"?

OH... "man" is short for "manual", but what on earth does "-f" mean and why did it fail when I tried "-F"?

Hmmm... case must be important.

How to make a directory? "md"? Nope, that didn't work... what now?

See? THAT is literally how a newbie sees it.

I had the good fortune of "coming up" through computer history from the days of home made wire-wrap and toggle switch computers.

I'm comfortable with them, and new concepts "click" easily.

But, some people only know "point and click Windows".

*WE* need to not only help them, but make them feel comfortable and confident and say "yeah darn it, I CAN learn this".

If we just say "read the man page moron", they will go back to Windows and we'll NEVER see them again!

-- Roger

Roger,

I know I've helped you in the past and you at least try to find the information. But the example about making a directory - well if you do a search for "Linux Commands" or "learning Linux" on Google, there are tons of cheat sheets even with the DOS equivalents on them. I would much rather help you with your DNS problem than post yet another 5 links on basic commands, see my point?

-Tim

---

### Post by cdenley on 2008-10-08
I've made posts with man commands because I assume they didn't think to look there or didn't know about man pages. Sometimes I tell them which section to look at if it is a very big manpage. Some are larger and more complicated than others. I will also sometimes provide an explanation if the manpage doesn't seem to quite cover it. I post man commands because it encourages new users to use references before posting. A man page will often have much more information than you need, but at least you will learn what the command can do while searching for the relevant section. I've actually learned a lot this way. If you are confused by "cryptic terminology", google it. When you learn the terms relevant to your problem, it becomes easier to find a solution and explain your problem to others.

I also post links to guides or how-tos sometimes. I'm not arrogant about it, just trying to give them the resources that would solve their problem. I often find solutions for other people's problems in man pages or guides, so instead of paraphrasing or copying and pasting, I simply direct them to where I found their answer.

I sometimes make very detailed posts, and explains things clearly, but I usually don't. I try to gauge the poster's level of experience, but if I can't, I just assume they are average linux users. If they ask for a better explaination, I give it to them. I'm not arrogant, I just don't waste time writing a detailed how-to unless it's necessary.

> 
Anyway, who says the n00b is running a production server? Maybe they are just learning how to do it by playing with one at their house.

Good point. Hands-on experience is the best way to learn. Just keep it off the net. Virtualization works well for this.

---

### Post by 47_MasoN_47 on 2008-10-08
[QUOTE=Krupski]There are also lazy USERS who can't or won't bother to even Google for the info.[/QUOTE]
I definitely agree that people who don't even try to help themselves don't deserve to be helped.

BTW Mikhail Kalashnikov is one of the greatest men ever.

---

### Post by cariboo on 2008-10-08
NM 

New Rule: Nover post in a thread when your mad about something else. :)

Jim

---

### Post by cdenley on 2008-10-08
> 
There are also lazy USERS who can't or won't bother to even Google for the info.

What annoys me is when posters skim through or even past my post. I usually respond with "read my post" or "re-read my post". Sometimes I even repeat myself, or occasionally I might ignore the thread. This seems to happen often. Maybe when people pay such little attention to my posts, I see less reason to go into as much detail as the sample response.

---

### Post by cariboo on 2008-10-08
Ignore my previous post, what I actually wanted to say is that we are relatively lucky here in these forums. 

I started playing with *BSDs thanks to Tim, I went to look for an answer on how to disable ipv6 in netBSD because I know nothing about it and I wasn't able to update any packages because of it. The answers I saw in some of the forums ranged from down right ridicule to no replies at all. For anybody that would tend to scare them away. I eventually tried Dragonfly which during the setup allows you to disable ipv6.

So now I have two choices:
1. to continue on with Dragonfly
or
2. learn all I can about ipv6

Jim

---

### Post by joewilliams on 2008-10-08
Perhaps we need to remember that part of the 'Open Source Software' culture is the idea that support is like a **self-help** group.  It is expected that one will search first and then ask.

Sometimes helping in forums feels like the guy standing by the door with a big sign that says EXIT, there's a long line of people, each one asking where's the exit after you just told the guy in front of him and pointed to the sign.:)

---

### Post by windependence on 2008-10-08
> **cariboo907 said:**
> Ignore my previous post, what I actually wanted to say is that we are relatively lucky here in these forums. 

I started playing with *BSDs thanks to Tim, I went to look for an answer on how to disable ipv6 in netBSD because I know nothing about it and I wasn't able to update any packages because of it. The answers I saw in some of the forums ranged from down right ridicule to no replies at all. For anybody that would tend to scare them away. I eventually tried Dragonfly which during the setup allows you to disable ipv6.

So now I have two choices:
1. to continue on with Dragonfly
or
2. learn all I can about ipv6

Jim

Jim, I'm not sure about NetBSD, but in FreeBSD you can disable it in the installer. I'm sure there is an easy way in NetBSD also. I'll find out and let you know. Did you try daemonforums.com?

-Tim

---

### Post by patrickballeux on 2008-10-08
> **windependence said:**
> Well, Linux, especially on the SERVER side IS geeky. That's why there is no GUI in the server edition. That certainly does not mean you can't run a server on the desktop edition, in fact, if you are a n00b and want to "play" and learn, you should probably start there anyway.


So how do you expect a newbie to understand geek language?  That newbie wants to learn, so let's give him the tools to learn.  If you just give him the command or say "See the man page", you are not helping that person.

> 
Trust me, this has changed DRAMATICALLY in the last ten years. The problem here is many don't want Linux "dumbed down" to be just another Windoze clone.


I read forum everywhere, and yes, this has changed, but they are still some zealots who take their computer for a temple.  Simple does not mean "dumb".  There are several ways to do things and none is better than the other, it is only different...  Windows is not evil, it is just not adequate for our needs.

> 
Even I don't use man pages unless I need to remember some switch or something. There are TONS of resources available on the web, many of them are step by step and geared toward new people to Linux. What aggravates me is when they don't even bother looking which is obvious to me when I get a full page of google hits when searching. I mean c'mon, you don't have to be a brainiac to do a simple search.


Some a just lazy, and I agree with you that we should not waste our free time on them, but some other are just ignorant that they can simply search for their information.  A few example, a few explanation and they're happy.  Give them at least the tools to understand.  Simply say "Google for it" won't really help them.  A few links, a few examples...

> 
... a waste of time to help on simple problems. Read above about people who don't even TRY to look for a solution before posting. 


My apologies then, but from the tone you of your writing, that's how I understood it.  

> 
I am humbled every day by what I DON'T know. Sadly, some people will never be able to have what it takes to be an asset to the Linux community and should probably stick with Windoze.


How can you judged if someone cannot be an asset to the linux community? Because he is not an expert with the command line or able to find quickly some info?

Are you telling me that you can become a linux user only if you are accepted by the community?  This is not a religion or a being good or bad.  Linux is for everybody, free and open!  If some are willingly not doing the effort of learning once they have the tools, natural selection will take care of them.

Don't confuse lazyness and ignorance.  Good for you if you know that you don't know, but for some other, they must learn that they have to learn.

"Sans rancune" (No offense intended)

---

### Post by patrickballeux on 2008-10-08
> **joewilliams said:**
> Sometimes helping in forums feels like the guy standing by the door with a big sign that says EXIT, there's a long line of people, each one asking where's the exit after you just told the guy in front of him and pointed to the sign.:)

That's the human factor showing...  It it the same a when you are asked if you are hurt when your bleeding...

Simply point the sign again, and move to the next one... :guitar:

---

### Post by cariboo on 2008-10-08
Tim

Actually I was planning on trying FreeBSD next when I get some spare time, It looks like the BSD's are the same as Linux, try them and then use the one you are most comfortable with.

Jim

---

### Post by Krupski on 2008-10-08
> **windependence said:**
> Roger,

I know I've helped you in the past and you at least try to find the information.

Yes, you have helped me a awful lot (thank you!) and yes I do try to find the answer first myself.

I have stumbled across many step-by-step instructions for doing certain things that, now, looking at them, are absurdly simple. 

But, when I first did them, I was in the dark and just typing verbatim what I saw.

Anything more complex than that... and I wouldn't have known where to begin.

I think, as a community, we CAN and SHOULD be friendlier, more patient and more helpful than those "other" people.

Not only because it's a "good idea", but because I know first hand how helpful "hand holding" can be when first learning.

Linux has a steep learning curve. It gets easier with time, but newbies need help with those first steps.

If they fall off, they may never come back again. Hopefully, we can avoid that.

-- Roger

---

### Post by Krupski on 2008-10-08
> **patrickballeux said:**
> So how do you expect a newbie to understand geek language?

To me, the term "geek" conjures images of a socially inept, freckle faced nerd that plays with his computer all day and lives at home at age 40.

I disagree. I know how to program in ASM, C, BASIC and even build my own microcontrollers and circuits. I also know how to run a metal shop and "build things", I can read blueprints, I can fix cars, I'm an engineer.

I'm married, have 3 kids and haven't lived at home in 30 years.

I don't think the term "geek" applies...  :)

Oh yeah... I'm also learning Linux now!  ;-)

---

### Post by Krupski on 2008-10-08
> **47_MasoN_47 said:**
> I definitely agree that people who don't even try to help themselves don't deserve to be helped.

BTW Mikhail Kalashnikov is one of the greatest men ever.

What I like about Dr. Kalashnikov is his devotion to SIMPLICITY.

Simple is easy to build. Simple is easy to understand. Simple is easy to repair and simple is the most reliable.

For those who don't know, I am referring to the &#1040;&#1074;&#1090;&#1086;&#1084;&#1072;&#1090; &#1050;&#1072;&#1083;&#1072;&#1096;&#1085;&#1080;&#1082;&#1086;&#1074;&#1072; &#1086;&#1073;&#1088;&#1072;&#1079;&#1094;&#1072; 1947 or "Automatic Kalashnikov, Model of 1947", also known as the "AK-47".

Yeah, I'm a gun nut too. Computers and guns. What a combo, huh?  :)

---

### Post by lykwydchykyn on 2008-10-08
When I see a question, I generally give a response that covers the basic gist of the answer.  If the person doesn't understand the answer, they are free to ask more questions, and those questions will get answered.  I don't see the point in giving a detailed response that the user might not need.  I also don't see a problem with posting links to howtos, especially if I'm just going to give them the same information all over again.  If they need more info, they can always ask.

The server forum desperately needs a FAQ.  I've been hanging out there for a couple weeks and I've seen the same questions at least 6 or 7 times already:
 - Can I / how do I install a GUI?
 - How to I transfer files to my computer?
 - Why can't I write files to /var/www

I could go on.

---

### Post by patrickballeux on 2008-10-08
> **Krupski said:**
> To me, the term "geek" conjures images of a socially inept, freckle faced nerd that plays with his computer all day and lives at home at age 40.


You are right that this give a negative image. But I don't think that "geek" is applying to the majority of technically gifted people :)

When I think about "geek language", I consider it as a technical description with a lot of holes that must be filled by the knowledge of the reader/listener.

It's like giving half the answer, hoping that the reader/listener will have the knowledge to follow the steps on his own.  So, "geek language" is not far from your own description as a "socialy inept person".

When you think about it, it is like you were explaining how an engine works to a kid, hoping that he will understand and know how to repair his car by himself.  And if he comes back, you say: Read the book, I don't just have that to do..."

It's good to give references to read, but adding a hint on what to read or how to read it is often what is needed for the user to be able to solve his problem.

If you ever work in technical support, that is something you learn really fast... :)


Have a nice day!

---

### Post by windependence on 2008-10-09
> **patrickballeux said:**
> 

How can you judged if someone cannot be an asset to the linux community? Because he is not an expert with the command line or able to find quickly some info?

You completely missed my point. The reason there aren't as many Linux/Unix admins than MCSEs is because there are some people who just don't happen to have the ability to learn on the level needed to become a Linux admin. User, maybe, but maybe not on the administration level, and after all if you are going to run servers, you need to be on the admin level.

> **patrickballeux said:**
> Are you telling me that you can become a linux user only if you are accepted by the community?  This is not a religion or a being good or bad.  Linux is for everybody, free and open!  If some are willingly not doing the effort of learning once they have the tools, natural selection will take care of them.

Nope, I personally don't have a problem with anyone using Linux, BUT, I don't think everyone is cut out to be a Linux user and I have no desire for everyone in the world to use Linux.

> **patrickballeux said:**
> Don't confuse lazyness and ignorance.  Good for you if you know that you don't know, but for some other, they must learn that they have to learn.

"Sans rancune" (No offense intended)

And that goes back to what I said earlier. Not everyone is cut out to be a Linux admin, or even a Linux user. No offense taken, I am not a Linux zealot, in fact I call myself an operating system agnostic. I actually us more BSD than Linux, and of course when I want a pretty, functional, usable GUI, I use my Mac. ;)

-Tim

---

### Post by windependence on 2008-10-09
> **cariboo907 said:**
> Tim

Actually I was planning on trying FreeBSD next when I get some spare time, It looks like the BSD's are the same as Linux, try them and then use the one you are most comfortable with.

Jim

Hey Jim, I know we're of topic for this thread but yes, in a sense you are right. FreeBSD is by far the most popular. It's goal is to be the best server operating system possible with excelllent stability.

NetBSD, is an OS with a goal of running on as many platforms as possible. It runs on just about anything.

OpenBSD has a goal of being the most secure OS on the planet, and arguably the vast majority of people including myself think it absolutely is. Only two remote holes in the default install, in more than 10 years! they also audit every single bit of code that goes into the OS for correctness.

When you get a chance try an install of FreeBSD and just tick off the IPV6 box during the install. SuSE Linux also will let you do this as well as disable the firewall which I wish Ubuntu would do. All my machines are natted behind my gateway box.

-Tim

---

### Post by cdenley on 2008-10-09
> **windependence said:**
> Hey Jim, I know we're of topic for this thread but yes, in a sense you are right. FreeBSD is by far the most popular. It's goal is to be the best server operating system possible with excelllent stability.

NetBSD, is an OS with a goal of running on as many platforms as possible. It runs on just about anything.

OpenBSD has a goal of being the most secure OS on the planet, and arguably the vast majority of people including myself think it absolutely is. Only two remote holes in the default install, in more than 10 years! they also audit every single bit of code that goes into the OS for correctness.

When you get a chance try an install of FreeBSD and just tick off the IPV6 box during the install. SuSE Linux also will let you do this as well as disable the firewall which I wish Ubuntu would do. All my machines are natted behind my gateway box.

-Tim

FreeBSD used to be my operating system of choice. Oddly, I went from Windows XP to FreeBSD. I was so annoyed by compiling software whenever I wanted to update it, that I switched to ubuntu. Also, getting the TV output on my ATI video card to work was obviously no easy task. I guess it's not meant to be a desktop OS, though. I don't think I'm switching back to *BSD, even for servers, because of the decent hardware support and binary package distribution systems in Linux.

---

### Post by windependence on 2008-10-09
> **cdenley said:**
> FreeBSD used to be my operating system of choice. Oddly, I went from Windows XP to FreeBSD. I was so annoyed by compiling software whenever I wanted to update it, that I switched to ubuntu. Also, getting the TV output on my ATI video card to work was obviously no easy task. I guess it's not meant to be a desktop OS, though. I don't think I'm switching back to *BSD, even for servers, because of the decent hardware support and binary package distribution systems in Linux.

We should really start another thread for this one. there are so many compelling reasons to use FreeBSD if you are running a production machine. Hardware support is now as good or better than Linux for server stuff. So many people want to run their desktop on *BSD. That's not what it's for, so you won't see good support for things like wireless and sound,  but you WILL see uptimes measured in YEARS instead of days. Linux is good but fragmented, and I hate to say it, becoming very bloated. Compiling software is no longer required because there are packages, although I recommend compiling anyway so that you can squeeze every last drop of performance out of your hardware. The new package management software like portsnap make it a breeze to keep up to date and install software. 

I'll put my *BSD boxes up against any Linux distro any day of the week. Smaller, faster, simpler, and more reliable. I am NOT knocking Linux, but *BSD was around long before Linus wrote his first line of code.....

-Tim

---

### Post by hyper_ch on 2008-10-09
I often just point out where people can find information. If they don't understand what's written there, then they will ask more... however if they then just brag the can't undestand a thing and I have the impression they just want to be spoon-fed then tehy land on my ignore list.

Don't forget that (1) all people that help on here are volunteers and (2) just about every question has been answered in this forum before.

And yes, the server subforum is geeky and from those that participate there I expect to put more effort into than in the absolute beginner forum.

---

### Post by koenn on 2008-10-10
> **lykwydchykyn said:**
> When I see a question, I generally give a response that covers the basic gist of the answer.  If the person doesn't understand the answer, they are free to ask more questions, and those questions will get answered. ...  I also don't see a problem with posting links to howtos, especially if I'm just going to give them the same information all over again.  If they need more info, they can always ask.

Exactly. 

> **hyper_ch said:**
> 
And yes, the server subforum is geeky and from those that participate there I expect to put more effort into than in the absolute beginner forum.
Well, not necessarily geeky, but if someone is planning to run any sort of server, I assume that they've seen a command prompt before and know how to open a text editor. 
Also : very often, answers to server-related questions tend to become long and elaborate, because that's just how servers are. So pointing to a howto, a tut, an artical that covers the question at hand (or refer to a man page for an explanation of options and switches to a command) is, imo, a valid answer. 

I remember one occasion where I knew of a web page that *literally* answered a poster's question, so I gave him the link. He came back with questions that were covered in that web page - if he'd actually looked at the page, the answers would have jumped in his face. So we have to be "helpful" and copy/paste such information into a forum post to save a poster the trouble of clicking a link ? I don't think so.

---

