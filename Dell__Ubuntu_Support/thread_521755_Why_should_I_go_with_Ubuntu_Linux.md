---
title: "Why should I go with Ubuntu Linux?"
date: 2007-08-09
forum: Dell  Ubuntu Support
---

### Post by arvadawest on 2007-08-09
Hi,
I am considering purchasing a new Dell pc (xps 410) with Ubuntu.  I know this may be a dumb question, but why should I go with Ubuntu v. Windows?  I hear and read about how superior Linux is, but I would like to know from some of you before I purchased.  Your answers will certainly reflect my decision.  Thank you for your time.

-aw

---

### Post by jrusso2 on 2007-08-09
If  you have not tried Ubuntu yet I would download an iso image and run it as a live cd first.  So then  you can decide it you like it or not

---

### Post by jacob01 on 2007-08-09
> **arvadawest said:**
> Hi,
I am considering purchasing a new Dell pc (xps 410) with Ubuntu.  I know this may be a dumb question, but why should I go with Ubuntu v. Windows?  I hear and read about how superior Linux is, but I would like to know from some of you before I purchased.  Your answers will certainly reflect my decision.  Thank you for your time.

-aw

my opinion for you is if you dont know for your self why you want linux then linux isnt for you

another thing is if you want to use linux then it is a commitment because you can't do much with out doing any thing vary technical

also another thought is what is the reason for a linux powered gaming computer when there are not many game that can be played although that is starting to change because of wine and also because of better driver support

another thing to think about is that if you plan an using software that is for windows on linux then you are in for a struggle to get it to work

you can do almost any thing you can do in window but just in a differant way

---

### Post by arvadawest on 2007-08-09
Hi, thank you for your reply.  Actually, I am familiar with the unix world, so my question should have been more detailed.  I just noticed that Dell is now including ubuntu with the xps 410 system.  The price looks really good, but I am just wondering how well Linux runs.  Is it true that you can run Ubuntu without a reboot for days, weeks, even months.  I found out that if I use Ubuntu desktop ed. I can run LAMP, but it's primary purpose for my network will be as a file server, DNS, and running apache.  Thanks for your reponses.  -aw

---

### Post by cacycleworks on 2007-08-09
imho, linux offers the kind of stability and integrated security that MS Windows family of products dream about. We can put linux on a computer and disconnect the power button. Set the bios to power on ac loss. Leave it on forever, turning off only for maintenance or replacement. It will work the same way from that time on with the software and configuration installed.

I believe it is impossible to achieve the same with windows - for a few reasons. First: it is impossible to have professional software and have a "steady state". Yes, you could refuse all Windows Updates, however, there is a time with each one that compatibility with other programs *suffers*. 

Then said other proprietary programs will have forced updates, some which may break tasks used on others. 

Worse, I see with Windows that when a program installs, it is normal for it to sprinkle DLLs all over the system and have important files in several directories, including the ones behind the users "identity key". 

With linux, all information from a user goes in their folder. I recently moved from a Sony laptop to a Dell. I copied my /user/home/chris directory and all subfolders over to the new computer. Upon boot up, all my settings were there; it was as though I hadn't done anything different! This is possible on a Windows box only with the most careful IT department where they have ready to install flash images of computers. And even then, there are many settings which cannot be transferred.

btw, we are transitioning away from WinXP. We tried out Vista. To be blunt, it is scary.

---

### Post by jacob01 on 2007-08-09
> **arvadawest said:**
> Hi, thank you for your reply.  Actually, I am familiar with the unix world, so my question should have been more detailed.  I just noticed that Dell is now including ubuntu with the xps 410 system.  The price looks really good, but I am just wondering how well Linux runs.  Is it true that you can run Ubuntu without a reboot for days, weeks, even months.  I found out that if I use Ubuntu desktop ed. I can run LAMP, but it's primary purpose for my network will be as a file server, DNS, and running apache.  Thanks for your reponses.  -aw

yea you can run it for days like just about any os and windows can also run for day so yea

