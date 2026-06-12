---
title: "Help with Mini1018 WiFi Realtek RTL8188CE."
date: 2010-09-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yerayenrique on 2010-09-22
Hi guys,

I would like some help to make my Dell Mini1018's WiFi card (Realtek RTL8188CE) work.

It doesn't work out of the box on 10.04, I've tried to enable it the way it's enabled on Dell1012 but the card must be different as it doesn't work. Not even with NDISwrapper.

This is very frustrating as I received the netbook few days ago and I have to stick a USB WiFi adapter that's almost half the size of the computer :mad:.

If you need further info, let me know and I'll reply shortly.

Thanks in advance :).

---

### Post by yerayenrique on 2010-09-27
Guys, any updates?

Thanks.

---

### Post by `JoXeR` on 2010-09-28
Hi, i read about driver you request to realtek on the french forum ( i can't post there 'cause my french is poor).
I'm very interested, reply me asap as you can work them.
Did you ask also for bluetooth driver?

Btw is mini 1018 a great machine to work? I would read ebooks and carry it to school to work there.

Thanks in advice

---

### Post by yerayenrique on 2010-09-28
Guys, I have to say this:

SOLVED!!!

1) Go to Realtek's WEB and contact the technical support department through email asking for the Linux drivers for RTL8188CE.

2) They will send you a tar.gz, which you must uncompress and read the readme file inside which will give you the compiling instructions.

NOTE: you must have previously done "sudo apt-get install build-essential", otherwise, you won't be able to compile.

The process is extremely simple and Realtek's technical service is awesome, they replied within a few hours.

Let me know if you have any doubts.

I can finally say: I GOT MY MINI1018 FULLY RUNNING WITH UBUNTU, BYEBYE WINDOW$.

---

### Post by yerayenrique on 2010-09-30
Hi there,

For all of you who are having trouble to contact Realtek's technical support (they may be getting loads of emails of people requesting the drivers) I've uploaded them for you to freely download:

[http://jump.fm/WDIUB](http://jump.fm/WDIUB)

Hope you enjoy!

---

### Post by Renttlm on 2010-10-04
Can you give me a complete description of process for the install?

i don't understand after reading the readme file...thanks in advance

---

### Post by yerayenrique on 2010-10-04
> **Renttlm said:**
> Can you give me a complete description of process for the install?

i don't understand after reading the readme file...thanks in advance

Let's see if I remember:

1) Download the file from the link provided above.
2) Uncompress it.
3) Open a terminal, and from there:
3.1) sudo su
3.2) navigate to the uncompressed folder
3.3) sudo apt-get install build-essential
3.4) make
3.5) make install
3.6) reboot

And you should have it working.

---

### Post by Renttlm on 2010-10-04
thankssss man work it!!!

finally ubuntu on my mini 1018! :)

---

### Post by yerayenrique on 2010-10-04
Yeah, it does feel nice.

I spent many days looking for this and when I finally got it it was like a miracle.

:guitar:.

---

### Post by wouzs on 2010-10-22
Is it possible to propose this driver to be included in the next ubuntu release so it will work out of the box? I think many people would like to put ubuntu on their Dell 1018 mini.

My next question is if it would be possible not having to build this driver again when there's a kernel update.

---

### Post by evilxsystems on 2010-10-25
thanks, worked for our new 1018...only catch was that we needed to do the sudo su, rather than sudo make , sudo make install....the former worked but the later didnt

---

### Post by wouzs on 2010-10-26
> **wouzs said:**
> Is it possible to propose this driver to be included in the next ubuntu release so it will work out of the box? I think many people would like to put ubuntu on their Dell 1018 mini.

My next question is if it would be possible not having to build this driver again when there's a kernel update.

Someone already made a deb package with a DKMS module. The PPA is the following:
[https://launchpad.net/~lexical/+archive/hwe-wireless](https://launchpad.net/~lexical/+archive/hwe-wireless)

---

### Post by mjuvt on 2010-11-30
That solved the problem on my Dell Inspiron mini10! Thanks! I just installed the package
[rtl8192ce-dkms_2.6.0003.0628.2010ubuntu2_all.deb]("http://merkur.informatik.rwth-aachen.de/bscw/bscw.cgi/d3065309/rtl8192ce-dkms_2.6.0003.0628.2010ubuntu2_all.deb") via the link in the above posting.

---

### Post by sjakok on 2010-12-03
> **yerayenrique said:**
> Let's see if I remember:

1) Download the file from the link provided above.
2) Uncompress it.
3) Open a terminal, and from there:
3.1) sudo su
3.2) navigate to the uncompressed folder
3.3) sudo apt-get install build-essential
3.4) make
3.5) make install
3.6) reboot

