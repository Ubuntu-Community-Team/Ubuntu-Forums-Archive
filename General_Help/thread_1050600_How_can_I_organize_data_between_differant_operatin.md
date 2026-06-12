---
title: "How can I organize data between differant operating systems"
date: 2009-01-25
forum: General Help
---

### Post by whazzzzzup17 on 2009-01-25
Basically I have only multi-booted a couple times and im trying to find a productive way on organizing my data between each operating system. I have made an extra partition to store "Data", such as programs like Firefox,aim,etc... Which is label "Drive D"

However it as been a hassle to share between different systems such as xp home,xp ultimate,vista ultimate,Linux Ubuntu 8.10. For example I'll install "Mozilla Firefox" on one operating system(Windows Xp Professional) and I will install it into a dictionary on my "Data" partition such as *"D: Program Files/Browsers/Mozilla Firefox"*.

Everything works fine so I edit my Firefox to my settings. However, if I restart my computer and load up a different operating system on start up, my "profiles/information/settings" will be missing and it will only be accessible if I load up the operating system in which I installed it from.

> **Note**: When I mean "not accessible" I mean that the settings I had on the previous operating system are gone, and I would have to manually do it over again" I can still load Firefox by navigating to my "Data" partition *(D: Program Files/Browsers/Mozilla Firefox/Firefox.exe)*, its just that all the settings are back to default, and I can only get them back if I load the operating system that I installed them on.

I did find away around this, and it was to navigate to *"C:\Documents and Settings\Administrator\Application Data"* and simply just coping the application folder to each of my operating systems partitions. This case doesn't work for all applications though. Such as Aim.

Is there a better way of doing this? For example changing the application data to be stored on the "Data Drive" with the rest on my installations? Is there other folders that save program data? Would you suggest a different way on storing data between different operating systems when multi-booting/dual-booting?

All suggestions will help a lot. Thanks

---

### Post by whazzzzzup17 on 2009-01-25
Basically I have only multi-booted a couple times and im trying to find a productive way on organizing my data between each operating system. I have made an extra partition to store "Data", such as programs like Firefox,aim,etc... Which is label "Drive D"

However it as been a hassle to share between different systems such as xp home,xp ultimate,vista ultimate,Linux Ubuntu 8.10. For example I'll install "Mozilla Firefox" on one operating system(Windows Xp Professional) and I will install it into a dictionary on my "Data" partition such as "D: Program Files/Browsers/Mozilla Firefox".

Everything works fine so I edit my Firefox to my settings. However, if I restart my computer and load up a different operating system on start up, my "profiles/information/settings" will be missing and it will only be accessible if I load up the operating system in which I installed it from.

Quote:
Note: When I mean "not accessible" I mean that the settings I had on the previous operating system are gone, and I would have to manually do it over again" I can still load Firefox by navigating to my "Data" partition (D: Program Files/Browsers/Mozilla Firefox/Firefox.exe), its just that all the settings are back to default, and I can only get them back if I load the operating system that I installed them on.
I did find away around this, and it was to navigate to "C:\Documents and Settings\Administrator\Application Data" and simply just coping the application folder to each of my operating systems partitions. This case doesn't work for all applications though. Such as Aim.

Is there a better way of doing this? For example changing the application data to be stored on the "Data Drive" with the rest on my installations? Is there other folders that save program data? Would you suggest a different way on storing data between different operating systems when multi-booting/dual-booting?

All suggestions will help a lot. Thanks

---

### Post by cardinals_fan on 2009-01-25
Well, your software won't be compatible across all those systems.  Setting that partition as your home directory on multiple Linux systems will do the trick, but it can also be a bit risky.

---

### Post by whazzzzzup17 on 2009-01-25
Well I have I use two different Windows Xp's, and two versions of Vista, and 1 Linux. The reason for that is because I tweak one version of each, so they can run faster. I also use them for games,and the defualt I usually add skins and stuff to show off on my laptop. So reconfiguring each software is a hassle, and Im trying to find a better solution.

Or at least find a way to change the default installation location, as well as the default location for the "Application data" to my data drive.

---

### Post by cardinals_fan on 2009-01-25
> **whazzzzzup17 said:**
> Well I have I use two different Windows Xp's, and two versions of Vista, and 1 Linux. The reason for that is because I tweak one version of each, so they can run faster. I also use them for games,and the defualt I usually add skins and stuff to show off on my laptop. So reconfiguring each software is a hassle, and Im trying to find a better solution.

