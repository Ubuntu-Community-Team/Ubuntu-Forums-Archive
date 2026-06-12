---
title: "doomsday (jdoom) on 5.10"
date: 2006-02-16
forum: Gaming &amp; Leisure
---

### Post by grimmson on 2006-02-16
Hello all. From what I've read the doomsday engine may be the best (updatable) doom port around. The problem is it's not listed in synaptic (and I'm to chicken to install from source). So I wanted to know If I could add the 5.04 repositories and install from there? Will the shareware doom.wad file work form the repositories? I have the deng-1.8.6.tar.gz downloaded. has anyone compiled from source on 5.10? any speed bumps? Please help, i miss doom.

---

### Post by grimmson on 2006-02-17
Quick update. I tried to compile from source but sdl 1.2.0 is required and I think synaptic says I have 1.2.7 w/ ogg. Can I point ./config to 1.2.7 or should I go on a wild goose chase for 1.2.0?

---

### Post by jasay on 2006-02-17
You should do a search, but here's a link anyway.  [Doomsday Repo]("http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu").  Don't forget you need an original .wad file to make it all work.

---

### Post by grimmson on 2006-02-17
That brings up an unrelated question. I know nothing about linux key mappers, spyware, viruses and so on. One thing I've read a while ago is "Use other repositories at your own risk." I agree with that. You never know who is trustworthy and if there not I'll have a hell of a time fixing it (whatever it may be.) I assume anything in our repos have been checked, virus scanned or at least given to us by a trustworthy source. I appriciate you link and your time, but I was hopeing to stay simple and close to home. If you have advice on determining whether a site is trustworthy please post so I'll know. thanks.

---

### Post by jasay on 2006-02-17
Always an interesting question isn't it?:-k   I don't have any real suggestions other than to keep your eyes open.  Unsupported repos are probably about as safe as randomly downloading programs in windows (in other words, not very).  On the plus side, GPL software is supposed to be accompanied by source so you could check it out if you really wanted.;)

In this case, the mantainer, [Yagisan]("http://www.ubuntuforums.org/member.php?u=14052") is actually a forum member and from previous post has expressed interest in getting the packages into debian and maybe ubuntu repos, but I guess that hasn't happened yet.  You might shoot him a message.

I can definately understand your suspicion.  It's the smart way to be on the web these days.

---

### Post by Yagisan on 2006-02-17
[QUOTE=grimmson]That brings up an unrelated question. I know nothing about linux key mappers, spyware, viruses and so on. One thing I've read a while ago is "Use other repositories at your own risk." I agree with that. You never know who is trustworthy and if there not I'll have a hell of a time fixing it (whatever it may be.) I assume anything in our repos have been checked, virus scanned or at least given to us by a trustworthy source. I appriciate you link and your time, but I was hopeing to stay simple and close to home. If you have advice on determining whether a site is trustworthy please post so I'll know. thanks.[/QUOTE]G'day grimmson,

It is definitely wise to be wary of third party repositries. Unfortantly there is no best answer on how to determine if any given site is trustworthy, so I can only offer some guidelines.

First - Is the site regulary maintained ? Is it updated often ? Can you easily get in contact with the packager if needed ?
Second - Why does the repository exist ? Is it code license issues ? (this is the case for doomsday, and why it is not yet in ubuntu), US software patents ? (often multimedia stuff like mp3 is here) Or does it have restrictive distribution terms ? (think sun java here)

I invite you to examine my website, and check out the repository to see if you feel I'm trustworthy. You may contact me on the forums, by email, or I'm usually in #ubuntu-motu (I am one of those people, that actually IS checking the offical repositories to make sure everything is ok.) If you do check upstream, you'll find that they recommend my repository for all ubuntu and debian users to make life easier for you, but in the end, it is your call. My repository provides full source, so if you wish, you may download and build the source yourself.

Regards,
Yagisan

---

### Post by grimmson on 2006-02-17
Now I feel like a #ick. Mr. Yagisan please accept my appoligy. If it helps I have done some research, and imho you are a very reliable source. Not to mention I appriciate your time spent on the doomsday package. Your toted as having the best doom port around and thats why I decided to try to install from source (so when idiots like me are unsure about you please just chuckle and post a nice message.)

Since your from Australia and are smarter than the average bear maybe you can advise on something else "security" related. I have gotten burned in the past. I'm not sure how it works, but once I was doing research on diy-cnc, I read a webpage located in switzerlan (or something like that) and got a $40 charge posted to my phone bill without my permission or knowledge for trans-continental long distance even though I use high speed dsl.  Since then I've allways tried to avoid international websites because I don't know how to determan if there may be a charge. Any hints on this would be appriciated. BTW it wasn't porn I promise.

---

### Post by Yagisan on 2006-02-17
> **grimmson]Now I feel like a #ick. Mr. Yagisan please accept my appoligy.[/quote]No need to apolgise, there was no offense taken. Although, it is odd to be called Mr Mr Yagi  said:**
> If it helps I have done some research, and imho you are a very reliable source. Not to mention I appriciate your time spent on the doomsday package. Thank you.

[QUOTE=grimmson]Since your from Australia and are smarter than the average bear maybe you can advise on something else "security" related. I have gotten burned in the past. I'm not sure how it works, but once I was doing research on diy-cnc, I read a webpage located in switzerlan (or something like that) and got a $40 charge posted to my phone bill without my permission or knowledge for trans-continental long distance even though I use high speed dsl.  Since then I've allways tried to avoid international websites because I don't know how to determan if there may be a charge. Any hints on this would be appriciated. BTW it wasn't porn I promise.[/QUOTE] Sounds like a "dialer" was installed. Often dodgey sites try to get you to install an run things like viruses, dialers etc. These usually only aftect Windows based boxes, as it is trivial to get Windows to run them without your knowledge. That sysem probally has a modem in it - if you don't use it unplug it. Also lowers the risk of pc damage in a lightning strike incident. If the system can't be converted to (edu/k/x)ubuntu then I'd install a firewall, 2 anti-virus applications, 2 anti-spyware applications. the anti-virus and anti-spyware needs to be run often to be effective (and not blindly running things downloaded off the Internet helps). The reason some of these have 2 is often 1 misses something the others find.

---

