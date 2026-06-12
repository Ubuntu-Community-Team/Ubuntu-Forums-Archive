---
title: "Killing Ubuntu - what could be done to avoid this simple way to crash Ubuntu ?"
date: 2006-01-13
forum: Desktop Environments
---

### Post by kurtkraut on 2006-01-13
Hello,

Please watch this video:

[http://video.google.com/videoplay?docid=464540691509009245&q=linux](http://video.google.com/videoplay?docid=464540691509009245&q=linux)

(flash plugin is needed)

What could be done to avoid this ? As happens on Windows, pretty soon bad websites, SPAMs and etc will give fake information to the user to make commands such as 'sudo rm -rf /' by mistake.

Anyone got an idea ?

---

### Post by IsSuE on 2006-01-13
i really dont get your problem? who would use rm by chance?

---

### Post by kurtkraut on 2006-01-13
For instance,

A SPAM like this could be sent:

'Want better performance in you Ubuntu box ? Just try out sudo rm -rf /'

Or even bad people over IRC can give this command as a hint thru channels or private messages.

I know that it is not a problem of Ubuntu, it probably exists in all distros. But what scares me is that a very simple command, without any prompt canl brake the system without any easy recovery way.

I think developers should study a way of prompting a warning that damage could be done while using some comands such as 'sudo rm -rf /'.

Sorry for my english... but is now my point clear ?

Thanks.

---

### Post by Michael Steinberg on 2006-01-13
Since the guy filmed the process, i suspect he knew just what was going to happen. But even assuming that a user doesn't know what rm (or -r) means, I'm tempted to ask the question my mother used to pose: "If somebody told you to jump off the Brooklyn Bridge, would you do it?"

---

### Post by peteyp666 on 2006-01-13
I found this is google,
[http://sunportal.sunmanagers.org/pipermail/summaries/2005-April/006371.html](http://sunportal.sunmanagers.org/pipermail/summaries/2005-April/006371.html)

---

### Post by Michael Steinberg on 2006-01-13
I do see your point. (My post & yours crossed in the ether...) The problem is that there are lots and lots of ways to screw up a computer. One of the nice things about a GUI is that lots harder to make things unfixable using point-and-click than it is with the command line. If you're cautious stick to GNOME. 

Things will happen, of course. If you're going to mess around with the command line & sudo you should be careful. In an ideal world everyone would know that you shouldn't type in a line of commands unless you either know what it's going to do or know and trust the person who's telling you to do it. If some people DON'T know this, we have to balance the danger they pose to their own machines with the risk that making complex or major changes too idiot-proof will also make them too annoying for the people who know what they're doing.

---

### Post by kurtkraut on 2006-01-13
[QUOTE=Michael Steinberg]
Things will happen, of course. If you're going to mess around with the command line & sudo you should be careful. In an ideal world everyone would know that you shouldn't type in a line of commands unless you either know what it's going to do or know and trust the person who's telling you to do it. If some people DON'T know this, we have to balance the danger they pose to their own machines with the risk that making complex or major changes too idiot-proof will also make them too annoying for the people who know what they're doing.[/QUOTE]

Yes, I agree with you. But we shoud put our minds to work together in order to find a way to avoid or warn the user before he screws up the system without knowing what he is doing.

So, what could be done ? Change the code of 'rm' to make warnings before deleting essential files to the system ? Better user education, a 'DONT DO THIS' list in the newbie user guides ? Or this kind of issue (not only the rm -rf / command) should be left as it is at the moment ?

---

### Post by 23meg on 2006-01-13
"UNIX was not designed to stop its users from doing stupid things, as that would also stop them from doing clever things."

This is part of what people mean when they say that any OS shouldn't be totally "dumbed down" for the average Joe; Joe should still know in the first place that when he has to put "sudo" as a prefix to any command, he's executing it as superuser and making system-wide changes with it, and he has to know the function of the "rm" command, just like most DOS/Windows users know the function of the "format" command, or just like he knows that the engine of his car makes it go and its brakes make it stop.

---

### Post by Michael Steinberg on 2006-01-13
Aliasing rm so that it's equivalent to rm -i would make some people squawk that Ubuntu's a "newbie distro" but they're going to say that anyway; maybe it's not a bad idea as a preset. After all, if the decision was made to omit build-essential from Breezy, this one wouldn't be a big step at all. And you could do a pleasant warning for use of sudo, too, the way OS X does.--Apple's is along the lines of "I assume the system administrator has given you the usual lecture. It runs, more or less: 1. Don't type anything unless you know what it's going to do..." (I'd cut-and-paste the whole thing but it turns out not to warn you when you do "sudo -s" and my timestamp hasn't expired...)

---

### Post by peteyp666 on 2006-01-13
[QUOTE=23meg]Let me float the cliché quote once more; keep in mind that all clichés are true.

*"UNIX was not designed to stop its users from doing stupid things, as that would also stop them from doing clever things." --Doug Gwyn*

This is part of what people mean when they say that any OS shouldn't be totally "dumbed down" for the average Joe; Joe should still know in the first place that when he has to put "sudo" as a prefix to any command, he's executing it as superuser and making system-wide changes with it, and he has to know the function of the "rm" command, just like most DOS/Windows users know the function of the "format" command, or just like he knows that the engine of his car makes it go and its brakes make it stop.[/QUOTE]

I agree.  After the user fracks his system he learns at least two important things. 1) Don't trust everything you read on the internets.  and b)  Its best to learn about things before jumping right in.

---

### Post by lcg on 2006-01-13
[QUOTE=kurtkraut]Please watch this video:

[http://video.google.com/videoplay?docid=464540691509009245&q=linux](http://video.google.com/videoplay?docid=464540691509009245&q=linux)
[/QUOTE]
"Currently, the playback feature of Google Video isn't available in your country."

I understand it is about an inconsiderate 'sudo rm -rf /', though.

[QUOTE=kurtkraut]
What could be done to avoid this ? As happens on Windows, pretty soon bad websites, SPAMs and etc will give fake information to the user to make commands such as 'sudo rm -rf /' by mistake.

Anyone got an idea ?[/QUOTE]
When I started using Unix like systems, some of them (Redhat, e.g., IIRC)had an alias set

```
alias rm=rm -i
```
With that, 'rm' would ask you about every file. However, I didn't really like it because I might have started to rely on this "feature" and one day I would surely encounter a box where 'rm' behaves more traditonally. So I usually removed it (along with others like 'mv=mv -i'). Such an alias could be one solution to prevent users from frying their system.

Another one (which I usually have in place in my home to save me from my own stupidity) is

```
cd /
sudo touch -- -i
```
This will create a file '-i' in your /. 'rm' will interpret the filename as an option (just like in the alias above) and start asking about deleting each file. (BTW, the -- terminates the option list for touch, telling it that the -i is in fact the filename not an option. That's why 'sudo rm -rf -- /' would probably still work, though I feel no desire to test that right now. ;) )

HTH,
Lars

---

### Post by meborc on 2006-01-13
i don't see the point... this command has existed a long time... and NOW we have a problem? :) ... my point is that i want to have power over my computer and i want freedom to delete everything i want... :D ... and noone can stop me (evil laughter)

when i was steping into the linux world... i learned the command from some nice guy from the forums... and understood, that i shouldn't never try that UNLESS it is needed... there are a lot of commands that can harm your computer, that are also short... they may not delete everything, but sometimes you don't need to delete everything to lose it all :)

again... (i must put it into my sig): **[COLOR="DarkRed"]IF IT DOESN'T ITCH, DON'T SCRATCH[/COLOR]**

---

### Post by lcg on 2006-01-13
[QUOTE=meborc]there are a lot of commands that can harm your computer, that are also short...[/QUOTE]
Oh yes, there are. :) 'dd' e.g. can be quite destructive. Nothing more effective than writing pseudo-random data over the first 512 KB of your harddisk. (And no, I will not post the necessary command. ;-) If anyone wants to mess with their own or someone else's computer, they should at least read the man page themselves.)

Even if Ubuntu eliminated 'rm' as a threat for beginners, one could always come up with a different command to make someone kill his or her system.

Lars

---

### Post by kurtkraut on 2006-01-13
[QUOTE=meborc]i don't see the point... this command has existed a long time... and NOW we have a problem? :)[/QUOTE]

No, we don't have a problem yet. But shouldn't we think that people use their computer differently from the way you use ? You may never did such destructive command but there are many many many people among the Ubuntu users that don't know what **sudo** means and they are not familiar with the risk of **rm**.

So, if there is a simple command that can do a huge harm to the system when executed by a newbie user, why we shouldn't avoid this ? Why we shouldn't prompt a warn ? Why we shouldn't prevent the user from harming his system whenever it is possible ?

I do understand that different people have different opinions, and I respect that. But sometimes, talking to people about this subject I feel that they don't mind if the user crashs his own system because it would be like a punishment for 'doing stupid things/commands'.

What is the sin if the system says 'This operation my cause damage to your system. Are you sure do you want to proceed ?' and then you may click in OK or press Y to go on. If this kind of warning is set by default and you are a experienced user, it won't be hard for you disabling this warnings. So newbie users will be protected and experienced users won't be bodered.

---

### Post by 23meg on 2006-01-13
[QUOTE=kurtkraut]No, we don't have a problem yet. But shouldn't we think that people use their computer differently from the way you use ? You may never did such destructive command but there are many many many people among the Ubuntu users that don't know what sudo means and they are not familiar with the risk of rm.[/QUOTE]Then they should learn, easy or hard way. Or avoid the command line totally, if possible. But then they'd have to learn not to hit "delete" when their boot folder is selected in Nautilus, wouldn't they? It's all about learning, about some basic but essential knowledge.

---

### Post by kurtkraut on 2006-01-13
[QUOTE=23meg]Then they should learn, easy or hard way. Or avoid the command line totally, if possible. But then they'd have to learn not to hit "delete" when their boot folder is selected in Nautilus, wouldn't they? It's all about learning, about some basic but essential knowledge.[/QUOTE]

Ok, since it is essential knowledge, how it could be more easily provided to the user that is just experiencing linux for the first time with Ubuntu ?

---

### Post by 23meg on 2006-01-13
Maybe a "basic Linux commands" page can be put into the help section; something like [this]("https://wiki.ubuntu.com/BasicCommands") maybe.

---

### Post by Aaron Hoy on 2006-01-13
I dont see why anything needs to be done.  If someone enters a command without knowing what it does just because somone else told them to, that's their problem.  Its not anyones responsibility to prevent them from doing that.  Similarly, someone could call you on the phone and tell you that it would be cool idea to stab yourself in the chest, but I dont think its anyone's responsibility to integrate knifeproof vests into everyone's chest with a little sign that says "warning, you are about to stab yourself in the chest, this will make a big hole and alot of your blood will come out through it, are you sure you want to continue?"

---

### Post by Michael Steinberg on 2006-01-13
Isn't there also a kind of tention between Linux as the coders'/hackers' playground and Linux the free software works-out-of-the-box OS? We wouldn't have anything like the second if the first weren't such a drew for the bright people who put the Os together, and the tension's not going to vanish; but what's needed to maintain a totally open, adaptable, flexible and improvable system aren't the same things as what are needed to make a bulletproof system for everyday use in the local clerk's office as well as by your Grandmother in Bayonne, Heilbronn or Van......

---

### Post by 23meg on 2006-01-13
..hence the need for distros and the variety they provide. Every distro has its own goals and rules that it sets according to its user base and as far as I'm concerned Ubuntu isn't the kind of distro that should really do something about this "problem".

---

### Post by datajack on 2006-01-16
[QUOTE=23meg]Then they should learn, easy or hard way. Or avoid the command line totally, if possible. But then they'd have to learn not to hit "delete" when their boot folder is selected in Nautilus, wouldn't they? It's all about learning, about some basic but essential knowledge.[/QUOTE]


Agreed, but Ubuntu, like most Linux distros, encourages the use of non-root accounts, hitting delete in nautilus on the /boot folder shouldn't have any effect.

This problem isn't an Ubuntu problem, it isn't a Linux problem. Hell, it isn't even a *nix problem (it's just as easy to hose a Windows system, probably easier as most peeps run with administrator privs more or less all the time). It's a people problem. If people just follow instructions from an untrusted source blindly, they seriously need to sit down and get a clue. If you can't ever take responsibility for your own actions on your system or question things before doing them, the solution is simple - get someone who does know how to handle themselves to manage your system. Get a completely unprivileged account for yourself and give the 'keys' to your machine to a trusted person who can do the job.