Or at least find a way to change the default installation location, as well as the default location for the "Application data" to my data drive.
You could just copy the config files between partitions.

---

### Post by mb_webguy on 2009-01-25
The problem with your specific example of Firefox (and your question in general) is that the user settings for applications aren't stored in the installation directory (i.e. "C:\Program Files" in Windows or "/usr" in Linux) but rather in the user directory, and the location and structure of the user directory is different for each OS -- even between different versions of Windows.  

For example, Linux keeps the settings for Firefox in "/home/<username>/.mozilla/firefox", while Windows 98/ME stores those settings in "C:\WINDOWS\Application Data\Mozilla\Firefox", Windows XP/2000 uses "C:\Documents and Settings\<username>\Application Data\Mozilla\Firefox", and Windows Vista uses "C:\Users\<username>\AppData\Roaming\Mozilla\Firefox".   In order for these settings to be universal, you would have to use symbolic links or shortcuts in all (but maybe one) of your OSes to point to the actual location of the Firefox settings directory, which, obviously, would require a bit of work.  When you further consider that you would need to do this for each cross-platform application, you have to start wondering if it's worth the hassle.

For a system with multiple versions of Windows, this isn't necessarily that difficult.  Just have a folder on a shared partition that is used by Windows 98/ME as "C:\WINDOWS\Application Data", by  Windows XP/2000 as "C:\Documents and Settings\<username>\Application Data", and by Windows Vista as "C:\Users\<username>\AppData\Roaming".  But when you add Linux (and MacOS, which is a close relative to Linux) into the mix, things aren't so simple, since (unlike Windows) Linux is case-sensitive.  Linux will not recognize "Mozilla\Firefox" as ".mozilla/firefox".  You'd at the very least have to get a bit more creative with your links.  Furthermore cross-platform applications don't necessarily store application data in the same way under Linux as they do in Windows, which means that even if you linked the "~/.mozilla/firefox" directory to the "Mozilla\Firefox" directory on the shared partition, there's no guarantee that everything would work correctly.

For these reasons, most people with multi-boot systems simply make sure their user data (i.e. documents, movies, music, etc.) are accessible from each OS, and then deal with each OS and its applications individually.

---

### Post by whazzzzzup17 on 2009-01-25
Yeah that's what I been doing, but that means I gotta do it all the time, to all four operating systems. Anytime I find a new software/bookmark/favorite. Anything ;d(

---

### Post by whazzzzzup17 on 2009-01-25
Well I know there are commands for the windows registry to change the different installation locations. Maybe if I found out how to change the default location for application data and change it to a "Application" Folder on my data drive, then it would be easier. 

All I would have to do is edit the registry  on all my windows operating systems and change the default application data location to the one on my "Data Drive".

I don't mind not having it for Linux (Ubuntu 8.10), but for all the windows, it sounds like a good idea. I don't know if there is a way to do that though.

***_REVISED_***

Okay this idea might work. However you can only use it on Windows Platform only, but it does save some work.

The link below goes to a tutorial of how to edit your registry to change the default location for your "Application Data" folder. Thus, allowing you to install each program one time, without installing them on each separate windows operating system. This also means you can bookmark a page on Firefox, restart your computer, load a new windows operating system, and it will be just like it was before.

I haven't tried it at the moment, but I will first thing in the morning. I'm about 90% sure this will work. I'll make a tutorial later if it works alright for me. 

As for Linux (Ubuntu 8.10). I guess I'll just have to deal with reinstalling each software, and manually editing them all over again. 

```
http://www.liutilities.com/products/registrybooster/tweaklibrary/tweaks/10471/
```

---

### Post by cardinals_fan on 2009-01-25
> **whazzzzzup17 said:**
> Yeah that's what I been doing, but that means I gotta do it all the time, to all four operating systems. Anytime I find a new software/bookmark/favorite. Anything ;d(
If you don't mind selling your soul to Google, the Google Toolbar will sync your bookmarks.  I think there are Firefox addons that do the same thing.

---

### Post by mb_webguy on 2009-01-25
You shouldn't have to mess around with the registry.  Just move the application data to a shared location, and then delete (or, to be safe, rename) the "Application Data" and "AppData" folders and make shortcuts in their place pointing to the shared application data location.

