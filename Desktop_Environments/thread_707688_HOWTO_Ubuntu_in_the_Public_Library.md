---
title: "HOWTO: Ubuntu in the Public Library"
date: 2008-02-25
forum: Desktop Environments
---

### Post by elianthony on 2008-02-25
Hi all,

I work at the Taylor County Public Library in Perry, FL.  We have just added an old Pentium 3 machine, loaded with Ubuntu 7.04, to the 11 other machines running XP that we have here for public internet access, word processing, etc.  I had to be able to justify this linux, non-Windows OS to the county's tech dept. as safe, secure, and stable before I could put it out for public use.  I searched long & hard on these forums for help with the process of securing the desktop, antivirus and so forth.  I got my chance because of an old machine running Windows 98 that the head of IT said we should junk.

I started with a Pentium III @ 500mhz / 256MB Ram / CD-Rom / nVidia graphics card / 13.5GB HDD / Windows 98

The other public access machines are Dell Dimension 2400s with Celeron 2.4Ghz / 256MB Ram / 40GB HDD / Windows XP / MS Office 2003 / Symantec AV

The XP machines were pretty well locked up through group policy, and Deep Freeze (AWESOME), and I had to come close to this level of lockdown for my Ubuntu machine.

I'm still a noob, so hopefully this will help other noobs out there like me....


[COLOR="DarkRed"][CENTER]___________________________________________________________________________________________________[/CENTER][/COLOR]

_**[SIZE="4"]STEP 1[/SIZE]**_

_[SIZE="3"]Install Ubuntu 7.04[/SIZE]_ -- I used the live CD cuz that's all I had, I should have used the *alternate CD*




**_[SIZE="4"]STEP 2[/SIZE]_**

