---
title: "Newbie Questions Ist Try. Random Questions"
date: 2010-04-22
forum: Desktop Environments
---

### Post by anon_private on 2010-04-22
Hi,
 
Random questions after 1st tryout.
 
I have just tried UBUNTU - not installed.
 
Since I have not unstalled UBUNTU can I click the 'Restricted Drivers Available' box. If so what extra features will I have?
 
According to the Help, the Network Manager is a yellow star. I see a little grey icon next to padlock (Restricted Drivers)!
 
When I connected to Wireless, I was asked for a password for the default key. What is the usual nomenclature for this password? Can it be used if I am just trying out UBUNTU? I don't really get the key bit!
 
Can I save files, etc if UBUNTU is not installed?
 
Is it possible to see my VISTA directories, files, and programmes and use them under UBUNTU? I'll need to change directories to c:
 
If VISTA became infected could I clean the hard drive, C, from within UBUNTU? Could I run my anti-virus programmes from UBUNTU?
 
Is it better to do on-line banking from within UBUNTU using Firefox, rather that IE under VISTA? How safe would it be?
 
Thanks
 
A

---

### Post by micio on 2010-04-22
> **anon_private said:**
> Hi,
 
Random questions after 1st tryout.
 
I have just tried UBUNTU - not installed.
 
[B]Since I have not unstalled UBUNTU can I click the 'Restricted Drivers Available' box. If so what extra features will I have?
[/B]

Usually this function will install/activate a new kernel module, so you need to reboot in order to get this feature working fine.. you can't do it in live mode (in live mode, every change is stored in RAM)
 
According to the Help, the Network Manager is a yellow star. I see a little grey icon next to padlock (Restricted Drivers)!
 
**When I connected to Wireless, I was asked for a password for the default key. What is the usual nomenclature for this password? Can it be used if I am just trying out UBUNTU? I don't really get the key bit!**

Are you talking abount WEP/WPA wifi key?
 
**Can I save files, etc if UBUNTU is not installed?**

Yes, but not on desktop :) you must mount an hdd and then save the files there.
 
**Is it possible to see my VISTA directories, files, and programmes and use them under UBUNTU? I'll need to change directories to c:**
You can see your files and folders at all but you can't run your applications under linux. 
 
**If VISTA became infected could I clean the hard drive, C, from within UBUNTU? Could I run my anti-virus programmes from UBUNTU?**
You don't need it :) Virus can't affect ubuntu! (not windows virus)
 
**Is it better to do on-line banking from within UBUNTU using Firefox, rather that IE under VISTA? How safe would it be?**

I guess.. however be carefully about firefox extensions (both on Linux and Vista)
 
Thanks
 
A

Please note the answer on quote :P

---

### Post by lovinglinux on 2010-04-22
> **micio said:**
> Please note the answer on quote :P

Please do not reply inside the quotes. It is confusing and makes harder for others to quote you.

> **micio said:**
> Is it better to do on-line banking from within UBUNTU using Firefox, rather that IE under VISTA? How safe would it be?

I guess.. however be carefully about firefox extensions (both on Linux and Vista)

