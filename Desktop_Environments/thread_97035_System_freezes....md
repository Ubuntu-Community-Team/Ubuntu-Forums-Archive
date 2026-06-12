---
title: "System freezes..."
date: 2005-11-30
forum: Desktop Environments
---

### Post by SmokingGun on 2005-11-30
My Breezy system freezes from time to time.  It locks up and i can't move the mouse cursor or do anything but switch off completely.  I was just wondering if there were any system logs i could look at to diagnose why it's happening? and where they are located?

---

### Post by TSJason on 2005-11-30
Yikes, never a fun situation. 

 Try taking a look at /var/log/dmesg* or /var/log/messages* to see if you can find any errors. BTW what hardware are you running? I had some trouble for a while with a box running madwifi drivers that locked up when the wireless network got funky.

---

### Post by SmokingGun on 2005-11-30
It's interesting you mention wireless.  I am using a Toshiba laptop with the ipw2200 wireless drivers.  I have never had a problem while using Hoary and now Breezy, but in the last couple of weeks i start to get these lock ups.  I'm not sure, but it seems to happen when downloading with Azureus, although i could be downloading for hours and then a sudden freeze?  Interestingly, i have a Nintendo DS and tried playing online wireless with Mario Kart but the game always freezes after around 10 mins.  Reading around it seems a few people have had problems with the router i am using but surely that shouldn't cause Ubuntu to completely lock up?  Anyhow, i will take a look at those logs you mentioned.  Thanks.

---

### Post by excelsior on 2005-12-06
same problem here
someone on another thread suggested I turned off DPMS, but that didn't really help.

---

### Post by excelsior on 2005-12-06
Dec  6 10:01:42 localhost syslogd 1.4.1#17ubuntu3: restart.
Dec  6 10:01:45 localhost gconfd (darren-8277): Resolved address "xml:readwrite:/home/darren/.gconf" to a writable configuration source at position 0
Dec  6 10:21:44 localhost -- MARK --
Dec  6 10:33:21 localhost syslogd 1.4.1#17ubuntu3: restart.

from the "messages" file

I turned it on (after freeze) at 10:01, and it freezed again about half past 10 or thereabouts. (what does --MARK-- mean?)

---

### Post by torf on 2006-01-29
I've been experiencing freezes as well on a Thinkpad R51 using the ipw2200 drivers.  Usually it occurs within the first five minutes of booting, but has occured other times.  Recently I switched to my wired connection and experienced no lock ups.  However, when I wanted to switch back to my wireless connection (via the Administration --> Networking tool) the computer would lock up every time I clicked a button such as "activate" or "properties" when eth0 (my wireless interface) was selected.  Oddly, ifconfig and iwconfig didn't cause any freezes.  Looking through dmesg and syslog, this line was repeated multiple times:
>  ipw2200: Firmware error detected.  Restarting.
One other thing I think I should mention is that I installed vmplayer, which I had never done on previous Ubuntu versions.  I was thinking that perhaps some crazy connection bridging might be causing problems, but it seems other people are having trouble with ipw2200. Anyway, If anyone has had similar experiences and has fixed it, I'd be interested hearing in what you did. Thanks. :)

Edit: Forgot to mention, I am using WEP.

---

### Post by SmokingGun on 2006-01-30
I turned off WEP on my router and the system freezes have dissapeared....

---

### Post by techflavor on 2006-02-09
Torf, I have been experiencing the same problems you mention.

I am on a ThinkPad T43 with Ubuntu 5.10 installed.  I have also done a recent VMPlayer installation--I was also thinking that may be the cause of the problem.  Our only difference is I am using an Atheros wireless card and you are using one of the Intel cards.  

My system just randomly freezes (I'm always using wireless) time to time.  

Tonight I think I might run the VMPlayer uninstall script and will test things out again...

EDIT:  Note-- I am not using an encryption on my wireless (no WEP or WPA)

---

### Post by techflavor on 2006-02-10
Well last night I removed VMPlayer and so far the system hasn't locked up once.  Again, I am always on the Internet connected with my Atheros wireless card.  

Seems that may have been the culprit...

---

### Post by torf on 2006-02-24
techflavor - glad to hear someone's in the same boat.  Just curious, how did you set up vmplayer, manually or let it choose the defaults?  I let it set everything up automatically, and it bridged the vmnet connections to eth0, my wireless connection.  I really would like to keep vmplayer, so perhaps our solution is some tweaking of the config files. Let me know if you have any ideas, I'll keep you posted with mine.  (Perhaps brige vmnet to the wired connection, switch it back to wireless only when its needed? A shellscript would be handy there ;) )

