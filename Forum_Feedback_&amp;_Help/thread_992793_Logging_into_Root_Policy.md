---
title: "Logging into Root Policy"
date: 2008-11-25
forum: Forum Feedback &amp; Help
---

### Post by CandyKiller on 2008-11-25
I would like to say I was greatly offended on xchat, as well as the threads that I found on these forums that were down right rude to individuals asking questions about how to log into a root(administrators) account. (I did finally figure out how to access my account in Root.)

From reading what the root account actually does, it seems to me just a protection upon the user so that he doesn't #$%^%^ up his OS.  Which I can agree can be a good thing, except for Linux is supposed to be a modular Operating System and "User-Friendly" in the fact that you can mold and form the operating system to your tastes.  If this involves setting up a Root account for certain instances where you need to edit multiple files in multiple directories without having to pull up the terminal to do so then so be it.  

I have been fulling around with computers for years now, I'm a qualified Radar Technician in the military which allows me to replace as little as resistors and other small components on microcards, and yet I was told that I cannot access a root account, do not ask, you're stupid if you try to do this and you might break something.  Basically an insult to my intelligence.

This is a laugh to the Linux community, the same Linux community that stands behind it's Operating System and hails at all the freedom you have with it, yet you limit your new users and those just transitioning over to Linux to not have "fun" and try to "break" the operating system.

I'm sorry but this just does not make sense to me and has annoyed me to the point of no return.  If the community doesn't want this feature so much as to refuse giving out this knowledge then why is it in the OS to begin with?

---

### Post by Wickd on 2008-11-25
Well not to be offensive, but I have successfully messed up my Linux at least four times. But unfortunately that does not increase your knowledge. The secret behind learning Linux is to fix what you broke. And I must also say that this forum has been a great help thus far. It is there to help you fix what you destroyed and not help you destroy it

I find your logic a bit silly for a qualified techi to be quite honest. Make sure of your facts before you post junk on the forum

---

### Post by Sub101 on 2008-11-25
> **Wickd said:**
> Well not to be offensive, but I have successfully messed up my Linux at least four times. But unfortunately that does not increase your knowledge. The secret behind learning Linux is to fix what you broke. And I must also say that this forum has been a great help thus far. It is there to help you fix what you destroyed and not help you destroy it

I find your logic a bit silly for a qualified techi to be quite honest. Make sure of your facts before you post junk on the forum

I agree. If you need to ask how to log in as root it may mean you skill may not be up to what you are trying to do. As Wickd said, you can really ruin your system.

I am by no means saying your technical abilities are not great, purely that as each system is different you need to learn each as an individual. I thought I new all there was to know about computers. Then I moved to Linux, and learnt a whole lot more.

---

### Post by scorp123 on 2008-11-25
> **aktiwers said:**
> Relax a moment..  You are in violation of the forum's rules:

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

> Tutorials explaining how to enable the root account for a graphical login or autologin will not be supported on the forums and will be moved to the Jail. Although we believe people should have the freedom to run their computers however they want, we also believe in supporting Ubuntu's security model. You can find or post information elsewhere on the internet regarding graphical Ubuntu root logins; such tutorials do not have to be hosted on the Ubuntu Forums.

Users posting such tutorials after this announcement will be given a warning or infraction at the discretion of the staff.

---

### Post by roshanjose on 2008-11-25
Hey the reasons why you are told not to access the root account is

1) Its an administration account. 

2) Very volatile and sensitive to hacking

3) When you use the user account instead, you are asked to enter   the      password,  which makes you think twice whether you really need to execute some shell or bash script or use sommand command interface

4) When hackers gain access to your root account, then can easily steal the data

5) In user account, the hackers have to give in the user password each time they perform any malicious task.

Now do you get convinced why you are told not to access the root account

---

### Post by randiroo76073 on 2008-11-25
I beg to disagree with you scorp123, aktiwer answered a question, did not post as a tutorial!  When I was new to Linx I ask the same question & was told the same, I don't need to know.  Linux is about knowledge, and part of that knowledge is knowing how to login as root. While I agree that there should not be a specific tutorial on this, the knowledge should be available to those who take the time too ask.

---

### Post by wizard10000 on 2008-11-25
I'm gonna have to echo the sentiments of a few people so far - if you need to ask how to enable the root account perhaps it'd be a good idea for you not to log on as root  :)

