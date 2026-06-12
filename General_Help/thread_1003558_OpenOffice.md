---
title: "OpenOffice"
date: 2008-12-06
forum: General Help
---

### Post by sam1993 on 2008-12-06
Hi there guys,

I successfully got Xubuntu to install on my Evo N200. I am now wanting to install OpenOffice on my laptop, could someone supply a link because I dont know what Linux one to download.
Also once I have downloaded the file is it a simple .exe install process or do I need to do a few things, if so what are they and how do I do them. I am a total Linux novice, first ever time of using Linux :)

I would be grateful for your help :)

---

### Post by OrangeCrate on 2008-12-06
To get OOo, go Menu > System > Synaptic Package Manager, and search for openoffice.org. Install that mega package, and you'll have it.

---

### Post by sam1993 on 2008-12-06
> **OrangeCrate said:**
> To get OOo, go Menu > System > Synaptic Package Manager, and search for openoffice.org. Install that mega package, and you'll have it.

Okay, cheers mate:)

I need to download the package first though, dont I? What package do I need to download? Linux 32?

---

### Post by mikewhatever on 2008-12-06
> **sam1993 said:**
> Okay, cheers mate:)

I need to download the package first though, dont I? What package do I need to download?

Synaptic will download and install everything for you.
[Software Installing Guide]("https://help.ubuntu.com/8.04/add-applications/C/index.html")

---

### Post by sam1993 on 2008-12-06
Would it be easier to download the linux package onto CD on my Desktop computer then open up Software sources and install it that way? Or is OpenOffice on the Xubuntu Alternate CD?

---

### Post by linux_tech on 2008-12-06
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by TeXtonyx on 2008-12-06
> **sam1993 said:**
> Would it be easier to download the linux package onto CD on my Desktop computer then open up Software sources and install it that way? Or is OpenOffice on the Xubuntu Alternate CD?

No, it would be easier to use Synaptic as people have told you.
If you tried Synaptic and its not working, that is what you should
report. There is a way to install OOo 3.0 manually:

[http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)

It has been recommended to use, sudo dpkg -i -R when installing
the *.deb files, rather than just sudo dpkg -i, maybe it matters.

---

### Post by sam1993 on 2008-12-06
> **TeXtonyx said:**
> No, it would be easier to use Synaptic as people have told you.
If you tried Synaptic and its not working, that is what you should
report. There is a way to install OOo 3.0 manually:

[http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)

It has been recommended to use, sudo dpkg -i -R when installing
the *.deb files, rather than just sudo dpkg -i -R, maybe it matters.

I will try Synaptic then.

What is sudo dpkg -i -R? I am a complete novice.

---

### Post by OrangeCrate on 2008-12-06
> **sam1993 said:**
> Would it be easier to download the linux package onto CD on my Desktop computer then open up Software sources and install it that way? Or is OpenOffice on the Xubuntu Alternate CD?

When you find that package in Synaptic that I outlined in my previous post, right click on the empty box to the left of the entry, and choose "Mark for Installation". Then go to the top of the page, and click "Apply". It'll then install Openoffice for you.

You admit you're new to Ubuntu and Linux. Don't get get over your head by installing third party repos, or deb packages from various websites. Stick to the repositories for what you need, and you'll be happier, and safer from a security standpoint, if you do.

---

### Post by ASK87 on 2008-12-06
@sam1993

When you want to know about a command try
```
man t*he_command*
```

Its very simple

---

### Post by sam1993 on 2008-12-06
> **OrangeCrate said:**
> When you find that package in Synaptic that I outlined in my previous post, right click on the empty box to the left of the entry, and choose "Mark for Installation". Then go to the top of the page, and click "Apply". It'll then install Openoffice for you.

You admit you're new to Ubuntu and Linux. Don't get get over your head by installing third party repos, or deb packages from various websites. Stick to the repositories for what you need, and you'll be happier, and safer from a security standpoint, if you do.


Okay, I have installed Linux as it's faster, dont need games for my Laptop and also want to learn what Linux has to offer and also what Linux can achieve. 