---

### Post by GrumpyBob on 2006-02-24
Yesterday my Thinkpad R52 running Breezy froze twice.  This hasn't happened before.  I have GKrellm on the Desktop - it was showing a high level of unexpected hard disc activity at this time.
I'll check the logs as described above to see if there are any explanations.

Robert

OK it's happening frequently enough to make the laptop pretty damned unreliable.  /var/log/messages indicate this happens each time before the freeze (when everything stops responding, and there is a lot of HD activity):
Feb 26 20:12:54 localhost -- MARK --
Feb 26 20:32:54 localhost -- MARK --
Feb 26 20:39:00 localhost gconfd (root-24985): starting (version 2.12.0), pid 24 985 user 'root'
Feb 26 20:39:00 localhost gconfd (root-24985): Resolved address "xml:readonly:/e tc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb 26 20:39:00 localhost gconfd (root-24985): Resolved address "xml:readonly:/u sr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Feb 26 20:39:00 localhost gconfd (root-24985): Resolved address "xml:readwrite:/ root/.gconf" to a writable configuration source at position 2
Feb 26 20:39:00 localhost gconfd (root-24985): Resolved address "xml:readonly:/e tc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Feb 26 20:39:00 localhost gconfd (root-24985): Resolved address "xml:readonly:/u sr/share/gconf/local.defaults" to a read-only configuration source at position 4
Feb 26 20:39:00 localhost gconfd (root-24985): Resolved address "xml:readonly:/u sr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Feb 26 20:39:00 localhost gconfd (root-24985): Resolved address "xml:readonly:/u sr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Feb 26 20:39:00 localhost gconfd (root-24985): Resolved address "xml:readonly:/v ar/lib/gconf/defaults" to a read-only configuration source at position 7

---

### Post by Skrot on 2006-03-05
I have the same problem in Kubuntu Dapper. 
It only happends when I use the ipw2200 driver, and it usually happends during the 5-10 first minutes after boot. 
I've tried upgrading to the latest driver (1.1.0) and latest firmware (2.4), but it still happends. 
This started after i dist-upgrade in february I think. I ran dapper in january without this problem.

There is absolutely no relevant information in either messages, kern.log or syslog at the time of the freeze.

---

### Post by Teotihuacan on 2006-03-06
Hello,

I have the same problem. I use the ipw2200 driver. I haven't found any solution so far... :( 
But as we are not alone in this situation, I really hope we will find a fix.

I have this problem since I have updated my ubuntu three days ago (I haven't updated it for the last 2 months).

I will tell you if I find something...

Bye.

---

### Post by Skrot on 2006-03-07
@Teotihuacan:

Could you explain further when this problem occurs? There seems to be a mix of when it occurs. Some get it after a while, and some get it as soons as 5-10mins after boot/wlan is turned on. :)

---

### Post by Teotihuacan on 2006-03-07
[QUOTE=Skrot]@Teotihuacan:

Could you explain further when this problem occurs? There seems to be a mix of when it occurs. Some get it after a while, and some get it as soons as 5-10mins after boot/wlan is turned on. :)[/QUOTE]

OK, I'm not sure because it seems to freeze randomly but :

