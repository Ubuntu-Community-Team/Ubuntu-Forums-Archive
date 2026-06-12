---
title: "New forum?"
date: 2006-11-07
forum: Forum Feedback &amp; Help
---

### Post by podunk on 2006-11-07
When you consider that the growth of the personal computer was driven by corporate useage rather than hobbyist adoption, wouldn't it make sense for us to have a forum dedicated to the business user? 

A place to resolve and discuss and share productivity and information management rather than the software and hardware issues the rest of the forums are dedicated to.

For instance I discovered Kontact this weekend. Any lingering hesitation I had about migrating to Linux has vanished. Koffice looks very promising also.

I think such a forum would benefit not only our community but be of direct benefit to our benevolent parent Canonical.

---

### Post by podunk on 2006-11-09
never mind! I understand now why no one commented on this, Ubuntu is no where near stable enough to be used in a production enviorment.

It looks cool, it's fun and I really like Kubuntu and will keep it to play and learn with on my home machine, but i think I'll try red hat for the business.

---

### Post by PriceChild on 2006-11-09
Hi there.

Please be patient :)

You may have heard the UDSmtv is taking place atm and that most if not ALL of the forums staff are involved in some way in discussions, leaving many, less time to frequent the forums this week.

Most of the admins are out of the UK timezone and will be asleep right now.

Just be patient and I'm sure you'll receive an answer from someone with more power/experience than me :)

You aren't being ignored :)

---

### Post by Najand on 2006-11-09
Well... Hmm, sounds a great idea to me... I think Ubuntu is stable enough to be used as a business and production envirnment. I am not aware of companies in the states or Europe or other parts of the world, but in Japan, many famous companies like Sony/Matsushita/Toshiba/... are using linux for produtcion and I am sure if many of them are very interested in an stable systme like ubuntu.

---

### Post by podunk on 2006-11-09
I'm not being impatient - I was jumping the gun on my first post. Since that post I lost all 3 of my work machines (Mine, my secretary's and the test bed).

1 was my "fault" I was optimizing it. I wasn't worried because I thought I had a good back up. It turns out if you put your backup in / before you restore it it get's overwritten and becomes a zero byte file.

2 of the machines were broken by official security/bug updates. Fortunately the backups for these were stored on a portable USB drive so I was able to recover them. One of them had my secretary's work on it, and I can't afford to have her fire me or anything like that. We've converted all the word processing files to Word friendly formats so she can redo them and save them there. I'll play hell getting her to try Linux again.

This is for sure the second time in 5 months I've lost a machine due to a patch/upgrade that came in through the update manager. The other time might have been my fault, but then again, it might not have.

I do know that anytime an update to the kernel or the kernel header thingies happens ATI cards lose 3D ability and it slows your machine to a crawl. As far as I can tell there is no graceful way to recover from this. You do a new install, install all the updates, *then* use various methods to install radeon/flgrx drivers.

ATI has about 30% of the market I seem to recall, it's a very popular video solution for work machines.

In a work environment you can't devote that amount of time and energy in an endless set up, especially for something that bills itself as being stable and offering long term support.

Does Canonical's commercial support supply tested updates rather than the untested ones released by the community here? If so it *might* be worth the price.

In any case I'm going to give Red Hat a try, they have a server solution for just 400.00.

I'll keep Kubuntu on my machine because i like it. :-) I can afford to lose it every couple of months. The only work I do around here is sign the checks and take customers out to dinner.  When mine crashes and burns it's no big deal.

---

### Post by PriceChild on 2006-11-09
> **podunk said:**
>  Does Canonical's commercial support supply tested updates rather than the untested ones released by the community here? If so it *might* be worth the price.You may be experiencing breakages due to unofficial repositories being added. You're the only one complaining about updates which you say are coming from the official security repository.> In any case I'm going to give Red Hat a try, they have a server solution for just 400.00.If you've got the money to spare then go for it! Whatever works for you, Linux is about choice.> I'll keep Kubuntu on my machine because i like it. :-) I can afford to lose it every couple of months. The only work I do around here is sign the checks and take customers out to dinner.  When mine crashes and burns it's no big deal.Glad to hear you're sticking with us slightly :)

---

### Post by Najand on 2006-11-09
What security update was that? Was it a main/restricted/universe/multiverse package?

---

### Post by frodon on 2006-11-09
> **Najand said:**
> Well... Hmm, sounds a great idea to me... I think Ubuntu is stable enough to be used as a business and production envirnment. I am not aware of companies in the states or Europe or other parts of the world, but in Japan, many famous companies like Sony/Matsushita/Toshiba/... are using linux for produtcion and I am sure if many of them are very interested in an stable systme like ubuntu.You know, all the semi-conductor companies use linux for the design, the test and production of all microcontrollers, processors, ...
And before that they used unix so there's already a whole sector using linux. However the only linux version used is red hat enterprise but ubuntu has good chances to replace red hat in the near future if it continue to grow.
What is missing are some companies to sell ubuntu support to these companies.

---

### Post by podunk on 2006-11-09
The security update (really a fix for a previous update apparently) was this one:
[http://ubuntuforums.org/showthread.php?t=294499](http://ubuntuforums.org/showthread.php?t=294499)

I “turned on” all the repositories that shipped with Ubuntu for those 2 machines. The only software came from those repositories. As far as I know you can't enable 3D with ATI cards unless you enable them all. I'm going to format and set up the test machine, I'll report afterwards.

It turns out that Red Hat was a little pricier than I thought, I read their web page wrong. Novel is better by some. In the short run Microsoft is by far the most affordable for a business my size. Of course, the next step up is quite a jump. Plus XP and my version of Office will be at the end of their support cycle before long. Which means Vista, and the endless upgrade. New Office version, new computers to take advantage of all the features (bloat) no one uses.

I like Kubuntu. It's look and feel. I understand now you can install KDE on any system, but still.

Ubuntu's server support pricing is ***very*** attractive. Has anyone here had any experience with it?

---

### Post by podunk on 2006-11-10
Well. 2 computers with everything, and I do mean everything set up in 3 hours flat.

ATI on old cards works out of the box now!:-) What ever it was they fixed fixed everything. I forgive them for breaking my computer. glxgears is about 100 fps slower than before - who cares?