So just stick to installing programs using Synaptic are you saying? How long will it take to be use it well? A couple of months?

---

### Post by jocko on 2008-12-06
> **sam1993 said:**
> I will try Synaptic then.

What is sudo dpkg -i -R? I am a complete novice.

If you just use synaptic, you will not have to bother with "sudo dpkg -i -R".
Just open up synaptic and search for a package named "openoffice.org". Mark it for installation and press apply.

---

### Post by timjohn7 on 2008-12-06
> **sam1993 said:**
> Okay, I have installed Linux as it's faster, dont need games for my Laptop and also want to learn what Linux has to offer and also what Linux can achieve. 

So just stick to installing programs using Synaptic are you saying? How long will it take to be use it well? A couple of months?

Welcome!  I was in your position about a year ago.  I am nowhere near expert, and I still have a few problems to sort out, but I would never look at going back to Windows as my OS.

If you are an average PC user, you should be running the full OpenOffice suite within days if not hours.

More complex packages may take a little longer, but no longer than their Windows equivalents (The GIMP has an equivalent learning curve to Photoshop, Scribus to Quark etc)

Although jocko says to not worry about the command line, you may well come to embrace it.  It's often quicker than its GUI equivalent, and many of the commands become second nature. Synaptic is a simple, secure option and provides a good interface so certainly look there as first option.

Based on my experience, you will have some problems and frustrations.  Come to this forum and search for answers.  We've all been there and many posts marked [SOLVED] will ease your pain.  When you ask a question, state it in detail and the help will surprise you.  Hang in there and you will be up and running early on.

What sort of apps do you currently use?  I have evaluated a few Windows vs Linux alternatives over thae last year, so perhaps can save you some time.

---

### Post by OrangeCrate on 2008-12-06
> **sam1993 said:**
> Okay, I have installed Linux as it's faster, dont need games for my Laptop and also want to learn what Linux has to offer and also what Linux can achieve. 

So just stick to installing programs using Synaptic are you saying? How long will it take to be use it well? A couple of months?

Whenever neighbors and friends ask me to help them learn about Linux, and Ubuntu, I have them start by reading these to sources:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Then, I suggest they get a fresh cup of coffee (or a cold beverage of their choice), and start Googling things they didn't understand from those two documents. Those searchs will lead to new things to read, and on and on they will go, developing a knowledge base...

One big difference between open source software, and closed source software such as Windows, is that there is no customer service department to call to get help.

Recent converts to Linux must take the time to learn the systems on their own. Forums such as this, are available to help with specific problems, of course, but Linux knowledge and expertise comes from a lot of self study, and that responsibility lies in the hands of the user.

With that said, it's nice to have you here. As you gain expertise, jump in and help others. From the newest noobie, to the most experienced users, to the staff, we're all volunteers just trying to help others, and strengthen the Linux community.

---

### Post by TeXtonyx on 2008-12-06
> **jocko said:**
> If you just use synaptic, you will not have to bother with "sudo dpkg -i -R".
Just open up synaptic and search for a package named "openoffice.org". Mark it for installation and press apply.

There is a way to install OOo 3.0 manually:

[http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)

It has been recommended to use, sudo dpkg -i -R when installing
the *.deb files, rather than just sudo dpkg -i , maybe it matters.

One goes to the webpage provided and reads the instructions.
One of the instructions on the webpage says sudo dpkg -i foo.deb
That is part of the process of installing OpenOffice 3 manually.

Why did I provide that method after I recommended Synaptic?
Because the openoffice 3 package was withdrawn from the
repository as of a couple of days ago, maybe it has been fixed
by now. Doing the openoffice install manually works around the
problem of Synaptic not working to install openoffice 3.

