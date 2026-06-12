---
title: "Do I need virus and firewall protection?"
date: 2005-12-23
forum: Desktop Environments
---

### Post by nami on 2005-12-23
Hi

I was looking into installing a virus program from the wiki and it said that Linux rarely gets viruses so more people do not need to install virus protection programs.

So, as I am currently using Linux ubuntu 5.10 for web browsing, word processing, and in the not too distant future am planning to get back into where I left off my C++ studying, will I need or do I need to install some sort of virus and firewall protection to keep my confidencial files confidencial?

nami

---

### Post by Rinzwind on 2005-12-23
Virus: not really. If you feel you should go ahead. 
Firewall: yes. But it's better to have a router than to have software (that's prone to more and more serious bugs/exploits).

---

### Post by NeghVar on 2005-12-23
in a word, yes. having an anti-virus and firewall running is always a good idea. even though viruses are generally less frequent for Linux they do exist, and as for a firewall, no matter what you are using you probably shouldn't be connected to the net without one. Mostly though comon sense is the best system.

---

### Post by nami on 2005-12-23
I have a linksys BEFSR41 router, but I don't know if it's any good as a firewall.  I think I will try to install virus and firewall programs just incase.

Thanks

nami

---

### Post by NeghVar on 2005-12-23
looking at your routers specs it does what most other routers do, which provides decent protection against attacks.

---

### Post by rikai on 2005-12-23
Honestly, there's really no need at this point in thime to install an antivirus program.
Yeah, there are some linux viruses, but they're pretty much only proof of concept viruses.
Most of the stuff that hurts linux computers has to do with exploits, not viruses, and 99% of the time, those are directed at people running webservers and other such stuff.
As far as a firewall goes, since your router already provides a firewall, i'd use that.
Software firewalls are good, but hardware firewals are generally beter, and also offload the firewall work from the cpu.
if you STILL decide to sue a software firewall, i reccomend disabling the firewall in your router, because 2 firewalls will only lead to more headaches when you need to allow ports and such.

---

### Post by Imexius on 2005-12-23
Doesn't ubuntu come with its own firewall?

---

### Post by NeghVar on 2005-12-23
not that I know of

---

### Post by Ocxic on 2005-12-23
it does, but it's not installed, it's called Firestarter in synaptic, just remeber when opening port do it in both your firewall and your router, i do this and have no trobles.

---

### Post by briancurtin on 2005-12-23
[QUOTE=Ocxic]it does, but it's not installed, it's called Firestarter in synaptic, just remeber when opening port do it in both your firewall and your router, i do this and have no trobles.[/QUOTE]
isnt firestarter just the GUI frontend though?

edit: i couldnt think of the name in a memory lapse, but yes, it is just a frontend to iptables

---

### Post by zoiks on 2005-12-24
[QUOTE=nami]I have a linksys BEFSR41 router, but I don't know if it's any good as a firewall.  I think I will try to install virus and firewall programs just incase.

Thanks

nami[/QUOTE]

