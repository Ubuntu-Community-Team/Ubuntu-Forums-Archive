---
title: "Forum Safety Suggestion"
date: 2010-04-27
forum: Forum Feedback &amp; Help
---

### Post by peterj on 2010-04-27
Hey Folks, 
I was reading the fairly comprehensive warning on avoiding malicious code within the forum. Funnily, years ago when I was starting off I used to wonder why I was trusting absolute strangers with code which could destroy everything with me being oblivious to it. But this is a real community, and back then it was a tight one. Now that Ubuntu has grown, and become more mainstream in some ways, the inevitable 14 year old 'wannabe' is probably unavoidable, sadly. 

My suggestion is as follows: 
Question is posted on forum
Question is answered by relative newcomer to the forums
Code remains hidden to the person who asked the question until a well experienced forum/ubuntu user has scanned it to ensure that there is nothing malicious. That person approves the code and it is revealed, he is rewarded with some kind of point/recognition system. 

I do not know how often malicious code is spread, if it is often enough this would, in my opinion, be worth the extra time required.

---

### Post by JamezQ on 2010-04-27
Thats a lot of extra time O.o.

I think ubuntu should just word censor some code for suggestion.

And only that code gets reviewed.

---

### Post by user1397 on 2010-04-27
Which gets me thinking, why can't ubuntu, or really linux devs in general just make those commands harmless so that even if you were to accidentally type them it would just say something like "sorry but this command will **** up your computer, don't type it again."

---

### Post by JamezQ on 2010-04-27
> **ubuntuman001 said:**
> Which gets me thinking, why can't ubuntu, or really linux devs in general just make those commands harmless so that even if you were to accidentally type them it would just say something like "sorry but this command will **** up your computer, don't type it again."

I agree, it should be able to tell if something is a fork bomb.

Or if it is safe to use rm ** where you currently are.

I mean it should *let* you, but it should tell you what it might/will do. And then you can override with whatever.

Typing "yes" or something

---

### Post by szymon_g on 2010-04-27
i disagree- first, you would have to employee a lot of people to check every codeblock- most people are here volunterly, they do not get money for doing it- but i'm not sure how many of us would like to check every commend etc.

and secundo- (it actually should be a first point)- no, i disagree- everyone should be learn responsibility and risk assestment- if you need a nanny to check every 'risky' command, well, than you should not use computer.

@ubuntuman001
no, commands should work fine, without asking/requiring confirmation 20 times. you know- at least, when you will loose your system, you will think twice and learn using brain instead of copy&paste

---