---

### Post by kperkins on 2006-01-16
Well, as I see it "sudo rm -rf /" is a feature, not a bug. :D Anyone stupid enough to run it without finding out what it does pretty much deserves what they get. Linux isn't here to baby the users, it's here to let them do what they want on their systems, which means actually *learning* a little bit about it.  Using the car analogy (which is so popular) everyone should know how to change a tire, or their oil, and everyone should learn some basic commandline stuff.  They don't have to use it, but they should at least know how.
If you're going to dumb down Linux so that new users don't have to learn anything, then you might as well just tell them to use Windows, where it takes ***no*** user action to hose your system at all, which is why antivirus, and anti-spyware software is so needed on it. (see the Sony rootkit as the latest  example of this)

---

### Post by datajack on 2006-01-16
[QUOTE=kperkins]Using the car analogy (which is so popular) everyone should know how to change a tire, or their oil[/QUOTE]


I don't agree here. To my shame, I don't know precisely how to do those things on my car. However, I am more than happy to pay for someone at a garage to do it for me. They have skills, knowledge and interest where I don't. (Though faced with no other option, I'd probably be able to firgure it out easy enough).

The beauty of using potentially complex multi-user systems is that you _can_ tie down an account so that the user can do nothing more than what they need to do and therefore have virtually no chance of breaking their system. If the system needs an 'oil-change', then they get their 'mechanic' to deal with it.