Definitely safer, although any browser has security issues. So keep your system and Firefox always updated and be careful with [phishing](http://en.wikipedia.org/wiki/phishing) [wikipedia.org]. Additionally, see [these Firefox extensions for Security and Privacy](https://addons.mozilla.org/en-US/firefox/collection/securityandprivacy).

In regard to extensions, you should avoid those that are [not hosted](http://ubuntuforums.org/attachment.php?attachmentid=152988&d=1271027640) by [Mozilla Add-ons](https://addons.mozilla.org/en-US/firefox/) site and the [Experimental](http://ubuntuforums.org/attachment.php?attachmentid=152987&d=1271027640) ones. Extensions that are hosted by Mozilla and does not have a experimental status are ALL reviewed by a Mozilla editor before going public and thus pretty much safe to use. Nevertheless, some extensions have additional privacy policies, because they might collect information about your system and browsing habits.

BTW, I use [52 extensions](https://addons.mozilla.org/en-US/firefox/collection/lovinglinux).

---

### Post by anon_private on 2010-04-22
Thanks for responding.
 
I was asking about antivirus because it occured to me that if I picked up a Windows virus that I could not remove then I might be able to use UBUNTU to gain access and clean up the c drive. Is this not possible?
 
I get the impression that I cannot save or use files to/in my Windows directories from UBUTU. Hence, I need to decide in advance which OS to use for any particular job - assuming I decide to keep both.
 
Thanks for the link to the browser extesnsion site. Do you recommend any particular extensions for those who conduct Internet banking. I am assuming that I can connect to a bank using Firefox (not tried as yet). Can the extensions be sucessfully installed if UBUNTU is not installed? I am wondering if anything can be save to UBUNTU if it is not installed (UBUNTU on CD-R).
 
Regarding the key, yes I was referring to the WPA wifi key.
 
Best wishes.
 
A
 
Ps. It does seem that some people use both OS's because there is an option to have both installed on a pc.

---

### Post by lovinglinux on 2010-04-22
> **anon_private said:**
> I was asking about antivirus because it occured to me that if I picked up a Windows virus that I could not remove then I might be able to use UBUNTU to gain access and clean up the c drive. Is this not possible?

It is possible and common to do that.

> **anon_private said:**
> I get the impression that I cannot save or use files to/in my Windows directories from UBUTU. 

In fact you can. What you cannot is read a Linux file system (ext3, ext4...) from Windows without additional software.

> **anon_private said:**
> I am assuming that I can connect to a bank using Firefox (not tried as yet). 

Not necessarily. Some banks are stupid enough to provide compatibility only for IE. If this is the case, then try to use [User Agent Switcher](https://addons.mozilla.org/en-US/firefox/addon/59).

> **anon_private said:**
> Can the extensions be sucessfully installed if UBUNTU is not installed? I am wondering if anything can be save to UBUNTU if it is not installed (UBUNTU on CD-R).

Yes, you can install software and Firefox extensions with an Ubuntu LiveCD. In fact, using Ubuntu CD to do Internet Banking is [a new trend in security recommendations](http://blogs.computerworld.com/15815/can_ubuntu_save_online_banking). Nevertheless, once you reboot, the changes will be lost. There is a way to make these changes permanent, but I'm not sure how and that would be less safer. Anyway, if you are doing your Internet Banking using a LIve CD and go only and directly to your bank site then yo don't need those security extensions.

> **anon_private said:**
> Ps. It does seem that some people use both OS's because there is an option to have both installed on a pc.

Yes, it's called dual-boot. Nevertheless, there is an easier way using Wub[i. See this](http://www.psychocats.net/ubuntu/wubi).

---

### Post by anon_private on 2010-04-23
Thanks for the responses.

Is there a good tutorial that covers the questions I have raised.

Thanks

---

### Post by anon_private on 2010-04-23
I noted that I could see the OS directories that I can see in VISTA, but I could not find my music directory and files etc.
 
Will these be available to me under UBUNTU. If not, is there a solution?
 
Thanks

---

### Post by lovinglinux on 2010-04-23
> **anon_private said:**
> I noted that I could see the OS directories that I can see in VISTA, but I could not find my music directory and files etc.
 
Will these be available to me under UBUNTU. If not, is there a solution?
 
Thanks

I'm not sure how Vista handles permissions, but perhaps you need to put the files on a shared folder or set the current ones to be shared.

---

### Post by anon_private on 2010-04-23
Thanks for responding.

I don't like the font that I am using.

Can it be changed to say and Ariel style font. Point change would also be nice.

Can the mouse buttons be swapped?

Thanks

A

---

### Post by anon_private on 2010-04-23
Is there s firewall in UBUNTU
 
Thanks

---

### Post by lovinglinux on 2010-04-23
> **anon_private said:**
> Is there s firewall in UBUNTU
 
Thanks

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by anon_private on 2010-04-24
What an excellent link.

I tried to pint a document using the word processing programme, but could not configure my printer. It is a USB printer connected to a single machine.

Please can you advise.

I note that my left hand mouse configuration disappeared on booting.

I expect the printer config will do likewise, but I would like to be able to print when using the LiveCD.

Thanks

A

---

### Post by ugm6hr on 2010-04-24
Yes - any settings made on the LiveCD will not be saved.

It is possible to create a "persistent" LiveUSB - try searching for this in Google for examples of how.  It allows you to use a LiveCD from a USB, but save settings to the USB for them to remain after rebooting.

Not all printers can be used in Ubuntu - some do not have the necessary driver software to make them work.

---

### Post by joeoshawa on 2010-04-24
> **anon_private said:**
> I noted that I could see the OS directories that I can see in VISTA, but I could not find my music directory and files etc.
 
Will these be available to me under UBUNTU. If not, is there a solution?
 
Thanks
I am a newbie myself now i had some problems seeing my music files because users have paswords and i needed to get some files off windows (7 so may be a little different) so i put them in the public user directories and got them and even still use them from there.

Windows 7 is broken and will not access the internet. it keeps telling me it is my router or modem but all is well in ubuntu (imagine that) so i am currently trying to switch to linux completely and have my 1tb drive all ubuntu now all i need is for coreboot to support my board and i will have a totally non proprietary machine.

---

### Post by anon_private on 2010-04-24
Hi, 

When I triied to playing an mp3 file stored in a Windows directory it would not play without a plugin. What files does Rythmbox support?

When I clicked on an mp3, Movie Player opened - How odd!

I checked my keyboard using Terminal. Most keys are all right, but some non-alpha numerics are not properly co-ordinated. I have tried to change the keyboard settings but these non-alphanumerics will not correspond properly to the keys.

@  This was obtained when hitting the double quote key.
" This was obtained when hitting the ampersand key.

I use a Dell keyboard (Dimension E520 computer)

Regarding the printer I use a Lexmark Z2390. Can it be used?

Any advice greatfully received.

Thanks

---

### Post by anon_private on 2010-04-24
Hi,

Can I display my Google Bookmarks list in Firefox?

Thanks

---

### Post by 3rdalbum on 2010-04-25
I think with all the things you're trying to do on Ubuntu, it would be best if you installed Ubuntu. You can have it as a "dual-boot" situation, where every time you start up you get the choice of booting into Windows or into Ubuntu.

Double-click the "Install" icon on the Ubuntu desktop to start the process. At the screen where it asks you how you want to partition, choose "Resize a partition" and then move the slider on the bottom bar graph towards the left, to choose how much space to give for Ubuntu.

> When I triied to playing an mp3 file stored in a Windows directory it would not play without a plugin. What files does Rythmbox support?

Rhythmbox supports whatever codecs are present on your system. Ubuntu doesn't ship with an MP3 decoder by default, because MP3 is a patented codec and Canonical doesn't have the $20,000,000 required to give all current Ubuntu users a copy of the codec. It's rather easy to install for free, though; the best way is to use Ubuntu Software Center or Synaptic Package Manager to install the "ubuntu-restricted-extras" package.

> Is there s firewall in UBUNTU

Windows requires a firewall because parts of Windows will listen for incoming connections, and attackers can take advantage of those parts of Windows remotely and take control of your computer. A firewall will stop those incoming connection requests from reaching Windows.

Ubuntu doesn't listen for incoming connections unless you enable Remote Desktop or install some software that will listen. So you don't need a firewall, because the attackers can't remotely connect to your computer if nothing is listening.

In a couple of limited situations it might be beneficial to run a firewall on your computer itself. If you want to run a web server as just a test, without anyone other than yourself being able to connect to it, then you will want a firewall. Install the "gUFW" package through Synaptic Package Manager and you've got one.

---

### Post by ugm6hr on 2010-04-25
> **3rdalbum said:**
> Rhythmbox supports whatever codecs are present on your system. Ubuntu doesn't ship with an MP3 decoder by default, because MP3 is a patented codec and Canonical doesn't have the $20,000,000 required to give all current Ubuntu users a copy of the codec. It's rather easy to install for free, though; the best way is to use Ubuntu Software Center or Synaptic Package Manager to install the "ubuntu-restricted-extras" package.

Of course, these will be lost after a reboot on a LiveCD.

As will gufw (the Firewall manager GUI - Graphical User Interface)

As mentioned - I think you are trying to hard to make a LiveCD into a usable long-term computer - not really what it was designed for.

Printer: [http://www.openprinting.org/printers/](http://www.openprinting.org/printers/)
You'll have to search for it here - although I think you will be out of luck. Lexmark are notorious for not releasing any Linux drivers.  If you are interested, Samsung & HP offer much better support for Linux.

---

### Post by dE_logics on 2010-04-25
> Since I have not unstalled UBUNTU can I click the 'Restricted Drivers Available' box. If so what extra features will I have?

That's not a feature, it will make a hardware work.
> Is there s firewall in UBUNTU

You don't need bullshit like firewall/antivirus for desktop purposes. Actually they never work in windows also...it's complete crap.


> According to the Help, the Network Manager is a yellow star. I see a little grey icon next to padlock 

Just do a few clicks on it and you'll understand everything.

> When I connected to Wireless, I was asked for a password for the default key.

I don't know what sorta crap is that...I'm myself pissed off with it. It's a software called 'sea horse', if you remove it, the whole ubuntu-desktop get removed.

Horrible apt dependency resolution.

> Can I save files, etc if UBUNTU is not installed?

To the HDD, yeah.

> Is it possible to see my VISTA directories, files, and programmes and use them under UBUNTU? I'll need to change directories to c:

Yes, but natively, you will not be able to run windows programs on Linux...there are alternatives through, but 50% possible.

With visualization it's 100% possible but it will be wayy slower than what it was with wine.

> If VISTA became infected could I clean the hard drive, C, from within UBUNTU? Could I run my anti-virus programmes from UBUNTU?

Even if it did not get infected you have to format it every 3 months right? But before doing that consult us, otherwise you'll be in trouble, big time.

> Is it better to do on-line banking from within UBUNTU using Firefox, rather that IE under VISTA? How safe would it be?

Ok, so you were using VISTA and IE for online banking.

Dude you're bankrupt! Go and cease your account NOW!!

---

### Post by 3rdalbum on 2010-04-25
de_logics: Do you want to remove the strong language from your post before a moderator sees it?

BTW Seahorse is the keyring manager. If you didn't have it, then Gnome probably wouldn't even start up successfully, and if it did then certain features would be broken. This is smart dependency resolution. The smart thing is to leave Seahorse where it is, and elect not to create a keyring (or just keep it unlocked).

---

### Post by anon_private on 2010-04-25
Thanks to all for responding. 

I am making progress.

The clock gives the right time after running as a LIVECD, but during work loses an hour. Is this a known bug?

For Internet Banking, are there any particular  plugins that I should consider?

Regarding WUBI. Surely installing UBUNTU in Windows would leave all the security problems that are associated with Windows!

It really is bad news if someone has printer that will not work under UBUNTU. Are there any drivers that will give a print of some kind (Lexmark printer (Z2390)).

Best wishes.

A

---

### Post by 3rdalbum on 2010-04-25
> **anon_private said:**
> For Internet Banking, are there any particular  plugins that I should consider?

No, just plain standard old Firefox will do nicely. Your internet banking site is just a web page like any other, really.

> Regarding WUBI. Surely installing UBUNTU in Windows would leave all the security problems that are associated with Windows!

Actually, no. Wubi is a Windows-based installer for Ubuntu - **not** Ubuntu running inside Windows. When Ubuntu is running, Windows is not and vice-versa. Insecure code doesn't hurt you when it's not running.

I tend not to recommend Wubi anyway, because if Windows stops working it also sometimes stops Ubuntu from working too; it's a bit difficult to explain the technical reason why this is so, but trust me.

> Are there any drivers that will give a print of some kind (Lexmark printer (Z2390)).

A quick web search yielded a link to this page, but Lexmark's site is misbehaving and I can't see what's actually on the page: [http://support.lexmark.com/index?page=content&productCode=LEXMARK_Z2300&actp=PRODUCT&id=DR860&segment=DOWNLOAD&userlocale=EN_US+&locale=en]("http://support.lexmark.com/index?page=content&productCode=LEXMARK_Z2300&actp=PRODUCT&id=DR860&segment=DOWNLOAD&userlocale=EN_US+&locale=en")

HP printers are well-renouned for working well with Linux.

---

### Post by anon_private on 2010-04-26
I know that UBUNTU can be installed to a pendrive.
 
Can it also be installed to a CD?
 
In UBUNTU, is there an equivalent programme to Windows Explorer?
 
Thanks

---

### Post by ugm6hr on 2010-04-26
No - you can't install on a CD - they are not big enough, and can't be written to.  Don't think a DVD-RW can do it either.

Yes - Windows Explorer = nautilus (see "Places" menu)

---

### Post by oldos2er on 2010-04-26
> **anon_private said:**
> I know that UBUNTU can be installed to a pendrive.
 
Can it also be installed to a CD?


That's essentially what the LiveCD is. If you're interested in creating a customized LiveCD, see [http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

---

### Post by anon_private on 2010-04-27
Thanks for the link.
 
I'll look into the topic.
 
On another point.
 
The Rescue Disk works well, but I cannot updtate the signature files from the CD because I use wi-fi.
 
I was wondering if it is possible to log into the router that I use from within the Rescue Disk, and then the Disk might be able to update the signature files?
 
Any thoughts.
 
Best wishes.
 
A

---