[http://tldp.org/guides.html](http://tldp.org/guides.html)  (free download, ATTN: OP)
Introduction to Linux - A Hands on Guide

version: 	1.27
author: 	Machtelt Garrels, <tille>
last update: 	Jun 2008
ISBN: 	1596821124
available formats: 	

   1. HTML (read online)
   2. HTML (read online, single file, 800k)
   3. HTML (tarred and gzipped package, 1.1M)
   4. PDF (1.6M)

---

### Post by sam1993 on 2008-12-06
> **timjohn7 said:**
> Welcome!  I was in your position about a year ago.  I am nowhere near expert, and I still have a few problems to sort out, but I would never look at going back to Windows as my OS.

If you are an average PC user, you should be running the full OpenOffice suite within days if not hours.

More complex packages may take a little longer, but no longer than their Windows equivalents (The GIMP has an equivalent learning curve to Photoshop, Scribus to Quark etc)

Although jocko says to not worry about the command line, you may well come to embrace it.  It's often quicker than its GUI equivalent, and many of the commands become second nature. Synaptic is a simple, secure option and provides a good interface so certainly look there as first option.

Based on my experience, you will have some problems and frustrations.  Come to this forum and search for answers.  We've all been there and many posts marked [SOLVED] will ease your pain.  When you ask a question, state it in detail and the help will surprise you.  Hang in there and you will be up and running early on.

What sort of apps do you currently use?  I have evaluated a few Windows vs Linux alternatives over thae last year, so perhaps can save you some time.

Okay, I see where you are coming from. It will take me a while obviously to learn a new Operating System.
I am going to be using Linux for things like programming, word processing and learning how to hack legally - hacking my own systems to gain more experience in computers. I also have to find other tasks Linux is good for and learn those tasks.

I will stay with Windows on my main desktop, might put another hard drive in on raid though, so I have more memory and I will also dual boot it with Windows Vista Premium which I am running currently and have Linux as the other OS, so then I can chose between each one. Also going to buy a cheap laptop off of my mate you refurbs laptops and does a load of other stuff with computers, buy a cheap dual core, 2GB, 200GB laptop off of him and dual boot that also with Windows and Linux.

> Whenever neighbors and friends ask me to help them learn about Linux, and Ubuntu, I have them start by reading these to sources:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Then, I suggest they get a fresh cup of coffee (or a cold beverage of their choice), and start Googling things they didn't understand from those two documents. Those searchs will lead to new things to read, and on and on they will go, developing a knowledge base...

One big difference between open source software, and closed source software such as Windows, is that there is no customer service department to call to get help.

Recent converts to Linux must take the time to learn the systems on their own. Forums such as this, are available to help with specific problems, of course, but Linux knowledge and expertise comes from a lot of self study, and that responsibility lies in the hands of the user.

With that said, it's nice to have you here. As you gain expertise, jump in and help others. From the newest noobie, to the most experienced users, to the staff, we're all volunteers just trying to help others, and strengthen the Linux community.


Thank you for the links, I will have a look at them. I know it is going to take a while to learn that but I am one of those guys who likes to dive straight in but, with Linux it seems that I cant dive straight in, I will have to take it slow and learn the OS like I did when starting on Windows.

---

### Post by sam1993 on 2008-12-06
> **ASK87 said:**
> @sam1993

When you want to know about a command try
```
man t*he_command*
```

Its very simple

So, when I go into the terminal, I put in:
```
man the_command
```
And it came up with No Manual entry for the command. 
Do I have put anything else in besides:
```
man the_command
```

Sorry about double post.

---

### Post by Arup on 2008-12-06
I would strongly recommend sticking to the OO2.4 in the regular Ubuntu repos. I have tried all other methods including installing OO 3 from the repos via adding the launchpad link and via the deb method. The deb method works but in my opinion, the Ubuntu in the repos is made by the go-oo team and is highly optimized, not only that, its updated frequently by the Ubuntu team and all bugs are patched. On the version 3 you are dependant on the OO team for updates and since it has not been fully tested by team Ubuntu, there could be issues arising from future Ubuntu upgrades so do bear this in mind.

---

### Post by OrangeCrate on 2008-12-06
> **sam1993 said:**
> 

<snip>

Thank you for the links, I will have a look at them. I know it is going to take a while to learn that but I am one of those guys who likes to dive straight in **but, with Linux it seems that I cant dive straight in, I will have to take it slow and learn the OS like I did when starting on Windows**.

That's right. Following my own suggestions in my last post ^, it didn't take long to get a good grounding in Linux.

It's a pretty cool operating system, and once you get used to it, my prediction is, that there will be no other one for you. There certainly isn't for me, and I still don't know a lot of the insides of the system. But, I have to honestly tell you, that I don't really have the time to learn that stuff, nor the interest. I just know the basic systems, I know how to use many of the programs, and I have customized Ubuntu for my own personal needs. That's more than enough to be happy.

:)