---

### Post by nocturn on 2006-01-16
This is actually the Al Quada virus ;-)

Sorry to say, but there is nothing you can do about this type of attack.  One mitigating factor is that if you have a home PC (shared), at least your kids cannot be tricked into doing this (no sudo access).

There's also nothing you can do to avoid damage from Emails recommending that you microwave your HD for 1 minute to increase performance...

---

### Post by nocturn on 2006-01-16
[QUOTE=kurtkraut]
I think developers should study a way of prompting a warning that damage could be done while using some comands such as 'sudo rm -rf /'.
[/QUOTE]

That would not do much good, then you ammend the SPAM to say, "You will get a warning saying ..., please choose yes".

---

### Post by 23meg on 2006-01-16
[QUOTE=datajack]
Agreed, but Ubuntu, like most Linux distros, encourages the use of non-root accounts, hitting delete in nautilus on the /boot folder shouldn't have any effect.[/QUOTE]I know, but we often advise new users to use a root nautilus window to make system-wide changes instead of logging into X as root. Again basic knowledge: "don't leave a root app open, close it when you're done with it". If the user is unaware of this basic practice, it's a typical case of [PEBKAC]("http://en.wikipedia.org/wiki/PEBKAC").

---

### Post by nocturn on 2006-01-16
Let's say rm gets modified (like on Sun) not to allow this.