### Post by lovinglinux on 2010-04-27
You might wanna take a look at my [FoxRunner](http://lovinglinux.megabyet.net/?page_id=527) extension for Firefox. It has different levels of security, which allows to control what you will be able to run. In the most restrictive setup, you won't be able to run any command without confirmation and even after that, blacklisted commands are not processed. You can add as many blacklisted commands as you want to the list.

The extension primarily function is to allow users to run commands from forum posts, by simple selecting them and clicking an option in Firefox context menu. It also allows you to send text as variables to custom scripts and create scripts with up to 10 variables. Everything is accessible from Firefox sidebar and context menu. Additionally, you can launch a simple runner from the status bar.

See pics below:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=154449&d=1272345798[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=154456&stc=1&d=1272362697[/IMG]

---

### Post by peterj on 2010-04-27
> **szymon_g said:**
> i disagree- first, you would have to employee a lot of people to check every codeblock- most people are here volunterly, they do not get money for doing it- but i'm not sure how many of us would like to check every commend etc.

and secundo- (it actually should be a first point)- no, i disagree- everyone should be learn responsibility and risk assestment- if you need a nanny to check every 'risky' command, well, than you should not use computer.

@ubuntuman001
no, commands should work fine, without asking/requiring confirmation 20 times. you know- at least, when you will loose your system, you will think twice and learn using brain instead of copy&paste

You and I have very different beliefs about what Ubuntu is and what it strives to be. 

'One of the sayings in our country is Ubuntu - the essence of being human. Ubuntu speaks particularly about the fact that you can't exist as a human being in isolation. It speaks about our interconnectedness. You can't be human all by yourself, and when you have this quality - Ubuntu - you are known for your generosity.'
                                                  -Archbishop Desmond Tutu

---

### Post by Bodsda on 2010-04-27
> **szymon_g said:**
> 
and secundo- (it actually should be a first point)- no, i disagree- everyone should be learn responsibility and risk assestment- if you need a nanny to check every 'risky' command, well, than you should not use computer.
 
@ubuntuman001
no, commands should work fine, without asking/requiring confirmation 20 times. you know- at least, when you will loose your system, you will think twice and learn using brain instead of copy&paste
 
I completely agree with that.
 
Bodsda

---

### Post by whiskeylover on 2010-04-27
> **JamezQ said:**
> I agree, it should be able to tell if something is a fork bomb.

Or if it is safe to use rm ** where you currently are.

I mean it should *let* you, but it should tell you what it might/will do. And then you can override with whatever.

Typing "yes" or something

This is simply not feasible. One can easily write code that uses commonly used APIs to create a fork bomb. How can you expect a machine to tell if a piece of code is a fork bomb?

---

### Post by mcoleman44 on 2010-04-27
Linux in general is made to do whatever I ask it to do. If I type sudo rm -rf / then I want it removed.  I dont want my computer to argue with me, thats what microsoft tried to do and look where I am now. Its the users job to be safe and know what he/she is typing. Were not there parents. They can figure
it out.

---

### Post by philinux on 2010-04-27
@peterj

It would be next to impossible to moderate that number of posts.

---

### Post by Doctor Mike on 2010-04-27
More to the point, what happens when a user posts malicious code? Are they banned for life?... I hope so...

Are they reported to there IP?... I hope so...

Do we get out the big sticks and clubs?... Ha, just a thought...

---

### Post by Doctor Mike on 2010-04-27
> **peterj said:**
> Hey Folks, 
I was reading the fairly comprehensive warning on avoiding malicious code within the forum. Funnily, years ago when I was starting off I used to wonder why I was trusting absolute strangers with code which could destroy everything with me being oblivious to it. But this is a real community, and back then it was a tight one. Now that Ubuntu has grown, and become more mainstream in some ways, the inevitable 14 year old 'wannabe' is probably unavoidable, sadly. 

My suggestion is as follows: 
Question is posted on forum
Question is answered by relative newcomer to the forums
Code remains hidden to the person who asked the question until a well experienced forum/ubuntu user has scanned it to ensure that there is nothing malicious. That person approves the code and it is revealed, he is rewarded with some kind of point/recognition system. 

I do not know how often malicious code is spread, if it is often enough this would, in my opinion, be worth the extra time required.One solution would be to make a spider that looks for potentially malicious code. You could spider the forum(s) yourself and check posts that are spider flagged, then report posts you feel are serious concerns. I believe there are many people here already on the look out for BAD code and or bad advise, but you could probably find people to help...:)

---

### Post by Elfy on 2010-04-27
It was before my time as a mod but I do remember that some malicious code was caught very quickly by staff/users reporting it to staff - it was jailed pretty quickly and the OP I think had burnt beans shortly after. 

I think that the way things wotk at the moment is and should be sufficient - if people see something that looks dodgy it gets reported.

In addition I think that people should soon learn to ask if they are not sure what some code does and not just run it - this not only makes them think but also learn.

This is not staff policy but merely my take on this.

---

### Post by Joeb454 on 2010-04-27
I thought rm -rf / now gave a prompt asking if you were 100% sure, even when run as root? I'm sure I remember this making it into either Jaunty or Karmic

---

### Post by bapoumba on 2010-04-27
> **Doctor Mike said:**
> More to the point, what happens when a user posts malicious code? Are they banned for life?... I hope so...

Are they reported to there IP?... I hope so...

Do we get out the big sticks and clubs?... Ha, just a thought...

> **forestpiskie said:**
> It was before my time as a mod but I do remember that some malicious code was caught very quickly by staff/users reporting it to staff - it was jailed pretty quickly and the OP I think had burnt beans shortly after. 

I think that the way things work at the moment is and should be sufficient - if people see something that looks dodgy it gets reported.


They get banned indeed. On a couple occasions we had a rash of users posting malicious code to unanswered posts in ABT. They kept making up new accounts, we kept banning them, for over 2 hours. About one new account and posts per 2 mins, that was exhausting :)
I bet aysiu remembers, we kept on reloading the new post page from ABT, banning, cleaning and reloading etc. They eventually got bored.
Only one person was harmed in the whole process (on this occasion and several other ones a little before and a little after where there were less posts and less activity).

Our best set up is you, UF members. You see everything, nothing escapes your scrutiny, because UF is a place you care about.

When people use proxies to mask their real IP, it is virtually impossible to do anything, and not worth the time. Being patient always works :)

---

### Post by madjr on 2010-04-27
This is why we need to implement the system [rollbacks]("http://www.phoronix.com/scan.php?page=article&item=fedora_13_btrfs&num=1") (Btrfs) like fedora will be doing and open solaris has had for long time

---

### Post by bapoumba on 2010-04-27
> **madjr said:**
> This is why we need to implement the system [rollbacks]("http://www.phoronix.com/scan.php?page=article&item=fedora_13_btrfs&num=1") (Btrfs) like fedora will be doing and open solaris has had for long time
Some guys from SliTaz told me that btrfs was the future of file systems. I should have a serious look.

---

### Post by CptPicard on 2010-04-27
> **whiskeylover said:**
> This is simply not feasible. One can easily write code that uses commonly used APIs to create a fork bomb. How can you expect a machine to tell if a piece of code is a fork bomb?

+1, generally recognizing if some given piece of code will do something in particular, is even theoretically impossible. There are a couple of variants of the issue...

1) Telling whether a piece of code contains an infinite loop (halting problem)

2) Telling whether a piece of code computes some given function (again, it could just run forever, and you can't tell if it does)

---

