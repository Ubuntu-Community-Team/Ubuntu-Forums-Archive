---
title: "Ubuntu or fedora?"
date: 2007-07-14
forum: Fedora/RedHat and derivatives
---

### Post by ENN0 on 2007-07-14
I wanna know what is all around better...i am a programmer mainly in HTML and CSS !

---

### Post by igknighted on 2007-07-14
There is no "better".  Fedora is more up to date and requires a little more user input (but you get more control for it).  If you want to get more into tweaking your OS try Fedora.  If you want the OS to be pretty mcuh completely working OOTB use Ubuntu.  Granted Fedora is mortly working OOTB, but if you need anything non-free that Ubuntu includes (like mad wifi) then you need to do more setup.

Basically, they are designed for different users.  Ubuntu is designed to be easier for beginners, while Fedora is for more intermediate users who want more control.  Neither is a bad choice, I would try them both out (both have liveCDs you can download).

BTW, don't tell any C/C++/Java/etc. programmers that you "program" html and css, they take offense to that ;)

---

### Post by bfr on 2007-07-15
I'm kind of new to Linux, but I have a tiny bit of experience with Ubuntu.  Fedora wouldn't be too hard to figure out, right?  It's similar enough...?  Is there anything in particular that Fedora would be better at than Ubuntu or that Ubuntu would be better at than Fedora?  What would be better in the long run?

---

### Post by igknighted on 2007-07-15
> **bfr said:**
> I'm kind of new to Linux, but I have a tiny bit of experience with Ubuntu.  Fedora wouldn't be too hard to figure out, right?  It's similar enough...?  Is there anything in particular that Fedora would be better at than Ubuntu or that Ubuntu would be better at than Fedora?  What would be better in the long run?

Fedora tends to have newer versions of programs.  Fedora tends to upgrade to the newest kernel in the middle of a release.  This can lead to bugs, but also newer features and better hardware support.  If you aren't careful, a newer kernel could cause your graphics or wifi drivers to stop working (until you reinstall a newer kernel module) as well.

Personally, I like Fedora because:
1) RPM/YUM gives you better control of installing packages (especially in a multi-arch environment... 32bit apps on 64bit OS for example)
2) The artwork is Gorgeous
3) More repositories allow you to configure your system how you want... exmaple: If you want to stay with the initial KDE release and get just bug fixes you can use that repo, or you can use one that always keeps your KDE at the latest version, or theres even a KDE4 repo for testing it.  The result is you can have your system your way.  But, and this is where many get thrown off, you need to be aware of what repo's you are using.  Clearly having multiple KDE repo's could create conflicts.  This is where RPM hell comes from.  It is really not the result of RPM's sucking as many like to believe, but users not being aware of the conflicts in the repo's they are using.  So if you use these extra repos, be cautious.
4) The Fedora installer is much better, it lets you custom pick the apps that are installed.  Don't use Skype?  Don't install it.  You can of course just select the default to save time, but the option to choose is nice.

Since you are a Ubuntu user, I will assume you know Ubuntu's strong points.  It is a simpler life, but you don't get as much control.  It really comes down to how much do you want to know/have to know about your system to operate it, and what you get in return.  From Fedora you can even go a step up to something like Gentoo, FreeBSD or even Arch/Slackware.  These give even more customization options, with the expectation of the user knowing more about the system so he/she can configure it properly.

It can't hurt to try.  If its too much, then go back.  But I think both are great choices, just depends which suits your needs better.

---

### Post by bfr on 2007-07-15
Thanks, that really helped.  :)

Also, sorry if this is too off-topic, but would you happen to know if it would be possible to initially install Fedora with GNOME, but then install KDE on top of it, so I could switch back and forth between the two?  If it's possible, would it be safe, or would there be a high probability of crashing and conflicts?

---

### Post by igknighted on 2007-07-15
> **bfr said:**
> Thanks, that really helped.  :)

Also, sorry if this is too off-topic, but would you happen to know if it would be possible to initially install Fedora with GNOME, but then install KDE on top of it, so I could switch back and forth between the two?  If it's possible, would it be safe, or would there be a high probability of crashing and conflicts?

Should work just fine.  They are both on the DVD installer if you choose to customize the packages installed (otherwise selecting "dektop" packages will only install gnome). Issues tend to arise when you choose repo's that have different versions of the same package.  For example, non-free stuff can be gotten from Livna, fresh-rpms and a few other places.  These repo's can conflict with each other.  While it is OK to install software from both, never add them permanently to your YUM database and do a systemwide update (the equivelent of adding both to your sources.list file in ubuntu and running apt-get update && apt-get upgrade).  Its best to leave them disabled unless you are trying to update a specific program from one.

