---
title: "re: the 'rm' command.... it is useful"
date: 2007-11-15
forum: Forum Feedback &amp; Help
---

### Post by GMachine_24 on 2007-11-15
You know . . . telling people never to use the 'rm' command because it can, in combination with other arguments or whatever they are called, delete information a user does not want deleted - this is like attempting to outlaw a crowbar because someone might use it to kill someone else or, like the RIAA's attempt to OUTLAW CD copiers, even the MP3 format, because someone can use them for illegal purposes.

Why not tell people to avoid format commands, other delete commands, and just about anything else including, hey, even the shirt off your back because you can take it off and use it to strangle someone!!! Yeah... wow.... T shirts are dangerous.

Let's face it, telling people not to use the 'rm' command is silly.

Computer users, even newbies, and especially Linux users, should have their systems backed up. A computer can crash at any time for any reason - REMEMBER MTBF??? - well it's there for a reason.

You cannot protect people from themselves, unless you want to lock everyone up and hey, look at U.S. prisons, they sure do a swell job at keeping people safe, don't they?

Oh yeah - I use the 'rm' command all the time . . . . most often to delete all the .deb packages I download to keep my Ubuntu system up-to-date. I cd to /var/cache/apt/archives wherein sit all those files which occupy a LOT of space if you don't delete them then I just sudo rm *.deb to get rid of all the .deb files. Enter my password. And voile.

In this instance, with Ubuntu adding the "sudo" feature, that does more to ensure the safety of my files than avoiding any one command.

And I agree with the following post that newbies should be told not to wipe their hard drives clean by accident. That sounds like a super suggestion.

:0

---

### Post by jordank on 2007-11-15
I think by telling people not to use the rm command in general is good to keep people who are new to ubuntu safe.  Obviously people that are experts in ubuntu won't take that advice and completely avoid the rm command all together.  It's stickied, and that's a good idea.  Speaking from experience, i got hit by the spammer and had to reinstall. By telling people not to use the rm command, it just avoids headaches for those new to ubuntu. It's a good idea to avoid that command.  If you're comfortable using it, that's fine. But this forum is "For the Absolute beginner".

---

### Post by Paul820 on 2007-11-15
We are not telling them to stop using the rm command, we are telling them to stop using the rm command the spammer was telling them to use which was destroying either their system or their data. Data that some of us have on our systems that are very important. I and most others do do backups, but a small fraction do not. This is a beginners forum and most do not know what the command did, they come here for help and assumed that the spammer was helping, when really he was being an idiot.

---

### Post by bodhi.zazen on 2007-11-15
Moved as this is not a request for support.

I think the objection is to the *misuse* of the rm command, or any command for that matter.

---

### Post by -grubby on 2007-11-15
add "sudo" in front of rm and you have a problem

---

### Post by PriceChild on 2007-11-15
The forums were attacked by a spammer repeatedly suggesting beginners use a command which would delete their hard drive. We have been wanting to protect our users by **warning** them against using random commands including "rm" if they do not understand it. We're not imposing laws that people should never use it ever... we're **just warning** users.

Stop blowing this issue up in such a ridiculous manner... its not even an issue.

I would also strongly advise against rm'ing random files like you have explained.
Instead use
```
sudo apt-get autoclean
```or```
sudo apt-get clean
```to remove unwanted cached debs.

---

### Post by GMachine_24 on 2007-12-02
Hi:

I certainly did not mean to blow things up .... or however you put it. But from my recollection the sticky re: the 'rm' command was essentially telling people to avoid the command altogether. This, I thought, was going overboard.

I understand there was a problem with a miscreant attempting, apparently successfully, to cause havoc. And I realize this occurred in a beginner's forum. Perhaps I have forgotten what it is like to be a 'newbie' to any OS. And perhaps it is my background as a news reporter that has lead me to believe the answer to problems like this is more information, not restrictions.

Anyway, you're correct - there has been enough written about this.

gm

---

### Post by LaRoza on 2007-12-03
> **GMachine_24 said:**
> Hi:

I certainly did not mean to blow things up .... or however you put it. But from my recollection the sticky re: the 'rm' command was essentially telling people to avoid the command altogether. This, I thought, was going overboard.


I thought so too, but the announcement is only protecting those who don't know what rm does, the average user of Linux with some experience will know, and will not avoid using the command.

---

### Post by PriceChild on 2007-12-03
The announcement does not tell people to never use the command... it just warns of the current dangers, and gives examples :/

---

