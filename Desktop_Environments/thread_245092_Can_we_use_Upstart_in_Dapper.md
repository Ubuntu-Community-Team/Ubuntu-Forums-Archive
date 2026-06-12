---
title: "Can we use Upstart in Dapper ?"
date: 2006-08-27
forum: Desktop Environments
---

### Post by ss0007 on 2006-08-27
Hi ,
I heard about the new boot system for linux is up in Universe
[http://www.netsplit.com/blog/work/canonical/upstart.html](http://www.netsplit.com/blog/work/canonical/upstart.html)

Has anybody tried it?
can i really use this ? Is this stable enough ?

---

### Post by lagagnon on 2006-08-27
I guess you did NOT read that document to its end because the last few paragraphs tell you it is still in the testing stage and the document was updated Aug26th so the answer to your last question is NO (but I should not have had to write this answer had you actually read the document).

The answer to your second question is of course you can try using it, but I would never touch (with a 10' pole) init sequences that have never been fully tested.

---

### Post by regeya on 2006-08-27
> **lagagnon said:**
> I guess you did NOT read that document to its end because the last few paragraphs tell you it is still in the testing stage and the document was updated Aug26th so the answer to your last question is NO (but I should not have had to write this answer had you actually read the document).

I must be an idiot too, because I read to the end and it sounded as if it were in Universe (Universe of WHAT RELEASE?) and that experienced users were invited to help test.

EDIT:  Two rounds were too inflamatory.  When I read a post that makes me mad, I should just learn to go off and do something else for an hour, then see if I still care enough to post. :-)

The thing is, the document is very clear on the intentions of the project, some technical details, some ideas about implementation, etc.  IF ONE READS TO THE END OF THE DOCUMENT, as you suggest any halfway-sentient being would be able to do, you get a vague impression that the release is in Universe (which is also the title of the post) and that experienced users should help test this.  

This leaves a few assumptions in the mind of the average (that's me!) reader.

# When someone just says 'Universe', I assume 'Universe in current release', which is Dapper.
# It's hard to not ask questions when you're assuming that it's in Universe of the stable release, yet a simple 'apt-cache search upstart' yields nothing.
# It's hard to not assume, without testing, that there's a certain level of readiness to upstart if it's in the (admittedly unsupported) Universe repo of the current stable release.
# It would be foolish to not ask your peers before leaping, especially if your testing machine will also be your main machine (my main reason for searching before asking myself, which is how I found this thread).
# While some of us may be scared off by the lack of compatibility tools, maybe the more casual user wouldn't be.
# When one encounters hostility when asking questions, one tends to stop asking questions...and move on to something else.  I don't care to mention the number of 'why I switched back to Windows' stories I've read that involve hostile "you idiot" responses from Debian, FreeBSD, etc. zealots who have more bile than compassion.
# Negative behavior accomplishes nothing.

All I'm saying is that while the original poster should have probably been scared off by the initial blog post, I'm going to have to side largely with the original poster, because I read the post and wasn't all that clear on whether or not it was ready for brave-but-casual users.  If you can't handle a few questions from people who're genuinely curious, then please give up on this 'upstart' thing now and keep sysvinit.  Otherwise if this is a sign of things to come, I want off this ride.  I've seen a number of Linux distributions go from friendly, to friendly banter, to out-and-out hostility, and it's always sad to see happen, because once you get to the negative hostility phase, the negativity tends to seep over into the dev team, and before long you have devs saying 'what we have is good enough!' and 'screw this, I'm going to buy a Powerbook.'

Can you believe, for example, that the Gentoo crowd used to be one of the friendliest Linux crowds I'd ever encountered?  People could even ask questions like 'what's Portage?' on the forums and and at most you'd see a thread locked with a friendly pointer in the right direciton.  Now?  Meh.  Just try to have a conversation about the future direction of Portage. :-)

Anyway, guys, just chill.  If people didn't care about their fave distribution, they wouldn't ask 'stupid' questions about development code.  All of us who're interested are just genuinely interested in seeing Ubuntu remain the great distribution it is, and it won't do that by sitting on its haunches and bragging about how great everything we already have is.  

Y'all have a great and extremely popular distribution.  Just look at all the anti-Ubuntu backlash on Digg! ;-)  What more proof do you need of success?  Wow, some of the bile lobbed at MS and Apple stories goes to Ubuntu on a highly popular tech site; how cool is that?

Keep up the good work, fellers, and um, both to devs and community people:  Don't give in to your anger.  Yes, I sound like a hypocrite, but I truly mean it.  Let's all work together to make this work as best it can. :-)

---

### Post by Anduu on 2006-08-28
Well I'll save everyone a little suprise and say upstart is NOT in Dappers repos anyways.

Might be in Edgy's tho...

---

### Post by escape on 2006-10-07
To offer some advice that is actually helpful, I did this. 

I changed the repos to edgy and did apt-get install upstart

There were about 97 other packages it required installed, so those got installed too. The only problems were that I got an error message about dbus when gdm started, and to have the keyboard be recognized I had to boot in single user mode, then boot gdm.

Everything else worked fine - wireless, ATI fglrx, etc. Eventually I got tired of having to but into single user mode and just installed edgy. Just piping in to say it can be done, and I don't really recommend it.

---

### Post by stevieb on 2006-10-26
has anyone tried this in the past couple of weeks?  i'd like to try and switch to edgy, but the consensus on the forums seems to be that wireless has been left out of the release; so i need to stick with dapper for that reason.

thanks,
-steve

---

