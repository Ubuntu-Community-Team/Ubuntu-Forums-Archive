---
title: "Wanted: HOWTO backuppc"
date: 2005-10-23
forum: Desktop Environments
---

### Post by steveM49 on 2005-10-23
I am fairly new to linux.  I like what I've read about backuppc.  I have been unable to get it working.  The documentation refers to a different file structure than the Synaptic package manager creates.  The dependancies in the package are not complete - it needs a flavor of apache, and perl, and rsync for perl.

When I find an error, I've tried to track it down and correct, but it's too much for me. Could one of the experienced users please develop and post a Howto?

Thanks
Steve

---

### Post by steveM49 on 2005-10-26
bump

---

### Post by camjoo on 2005-11-01
I am also on the hunt for some Backuppc instructions. I went looking for a linux distro just to run Backuppc on a winblows network and chose ubuntu. So far I love it.

As SteveM49 mentioned, I found the install and install instructions to be different. I havn't managed to get Backuppc running yet and I'm unsure of my config.pl settings regarding drive mappings etc. The instructions seem to asume a lot of proir knowledge. I'd love to spend the time learning but I have to get this box running soon.

If someone could run through or explian the config file with/to me or give some pointers that would be fab.

SteveM49 if you are backing up windows boxes then I can give you some advice re rsyncd client for the windows machines.

thanks
cam

---

### Post by iamtaylormade on 2005-11-02
When and if either of you gentlemen discover anything, please drop me a message. I have been tweeking Backuppc for four days now and I am still not sure what I am missing.
I can enter the program via the browser but continue to get the "Unable to connect to the backup server" message.
I have tried re-loading, to no avail. I used SPM to do the install (latest version) and installed perl v5.8.7, perl2html v0.9.2-2, perl-base v5.8.7-5, perl-doc v5.8.7-5, perl-modules v5.8.7-5 and perl-suid v5.8.7-5.
I was curious if this has anything to do with not being able to actually log in as root, considering the documentation continually refers to logging in as such. I added my user name to the "backuppc" user group, nothing.
It looks like a great program but the man was written for those that have a bit more Linux/Unix experience than I.
I hate to admit it, I need a "backuppc for dummies" guide.
Take care.

---

### Post by camjoo on 2005-11-02
[QUOTE=iamtaylormade]When and if either of you gentlemen discover anything, please drop me a message. I have been tweeking Backuppc for four days now and I am still not sure what I am missing.
I can enter the program via the browser but continue to get the "Unable to connect to the backup server" message.
I have tried re-loading, to no avail. I used SPM to do the install (latest version) and installed perl v5.8.7, perl2html v0.9.2-2, perl-base v5.8.7-5, perl-doc v5.8.7-5, perl-modules v5.8.7-5 and perl-suid v5.8.7-5.
I was curious if this has anything to do with not being able to actually log in as root, considering the documentation continually refers to logging in as such. I added my user name to the "backuppc" user group, nothing.
It looks like a great program but the man was written for those that have a bit more Linux/Unix experience than I.
I hate to admit it, I need a "backuppc for dummies" guide.
Take care.[/QUOTE]

Yeah a Windows to Backuppc guide would help a lot of ppl I imagine. If I get this ubuntu box to play ball I think I'll write it all up and slap up a backuppcfordummies.org or something like that. This product seems too good to let slip past for lack of instructions.

---

