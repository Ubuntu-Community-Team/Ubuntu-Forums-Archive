---
title: "Howto: Make Ubuntu popular in India"
date: 2006-05-05
forum: Desktop Environments
---

### Post by dhruv_1884 on 2006-05-05
Howto: Make Ubuntu popular in India



Hi Dudes,
I've been using Ubuntu for 2 weeks now and i have thoroughly enjoyed the experience.

During these 2 weeks, i have been able to make some observations and based on these observations i enumerate points below on how to make Ubuntu popular in India.

1.Provide a simplified document on partition management for the Ubuntu Install. It should include the procedure to delete a partition from Windows so that Ubuntu installs in the available Free Space
2.Ubuntu should have the ability to mount all the partitions on the disc during boot up. Necessary warnings to be provided for NTFS and other types restricted partitions
3.The Install should contain the following programs
1.Xmms
2.Mplayer
3.RP-PPPOE
4.Firestarter
5.JRE
6.A wine version of Mozilla with the Real Player Plugin. Sites like raaga.com are very popular in India, but the native Mozilla on Ubuntu does not support audio streams from these sites. Either make the native Mozilla compatible or provide the wine version.
7.Make the default sound device ALSA
4.Most home users in India do not have a net connection , so installing extra softwares would be difficult for them. Provide a version of Synaptic that could install softwares from CD's or packages that are transported onto the hard disk. It should be able to figure out what to do in the event an RPM or Bin file is to be used. Basically just make the install process completely GUI, no need for ./configure etc.
5.Create awareness about your product by having Ubuntu installed at Cyber Cafe's ( a joint where an Indian goes to browse the web, there are millions of these), and by training computer hardware store staff on howto install Ubuntu
6.Have a CD distribution center in India. Shipit takes too long. Or at least provide computer stores with the CD's so that they may be able to distribute copies

I am pretty sure that there is a 7, 8, 9, 10.... but nothing else is going through my mind right now.

In India the word of mouth is enough to make a product popular. Ubuntu is a great product but it needs to be tuned to Indian needs.
One in every six on earth is an Indian. If you can be successful here then the rest of the world should not be a problem.

Hope you consider my observations.

Regards
-
Dhruv Chopra.
dhruv_1884

---

### Post by Bloch on 2006-05-05
Hi Dhruv;
You are in India I suppose? How popular is linux in general there?

Your list would certainly go a long way towards making ubuntu popular. But a few of them conflict both with the law and with ubuntu's open-source policy.
Ubuntu wants to provide a completely free open-source operating system, one that individuals and organisations can adapt to their needs and redistribute.

Java, Realplayer, windows codecs, codec to play dvds, many fonts, plugins to play multimedia are all proprietary formats. They might be individually available free of charge from the rights holder, but cannot be supplied by ubuntu. And the rights holder can and often does charge a fee when large organisations use this software. See
[http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)
on how to install them.

I know it seems silly that you can install all these codecs and software yourself to get a fully functional system. Everybody does it, and yet ubuntu is still forbidden from includng them. There is even an automated script easyubuntu (and another called automatix) that will install all these in a matter of minutes, grabbing them from various sites around the world. It is a grey area to what extent commercial organisations can make use of these scripts.

Your other points seem reasonable to me particularly
> Most home users in India do not have a net connection , so installing extra softwares would be difficult for them. Provide a version of Synaptic that could install softwares from CD's or packages that are transported onto the hard disk.  
I think there is a whole thread on how to run ubuntu without direct internet access, and it involves burning several cds (or dvds) and using them with synaptic more or less as you suggest. But the general word is it's not fully foolproof.

xmms and mplayer only provide extra capability because of he extra codecs they have. When the codecs are installed (with easyubuntu) there is no strong need for these. I don't use either, however the mplayer plugins are used in firefox.

I agree the information n partitioning should be more easily available. It is there, but it should be on some "Welcome to Ubuntu" page when you log in for the first time.

---

### Post by dhruv_1884 on 2006-05-05
Hi,
Linux is quiet unpopular in India, there is a tale of it being hard to use, hard to install, and easy to ruin the comp.

seems like there are too many consisderations on software distribution, but at least the present ubuntu distribution system needs to improve. it takes weeks to get the cds.

why is there no product awareness program.
in india, ppl only need to be aware of a product, and the rest of the product tweaking can be done by them.

and for india synaptic has to have the "run from cd" capability

hope some suggestions are considered

regards
-
dc

---