---

### Post by whazzzzzup17 on 2009-01-25
I actually thought that there might be away to change the default "Application Data" location for each Windows System, and change it to a "Data Drive/Data Partition". 

So I actually found an article of it, however you can only use it on Windows Platform only, but it does save a lot of time.

The link below goes to a tutorial of how to edit your registry to change the default location for your "Application Data" folder. Thus, allowing you to install each program one time, without installing them on each separate windows operating system. This also means you can bookmark a page on Firefox, restart your computer, load a new windows operating system, and it will be just like it was before.

I haven't tried it at the moment, but I will first thing in the morning. I'm about 90% sure this will work. I'll make a tutorial later if it works alright for me. 

As for Linux (Ubuntu 8.10). I guess I'll just have to deal with reinstalling each software, and manually editing them all over again. 

```
http://www.liutilities.com/products/registrybooster/tweaklibrary/tweaks/10471/
```

---

### Post by whazzzzzup17 on 2009-01-25
Yeah I see your idea, but wouldn't that mean you would have to do that every time you installed something or added a new bookmark to your browser? That can be a hassle. To tell you the truth, I don't fully got the gist of your idea. I'm a little lost.

**Revised**

I think I may of found your idea. I think were talking about the same thing. lol. Changing the default "Application Data" to a shared location, for example my "Storage Drive". 
Not sure if you said there would be an easy way for Linux to share or not? Because you said they were case-sensitive.

---

### Post by fwojciec on 2009-01-25
It is by all means possible to share Firefox/Thunderbird data between different OSs, including Windows in Ubuntu.

I could be wrong, but what you seem to be describing as "sharing data" is actually just installing Firefox to a shared partition, or am I misreading what you're saying?

In either case...

Basically the idea is that on each OS you create a custom default Firefox user profile and explicitly specify the directory where Firefox will store user data.  The default Firefox user profile on each of the OSs must use the same directory to store user data.  The directory, for obvious reasons, has to be located on a partition that's shared by/visible to all the OSs.  If you google this you should find a lot of tutorials on how to do it.

An analogous procedure can be used to share mail data using Thunderbird on different operating systems.

---

### Post by whazzzzzup17 on 2009-01-25
Yeah you basically got the gist of my idea. However I was just using "Firefox" as an example, and I mean any program I install. But since I use a different partition for my data (Storage Drive), *which is what everybody should do because it allows you to reformat easier*, I also added a folder to my "Storage Drive" which is for Application data. So basically I just changed the default location for saving the "Application Data" files.

So in my (Storage Drive), I have the folders "Program Files" and "Application Data", just make sure you edit the registry on each Windows Operating system. 

**Note:** *Installing Firefox to a shared patition "Storage Drive" will allow each Operating system to use it. However, what im trying to explain is to also make "Application Data" to a shared partition, because that is what holds the settings for each program. *

As for Linux things aren't so simple, since Linux is case-sensitive. Linux will not recognize "Mozilla\Firefox" as ".mozilla/firefox". So unfortunatily would have to manage and reinstall everything like normal.

---

### Post by mb_webguy on 2009-01-25
What I was saying was simply to delete the regular "Application Data" folder and create a shortcut called "Application Data" where that folder was, which points to where you want to keep your shared application data.  On Vista, you would delete the "AppData" folder and create a shortcut called "AppData" pointing to the location of the shared application data.

Then, whenever you install or run a program, the version of Windows you're using will look in "Application Data" or "AppData", but because those are now shortcuts instead of folders, they will be redirected to the shared application data.

Yes, you could fiddle with the registry to change the locations where application data is stored, but in my experience it's better to avoid editing the registry if at all possible.  And my solution is much simpler than editing the registry.

---

### Post by whazzzzzup17 on 2009-01-25
I see your idea. Never thought of that, and you are defiantly right. Ill use your idea.

I never thought of using a shortcut like that. I can use that for so many other things as well. Thank you.

As for linux? Basically just install everything by itself and not worry about that right? Because it is case sensitive?

---

### Post by mb_webguy on 2009-01-25
Yes, that's what I'd do.  And when it comes to Firefox, it's easy enough to export and import bookmarks and other information.  You might want to check out the [FEBE extension]("https://addons.mozilla.org/en-US/firefox/addon/2109").  It lets you easily backup and restore your entire Firefox profile.