how do you think all the web servers run? most of them run on linux and they have to be reliable and run without a reboot for a long time

---

### Post by az on 2007-08-09
> **jacob01 said:**
> 

another thing is if you want to use linux then it is a commitment because you can't do much with out doing any thing vary technical


I disagree.  My father-in-law can handle Ubuntu a lot easier than windows.  He gets stuck even installing a printer in XP.  He doesn't seem to have a problem with Ubuntu.

I think you have to be very technical to be a power user regardless of what operating system you use.  For most people, they either have a power user friend who can help them out or they just don't do anything out of the ordinary.  I would say Ubuntu is the same as windows in that respect.

I would even tend to think that Ubuntu is easier to manage.  For example, my father-in-law still can't figure out how to safely pull out a USB drive in XP.

---

### Post by cacycleworks on 2007-08-09
Yes, to agree with az, my secretary got a virus on her notebook and was frustrated. When I volunteered to help her run kubuntu, she went for it. She is so happy with her laptop now -- and was so happy to learn how (be forced to) use command line for an install or two. 

Definitely not a power user by any stretch, but she's smart and just wants her computer to "work". :D

---

### Post by foxholeunder on 2007-08-09
> **arvadawest said:**
> Hi, thank you for your reply.  Actually, I am familiar with the unix world, so my question should have been more detailed.  I just noticed that Dell is now including ubuntu with the xps 410 system.  The price looks really good, but I am just wondering how well Linux runs.  Is it true that you can run Ubuntu without a reboot for days, weeks, even months.  I found out that if I use Ubuntu desktop ed. I can run LAMP, but it's primary purpose for my network will be as a file server, DNS, and running apache.  Thanks for your reponses.  -aw

If your going to be using this primarily as a server which it sounds like you are, I would without hesitation choose any distribution of Linux over Windows XP. 

First off, the code base underneath Windows XP is not tuned for secure serving. 

Second, about the only reason to run these type application with XP is if you are a developer and need local testing or are going to only access them from inside a local area network. I would not advice presenting these services to the wild-lands of the internet using XP. Especially if you also intend to use this system as a desktop.

Ubuntu is a great choice for Linux distro's as root is disabled by default adding that extra layer of protection from wrong-doers.

The only way I would consider running Windows as a server is if the Windows version were Windows Server Edition. which will cost a considerable amount more than XP.

I used to work with Windows Server 2003 and since I found Ubuntu I will never go back to a Windows based server. The flexibility offered by a *nix environment is just too good to give up. Control over security etc... 

I can actually relax and not worry about having to restart the server after 99.9% of  updates unless I updated the kernel. Not to mention just having to restart the system periodically because the registry breaks down and programs start to complain about missing dll files due to misplaced links in the registry. This occurs after awhile due to every time a file is accessed it is moved on the drive and eventually the registry loses track and just breaks.

Hope this helps and best of luck to you!

EDIT:

I should have mentioned that I have four Ubuntu systems that have been running for over a year now only rebooting a few times when I updated the kernel and they are running as smooth as day one!

---

### Post by arvadawest on 2007-08-09
Hi Fox,
Thanks so much for your response.  I am so tired of all the darn reboots and I need an OS that will run continuously for weeks or longer.  I intend on using Ubuntu (desktop ed.) as a file server, DNS, apache with my windows network.  I appreciate your insights into the registry on windows, I thought is was only the memory that had issues.  Thank you very much!

-aw

---

### Post by foxholeunder on 2007-08-09
arvadawest,

Glad I could offer some help.

I am just truly happy since switching to Ubuntu. I have found it to be actually easier to figure out how to do stuff and trouble shoot why things don't quiet work the way they should. Especially during initial setup. 

I still run Windows (both XP/Vista), but they are now sandboxed inside of a virtual machine environments.

Stability is for sure a top requirement and *nix offers that even if running as a desktop on top.

---

