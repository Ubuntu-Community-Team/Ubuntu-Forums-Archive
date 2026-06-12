---
title: "Linux Virus's"
date: 2006-04-18
forum: Desktop Environments
---

### Post by phil66 on 2006-04-18
New virus threatens Linux and Windows PCs

Virus writers have released Bi, a malware targeting both Linux and Windows, according to Kaspersky Labs. The malware targets the ELF (Executable and Linking Format) and PE (Portable Executable) file formats used in executables, including Windows' .exe and .dll files. The virus is only a proof-of-concept, however, such proofs are usually followed by a malicious version. The SANS Institute warns that Linux and Mac OS X users must drop their sense of invulnerability against viruses and start protecting themselves with antivirus products.

[http://www.techworld.com/security/news/index.cfm?NewsID=5752](http://www.techworld.com/security/news/index.cfm?NewsID=5752) 

All threads concerning use of anti-virus programs in Linux have a tendency to discourage users from installing protection.

Does not this script show that it is inevitable that Linux will be attacked and would it not be wise to start using protection now?

---

### Post by localzuk on 2006-04-18
Well, the thing with Linux and viruses/malware is that it can only execute in user space if ran in user space. So, if and only if it has access to root will it be dangerous.

Rather than install protection products, simply following the following should stop 99.9999% of problems:

Have a seperate admin account to the normal user account,
Make the /home partition non-executable (also the any temporary storage areas such as /tmp)
Don't try and execute software that you don't *know* the source of

Simple really... No need for a cpu and memory hogging anti-virus package.

---

### Post by angkor on 2006-04-18
[QUOTE=phil66]Does not this script show that it is inevitable that Linux will be attacked and would it not be wise to start using protection now?[/QUOTE]

The script shows that it is *possible* to write a virus for linux. Nothing new here. 

I'll start protecting my linux systems with antivir when someone actually succeeds in releasing a linux virus that can actually spread itself. To do that it would need root permissions and if someone releases a virus asking you for your root passwd I doubt it will spread widely.

On a side note. If you run a mission critical system you can choose to only install software from a trusted source (the ubuntu repositories), by that you greatly diminish the chance of installing malware on your system as some cracker would need to succeed in getting his code (which is there to see for everybody) in the repos

---

### Post by NeghVar on 2006-04-18
> The script shows that it is possible to write a virus for linux. Nothing new here. 

Exactly, especialy with the fact that when it actually was new a week ago we had 4 threads on it...

---

### Post by apjone on 2006-04-18
I think wth all threats, including virus/malware - Good operational practice is just as good as any anti-virus software. I just feel sorry for the few windows users who may be constantly logged in as root when using linux and are browsing the World Wide Mine Field !!

---

### Post by sxtz on 2006-04-18
[quote=localzuk]Well, the thing with Linux and viruses/malware is that it can only execute in user space if ran in user space. So, if and only if it has access to root will it be dangerous.[/quote]

but.. seeing as most of us use sudo here that are running *buntu, doesn't it follow that one could mistakenly run the program through whatever devious means some cracker worked out, and it could grab root privs the next time you use sudo?  

does this now mean that i have to have a sudoer account,  log out of my regular account, log into my priveleged account, <insert priveleged activity here>, log back out, then relog into my user acct?  all just to say... install a new package w/ synaptic? (i know i could just switch to console to log in and use apt[itude], but just as an example) 

  -ck

---

### Post by aysiu on 2006-04-18
[QUOTE=sxtz]but.. seeing as most of us use sudo here that are running *buntu, doesn't it follow that one could mistakenly run the program through whatever devious means some cracker worked out, and it could grab root privs the next time you use sudo?[/quote] I'm with sxtz on this one.

Even though not that many people answered this poll, [it appears that most users on these forums install from sources outside the repositories](http://www.ubuntuforums.org/showthread.php?t=116365).

If you have users who are dumb enough to download sketchy software, the password will be more of an enabler to malware than a block against it.

The sketchy software will ask for a password to be installed and then dumb user will think *good thing it's asking me for a password--I'm so secure not operating as root*, little knowing that the software is bringing a keylogger along with it.

---

### Post by skymt on 2006-04-18
I typically install from source what I couldn't find in the official repositories, and I usually install it in my home directory. That pretty much eliminates the "sketchy software" attack angle, limiting the damage done. The exception is Opera, which I downloaded from the official site, so I really doubt it has a keylogger built in.

---

### Post by angkor on 2006-04-18
[QUOTE=aysiu]If you have users who are dumb enough to download sketchy software, the password will be more of an enabler to malware than a block against it.[/quote]

What difference does it make to the dumb user? He / She is going to install the software anyway.

> The sketchy software will ask for a password to be installed and then dumb user will think *good thing it's asking me for a password--I'm so secure not operating as root*, little knowing that the software is bringing a keylogger along with it.

I'm not sure I follow this line of reasoning. We're talking about one **dumb** user here! :)

A password request is usually (in case of a not so dumb user) a point where the user might think: " Hey, why is this fun little  screensaver asking for my password?"

---

### Post by angkor on 2006-04-18
[QUOTE=sxtz]but.. seeing as most of us use sudo here that are running *buntu, doesn't it follow that one could mistakenly run the program through whatever devious means some cracker worked out, and it could grab root privs the next time you use sudo? [/QUOTE]

Maybe. And that is one of the reasons linux is very secure. A cracker needs to be able to write software that can do that. Most virii out there written by the infamous script-kiddies aren't *that* advanced. Futhermore this would-be virus could infect ubuntu users, yet would be harmless to a Debian user who doesn't even have sudo installed on his system.

I'll wait to install antivir on my box untill I see the first *working* virus for linux.

---

### Post by sxtz on 2006-04-18
[quote=aysiu]
Even though not that many people answered this poll, [it appears that most users on these forums install from sources outside the repositories]("http://www.ubuntuforums.org/showthread.php?t=116365").[/quote]

i have to admit i've done this as well,  in the case where the repos were carrying old versions that lacked functionality.. i had to make my  own debs of conky and openbox, for example.

unfortunately, there are methods to get through the measure of ONLY installing software from the repositories, such as using a man-in-the-middle attack to implant bad code in downloaded packages.  obviously this requires a set of special circumstances, but it's just an example.

a little proof? toy around with ettercamp for a while and see if you can sniff some passwords off of the other boxen on your network. it's in the repos.

---

### Post by agger on 2006-04-19
Of course, we should do well to remember that while Windows is much more vulnerable to attack these days, the first damaging virus attack actually exploited a buffer overflow on a Unix machine.

That being said, I believe the threat to Linux boxes - for everybody using the standard safe practises of not running as root, etc., as indicated in other posts - is still highly theoretical. Kaspersky Labs have a clear partisan interest, as have Grisoft, who have earlier announced the necessity  of antivirus checks on Linux.

OTOH, running antivirus checks on incoming mail is a nice courtesy to Windows users, I believe. But if you ever tried to clean up a malware-infected XP PC, you'd know Linux is really miles ahead in the security dept.

---

### Post by localzuk on 2006-04-19
I think people are missing what I said - I said that you have to take **some** precautions, such as those listed in my first post. If you don't or think 'oh it won't happen to me' is naive - so you should do something.

What I am saying is that you should make it so your 'normal' user does not have sudo priv's, and make it so your home dir (and temp dirs) is non-executable. That way, anything a person **does** download which is dodgy **cannot** be ran without messing around - which makes it more difficult for things to go wrong.

It takes 10 minutes of setting up to do these simple things, compared with having a virus scanner use 5% of your cpu cycles and 5% or more of your RAM constantly.

I also mentioned using software only from places you trust. This doesn't just mean using it from the repo's only, obviously, but it also means downloading from reputable sources - so only downloading a package from the original author site, from a linux magazine cd/dvd or similar. Checking the md5 sums also to ensure it is what it says it is. Also, trying to get signed packages is also a good thing - so you can check it for a digital GPG signature.

This is all better than using AV software.

However, you still have to be vigilant and not become complacent.

---

### Post by localzuk on 2006-04-19
To answer this directly, yes you should log out and back in to do admin tasks. Or simpler still, you could use the 'Create new session' function and have 2 accounts logged in seperately, or even use the console in order to run the commands instead.

Using an account with sudo is the same as using the root account - a bad idea.

---

### Post by lucia_engel on 2006-04-19
On another note:

[Torvalds creates patch for cross-platform virus]("http://software.newsforge.com/article.pl?sid=06/04/18/1941251")

Linus Torvalds was examining the virus and came across a kernel bug, which actually prevented the virus to propagate itself. The bug has now been patched.

---

### Post by angkor on 2006-04-19
[QUOTE=localzuk]I think people are missing what I said [/QUOTE]

I think people were replying to the original poster and not to your post. ;)