The root account on my Ubuntu installation is enabled but I've logged on as root exactly once - to remove my own GNOME profile after I'd trashed it.  Didn't even need root for that - I could have just booted into recovery mode and did what I needed to do.

Editing multiple files in different directories without logging on as root is fairly simple - you can launch nautilus as root with a simple 

```
gksu nautilus /
```

or open gedit with elevated privileges and just drag files from a nautilus window into gedit for editing - none of this is particularly difficult.

I've been a professional geek for a heck of a long time and you don't want more permissions than you need to perform the task at hand - if you don't have rights to break it they can't blame you for breaking it  :D

---

### Post by Paqman on 2008-11-25
> **CandyKiller said:**
> If this involves setting up a Root account for certain instances where you need to edit multiple files in multiple directories without having to pull up the terminal to do so then so be it.  


You don't need the root account to do this. Just Alt-F2 and launch Nautilus with:
```
gksu nautilus
```
(substitute gksu with kdesu if you're using Kubuntu)

Generally, Ubuntu is designed to be used without a root account, which is why people will tell you not to enable it. Sudo does everything you'd need a root account for on a different distro.

---

### Post by scorp123 on 2008-11-25
> **CandyKiller said:**
>  I would like to say I was greatly offended on xchat And so? That never stopped me back in the 90's when I started with Linux. Deal with it. You'll survive. ;)

> **CandyKiller said:**
>  as well as the threads that I found on these forums that were down right rude to individuals asking questions about how to log into a root(administrators) account.  Because it's a rather silly question, you see. If people would care to read the forums a bit (and maybe use the search functions here?) they wouldn't have to ask such silly questions and then people who respond would not get get so agitated all the time.

It's one of the most often asked questions here: "How do I enable 'root'?" ... If you have to read the same question again and again and if you have to respond to those people again and again: "It's not necessary, please read here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) .... " then it's sort of natural that people may lose their temper and good manners a bit.

But as I said above ... you'll likely survive that. Words no matter how badly chosen are just that ... words. They can't really hurt you, can they?

> **CandyKiller said:**
>  (I did finally figure out how to access my account in Root.)  If you are knowledgeable enough then you don't have to ask; if you have to ask then you lack the experience and knowledge to treat the "root" account with the necessary levels of respect. ;)

> **CandyKiller said:**
>  If this involves setting up a Root account for certain instances where you need to edit multiple files in multiple directories without having to pull up the terminal to do so then so be it.  There are other less risky ways to achieve this. One false "drag & drop" as root and it's "bye bye file system". The "root" account is almighty and way too powerful (you better know _precisely_ what you do here!), and if you run graphical programs as "root" then other components all of a sudden enjoy root's unlimited powers ... components that most likely were never meant to have these powers. That's exactly why Windows sucks so badly security-wise: way too much stuff runs in way too many graphical components (so it's easy for the user to screw up!) and all that with "administrator" priviledges ... Yuck.

> **CandyKiller said:**
>  I have been fulling around with computers for years now  I don't mean to offend ... but: Unless you've been working with UNIX-like operating systems that doesn't mean anything. 20 years of Windows experience count for nothing here: you're still a noob and have no clue whatsoever what you're doing. **Linux is not Windows.** On the other hand: 5 years of experience on a UNIX-like operating system (HP-UX, Solaris, BSD, ...) and you're on the fast-track to "Linux guru" levels because you then at least understand the lingo and now what people are talking about when they mention stuff like "kernel parameters", "killing processes", "process zombies", "putting tasks into the background", etc.

> **CandyKiller said:**
>  I'm a qualified Radar Technician in the military which allows me to replace as little as resistors and other small components on microcards, and yet I was told that I cannot access a root account  One doesn't have anything to do with the other. You could be Chuck Norris and you'd still get the same answer :D

> **CandyKiller said:**
>  Basically an insult to my intelligence.  You'll survive.

> **CandyKiller said:**
>  yet you limit your new users and those just transitioning over to Linux to not have "fun" and try to "break" the operating system.  Sure, go ahead and break it. You get to keep both parts then :D

> **CandyKiller said:**
>  I'm sorry but this just does not make sense to me and has annoyed me to the point of no return. Have fun with Windows then :D

---