---

### Post by sam1993 on 2008-12-06
> **OrangeCrate said:**
> That's right. Following my own suggestions in my last post ^, it didn't take long to get a good grounding in Linux.

It's a pretty cool operating system, and once you get used to it, my prediction is, that there will be no other one for you. There certainly isn't for me, and I still don't know a lot of the insides of the system. But, I have to honestly tell you, that I don't really have the time to learn that stuff, nor the interest. I just know the basic systems, I know how to use many of the programs, and I have customized Ubuntu for my own personal needs. That's more than enough to be happy.

:)

Thanks for your help, I am very grateful:)
I am interested in such things like programming is because, I am wanting to become a software and web developer when I am older, so I find it very interesting. I will learn how to use Linux before I start to program on it or start to hack my own systems using it.

---

### Post by ASK87 on 2008-12-06
> **sam1993 said:**
> So, when I go into the terminal, I put in:
```
man the_command
```
And it came up with No Manual entry for the command. 
Do I have put anything else in besides:
```
man the_command
```

Sorry about double post.

No i meant to learn about any command (say-dpkg) just type
```
man dkpg
```

likewise try for any new command you come across.

PS: I am also switching to linux completely, now its hard for me to use windows. Good to see people switching to Linux.

---

### Post by linux_tech on 2008-12-06
dpkg -i installs the package. If -R option is specified, the package must refer to a directory.  It specifies to recursively handle all regular files matching pattern *.deb found at specified directories and all of its sub-directories.

---

### Post by sam1993 on 2008-12-06
> **ASK87 said:**
> No i meant to learn about any command (say-dpkg) just type
```
man dkpg
```

likewise try for any new command you come across.

PS: I am also switching to linux completely, now its hard for me to use windows. Good to see people switching to Linux.

Okay. But, How can you find Windows hard to use, it's the most easiest OS to use lol.

> dpkg -i installs the package. If -R option is specified, the package must refer to a directory. It specifies to recursively handle all regular files matching pattern *.deb found at specified directories and all of its sub-directories.

Okay, thanks :)

---

### Post by ASK87 on 2008-12-06
LOL, ya thats true. After using Linux for a long time, Windows seems diff for me. Thats what i meant...

---

### Post by TeXtonyx on 2008-12-06
> **sam1993 said:**
> So, when I go into the terminal, I put in:
```
man the_command
```
And it came up with No Manual entry for the command. 
Do I have put anything else in besides:
```
man the_command
```

Sorry about double post.

the_command means substitute the particular command you want help with.

man dir
man ls
man tr
man cp

His idea of "the_command" was to generalize a procedure of instances

*.deb the * means for each and every .deb file and so could mean 
very many of them. It's an idea about how to talk about all the cases,
rather than listing them one at a time.

---

### Post by sam1993 on 2008-12-06
I opened up Synaptic and in quick search I put in - openoffice.org And no searches called openoffice appeared. Do I need to add any servers?

---

### Post by TeXtonyx on 2008-12-06
> **sam1993 said:**
> I opened up Synaptic and in quick search I put in - openoffice.org And no searches called openoffice appeared. Do I need to add any servers?

Do not put in " - openoffice.org " only put in the search window,

openoffice

that is the name of the program, openoffice.org is its website.
Don't confuse this with adding a repository, which is likely, aok.
So if you wanted thunderbird, or firefox, or emacs you'd just put,

thunderbird

firefox

emacs