### Post by Ramses de Norre on 2006-05-05
Synaptic can easily install from a cd, I have this line for my install cd-rom in /etc/apt/sources.list```
##deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

```
But I commented it out because when you've got internet it's easier to download then to search for the cd;)

You can add cd-rom's with apt-cdrom (check man apt-cdrom).

---

### Post by Bloch on 2006-05-05
> Linux is quiet unpopular in India, there is a tale of it being hard to use, hard to install, and easy to ruin the comp.

Yes, we know this tale. :-)  It has not been true since about 1998.

What about the cost of Microsoft Windows? Or is it true to say that most people are using a bootleg copy of MS windows? I think if they were paying $60 or more dollars more would use linux.

I too was surprised at the Members Map at the low number in India compared to Brazil and the Philippines - both of which are also middle-income countries. China has its own version of linux, Red Flag, so perhaps not as many use ubuntu.
I know that India has a good reputation for its IT industry. Perhaps it is only a matter of time?

---

### Post by dhruv_1884 on 2006-05-06
Every home user in India has a pirated version of Windows XP. 
most of thse pirated version users even update their windows regularly, i still cant understand how microsoft has not been able to detect these users.
Its a known fact that computer hardware stores provide the pirated version free of cost. The guys at microsoft must be deaf, dumb and blind no to know this, its so rampant.
I am of the opnion that in all this unchecked piracy microsoft has played a role, because if microsoft wanted it could have blocked all the pirated versions, but it didnt do so. if it ever did so, everybody in India would be forced to shift over to linux, and because indians have a short learning curve, it is possible that they might embrace linux and microsoft would have inadvertently hurt their own cause.

i suggest the ubuntu distribution team atleast makes an effort to provide all these harware stores in India with the install Cd,s and relevant documentation


regards
- 
dhruv

---

### Post by aysiu on 2006-05-06
Microsoft cares only a little bit about piracy.
It would rather have user lock-in than crack down fully on piracy.

Think about it--if you were Microsoft, wouldn't you rather have people using illegally obtained copies of Windows XP than legally obtained copies of Ubuntu Breezy?

---

### Post by RajivNair on 2006-05-08
hi guys,i guess im a lil late on this discussion but still . im frm India,ive been using Ubuntu for 3 months now and im really impressed by it and also by the fact that u get an OS completely free and that too shipped to ur doorstep. yes it is a reality that Linux is still a taboo among people here,i used to be among them too . Ubuntu changed all that and i even managed to convince couple of my friends to use it . as u would expect they turned out to be nerds and wouldnt use it coz u cant copy paste with right click on ur mouse. but i believe things are changing and OS like Ubuntu r doing a great job in promoting free and open software . i came to know about Ubuntu by a seminar conducted in my college by FSF(free software foundation) . Well what i want to say is if u want Ubuntu to be used widely here in India,spreading awareness about it is the best way. i myself am trying my best to get my friends into it . my dad had to take a loan to buy me a pc,and if i choose to go for all legal properiatry software ,my dad will have to take another one . now people r ready to die for anything they can get their hands on for free and i believe if people come to know about it theyll definitely give it a go . whether they use it or not will depend on whether theyre like my friends or not. also most of the computer users here are teens or say just got out of teen and are avid gamers . now that too is a serious factor as to whether theyll turn to linux . but, finally i believe the taboo needs to be removed which is their among people and that can only be done by spreading awareness about Linux n Ubuntu.

---

### Post by towsonu2003 on 2006-05-08
I'd reccomend you to file bug reports (and mark them as "wishlist" under "severity") in order for the developers to see your ideas: [https://launchpad.net/distros/ubuntu/+bug/](https://launchpad.net/distros/ubuntu/+bug/)

---

### Post by hellmet on 2006-05-09
Hmm...well you are absolutely rite Dhruv..
To make UBUNTU a hit in India, it still needs to get
more userfriendly...more like xandros or something..
but still remain free..

One more thing is that..the main problem of Linux is
its hardware incompatibility.
If once we have a PC manufacture who would
take up the task of sellin PCs with Pre-Installed Linux..
It wud work out to be great.
That Out-Of -The Box experience is lacking in Linux.
Again..anyday..u install something new and things screw
up for the novice PC user,
There is nothing more Novice friendly than the Windows.
Thats the only reason MS is still living in this world...

---

### Post by intel on 2006-05-10
You want reasons why Indians use WinXP(.....also)?