_[SIZE="3"]Create an unprivileged user & log in with that account[/SIZE]_ -- Go to ***System > Administration > Users & Groups > Add***.  Give them permission to use whatever you want, such as floppy drives, modem (only if you're using dial-up), etc.  Now log in as that user, in our case it's user: *public*




_**[SIZE="4"]STEP 3[/SIZE]**_

_[SIZE="3"]Configure the desktop & panels[/SIZE]_ -- I deleted the top panel, and on the bottom panel I have a few applets... quit, weather, dictionary, window list, volume control, & clock.  I also have a drawer with Firefox, Open Office apps, volume control, and a Sys Info app I got from the repositories in case anyone is curious about this new computer.  To configure the panel, **[SIZE="3"][SIZE="2"]right-click[/SIZE][/SIZE]** on it and choose ***Add to Panel***.  On the desktop we have a Firefox launcher and a bunch of links.  And no main menu.  That's it.  Pics to follow.

Here's what the desktop looks like.  It's cluttered with links to all of our online databases, and stuff we have on our website.
[IMG]http://i274.photobucket.com/albums/jj249/libraryeli/Desktop.jpg[/IMG]




_**[SIZE="4"]STEP 4[/SIZE]**_

_[SIZE="3"]Lock down the panels[/SIZE]_ -- 2 ways to do this.  First one, which has a GUI, is Lockdown Editor (pessulus), which is available from the repositroy...* **Applications > Add/Remove > **Lockdown Edito*r.  Once installed, you'll find it in*** System > Administration > Lockdown Editor**.*  Go to the Panels tab and check the box for lockdown.
Second option requires no additional software.  Type ***gconf-editor*** in a terminal.  Go to ***apps > panel > global ***and check the* locked_down* box.  

Both of these options do the same thing...  _***The panels, and the menus cannot be altered in any way.***_

But the menus can still be accessed by pressing ***ALT+F1***, a run dialog box can still be run with ***ALT+F2***, and so on.  To stop that, simply hit*** ALT+F1*** to open a main menu.  Go to ***System > Preferences > Keyboard Shortcuts*** and simply change all of the shortcuts that can cause trouble, or simply disable them.  I have changed them to something odd that I hope noone will figure out.


_**[SIZE="4"]STEP 5[/SIZE]**_

_[SIZE="3"]Lock down the desktop[/SIZE]_ --This is done with permissions & modifying a system file.  Go to ***Places > Home Folder***.  Right click on the *Desktop* folder and go to *Properties*, then to the *Permissions* tab.  Change the *Owner* permission from *Create and Delete Files* to *Access Files*.  Do not remove the user's permission to their own directory... */home/public*.  I did this, and gave the admin account read/write permission to the public's home folder, and the system didn't like it.  It acted strange at every logon, and I had to return to the default permissions.  Only restrict permission to the Desktop.

Here's what they get when they try adding to, or deleting from the desktop...
[IMG]http://i274.photobucket.com/albums/jj249/libraryeli/CreateFolder.jpg[/IMG]
[IMG]http://i274.photobucket.com/albums/jj249/libraryeli/CreateDocument.jpg[/IMG]
[IMG]http://i274.photobucket.com/albums/jj249/libraryeli/CannotDelete.jpg[/IMG]

_[SIZE="3"]Modify the desktop's context (*right-click* menu)[/SIZE]_ -- Open a terminal and ***[SIZE="2"]cd /usr/share/nautilus/ui[/SIZE]***, then [SIZE="2"]```
sudo gedit nautilus-desktop-icon-view-ui.xml
```[/SIZE]  You're going to add a line to this file.  You're going to change the line... 

*<menuitem name="Change Background" action="Change Background"/>* to... 

*<menuitem name="Change Background" action="Change Background" **[SIZE="2"]hidden="true"**[/SIZE]/>*

Adding*** hidden="true"*** to the end of that line removes, or hides, the Change Desktop Background options from the right-click menu.  This same action can be done to the Create Launcher entry in this same file, which is what I did.  However, they can't really do much harm with that one anyway since the launcher would be put on the desktop--which they don't have permission to add anything to anyway.

**_[SIZE="4"]Step 6[/SIZE]_**

**_Installing antivirus(Avast!) & root kit hunting software(rkhunter)_**

I think you have to enable the software repositories in the *sources.list* file.  I'll link to a tutorial for that soon.  To download & install *rkhunter*, open a terminal and...

```
sudo apt-get install rkhunter
```

Type in your administrative password(probably the one you use to login) when prompted.  You may have to answer yes to a couple of questions during installation.  Then run...

```
rkhunter
```

to see your options.




[COLOR="#8b0000"][CENTER]___________________________________________________________________________________________________[/CENTER][/COLOR]

This has been working very well for us so far.  The only thing I've had to deal with have been people moving the icons around on the desktop, and one openoffice.org document saved in the public's home folder.  I hope this will help people looking to do what we've done here.

Total cost for all of this -- **[SIZE="2"][SIZE="4"]$0.00[/SIZE][/SIZE]**

---

### Post by Palmyra on 2008-03-01
Keep us updated.  I would like to know how this experiment goes, and how visitors are reacting to the Ubuntu machine.  How are your supervisors at the library reacting so far?

---

### Post by elianthony on 2008-03-05
Our library director **loves** it.  This is a machine that had been sitting unused for so long that the staff sort of forgot it was even there.  To be able to now put it to use has amazed and impressed her.  She is very excited about doing more of this, especially since it's free and money is always a concern at many libraries.  

The head of our county's IT department was skeptical at first, being strictly a Windows / Dell man.  But now I think he's shifting.  If this machine works well for awhile without a serious hitch, he's going to let me put together more Ubuntu machines in the future which will save the county LOTS of money.  Because of how the county is set-up here, I must get approval from both the library director, and the IT dept.

I'm now working on a proposal for Edubuntu in our children's room.  We currently have 5 Gates grant Dell's with Pentium D's and 1GB Ram & a bunch of educational games.  These things are great when they're not crashing, which is all the time.  Going to pitch a thin client setup using some more of our old machines.

---

### Post by ubuntu27 on 2008-03-05
Hey that's great what you're doing. :) 

Why are you going to install Antivirus? GNU/Linux doesn't need one. The antivirus available for linux is for scanning Windows Viruses (useful in a linux servers that connects to WIndows clients)


What kind of software is installed in the WIndows computers? You should check out what you can use in Ubuntu Linux.

---

### Post by elianthony on 2008-03-06
Thanks!!

> **ubuntu27 said:**
> Why are you going to install Antivirus? GNU/Linux doesn't need one. The antivirus available for linux is for scanning Windows Viruses (useful in a linux servers that connects to WIndows clients)

Well, let me explain.  These are the library's computers, but we are part of the county.  That means that administration of every machine here is the responsibility of the county's IT dept., not us.  We can do whatever we want, with their approval.  It's the head of that dept., one of my three supervisor's BTW, that required me to find, install, & test antivirus software.  He wouldn't even consider putting this machine on the county network without it.  He is **very security minded**.  I ended up going with **avast!**, and it met his approval.

---

### Post by ubuntu27 on 2008-03-06
> **elianthony said:**
> Thanks!!



Well, let me explain.  These are the library's computers, but we are part of the county.  That means that administration of every machine here is the responsibility of the county's IT dept., not us.  We can do whatever we want, with their approval.  It's the head of that dept., one of my three supervisor's BTW, that required me to find, install, & test antivirus software.  He wouldn't even consider putting this machine on the county network without it.  He is **very security minded**.  I ended up going with **avast!**, and it met his approval.

Fair enough. :)

---

### Post by jfinkels on 2008-03-06
> **elianthony said:**
> 
[snip]
He is **very security minded**.
[/snip]

Very WINDOWS security minded. Make him realize where the problem lies!

Keep up the good work, and congratulations!

---

### Post by ubuntu27 on 2008-03-06
> **jfinkels said:**
> Very WINDOWS security minded. Make him realize where the problem lies!

Keep up the good work, and congratulations!

True enough. Here are some links about WIndows and UBuntu security.

[Ubuntu Security ]("http://ubuntuforums.org/showthread.php?t=694198") ([WIndows Mindset VS Ubuntu GNU/Linux Mindset]("http://ubuntuforums.org/showthread.php?t=694198"))

[Are Firewall and Antivirus necessary in Linux?]("http://ubuntuforums.org/showthread.php?t=131616")

---

### Post by punong_bisyonaryo on 2008-03-07
Thanks for the really great tutorial. I'm thinking about using this info to set up some comouters open to public (not library). As in really public, just so users can be introduced to Linux.

---

### Post by mozetti on 2008-03-07
The reason anti-virus is a good idea:

1) It will clean up any viruses people introduce to the network when accessing webmail and sites. Chances are low that it could get out into the wild of the network, but why risk it?

2) If USB memory sticks are allowed to be used on the machine, it's very feasible that a user could go from the Ubuntu machine at one sitting, and then move to one of the XP machines at the next sitting -- kill viruses whenever and wherever you can.

Also, a note about locking down launchers -- you might want to do that in case someone who's familiar with linux uses the machine and wants to be naughty. Or, maybe a tech-minded person decides to find out about Ubuntu while using the machine, ends up here, and finds out how to make some trouble. IMO, lock it down.

Finally, great for you! This is a great idea, especially the Edubuntu -- maybe you can talk the IT department into doing dual-boots on the Gates grant Dells to open up more software for the kids?

---

### Post by elianthony on 2008-03-07
> **mozetti said:**
> The reason anti-virus is a good idea:

1) It will clean up any viruses people introduce to the network when accessing webmail and sites. Chances are low that it could get out into the wild of the network, but why risk it?

2) If USB memory sticks are allowed to be used on the machine, it's very feasible that a user could go from the Ubuntu machine at one sitting, and then move to one of the XP machines at the next sitting -- kill viruses whenever and wherever you can.

I agree about anti-virus being a good idea for exactly those reasons.


> **mozetti said:**
> Also, a note about locking down launchers -- you might want to do that in case someone who's familiar with linux uses the machine and wants to be naughty. Or, maybe a tech-minded person decides to find out about Ubuntu while using the machine, ends up here, and finds out how to make some trouble. IMO, lock it down.

I agree here too, and that's why I removed this option from the context menu, sorry I didn't include that in my initial write up, but it's there now.  However, I tried to create a launcher on the machine after I restricted permissions to the desktop but before I removed the Create Launcher option from the context menu and it wouldn't let me complete the process.  I would think this would be good enough, but removing it from the menu altogether put my mind at rest completely.

---

### Post by Pap3r on 2008-03-07
This is a very good idea, as well as a well made tutorial.  I'm 17, and have been talking to the IT guys at my school for a few months about moving some of the (hundreds) of computers into the linux environment.  Once the machines are set up properly, they would be solid.  However, the IT guys are disregarding my proposals, insisting that since linux has no support "phone-line" or anything like that, if they get lost, or brick a machine, they will have no idea what to do.  They like using windows because 
a) They are fairly proficient with it 
b) My city is based on a Windows network, I don't think there is a single non-windows machine on it
c) They think that once they are caught dead-in-the-water, they are screwed without Tech support.

I have tried to convince them with the common arguments: free, more secure, no viruses etc, but I can't get through to them.  Has anyone else had any experience in this area?  I figure if I could just install it on an old machine, like you did in the library, they would warm up.  We have a bunch of old computers all over the place, most of them not even used.  They could be reborn machines :)

---

### Post by elianthony on 2008-03-07
Thanks a lot.

> **Pap3r said:**
> However, the IT guys are disregarding my proposals, insisting that since linux has no support "phone-line" or anything like that, if they get lost, or brick a machine, they will have no idea what to do.  They like using windows because 

Canonical does have [phone support]("http://www.ubuntu.com/support/paid") for Ubuntu actually.

Also, they might be interested in seeing other [schools]("http://www.ubuntu.com/products/casestudies") that have adopted Ubuntu, or even whole countries...like [Macedonia]("http://www.news.com/8301-13580_3-9819344-39.html")

---

### Post by Pap3r on 2008-03-11
> **elianthony said:**
> Thanks a lot.



Canonical does have [phone support]("http://www.ubuntu.com/support/paid") for Ubuntu actually.

Also, they might be interested in seeing other [schools]("http://www.ubuntu.com/products/casestudies") that have adopted Ubuntu, or even whole countries...like [Macedonia]("http://www.news.com/8301-13580_3-9819344-39.html")

Awesome!  I'll be sure to show them this.  That's really funny actually... whole countries.. :)

---

### Post by elianthony on 2008-03-17
_**UPDATE**_

Edubuntu has received an OK from IT.  Now to just find the time to install, and deploy it in the children's room.  I'll let you know how it goes.

---

### Post by Pap3r on 2008-03-18
> **elianthony said:**
> _**UPDATE**_

Edubuntu has received an OK from IT.  Now to just find the time to install, and deploy it in the children's room.  I'll let you know how it goes.

I also have just received the okay to ressurect some old machines form the basement.  Should be a good time :)

---

### Post by ubuntu27 on 2008-03-19
> **elianthony said:**
> _**UPDATE**_

Edubuntu has received an OK from IT.  Now to just find the time to install, and deploy it in the children's room.  I'll let you know how it goes.

Good news! Please keep us updated :) 

Good job mate! :)

---

### Post by elianthony on 2008-03-19
Edubuntu update:

I've installed Edubuntu 7.10 onto an old 1.8ghz P4 Dell Dimension 2350 for use in the children's room here at the library.  I've installed tons of extra games & educational software that looked appealing.  Now, I just have to test each one to make sure that it's not only cool, but pretty stable, and of course, educational in some way.  I reckon the machine will be put out for public use next week.

On another interesting note, we have just received a book for circulation... [Ubuntu 7.10 Linux UNLEASHED]("http://www.amazon.com/Ubuntu-7-10-Linux-Unleashed-3rd/dp/0672329697/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1205966758&sr=8-1") by Andrew & Paul Hudson.  I haven't had a chance to really look at it, but it seems to be pretty comprehensive.

---

### Post by mjwhitfield on 2008-04-02
This is great, I'm so glad it's working out for you :)

Also, the little howto at the start will be very handy for me!

---

### Post by elianthony on 2008-04-02
Well, the machine is out for public usein the children's room. ** I switched from Edubuntu 7.10 to Ubuntu 7.04**, for a few reasons.  I felt that the older version might run a little quicker, and I want Ubuntu to have every advantage it can against the newer XP machines.  Also, this is just a stand alone machine, so I didn't need any of Edubuntu's extra features, like LTSP.  I installed all the same packages as on Edubuntu, and a lot more.  So I kinda made a hybrid of the 2 I guess.

BTW, I used the same lockdown steps as I detailed in the beginning of this thread for this machine, except for the anti-virus, since this machine won't see the internet.

The machine's been out for 3 days now with impressive results.  I've been weeding out the apps that cause the system to hang, like Tux Paint when run from inside GCompris.  (However it doesn't have that problem when I run it directly.)  I've also found a few other problems inside GCompris that have caused hanging, and required a CTRL-ALT-BKSPCE.  You must understand that our children's computers get ABUSED all day long.  The XP machines need attention at least 4-6 times a day, and when we're busy, they'll need a restart at least once a day.  Ubuntu however, hasn't had this problem, especially since I've been weeding out the problem apps.

I've told in a previous post the specs of this children's Ubuntu machine.  It's Windows counterparts are Pentium D 3.4Ghz / 1GB Ram / Dell Optiplex 745 machines.  

So far, Ubuntu has seen more "uptime" than they have.

---

### Post by elianthony on 2008-04-16
Well, a few weeks going now, and I'm happy to report that the Ubuntu machine in our children's area is still going strong.  It has taken it's hits, and even physical abuse to the machine itself from the kids.  However, it is still proving to be our most reliable machine in there.

On another front, I have just loaded another machine with Ubuntu 7.04 for use at our circulation desk.  This machine is used for checking books in and out using our new open-source library software, [Koha]("http://www.koha.org/").  Ubuntu was chosen for a few reasons, including security, since this machine is going to be hooked up directly to our cable modem, and not passing through our WatchGaurd Firebox.  

I'll expand on this later, but here's a quote from our IT director who once laughed away the idea of linux... **"I'd prefer to support a linux machine that's out on the internet by itself, rather than trying to support a Windows machine out there unprotected."**

Now I get to use Ubuntu everyday at work, nice.

---

### Post by ubuntu27 on 2008-04-17
Each time I read this thread I am surprised and happy to see that GNU/Linux is spreading across the globe even in Libraries.

Where was your library located again? People should visit it :)

---

### Post by Triggerhapp on 2008-04-17
> **elianthony said:**
> Now I get to use Ubuntu everyday at work, nice.
That would be heaven to me. XD

Good work and everything, its impressive to see how much sway you've had on your place.

---

### Post by elianthony on 2008-04-21
Thanks! I figure I'll give a total of what we've got in the way of Ubuntu here at the library... 3 machines running Ubuntu so far:

**1** - public access / internet computer with Ubuntu 7.04, it's 1 of 12 public access machines here, the rest being XP machines.  It's a Pentium 3 500mhz / 256MB Ram / 13.5 GB HDD.

**1** - children's computer, not online w/ Ubuntu 7.04 and a whole bunch of educational games, loaded on a Dell 2350 w/ P4 1.8Ghz / 512MB Ram

**1** - circulation desk computer that runs our open-source library software, [Koha]("http://www.koha.org").  It's on a Dell 2350 w/ P4 1.8Ghz / 768MB Ram.  This machines owns the other circulation desk machine that's running on XP.

Coming soon...

Our 2 search (OPAC) computers will be refitted/replaced.  One is a Dell Dimension 2400 running XP, it's getting reloaded with Ubuntu, or Xubuntu.  The other is so old, it has only 32mb Ram, and it's running NT.  It's getting replaced by another old Dell Dimension 2400 that'll get loaded with Ubuntu, or Xubuntu, haven't decided yet.  I'll probably stick with Ubuntu seeing how much our IT director loves standardization.

So, that's the state of GNU/Linux affairs here at the Taylor County Public Library in Perry, FL.  [Perry]("http://maps.google.com/maps?client=opera&rls=en&q=perry,+fl&sourceid=opera&ie=UTF-8&oe=utf-8&um=1&sa=N&tab=wl") is about an hour SE of Tallahassee in North Florida.  Please, anyone who wants to visit is welcome.

---

### Post by elianthony on 2008-05-06
Well, we've **added 2 more Ubuntu machines**. Our 2 OPAC computers that our patrons use to search our catalog for books are now Ubuntu 8.04 machines!  They're both configured the same way as I layout in the beginning of this thread, with a couple of differences due to their specialized use.  These 2 machines only need to view our online catalog, which is hosted remotely, and accessed over the internet.  So, we use Opera, locked down to view only our site.

One is a Dell Dimension 2350 with a P4 1.8 Ghz / 256 RAM / 40GB HDD / On-board video & sound.

The second one is identical except for having a 2.4 Ghz Celeron processor.

I'll fill in on details later, it's busy here at the circulation desk after school.

---

### Post by mjwhitfield on 2008-05-19
How speedy are you finding 8.04 on 256mb?

---

### Post by elianthony on 2008-05-19
> **mjwhitfield said:**
> How speedy are you finding 8.04 on 256mb?

It's noticeably slow when opening an app.  However, once it's open things run pretty decent.  Take Opera for example... it takes a few seconds for it to open, but once it does it runs just fine.  I must say that I haven't used it much on the machines with only 256MB so I can't really talk much about it's performance.  The machine I mainly use has a P4 1.8, w/ 768mb RAM running Xubuntu 8.04 and it's pretty snappy.

---

### Post by elianthony on 2008-05-20
I just replaced Nautilus with [PCMan File Manager]("http://www.ubuntugeek.com/how-to-replace-nautilus-with-pcman-file-manager-in-ubuntu.html") for my file manager on the 2 Ubuntu 8.04 OPAC machines.  This won't make any real difference to the public, but it has made things quicker for me if and when I bop around in the system graphically.  I figure I'm going to keep these 2 machines going as long as I possibly can without any upgrades to their hardware.

---

### Post by pnthrpride on 2008-05-21
Thank you elianthony for informing us about your experiment.
I also work in a public library and interested in installing UBUNTU here for the public.
I would like to know if you use PCRES for reservation and LPTONE for public printing? and how did they like Linux

---

### Post by elianthony on 2008-05-22
Well, pnthrpride, we don't use anything for public printing or for reservation.  The one Ubuntu machine that's out for public internet access isn't hooked to a printer.  Aside from the problems associated with a 500mhz processor, people love it.  They do however always want to be switched off of it when it gets slow.

I hope it goes well for you with putting Ubuntu out for public use in your library.  It has really saved us some headaches, not to mention some money.

---