### Post by scorp123 on 2008-11-25
> **randiroo76073 said:**
> I beg to disagree with you scorp123, aktiwer answered a question, did not post as a tutorial! I believe the admins here will decide about that pretty soon.

---

### Post by mikewhatever on 2008-11-25
> **CandyKiller said:**
> 
I have been fulling around with computers for years now, I'm a qualified Radar Technician in the military which allows me to replace as little as resistors and other small components on microcards, and yet I was told that I cannot access a root account, do not ask, you're stupid if you try to do this and you might break something.  Basically an insult to my intelligence.
I think you are insecure about the level of your intelligence, hence your exaggerated sense of entitlement for support and self importance. The fact that you, 'a qualified Radar Technician in the military', had to come here and post the insult, just because you didn't get spoon fed, is laughable, to say the least.

> 
This is a laugh to the Linux community, the same Linux community that stands behind it's Operating System and hails at all the freedom you have with it, yet you limit your new users and those just transitioning over to Linux to not have "fun" and try to "break" the operating system.

Your failure to distinguish between limiting the scope of support for practical reasons and limiting users is clearly evident. If you must be told, here you go, you can have as much fun as you want with your computer. An official permission from mikewhatever, stamped. Make a soup out of your PC, who cares, just fix it yourself after it's cooked.

> 
I'm sorry but this just does not make sense to me and has annoyed me to the point of no return.  If the community doesn't want this feature so much as to refuse giving out this knowledge then why is it in the OS to begin with?

Hope you can cope with a page long read.
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by scorp123 on 2008-11-25
> **wizard10000 said:**
> I'm gonna have to echo the sentiments of a few people so far - if you need to ask how to enable the root account perhaps it'd be a good idea for you not to log on as root  :) Amen to that!

---

### Post by Wickd on 2008-11-25
Also this forum is not the final answer. There is one better and that is google. So do a little research before you post. Never hurts.

Also read through some of the Beginner forums. Lots of answers in there as well

---

### Post by ByteJuggler on 2008-11-25
CandyKiller, the information is out there (findable within seconds/minutes with Google) and in any case, once you're sufficiently capable in Linux/Unix you should be able to just guess at how to enable the root account, without any outside help.  There's no point in getting upset/frustrated about a forum rule that is there for good reason.  Just accept it and move on.     

As an aside:  In my 15+ years of using/exposure to Linux/Unix, 99% of newbie user's requests for having access to a root account password was, it turned out, better served in some other more appropriate way not involving something as fraught with risk as direct access to/an unlocked root account.  Enabling the root account may seem at first glance like the easiest way/way of least resistance to solve many problems.  This does not mean that it's in fact the best or safest or even easiest (once a bit more knowledge/understanding comes into play.)  Clearly explain what you're actually trying to achieve and we'll help you find less fundamental ways of getting done what you want done.

---

### Post by randiroo76073 on 2008-11-25
While not being a "professional geek" & having been in the military(need to know basis), I find that having a root account enabled allows me to perform certain tasks quicker, I run multiple distros and at times need to access them without gksu/sudo multiple times just to accomplish a task. It is, for some, just another tool, to be used with caution for sure. All caveats need to be explained & then let the user decide. I dumped Win for Linux because of freedom of choice.

---

### Post by chucky chuckaluck on 2008-11-25
logging in as root is a feature of linux OS's. ubuntu forums is a support forum (as we are so often reminded) and not everyone's parents (mine are still alive). if you want to give people warnings about a feature, fine, but tell them how to use the feature.

---

### Post by scorp123 on 2008-11-25
> **chucky chuckaluck said:**
> ubuntu forums is a support forum (as we are so often reminded) and not everyone's parents Maybe so. But forums have rules. And the rules regarding "root" and telling beginners how to enable it are perfectly well explained here:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

You don't like those rules? Well, nobody is forcing you to hang around in this forum. You can't choose your parents, but you can choose the forum you're going to hang around on.

> **chucky chuckaluck said:**
>  give people warnings about a feature, fine, but tell them how to use the feature. It's all perfectly well explained here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

This is the official way how Ubuntu approaches root's super-user powers. There you go.

---