---

### Post by overdrank on 2009-01-25
Please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by whazzzzzup17 on 2009-01-26
Hey mb_webguy

I used your way with the shortcut, however I installed aim on one of my windows partition, and then when I load up another windows, aim doesn't load. 
Do you know why? 

Is there another place where windows stores information for programs? Im not sure why it doesn't work. All my other programs are working fine, and I have to admit this way is so much better. Its a completely better way with communicating with different windows operating systems.

---

### Post by mb_webguy on 2009-01-26
It's possible that AIM stores some information in another location.  If so, this is a nonstandard behavior for a Windows application.  But since there's no way to ensure that every software developer follows the standards for developing software for a particular platform, this sort of thing is unfortunately possible.

Look in the Program Files folder for AIM, and see if you can find any files or folders that look like they might be data or configuration files.  If so, copy these files to the appropriate folder in your new application data directory, and create shortcuts to them from the original location.  And of course, make sure the file or folder and the corresponding shortcut have the same name.  You'll need to make similar shortcuts for the other operating systems.  I'm afraid I can't be any more specific, since AIM is apparently not following standards for Windows applications...

Btw, if AIM does store application data in Program Files, I'm surprised that it will run in Vista, since User Account Control considers Program Files a protected folder.

---

### Post by whazzzzzup17 on 2009-01-26
I'm pretty sure Aim doesn't store its Application in the installation folder, because I installed all my programs on a shared partition, in a new program files folder. As well with the Application folder tip you gave me. So basically my "Shared partition" has two folders; "Program files" and "Application Data".

So if it did save its information data in the program files folder, it would be shared with of the operating systems anyways and should work as normal. 
So Im guessing that it stores it somewhere else, like a windows folder or something stupid like that.
I can't even get aim to load on other windows operating systems. I even tried it with another version of xp, to make sure it wasn't vista.

Also I got another problem which might solve the Aim problem. I also installed "Eset Nod 32" on windows xp. However If I load my other windows xp and try and load it, I'll get an error saying can't communicate with kernel. Which basically means it can't find the service that is running in the background. 

So that service only installed on "windows xp 1". Do you know how to add the services to my other windows xp? 
You can check your services by holding the windows key and the "r" key. Then by either typing "msconfig" or "services.msc"

---

### Post by mb_webguy on 2009-01-26
Well, one option is to use some other IM client like Pidgin.  It can handle numerous IM protocols, including AIM.

---

### Post by whazzzzzup17 on 2009-01-27
Yeah, I have many instant messangers installed, i was just wondering how just since were on topic. Pluss I love learning new things. 
Especially the ones the simplify things .


How about the Eset? Some programs install services as well with the program. Like my Nod 32 anti virus. How can i add those to my other operating system?

---

### Post by handy on 2009-01-27
> **whazzzzzup17 said:**
> 
Yeah, I have many instant messangers installed, i was just wondering how just since were on topic. Pluss I love learning new things. 
Especially the ones the simplify things . 

You could have fooled me "Especially the ones th[at] simplify things."  You really have created an over complicated system imho. :-)

I use OSX & a variety of distro's plus a standalone IPCop box & a FreeNAS box.  As far as Firefox is concerned I set it up how I like it on OSX & the distro's & use the Foxmarks plugin to keep my bookmarks sychronised (which it does beautifully without compromising my privacy).

> **whazzzzzup17 said:**
> 
How about the Eset? Some programs install services as well with the program. Like my Nod 32 anti virus. How can i add those to my other operating system?

You could go & find a free PII or PIII box at the recyclers & make an IPCop box which could do your firewall/anti-virus/proxy chores (plus a whole lot of other services you can choose from) for all OS's/machines on your LAN, transparently.  

You could get another one of those free PII/PIII boxes & install a larger drive in it, set it up as a FeeNAS box & you would have a transparent storage device available for all that you allow to use it, be they windows, OSX, BSD or any of the distro's.

If you like learning about things that simplify things, have a look at [***_IPCop_***]("http://www.ipcop.org/") / [***_Copfilter_***]("http://www.copfilter.org/") & [***_FreeNAS_***]("http://www.freenas.org/"), they are mature highly polished & free solutions that transparently provide OS independent security & storage.

