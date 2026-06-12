---
title: "Linux Newbie needs help"
date: 2008-12-26
forum: General Help
---

### Post by fawzley on 2008-12-26
I am lost and frustrated with Linux. Am unable to find any reliable documentation, or other help. What documentation I can find  is either wrong, is not understandable or leads me to down a long convoluted path only to find it does not apply to my questions or the person I was communicating with not know what they are talking about.  
I am a retired computer systems engineer 27 years experience in mainframes, minis, speciality hardware & communications. I know windows, MCP, guardian, Ambilog 2000, 7171, DOS, CP/M Forte, PCAM, NDL etc.. have oodles of command line under my belt but zip for Linux (unix). 

Where can I find reliable documentation/support for Linux 8.10

I have three personal projects I am working on currently

1) Need to map some functioning windows shares to my Linux box. Looks like the package to use is samba ... How do I beg/borrow or steal a copy of the software and reliable documentation.

2) Looking to install a copy of Thunderbird. Was able to download a copy thunderbird-2.0.0.18, decompressed (tar'ed) it into \home\thunderbird..
How is the software executed (run)?

3) How can I locate documentation explaining Linux commands, terminology, software overview, boot sequence, architecture, file standards, file layouts, directory structure & Linux file permissions?

What support is available?

---

### Post by Ahadiel on 2008-12-26
1) Samba is free; sudo apt-get install samba
2) sudo apt-get install thunderbird
3) By using google. Maybe [this](http://linuxcommand.org) will be of help.

---

### Post by cdwillis on 2008-12-26
You can read the official Ubuntu documentation here:
[https://help.ubuntu.com/](https://help.ubuntu.com/)

and this site is good for general Linux information:
[http://wiki.linuxquestions.org/wiki/Main_Page](http://wiki.linuxquestions.org/wiki/Main_Page)

---

### Post by fawzley on 2008-12-26
> **Ahadiel said:**
> 1) Samba is free; sudo apt-get install samba
2) sudo apt-get install thunderbird
3) By using google. Maybe [this](http://linuxcommand.org) will be of help.

Thanks. Ran the sudo commands and both seemed to install. How do I execute the software? I am unable to find where the packages installed or any documentation. 
From the link to linuxcommand.org the commands are there need to figure them out any samba docs?

---

### Post by dannytatom on 2008-12-26
Thunderbird should be in Internet > Thunderbiard in the menu, no clue where Samba would be (don't use it).

Samba's official HowTo: [http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

### Post by glotz on 2008-12-26
As with all the other systems you're accustomed to [http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

---

### Post by theozzlives on 2008-12-26
I found "Ubuntu Linux Bible 8.10", "Linux Bible 2008", and "Ubuntu Hacks" very handy. "Ubuntu Hacks" is based on 6.06 but still helpful. All available on Amazon (or maybe the library). Also, Google has been my friend in solving problems.

---

### Post by Teabicky on 2008-12-26
I brought a book. It's called 

> Beginning Ubuntu Linux  

and it is amazing. My understanding of Ubuntu and Linux in general has increased no end.  It is highly informative as well ab being clear and concise.  I got it from Amazon.

---

### Post by gTinker on 2008-12-26
[QUOTE=fawzley]I am lost and frustrated with Linux. [/quote]

Yes, that is clear from your post. However, with your experience you should be well aware that trying to figure out new systems that are different from your previous experience while frustrated is counter productive.

[QUOTE=fawzley]
Am unable to find any reliable documentation, or other help. What documentation I can find  is either wrong, is not understandable or leads me to down a long convoluted path only to find it does not apply to my questions or the person I was communicating with not know what they are talking about.[/quote]

Yes, and the same thing happens in MS Windows forums too, there are lots of people around who don't and can't troubleshoot correctly and/or who misinterpret the data they see. Yet they often present it as "the solution". The forums are populated mostly with users who are just barely ahead of you in GNU/Linux skill and they want and try to help, but are not always successful. This should be somewhat less of an impediment to someone with your experience because you have developed the skills of evaluating what is suggested to you and understanding before you follow advice. If the helpers were paid for their work, we could probably have higher expectations.



[QUOTE=fawzley]  
I am a retired computer systems engineer 27 years experience in mainframes, minis, speciality hardware & communications. I know windows, MCP, guardian, Ambilog 2000, 7171, DOS, CP/M Forte, PCAM, NDL etc.. have oodles of command line under my belt but zip for Linux (unix).[/quote]

OK, but, as I mentioned, this should lead you to reasonable expectations. I'm retired too with over 30 years in the business, was a senior field engineer with Data General when the first PCs were born, I still had to learn when I started something new. 

I'm surprised that someone with your experience doesn't take the approach of assembling documentation first and familiarise themself with how the system is supposed to work, rather than just putting in a CD and starting like novice users do. Didn't you spend time and effort planning software upgrades on your previous servers and working out as many of the problems as could be envisioned before the upgrade, I'm referring to something similar to that approach?

[QUOTE=fawzley]
Where can I find reliable documentation/support for Linux 8.10[/quote]

One good place to start is with this post which is a "sticky" at the top of the beginner forums:
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
It has the title:  New to Ubuntu? Start here...

Keep in mind that 8.10 (the .10 stands for Oct.) is relatively new and volunteers may not have caught up with documentation. As you gain more experience you'll find that in most cases slightly older documentation can still be applied. A caveat, different distros don't always track the same way and wildly divergent versions of the same distro may have major differences. Most of the time those differences will not lead you to trash your system, just that the examples won't work.


[QUOTE=fawzley]
 Need to map some functioning windows shares to my Linux box. Looks like the package to use is samba ... How do I beg/borrow or steal a copy of the software and reliable documentation.[/quote]

Someone has already helped you install samba. If you were to open up a terminal and type ```
man samba
``` The manual page for samba would be displayed. In general, that is a good way to understand many GNU/Linux commands, read the manual page, with something like, man *commandname*. 


[QUOTE=fawzley]What support is available?[/QUOTE]

Apart from the paid support already mentioned, there is users helping users and your own initiative. Tons of forums and newsgroups and there is Google. Most distros have wikis and most forums have "howto" sections. Regarding things you asked specifically about, samba and thunderbird are both popular here in Ubuntu and there are lots of threads.

Take some time to learn how the distro you choose to learn handles package management, that's how you load software from the Ubuntu repositories, they are setup to install and give you menu choices, if you choose to install some other way (like you did thunderbird at first), then you probably have to add your own shortcuts to a menu somewhere.

It all seems shadowy at the beginning, because it is different from what you already know. However, with your background, it will start to fall into place and make logical sense if you keep reading and trying things patiently.

---

### Post by fawzley on 2008-12-26
Thanks,  the myriad of responses will keep me busy figuring out the innards  of Linux/Samba/wireless networking.

F.

---

### Post by fawzley on 2008-12-26
> **dannytatom said:**
> Thunderbird should be in Internet > Thunderbiard in the menu, no clue where Samba would be (don't use it).

Samba's official HowTo: [http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/)


Thanks. T-bird was right where you said it would be, still working on the samba beast.  Do you happen to know where the data (email) files are stored?

---

### Post by fawzley on 2008-12-26
> **glotz said:**
> As with all the other systems you're accustomed to [http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)
Thanks, paid guns are always an option...

---

### Post by BatsotO on 2008-12-27
Before you open your wallet try too search in the forum.
samba is a service, it is run once it is installed. the configuration file is in /etc/samba/smb.conf, you can use ftp or ssh if someone advise you not to use sambayou have to sudo to do editing, search this forum or google, you can find easy to confusing ways to set up samba share or you can install system-config-samba.

---

### Post by fawzley on 2008-12-27
[Also, Google has been my friend in solving problems.]

Yes I am having some problems with the l'ix terminology but I am getting better.

---

### Post by melojo on 2008-12-27
Dual booting works good for someone new.  Just keep with it, when you get aggravated stop take a break then get back to it.  Before long you will get the hang of it. I think most who love using linux are ones that like tinkering with things and figuring them out.  I like the added security of not having to worry about spyware or viruses because I don't believe any are in the wild.  

Good luck

---

### Post by bodhi.zazen on 2008-12-27
> **fawzley said:**
> I am lost and frustrated with Linux. Am unable to find any reliable documentation, or other help. What documentation I can find  is either wrong, is not understandable or leads me to down a long convoluted path only to find it does not apply to my questions or the person I was communicating with not know what they are talking about.  
I am a retired computer systems engineer 27 years experience in mainframes, minis, speciality hardware & communications. I know windows, MCP, guardian, Ambilog 2000, 7171, DOS, CP/M Forte, PCAM, NDL etc.. have oodles of command line under my belt but zip for Linux (unix). 

Where can I find reliable documentation/support for Linux 8.10

I have three personal projects I am working on currently

1) Need to map some functioning windows shares to my Linux box. Looks like the package to use is samba ... How do I beg/borrow or steal a copy of the software and reliable documentation.

2) Looking to install a copy of Thunderbird. Was able to download a copy thunderbird-2.0.0.18, decompressed (tar'ed) it into \home\thunderbird..
How is the software executed (run)?

3) How can I locate documentation explaining Linux commands, terminology, software overview, boot sequence, architecture, file standards, file layouts, directory structure & Linux file permissions?

What support is available?

LOL, love the avatar.

First , welcome to Ubuntu. Yes, a new OS is over whelming and Linux is one deep rabbit hole.

Here is a great resource :

[http://linuxcommand.org/](http://linuxcommand.org/)

From there, if you get stuck, or you see a command or terminology you do not understand, just ask. The Ubuntu community is large and diverse and although we can not answer all questions or fix all the issues one might face, we will do out best.

With your background, once you learn your way around bash I think you will be just fine.

As far as documentation, yes it can change rapidly, but it is rare that it is wrong. If you see an error on the fourms or wiki, please point it out.

I suggest you start here :

[https://help.ubuntu.com/8.10/index.html](https://help.ubuntu.com/8.10/index.html)

I always start with the "official" documentation that exists for a distro before I go to 3rd party sites. Not that 3rd party sites are bad mind you, I just find the official documentation a solid foundation.

---

### Post by gTinker on 2008-12-27
> **fawzley said:**
> Thanks. T-bird was right where you said it would be, still working on the samba beast.  Do you happen to know where the data (email) files are stored?

It is stored in the Thunderbird user's profile. As a general rule in *nix, user's files are stored in the user's home directory (folder). This is the place where a user has permissions sufficient to write files. You will see it referred to as home; /home/*username*/; and ~home. Since it is the mozilla organisation that creates Thunderbird, it might be found in .mozilla-thunderbird. Something you might not have learned yet is that files and directories that start with a "." are hidden files and there are a few of them in your home.


[edit] Fawzley, it occurred to me that it might be a good time to suggest you have a look at the Linux Filesystem Hierarchy.
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)

---