### Post by ByteJuggler on 2008-11-25
> **randiroo76073 said:**
> While not being a "professional geek" & having been in the military(need to know basis), I find that having a root account enabled allows me to perform certain tasks quicker, I run multiple distros and at times need to access them without gksu/sudo multiple times just to accomplish a task. It is, for some, just another tool, to be used with caution for sure. All caveats need to be explained & then let the user decide. I dumped Win for Linux because of freedom of choice.

You do not need to use sudo/gksudo multiple times to accomplish a task, regardless of whether you have root account enabled or not.  There is a way to use "sudo" to give you a root shell, for example.

---

### Post by pp. on 2008-11-25
The manufacturer of your RADAR systems will not tell you how to replace transistors while the unit is plugged into the mains and running, either, I suppose.

---

### Post by chucky chuckaluck on 2008-11-25
> **scorp123 said:**
> Maybe so. But forums have rules. And the rules regarding "root" and telling beginners how to enable it are perfectly well explained here:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

You don't like those rules? Well, nobody is forcing you to hang around in this forum. You can't choose your parents, but you can choose the forum you're going to hang around on.

it's a rule that needs to change, in my view. you can't, on the one hand, promote freedom of computing choices and then insist, on the other hand, that people be denied one of those choices. it might be well for ubuntu to divorce itself from the whole 'freedom' issue altogether.

---

### Post by wizard10000 on 2008-11-25
> **chucky chuckaluck said:**
> it's a rule that needs to change, in my view. you can't, on the one hand, promote freedom of computing choices and then insist, on the other hand, that people be denied one of those choices. it might be well for ubuntu to divorce itself from the whole 'freedom' issue altogether.

I really liked the ATM analogy in the "don't show people how to log on as root" post.

> **Isn't knowledge power? What's the harm in having these tutorials posted?**

Let's say you put your money into a bank and the bank gives you an ATM card allowing you to withdraw money if you enter a password in. You decide, however, that you don't want to have to enter a password. You'd rather just be able to put the card into the ATM machine and withdraw cash with just the card and no password. Let's also say that there is a way to tweak the card so as to no longer require a password. If you know the tweak, do you have the right to use it? Well, you probably wouldn't, but let's say the bank's policies on this matter were a little lax. Does the bank have to host tutorials on the card tweak? Absolutely not. The bank wants you to use the ATM with a password and supports that method of security.

---

### Post by CandyKiller on 2008-11-25
Some of the posts on this topic astound me, they really do...

First of all...the - If you had to ask you don't have the intelligence to use it is totally and absolutely absurd.  How many times have you went to buy a new car, and couldn't find where to pop the hood at?  The car still works the same, you still get from point A to point B in it, but just because a car manufacturer might put the ejection handle in a tricky or unseen place means that the buyer doesn't have the knowledge to get under the hood and fix his vehicle? PLEASE...this is the same exact analogy the forum viewers are giving me about how to log into a root command.

Seeking knowledge and then told that it cannot be done, should not be done, and don't ask again without a given explanation is downright rude, especially when you know it can.  This matters not what the cause of the reason behind the person saying it was or not. 

The fact that I haven't worked with linux before doesn't make me a total noob either, computers work the same, they all have the same function.  They all do certain tasks, their methods might be the different, but you can't tell me Linux redefines the way computing is done in theory, that's laughable.

On the side note, all I wanted to do was rename a .png file for my desktop "Start" Ubuntu graphic to replace it with one I had downloaded on Gnome-Look.org.  If this renaming a PNG FILE is going to harm the integrity of my system then maybe I really don't know anything about computers, but I think it's safe to say that me wanting to rename two files, replacing one so that another one will load should be available for me to do without me having to think about using root at all...and in that case something that I shouldn't have to go to the terminal to do. 

Bad design flaw? Ok, well guess what...I was wanting to fix it to where I didn't have to do that, because frankly I don't like knowing that I can't rename a picture on my computer without going through some terminal to do it. That would again be the beauty of Linux would it not?  To change the way the operating system runs FOR YOU.

---

### Post by aktiwers on 2008-11-25
I had no idea that there has been created yet another rule to limit the sharing of knowledge on these boards..
I am sorry if I broke the rules (which I did since my post is jailed), but really I missed the announcement of this strange new rule..

---

### Post by wizard10000 on 2008-11-25
> **CandyKiller said:**
> ...That would again be the beauty of Linux would it not?  To change the way the operating system runs FOR YOU.

So change it - no one's stopping you :)