And you should have it working.

Hi, I'm total beginner so I need even more help, I've downloaded file, started terminal with sudo su, but I can't navigate to the uncompressed folder, so I was unable to solve the problem with wireless... would someone be so kind to wright manual how to do it for absolute beginner, I do not know absolutely nothing about ubuntu, I saw it yesterday for the first time! Thank you!

---

### Post by canucked on 2010-12-09
sjakok: If you add the following PPA and install the rtl8192ce-dkms package mentioned in the earlier post (Thanks wouzs and Keng-Yü Lin!), you don't have to go to the trouble of compiling Realtek's driver.  And you won't have to recompile manually when a new linux kernel is installed.

In terminal, run:
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```

Reboot, and hopefully your wireless will be working!

---

### Post by tomreid on 2010-12-19
Thanks for this fix it is really simple and worked first time. I can now get Ubuntu working on the Dell Mini I bought for my Mum's Christmas.

cheers all

---

### Post by mid4200 on 2010-12-22
> **yerayenrique said:**
> Let's see if I remember:

1) Download the file from the link provided above.
2) Uncompress it.
3) Open a terminal, and from there:
3.1) sudo su
3.2) navigate to the uncompressed folder
3.3) sudo apt-get install build-essential
3.4) make
3.5) make install
3.6) reboot

And you should have it working.

hey please i didn't understand the step 3.2) how can i do it ?

---

### Post by tomreid on 2010-12-24
Hi

The fix supplied by Canucked seemes to work fine, but I'm hitting an issue I have seen before on Ubuntu systems now.

When I have been using the wifi for around 10 mins, when I surf to another URl, the browser gets stuck at "looking up....." and I have to re-boot the system to start the internet working again.

I have an older Dell mini 10V (it's about 16 months old running off the same wifi in the same house and it never does this. I also had exactly this same issue on a HP Desktop, it seemed to be some kind of DNS look up issue, but I never got to the bottom of it.

Any help gratefuly received.

cheers

---

### Post by canucked on 2010-12-24
tomreid: The Toshiba L655 laptop with Realtek RTL8188CE wireless I configured worked fine after installing rtl8192ce-dkms from the lexical/hwe-wireless PPA.  I didn't notice any DNS issue.

However, in this post: [http://ubuntuforums.org/showthread.php?t=1641931]("http://ubuntuforums.org/showthread.php?t=1641931")
bwdave did have a DNS problem after installing rtl8192ce-dkms.  He had to delete the wireless connection, then re-establish it.

One possible reason I didn't experience that problem is that I don't use my ISP's DNS servers; I use OpenDNS.
[https://store.opendns.com/setup/device/ubuntu/]("https://store.opendns.com/setup/device/ubuntu/")

To use the OpenDNS servers, edit /etc/dhcp3/dhclient.conf and insert:
```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```
After rebooting, you can verify that you are using OpenDNS by visiting: [http://welcome.opendns.com]("http://welcome.opendns.com")

Does deleting your wireless connection or using a different DNS provider solve your connection issue?

---

### Post by canucked on 2010-12-24
mid4200: Step 3.2 involves changing directories using the "cd" command in Terminal.  You can read about it here:
[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")

---

### Post by ilanesh on 2011-01-28
I just got a new dell mini 1018 too where I need the same driver, I have downloadet it, but when it comes to make, then it tells me no make file, and also I do not know how to uncompress it, I am no techi and never did soemtehing like this. Please help, how to uncompress, it is all in my home folder. I now for days here try to get wireless working and I just got the wrong netbook I see, it is horrible, do not know what to do with it now. Please help.

---

### Post by yerayenrique on 2011-01-28
> **ilanesh said:**
> I just got a new dell mini 1018 too where I need the same driver, I have downloadet it, but when it comes to make, then it tells me no make file, and also I do not know how to uncompress it, I am no techi and never did soemtehing like this. Please help, how to uncompress, it is all in my home folder. I now for days here try to get wireless working and I just got the wrong netbook I see, it is horrible, do not know what to do with it now. Please help.

Hi,

This is very simple:

1) Uncompress file (using nautilus: right click > uncompress).
2) Open a terminal.
3) Navigate to the folder that you just extracted (if you extracted the zipped file to /home/user (where user is your user name) and the folder is called (RTLDRIVERS) this would be: cd /home/user/RTLDRIVERS.
4) sudo su
5) make
6) make install
7) reboot.

This should have it working.

I hope you have luck with this, at first me too I was dissapointed with the netbook, but now that I got it all working OK im happy with it :).

---

### Post by ilanesh on 2011-01-29
Hi, thank you for your reply. I tried it, it is telling me no such directory. Also on my file browser when iclick on it it is only extracting it, no option for something else, only extract, and it has extract it to my home folder, and I could not find inside there an rtldrivers, I dontn o what is going on, I wish I could give this dell thingy back and get my acer one back, never had a problem with it. I really don`t no what to do. I have ubuntu 10.04.1  and ubuntu 9.10, on ubuntu 9.10 those commands are not working. I just don`t want to install over the windows 7 now anything else because when I want to give it back they will not take it back. I am so frustraited, why ubuntu is not enableing this driver that it works out of the box? I need someone who could try to do this for me, I am no techi at all. Please help maybe something easier? Thank you. :(

---

### Post by yerayenrique on 2011-01-29
> **ilanesh said:**
> Hi, thank you for your reply. I tried it, it is telling me no such directory. Also on my file browser when iclick on it it is only extracting it, no option for something else, only extract, and it has extract it to my home folder, and I could not find inside there an rtldrivers, I dontn o what is going on, I wish I could give this dell thingy back and get my acer one back, never had a problem with it. I really don`t no what to do. I have ubuntu 10.04.1  and ubuntu 9.10, on ubuntu 9.10 those commands are not working. I just don`t want to install over the windows 7 now anything else because when I want to give it back they will not take it back. I am so frustraited, why ubuntu is not enableing this driver that it works out of the box? I need someone who could try to do this for me, I am no techi at all. Please help maybe something easier? Thank you. :(

Hi,

All I can do now and in order for you NOT TO SWITCH BACK TO WINDOWS if to offer you remote assistance through Team Viewer. If you're up to it, let's arrange a date.

---

### Post by ilanesh on 2011-01-30
Hi yerayenrique, thank you this is very nice from you. But now I founbd out that there are other problems too, no sound, is working, no wifi, and ubuntu 10.04 and 10.10 both of them are not installing on the internal hdd from this netbook, also not on any of my external usb hdd`s. It installs perfect without problems only to my new asus altec, no problem with that. Then I finally could install the ubuntu 9.10 on the dell inspiron, but no sound at all. Then I tried via instructions to install and compile and upgrade the alsa sound and all is not good anymore and have a mass.
I do not want any dell anymore, this is horrible.
I wish I would know with which netbook the ubuntus work with everything out of the box, sound wifi etc webcam video everything like on my asus laptop. I had once asus eee and it was not good and broke befor the year was over and also is too expensive. I had a acer one 9 inch where I had no problems but it broke. Now they have only the new once here with 10 and 12 inch this is too big 12 inch. I don`t no what to do. Windows is gone also cause I installed the old ubuntu on it.

---

### Post by ilanesh on 2011-01-31
Hi enrique, I have sent you an email, I have also yahoo with different username. Hope it is not going to your yahoo spam folder, please look also in spam folder when it is not in your inbox. Hope you have time this eving? Thanks again, Ilana

---

### Post by yerayenrique on 2011-02-01
> **ilanesh said:**
> Hi enrique, I have sent you an email, I have also yahoo with different username. Hope it is not going to your yahoo spam folder, please look also in spam folder when it is not in your inbox. Hope you have time this eving? Thanks again, Ilana

Hi,

Yes, I've replied to your personal email. Let's see if we can fix this through Teamviewer and post results back ;).

---

### Post by ilanesh on 2011-02-01
ok thank you, thought my email went to your spam folder and you never received it. :-)

---

### Post by AngryNick on 2011-02-14
FYI:  I found myself reading this thread again about 2 months after getting the Mini 1018 wifi working using the steps above.  

The Realtek wifi driver stopped working on my machine after the latest kernel 2.6.35-25 update on Lucid. Since I had retained the driver files from before, all I had to do was navigate to their folder and run:

1. sudo su
2. make (i don't know that this was necessary for me)
3. make install
4. reboot

Wifi worked again after that.  Previous updates didn't blow out the driver, so perhaps mine was an unusual situation.

---

### Post by ilanesh on 2011-02-14
Why to try to figure out all this and waste the precious time when you have a distro who is especially made for the netbooks, especially for the dell mini 1018. Use Jolicloud 1.1, it is the best, the one befor the 1.0 I also did not like, it would not work properly, but their new one it blew me away.
All works out of the box, sound video wifi, no configuration needet, wow. If i would know this from the beginning it would spare me lots of troubles. ;)

---

### Post by jock mackay on 2011-02-14
Can I add something to this thread please? 
I too am using a Dell Mini with the Realtek wireless card, and thanks to this thread I got wireless working by using the PPA issued by Keng-Yu Lin and installing rtl8192ce-dkms. This got the wireless working, but left an irritating fault, namely that whenever I use BBC IPlayer, or the ITV version the internet is killed and "Unable to locate server" is returned. Rebooting gets wireless internet going again, but attempting to use IPlayer kills it again. This fault does not show up using ethernet connection.
Has anybody else had this issue, and how is it resolved?

---

### Post by ilanesh on 2011-02-14
The best solution is to install Jolicloud 1.1, it is Ubuntu based, and it has all the drivers installed and works out of the Box. I just tried now on it the BBC Iplayer on it from the Browser, no crashing no wifi disconnecting. Try it. ;)

---

### Post by jock mackay on 2011-02-14
Thank you, ilanish, for that suggestion. Jolicloud is a brand new concept to me (also, I am new to Ubuntu), and was not quite what I expected the solution to be. I will take a little time to think about this, but it is great to see that you have the dell with Realtek wireless functioning properly.

---

### Post by jock mackay on 2011-02-19
For ilanesh .... I did attempt to load jolicloud last night. The down load failed citing a partition problem, and leaving me win grub recovery. Thankfully I was able to reload 10.10 from a flash drive and have the system working, but with the same problem as before.

Back to the forums, I guess

---

### Post by ilanesh on 2011-02-20
What do you mean with partition problem? Do try to install it to windows? you can run it inside windows also, but I have formated the whole HDD and let Jolicloud do his job, I did nothing only waiting till it was finishe, it formated it also automatic after asking me if i want to whip out the whole harddrive, and I clicked yes.
Then after finished it booted up normal and it did updates and thats it, but together with another operating system I don`t no how. I am only happy I don`t need windows 7 starter anymore, it was horrible.
You can try Linux Mint, this is very good, but then you need to know how to install the wifi driver but its the same like ubuntu. Linux mint works perfect with audio on my Dell Mini 1018, but honest I don`t no how to install the wifi driver, i did it exatly like it is written on the forum and had no luck with it.
Linux Mint works more out of the box then the orignal ubuntu, they have also preinstalled many software like java and flash player, and VLC Player when you download their DVD. As to the flash crashing, I get only flash player crashings when I want to login on paltalk express, it is annoying on the Dell mini, but the other stuff works with flash. Linux mint is Ubuntu based too, I like it. I have it on my Asus Laptop.