I found a quick and dirty point and click way to set up Samba! 10 minutes flat.

My secretary and I both turned on our computers about the same time. Mine was playing the radio while hers was loading Zone Alarm. Several exasperated sighs as she waited for stuff to load. I give it a week before she's ready to try Kubuntu again.

podunks quick and dirty Samba:

Found an easy way to do Samba! Entirely by accident. Why installing NFS makes Samba so easy to set I don't have a clue.

In Kubuntu:
Kmenu>System>Adept Package manager and add the following files:
libnfsidmap
nfs-common
nfs-use-server
samba
samba-common
smbc
Click &#8220;Apply changes" Close the manager.

Kmenu>System Settings>Network Settings. Enter Administrative mode (note you will have to enter Administrative mode each time you change screens)
Network Interfaces tab
Click the Manual spot button. Enter IP address and Netmask (on my box 192.168.1.97  255.255.255.0)
Click &#8220;Advanced&#8221; and enter Broadcast and Gateway (192.168.1.254 for both on my computer &#8211; it will depend on your router settings)
****Click Automatic after making the changes and make sure DHCP shows**** Click OK
Click the Routes tab and make sure the Default Gateway address from previous instruction is there.
Click the Domain Names System tab.
In Host name enter your log in name
Enter Mshome in Domain name (you can edit smb.conf all damn day long and it won't change this, so go with the flow here)
Under Static Hosts click Add then enter the IP address of the other computer. Click the Add button and enter the log in name  of the other computer. Click OK. Repeat for other computers on the network. Click "Apply"
Click &#8220;Show all&#8221; in the upper left corner
Click  Sharing, tick &#8220;Simple sharing.&#8221;
Click Add.  Next to the Folder field is a browse icon, click it and browse to the folder you wish to share.  You can share any folder in /home. Click the folder then OK
Click Share with NFS.  Click Public  (and writable if you trust the user of the other machines.) 
Click &#8220;More NFS Options&#8221; and enter the IP of  the other computer.  Click &#8220;Writable and &#8220;No hide&#8221; if you trust the other computer. Click OK.
Click Share with Samba. Click &#8220;More Samba Options&#8221; and click stuff that seems appropriate to the other computer (depending on how much trust it) **Do not play with the advanced setting unless you know what you're doing***and if you've read this far you likely don't :-) Click OK
Restart the computer

In Ubuntuu.
System>Administration>Synaptic Package Manager; install the following files:
libnfsidmap
nfs-common
nfs-use-server
samba
samba-common
smbc
Click &#8220;Apply changes&#8221;
Close the package manager

System>Administration>Networking
Click &#8220;Ethernet Connection>Properties
Change &#8220;DHCP&#8221; to &#8220;Static IP Address&#8221; (for me 192.168.1.98, 255.255.255.0, 192.168.254 this last number will be the IP of your router)***Do not change back to DHCP!*** 
Click the &#8220;General&#8221; tab and make sure your log in name is entered. For &#8220;Domain name&#8221; enter Mshome
Click &#8220;DNS&#8221; and enter your routers IP
**Important: Click &#8220;Hosts&#8221; Click &#8220;Add&#8221; Enter the &#8220;IP Address&#8221; of the other machine. Click in &#8220;Aliases&#8221; and enter the user name of the other machine. Click OK
Repeat for all machines on the network
Click OK, Network manager will close
Open Nautilus Places>Home Folder
You can share any folder in /home
Right click and chose &#8220;Share Folder&#8221; chose &#8220;SMB&#8221;
Enter a share name (I just use the name of the folder here) Add a comment. Click &#8220;Allow browsing folder&#8221; If you don't trust the rest of the network click &#8220;Read only&#8221;
Click &#8220;General Windows sharing settings&#8221; then chose &#8220;This computer is a WINS computer&#8221; Click OK
Restart the computer

Browsing the network.

In Ubuntu Places>Network Servers &#8211; this will open then at the top will be &#8220;Service type&#8221; Click it and then click &#8220;Windows share&#8221; Enter the IP of the other machine then a &#8220;Share Name (I used the name of the other person) then click OK. This will put a folder for that network connection on your desktop and under Places on the task bar. :-)

In Kubuntu 3 ways
Open Konqueror. Type in 
smb://IP_of_other_computer
Bookmark this when it opens

Next to Kmenu is System Menu. Click &#8220;Remote places&#8221;
Click Samba Shares
Click Mshome
You'll see every other computer on the network 

Open Konqueror
Click Network Folders
Click Samba Shares
Click Mshome
Click the name of the other computer

Once you've connected to a machine the first time you can create a shortcut to it on the desktop.
Right click an open area of the desktop
Chose &#8220;Create new&#8221; then &#8220;Link to location (URL)
Enter smb://IP_address_of_other_computer. Enter the name of the machine you want
Click OK 
This puts an icon for the share on the desktop . You can drag this to the system area of your task bar for easy access.

---

### Post by bonzodog on 2006-11-11
I think you are finding something out about linux - it's a different way of doing things that sometimes requires another way of thinking about the problem. 
If you are using edgy, that might be why you got broken updates. In devel releases this often happens.

---