>MS-Excel (even a mac has MS Office X)
>MS-Exchange+AD+Outlook
>VB, IDE

Since most indians (10% population) work for the US outsourcing
They have to use Windows....think dell 

Plus, linux will seem sluggish 1/4 of the time, cause you need to recompile
the kernel.

People want to 
) check email, browse
) work on Excel macros
)  Share  files  on  windows  domain

the list goes on........

---

### Post by aysiu on 2006-05-10
[QUOTE=intel]
Plus, linux will seem sluggish 1/4 of the time, cause you need to recompile
the kernel.[/QUOTE] I don't know if I'm in the minority, but my Linux is not sluggish, and I've **never** recompiled a kernel.

---

### Post by christhemonkey on 2006-05-10
is really every 1 in 6 people Indian?

Didnt realise that figure was quite so high!

---

### Post by aysiu on 2006-05-10
[QUOTE=christhemonkey]is really every 1 in 6 people Indian?

Didnt realise that figure was quite so high![/QUOTE] [I think the ratio might be higher for Chinese.](http://www.cia.gov/cia/publications/factbook/rankorder/2119rank.html)

---

### Post by christhemonkey on 2006-05-10
Wow, interesting stuff there!

---

### Post by aysiu on 2006-05-10
According to that link, it looks as if India makes up 16% of the world population, with China making up around 20% of the world population.

---

### Post by mishranurag on 2006-05-30
Some pirated versions of Windows now don't update. I have first hand experience :)
Anurag

---

### Post by mishranurag on 2006-05-30
Dear Dhruv!

I discussed part of this problem with some users in UBUNTU-India mailing list.  I have agreed to make some CD and DVD repositories of useful and critical program and ship it to few interested people. The copies of these CDs and DVDs will take out the biggest headache of some people, if they want to have extra programs with poor or no internt connection. They can further make copies and use it upon their wish. I will start doing that in couple of weeks. I have put up following blog where I will make the list based on comments from users.

[http://ubuntu-india-mishranurag,blogspot.com](http://ubuntu-india-mishranurag,blogspot.com)

Anurag

---

### Post by dhruv_1884 on 2006-05-31
Thanks Dude,

Put up your blog soon, i'll put up the list.

thanks

regards
]
dhruv

---

### Post by Sukarn on 2006-05-31
I seem to be somewhat late in the discussion, but I'm from India too, and its true that most of the vendors in India are handing out pirated copies (most of which dont update cause of the illegal CD-Keys). I had a CD-Key that worked for updates, but I had to reinstall (is that a new thing?) and then suddenly the same CD-Key stopped working. It had gotten listed as an illegal one.

About the anti-linux thing in India - its true that Indians believe what they hear, and MS has done all in their power to make it look like linux is the most difficult to use/manage OS ever. I disbelieved that and kept trying out different live CDs. I found Ubuntu quite by accident actually and the only reason I tried it was the free CD from shipit. I love it now and haven't used Windows for more than printing something (having problems setting up my printer in Dapper).

I was using Ubuntu when a friend came by and wanted to surf the net for something. He saw the interface was different than windows and I told him it was linux. He instantly got to "Linux is crap" "Linux is unusable" "Linux is the worst OS" and all those things that had been fed to us Indians. No amount of explaination would make him see sense. I just asked him why he kept saying that without even trying out Linux and the answer I got was "I've heard it". That was the crappiest answer I had ever heard.

**@dhruv:** As far as I know, rppoe is already available in Ubuntu. I am using an ethernet router set up with pppoeconf command which I believe is a command belonging to rppoe.

---

### Post by abhitux on 2006-06-01
I disocvered this thread by chance. 

We are trying our level best by spreading the good word about Dapper on the forums ([www.vinuthomas.com)](www.vinuthomas.com)). Plus we have a dedicated IRC channel for the same.

As for the Ship It, I feel that there may be some real logistics hassles.

Most of the computer maagzines are crap with MS only write ups. Linux is making it's presence felt but very slowly. Even the pressed DVD's that come with Linux need a windows computer to copy the ISO's. This makes it useless for any one else on another platform. So, it is a case of misplaced priorties. 

It would be very difficult to convince the hardware vendors to carry Linux on their assembled computers. They earn majorly out of the "support structure" because Windows crashes ever so often! Hence, I see no reason for them to adopt open source.

As for someone who pointed out here, MS would want to keep customers locked in; the updates may or may not work. It's give or take. Though, I have been out of MS crap for over a year now.

