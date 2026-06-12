---
title: "New Dell Mini 9 - Networking / Bluetooth"
date: 2009-02-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by delboy1 on 2009-02-02
Hi all

I just got my new Dell Mini 9 with Ubuntu (which I am new to) and have started playing around with it. Swapped out the RAM for 2GB and will update to a Runcore 32Gb SSD when someone gets some stock here in the UK. In the meantime I am sticking with the stock Dell Ubuntu while I get used to things. However, at the moment I have three problems

1 - How do i get it to talk to my Windows network. For the sake of assistance, The network is called Workgroup and the Server (running Windows Home Server) is called server. The username is user and the password is password. I appreciate it will never be quite the same as a WHS to Windows XP or Vista relationship but surely the Dell Mini should be able to open files from and store files to the server.

I can mount a folder from the server (say my documents) and see the files and sub folders within it but when I click on, say, a word document, Open Office appears to start (i.e. the OO splash screen comes up) but it doesn't actually start and the document doesn't open. If I copy the document from the folder onto the Mini then all seems Ok and I can access the document. If I mount a videos folder, I can get a video to open and play in Totem (very shakily) but it won't open in VLC. If I copy the file to the Mini, it plays just fine in VLC. I am totally confused.

2 - I have problems with the Network Manager. Sometimes it (i.e. the network icon) starts on start up and sometimes it doesn't. If my network is on then generally it starts up and finds it. If the router is turned off then it doesn't start up and I can't find an option to get it started and force it to look for networks. The strength indicator is four grey bars but i thought they were supposed to be blue and despite the network SSID being called DPC2009 if I hover the cursor over the grey bars the yellow message is "Wireless network connection to '(none)' " - why is it not saying .....connection to 'DPC2009'

3 - Is there anyway to stop Bluetooth coming on by default. I don't want it all the time and surely by being on it wastes battery. I have found that I can turn it off through aircraft manager but that is a real PITA to have to do this every time I turn it on.

4 - Is there an equaliser function in Ubuntu for the sound? The sound from the speakers is quite feint and very tinny.

Finally, please can someone confirm that the Ubuntu disc that came with the Mini is the Dell version of Ubuntu as the disk gives no indication of that and just looks like a plain Canonical Ubuntu disk.

Sorry for the all the questions but I am a complete Ubuntu noob having been force fed Windows all my computing life to date. Thanking you all for any assistance

Delboy

---

### Post by armandh on 2009-02-02
if you are using the ubuntu interface 
places>network>workgroup>>>etc
I've moved on to 8.10 and have forgotten the dell interface
but I think places is in the dropdown

I use a NSLU2 NAS and have no problems with the home network hooked to the dsl. the other network attached to the cable modem I could never see the NAS correctly.

if your router/wlan is turned off
it won't find it [same for wired]

I did not get bluetooth

the speakers are the limiting factor try ear phones

the DVD disk that came with my mini 9 is the dell remix and codex/drivers. it is NOT a live disk and will only restore to a factory new OS by formatting the disk and copying the Dell OS to the Hdd it is not a regular Ubuntu OS. I am happy[er] with 8.10 Ubuntu

---

### Post by delboy1 on 2009-02-02
> **armandh said:**
> if you are using the ubuntu interface 
places>network>workgroup>>>etc
I've moved on to 8.10 and have forgotten the dell interface
but I think places is in the dropdown

if your router/wlan is turned off
it won't find it [same for wired]

I did not get bluetooth

the speakers are the limiting factor try ear phones

the DVD disk that came with my mini 9 is the dell remix and codex/drivers. it is NOT a live disk and will only restore to a factory new OS by formatting the disk and copying the Dell OS to the Hdd it is not a regular Ubuntu OS. I am happy with 8.10 Ubuntu

As I say I can find and mount the shared folders and can see all the files but they just won't open properly unless I physically copy them across from the server onto the mini and then open them. That cannot be right.

I appreciate that if the router is of it won't find it. What I am saying is that if my router is off it doesn't find anything and I can't find a way to force it to look for networks. Therefore unless I am at home and can log onto my home wifi I can't log on to a wifi network.

I will give earphones a try

How hard was it to go the 8.10 route. Did everything work? I have seen postings of people having various problems with sound, wifi, etc

---

### Post by ugm6hr on 2009-02-02
Left-click on the network manager icon (two computers in top right panel) to drop-down a list of networks.