### Post by oldos2er on 2007-08-09
If you're not afraid of the command line, and there are no particular Win* apps you need to run, I'd say go ahead and try Linux. I think the easiest thing to do before you actually order a new PC is to download the LiveCd and see how Ubuntu "fits."
 There are just a couple caveats: wireless internet can be problematic in some cases to set up, and so can video. Of course if you're buying an Ubuntu pre-installed system, those things shouldn't matter.
 You won't need to worry about anti-virus programs, or firewalls, or spyware hunters.
 Last month I bought a Dell desktop with Ubuntu pre-installed, and I'm extremely happy with it.
 Good luck.

---

### Post by Frak on 2007-08-09
Since you said you have experience in the *nix environment, I see no reason why Ubuntu wouldn't work for you.
Just try out the LiveCD first, it can make or break you. Remember that an informed desicion is a good desicion.
Oh, and try Kubuntu also. You may like Kubuntu, who knows. ;)

Lastly, if you do decide to buy a Dell computer, you are making a good decision because all hardware is guaranteed to work.

Frak

---

### Post by arvadawest on 2007-08-09
wow!  thank you for all the responses.  All I was hopeful for is the fact that I could run DNS, Apache, and use Ubuntu desktop ed. as a file server (or quasi server) and for it to be reliable, running continuously for days/weeks even months with little or no reboot.  I think that the Dell 410 (though more expensive and comes with 2gb of ram) is the way to go.  I am not concerned with playing games on Ubuntu, but I am looking for scalability, reliability, cost savings, and a strong platform that the other windows systems can access files and use the DNS internally.

I thank you all.  If any one has any more information, I am very happy and appreciative of reading.  I am so into Routers, Switches, and Firewalls, that I do not pay much attention to pc's as long as they run and are reliable, but I am sick and tired of Windows.

Dissemination of information is the key to knowing and understanding as well as applying.  Thank you!

-Arvada West (Dr.)

---

### Post by Frak on 2007-08-09
Well, if you wanted a server, Linux is the best choice next to BSD. Its even a natural choice, as its not really smart to use IIS on Server 2003, for security reasons.

Happy Purchasing. :)

---

### Post by mike999999 on 2007-08-09
> **arvadawest said:**
>  I am not concerned with playing games on Ubuntu, but I am looking for scalability, reliability, cost savings, and a strong platform that the other windows systems can access files and use the DNS internally.


Hey Arvada,

From what you're describing you may want to look closely at the 530n w/ upgrades.

Hardware wise, you can prop that sucker up with some nice upgrades and still come 
in with a better deal. Plus, if you were to scale it up it's cheaper.

Mike

---

### Post by arvadawest on 2007-08-09
Hi Mike,
Thank you for the advice.  I will look into it.  I may have to go with 4gb of ram as I will be using ArcGIS and ArcIMS and they require a lot of memory, but thank you.  I will check into the 530.  

Dr. AW

---

### Post by odin1965 on 2007-08-10
> **arvadawest said:**
> Hi Fox,
Thanks so much for your response.  I am so tired of all the darn reboots and I need an OS that will run continuously for weeks or longer.  I intend on using Ubuntu (desktop ed.) as a file server, DNS, apache with my windows network.  I appreciate your insights into the registry on windows, I thought is was only the memory that had issues.  Thank you very much!

-aw

I replaced our aging windows 98 file server at work with Ubuntu 6.06 and I am very happy with it. It only servers 13 other computer, all windows, but it is by far the most reliable machine in the office. Just a run of the mill emachines same as the rest, but I onlt reboot for kernal upgrades (and power outages) :)

---

### Post by arvadawest on 2007-08-10
Hi Odin,
Thanks.  That is very helpful to know.  If an older version of Ubuntu desktop works well, then I assume the ver. 7 is great.  Thank you!

-aw

---

### Post by Frak on 2007-08-10
Actually, I would recommned 6.06 over ver. 7.
Its WAY more stable. And was actually created for servers, in fact, its supported for another 2 years.
(6.06.2 is coming out soon also)

---

