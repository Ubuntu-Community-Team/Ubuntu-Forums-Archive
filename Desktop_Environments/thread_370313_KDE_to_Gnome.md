---
title: "KDE to Gnome"
date: 2007-02-25
forum: Desktop Environments
---

### Post by johndur on 2007-02-25
Hello,

After almost two years of playing (I use that word somewhat facetiously) with KDE I am to the point where MSFT is beginning to look not like a better alternative but at least a less painful one.

Over the past two years I have spent an inordinate amount of time trying to perform the most simple tasks such as, configuring a monitor,  getting wireless to work or having a video play in the web browser,  My patience is at the end.

My question to this group is can the gnome desktop be easily configured to do the following tasks without resorting to an endless march through search engine results, documentation and forums.

My wish list:

- Configure a monitor and video card in a straight forward manner
- Configure wireless connectivity
- Configure a network printer (on a MSFT home network, no domain)
- Install a component that will play mp3, wmv, wvx and quicktime

To be fair, at this point I know the basics of this stuff and in all probability  have the appropriate codecs and libraries installed. I run Firefox and Thunderbird.

My request is you consider this list and advise as to if these tasks can be accomplished in a Gnome environment and is it possible to affect this change without disrupting my email and browser setups.

I will certainly appreciate responses or comments.

This is the last roundup. Next stop Redmond.

Thank you,
John

---

### Post by TheWizzard on 2007-02-25
as far as i know, all your problems are DE independent. switching to gnome wouldn't help a bit. 

as for question #4: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by johndur on 2007-02-25
I understand the issues enumerated are for the most part underlying OS issues which may or may not be well documented. I didn't intend to start on a rant but I will anyway. I offer some qualification of the issues.

- Configure a monitor and video card in a straight forward manner. Fooled with this for 4 days lurching through the kde doc. Finally I went to Ubuntu were the answer was found in less than 5 minutes.

- Configure wireless connectivity. A nightmare with kde. Rather than fooling with the NDIS wrapper I purchased a driver for my card. The kde utility for managing the card was so bad I went back to the command line. The wireless utility would run three or four instances on startup.

- Configure a network printer (on a MSFT home network, no domain) - Again disjointed user interface for identifying resources, adding passwords where necessary etc. Menu boxes were unclear and the examples were nonexistent. 

- Install a component that will play mp3, wmv, wvx and quicktime. Here about four days was spent again sifting through a myriad of kde doc and forums. On the desktop there are three unique menus for associating file types with applications and none of them are coordinated. Finally went with Firefox and was able to start watching wvx feeds after about 10 min of configuration. 

- The famous KControl Center where you can do just about anything. Only problem is it was not included on the menu system as delivered. If you are a real masochist you can opt for SuSe and deal with Yast.

- The Samba interface works fairly well with Windows however it ignores other linux machines on the network.

- After setting konqueror preferences in a profile, every third time or so it forgets the preferences. Also the doc is flat out wrong when describing the process of configuring these view profiles.

So much for my rant. What I would like to do is install gnome and try it out. Before sifting through all the doc perhaps some could tell me what script loads kde in order to disable it  so I can switch to gnome.

Thank you.

---

### Post by aysiu on 2007-02-25
This will help you install Gnome:
[http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)

I'd advise installing *network-manager* for wireless connectivity.

As for other issues, you're running into two fundamental obstacles--lack of preinstallation and Ubuntu's Free software philosophy. If you buy a preinstalled Ubuntu computer, you don't have to fiddle around with video settings or wireless connectivity. If you use something other than Ubuntu (Linux Mint, Mepis, or PCLinuxOS), a lot of the proprietary formats (Flash, MP3, etc.) come by default with the operating system.

---

### Post by johndur on 2007-02-26
Thank you. I appreciate the information.

---

### Post by ComplexNumber on 2007-02-26
> **johndur said:**
> Hello,

After almost two years of playing (I use that word somewhat facetiously) with KDE I am to the point where MSFT is beginning to look not like a better alternative but at least a less painful one.

Over the past two years I have spent an inordinate amount of time trying to perform the most simple tasks such as, configuring a monitor,  getting wireless to work or having a video play in the web browser,  My patience is at the end.

My question to this group is can the gnome desktop be easily configured to do the following tasks without resorting to an endless march through search engine results, documentation and forums.

My wish list:

- Configure a monitor and video card in a straight forward manner
- Configure wireless connectivity
- Configure a network printer (on a MSFT home network, no domain)
- Install a component that will play mp3, wmv, wvx and quicktime

To be fair, at this point I know the basics of this stuff and in all probability  have the appropriate codecs and libraries installed. I run Firefox and Thunderbird.

My request is you consider this list and advise as to if these tasks can be accomplished in a Gnome environment and is it possible to affect this change without disrupting my email and browser setups.

I will certainly appreciate responses or comments.

This is the last roundup. Next stop Redmond.

Thank you,
John
it depends more upon the admin tools that the distro provides. ubuntu isn't very good in that area. i would suggest the following distros for you:
suse - has a great set of admin tools to help you with all your hardware
PCLinuxOS - ditto
mandriva (i find it a bit buggy, but only in the last 2 years).

---

### Post by jhorner on 2007-02-26
For the restricted formats (mp3, audio - video codecs) just download Automatix.  I am pretty sure, it also has a utility for setting up printers or printer drivers.

---