_ It freezes when I'm connected (WIFI+Wep)
_ It seems to freeze when a program dowload something (a mail, a rss feed, a web page, etc...)
_ My system haven't frozen during the last two months : I wasn't connected to Internet.
_ Last year, I had a WIFI connection too, and I had no problem. (that's why I thought it was the recent system update)
_ The system can lock after 2min of connection, but I can spend hours sometimes without a problem.


So I though it was the WIFI, but something is wired :

_ It can be a while before it freezes. I have spent a night downloading the ubuntu-desktop (I had just KDE) and kubuntu-desktop (I had KDE 3.5, I canted to come back to the "normal" version to see it it was the problem) whithout a problem. (I was in rescue mode)
_ At the beginning, I thought it was KDE, so I have installed Gnome.  It freeze less often with Gnome but it might be because I use less program on Gnome that use my connection. 


I haven't found anything interesting in the system logs (no error just before the freeze). I don't know exactly where to search, but my problem seems the same that some people in this forum thread (maybe it's not...).
The only thing I haven't try is gnome without KDM. I'm going to test this.

Thanks

---

### Post by Teotihuacan on 2006-03-08
For example, my last use of my computer has lasted less than one hour :

```

Mar  8 13:22:10 localhost syslogd 1.4.1#17ubuntu3: restart.
Mar  8 13:22:10 localhost anacron[7341]: Job `cron.daily' terminated (exit status: 1) (mailing output)
Mar  8 13:22:10 localhost postfix/sendmail[8533]: fatal: open /etc/postfix/main.cf: No such file or directory
Mar  8 13:22:11 localhost anacron[7341]: Tried to mail output of job `cron.daily', but mailer process (/usr/sbin/sendmail) exited with ststus 1
Mar  8 13:22:11 localhost anacron[7341]: Normal exit (1 job run)
Mar  8 13:27:31 localhost kernel: [4295807.798000] ipw2200: Firmware error detected.  Restarting.
Mar  8 13:33:44 localhost kernel: [4296179.990000] ipw2200: Firmware error detected.  Restarting.
Mar  8 13:39:01 localhost /USR/SBIN/CRON[9242]: (root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)
Mar  8 13:50:33 localhost kernel: [4297189.438000] ipw2200: Firmware error detected.  Restarting.
Mar  8 13:51:06 localhost kernel: [4297222.928000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Mar  8 13:51:06 localhost kernel: [4297222.928000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Mar  8 13:51:06 localhost kernel: [4297223.114000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Mar  8 13:51:06 localhost kernel: [4297223.114000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Mar  8 13:57:08 localhost kernel: [4297584.788000] ipw2200: Firmware error detected.  Restarting.
Mar  8 14:03:21 localhost kernel: [4297957.506000] ipw2200: Firmware error detected.  Restarting.
Mar  8 14:07:17 localhost kernel: [4298193.491000] ipw2200: Firmware error detected.  Restarting.
Mar  8 14:19:39 localhost syslogd 1.4.1#17ubuntu3: restart.
```

I wasn't in front of my computer when it froze. But here are the last logs from syslog.

---

### Post by Teotihuacan on 2006-03-09
As my computer was still crashing, I have decided to updrade to dapper (anyway, my breezy was unusable)

I havent succed to download the dapper upgrade but I have more information about the crashes :

I have launched an apt-get dist-upgrade from the "recovery mode". So X wasn't launched and I was able to see all the kernel error messages. When my computer froze, I had a lot of messages concerning the ipw module and finally a "Kernel panic" message.
Now I am sure it's a problem with the ipw module.

---

### Post by Teotihuacan on 2006-03-10
As the problem came from the ipw driver I decided to install a new one.

I have followed this tutorial : [http://doc.gwos.org/index.php/Install_ipw2200](http://doc.gwos.org/index.php/Install_ipw2200)
It's quite easy to install it this way. 

I have chosen the 1.1.0 version. Maybe it's to soon to say it, but it seems to be fixed.

Bye.

---

### Post by Skrot on 2006-03-11
[QUOTE=Teotihuacan]As the problem came from the ipw driver I decided to install a new one.

I have followed this tutorial : [http://doc.gwos.org/index.php/Install_ipw2200](http://doc.gwos.org/index.php/Install_ipw2200)
It's quite easy to install it this way. 

I have chosen the 1.1.0 version. Maybe it's to soon to say it, but it seems to be fixed.

Bye.[/QUOTE]

That was my first idea as well. I installed the 1.1.0 version of the ipw2200 driver, and version 2.4 for the firmware, but the problem endures. Let us know what you find out :)

---

### Post by Teotihuacan on 2006-03-11
Actually my computer haven't frozen since my last message. I really think it was the solution for me.

_ The tutorial that I have followed include a step that delete all the old modules. It also tells to install the latest module ieee80211. Maybe you have forgotten a step.

_ Maybe you have not the same problem than me. Maybe you can try to be in a terminal (I mean CTRL+ALT+F1) when it freezes... you may see some usefull messages...

---

### Post by danish_demon on 2006-03-11
i am having a similar problem, but am using a different wireless device (rt2570 driver).  some times when i first start up and attempt to connect to my wireless network via nm-applet, it will freeze.  to the best of my recollection, this has never happened after i have been able to connect to my network and then had to reconnect.  when it happens again i will have to remember to look at my system logs and maybe post some more info.

---

### Post by Skrot on 2006-03-13
[QUOTE=Teotihuacan]Actually my computer haven't frozen since my last message. I really think it was the solution for me.

_ The tutorial that I have followed include a step that delete all the old modules. It also tells to install the latest module ieee80211. Maybe you have forgotten a step.[/QUOTE]

That's true. I did not remove the old stuff. I'll try it. Thanks. 

[QUOTE=Teotihuacan]_ Maybe you have not the same problem than me. Maybe you can try to be in a terminal (I mean CTRL+ALT+F1) when it freezes... you may see some usefull messages...[/QUOTE]

My computer will freeze about 5-15 minutes after boot if wlan driver is enabled. It doesn't matter if I'm in KDE or terminal. There is no usefull information from logs (messages, syslog kern.log).

---

### Post by Teotihuacan on 2006-03-14
[QUOTE=Skrot]My computer will freeze about 5-15 minutes after boot if wlan driver is enabled. It doesn't matter if I'm in KDE or terminal. There is no usefull information from logs (messages, syslog kern.log).[/QUOTE]

Actually, the messages I'm talking about are not the one that are put into the logs. I was a "kernel panic". A kernel panic is not written in the logs... the problem is we can't see it if we are not in a terminal when it crash.

But I hope your problem will be fixed after you will compile the drivers. (it worked for me)

---

### Post by Skrot on 2006-03-14
[QUOTE=Teotihuacan]Actually, the messages I'm talking about are not the one that are put into the logs. I was a "kernel panic". A kernel panic is not written in the logs... the problem is we can't see it if we are not in a terminal when it crash.

But I hope your problem will be fixed after you will compile the drivers. (it worked for me)[/QUOTE]

Okay. Last time I was in console I did not notice any kernel panic when it froze.

Anyway, I tried upgrading to 1.1.1 with firmware 3.0 which was just released a couple of days ago. At first it did not freeze my computer. But when I rebooted it froze as soon as I turned the WLan on. 

Still nothing usable in the logs. :(

---

### Post by Teotihuacan on 2006-03-15
[QUOTE=Skrot]Okay. Last time I was in console I did not notice any kernel panic when it froze.

Anyway, I tried upgrading to 1.1.1 with firmware 3.0 which was just released a couple of days ago. At first it did not freeze my computer. But when I rebooted it froze as soon as I turned the WLan on. 

Still nothing usable in the logs. :([/QUOTE]

I have installed the 1.1.0 because it was marked "stable". I don't know if it's the reason.

---

### Post by stepherhall on 2006-03-20
I'm getting frequent freezes with Dapper (previously had a very stable Breezy based system), and every time the last thing in the system log is gconfd, as a couple of previous posters have shown in their logs.   I am also using wireless (Linksys usb adapter), but through ndiswrapper, rather than a native driver.  Strangely, it only locks when I am using X, and it only seems to be when I am accessing the internet, either with Firefox, Konqueror, or downloading updates using Synaptic.  Firefox will get halfway through downloading a page, Synaptic will download the first few packages, before everything stops.  

I have no problems, however, accessing the internet from a text console, using lynx, aptitude or apt-get (downloaded Kubuntu desktop from console), without any crashes at all, even though X is still running.

Any suggestions gratefully received.

---

### Post by Skrot on 2006-04-07
I think this is related to [ this bug](https://launchpad.net/distros/ubuntu/+source/linux-image-2.6.15-19-686/+bug/34870)

---