### Post by radagast1155 on 2007-08-10
Oh yeah definantly want Ubuntu then!
I havent powered down in three weeks and nothing has happened!
I do recommend the 32-bit version though the 64-bit version just kept giving me problems. lol

---

### Post by zero244 on 2007-08-10
If setup right even a Ubuntu desktop version would be as stable as a Windows desktop.
Ubuntu has real security built in.
Ubuntu is virtually free.
I think most people who use Ubuntu as a server for 24\7 use will opt for the server version which doesn't use a graphical interface.
Ubuntu with a basic Gnome interface setup with stable drivers and running lean should give you some good uptimes.
I haven't really tested Ubuntu for uptimes since I shut down my computer everyday.
Plus I run Beryl which probably isn't a good idea for maximum uptimes.
One of these days I might do a uptime test and see how long it will run without a reboot.
The one thing  I dont like about ext3 is you cant spin your harddrive down since the harddrive is accessed every five seconds, even when your not doing anything.
Or least I haven't been able to spin my drive down using Edgy without going into full hibernation.

---

### Post by arvadawest on 2007-08-10
HI Frak,
I just order the XPS 410 because of the great feedback from all of you.  As you read, I plan on using this as my primary file server, DNS, Apache, etc and move away from the 2000 Server (except for logins), but will continue to migrate to the *nix world in time.

Does ver. 6 come with the GUI already installed?  How is v.6 more stable than v.7?  Thank you.

Dr. AW

---

### Post by arvadawest on 2007-08-10
Thanks Zero,
To repeat, I am hopeful to run this system 24/7.  Unfortunately, Dell only ships with the desktop ed., but I have been told that the desktop ed. can do almost everything the server ed. can (file server, dns, apache, security, etc).  -aw

---

### Post by cacycleworks on 2007-08-10
> **arvadawest said:**
> Does ver. 6 come with the GUI already installed?

Is easy to install a command line (cli) server... when you get the ISO image, get the one that says server.

Some translation of the ISO images (I like Kubuntu for the KDE desktop and am not a huge fan of gnome):

AMD64 is for dual core computers. You will end up with a "generic" kernel that works equally well on Intel EMT or AMD64 machines.

x86 is for standard "pc"s that are not 64 bit or for those who find difficulty installing the 64 bit version of the OS. 

alternate CDs are simply installation CDs with text based guided install. 

The other CDs without extra labels are "Live CDs" and you can boot to the OS from the CD and choose to or not to install to your computer.

:)