---

### Post by Pastor_JW on 2012-04-06
> **canucked said:**
> sjakok: If you add the following PPA and install the rtl8192ce-dkms package mentioned in the earlier post (Thanks wouzs and Keng-Yü Lin!), you don't have to go to the trouble of compiling Realtek's driver.  And you won't have to recompile manually when a new linux kernel is installed.

In terminal, run:
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```

Reboot, and hopefully your wireless will be working!

Thank You very much for this!  Fixed and worked perfectly for 10.04 on a HP pavilion g7 laptop!  Good one!

---

### Post by ilanesh on 2012-04-06
> **Pastor_JW said:**
> Thank You very much for this!  Fixed and worked perfectly for 10.04 on a HP pavilion g7 laptop!  Good one!
I did not know that still is ubuntu 10.04 around, we have long agao now ubuntu 11.04 and 11.10 and now even ubuntu 12.04, and on all those no problems with wireless driver on dellInspiron Mini. You should use the newer Ubuntus. All problems fixed.

---

### Post by paintba11er89 on 2012-06-03
> **canucked said:**
> sjakok: If you add the following PPA and install the rtl8192ce-dkms package mentioned in the earlier post (Thanks wouzs and Keng-Yü Lin!), you don't have to go to the trouble of compiling Realtek's driver.  And you won't have to recompile manually when a new linux kernel is installed.

In terminal, run:
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```

Reboot, and hopefully your wireless will be working!

This method doesn't work for 12.04 Precise unfortunately :/

---