Next attack vector:
dd if=/dev/zero of=/dev/hda

so, modify dd to detect this, also dd_rescue...

cat /dev/zero > /dev/hda

or even
while true; do echo 1>/dev/hda; done

There is no end.

Securing rm would help guard against accidents though (thinking you do sudo rm -rf * in /tmp while you are in /)

---

### Post by mcduck on 2006-01-16
[QUOTE=Michael Steinberg]After all, if the decision was made to omit build-essential from Breezy, this one wouldn't be a big step at all.[/QUOTE]
How is that related? I wouldn't consider myself as a beginner with computers, or even Linux, but I still don't need to compile programs., and I'm happy that buid-essential isn't wasting my disk space.. If I need it, it only takes one command to install it anyway.

Anybody randomly executing commands from e-mails sent by unknown people would sooner or later break his/hers system anyway. Whatever is done to OS to prevent that, there is always to break your system, unless it's so crippled that it lacks to be usefull at all.. If somebody is ready to execute 'sudo rm -rf /' because some spam mail told to, and then types his/hers password to confirm that, why would any extra 'are you sure? y/n' help?

---

### Post by Miguel on 2006-01-16
My car's hood doesn't warn me:

* By Hitting the engine with a hammer, you may cause malfunction*
* Warning: Spilling nitric acid on the injectors will thrash your car*
* It is not advised to throw your car down a cliff*

What I mean is that we need both education and common sense. Are newbies vulnerable to those attacks? Probably. But then, we should educate them to sudo things they can understand, and only these things. There is a reason we are not logged in as root, isn't it?

Remember: the ability to fly also gives us the ability to crash into the ground.

But I must admit that using rm -rf as root doesn't seem much advisable unless you are ABSOLUTELY sure of your path and your target. Anyway...

OT: The imagination nocturn showed to thrash his system was cool! I must gain more experience in *nix to gain that ability ;)