Your underhood analogy fails because opening the hood on an auto is required to perform routine maintenance - logging on as root is not.

You fail to grasp the larger picture here, CandyKiller - Ubuntu has chosen to not support graphical logins or autologins as root.  There's no requirement for the official support forums to provide or allow tutorials to break their own security model.

---

### Post by chrisod on 2008-11-25
You still don't get it Candykiller. Nobody here has told you that you can't run as root 24 x 7 if that is what you want to do. We just aren't going to tell you how to do it. In the time you've spent whining here you could found the answer on Google and done whatever it is that you want to do.

---

### Post by CandyKiller on 2008-11-25
> **wizard10000 said:**
> 

Editing multiple files in different directories without logging on as root is fairly simple - you can launch nautilus as root with a simple 

```
gksu nautilus /
```

or open gedit with elevated privileges and just drag files from a nautilus window into gedit for editing - none of this is particularly difficult.


Thank you, this was actually helpful knowledge.

---

### Post by wizard10000 on 2008-11-25
> **CandyKiller said:**
> Thank you, this was actually helpful knowledge.

I created a launcher just for this purpose.  Works pretty well  :)

---

### Post by Sub101 on 2008-11-25
> **CandyKiller said:**
>  

On the side note, all I wanted to do was rename a .png file for my desktop "Start" Ubuntu graphic to replace it with one I had downloaded on Gnome-Look.org.  If this renaming a PNG FILE is going to harm the integrity of my system then maybe I really don't know anything about computers, but I think it's safe to say that me wanting to rename two files, replacing one so that another one will load should be available for me to do without me having to think about using root at all...and in that case something that I shouldn't have to go to the terminal to do. 

 If thats all you wanted to do then ask how to do it? Especially as you already new such tutorials are not allowed in this forum.

---

### Post by francisc1701 on 2008-11-25
These are support forums, but if some people choose not to help you with something they are well within their rights to do so. They don't don't owe you anything, and you are not **entitled** to anything. Sorry.
It might be a good idea to read this: [http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html) It's a bit long, but it's worth reading.

Anyway, if a number of people tell you you don't need a root account, maybe you should stop for a minute and think why they say that -- they may a very good reason, or several.

In your case this is a must-read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Cheers

---

### Post by Paqman on 2008-11-25
> **CandyKiller said:**
> 
On the side note, all I wanted to do was rename a .png file for my desktop "Start" Ubuntu graphic to replace it with one I had downloaded on Gnome-Look.org.  If this renaming a PNG FILE is going to harm the integrity of my system then maybe I really don't know anything about computers, but I think it's safe to say that me wanting to rename two files, replacing one so that another one will load should be available for me to do without me having to think about using root at all...and in that case something that I shouldn't have to go to the terminal to do. 


OK, that simple task absolutely does not require you to enable the root account, and to do so would be a reduction in security.

Bottom line: you were given the right advice, although someone should also have told you how to use Nautilus as root.

---

### Post by ByteJuggler on 2008-11-25
> **CandyKiller said:**
> On the side note, **all I wanted to do was rename a .png file **for my desktop "Start" Ubuntu graphic to replace it with one I had downloaded on Gnome-Look.org.  **If this renaming a PNG FILE is going to harm the integrity of my system **then maybe I really don't know anything about computers, but I think it's safe to say that me wanting to rename two files, replacing one so that another one will load should be available for me to do without me having to think about using root at all...and in that case something that I shouldn't have to go to the terminal to do. 

Bad design flaw? Ok, well guess what...I was wanting to fix it to where I didn't have to do that, because frankly I don't like knowing that I can't rename a picture on my computer without going through some terminal to do it. That would again be the beauty of Linux would it not?  To change the way the operating system runs FOR YOU.

As a side note, **you don't need to enable root or go through the terminal to rename a file **(your PNG file) belonging to root.  (Even though for Unix/Linux using the terminal for this is likely the easiest/quickest way.  But an alternative more GUI-esque way is alt-F2, enter "gksudo nautilus", browse to the file, rename (F2 IIRC), done.  If you like, make a shortcut/launcher to "gksudo nautilus" for future rename operations in that vein.  No root account unlocking required, see?)  