Agree with what you said though. It's good practice to be careful.

---

### Post by angkor on 2006-04-19
[QUOTE=localzuk]Using an account with sudo is the same as using the root account - a bad idea.[/QUOTE]

I disagree. Why is it the same?

When I run as root *all programs* I start are run as root. This is not the case when using a user that also has sudo priviliges.

---

### Post by uantuzri on 2006-04-19
[QUOTE=localzuk]What I am saying is that you should make it so your 'normal' user does not have sudo priv's, and make it so your home dir (and temp dirs) is non-executable. That way, anything a person **does** download which is dodgy **cannot** be ran without messing around - which makes it more difficult for things to go wrong.
[/QUOTE]

I totally agree with you. I havent been using Linux for a long time, but from the very first moment I saw that Linux was much safer than other OS because of the permissions and the sudo privileges. If necesary, you can take extra measures, as the one you said, though they are not essential for every computer or user.

Linux might not be unvulnerable, but fortunately, it makes it hard to viruses to get into the system.

---

### Post by uantuzri on 2006-04-19
[QUOTE=angkor]I disagree. Why is it the same?

When I run as root *all programs* I start are run as root. This is not the case when using a user that also has sudo priviliges.[/QUOTE]


I think that the difference is than when using sudo, it is expected to take at least some seconds thinking what you're doing. That doesn't happen when you start as root.