OT2: touch, dd,... are those commands really helpful? I could imagine using touch on a hacked system, but dd? If someone would enlight me in my ignorace, I'd be grateful.

*EDIT: I forgot! IMHO,  the real danger lies in malicious debs which some phisher tricks the user into installing and then thrashing his system... in the best of cases (remember identity, theft, spionage,...).*

---

### Post by earobinson on 2006-01-16
This is not a bug, This is a feature.

sudo = super user = you know what you are doing. There is many many many ways that the super user can make the computer crash, by rming random files. As long as a normal user can not crash the computer that is all that matters.

---

### Post by nocturn on 2006-01-16
> **Miguel]
OT: The imagination nocturn showed to thrash his system was cool! I must gain more experience in *nix to gain that ability  said:**
> 

There's much more where this came from ;-)

> 
OT2: touch, dd,... are those commands really helpful? I could imagine using touch on a hacked system, but dd? If someone would enlight me in my ignorace, I'd be grateful.


Yes, they are.  many of them are used by other tools.  dd for example is very usefull to create an ISO or floppy image (and rewrite a floppy image).

dd if=/dev/cdrom of=copy.iso -> will copy a CD
dd if=/dev/fd0 of=floppy.dd -> will copy a floppy
dd if=floppy.dd of=/dev/fd0 -> will rewrite an identical floppy

[quote]
*EDIT: I forgot! IMHO,  the real danger lies in malicious debs which some phisher tricks the user into installing and then thrashing his system... in the best of cases (remember identity, theft, spionage,...).*

As long as you use repositories you trust (such as ubuntu), this danger is mitigated by the fact that the package list is signed (using PGP).  So uploading a rogue package is not that easy.
But downloading an infected .deb and using sudo dpkg -i will get you though... nothing to avoid this.

---

### Post by Miguel on 2006-01-17
[quote=nocturn]As long as you use repositories you trust (such as ubuntu), this danger is mitigated by the fact that the package list is signed (using PGP). So uploading a rogue package is not that easy.

But downloading an infected .deb and using sudo dpkg -i will get you though... nothing to avoid this.
[/quote]

Yes, I was referring to installing debs from the wild wild web, not the repositories. You know, not every site should be trusted and given full root access. It's kinda like installing programs in windows (though to a lesser degree). If you do it in a brainless way, chances are you will get "infected" (or rootkited or whatever). Sometimes there is no substitute to common sense.