Images here: [http://mirrors.cs.wmich.edu/ubuntu-releases/kubuntu/feisty/](http://mirrors.cs.wmich.edu/ubuntu-releases/kubuntu/feisty/)
kubuntu-7.04-desktop-i386.iso          
kubuntu-7.04-desktop-amd64.iso   699M  Desktop CD for 64-bit PC (AMD64) computers (standard download)

kubuntu-7.04-alternate-i386.iso     695M  Alternate install CD for PC (Intel x86) computers (standard download)
kubuntu-7.04-alternate-amd64.iso   697M  Alternate install CD for 64-bit PC (AMD64) computers (standard download)


On this page:  [http://mirrors.cs.wmich.edu/ubuntu-releases/feisty/](http://mirrors.cs.wmich.edu/ubuntu-releases/feisty/)
**The server install CD** allows you to install Ubuntu permanently on a computer for use as a server. It will not install a graphical user interface.

There are three images available, each for a different type of computer:

PC (Intel x86) server install CD
    For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows, as well as newer Apple Macintosh systems based on Intel processors. Choose this if you are at all unsure.

64-bit PC (AMD64) server install CD 
    Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead.

---

### Post by cacycleworks on 2007-08-10
> **arvadawest said:**
> Thanks Zero,
To repeat, I am hopeful to run this system 24/7.  Unfortunately, Dell only ships with the desktop ed., but I have been told that the desktop ed. can do almost everything the server ed. can (file server, dns, apache, security, etc).  -aw

Yes, and you can "convert" it to command line by removing the ubuntu desktop package. A little research via google or these forums can explain that fully.

---

### Post by arvadawest on 2007-08-10
Thanks Ann.  Have you run your systems continuously with Ubuntu?  How is the uptime on them?  I have read what others stated that they have not had to reboot much.  As you already read, I am going to use Ubuntu desktop ed as a quasi-server (file, dns, web, etc).  Thanks.  :)

---

### Post by nick.inspiron6400 on 2007-08-10
I was thinking when I switched that Linux was for Unix gurus, and people that have never used anything but Unix.

With Ubuntu Linux, I was wrong...

Ubuntu is the linux for the human being, I use the terminal for certain things. But I can do everything without it. 

Maybe there should be a version of Ubuntu without the terminal, if they could do it???? 

I would buy the Dell with Linux, you have will have so much more opportunities with Linux than Windows.

Get the Dell with Ubuntu.

---

### Post by Steveway on 2007-08-10
You can run a Linux-system months, even years without a reboot.
You only need to reboot if you do a kernel-upgrade, but you don't have to update.
What me concerns are your comments about Apache. You seem to think that it is mainly a Windows thing, IT'S NOT, Apache comes from the Linux-world and runs best on a Linux or BSD-System.
Yes it runs on Windows, but you're better with a Linux-server.
Most of the Servers in the world run with Linux.

---

### Post by leftcase on 2007-08-10
> **arvadawest said:**
> Thanks Ann.  Have you run your systems continuously with Ubuntu?  How is the uptime on them?  I have read what others stated that they have not had to reboot much.  As you already read, I am going to use Ubuntu desktop ed as a quasi-server (file, dns, web, etc).  Thanks.  :)

Hi there,

Just picked up on this thread, so thought I'd reply.

I'm running Ubuntu 6.06 as the operating system for a proxy server which is serving a network of around 400 computers. The server has been up and running for about 10 months continuously without bothering me, but went down last week because of a power outage (nothing to do with Ubuntu though).

I'm also running Windows Server 2003 boxes too, (Active Directory, File Server etc), but find that they need more attention to keep running smoothly. Unfortunately, Windows updates often cause them to restart although this can be scheduled to happen at quiet periods.

When comparing Ubuntu servers to Windows server I'd choose Ubuntu every time. The only reasons I use Windows are.

1) Because the powers that be make me use it!
2) Active Directory
3) Some of the server applications we use, only run on Windows.