Hence any initiative has to come from Ubuntu HQ itself. Mark Shuttleworth was here in India recently and some major newspapers carried out his interview. I'd be interested to contribute my time to some sort of a mailing list; we can decide together to mail the major newspapers/ news channels to carry out the review of Linux/ Open Source in general. This is one way out in my opinion.

Majority of the games are made for Windows; some may be ported using Cedega (which again is a paid solution AFAIK and involves tweaking enough to scare even people like me); which makes it impractical to adopt on a mass scale. However, for everything else there is Ubuntu (or any o0ther version of Linux). 

In my opinion, the Government has to move towards Open Source applications and aviod paying tax payers money to the corporations. Ubuntu could tie up with hardware vendors to "work out of the box"; this is far fetched. No one would be willing to spend money on advertising for a product they aren't sure that it would sell. AMD faced a major hassle before it could remove the entrenched Intel solely on its performance.

I am trying to do my bit by distributing the free CD's that came in and following it up on a regular basis. I have been able to convert two people to Ubuntu (from Windows and one from Red Hat). Still trying. 

Cheers!

---

### Post by mishranurag on 2006-06-01
Its up at 
[http://ubuntu-india-mishranurag.blogspot.com](http://ubuntu-india-mishranurag.blogspot.com)
Anurag

---

### Post by mishranurag on 2006-06-01
There is a UBUNTU India mailing list, and I would recommend you to join that. It address is 
[B]Ubuntu India Local Community <ubuntu-in@lists.ubuntu.com>

[/B]I am also planning to make copies of repostory CD and DVD and ship to India for free for some people who cannot get good internet connection and can copy the CDs and DVDs and dsitribute it. I have put up my blog where I will prepare the list of required programs and make repository DVDs and CDs according to that.

[http://ubuntu-india-mishranurag.blogspot.com](http://ubuntu-india-mishranurag.blogspot.com)

Anurag

---

### Post by vinodis on 2006-06-02
I am in India. I have been using Breezy for a while and now on Dapper. I have converted Myself and a few of my freinds COMPLETELY to (K)ubuntu at home.
At Work we are 'forced' to Windows.

---

### Post by vinodis on 2006-06-02
Hi VinuThomas, it would be great if you could Co-Host the [Dapper Automatix CD]("http://www.ubuntuforums.org/showthread.php?t=177646&highlight=Automatix") _once it is upgraded to work with Dapper_ - in your website. Without the Automatix CD it would be difficult to get a 'Working' Ubuntu installation. 
Please think about this proposal.

---

### Post by abhitux on 2006-06-02
Hmm, I'm just a moderator there! I shall try and convince the webmaster to host some space. It's a long shot but nevertheless this is a good sugeestion.

---

### Post by ambrish on 2006-06-07
I came across this link 
[http://www.ubuntu-in.org/]("http://www.ubuntu-in.org/")

---

### Post by hellmet on 2006-07-08
well I actually started a "Get Ubuntu" community on Orkut..
Just have a look at it..and see if u cud help!!

[Get ubuntu]("http://www.orkut.com/Community.aspx?cmm=14253544")

---

### Post by cleverselfreferentialname on 2006-07-08
My appologies for bumping an older thread, but this brings up an important subject; hardware support. I'd like to see a tool for Windows that checks the hardware to create a profile and see how linux-compatible it is. That way we could be certain of compatibility without even having a liveCD.

---

### Post by hellmet on 2007-02-20
Again, sorry for bumping.. we @ ubuntu india non-official, are trying it in our own possible way to spread Ubuntu. 
[www.ubuntu.co.in](www.ubuntu.co.in)

---

### Post by ashmew2 on 2007-03-29
Found it !!
Since there are many people without internet in India (like many of my friends) , we could make a custom installation disc which will ask them if they want to install the codecs or not....etc
And we could upload the iso image somewhere for folks that cannot have easy access to the codecs and stuff maybe because of slow internet or any oth er problems

---

### Post by aysiu on 2007-03-29
Something like this?
[https://ubuntuplus.bountysource.com/](https://ubuntuplus.bountysource.com/)

---

### Post by saratchandra on 2008-06-27
One of the major problems for linux in India is how the media portrays Microsoft and uncle Bill as some sort of saints. Bill Gates is a role model for the average computer guy. Then, most of the support guys don't know a thing about linux. I've been asked again and again to remove linux if I was to get any support for my hardware. Most computers in India come with an illegal version of Windoze and the users don't really care about installing another operating system or even a new browser software.

---