As for renaming a file compromising the integrity of your system: No that by itself won't, but unlocking the root account is not the same as (just) renaming a file, is it?  An unlocked root account is an open attack vector for an external hacker, since most unix systems have root accounts, meaning all the hacker has to do is find the password to account "root".  By locking the account you eliminate that avenue of attack -- now the hacker has to obtain/guess both the account name (for a user with sudo rights) *as well as* their password.  A lot harder, or at least, one more hurdle to overcome.

---

### Post by scorp123 on 2008-11-25
> **chucky chuckaluck said:**
> people be denied one of those choices. This has nothing to do with it. Read that policy again.

>  *Isn't knowledge power? What's the harm in having these tutorials posted?*

Let's say you put your money into a bank and the bank gives you an ATM card allowing you to withdraw money if you enter a password in. You decide, however, that you don't want to have to enter a password. You'd rather just be able to put the card into the ATM machine and withdraw cash with just the card and no password. Let's also say that there is a way to tweak the card so as to no longer require a password. If you know the tweak, do you have the right to use it? Well, you probably wouldn't, but let's say the bank's policies on this matter were a little lax. Does the bank have to host tutorials on the card tweak? Absolutely not. The bank wants you to use the ATM with a password and supports that method of security.

Likewise, we on the forums support Ubuntu's security model. If people are able to set up Ubuntu in other ways and still be secure, they can find ways to do that without the forum providing those ways.

You're not being denied of anything. You can enable "root" if you really wish to do it, e.g. there is no mechanism inside of Ubuntu that would prevent that.

It's just that posting such information here is something the staff don't want to happen because it causes too many problems (as explained in the rationale behind that decision).

If you on the other hand are indeed a pro user and know what you are doing than nobody and nothing will stop you from enabling "root" and using that account in all its full unlimited God-like glory. If you crash your system you'll hopefully be experienced enough to fix it again too and not bother people here on this forum with that self-inflicted problem. ;)

---

### Post by CandyKiller on 2008-11-25
I did not **know** that you were unable to post tutorials about such things.

I was never given a reason to not access root, therefore the answer I received was very rude.  If they did not wish to share the knowledge in the first place they should of kept their mouth shut.  I was not pressuring anyone to giving me knowledge, nor do I expect anyone to "owe" me anything here.

Not needing access to a root account for that one process might not of been needed, but would of ended in the same effect.  Furthermore, it would be a nice bit of knowledge to know.

I obviously agreed to lower the security of my computer to do this task, due to it only taking a few moments.  I personally have never been hacked to my knowledge, even running in windows which I deem pretty easy to do. Considering that this is a fresh install of an OS as well it doesn't really seem necessary to have 6inch steel walls around it when there's a high possibility I might reinstall again.

Thank you everyone though for warning me about the reasons as to why I shouldn't use root, for the ones that did provide that information, it was a bit more helpful then the "don't ever ask again, you don't need to know, you can't" response I had gotten before.

---

### Post by chucky chuckaluck on 2008-11-25
> **scorp123 said:**
> This has nothing to do with it. Read that policy again.


being denied the knowledge is, in essence, being denied the choice. you kind of have a point about the forums not wanting to clean up someone's mess they might make while in root, but i really don't think there needs to be a punishment for informing someone of a feature of the system. it's not as if it were an apple in a beautiful garden somewhere.

---

### Post by scorp123 on 2008-11-25
> **CandyKiller said:**
>  How many times have you went to buy a new car, and couldn't find where to pop the hood at?  The car still works the same, you still get from point A to point B in it, but just because a car manufacturer might put the ejection handle in a tricky or unseen place means that the buyer doesn't have the knowledge to get under the hood and fix his vehicle?  That analogy is lacking. There is such a mechanism here, it's called "sudo" and it perfectly does what you want: it temporarily gives you root's rights and allows you to look under the hood and fix stuff if needed.

However, asking to enable "root" and run GUI stuff with full "root" powers (especially for something silly simple such as renaming _ONE_ single PNG file!) is like asking for a jackhammer to open the hood of your car ... Sure, you can open cars with a jackhammer. It's just total "overkill".