Checking out the eBox platfrom - It even looks like setting up Linux servers is going to get easy. [http://www.ebox-platform.com/](http://www.ebox-platform.com/)

Cheers

Chris

---

### Post by arvadawest on 2007-08-10
Thanks Steve,
My question to you is:  would this run just as well on Ubuntu desktop ed. (i know it would run on Ubuntu server ed, but the system I purchased will come with desktop ed. preloaded.  Thanks.

-aw

---

### Post by foxholeunder on 2007-08-10
> **arvadawest said:**
> HI Frak,
I just order the XPS 410 because of the great feedback from all of you.  As you read, I plan on using this as my primary file server, DNS, Apache, etc and move away from the 2000 Server (except for logins), but will continue to migrate to the *nix world in time.

Does ver. 6 come with the GUI already installed?  How is v.6 more stable than v.7?  Thank you.

Dr. AW


Ubuntu 6.06 LTS is considered a major release. 6.06 will be supported by the Ubuntu developers as follows:
3years or until 2009 for the desktop edition
5years or until 2011 for the server edition.

Ubuntu 7.04 (Current stable release) is not a major release and be supported by the Ubuntu developers as follows:
1year or until 2008 for both server and desktop.

Now as with most distributions of *nix community support will last indefinitely depending upon how popular that version is amongst the community of users. 

However, official support by Ubuntu will only be as listed above. By support I mean ensuring that all package repositories for that release are updated with all the latest security patches. 

So, for at least until 2009/2011 for desktop/server 6.06 respectively, any software you have installed on your system  will be kept up to date with any required security patches.

The really nice thing about *nix, is that upgrades to newer editions down the road seldom mess up your current configuration. 

Example: If you manually configure your xorg.conf file to fine tune it for you monitor setup, Update will never replace this configuration, you will always be able to keep your configurations exactly as you define them. Making updates/upgrades super smooth. Now of course updating to a test build like th e current Gutsy Gibbon release (I am posting with this box right now) you may end up with some quirks... But stay with the stable versions and you should not encounter problems.

One of the #1 reasons I have fallen in love with *nix is that all packages in the supported by the release are thoroughly tested before that build is classified as a 'stable' release. The *nix community and developers are extremely good about ensuring things work. The only real problems they run into is proprietary drivers - Graphic cards for one example...

When you choose a flavor, distro, etc... of *nix you not only get support for the OS itself, you get support for all of the packages that are included with it. This I imagine many thousands of Windows users are frustrated about if they chose to upgrade to the new Vista... Almost nothing that worked on XP works on Vista... But as far as Microsoft is concerned it is not their problem, software vendors either need to change their code or not make versions for Vista... -- 

No support across-distributions in Windows. It's not just the OS, ask any Web developer about having to write standards compliant code then write exceptions for Internet Explorer 5, 6, and now 7 ... IE-5,6,7 are not even compatible with each other. Or Microsoft Works suites or Word suites, same thing, each version incompatible with the older version; requiring special plugins to be installed in order to view work you created on a different version. 

I could go on... Anyways, the whole thing is rather sad. I know so many people that are mad at themselves for switching to Vista. So mad that they have actually taken to considering trying Mac or Linux. 

Like I said earlier in a prior post, I still run Windows XP/Vista, I just run them sandboxed inside a virtual machine...

Getting carried away.. sorry!

Main point:

6.06 will be supported longer by Ubuntu developers than 7.04, however Upgrading to newer stable distributions should give you no troubles.

Worse case scenario is if you have a manualy configured file (again I will use xorg.conf as an example) - If during update that file needs to be updated for security reasons, it will not install the update, but rather inform you that the file needs to be replaced and will give you options to either keep your existing configuration, completely overwrite your configuration, or back up your configuration and then install the new one. In witch case you can then copy the required info from you exiting file to the new file. 

Major changes do not take effect until you reboot your system so you will have plenty of time to ensure everything is the way it is supposed to be. 

Example: 
If you are notified of well... any updates at all, you can install them whenever you desire. Or say a major update to the kernel that will require reboot. You can install these anytime you desire and if you are not able to reboot your system till after hours three weeks from receiving the update, then you do not have to reboot until that time rolls around. 

There is no you have to reboot now and were going to reboot you whether or not you want to now or not... it is reboot at your leisure... This helps ensure you that the system is not down during a high demand time.

Since you mentioned that you are running a Web server on this box as well, I might mention that if this Web server is going to be under heavy traffic 24/7 you may consider setting up some redundancy. 

The process is fairly simple, I just completed setting this up for my own systems. 

I found this great tutorial here:
[http://www.howtoforge.com/high_availability_loadbalanced_apache_cluster]("http://www.howtoforge.com/high_availability_loadbalanced_apache_cluster")

The tutorial will walk you through setting up two servers (they use apache as example but really it could be any kind of server - file, database, etc..), and two load balancers. At the bare minimum you would only need one load balancer, but obviously if the load balancer fails it would be the same as only having one server that fails... nobody would be able to access anything - So the tutorial sets up two load balancers.

Once set up if one server drops or (needs maintenance), the other server will automatically take over. Also, if one load balancer drops, the other one will still (hopefully) be alive and able to direct traffic to the server.

Very slick and super easy to install! I was very amazed at how easy it actually was.

I am going to stop here...

Again... Good luck and have fun!

EDIT: 
the only Ubuntu releases without a GUI are server editions. Although literally, in as little as 5 commands you can have a GUI installed. Oh... and basically all distros of *nix are servers underneath... it is only missing the GUI packages.

---

### Post by arvadawest on 2007-08-10
Thank you Jeremy.  Great reply.  Yes, you answered what I was hoping to hear, that the Ubuntu desktop ed can be used as a quasi-server (just wanted the gui).  

I just purchased the Dell 410N with 2gb ram, 250hd, and the big monitor.  I assume that I can just download a more stable Ubuntu OS and reload it in place of v.7 desktop I guess.  Thanks.

Dr. -aw

---

### Post by Steveway on 2007-08-10
Yes sure it will run equally.
You can easily remove the Desktop-part and install the Server-part or keep both.
You just need to mark ubuntu-server to be installed in Synaptic to install the server-part and to remove the Desktop part, just mark ubuntu-desktop to be removed in Synaptic.
Or you can do this from a terminal with apt-get:
sudo apt-get install ubuntu-server
sudo apt-get remove ubuntu-desktop
Pretty easy.

---

### Post by Frak on 2007-08-10
sudo apt-get remove ubuntu-desktop may not work.
ubuntu-desktop is just a meta-package, meaning it has literally no value, exept as a container.
to get rid of the gui, you may want to run
sudo aptitude remove libglib2
that should work

---

### Post by foxholeunder on 2007-08-10
> **arvadawest said:**
> Thank you Jeremy.  Great reply.  Yes, you answered what I was hoping to hear, that the Ubuntu desktop ed can be used as a quasi-server (just wanted the gui).  

I just purchased the Dell 410N with 2gb ram, 250hd, and the big monitor.  I assume that I can just download a more stable Ubuntu OS and reload it in place of v.7 desktop I guess.  Thanks.

Dr. -aw

Yeah, if your looking for longer support between upgrades I would reinstall it with 6.06

The main difference between 6.06 and 7.04 is in the GUI and some of the programs preinstalled. For example, if you have a file that you currently can not open as you do not have the correct program to view/access the file, 7.04 comes with a great utility that will pop up and tell you that you will need such and such program to view/access this file would you like to install it... If you do then you choose to install the program. Many times their will be several program choices each with a good description of its features.

A very useful tool. I am positive that this feature could be added to 6.06 however I do not actually know the name for the application  but I am sure with a little research the name could be found. Once known it could be fairly easily added either through the GUI program installer or via terminal. 

I am curious now as to its name...

Anyways.. mp3 for example is a proprietary codec and as a result no support is offered directly with Ubuntu do to the license restriction by the owners of the patents for mp3 codecs. This new application feature makes it easy to install the required packages in order to play these otherwise proprietary codecs/files/etc..

---

### Post by arvadawest on 2007-08-10
Hi Frak,
Why would I want to remove the GUI?  Is there any benefit?  Thanks.  -aw

---

### Post by arvadawest on 2007-08-10
Oops, I also meant to add that yes 704 is only supported until 2008, but wouldn't they come out with an update that would be supported longer.  Why would I want to remove 704 with my new system (which I won't get until late next week), wouldn't Ubuntu come over with a newer version and I can just upgrade to that?  Thanks.  -aw

---

### Post by foxholeunder on 2007-08-10
> **arvadawest said:**
> Oops, I also meant to add that yes 704 is only supported until 2008, but wouldn't they come out with an update that would be supported longer.  Why would I want to remove 704 with my new system (which I won't get until late next week), wouldn't Ubuntu come over with a newer version and I can just upgrade to that?  Thanks.  -aw

Ubuntu releases new stable versions every six months!

Gutsy Gibbon will out in only a few short months then six months after that there will be another release. Im not sure I would have to read again but but I believe (feel free to correct me if I am wrong) that every third stable release will be a long term supported release. I am pretty sure that it is every third release with long term support. it may be every fourth release though. But definetally every six months their will be a new stable release!

---

### Post by foxholeunder on 2007-08-10
UPDATE on releases...

The next LTS or Long Term Support release of Ubuntu will be in 2008 for version 8.04. 

Basically, about the time Fiesty 7.04 is no longer supported you can upgrade to 8.04 LTS and gain the longterm support.

Personally I would not see any need to downgrade to 6.06 if 7.04 is already installed and you are also going to use the GUI on this box...  I would just wait till 8.04 comes out.

I have three servers running 7.04 and two with 6.06 but they are only running 6.06 as they are both Sun machines and I could not find a sparc processor version for 7.04; only 6.06.

---

### Post by Steveway on 2007-08-10
You don't really need a GUI on a Server, it's just waste of space and ressources.
Thanks, frak, I wasn't quite aware that it doesn't remove it, thanks for correcting me.

---

### Post by foxholeunder on 2007-08-10
I think it is important to note that arvadawest wants to use a GUI as well as have it running server processes. The box will primarily be for serving; yet access to a GUI is desired.

---

### Post by oldos2er on 2007-08-10
> **arvadawest said:**
> Thanks Ann.  Have you run your systems continuously with Ubuntu?  How is the uptime on them?  I have read what others stated that they have not had to reboot much.  As you already read, I am going to use Ubuntu desktop ed as a quasi-server (file, dns, web, etc).  Thanks.  :)

 This is my home computer--no server software--and I shut it down every night. The only reason I've had to reboot is after upgrading some system software, never because of any instability.