into the Synaptic search window and start the search.

---

### Post by sam1993 on 2008-12-06
> **TeXtonyx said:**
> Do not put in " - openoffice.org " only put in the search window,

openoffice

that is the name of the program, openoffice.org is its website.
Don't confuse this with adding a repository, which is likely, aok.
So if you wanted thunderbird, or firefox, or emacs you'd just put,

thunderbird

firefox

emacs

into the Synaptic search window and start the search.

Oh I see. I am pretty good on computers but, using Linux makes me feel thick lol.

---

### Post by sam1993 on 2008-12-06
Sorry for double post. When I put in openoffice, no searches appear. I click search, chose Look in, name and then search for openoffice. And nothing comes up. Why is this, do I need to do anything?

Could it take around 20 minutes for it to find the file?

---

### Post by sam1993 on 2008-12-06
Anyone able to help?

---

### Post by sam1993 on 2008-12-06
All installed now. Took a while for it to find the file but it did in the end. Now just have to get my Wifi card working lol. Any other good applications/software for Linux?

---

### Post by TeXtonyx on 2008-12-06
> **sam1993 said:**
> All installed now. Took a while for it to find the file but it did in the end. Now just have to get my Wifi card working lol. Any other good applications/software for Linux?

Yes, you betcha! There are two programs, LaTeX and Emacs that will
help you write great papers and your thesis. The basis for LaTeX
is TeX, invented by Don Knuth of Stanford and is almost perfectly
bug free. I think that is because he has the same birthday as me ;)