> **CandyKiller said:**
>  The fact that I haven't worked with linux before doesn't make me a total noob either, computers work the same, they all have the same function.  In theory, yes. But theory is just that: theory. If you don't know anything about UNIX-like OS'es it's very very easy to screw up your entire system in a blink. Been there, done that. When I was a noob back in 1995/1996 did people tell me not ever to login as "root"? Yes they did. On IRC. And they insulted me a lot back then. Did I listen? Nope. All computers work the same, right? If I can be logged in as "administrator" on Windows NT and nothing bad happens then I can also be logged in as "root" on Linux and nothing bad will happen, right? .... After horribly screwing up my installation back then I know better :D

You're free to repeat my mistakes of course :D

> **CandyKiller said:**
>  but you can't tell me Linux redefines the way computing is done in theory, that's laughable.  **[COLOR="Red"]It does.[/COLOR]** And that you find this "laughable" just shows how very little you know! :D

First of all, on UNIX-like OS'es [COLOR="Red"]**there is no handholding.**[/COLOR] Different than those crap OS'es from Microsoft a UNIX-like OS will never ever question your authority: You're the human in front of the terminal, you're the one with 1 billion+ brain cells, you're the one who is supposed to know what he does. And if you issue a command as "root" then there is [COLOR="Red"]nothing that will stop your command[/COLOR] from being executed. [COLOR="Red"]**You are "root". To the system you are it's God,**[/COLOR] your commands are to be executed without questioning, without asking stupid nonsense such as "Are you sure (y/n)?" ...

**And that's where the trap lies.**

This unlimited no-handholding-BS-do-as-I-say power of "root" makes Linux (and any other UNIX-like OS for that matter) a very very powerful tool ... **in the right hands.**

[B]But as a noob you have a very high chance of totally screwing up. It's a fact. As I said: been there. Done that. :D
[/B]
So simply believe us if we tell you that enabling "root" and working as "root" in a GUI environment is simply put a very stupid idea and one really fast way to totally screw up your computer, your files, your data.

In my case it was something simple as an unintentional "drag & drop" operation between two open file manager windows, and to make matters worse I accidentally hit on the middle mouse button while the pointer was hovering over an open "root" terminal which then copied and pasted tons of BS into this open "root" shell .... 

I should have listened and I paid for my mistake by being ridiculed on all IRC channels for the rest of the month. :D

But hey, you're welcome to repeat my mistakes and just ignore everyone's good advice here :)

---

### Post by scorp123 on 2008-11-25
> **chucky chuckaluck said:**
> being denied the knowledge is If you don't know how to enable "root" by yourself, then you better leave it be for you're lacking the necessary experience to treat the "root" account with the right levels of respect. On the other hand, if you have the right levels of knowledge and experience, you would not have to ask such things ;)

As twisted as this logic may be, there is a lot of truth in it.

And I fail to see why noobs should require that "feature" as you call it. It's definitely safer for them if "root" remains disabled as it is per default. Otherwise they might be tempted to work as "root" all the time. Been there + done that when I was a noob back in 1995/1996. And it was a mistake.

Disabling "root" on Ubuntu is in fact an excellent design decision, also from the security point of view. If there is a user account a hacker will search for on _every_ UNIX-like OS then it's "root", for the account simply exists everywhere. Thus disabling it and keeping it disabled keeps a lot of other dangerous trap doors locked ... trap doors you were most likely not even aware of.

---

### Post by -grubby on 2008-11-25
There's a happy medium:

```
sudo -i
```

Exactly like root, without everyone yelling at you

---

### Post by gn2 on 2008-11-25
> **chucky chuckaluck said:**
> being denied the knowledge is, in essence, being denied the choice. 

While these forums are an excellent resource, they are far from the sole source of information concerning Ubuntu.

---

### Post by miggys on 2008-11-25
First, let me say, I can follow rules whether or not I agree with them.  Still, I question the inspiration for the rules.  Did a mod simply say this is how I feel so I'm going to enforce on everybody...?  I don't know.  

Anyway, most of these posts here don't sit well with me pedagogically.  Most people who are posting are simply regurgitating information without really understanding it or giving explicit reasons.  Those who say: "it's a security risk/hackers could pwn you" probably don't really understand.

Also, I am not a fan of all these analogues that people try to use.  This is a computer.  It's cut and dry.  If you know why it should be done, it can be said explicitly.  Don't try to treat people as though information needs to be dumbed down.

Here's other possible analogues:  
1) ATM...you can get rid of password...but somebody said: it's a security risk...so you don't do it...some robber makes you go to ATM makes you get money...in your nervousness you don't punch in code correct...he gets mad and shoots you!!!