---

### Post by ThinkBuntu on 2007-07-16
I'm going to give Fedora a try...something does seem nice that actual Red Hat employees maintain many packages. And as far as corporate distros, I trust and respect Red Hat far more than Novell, whether it's fair or not. I've tried so many distros, it's funny it's taken me so long to get to Fedora!

---

### Post by stmiller on 2007-07-18
Fedora is great, and new package updates come right away. So if something new comes out, you can be sure it will be in your updates in less than 12 hours. Fedora seems to run very quickly too, faster than Ubuntu on hardware I've used it on.

---

### Post by ThinkBuntu on 2007-07-18
> **stmiller said:**
> Fedora is great, and new package updates come right away. So if something new comes out, you can be sure it will be in your updates in less than 12 hours. Fedora seems to run very quickly too, faster than Ubuntu on hardware I've used it on.
Yet Sunbird isn't available, nor is Streamripper (although Streamtuner is...)

---

### Post by kellemes on 2007-07-20
I cannot find any good reason to use Fedora period!
There package-management-system is horrible and it's backed bu RH, please.. if you need to choose between these two (although there are 358 active brands), let it be Ubuntu.

---

### Post by Frak on 2007-07-20
> **kellemes said:**
> I cannot find any good reason to use Fedora period!
There package-management-system is horrible and it's backed bu RH, please.. if you need to choose between these two (although there are 358 active brands), let it be Ubuntu.
Thats a common misconception, much of that has been fixed in the latest version of Fedora Core 7.
But I say, if your working for more production purposes, Ubuntu. For casual use, Ubuntu or Fedora.

---

### Post by igknighted on 2007-07-20
> **kellemes said:**
> I cannot find any good reason to use Fedora period!
There package-management-system is horrible and it's backed bu RH, please.. if you need to choose between these two (although there are 358 active brands), let it be Ubuntu.

Say you have an x86_64 system, then you would definitely want Fedora.  Fedora (and RPM distro's in general) are able to handle multiple architectures properly.  This makes running things like 32bit firefox (for flash) much easier.  This is just one example.  There are myriad reasons to choose Fedora over Ubuntu (enterprise or casual use).  So while it was not your ideal, please be objective and state why it wasn't for you and move on.  Your extra digs were uncalled for.

---

### Post by tcoffeep on 2007-07-21
I've tried installing Fedora, but I found it horrifyingly slow. :) So I say, Go Ubuntu :)

---

### Post by darksidedude on 2007-07-24
I've used fedora in the past, I like how yum works faster, but in the end why do something that takes 30 mins of dependency hell in fedora, when ubuntu and Gdebi do it in about 4? Fedora does have some advantages but it is backed by a real company, it seamed to me they were trying to get me to by the "real redhat"

---

### Post by Zzl1xndd on 2007-07-24
I came to Ubuntu from Fedora ;)

---

### Post by igknighted on 2007-07-24
> **darksidedude said:**
> I've used fedora in the past, I like how yum works faster, but in the end why do something that takes 30 mins of dependency hell in fedora, when ubuntu and Gdebi do it in about 4? Fedora does have some advantages but it is backed by a real company, it seamed to me they were trying to get me to by the "real redhat"

Doubtful.  They need you to use Fedora in order to make sure that Red Hat is enterprise-level stable.  Plus, RHEL is aimed (and priced) in a range that is clearly targeted at corporate users, not home users.  If you don't believe me, try out CentOS.  It is rock solid stable, but lacks a lot of home desktop-specific packages.

As for YUM, I'm still not sure what you mean by dependency hell.  Spend 5 minutes and read the documentation, and they very clearly state which repo's are OK to mix and which are not.  Note: this does not mean that you cannot install a few things from these incompatible repo's, but NEVER do a system update with them enabled.

Yes, it requires you to do a little bit of research and it is different than Ubuntu.  It is not for everyone.  My point is that trashing a distro for user error is misleading.  Just say, "I found the YUM/Fedora method of package management confusing and made mistakes while using it.  Be aware that there is more to managing repo's in Fedora and if you are not ready/aware it can cause major issues."  Since there is less end-user addition/subtraction of repo's in Ubuntu it isn't as widespread, but there have been several high-profile repo's that caused identical types of issues in Ubuntu (Trevino's repo for Dapper had issues at one point IIRC), so it's not something that is Fedora specific.