---

### Post by akshaysrinivasan on 2006-04-19
Actually there is a vulnerability,even though most of never log in as root,we use sudo command don't we?and when sudo executed within 1-2 minutes of the first execution,does not ask for a password,ther could be a potential virus exploiting this.it is only a matter of time before virus writers shift their focus to linux and mac OS

---

### Post by aysiu on 2006-04-19
[QUOTE=akshaysrinivasan]Actually there is a vulnerability,even though most of never log in as root,we use sudo command don't we?and when sudo executed within 1-2 minutes of the first execution,does not ask for a password,ther could be a potential virus exploiting this.[/QUOTE] That's a problem only with *gksudo* or *kdesu*, not *sudo*.

If you open a terminal and type a *sudo* command, you won't be prompted for a password again for fifteen minutes **in that window**.

However, if, within that fifteen minute time span, you open a new terminal window and type another *sudo* command, you **will** be prompted for another password.

So, unless someone can find a way to hijack the particular terminal session you have open (which is probably possible--I don't know), *sudo* is actually quite secure.

*gksudo* and *kdesu* don't operate this way, though. If, for example, I run ```
gksudo synaptic
``` I'll be prompted for a password. But if I run ```
gksudo nautilus
``` before the timeout, then I will **not** be prompted for a password.

In other words, if a program wanted to spawn a graphical application using root privileges within fifteen minutes of you typing *gksudo* something, it could.

---

### Post by localzuk on 2006-04-19
For the purpose of my post I mean that sudo is the same as root as in the account has the ability to run root software.

For example, if a keylogger was running in your session, under your username, all you would have to do is run a command using gtksu, sudo, kdesu or similar and the malware would then have root access to your system.

If you split your accounts and only allow admin stuff to be done in an account where you don't download random junk (so only get stuff from reputable sources), you severely reduce the chances of a keylogger being effective - as it would not be able to gain the root priv's.

Sudo **is** the same as root in my mind. The password check is there to double check that you want to run something as root - and this can be overcome by adding yourself to the 'sudo' group or adding NOPASSWD to the sudoers file for your username.

---

### Post by angkor on 2006-04-19
[QUOTE=localzuk]For the purpose of my post I mean that sudo is the same as root as in the account has the ability to run root software.

For example, if a keylogger was running in your session, under your username, all you would have to do is run a command using gtksu, sudo, kdesu or similar and the malware would then have root access to your system.

If you split your accounts and only allow admin stuff to be done in an account where you don't download random junk (so only get stuff from reputable sources), you severely reduce the chances of a keylogger being effective - as it would not be able to gain the root priv's.

Sudo **is** the same as root in my mind. The password check is there to double check that you want to run something as root - and this can be overcome by adding yourself to the 'sudo' group or adding NOPASSWD to the sudoers file for your username.[/QUOTE]


I see your point. 

It's just that I'm a user (with sudo permission) who, even if I sometimes *download* random junk, doesn't *install* random junk. Not as a user, sudo user, root or any other user for that matter. With that I don't need to reduce the chances of a keylogger being effective, I reduce the chance that a keylogger will be installed on my system.

---

### Post by localzuk on 2006-04-19
Ah, yes but what about accidental execution of stuff? I suppose if you set you /home and /tmp partitions to be non-executable then you would stop this happening but IIRC gnome now allows files to be executed by clicking on them does it not?

---

### Post by az on 2006-04-19
Nobody is taking this thing seriously.  It is not a virus, just code that seems to be executable on more than one platform.  Big deal.

A virus is something that penetrates your system without user interaction.  This is not the case.  On Windows, you cannot avoid this happening, you can just patch it.  As for linux, it is a completely different operating system and you can't really do that.  

Keep up to date with your security updates, but this is not a reason to install an antivirus.

Anyway, if there ever was the need, you can bet that the next day's ubuntu-desktop package would start depending on the appropriate software.  Not holding my breath, though.

---

### Post by angkor on 2006-04-20
[QUOTE=localzuk]Ah, yes but what about accidental execution of stuff? I suppose if you set you /home and /tmp partitions to be non-executable then you would stop this happening but IIRC gnome now allows files to be executed by clicking on them does it not?[/QUOTE]

Accidental execution? :-k  

I've never installed a program through the gui (save for using synaptic sometimes), you won't accidentally install a program in the terminal. ;)


I still see your point I just don't think the extra measure of creating a different sudo user is necessary atm. If you are careful that is.

---

### Post by nocturn on 2006-04-20
I would like to point out again that what they created is NOT a virus.

Viruses replicate automatically, this piece of code does not.  It requires you to run it manually on a Linux system and can only do damage outside of your own homedirectory if you run it as root.

So far, Linux has lacked the automated attack path that the monoculture on windows (like Outlook) has created.

---

### Post by nocturn on 2006-04-20
[QUOTE=sxtz]but.. seeing as most of us use sudo here that are running *buntu, doesn't it follow that one could mistakenly run the program through whatever devious means some cracker worked out, and it could grab root privs the next time you use sudo?  
[/quote]

Security is always a tradeoff.   In the minutes after entering your sudo password, a program that *is already active* could grab your credentials to do bad things.  You can limit this by switching of the cache and entering your password every single time.

> 
does this now mean that i have to have a sudoer account,  log out of my regular account, log into my priveleged account, <insert priveleged activity here>, log back out, then relog into my user acct?  all just to say... install a new package w/ synaptic? (i know i could just switch to console to log in and use apt[itude], but just as an example) 


I wouldn't recommend this actually.  Be carefull in what you execute outside of the repositories and have a good password.  That will get you a long way.

---

### Post by nocturn on 2006-04-20
[QUOTE=agger]Of course, we should do well to remember that while Windows is much more vulnerable to attack these days, the first damaging virus attack actually exploited a buffer overflow on a Unix machine.
[/QUOTE]

Although that is true, the lesson to be learned here is not that we need AV protection, which comes in too late in many cases, but that we need a better generic protection against attacks (PaX etc).  And we shouldn't rely on a software monoculture.

---

### Post by nocturn on 2006-04-20
[QUOTE=localzuk]
Using an account with sudo is the same as using the root account - a bad idea.[/QUOTE]

I really disagree.

If you log in as root, everything runs as root, including Gnome etc.
If you use sudo, you elevate your privileges only when needed.  Secondly, there's only one password to protect and you're more likely to change your user password regularly then your root password.

---

### Post by nocturn on 2006-04-20
[QUOTE=localzuk]Ah, yes but what about accidental execution of stuff? I suppose if you set you /home and /tmp partitions to be non-executable then you would stop this happening but IIRC gnome now allows files to be executed by clicking on them does it not?[/QUOTE]

Only if they have the x bit set.  
So you need to download something, and chmod +x it before clicking on it.  This is a very deliberate action and if you are willing to do this, nothing is going to stop you from executing that app.

---

### Post by localzuk on 2006-04-20
> 
Only if they have the x bit set.
So you need to download something, and chmod +x it before clicking on it. This is a very deliberate action and if you are willing to do this, nothing is going to stop you from executing that app.

I think you are underestimating the 'generic' non computer savy user. The average 'download and run first, ask questions later' user would run any old application... But then again, they likely wouldn't bother to check the source of a package either.

I think I am thinking in terms of my current home setup - where no-one (not even house mates) have root priv's to their own boxes, only I do. They agree that it is best and it seems to work well (sort of a corporate computer layout).

---

### Post by nocturn on 2006-04-20
[QUOTE=localzuk]I think you are underestimating the 'generic' non computer savy user. The average 'download and run first, ask questions later' user would run any old application... But then again, they likely wouldn't bother to check the source of a package either.
[/quote]

That's were Linux does at least better than many alternatives.  If your average you downloads uglyvirus.bin, he at least has to set the x bit which he is likely not capable of.

If he is, there is nothing to prevent him from logging in as root and executing rm -rf / when instructed to do so.  The only option is not to grant root access to him at all (or sudo).

[/quote]
I think I am thinking in terms of my current home setup - where no-one (not even house mates) have root priv's to their own boxes, only I do. They agree that it is best and it seems to work well (sort of a corporate computer layout).[/QUOTE]

Same here.  At home, I have an LDAP/Kerberos server that holds all authentication data.  Only my account has a root principal and it is the only one that has admin access on any of my boxes.

---

### Post by Epperly on 2006-08-03
So how likely, does everyone think, is it that there is going to be active viruses around in Linux (sooner or later)?

---

### Post by nocturn on 2006-08-03
> **phil66 said:**
> 
Does not this script show that it is inevitable that Linux will be attacked and would it not be wise to start using protection now?

The antivirus companies would love for this to happen, but as I stated before, AV is a flawed solution to the virus problem.

Basicly, Internet worms spread like wildfire and AV vendors are simply too slow to respond to it, not to mention the hidden agenda that allowed the Sony rootkit to florish for over a year without users being alerted.

If we want to be safer from viruses, we should look at having PaX by default and/or implement something like AppArmor.

Still, your default Ubuntu install is not at immediate risk even if it were trivial to write a Linux virus/worm because:
1. You have no open ports listening to the net (hence  nothing to attack directly)
2. There's nothing like ActiveX/Outlook that allows infection simply by visiting a rogue site or opening a mail
3. As long as you stick to the repositories for installing software, the chance of downloading a virus are pretty slim
4. You do not run as root, so any virus will be confined to your local user unless there is an application vulnerability that allows it to get root.

Again, the virus threat on *Nix is very real, yet AV is not a solution.

-- EDIT, I forgot that I already replied to this thread, one of   the downsides of a 3 week break :-)

---

### Post by nocturn on 2006-08-03
> **Epperly said:**
> So how likely, does everyone think, is it that there is going to be active viruses around in Linux (sooner or later)?

Very likely, nearing certainty.

Yet I hope that we implement a structural solution instead of adopting the band-aid that AV is.

---

### Post by Epperly on 2006-08-04
Oh, god... I was just foolin around and found antiviruses for Linux out already, so I scanned for the hell of it and it actually found a virus:
[IMG]http://img.photobucket.com/albums/v92/k20importtuner/Screenshot-Warning-1.png[/IMG]

---