Does the Airplane Mode menu not remember your setting after a reboot?  I thought it did (but can't remember for sure).

I suspect the networking issue is a reflection of the speed of your wifi network.  If video is shaky etc - that is because it cannot read the file at speeds required not to be shaky.  Bit surprised by OO Writer files not working with shares though...

---

### Post by delboy1 on 2009-02-02
> **ugm6hr said:**
> Left-click on the network manager icon (two computers in top right panel) to drop-down a list of networks.


I can't because it's not there. It only starts if it can detect my home network otherwise it doesn't start.

My network speeds are fine - rock solid 54 Mbps. No other laptops have this problem. I have a vista laptop which I connect to the TV to watch videos and it works fine.

have to say this whole Ubuntu thing has not got off to a good start and I'm really tempted to wipe it and revert to XP

---

### Post by armandh on 2009-02-03
I think I understand you now

I don't believe your mini9's Wireless lan is "off" if it will log on to your home wireless lan. to log on to other wireless lans such as the local coffee shop, click on the "bars" and select the one you want. It probably does not display bars if there are no wireless lans with in range.

most mcdonalds have wireless lan and if your home DSL is AT&T you can log on free using your main e-mail and pass word.

if you are looking for a G3 type connection to the www you need usb plug in  or the correct mini9 options [I did not get this] and an account with a provider.

---

### Post by delboy1 on 2009-02-03
There are no bars and no little mini computers. If it can't see a network it can automatically log on to then it just doesn't start and there is nothing in the top right panel to click. I can open Network Manager but unless I know the SSID of a network then I can't log on.

The whole thing appears to be screwed as even when it does connect to my home network the bars are greyed out (are they not supposed to be green or blue?) and despite the network SSID being called DPC2009 if I hover the cursor over the grey bars the yellow message is "Wireless network connection to '(none)' " - why is it not saying .....connection to 'DPC2009'

All I can think is that I upgraded to version 7 of Network Manager and something has gone wrong?? How do I go about uninstalling and reinstalling Network Manager - is it just via Synaptic - mark for deletion and then mark for installation or is there anything I need to do to make sure all trace of it goes prior to reinstalling

Anyone got any clues as to why I can see folders on my server but not open them? If I try to run, say, an MP3 then I can see Rhythmbox start but within a second it closes again. Likewise OpenOffice for documents & spreadsheets.

---

### Post by ugm6hr on 2009-02-03
> **delboy1 said:**
> All I can think is that I upgraded to version 7 of Network Manager and something has gone wrong?? How do I go about uninstalling and reinstalling Network Manager - is it just via Synaptic - mark for deletion and then mark for installation or is there anything I need to do to make sure all trace of it goes prior to reinstalling

Try to refrain from messing around with unofficial upgrades until you know what you are doing.

The Dell Mini 9 does not have a standard Ubuntu, so most unofficial How-tos wont work.

Sorry - forget to tell you how to re-install original version...

It depends on how you upgraded - tell us how you did that, and maybe we can help.

Also - it is generally best to give all relevant details when asking for help.  That would have been my first thought if you had mentioned that you had upgraded network manager.

---

### Post by delboy1 on 2009-02-03
So how do I get back to where I was? Uninstall v7 delete the repositories for that and then hopefully it will pick up the previous version??

Upgraded per a thread on another forum trying to solve the network issues of files being seen but not opening. Others with dell ubuntu had upgraded succesfully

---

### Post by delboy1 on 2009-02-03
I added the following repositories to upgrade Network Manager

deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main

---

### Post by ugm6hr on 2009-02-03
It depends on which packages were upgraded.

However, as you suggest, removing the new PPA repo, completely removing network-manager in Synaptic, reloading the repos, then reinstalling should work.

Be wary though....  Your wifi will not work during this - so make sure you have a wired connection.

---

### Post by delboy1 on 2009-02-03
> **ugm6hr said:**
> It depends on which packages were upgraded.

However, as you suggest, removing the new PPA repo, completely removing network-manager in Synaptic, reloading the repos, then reinstalling should work.

Be wary though....  Your wifi will not work during this - so make sure you have a wired connection.

That would reinstall version 7 but how do I get back to version 6

Remove repos, uninstall and then update / install from remaining Dell repos???

---

### Post by ugm6hr on 2009-02-03
> **ugm6hr said:**
> However, as you suggest, **removing the new PPA repo**, **completely removing network-manager** in Synaptic, **reload package information**, then **reinstalling should work**.

I have edited the words to make it clearer.

But yes. What you said.

---

### Post by delboy1 on 2009-02-03
Thanks for your help ugm6hr. I will give that a go when I get time.

---

### Post by delboy1 on 2009-02-05
Removed PPA from Repos and uninstalled network manager completely

I now have NO network connection at all (wireless or wired) so how do I reload package information and reinstall??????

---

### Post by ugm6hr on 2009-02-05
Reboot with wired cable plugged in.

---

### Post by delboy1 on 2009-02-06
Whatever happened caused a major breakdown - Ubuntu would not start properly and when it eventually did start (took several minutes to boot) it was running extremely slowly - like 2 or 3 minutes to open applications.

Then tried to make an ISO (IMGBurn) of the dell linux DVD and use unetbootin to make a USB bootable to re-install but just couldn't get that to work. It would recognise the stick, load a couple of files and then just sit with a cursor flashing.

Used unetbooting to load 8.10 ISO onto the stick and that worked suggesting there is something wrong with my 8.04 Dell ISO.

Anyway, now have 8.10 loaded and all seems to be working for the moment

---

### Post by Buzzdee on 2009-02-06
Hey, 

concerning the generally slow performance and networking problems, have a look at the /etc/hosts file (open it writable with the command 'sudo gedit /etc/hosts'). Is there a line saying "127.0.0.1 localhost"? If not, add it and reboot. 

If your network manager applet is not shown (the 'bars', as referred to in this thread ;) ) try 'sudo /etc/init.d/networking restart', followed by 'network-manager-applet &'. 

I hope this could help :)


Best regards, 
Bastian

---

### Post by delboy1 on 2009-02-06
OK, I really am getting to the end of my tether with linux & ubuntu now. The XP install disc is getting closer and closer.

Set up 8.10 last night and all has been working well and then all of a sudden Networking stops working. Why?

I can't get a wired connection. I can't get a wireless connection. All I did was shutdown to recharge and start up again.

How do I get the Network back

---