### Post by kozimodo on 2005-11-02
[QUOTE=iamtaylormade]When and if either of you gentlemen discover anything, please drop me a message. I have been tweeking Backuppc for four days now and I am still not sure what I am missing.
I can enter the program via the browser but continue to get the "Unable to connect to the backup server" message.
I have tried re-loading, to no avail. I used SPM to do the install (latest version) and installed perl v5.8.7, perl2html v0.9.2-2, perl-base v5.8.7-5, perl-doc v5.8.7-5, perl-modules v5.8.7-5 and perl-suid v5.8.7-5.
I was curious if this has anything to do with not being able to actually log in as root, considering the documentation continually refers to logging in as such. I added my user name to the "backuppc" user group, nothing.
It looks like a great program but the man was written for those that have a bit more Linux/Unix experience than I.
I hate to admit it, I need a "backuppc for dummies" guide.
Take care.[/QUOTE]
Have you looked at [http://backuppc.sourceforge.net/faq/ssh.html](http://backuppc.sourceforge.net/faq/ssh.html)?  You need to set up the means for your backup server to connect to the client (linux) machines. This ([http://www.nerdylorrin.net/wiki/Wiki.jsp?page=BackupPC](http://www.nerdylorrin.net/wiki/Wiki.jsp?page=BackupPC)) is useful for configuring it to backup OS X. Can't help with XP. I have it set up to backup 2 linux boxes, OS X and a file server.

---

### Post by iamtaylormade on 2005-11-02
[I][quote=kozimodo]Have you looked at [http://backuppc.sourceforge.net/faq/ssh.html]("http://backuppc.sourceforge.net/faq/ssh.html")?  You need to set up the means for your backup server to connect to the client (linux) machines. This ([http://www.nerdylorrin.net/wiki/Wiki.jsp?page=BackupPC]("http://www.nerdylorrin.net/wiki/Wiki.jsp?page=BackupPC")) is useful for configuring it to backup OS X. Can't help with XP. I have it set up to backup 2 linux boxes, OS X and a file server.[/quote] 
[/I]Thanks Kozimodo, that second site appears to be pretty useful. The sourceforge site however is still lacking. I looked at that same faq site prior to my post. I states that ssh is not required if using rsync, which the perl app is using. I assume that ssh is not required, maybe the assumption is where I am going wrong.
I am going to remove then re-apply the application using the nerdylorrin site's recommendations, there is a part about WinXP as well there.
Thanks again for the post.

---

### Post by wulfy814 on 2005-11-02
Ok folks - I'm running this on several machines - easy install

I've usually compiled it from source rather than use apt - it's all perl anyway.

You will need an apache version (1.x or 2.x)
perl-suidperl

I also compile a few Perl modules that the docs refer to.

I can put together a more complete walkthrough in a couple of days.

On the windows side I install the cywind package and use rsyncd - works great.

Install via apt puts things in the file structure it wants, if you install from source you can customize.

--the wulf

---

### Post by camjoo on 2005-11-02
Thanks for the links kozimodo, the second one is getting me closer, I can feel it :P

and thanks wulf, any help re. a walkthrough would be fantastic. I am going to write a step by step guide for us windows admins. I think I'll start my build again and document the steps. This way I can be easily corrected if I'm doing something wrong- much more reasonable than expecting help from the start driving linux as well.

---

### Post by iamtaylormade on 2005-11-09
[quote=wulfy814]

I can put together a more complete walkthrough in a couple of days.

[/quote] 
Wulfy,
This would be great if you find the time. I would really like to get this product working. I have been beating my head on the KB.
Thanks in advance,

MT

---

### Post by camjoo on 2005-11-09
ok got it running again :)

Im busy as this week so I'm just going to skim through the bits that are missing from the instructions that I thought were the most critical, and maybe that will be enough to get you rolling MT.

Firstly I'm running ubuntu 5.04 on a p4 2.8/512 with average specs. I chose to make backups using rsync and so installed all the extras from cpan as suggested in the manual. 

To install some of the extra modules you need a c/c++ compiler. I chose gcc. I just "apt-get install gcc" from the root terminal and it installed. After doing this, the extra packs the manual reccommends installed without errors.

While installing the packs the install pauses and the program suggests you install extra packs. These were:

apache-doc
apache-ssl
apache-perl
libfile-rsyncp-perl
ssh
exim4
sendmail
par2
ca-certificates
apach-dev
libapache-mod-perl-doc

There may be a typo there (sorry) so be carefull. All these are listed during the install anyway. I'm not sure if they are all needed but my install works so they didn't break it.

I guess that's about all so far- I'm up to "perl config.pl" which isn't working so when I sort that I'll write that up too. Good luck.

cam

---

### Post by Tommy on 2005-12-01
[QUOTE=steveM49]I am fairly new to linux.  I like what I've read about backuppc.  I have been unable to get it working.  The documentation refers to a different file structure than the Synaptic package manager creates.  The dependancies in the package are not complete - it needs a flavor of apache, and perl, and rsync for perl.
[/QUOTE]

Hi, Steve, thanks for writing me directly... I am the one who filed bugzilla bug 11026 [https://bugzilla.ubuntu.com/show_bug.cgi?id=11026](https://bugzilla.ubuntu.com/show_bug.cgi?id=11026) complaining the documentation in backuppc has not been modified to match the Ubuntu (from Debian) packaging.

I see that another poster on this thread has had better luck starting from a non-packaged install. That should be fine, though MY good news is I can say the Ubuntu package DOES work (or at least it did under Ubuntu Warty and probably Hoary, but I don't know whether it would work under Breezy). The bad news is I haven't run it in several months and the machine it's installed on is offline until I get my new office built.

Here's what I remember... The documentation refers to running a configuration script. The Ubuntu package does not require it, as the configuration and backup directories have all been set already. Once I realized that, I pretty readily found the directories, and (because I wanted to back up to somewhere else) I symbolically linked the backup directory to the place where I wanted it.

As for the special thing you install in perl, I did a few Google searches and found the place to download it and I installed it without any trouble. Sorry I don't remember any details but it was ultra simple once I figured out what I needed. I do remember there was no Ubuntu package for it -- I got it from a standard perl archive.

The hardest concept for me to get through was in the backuppc configuration files. There are two sets. (this is all from memory so please correct me if I'm off base) They're all in the /etc/backuppc directory.  There's one big file with a gazillion options in it, sortof like the daunting cupsd.conf file -- but if you examine it awhile you'll notice it just spells out defaults for everything, and after about the first quarter, most of it is sections for the different transport mechanisms backuppc can use. And this is just spelling out the DEFAULTS, not what individual clients will use. Remember that...

In addition to this master configuration file, you can have a separate file for each client you want to back up. I had a lot of trouble figuring this one out... I wanted to use rsync, and it took me awhile to realize how to define the rsync settings in the specific client file. In order to make it work you EITHER have to have a script on the client machine OR you can create ssh keys that let backuppc log in to the client and start the rsync process running all by itself. The ssh key creation proces is totally independent of anything in backuppc, and you learn how to do it from the ssh documentation. Once you have the keys set up and a client file (or a really clever defaults file) set up for your client, backuppc will start polling the clients on the schedule you've defined (the default is once an hour, if I remember correctly).

Backuppc doesn't even LOOK at your clients until you have (a) defined them in the list of clients and/or (b) you have created an individual client file with the appropriate name in /etc/backuppc  -- 

There should be a way to define a "client" that is actually a CD-R or DVD image file, but my old slow machine really bogged down trying to make that work.

SO, don't give up hope... just ignore everything in the documentation about configure.pl and config.pl ... instead of worrying about DEFINING where the files go, look in the Debian-style "logical" place they're already defined in. I want to say everything gets backed up in a directory under /var but I am not absolutely certain. Once you find it, either create a symbolic link to the place you actually want to store it, OR make sure whatever device that part of the filesystem tree is sitting on has LOTS AND LOTS of space on it. For example, if it's under /var/backuppc, you can just symbolically link the /var/bacuppc directory to a directory on a big hard drive.


Here's my overall impression... I was happy with the way Backuppc worked and allowed me to recover files using a web browser, etc. It was nice when it was working smoothly because I didn't have to wonder whether the machines were getting backed up. HOWEVER, if the machines on your network aren't turned on all the time and ESPECIALLY if someone is prone to turn the machine on, check their email and turn it off, backuppc will never finish. Also, I had a 10Mbps portion of my network to accommodate some older equipment, and backuppc bogged totally down on the video and audio files my son was creating on my wife's Mac.

Oh, and that was another issue -- the way files get stored on a Mac is different from the way files get stored under linux, so even though the files were getting copied, there's a little kink in the way rsync works, and (at the time I was working with it) the conversion doesn't work seamlessly between a Mac and a linux box. So for the Mac files I went back to using netatalk, which backuppc doesn't know how to use. (I'm sure it COULD.) I'm not going to go into the details here, but it has to do with how Mac "forks" get defined on a non-hfs file system.

But it worked just GREAT for backing directories on linux boxes. I'm sure it would work fine on PCs too but I don't have any Windows boxes here. (I may reluctantly get one because people keep asking me Windows XP questions. Yuck.)

I hope my little rant helps someone... my new office should be built by mid-December and soon afterward I'll have some room to plug in all my systems again.

---

### Post by reloded on 2007-09-11
Though an oldish thread, I can give my two cents worth of directions:

[http://www.howtoforge.com/linux_backuppc]("http://www.howtoforge.com/linux_backuppc")

I rest my case.

---

### Post by dj1 on 2007-09-14
I have written a quick start [guide ]("http://www.southmainvancouver.com/index.php?search=Backuppc%20Simple%20Configuration")

Also here is the text. Note, if I find documentation errors in my quick start guide, I will fix at my web site, but not necessarily in this forum thread.

Quick start guide

For our shop here at Printcraft Solutions, we use Backuppc to back up critical servers and workstations (but not the Prinergy server as I haven't written a script to enable the backup of Oracle yet).

It's hard to configure because to put it diplomactically, the documentation is not very user friendly. Actually, some of it is downright incorrect, and scattered across the Internet to boot. 

Therefore, I am now writing this Quick Start for Backuppc on Ubuntu (Debian) so at the very least, if I need to reinstall it again, it won't take me 2 days.

Backuppc on Ubuntu

Installation:
Don't use Synaptic Package Manager, instead open up a terminal window and type 

sudo apt-get install backuppc.

This way will ensure that you see the password that is assigned to the backuppc user. 
After installation, you can start, stop or restart backuppc with the following commands:

/etc/init.d/backuppc start 
/etc/init.d/backuppc stop
/etc/init.d/backuppc restart

Open a web browser anywhere in the shop and type in the ip address of the backppc server followed by "/backppc." You should be then be asked for username (backuppc) and then the password (whatever the installation assigned to you).

If you don't get that far, then you probably need to install Apache on your server.

If you don't like the password and you want to change it here how:
htpasswd /etc/backuppc/htpasswd backuppc

One last thing, you now need to go to Synaptic Package Manager and install winbind. Trust me, you need this package so that your Ubuntu server can "ping" the various Windows servers/workstations that you are backing up.

Configuration

Now you need to configure a rather obscure network configuration file:
sudo gedit /etc/nsswitch.conf

And change this line:

hosts: files dns

to:

hosts: files dns wins

Now you should be able to ping various machines in the shop using their Netbios names.

Next, open up the hosts file:

sudo gedit /etc/backuppc/hosts

At the end of the file, you will see examples of how to add workstations and/or servers to the backuppc list. This is where the documentation gets it wrong, and it will cost you a few days to figure it out, unless you listen very carefully to what I say.

**Always set the dhcp flag to 0. Never choose 1. Backuppc has always worked when I set the flag to 0, but never when I set it to one. Just do it.**

Now add the names of your machines to the hosts list and save. Next you will need to open up your config.pl files. I don't use rsynch, even though it is superior to smb, so that's all we are going to cover. If you use rsynch, feel free to ponder your superioriness over a schlob like me. But for now, this Quick start guide uses smb to back up the windows boxes. Note that if want to back up Mac and/or Linux boxes, it's best to configure rysynch which beyond the scope of this document.

Open up the config.pl file:

sudo gedit /etc/backuppc/config.pl

This config file is very long, but mostly because it is very well-commented. You will be looking for the following parameters: $Conf{SmbShareName}, $Conf{SmbShareUserName}, $Conf{SmbSharePasswd}, $Conf{SmbClientPath}, $Conf{SmbClientFullCmd}, $Conf{SmbClientIncrCmd} and $Conf{SmbClientRestoreCmd}.

Whatever username and password you pick, you need to set that username and password on each of the windows machines and make it a member of the backup operator group.

Now, fire up a browser and open up a window to [http://yourserver/backuppc](http://yourserver/backuppc). Start a full backup on any one of the servers you have entered in the hosts file. Enjoy.

Note, if you having problems backing up a Windows XP workstation, see if you can map to the c$ from any other computer on the network using the backup account. If you can't establish any type of network connection, it may be because that install is set to only allow guest access from the network. This happened to me at work, and it took me three (!) to figure out how to connect to the stupid box (not my finest moment as sys admin). 

Got to Control Panel - Administrative Tools 
Go to Local Policies - Security Options 
Check the Network access: Sharing and security model for local accounts 
Set it to Classic - local users authenticate as themselves

---

### Post by Dirk_DC on 2007-10-07
For Edgy or Feisty clients you need to replace --device by -D in the definition of the rsync commands in /etc/backuppc/config.pl, otherwise clients refuse to back up with the "fileListReceive failed" error.

---

### Post by musper on 2007-10-26
Hi,

I've found this guide to be most noob-friendly, and it worked for me. Thanks to it I can now access backuppc web manager, and currently learning how to add and manage jobs for other hosts/clients

[http://ubuntuforums.org/showthread.php?t=553095&highlight=backuppc](http://ubuntuforums.org/showthread.php?t=553095&highlight=backuppc)

---

### Post by robaroooo on 2008-03-02
I have been struggling to understand Backuppc XferLOG, Errors. I have successfully backed up a server, but am getting the following errors on some directories. I am assuming these are active system files and therefore cannot be accessed. I have seen a couple of tutorials that show how to install and config Backuppc, and right there on the screen shot I am seeing the number of XferLOG, Errors (24,000) in one case, but no comments about why or whether to be concerned.

I don't believe this is a "root" permission issue...

...
Remote[1]: rsync: send_files failed to open "/sys/block/fd0/uevent": Permission denied (13)
[ skipped 17 lines ]
Remote[1]: rsync: send_files failed to open "/sys/block/sda/sda1/uevent": Permission denied (13)
[ skipped 5 lines ]
Remote[1]: rsync: send_files failed to open "/sys/block/sda/sda10/uevent": Permission denied (13)
...

Backup Summary

Click on the backup number to browse and restore backup files.
Backup# 	Type 	Filled 	Level 	Start Date 	Duration/mins 	Age/days 	Server Backup Path
0 	full 	yes 	0 	3/1 21:59 	415.0 	0.5 	/var/lib/backuppc/pc/server1/0

Xfer Error Summary

Backup# 	Type 	View 	#Xfer errs 	#bad files 	#bad share 	#tar errs
0 	full 	**XferLOG, Errors 	826** 	0 	0 	0

Thanks for any help!

---

### Post by robaroooo on 2008-03-03
I asked my office Linux IT support and he told me these files run in memory and can't be accessed by BackupPC. He recommended I add the command --one-file-system to RsyncArgs. The incremental that ran tonight worked without any XferErrors! Hope this helps anyone with similar problems.

---