Oh! And thanks for your info on dd.  As it copies things from /dev, I suppose this thing also copies filesystem and such, not just files. Am I wrong? (yes, it's a bit OT)

Have a nice day

---

### Post by datajack on 2006-01-17
[QUOTE=Miguel]Oh! And thanks for your info on dd.  As it copies things from /dev, I suppose this thing also copies filesystem and such, not just files. Am I wrong? (yes, it's a bit OT)[/QUOTE]

Yup, it will copy any data held in a file (devices are just files under *nix). So dd if=/dev/hda of=hdimage.dd will copy the whole disk, boot sector, partition table and all filesystems on that disk.

The command :

dd if=/dev/hda of=mbr.dd bs=512 count=1

Will create a abckup copy of the first sector of your hard disk, which is always useful if an install some other OS overwrites GRUB even though the new OS is installed in it's own partition. Such powerful tools will let you get things done that you can't do without them, but they are sharp, not blunted down kids toys.

Of course, you would research the dd command to verify what I'm saying before trying it :)

---

### Post by nocturn on 2006-01-17
[QUOTE=Miguel]
Oh! And thanks for your info on dd.  As it copies things from /dev, I suppose this thing also copies filesystem and such, not just files. Am I wrong? (yes, it's a bit OT)

Have a nice day[/QUOTE]

Yes, it does.   The nice thing is that dd can copy discs with filesystems that are not supported in the kernel (because it operates at block level).

The downside is that backing up a 10 GB partition with 4 GB of data will result in a 10 GB file (uncompressed).

---

### Post by nocturn on 2006-01-17
Blank every file on the system without using rm:

find / -type f -exec echo "" > "{}" ";"

Or symlink them

find / -type f -exec ln -s /dev/zero "{}" ";"

without find:

for i in `ls -R /`; do echo "" > $i; done

---

### Post by newuser111 on 2006-01-18
a nice educational clip, thanks for posting that

we must all be aware of the power of the sudo rm -rf / rm -r commands, especially in linux since you end up using this command a lot

what ubuntu needs is something like windows xp system file protection because windows boxes were just as easy to destroy before system file protection was introduced in windows ME, now it prevents the deletion of important system files

maybe there should be a way to setup the sudoers permissions so that certain rm -r commands cannot be executed (Such as in the / root)

---

### Post by Miguel on 2006-01-18
I beg to differ.

I don't think we need that windowslike "protection". Why? As you have seen from nocturn's examples, it's nearly trivial to kill your system without even using rm. And if we start "protecting" files, we will end up with a system full of uneditable files, which are the ones that allow us to set up the system exactly like we want to.

What we really need is better education. Never do anything as root (or with sudo) unless explicitly needed. Do not run non-admin programs as root (a game that required sudo comes to mind). If your non-admin job requires software that requires root, that software is badly done and a security concern to your system. And, of course, install things that come from trusted sites.

Remember, education. In the same way that driving a car also requires some training.

PS: There used to be a flaw in the vanilla kernel (2.6.8?) that only allowed cd burning to root. Of course, this was promptly fixed.

---

### Post by datajack on 2006-01-18
Windows file protection is only a half-way house. You are protecting the system from a group of people (who should not have permissions to delete those files anyway), but it becomes a total PITA should the system start protecting an incorrect or corrupted file.

---

### Post by linuxden on 2006-01-18
What about 

```
 sudo rm -r * 
```

---

### Post by hatstand on 2006-01-18
[QUOTE=Aaron Hoy]I dont see why anything needs to be done.  If someone enters a command without knowing what it does just because somone else told them to, that's their problem.  Its not anyones responsibility to prevent them from doing that.  Similarly, someone could call you on the phone and tell you that it would be cool idea to stab yourself in the chest, but I dont think its anyone's responsibility to integrate knifeproof vests into everyone's chest with a little sign that says "warning, you are about to stab yourself in the chest, this will make a big hole and alot of your blood will come out through it, are you sure you want to continue?"[/QUOTE]

Terrible analogy. For newbies such as myself (and i have moved - totally - because I simply hate Windows' propriety and economically monopolistic tendencies), there is nothing that screams "danger!" about an innoccuous looking rm command, whereas there is obvious danger in someone telling you to stab yourself.

I may be cautious enough to not follow advice but people used to being told what to input (Windows users trying to solve a problem or Linux newbies lloking for a solution without having to learn all the command line prompts on the How Tos) may not be. But, as you say, (and others on here seem to agree) "that's their problem". Thanks for the help and support. So much nicer than Microsoft. How dare we newbies not know commands? There is prevalent implication that you feel that Linux should be kept for command line literatiis and attempts to make it more user friendly (and therefore popular) will diminish it. Are you trying to keep it to yourself so you can say "I'm on Linux" in a smug, supercilious manner, implying a higher level of computer usage than mere GUI morons?

A much more helpful suggestion is by Miguel, who rightly says that education is the key (rather than learning from mistakes that can be data costly and offputting to prospective users, as others suggest). Maybe upon installation there could be a splash screen that gives exactly his advice? It could be optional: "Are you new to Linux? Yes/No".

---

### Post by MacV on 2006-01-19
I think the common line of thought of "Well, if he/she did that,then they deserve it and now learned from it" mentaility comes from the assumpsion that most "newbies" to Ubuntu(and linux in general) have some knowlage of not screwing up their computers. They obviously know how format and install the new OS(and sometimes dual boot), so they should know well enough to research linux commands and what they do. 

Of course,that's just my thought, and I';m feeling the same way as the others. How can a person just plug in any old commandline code and not know(or at least find out before hand) what it does? They spent the time researching their new OS, downloading it and installing it, you'd think they spend even more time on how to figure out how not to screw it up.

---

### Post by Galoot on 2006-01-19
This is a common enough trick that I heard about it years before I even looked at *nix. A similar one -- _echo y| deltree C:\*.* > nul_ -- floated around during the DOS era.

There is absolutely *no* way to stop a gullible user from doing something stupid to his PC--or to his microwave, car, table saw, furnace, whatever. There are too many ways to break things. The only way to safeguard against harming something is to forbid the user from touching it, and even that's not a sure thing.

BTW, don't cut toward yourself.

---

### Post by nocturn on 2006-01-19
[QUOTE=newuser111]a nice educational clip, thanks for posting that

we must all be aware of the power of the sudo rm -rf / rm -r commands, especially in linux since you end up using this command a lot

what ubuntu needs is something like windows xp system file protection because windows boxes were just as easy to destroy before system file protection was introduced in windows ME, now it prevents the deletion of important system files

maybe there should be a way to setup the sudoers permissions so that certain rm -r commands cannot be executed (Such as in the / root)[/QUOTE]

You could make your system file immutable 
[http://linuxhelp.blogspot.com/2005/11/make-your-files-immutable-which-even.html](http://linuxhelp.blogspot.com/2005/11/make-your-files-immutable-which-even.html)

This prevents even root from deleting them without removing the attribute first.

This function is in Ubuntu right now, but the attribute is not set on any files AFAIK.

---

### Post by nocturn on 2006-01-19
[QUOTE=hatstand]Terrible analogy. For newbies such as myself (and i have moved - totally - because I simply hate Windows' propriety and economically monopolistic tendencies), there is nothing that screams "danger!" about an innoccuous looking rm command, whereas there is obvious danger in someone telling you to stab yourself.
[/QUOTE]

Ok, the analogy is flawed because you can spot the danger of stabbing yourself at first glance.

But, the broader problem is trust.  As long as people blindly do what an anonymous person tells them to do, they will end up with harm.

Education is the only thing that can prevent this kind of damage, education and limiting access to the system (your kids do not need sudo).

This kind of thing is not limited to computers, I have seen people ruin cars or other electronics by trying something they heard would be cool.

I overheard a salesdrone on a computer market sell a PI CPU fan to someone who had just purchased an Athlon.  This person will destroy his processor for sure.

The point is that people need to learn the fine art of turst and distrust.  Even with education, you will sometimes be harmed, without, you are a sitting duck.

---

### Post by 23meg on 2006-01-19
[QUOTE=hatstand]Terrible analogy. For newbies such as myself (and i have moved - totally - because I simply hate Windows' propriety and economically monopolistic tendencies), there is nothing that screams "danger!" about an innoccuous looking rm command, whereas there is obvious danger in someone telling you to stab yourself.[/QUOTE]A better analogy: on a brand new car, there's nothing that screams "danger!" about a carburetor mod that a random mechanic can suggest to you that will totally ruin your engine, yet if you have absolutely no idea what a carburetor is and why it might be risky to do it, you may do it, and blow your engine. You'd do this because you'd trust the mechanic, and you'd trust the mechanic because you don't know about your car yourself.

You don't have to know about cars as much as mechanics do, if you won't make a living out of fixing cars, but as I said before, you have to know some basics; you have to know that the engine makes the car go and the brakes make it stop.

---

### Post by linuxden on 2006-01-19
In my view the main way someone would ever type in that command without knowing the consequences would be if they were instructed to do so by a third party... (perhaps some "VERY bad/Malicious advice on this site or another for that matter....)

Now IMO if someone were stoopid enough to post something like do that in the ubuntu forums they'd get caught out... 

I wouldn't worry about it too much...

windows like file protection, no thanks i dont want any file protection taking away some of the power from me!!!!! if i dont want files on a system to get deleted by stupid users i can set file ownerships...(but we are only talking here about personal desktops... right??)

---

### Post by datajack on 2006-01-19
[QUOTE=23meg]A better analogy: on a brand new car, there's nothing that screams "danger!" about a carburetor mod that a random mechanic can suggest to you that will totally ruin your engine, yet if you have absolutely no idea what a carburetor is and why it might be risky to do it, you may do it, and blow your engine.[/quote]

Precisely. I know nothing about my car's engine, therefore I don't touch it. If someone tells me that my carburretor needs changing, then I call in a mechanic.

> You'd do this because you'd trust the mechanic, and you'd trust the mechanic because you don't know about your car yourself.
If I'd gone to a reputable garage and their mechanic told me exactly what I needed to do, I may be able to do it myself. I would trust that mechanic and I can check his credentials and not worry about his motives.

However, If I'd gone to jazzedupboyracersforums.com and some random guy told me to do something, there's no way I would do it, at least without discussing it with a mechanic I trust.

If you know (independantly of the information telling you to do it) what the effects of an action will be, or the source of the information is clearly trustworthy (professionnal with a reputation to keep and/or liability for malicious info - Ubuntu staff members would count for that in this forum), then you will be OK carrying out the instructions, otherwise I would hang-fire until I could mentally tick either of those two 'boxes'.

---

### Post by MaX on 2006-01-19
But this is linux where talking about...

When I ran Gentoo I accidentaly did "rm -rf /" instead of "rm -rf ./",
it took me a while until i glanced at the terminal and saw that it couldn't delete
the stuff in /dev.

I killed the command but /bin was already gone... Linux still works though.
I didn't have ls but echo and I didn't have cp etc. But xchat/gaim and firefox worked and I fixed the system.

You can't protect people from doing stupid things.

---

### Post by Galoot on 2006-01-19
Sure you can, but it involves burying them up to their necks.

---

### Post by datajack on 2006-01-19
[QUOTE=Galoot]Sure you can, but it involves burying them up to their necks.[/QUOTE]

Heh, I like that.

I suppose you can stop them from doing stupid things, as long as you make them incapable of doing clever, inventive things.

---

### Post by 23meg on 2006-01-19
[QUOTE=datajack]Heh, I like that.

I suppose you can stop them from doing stupid things, as long as you make them incapable of doing clever, inventive things.[/QUOTE]
Right, as the quote goes..

[http://www.ubuntuforums.org/showpost.php?p=654068&postcount=8](http://www.ubuntuforums.org/showpost.php?p=654068&postcount=8)

---

### Post by kurtkraut on 2006-01-19
[QUOTE=hatstand]Terrible analogy. For newbies such as myself (and i have moved - totally - because I simply hate Windows' propriety and economically monopolistic tendencies), there is nothing that screams "danger!" about an innoccuous looking rm command, whereas there is obvious danger in someone telling you to stab yourself.

I may be cautious enough to not follow advice but people used to being told what to input (Windows users trying to solve a problem or Linux newbies lloking for a solution without having to learn all the command line prompts on the How Tos) may not be. But, as you say, (and others on here seem to agree) "that's their problem". Thanks for the help and support. So much nicer than Microsoft. How dare we newbies not know commands? There is prevalent implication that you feel that Linux should be kept for command line literatiis and attempts to make it more user friendly (and therefore popular) will diminish it. Are you trying to keep it to yourself so you can say "I'm on Linux" in a smug, supercilious manner, implying a higher level of computer usage than mere GUI morons?

A much more helpful suggestion is by Miguel, who rightly says that education is the key (rather than learning from mistakes that can be data costly and offputting to prospective users, as others suggest). Maybe upon installation there could be a splash screen that gives exactly his advice? It could be optional: "Are you new to Linux? Yes/No".[/QUOTE]

Your post summarize everything I wanted to say about this subject but my poor english didn't allow me to say. Thanks.

---

### Post by datajack on 2006-01-19
[QUOTE=23meg]Right, as the quote goes..[/QUOTE]

Dammit .. I knew it sounded too snappy for me to have thought it up mysefl. No intentional plagarism there, I assure you.

---

### Post by ardchoille on 2006-01-19
[QUOTE=kurtkraut]Hello,

Please watch this video:

[http://video.google.com/videoplay?docid=464540691509009245&q=linux](http://video.google.com/videoplay?docid=464540691509009245&q=linux)

(flash plugin is needed)

What could be done to avoid this ? As happens on Windows, pretty soon bad websites, SPAMs and etc will give fake information to the user to make commands such as 'sudo rm -rf /' by mistake.

Anyone got an idea ?[/QUOTE]
I have an idea.. educate yourself. I learned early on to never run a command given to me by a total stranger without first reading the man page of that command.

Someone once told me to "rm -rf /" and I refused to do that until I read the man page. Then I found out that it was a command given to me by a malicious person to harm my box. I remembered that person and refuse to follow any of their advice in the future.

Instead of "dumbing down" Linux, why not educate users instead?

---

### Post by kurtkraut on 2006-07-12
I've heard that OpenSolaris has some '**rm -rf**' protection. The example given to me that this system won't allow you to delete 'the root directory'.

It is not clear for me if it is **/home/root** or just **/**. But is it well known that OpenSolaris is not a user-friendly sytem and they are starting to give some attention to the things discussed here.

In my country (Brazil) suicide is considered a crime. It is a homicide that the criminal, and the victim is the same person. Of course there is no trial with attouneys etc when that happen but it is a demonstration of our state's philosophy that the law must protect the citzen even from himself.

I think Ubuntu should at least attemp to do the same.

---