2) Some evil haxor remotely accesses your computer.  He starts doing bad stuff.  You go to kill the process he has started.  Uh-oh, he already changed root password!!!  If you were logged in as root, you wouldn't have to type in the password while all your illegally downloaded torrents were being ba-leeted or whatever.

Lastly, stop saying if you have to ask you don't have the knowledge.  WHAT???  you gotta learn somewhere...you ask on forums...you ask on google...you ask in an index of a book...it's impossible to learn without, in some sense, asking.  

Okay, I think I'm done :)

---

### Post by chucky chuckaluck on 2008-11-25
> **gn2 said:**
> While these forums are an excellent resource, they are far from the sole source of information concerning Ubuntu.

right, so someone finds out "on the streets" how to enable root, hose their system and still have to come here for help. it would be better for ubuntu to educate the user in using root safely rather than denying its existence.

---

### Post by wizard10000 on 2008-11-25
> **chucky chuckaluck said:**
> right, so someone finds out "on the streets" how to enable root, hose their system and still have to come here for help. it would be better for ubuntu to educate the user in using root safely rather than denying its existence.

I don't see anybody denying root's existence  ;)

I also see no reason for Ubuntu to support folks breaking their security model - as has already been stated if you want that particular piece of knowledge it's really not hard to find.

---

### Post by scorp123 on 2008-11-25
> **miggys said:**
>  2) Some evil haxor remotely accesses your computer. If you leave the "root" account disabled that hacker will have one hell of a hard time guessing any working account name ;)  And that's where your analogy is lacking ... how should the hacker remotely access anything if he can't even be sure which account will be working so he can focus on brute-forcing the password? With "root" enabled it's easy: Every UNIX-like OS has this account, all that's left for the hacker is to find a weakness and guess or brute-force the password.

But with "root" disabled the job gets frustratingly complicated. You first need to find a working account name. Unless you know a little something about your intended target that might just be impossible. If it's a multi-user system (e.g. a company's server) you'd need to find not only working accounts, but you'd also need to find the one(s) which can execute "sudo" ... More frustration. And even if you can get in via a system account (games, bin, daemon, mail, www, etc.) ... they are useless because none of them can execute "sudo". More frustration for the hacker.

I am not saying that it is impossible to hack an Ubuntu box ... but with "root" turned off as it is per default and with no additional knowledge about the target I'd say it should be quite hard for a hacker to get in.

> **miggys said:**
>  Uh-oh, he already changed root password!!!  Irrelevant. You still have your password and "sudo". Or you simply turn off the machine, and/or disconnect it from the network, and then do a recovery. For as long as you have physical access to the machine and the intruder doesn't you're always in the better position.

> **miggys said:**
>   If you were logged in as root, you wouldn't have to type in the password while all your illegally downloaded torrents were being ba-leeted or whatever. Being logged in as "root" and downloading crap from the Internet is in fact a very good way to get your machine infected with something ... basically the very same problem Windows has all the time. All it takes is someone stupid enough to open a web browser as "root" and go to a shadowy web site which tries to install some JavaScript BS and/or exploit a browser weakness ... bingo! Own3d. Because you were "root".

[COLOR="Red"]Again: working as "root" is a bad bad bad idea.[/COLOR]

> **miggys said:**
>  if you have to ask you don't have the knowledge. It's a fact. :D

---

### Post by scorp123 on 2008-11-25
> **chucky chuckaluck said:**
> it would be better for ubuntu to educate the user in using root safely  by educating people to use "sudo" they are doing exactly that ;)

---

### Post by gn2 on 2008-11-25
> **chucky chuckaluck said:**
> ~ and still have to come here for help. 

Nope, these forums are not the only source of help, no-one is compelled to use them.

Anyone wishing to use a root account in Ubuntu is perfectly at liberty to look elsewhere for support and guidance.

---

### Post by aysiu on 2008-11-25
The reasons for this policy have already been explained and repeated numerous times.

It has also, not only in this thread but also in the policy explanation, been mentioned several times that these forums are not the only source of information on Ubuntu, and it really takes only a simple Google search to find out how to log in as root graphically if you are that determined to find out.

If you really don't understand that after 5 pages, I don't see how another 5 pages will help you understand.

---