---

### Post by angryfirelord on 2007-07-24
For those that haven't used FC7, yum is a lot faster in this version. I also believe Red Hat stays true to open-source, unlike *cough* Novell, Linspire, Xandros *cough*. 

I you can't decide between Ubuntu & Fedora, then just get a quarter and flip it....

---

### Post by donkyhotay on 2007-07-25
I used fedora for quite awhile back and although it wasn't my first distro it was the one I really learned alot about linux on. I really don't consider fedora easier or harder then ubuntu, merely different. The main reason I switched to ubuntu and use it exclusively now is because it seems like debian packages are more likely to be offered compared to RPM packages. I tried using debian however had issues with the installer (debian wouldn't recognize my NIC's and I couldn't get the drivers without access to the internet, but without NIC's I couldn't access internet). Personally though I would recommend getting a liveCD, trying both of them out and finding out what you prefer. The debate between fedora vs. ubuntu (or any other distro's) is just like the debate between KDE and gnome. Ultimately they both do the job so find the one you prefer and work with it.

---

### Post by rajesh0975 on 2007-08-23
Hi,
    I think everyone has different expectations form their OS. Fedora  won't be comfortable for  a newbie. Few basic tasks such as mounting non Linux partitions and installing gstreamer codecs for mp3 and DVD are manual. 

   I didn't like few things with Fedora 7 which I tried only for a week. The software updates on install are huge which I downloaded during my free DSL usage at night.  The annoying thing was yum downloading close to 6MB everytime I switched on my DSL. For someone with a limited daytime DSL usage, it wasn't comfortable.
 
   Hence I decided to terminate my Fedora trial and return back to Ubuntu.:)

---

### Post by igknighted on 2007-08-23
If you want to try it again, Fedora 8 is going to use delta RPMs to greatly cut down on what needs to be downloaded in patches.  I think Suse uses a similar system.  Its nice, especially for stuff like minor bug-fixes for OO.o, to not have to download the whole program again.

---

### Post by Caraibes on 2007-08-25
Fedora is a really good distro. I have been using FC3, FC5, FC and now F7. I think it is simply the best for a desktop (my personal opinion). The only time I need to install a *Buntu distro is for laptops, because it is undeniable the *Buntu hase much better wireless cards drivers support.

I use F7 on my main box, and Debian Etch on my 4 others desktops (for the whole family)... I use Xubuntu Dapper with Fluxbox on my older laptop, sticked with Dapper because of the wireless card drivers... 

But Fedora is more flexible than *Buntu for a desktop, faster, more up to date... Very easy to configure : just add the livna.org repos and off you go !

---

### Post by flatwombat on 2007-08-26
With drives being so large and cheap these days, why limit yourself to just one or the other distro?  I'm booting 7 off of two 80 gig drives and still have plenty of room to spare when I find that interesting #8.  

Personally, I like to take Live CD distros for a spin before installing.  How well the Live CD boots and performs is a good indication of how well my hardware is going to be accepted and if I like the general 'feel' of the distro.

Another suggestion might be to check out the 'variants' of both Fedora and Ubuntu.  For Ubuntu, there's Mint, Pioneer, Elive plus a dozen or so more (grab Elive & Mint - awesome!).  For Fedora, there's Blag, Momonga and Berry - those variants aren't FOSS either!

---

### Post by InTrance on 2007-08-30
I was a Fedora user for years and still am on my laptop.
Then my main computer crashed and I had to replace it.
So I decided I should try Ubuntu and have never looked back, I intend to change my laptop to Ubuntu.
Fedora is a nice OS it requires some extra user knowledge and editing of .conf files to make things work the way you want them to.
Ubuntu is simpler for an average user to configure and in my case seems more stable.
If a new user asked me what Linux OS to try I would point them to Ubuntu.

---

### Post by Zef_ on 2007-09-03
The fedora 7 live cd is great. I'm trying out the kde version now, and it allows you to load the system into ram to try it out - no horrible cd whirring. Also, it's detected and set my display properly to 1680x1050, something that ubuntu/kubuntu didn't do. I think if you like kde, fedora is a better choice than kubuntu. If you prefer gnome, then it's still a toss-up.

I'm well impressed with fedora and will definitely be using it for my workstation. Ubuntu's time on my laptop may be limited.

---