Of course you can also write a thesis in OpenOffice Writer. Here
is a video,   [http://www.mininova.org/tor/1077782](http://www.mininova.org/tor/1077782) 

And a 400 page guide [http://www.vodes.net/ooguide.pdf](http://www.vodes.net/ooguide.pdf)
which is all about using OpenOffice Writer. [free!]

---

### Post by sam1993 on 2008-12-06
Could you tell me of any good programs I can get that are good for script writing and C++/C#/PHP/CSS/HTML? I have had a look to see if there are any programming tools already installed and I cant find any.

---

### Post by thomas228 on 2008-12-06
> **Arup said:**
> I would strongly recommend sticking to the OO2.4 in the regular Ubuntu repos. I have tried all other methods including installing OO 3 from the repos via adding the launchpad link and via the deb method. The deb method works but in my opinion, the Ubuntu in the repos is made by the go-oo team and is highly optimized, not only that, its updated frequently by the Ubuntu team and all bugs are patched. On the version 3 you are dependant on the OO team for updates and since it has not been fully tested by team Ubuntu, there could be issues arising from future Ubuntu upgrades so do bear this in mind.

Hi 
I know you've solved your 00o3 installation problem but after reading the following article [http://www.linux.com/feature/154364]("http://www.linux.com/feature/154364") it appears that the go-oo team has finished the ubuntu 00o3 version.

I think I'll try it:D

Does anyone know if hardy will support it?

Thanks
Tom

---

### Post by TeXtonyx on 2008-12-06
I did the manual install a few days ago on Hardy and it worked.

---

### Post by TeXtonyx on 2008-12-06
> **sam1993 said:**
> Could you tell me of any good programs I can get that are good for script writing and C++/C#/PHP/CSS/HTML? I have had a look to see if there are any programming tools already installed and I cant find any.

Yes, but you can get python and perl and gcc is a c compiler I think.

But for writing scripts, Bash has a great reputation. There is a 
guide 800+ pages that teaches a bit of programming and mucho scipting.

[http://tldp.org/guides.html](http://tldp.org/guides.html)
Advanced Bash-Scripting Guide

version: 	5.5
author: 	Mendel Cooper, <thegrendel(at)theriver.com>
last update: 	Nov 2008

"This document is both a tutorial and a reference on shell 
scripting with Bash. It assumes no previous knowledge of 
scripting or programming, but progresses rapidly toward an 
intermediate/advanced level of instruction. The exercises and 
heavily-commented examples invite active reader participation. 
Still, it is a work in progress. The intention is to add much 
supplementary material in future updates to this document, as 
it evolves into a comprehensive book that matches or surpasses 
any of the shell scripting manuals in print."

Writing scripts usually requires a good knowledge of regualr
expressions, and though there is a chapter in ABSguide, the
book Master Regular Expressions is the perennial standard.

---

### Post by sam1993 on 2008-12-07
> **TeXtonyx said:**
> Yes, but you can get python and perl and gcc is a c compiler I think.

But for writing scripts, Bash has a great reputation. There is a 
guide 800+ pages that teaches a bit of programming and mucho scipting.

[http://tldp.org/guides.html](http://tldp.org/guides.html)
Advanced Bash-Scripting Guide

version: 	5.5
author: 	Mendel Cooper, <thegrendel(at)theriver.com>
last update: 	Nov 2008

"This document is both a tutorial and a reference on shell 
scripting with Bash. It assumes no previous knowledge of 
scripting or programming, but progresses rapidly toward an 
intermediate/advanced level of instruction. The exercises and 
heavily-commented examples invite active reader participation. 
Still, it is a work in progress. The intention is to add much 
supplementary material in future updates to this document, as 
it evolves into a comprehensive book that matches or surpasses 
any of the shell scripting manuals in print."

Writing scripts usually requires a good knowledge of regualr
expressions, and though there is a chapter in ABSguide, the
book Master Regular Expressions is the perennial standard.

Thanks for the link and telling me a good program. I will download it tomorrow. I have a question though, is the scripting shown in the tutorial only for doing certain things in Linux or can it also be used for other tasks. I ask this because you can do a lot of tasks with scripts - such like, hacking, writing scripts to Digital boxes and so on. So will the tutorial show me a lot of tasks that can be carried out with scripts that aren't all Linux orrientated. I hope you can understand what I mean/saying, I am very tired, so it may not make much sense. I will explain again if you can understand what I mean :)

---

### Post by sam1993 on 2008-12-08
Bump ^

---

### Post by sam1993 on 2008-12-08
Can anyone tell me some good programs to put on Linux and what **good programming** applications/software is out there for Linux?
I need something to make Linux more fun, I have mainly got it to start to learn hacking as a hobby but not using it in a malicious manner. I just need something to start me off enjoying Linux. I am thinking of dual booting it on Vista, dont know yet.

---

### Post by TeXtonyx on 2008-12-08
> **sam1993 said:**
> Can anyone tell me some good programs to put on Linux and what **good programming** applications/software is out there for Linux?
I need something to make Linux more fun, I have mainly got it to start to learn hacking as a hobby but not using it in a malicious manner. I just need something to start me off enjoying Linux. I am thinking of dual booting it on Vista, dont know yet.

Emacs and vim are used as programming editors. Emacs is programmable
and one can write macros. It has something like templates to check
code for different programming languages. It can surf the internet
and send email. I don't know if its fun, because to start with
there is a lot to learn. Scripts are good for doing things to
webpages, and administrative tasks, searching for exact text
that comes *just* at the ends of lines. You can string a lot of
linux commands together to do complicated stuff. But programs
are usually created with programming languages and they do big
things like Gimp does a lot of image work. For instance about
webpages, you might want to add "next" and "previous" navigation
boxes at the bottom of a lot of webpages because at just the 
top, is not good enough. Can you imagine doing that manually to
800 pages of html code? Geeks call fun writing scripts rather
than playing WoW although some are in both camps. I think dual
booting is fun, but its actually not that hard to do so the
fun wears off after you learn what to do.

---

### Post by sam1993 on 2008-12-08
I did start to learn how to code, mostly in HTML, was going to start to learn C# and C++ but haven't got round to it yet. Forgot HTML tags because I haven't coded in html for ages and plus I wouldn't of remembered that much anyway because I only spent a week learning the basics. I know how to dual boot, just wondering if there is any point dual booting Linux with my desktop (main computer) that runs Vista Premium. 

I think the fun to be had with Linux is hacking or am I wrong?

---