I have used the same one (as have many, I'm sure) and it will work fine as a firewall.  Just don't use things like the "DMZ" ports option.  You probably don't have to worry about a software firewall if you use the router, but if you want to use firestarter, knock yourself out.  The firestarter web site's FAQ list contains tips on how to get firestarter to start automatically when you boot your machine.

---

### Post by Ocxic on 2005-12-24
no, it's the firewall itself, and the gui

---

### Post by briancurtin on 2005-12-24
[QUOTE=Ocxic]no, it's the firewall itself, and the gui[/QUOTE]
it starts its own version of iptables (firewall), and the GUI manipulates it

---

### Post by anil_robo on 2005-12-24
**Issue1: Firestarter:** It's a GUI frontend to iptables. Looks like this: (Click on image below to enlarge):

[ATTACH]4796[/ATTACH]

It has a  lot of configurability just by GUI:

[ATTACH]4797[/ATTACH]

And if you hardly know anything about firewalls, it has an easy wizard as well:

[ATTACH]4798[/ATTACH]
Installation code: ```
sudo apt-get install firestarter
```
How to run: Applications-->System Tools--> Firestarter

[B]Issue2: Viruses:

[/B]There **are** known viruses for Linux. They screw you only when you're logging in as a root. Ubuntu does not include a root account by default, and you can safely use "sudo" command for most root actions. If you do need to create a root user sometimes, make sure to delete it right after your job is done.

Play safe!

---

### Post by bagel on 2005-12-24
[QUOTE=anil_robo]

[B]Issue2: Viruses:

[/B]There **are** known viruses for Linux. They screw you only when you're logging in as a root. Ubuntu does not include a root account by default, and you can safely use "sudo" command for most root actions. If you do need to create a root user sometimes, make sure to delete it right after your job is done.

Play safe![/QUOTE]

Hello there;

I'm using Linux for some time by now but I'm rather new to Ubuntu. So following your advice(and without ANY thinking at all.. *Very very stupid me*) I just did a quick:
sudo userdel root
(D'Oh).. Any suggestions how I might get back my root Acc.? (sudo $anycommand ) does not work:
sudo: no passwd entry for root!

Thanks, and excuse my stupidity today (-;
Bagel

---

### Post by AndyCooll on 2005-12-24
Your router firewall will probably be sufficient, though if you want to take extra precautions by all means follow the advice already given (Firestarter etc)

And though Linux might not get many viruses I still prefer to play safe. Just install clamav using synaptic. It happily works in the background.

:cool:

---

### Post by anil_robo on 2005-12-24
[quote=bagel]Hello there;

I'm using Linux for some time by now but I'm rather new to Ubuntu. So following your advice(and without ANY thinking at all.. *Very very stupid me*) I just did a quick:
sudo userdel root
(D'Oh).. Any suggestions how I might get back my root Acc.? (sudo $anycommand ) does not work:
sudo: no passwd entry for root!

Thanks, and excuse my stupidity today (-;
Bagel[/quote] 
```
sudo passwd root
``` Then enter your new password.

---

### Post by bagel on 2005-12-24
As I said:

greg@bagel:/etc$ sudo passwd
sudo: no passwd entry for root!

But thanks anyway (-;

---

### Post by nami on 2005-12-24
Thanks for all the advice!  Been very very helpful. :)

Just 2 questions

If I install firestarter from Synaptic Package Manager will I still need to configure it manually to get it to start when my machine boots?

I tried to install clamav from Synaptic Package Manager following the instructions in the wiki, but got the following error:

Click to enlarge:
[[IMG]http://img475.imageshack.us/img475/9766/clamaverror7hy.th.png[/IMG]](http://img475.imageshack.us/img475/9766/clamaverror7hy.png)

Any known solutions for this problem?

nami

---

### Post by NewbieNik on 2005-12-24
[QUOTE=nami]Thanks for all the advice!  Been very very helpful. :)

Just 2 questions

If I install firestarter from Synaptic Package Manager will I still need to configure it manually to get it to start when my machine boots?

I tried to install clamav from Synaptic Package Manager following the instructions in the wiki, but got the following error:

Click to enlarge:
[[IMG]http://img475.imageshack.us/img475/9766/clamaverror7hy.th.png[/IMG]](http://img475.imageshack.us/img475/9766/clamaverror7hy.png)

Any known solutions for this problem?

nami[/QUOTE]

Try running:-

sudo apt-get -f install

to fix any errors in installation packages, then run your clamav install.

Hope this helps.

---

### Post by NewbieNik on 2005-12-24
[QUOTE=bagel]As I said:

greg@bagel:/etc$ sudo passwd
sudo: no passwd entry for root!

But thanks anyway (-;[/QUOTE]

Couple of things:-
Try sudo passwd root to set a password first.

Have you tried using su?
**not recommended for everyday use**

This should, I say should, log you in to the terminal as root. If not, then without investigating further and searching in the posts and google, I would say re-install. **Don't Forget To Back-Up First!!!!!**

---

### Post by kosmic on 2005-12-24
[quote=bagel]Hello there;
 
I'm using Linux for some time by now but I'm rather new to Ubuntu. So following your advice(and without ANY thinking at all.. *Very very stupid me*) I just did a quick:
sudo userdel root
(D'Oh).. Any suggestions how I might get back my root Acc.? (sudo $anycommand ) does not work:
sudo: no passwd entry for root!
 
Thanks, and excuse my stupidity today (-;
Bagel[/quote]
 
The best solution for you is to install Ubuntu again :( because you realy deleted the root account...this is a big NO NO[-X [-X .
 
Ubuntu comes with the root account but is deactivated, what you did was remove the root account, so now you can't access nothing that need to have root previlegies :(

---

### Post by daibak on 2005-12-25
nami of post#19,

Got identical error message today and went back into Synaptic and re-marked clamav entry for Re-installation, then pressed Apply button to redo the original installation and Synaptic took care of everything perfectly second go-around.
Then ran freshclam and clamscan in terminal to be double-sure. All OK.

---

### Post by halfvolle melk on 2005-12-25
Why would you want a firewall? For denial of service stuff and the like?

---

### Post by nami on 2005-12-26
I tried that but am still getting an error when I log off.  I also noticed the following:

Click to enlarge:
[[IMG]http://img461.imageshack.us/img461/4080/freshclam5xc.th.png[/IMG]](http://img461.imageshack.us/img461/4080/freshclam5xc.png)

This happens when I try to install freshclam even for a re-install!

nami

---

### Post by daibak on 2005-12-26
[QUOTE=nami]I tried that but am still getting an error when I log off.  I also noticed the following:
...
This happens when I try to install freshclam even for a re-install!

nami[/QUOTE]

nami,

Having Ubuntu Backports in your sources.list will also help you get up-to-date clamav is what I read in the [wiki page]("https://wiki.ubuntu.com/ClamAV") and may have helped correct my first unsuccesful attempt to install clamav.
I've put up screenshots of clamav as now installed by Synaptic on this HP notebook together with clamav Properties versions showing backports too.

---

### Post by pmjdebruijn on 2005-12-26
To clear something up...

Firestarter doesn't have it's own version of iptables...

Firestarter is a graphical user interface which generates a script which in turn generates a ruleset for the standard netfilter firewall included in the Linux kernel.

Regards,
Pascal de Bruijn

---

### Post by briancurtin on 2005-12-26
[QUOTE=pmjdebruijn]To clear something up...

Firestarter doesn't have it's own version of iptables...[/QUOTE]
thats not what i have read

"Firestarter is in charge if it has been installed--it shuts down the normal iptables and maintains it's own set of "iptables"
"firestarter has it's own version of iptables--it stops the default iptables--more or less.."

i was under the impression that it stopped the service and created its own. could be wrong

---

### Post by lcg on 2005-12-26
[QUOTE=nami]will I need or do I need to install some sort of virus and firewall protection to keep my confidencial files confidencial?[/QUOTE]
As for virus protection: I have yet to find a virus, which will work properly in wine.
Seriously, there are viri for Linux out there, but they are very rare. And even if you really caught one of them, there wouldn't be much damage. As programs usually are executed with the limited rights of a user account, no real harm can come to a users machine.
Your data, however, is a different story. A virus executed with your privileges could wipe your home (that's why we're all making backups, right?) or even send out your data to any place in the world.

Regarding firewalls: I really think a firewall (or rather a packet filter) on a workstation is pretty pointless. A firewall is a security concept between networks, regulating access, usually implemented via a packet filter. You may want to read the [de.comp.security.firewall FAQ]("http://www.iks-jena.de/mitarb/lutz/usenet/Firewall.en.html") to get a better understanding of securing a computer and the concepts involved (site is in english).
And if anyone thinks I just said that firewalls are a bad thing, read again. There are only very few good reasons to use one on a workstation, though. (That being said, a well designed policy, implemented via netfilter/iptables, beats any Windows personal firewall hands down. Of course, the vendors of Windows personal firewalls don't really tell you that they are selling snake oil.)

HTH,
Lars

---

### Post by yaddoshi on 2005-12-26
[QUOTE=rikai]Honestly, there's really no need at this point in thime to install an antivirus program.[/QUOTE]

Actually - as a repair technician it would be useful to connect virus infected hard-drives (with Windows) via USB 2.0 to a LINUX system with a virus-scan utility capable of handling scanning various file-system types, especially if the infected drive was rendered unbootable.  You would have a safe environment to handle the infected system (since Windows virus-types are not intended for LINUX systems) and at the very least could recover data and make sure it is not infected.

I'm just curious as to whether there is any antivirus software that people have tried and like...

---

### Post by anil_robo on 2005-12-29
[quote=yaddoshi]I'm just curious as to whether there is any antivirus software that people have tried and like...[/quote]
See my post here (with screenshots for proof): [http://www.ubuntuforums.org/showthread.php?t=104001#19](http://www.ubuntuforums.org/showthread.php?t=104001#19)

---

### Post by sharke on 2005-12-29
I have been using Linux for 2 Years and in that time i have not had a virus. But i have had viruses in recieved emails which are intended for windows if i did not use a antivirus email checker i could have been helping spread theese viruses . I think it is irresponsible to not use a anti virus programme.
Regards
Sharke

---

### Post by veehell on 2005-12-29
[QUOTE=rikai]Honestly, there's really no need at this point in thime to install an antivirus program.
Yeah, there are some linux viruses, but they're pretty much only proof of concept viruses.
Most of the stuff that hurts linux computers has to do with exploits, not viruses, and 99% of the time, those are directed at people running webservers and other such stuff.
As far as a firewall goes, since your router already provides a firewall, i'd use that.
Software firewalls are good, but hardware firewals are generally beter, and also offload the firewall work from the cpu.
if you STILL decide to sue a software firewall, i reccomend disabling the firewall in your router, because 2 firewalls will only lead to more headaches when you need to allow ports and such.[/QUOTE]

ad_Two firewalls: i think it is more better, because you can manage more, (DMZ, dualhomed router, portforwarding, nat/pat) etc...for skilled user it is more secure...:)) for not so skilled it is really pain in the a$$. 

IMHO one FW to secure LAN and one FW to secure station(s) (for all OS/platforms)

ad_FW_itself: there are several FW (with gui or without - check synaptic/apt-get or debian/ubuntu sources via web)some of them have some basic configuration like FW on win platform...:( i hate them ;)
there is simply iptables...so it is better faster way to have FW i think..
for those, who dont like direct iptabling...there is quite nice tool called
[fireHOL]("http://firehol.sourceforge.net/")(it generates own iptables depend only on your config file which is quite easy to write for newbies) 

install firehol, change config file[..inspiration..]("http://wiki.gednet.com/DebianServerOSSecurity"), change default(/etc/default/firehol), run firehol (/etc/init.d/firehol start) and that's it...

ad_antivirus: i agree there is no issue to have it...if you have secured services (apache,ftp etc...) ... on linux there are some exploits to harm your computer not exactly viruses/worms in the way you know from win32 platform ;)

ad_router: some kind of "broadband" routers have small *nices installed on it, usually with some "iptables" like FW on it with WEB form to have it more comfortable to set it up. Also sav config and own edit and reload is possible (so you can bypas the forms and set really your specialities which the default form does not provide)

--- hm...i am quite flooding..so righ time to stop me.

---

### Post by lcg on 2005-12-29
> **sharke]I have been using Linux for 2 Years and in that time i have not had a virus. But i have had viruses in recieved emails which are intended for windows if i did not use a antivirus email checker i could have been helping spread theese viruses .[/QUOTE]
How? I mean, just by receiving a virus attachment, you do not automatically spread it. If your box is infected, then you could unknowingly spread the infection. But as a Linux user, you don't really have to worry about a Windows virus. IMO, correctly running a virus might not be too high on the list of priorities of the Wine developers (I could be wrong, though said:**
> I think it is irresponsible to not use a anti virus programme.
Just don't run the viri you receive. Unless you execute a program, it's all just a bunch of 0s and 1s.
People don't use condoms 24/7, it's the same with anti-virus software: If you're not doing something to risk an infection (read: execute each and every unknown email attachment, etc.), protection is essentially unnecessary.

HTH,
Lars

---

### Post by randlieb on 2006-01-01
i have clamav installed on breezy ubuntu and ran a scan. it found 9 viruses. do i need to do something further or does clamav delete them itself?

i see talk of wine. when using a windows app in wine does that open the os to viruses?

---

### Post by aysiu on 2006-01-01
[QUOTE=lcg]And even if you really caught one of them, there wouldn't be much damage. As programs usually are executed with the limited rights of a user account, no real harm can come to a users machine.
Your data, however, is a different story. A virus executed with your privileges could wipe your home (that's why we're all making backups, right?) or even send out your data to any place in the world.[/QUOTE] I don't know about you, but I consider my personal data and files to be *real* damage. My system files and such can be replaced. It would take me a maximum of three hours to reinstall and configure Ubuntu. Personal files can't be replaced unless they're backed up.

I think the best way to do things in terms of security:

1. Don't keep files with personal information (pins, passwords, birthdates, etc.) on your computer.
2. Back up your personal data regularly.
3. Don't be stupid when surfing the internet.

---

### Post by anil_robo on 2006-01-01
[quote=aysiu]
3. Don't be stupid when surfing the internet.[/quote]

Also see my [how-to on blocking advertisements and spyware on linux.]("http://www.ubuntuforums.org/showthread.php?t=110440")

---

### Post by lcg on 2006-01-02
[QUOTE=aysiu]I don't know about you, but I consider my personal data and files to be *real* damage. My system files and such can be replaced. It would take me a maximum of three hours to reinstall and configure Ubuntu. Personal files can't be replaced unless they're backed up.[/QUOTE]
From where in my post did you get the impression I didn't value my personal data? :)

Actually, I do. And I fully agree, Ubuntu is reinstalled easily (if that ever becomes necessary, which it shouldn't, as a virus would not have the privileges under your user account), your data usually is not.
That's why my personal data is replicated across three computers. The chance that all three copies are damaged at the same time is pretty slim.

Lars

---

### Post by DevilsAdvocate on 2006-01-02
I think you should use a classic risk-benefit analysis here:

What are the risks of installing a FW and AV program?  Few.  They're free and relatively easy to configure.  I don't believe they're very resource intensive either.

What are the benefits?  Potentially enormous.   Native virii are remote.  But hackers are not.  

So, in my analysis, there's almost no drawback and a potential huge gain, so why not?

I wouldn't go so far as to say it's irresponsible to not run AV, but I do believe there's is a benefit to the overall web-ecology.  Even if a virus doesn't run on your computer, you could be passing it on to those in you Address Book unknowningly.  If you spot it and clean it, well then there's no chance.

---

### Post by handy on 2006-01-02
On windoze you can definitely see anti-virus software slowing things down, you don't need a stop watch for that one.

You can't spread windoze viruses through any form of *nix. 

I started an identical thread to this some weeks back, I was told there was no need for anti-virus software, & firewall is questionable if you have a router.

Here is a very good link if you are interested:

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

Cheers,

handy

---

### Post by Storm Rider on 2006-01-02
Wow, no firewall installed and configured during the installation.   That's a bloody big oversight or mistake IMHO.

No firewall makes it real easy to connect to other machines on a network but leaving a machine with a highspeed connection to the internet without a firewall is foolish.  Most folks I know aren't using a router.

---

### Post by Storm Rider on 2006-01-02
[QUOTE=yaddoshi]Actually - as a repair technician it would be useful to connect virus infected hard-drives (with Windows) via USB 2.0 to a LINUX system with a virus-scan utility capable of handling scanning various file-system types, especially if the infected drive was rendered unbootable.  You would have a safe environment to handle the infected system (since Windows virus-types are not intended for LINUX systems) and at the very least could recover data and make sure it is not infected.

I'm just curious as to whether there is any antivirus software that people have tried and like...[/QUOTE]
I use F-Prot and gui qtFprot on my Linux systems.  Seems to work for me.  I usually have an EICAR test file sitting in my home directory just so I know the AV is working properly.

---

### Post by anil_robo on 2006-01-02
[quote=handy]On windoze you can definitely see anti-virus software slowing things down, you don't need a stop watch for that one.[/quote]
This is because most windows antivirus programs monitor files and processes in realtime. That's what slows it down. Whereas in Linux, we have just scanners - which you run every now and then to check the computer for viruses. The scanner will slow the system down (depends on your system processing power however) when it's running, just as antivirus programs slow things down in windows.
 
> You can't spread windoze viruses through any form of *nix. 
Yes you can! Let's say you got a virus infested file you downloaded from somewhere on your Ubuntu box. It won't do a thing to your Ubuntu. But if you post this file on a web server for windows users to download, you can understand the consequences. Email is another such way by which one can easily transfer viruses from a *nix box to a windoze box.
 
> I started an identical thread to this some weeks back, I was told there was no need for anti-virus software, & firewall is questionable if you have a router.
My router comes with a built-in firewall which is pretty much configurable. But still I'd like to have a firewall like firestarter for Ubuntu because I want to know what's happening! I don't know as yet how to read router logs, but firestarter does show me graphically what all connections it has refused. Comes pretty handy!
 
> Here is a very good link if you are interested:
[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/]("http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/")
 Thanks for this! :)

---

### Post by soulestream on 2006-01-02
> My router comes with a built-in firewall which is pretty much configurable. But still I'd like to have a firewall like firestarter for Ubuntu because I want to know what's happening! I don't know as yet how to read router logs, but firestarter does show me graphically what all connections it has refused. Comes pretty handy!

If you have no open ports, have turned off UPnP in your router, You do not need a firewall. The reason for this is that nothing can pass through the router. The beauty of NAT. If a person "hacker/cracker/kiddie" can get through a proper ly closed router, they will blow through a software firewall. 

Nnow the argument for having a firewall on your system, will be if you have open ports for web/ssh/ftp/filesharing/etc. Then you might need one. However, if you are allowing connections for port 22 through on your router, then you are going to have to on your firewall too, which means in that case the firewall is kinda useless, unless you are filtering certain connections.(which btw a real router will do also) 

The only other argument for a firewall is to monitor outgoing connections. In that case, that is my job. I know what is installed on my systems. I dont use a firewall on any of my systems windows or linux, unless im not behind my router. 

As far as anti-virus, I have never even actually seen a linux anti-virus in person. I know they exist, but dont really see the point in them. I guess I could see scanning my webserver for rootkits or something, but I monitor the logs closely, so I am usually aware of what is going on. Patch. Patch, Patch.


soule

---

### Post by dcstar on 2006-01-02
[QUOTE=Storm Rider]Wow, no firewall installed and configured during the installation.   That's a bloody big oversight or mistake IMHO.

No firewall makes it real easy to connect to other machines on a network but leaving a machine with a highspeed connection to the internet without a firewall is foolish.  Most folks I know aren't using a router.[/QUOTE]
That might be valid if an operating system as vulnerable as Windows was the issue, but since we are talking about Linux - and a Linux with the root account disabled by default - so I don't see much of a problem.

I prefer Ubuntu not to install a software firewall - which is of little use to those of us who use NAT - by default.

---

### Post by dna on 2006-01-02
[QUOTE=Storm Rider]Wow, no firewall installed and configured during the installation.   That's a bloody big oversight or mistake IMHO.

No firewall makes it real easy to connect to other machines on a network but leaving a machine with a highspeed connection to the internet without a firewall is foolish.  Most folks I know aren't using a router.[/QUOTE]


I have to jump in with my 2 cents. *There are no known linux viruses in the wild* Linux != Windows. I would be very comfortable hooking a Debian based distro straight to the internet out of the box with no firewall. The only open port I can think of is ping and it's pretty much bulletproof. I once took a stock freeBSD install and hooked it up in a dmz for over a year to log attack attempts and the worst thing that happened was my ISP sent an email saying I had a virus because ports were opened by the logging program that viruses like to use. I've been thinking about doing the same thing with a stock ubuntu server edition... 

I think the main problem here is the marketing departments of the big AV companies and people straight out of Windows. A Windows box won't last 2 min. on the net before it gets owned but any linux distro not made by some guy in his mom's basement can be put out there with no worries.

There might be some concern about sending viruses to your windows friends in email or through some file over the web but that's why the av companies make the big bucks and who really forwards all the V1agr4 spam anyway. The newest windows trojan/virus is very, very bad and it really sucks to be them right now but that's why I use Ubuntu so I don't have to worry about stuff like that.

---

### Post by Storm Rider on 2006-01-02
But,but ,but.....my Ubuntu machine is networked to my XP machine.   Without a firewall, it's straight forward to connect to the XP machine through Ubuntu.

Honestly, I don't know enough about this......guess that's why I'm worried about folks leaving the doors unlocked.  As for me, I'm behind a router a quick look at the firewall log and can say for sure that it blocks tons of crap.  Half of which, I've no idea what  it is.  If I check the log on the Windows machine firewall, I see it is getting NO action.  Before the router, it was blocking incoming traffic 3-4 times a minute:( 

Also, I believe that any of the other mainstream distro's I've installed all enabled a firewall during the installation.   Strange they would consisder it important but Ubuntu doesn't.

---

### Post by handy on 2006-01-03
[QUOTE=anil_robo]
Yes you can! Let's say you got a virus infested file you downloaded from somewhere on your Ubuntu box. It won't do a thing to your Ubuntu. But if you post this file on a web server for windows users to download, you can understand the consequences. Email is another such way by which one can easily transfer viruses from a *nix box to a windoze box.[/QUOTE]

I should have been more verbose on this one (most unlike me :D ): 

What I meant was that our email clients don't alow viruses to grab an address book & send themselves to everyone we have listed.

& yes if we are running a server we have responsibilities.
 
[QUOTE=anil_robo]
My router comes with a built-in firewall which is pretty much configurable. But still I'd like to have a firewall like firestarter for Ubuntu because I want to know what's happening! I don't know as yet how to read router logs, but firestarter does show me graphically what all connections it has refused. Comes pretty handy!
[/QUOTE]

That's your choice :D  NAT will do me just fine.  :KS 

[QUOTE=anil_robo]
 Thanks for this! :)[/QUOTE]

Your welcome...  :p 

handy

---

### Post by anil_robo on 2006-01-03
[quote=soulestream]If you have no open ports, have turned off UPnP in your router, You do not need a firewall.[/quote]
How do I know if I have  open ports? I have configured my router to allow VNC and Diablo2, but I guess Diablo2 was able to run fine even without allowing ports open for that! How?

> The reason for this is that nothing can pass through the router. The beauty of NAT. If a person "hacker/cracker/kiddie" can get through a proper ly closed router, they will blow through a software firewall. 
Does this mean firestarter is hardly of any use? Is it for cosmetic purposes only then? (I couldn't understand your quote below properly) :(

> Nnow the argument for having a firewall on your system, will be if you have open ports for web/ssh/ftp/filesharing/etc. Then you might need one. However, if you are allowing connections for port 22 through on your router, then you are going to have to on your firewall too, which means in that case the firewall is kinda useless, unless you are filtering certain connections.(which btw a real router will do also) 
How do I filter certain connections? And which ones?

> As far as anti-virus, I have never even actually seen a linux anti-virus in person. I know they exist, but dont really see the point in them. I guess I could see scanning my webserver for rootkits or something, but I monitor the logs closely, so I am usually aware of what is going on. Patch. Patch, Patch.
ClamAV is an antivirus for Linux which I occasionally use to scan the computer (particularly the drive shared by Linux and windows).
Can you elaborate what is "rootkits"? I keep hearing it but haven't been able to find "user friendly information" on this topic.
Thanks! :)

---

### Post by Omnios on 2006-01-03
I tryed using Clam on a p4 1.6 ghz and found it would east up a lot of my ram and cpu as seen in system manager. Though I proefear to run a anti virus on Ubuntu I found it hampered my computers performance to the point where I had probles with games. That was a while ago but I might be interesting in a stricly e-mail scanner as that would be more affective without eating up my resources.

 Also Yahoo mail pro comes with my isp so email viruses are not much of a problem even when using XP

---

### Post by soulestream on 2006-01-03
> How do I know if I have open ports? I have configured my router to allow VNC and Diablo2, but I guess Diablo2 was able to run fine

You look in your router config for port forward/filtering section and make sure its empty or any ports in there are disabled. As far as Diablo, I dont play games, but I imagine Its because you are originating the connection. Think of it more like you viewing a webpage, than you logging in from somewhere else to your home through VNC. 

> Does this mean firestarter is hardly of any use?

Its completely useless if you dont need it or don't know how to use it. I can think of many uses for it. One would be for forwarding packets and filtering users/ports if your router doesnt. Mine does so I dont need it.

> How do I filter certain connections? And which ones?

In your router config(or firewall) you may(should) have port forwarding or filtering setting where you can for instance 

********************************************************
allow - incoming connections from IP address ranged 52.45.XXX.XXX on port 22 and forward that connection to computer 192.168.12.100 port 22. 

disallow all others. 
*********************************************************
if you router doesnt allow this detailed of a connection(and some dont) then you can use something like iptables to do it for you. Firestarter is just a GUI for Iptables.

One thing to remember is that a firewall and a router do many of the same functions. If one doesnt do what you need, use the other.

soule

---

### Post by nami on 2006-01-21
I still can't install clamav?

Can someone please give step by step instructions on how to install it.  What I am doing is going into synamitcs and searching for clamav.  I click on the first result and install.  But that gives me errors?

PLEASE HELP!

---

### Post by nami on 2006-01-31
Finally got it to work:

[https://wiki.ubuntu.com/ClamAV?highlight=%28clamav%29](https://wiki.ubuntu.com/ClamAV?highlight=%28clamav%29)

---