---

### Post by whazzzzzup17 on 2009-01-27
Okay I'll check those out.
As for it being complicated, its actually pretty easy. It just seems complicated because we were talking about different ways to do it.
Its just simply replacing a folder with a shortcut that points to a data drive. Thus allowing it to store both the installation files "Program files" and data files "Application data" all on one data drive that is shared between operating systems.
Ill check out those links

IPCop box
seems to be for linux. im sorta working on the windows os's and sharing the same "services". We were trying to shared data between linux, but we got stuck :d(

---

### Post by handy on 2009-01-27
> **whazzzzzup17 said:**
> 
IPCop box
seems to be for linux. im sorta working on the windows os's and sharing the same "services". We were trying to shared data between linux, but we got stuck :d(

IPCop is used as a firewall/proxy +, on many corporate windows systems, with 400+ windows machines hanging off one low powered IPCop box.  IPCop (as you will find if/when you review their site) is a specialised install that is quite quick & easy to set up once you have worked out how ;-) a PII is ideal as they use such a small amount of electricity, I'm using an old PIII with an 8Gb drive & 256Mb of RAM, & it never does more than idle.  

My internet speed is faster than when I was using the router in my ADSL modem/router, even though I have the Privoxy & ClamAV anti-virus services provided by the IPCop/Copfilter add-on, this is due to Linux handling data packets in a superior fashion to windows & cheap windows based routers. (Not that I need anti-virus protection on my system, but if it doesn't slow the system down why not use it?) 

It is also possible to run multiple anti-virus services via Copfilter, they also update themselves on the schedule that you very simply set, for instance my ClamAV updates at 1.am every morning.  Copfilter incorporates itself into the IPCop maintenance GUI beautifully, I must say I am still knocked out by the elegance of the system after having used it for some months.

You can not use the IPCop box as a data storage center, doing so would be very difficult & would dramatically interfere with your network's security.

For data storage using FreeNAS, which again is also a tiny & very specialised build (though this time based on FreeBSD & not Linux as is IPCop), which installs very quickly & easily, is also (like IPCop/Copfilter) managed via a slick, web browser interface from a client machine.

FreeNAS makes the data stored on it easily available to windows, BSD, Linux, OSX, Solaris & whatever else can use the large range of networking systems that it provides as services which you can choose to enable.  

FreeNAS also has reliable soft RAID built in for those that choose to use it, & of course can use hardware RAID.

For my personal use, I use FreeNAS on a PIII/1000Mhz 512Mb RAM with no RAID, as there is no benefit provided by RAID due to the LAN speed being the bottleneck, even Gb LAN will not benefit from RAID set ups that provide decreased access speed & faster throughput of data as it is still the bottleneck, adding multiple Gb NIC's to each machine (where possible) can certainly increase data throughput though.

I have not done it yet, but it is possible to set FreeNAS up as a torrent slave, where you have a shared watch directory on your FreeNAS box, that when you drop a .torrent file in it, it will see it & autonomously take control of the .torrent.  This means you can turn off your clients & go to bed leaving your (hopefully low powered old) FreeNAS box (& in my case my low powered old IPCop box as well :-)) running whilst you sleep.

Setting up the torrent slave is not simple, everything else to do with FreeNAS is simple, from my experience thus far.

For those that have use of them, I can't recommend IPCop/Copfilter & FreeNAS highly enough. The hardware (apart from the potential need of more drive space on the FreeNAS box) should cost nothing or very close to it.  Old PII's & slower PIII's are cheap to run on electricity, unless you have a RAID rig with 4+ drives spinning perpetually, as each drive is usually worth 10 watts when working.

There is the possible added expense of a PCI to SATA card or an IDE to SATA adapter card for the using SATA drives on the old motherboards.  If you are interested in the PCI to SATA card solution apparently the VIA chipped cards are well supported.  There is also a list of supported hardware on the FreeBSD site.

---

### Post by JSchoeck on 2009-02-06
How can I create a symbolic link on my Ubuntu partition that points to the Firefox / Thunderbird config folders on my Windows partition?

I read above that it works the other way around, but since I want to keep the actual data on my NTFS partition and not on the (/home) Ext3 partition I need a symlink pointing the other way.

Please guide me, as I'm still fairly new to Linux and Ubuntu.

Thanks!

---