---

### Post by Frak on 2007-08-10
Seriously, I thought you just didn't want a GUI. If you want the GUI, there isn't a downfall unless you run desktop effects, but even then, if its powerful enough, it'll be fine.

---

### Post by arvadawest on 2007-08-10
Thanks Frak and Jeremy!

Jeremy:  bingo, you hit right on what you said, "I think it is important to note that arvadawest wants to use a GUI as well as have it running server processes. The box will primarily be for serving; yet access to a GUI is desired."  

...do I really need to run Ubuntu server ed. if the desktop ed. will run the server processes just fine?  Thanks.

This is what I really meant.  Thank you.  We have sensitive information and need a reliable, scalable, secure OS that will help us migrate several terabytes of info and data.

We are very appreciative with everyone's great responses and you have all helped us make a decision, that for us, is highly critical.  Thank you.

Dr. AW

---

### Post by Frak on 2007-08-10
Its very easy to setup a server from Ubuntu Desktop ed.
> System->Administration->Synaptic Package Manager->Edit->Mark Packages by Task...->LAMP Server & DNS Server
That should do it :)

---

### Post by arvadawest on 2007-08-10
Thank you Frak!  That is helpful.

I wonder, is there a way for me to get a printer friendly of this thread that I started to keep for our records when our machine is delivered?  Sorry, probably a dumb question.  Thank you.

Dr. -aw

---

### Post by cacycleworks on 2007-08-10
at top of page under "thread tools" is "printer friendly version"

which gives you this: [http://ubuntuforums.org/printthread.php?t=521755](http://ubuntuforums.org/printthread.php?t=521755)

:D

---

### Post by bwtranch on 2007-08-10
Hi I just did jump on this thread and I noticed a lot of my buds are here, like Fx. he was helping on another project, (that we haven't quite got solved, yet, but will) I do agree with the prior posts. I think you do have to have a commitment to this. Because we are part of it. We all have a little bit of stock in Linux and we all commit a little of our time and effort to try to make it better. Different people do it in different ways. It's not a requirement for downloading, either. But, I can tell you, it's the nicest club I have ever joined and the dues are very reasonable :)

---

### Post by foxholeunder on 2007-08-11
Glad I could be of some help!

I am newish to the forums at least as far as jumping in and posting, but I have been running some *nix flavor for about 10 years now, and finding Ubuntu made me drop all boxes with Windows and go straight *nix -- 'cept of course the virtual machine environments... My main job requires knowing how to trouble shoot issues with Windows and the software the company is using. 

Nice to meet you!

Again, Good Luck and I will be monitoring the forums virtually daily for items I can help with!

---

