---
title: "Sync Sony Ericsson W700i with Ubuntu?"
date: 2006-08-24
forum: Desktop Environments
---

### Post by Flavian on 2006-08-24
Does anyone know a WORKING way how to sync my Sony Ericsson W700i with Ubuntu. I would need it for the contacts, since I have phone numbers and mail adresses all in there.
I would prefer Thunderbird, but I would use Evolution as well if Thunderbird is not possible...

I would be thankful for a good HOWTO!
Thanks very much in advance.

Flo

---

### Post by PartisanEntity on 2006-11-18
I would also be interested to know if there is a way to sync a Sony Ericsson phone with Thunderbird.

Thank you!

---

### Post by Aetherius on 2006-11-19
Hey all,

I won't say this is a definitive HOWTO but this is how i did it for my k800i and evolution, as for thunderbird, i don't know, never tried, i'll have a look-see and let you know.


[SIZE="4"][COLOR="DarkOrange"]step 1 REQUIREMENTS[/COLOR][/SIZE]


```
sudo apt-get install multisync
sudo apt-get install libmultisync-plugin-evolution
sudo apt-get install libmultisync-plugin-irmc
sudo apt-get install libmultisync-plugin-irmc-bluetooth
sudo apt-get install bluez-utils

```

If you have any trouble with the bluetooth then just install any package with bluetooth in the description :p 


[SIZE="4"][COLOR="DarkOrange"]step 2 PAIRING[/COLOR][/SIZE]


The best way to do this is to start from the phone, go to the **bluetooth settings** and then to '**My Devices'**, select **'New Device'** and search for your computer. Then enter a PIN. Then a popup should appear on your computer asking for the PIN. 

Because you initiated this pairing from your phone you avoid the notorious problems with defining the default pin on ubuntu.

Once you successfully paired them select your computer on your phones menu and set it to **ALWAYS ALLOW CONNECTION.**


[SIZE="4"][COLOR="DarkOrange"]step 3 MULTISYNC[/COLOR][/SIZE]


Now go to your ubuntu menu and click on **multisync**, if its not there anywhere don't worry, just hit alt+F2 and type multisync.

Now once you have the multisync window open hit **'New...'** This will open a little window called [B]'Synchronization Pair'.
[/B]
For the '**First Plugin'** select '**Ximian Evolution 2'**, if its not an option then make sure you have installed all the necessary plugins, if its still not an option then install all the multisync plugins (i had to do this before).

Now, beside the first plugin **click options**. Here you will select which Calendar/Address Book/To-Do List you will sync, by default they should all be 'Personal', but if you have set up your own in evolution then change it to match here.

**'Second Plugin'** select **'IrMC Mobile Device'**, if its not option then see above. Click 'Options'. Make sure the Connection Type is set to **Bluetooth**.

Now make sure your phone is discoverable and click **'Search for units'**, it'll search away and eventually return the MAC address and Bluetooth channel of your mobile. Select your mobile by clicking on it and clicking OK. 

Hit '**Test connection'** to make sure. Hopefully you will get a 'Connection sucessful' message and 'Session completed' should appear on your phone.

Hit OK, and enter a '**Display Name'** in the appropriate field.

The rest of the options in the 'Synchronization Pair' dialog are your personal preference, have a look around the 'Synchronize options' and 'Filters' tabs if you want. The defaults pretty good for me.

Once you're done hit OK.


[SIZE="4"][COLOR="DarkOrange"]step 4 SYNCING[/COLOR][/SIZE]


Now select your synchronisation pair from the list and hit the **'Sync'** button on the toolbar.

The status should change from "connecting to second client" to "getting plugin changes" etc etc until it finishes and says "Press "Sync" to synchronize" again.



Open up your evolution to make sure all the details copied across, and thats it.

Any problems lets me know and I'll see what I can do. I'll tell you one thing tho' this was a hell of a lot easier than the 4 weeks I spent trying to sync my various nokias with ANYTHING....

Aeth

---

### Post by Flavian on 2006-11-22
I got one simply problem.
My laptop does not have bluetooth and if I select "cable" It can not MultiSync can not find the device, even though it is propperly connected!
Can someone help? I'd really like to sync!!

Flo
Ps: Also funny, what I just encountered, if I use the "backup" plugin as the second plugin it saves my contacts into the folder!! - So syncing is possible, just not syncing with evolution, because iRmc does not recognize a connection.

---

### Post by mosestruong on 2006-12-30
What version of multisync are you using? I'm current using 0.82 and am able to sync without problems with either cable, IR or bluetooth. Although bluetooth sometimes can be a pain with the security...

In the plugin, select IrMC Mobile Device, then click "Options", in the connection type, you can choose the method you want to connect via. For IR or Bluetooth, let Multisync search for the device. For Cable, my device is /dev/ttyACM0 - I can't remember how you find out which device it is connected as... maybe someone can help you with that.

Then for the other plugin, select Ximan Evolution 2.

---

### Post by PartisanEntity on 2007-02-16
I completely forgot that I had posted in this thread, but I came across it today while researching about syncing my phone with Evolution and I would like to thank **Aetherius** for this excellent How-To. Just tried it and it worked without any errors using my Sony Ericsson D750i and Evolution in Dapper.

---

### Post by miseryshining on 2007-02-27
wohoooo, great little howto! Got my new k550i to sync perfectly in a few minutes, thanks a 1000 times!

---

### Post by rainwalker on 2007-02-27
Could I just do the first couple of steps to connect to my computer, and transfer files over to my phone instead of syncing contacts? Because I really want to transfer some themes and ringtones over but I haven't been able to get my box to connect to my phone (Edgy on an Inspiron 8600, it has an IR port and maybe, not sure, built-in bluetooth; I doubt it though)

---

### Post by Flavian on 2007-03-02
> **mosestruong said:**
> 
For Cable, my device is /dev/ttyACM0 - I can't remember how you find out which device it is connected as... maybe someone can help you with that.


I just tried it yesterday! And it works totally fine! Thanks a lot Aetherius for the nice and easy howto and mosestruong for the right USB device name :)
It's funny though, cause the only think that hindered me from syncing was the right USB Port name... what does /dev/ttyACM0 mean btw? Can someone explain to me why /dev/ttyS0 as given by default does not work and is the wrong one?
And maybe, can someone give me a bash command that lists the CORRECT USB Ports on my laptop, so I know in the future, what to do if I want to find them out :)

Btw: Why not move / copy this into the HOWTO section?

---

### Post by rasmusbp on 2007-03-17
I'm trying to sync a SonyEricsson W810i with Evolution (with an USB cable) using the method suggested here, empoying MultiSync. But I also have problems figuring out the right device name. Maybe someone knowledgable can help? this poor noob?  : )

I've been trying the stuff mentioned here, ie

/dev/ttyACM0 
/dev/ttyACM1

I also tried the path that is mentioned (/dev/sdb1) when I connect the phone in "File transfer" mode - ie two devices are automatically mounted ("PHONE" and "PHONE CARD").

In either way, I get "No connection" when I "test connection" i MultiSync.

Alas, the phone can connect in either "file transfer" or "phone" mode - the latter does not entail that the two devices are automatically mounted. But using the SonyEricsson software in XP, it's the "phone mode" that is used for synchronizing with Outlook Express. 

Can someone please help? 

All the best
Rasmus, Copenhagen

EDIT: I installed the "Wammu" application, and it managed to connect to my phone in regular "phone mode" on /dev/ttyACM0 - on the connection "at19200" (look at the attached screendump)

---

### Post by Flavian on 2007-04-25
Can someone help me really quick. I think this is just a matter of 2 seconds.
I managed it again in my fresh Feisty install to sync with evolution, and now syncing again works flawlessly as well :) YEAH, awesome.

BUT, since I am from Austria and my mothertongue is German I have a problem with "Ö, Ä, Ü, ß" Characters!

I get weird symbols instead of the normal ones!
I took a screenshot in order for you guys to know what I mean.
The names in descending order should be:
Hans-J[COLOR="Red"]ö[/COLOR]rg
W[COLOR="Red"]ö[/COLOR]ckinger
W[COLOR="Red"]ö[/COLOR]rister
W[COLOR="Red"]ö[/COLOR]rister
W[COLOR="Red"]ö[/COLOR]rister
W[COLOR="Red"]ü[/COLOR]hrer
[COLOR="Red"]Ö[/COLOR]BB Handyticket

Before I synced I changed the charset in the IrMC plugin to **ISO8859-15** already, but I am not sure if that is the right charset for the GERMAN language and all it's special characters.

Any help to get rid of that but would be highly appreciated!

Thanks in advance
Flo

---

### Post by natuk on 2007-05-07
Does anybody know if there is a way to send more than one calendars from evolution to the phone? What if events in subscribed calendars need to be on the phone as well?

Thanks

natuk

---

### Post by PartisanEntity on 2007-05-08
> **natuk said:**
> Does anybody know if there is a way to send more than one calendars from evolution to the phone? What if events in subscribed calendars need to be on the phone as well?

Thanks

natuk

Sorry but I am not sure what you mean. What do you mean with "more than one calendar"?

---

### Post by Aetherius on 2007-05-08
Hey!

Forgot I posted a howto here! Glad I could help some people :D

@natuk: Sony Ericsson phones (in general) only support one calendar. However in multisync you can select which calendar you are syncing. So a simple little work around would be to **create multiple synchronization pairs** one for each calendar you want to sync.

Make each pair identical, except, in the "**ximian evolution 2" plugin options select different calendars**. Then in "synchronize options" for each pair, make sure to** select "Always use the entry from the first plugin"** (or second plugin is that is where the evolution plugin is).

This way your sinlge calendar on the phone will receive entries from multiple calendars on your computer.

Later ;)

---

### Post by Flavian on 2007-05-14
All of a sudden I can not sync anymore. I get the weird error:
> "Failed to get first plugin changes: Unknown error"

I've found a bug report about it, but I can't understand the reason WHY it wouldn't work anymore. I could sync and resync all the time and now i can't anymore ! :(
Can someone PLEASE HELP. This is very annyoing not being able to sync my contacts with evolution :(

---

### Post by Flavian on 2007-05-15
> **Flavian said:**
> All of a sudden I can not sync anymore. I get the weird error:


I've found a bug report about it, but I can't understand the reason WHY it wouldn't work anymore. I could sync and resync all the time and now i can't anymore ! :(
Can someone PLEASE HELP. This is very annyoing not being able to sync my contacts with evolution :(
Crap :(
Why can't anyone help... ? Google doesn't give much information!! - It seems as if a lot of people have the same problems I have, just out of the blue, but there seams to be no one with a solution for it :(
DAMN! - syncing my contacts is a very necessary thing for me... arrrrgh I AM ANNOYED.
If things like that keep to happen I will buy a Mac :( 

PLEASE HELP :/

---

### Post by XTREEM|RAGE on 2007-05-17
hmm sorry i cant help you.
but i also did the little how to for my SE W950i, but i dont really know the usb port for it(using cable). Feisty can see my SE W950i but i cant really makeup what kind of usb port it uses. Then i did this:

```
$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 0fce:d058 Sony Ericsson Mobile Communications AB 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

Some1 can help me, i'm new to ubuntu so...dont really know how to look for the usb port

---

### Post by octopuskevin on 2007-05-17
I was able to get mutlsync working with my w810i... [im on a rogers contract in canada]

i found that multisync will mess up if the phone goes into its standby mode [i.e. screen goes off etc...], in which case you need to unplug and replug the phone, and restart multisync..   the reason why is still unclear as wammu does not have this problem..

i was using /dev/ttyACM0 as the connection source...


here is my problem, i can perfectly sync from the phone to evolution without a problem...  however my evolution information does not get synced onto the phone...

wammu however is able to sync in both directions, so this must be an evolution problem...

anyone have some points, or guides to how to get evolution to set up right?
multisync configuration is set to always use first set [evolution] and i have chosen 'personal' for all the options..

cheers,

Kevin

---

### Post by nandotron on 2007-05-17
Hi Guys,

I am syncing my k750i with evolution and found this Howto very useful indeed.  I just have one problem.  I have been able to import all of my contacts into evolution from the phone and calendar entries too, but the syncing only seems to work one-way: when i sync, calendar appointments do not seem to be imported into the phone from evolution.  Any help with this would be greatly appreciated!

Nando

---

### Post by mtn on 2007-05-18
Thanks for the how to.

I got my Sony-Ericson K610i syncing perfectly butI had to do some other stuff first, see my post about this here [http://ubuntuforums.org/showpost.php?p=2675966&postcount=3](http://ubuntuforums.org/showpost.php?p=2675966&postcount=3). Then following the instructions above worked. Cheers

---

### Post by gweaver on 2007-06-29
There is a poll on Mobile Device Synchronisation here:
[http://ubuntuforums.org/showthread.php?t=484251](http://ubuntuforums.org/showthread.php?t=484251)

You may want to vote and add comments.

---

### Post by pepertje on 2007-09-12
I seem to be having the same problem as some people on here that I can get my calender from my Sony Ericsson K750i, but not on it. So it's a one way sync wich is rather unusefull since I'll be making most of my apointments in Evolution...

Can anyone help me?

---

### Post by durus on 2007-09-25
I have a strange problem. The password is accepted when i am trying to establish connection between my laptop and sonyeriksson w880i. But after that i can't connect, so i have to search for the computer again write a password, and write the password again on the computer, and the password will be accepted. But then the again i can't establish connection. Do you know whats wrong ? It seems like the computer or the phone forgets the passwords or something like that.

---

### Post by girard on 2007-09-28
should i be able to make this work with a k800i?

---

### Post by mosestruong on 2007-10-10
I found that with the latest Multisync, I need to turn off the option "Do not tell client we are synchronising" in order for the connection to succeed.

This can be turned off in Multisync, press the Edit button, in "Synchronisation Pair" window, click Options for the IrMC Mobile Device, then click on the Options tab, and Bug workarounds tab.

Hope that helps.

---

### Post by pyriX on 2007-11-30
> **nandotron said:**
> Hi Guys,

I am syncing my k750i with evolution and found this Howto very useful indeed.  I just have one problem.  I have been able to import all of my contacts into evolution from the phone and calendar entries too, but the syncing only seems to work one-way: when i sync, calendar appointments do not seem to be imported into the phone from evolution.  Any help with this would be greatly appreciated!

Nando

I had the same problem with my K610i. Solution I found was to make the first plugin the IRMC device (your phonicle), and the second one Ximian, that is, evolution.

That will successfully send data from your phone to evolution. not quite sure why this isn't a two way transfer, and I might play around with it later.. but i keep most data on my phone anywho, and I have to be at work in half an hour :p

---

### Post by fonsi2099 on 2007-12-01
I followed your advice  mosestruong, ", turn off the option "Do not tell client we are synchronising" in order for the connection to succeed.

 it works nice with my k800i, 
now my calender and contacts are been synchronized and updated with evolution.  
[INDENT][I]
"This can be turned off in Multisync, press the Edit button, in "Synchronisation Pair" window, click Options for the IrMC Mobile Device, then click on the Options tab, and Bug workarounds tab  " mosestruong, [/I][/INDENT] 

:guitar:

---

### Post by ugm6hr on 2007-12-08
I am trying to get my calendar to sync from Evolution to Sony Ericsson W810i mobile.

I run Gutsy, and have installed Multisync (multisync) with the all plugins addon (libmultisync-plugin-all) from synaptic.  Multisync0.9 seems useless, so I removed it again.

I want to use my cable (since I don't have Bluetooth on my laptop).  I set the connection for the IrMC Mobile Device (phone) as dev/ttyACM0 (as previous advice here) - which works with the cable.  The other settings are as default "None".

I picked "Personal" events calendar on Ximan Evolution 2 (Evolution / Laptop).

I have tried this both with mobile and laptop as "1st" device.  I thought this would allow me to sync in both directions with 2 clicks.

However, contacts sync OK - sort of.  My phone contacts were imported OK, but when syncing in the other direction, it didnt realise that the contacts were the same, and made second copies of every entry (on my laptop).  That's OK - I don't really need the contacts on my laptop - it was more for backup reasons.

The calendar is a different story.  I can import entries from the phone OK (altho it does put them 2 hours early on my laptop), but entries made in Evolution don't go back in the other direction.  It is this functionality that I need.

I also had a look at this: [http://www.williambrownstreet.net/wordpress/?p=27#more-27](http://www.williambrownstreet.net/wordpress/?p=27#more-27)

Any ideas?

---

### Post by eumetaxas on 2007-12-23
Hi!
I just got a **sonyericsson k800**i and i tried to sync over multisync. I do not have bluettoth on my laptop so i chose** cable**. I've chosen the right plugins in multisync, /dev/ttyACM0-1 in ports and the when i test connection it says **connection failed**. Let me tell you that kernel finds my phone under "lsusb",everything is fine in wammu,  in "file transfer" mode of the phone ubuntu recognizes the phone as a usb stick and my pda is synchronizing ok with multisync. Most posts instruct synchronizing over bluetooth - not cable. 

Thanx!

---

### Post by gmaniac on 2007-12-30
Thnx for the guide. I backed-up my w800i contacts with a cable using multisync.It worked great.

> **eumetaxas said:**
> Hi!
I've chosen the right plugins in multisync, /dev/ttyACM0-1 in ports 
Thanx!

U mean /dev/ttyACM0 not /dev/ttyACM0-1 correct?

---

### Post by olskar on 2007-12-30
Im also having troubles with syncing my K610i with cable../dev/ttyACM0 and /dev/ttyACM1 doesnt work.. I would love som help!

---

### Post by eumetaxas on 2007-12-31
> **gmaniac said:**
>  U mean /dev/ttyACM0 not /dev/ttyACM0-1 correct?

Yes. I do mean /dev/ttyACM0 and /dev/ttyACM1 not /dev/ttyACM0-1. Also firestarter is turned off.
Any ideas?
Had do boot into windows after months to import contacts to k800 and  felt terrible!
Help me so i do not have to use windows again!
thanx!

---

### Post by gmaniac on 2008-01-03
```
 cat /proc/bus/usb
```if nothing shows up ```
mount -t usbdevfs none /proc/bus/usb
```and then retry...

---

### Post by eumetaxas on 2008-01-04
thanks for answering again!
> **gmaniac said:**
> ```
 cat /proc/bus/usb
```.
returns:
**cat: /proc/bus/usb: Is a directory**

and
 ```
mount -t usbdevfs none /proc/bus/usb
```
returns:
**mount: unknown filesystem type 'usbdevfs'**

also tried usbfs. Did not return error but did nothing. In synaptic could not find a package containing 'usbdevfs'
Any ideas?
Thanx!

---

### Post by gmaniac on 2008-01-05
Wow did i really say all that crap?:confused: 
Must have been drunk or something...:)
(After you plug in your phone)

Ok first i must have meant ```
cat /proc/bus/usb/**devices** 
``` to see that is populated,** if it's not** then the **correct **comand (as you found out) is ```
sudo mount -t **usbfs** none /proc/bus/usb
```
To see if it works try to use the software or do a ```
cat /dev/ttyACM0
```it should display nothing (not even your prompt)

If it doesn't work (with usbfs still mounted) try to plug-in and out your phone one more time,
try the software and copy paste the output of the above cat and of a ```
dmesg
```.

---

### Post by eumetaxas on 2008-01-07
thanx once more! 
Connection keeps failing. Tried both ACM0 & ACM1.
after mounting and re-plugging the device
```
cat /proc/bus/usb/devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc= 15/900 us ( 2%), #Int=  3, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.22-14-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:07.2
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=045e ProdID=0040 Rev= 3.00
S:  Manufacturer=Microsoft
S:  Product=Microsoft 3-Button Mouse with IntelliEye(TM)
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=10ms

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=02(comm.) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0fce ProdID=d039 Rev= 0.00
S:  Manufacturer=Sony Ericsson
S:  Product=Sony Ericsson K800
S:  SerialNumber=3590880137764810
C:* #Ifs=10 Cfg#= 3 Atr=80 MxPwr=500mA
I:* If#= 0 Alt= 0 #EPs= 0 Cls=02(comm.) Sub=08 Prot=00 Driver=(none)
I:* If#= 1 Alt= 0 #EPs= 1 Cls=02(comm.) Sub=02 Prot=01 Driver=cdc_acm
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=16ms
I:* If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:* If#= 3 Alt= 0 #EPs= 1 Cls=02(comm.) Sub=02 Prot=01 Driver=cdc_acm
E:  Ad=84(I) Atr=03(Int.) MxPS=  16 Ivl=16ms
I:* If#= 4 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
E:  Ad=05(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=85(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:* If#= 5 Alt= 0 #EPs= 0 Cls=02(comm.) Sub=0b Prot=00 Driver=(none)
I:* If#= 6 Alt= 0 #EPs= 0 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)
I:  If#= 6 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)
E:  Ad=06(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=86(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:* If#= 7 Alt= 0 #EPs= 1 Cls=02(comm.) Sub=09 Prot=01 Driver=(none)
E:  Ad=87(I) Atr=03(Int.) MxPS=  16 Ivl=16ms
I:* If#= 8 Alt= 0 #EPs= 1 Cls=02(comm.) Sub=06 Prot=00 Driver=cdc_ether
E:  Ad=88(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 9 Alt= 0 #EPs= 0 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
I:* If#= 9 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
E:  Ad=09(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=89(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:  If#= 9 Alt= 2 #EPs= 2 Cls=0a(data ) Sub=00 Prot=ff Driver=cdc_ether
E:  Ad=09(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=89(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
```


```
cat /dev/ttyACM0
``` returns nothing, just the bar flashing. When trying edit the connection returns ATZ OK.

```
 dmesg
 [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ea400 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000137f0000 (usable)
[    0.000000]  BIOS-e820: 00000000137f0000 - 00000000137ffc00 (ACPI data)
[    0.000000]  BIOS-e820: 00000000137ffc00 - 0000000013800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 311MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 79856) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    79856
[    0.000000]   HighMem     79856 ->    79856
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    79856
[    0.000000] On node 0 totalpages: 79856
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 591 pages used for memmap
[    0.000000]   Normal zone: 75169 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7520 checksum 0
[    0.000000] ACPI: RSDP 000F7520, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 137FC6CB, 002C (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 137FFB64, 0074 (r1 COMPAQ Borg      6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 137FC6F7, 346D (r1 Compaq Wrangler  6040000 MSFT  100000B)
[    0.000000] ACPI: FACS 137FFFC0, 0040
[    0.000000] ACPI: BOOT 137FFBD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 13800000:ec7e0000)
[    0.000000] Built 1 zonelists.  Total pages: 79233
[    0.000000] Kernel command line: root=UUID=4f66b778-a55e-43b1-993e-03e2c16febbf ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0127d000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 850.119 MHz processor.
[   15.094797] Console: colour VGA+ 80x25
[   15.095693] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.097303] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.135469] Memory: 304908k/319424k available (2015k kernel code, 13860k reserved, 916k data, 364k init, 0k highmem)
[   15.135495] virtual kernel memory layout:
[   15.135498]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   15.135501]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.135505]     vmalloc : 0xd4000000 - 0xff7fe000   ( 695 MB)
[   15.135508]     lowmem  : 0xc0000000 - 0xd37f0000   ( 311 MB)
[   15.135512]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   15.135515]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   15.135519]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   15.135527] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.135617] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   15.215615] Calibrating delay using timer specific routine.. 1702.34 BogoMIPS (lpj=3404680)
[   15.215676] Security Framework v1.0.0 initialized
[   15.215695] SELinux:  Disabled at boot.
[   15.215732] Mount-cache hash table entries: 512
[   15.216011] CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   15.216036] CPU: L1 I cache: 16K, L1 D cache: 16K
[   15.216043] CPU: L2 cache: 256K
[   15.216050] CPU serial number disabled.
[   15.216056] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   15.216078] Compat vDSO mapped to ffffe000.
[   15.216109] Checking 'hlt' instruction... OK.
[   15.231875] SMP alternatives: switching to UP code
[   15.232281] Freeing SMP alternatives: 11k freed
[   15.232988] Early unpacking initramfs... done
[   16.074566] ACPI: Core revision 20070126
[   16.074906] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.077779] ACPI: setting ELCR to 0400 (from 0a00)
[   16.081870] CPU0: Intel Pentium III (Coppermine) stepping 06
[   16.081888] SMP motherboard not detected.
[   16.081895] Local APIC not detected. Using dummy APIC emulation.
[   16.082032] Brought up 1 CPUs
[   16.082458] Booting paravirtualized kernel on bare hardware
[   16.082644] Time: 22:58:52  Date: 00/07/108
[   16.082744] NET: Registered protocol family 16
[   16.083124] EISA bus registered
[   16.083163] ACPI: bus type pci registered
[   16.084873] PCI: PCI BIOS revision 2.10 entry at 0xfd83e, last bus=1
[   16.084882] PCI: Using configuration type 1
[   16.084887] Setting up standard PCI resources
[   16.088169] ACPI: EC: Look up EC in DSDT
[   16.090528] ACPI: EC: GPE=0x01, ports=0x66, 0x62
[   16.092250] ACPI: Interpreter enabled
[   16.092264] ACPI: (supports S0 S1 S4 S5)
[   16.092296] ACPI: Using PIC for interrupt routing
[   16.102668] ACPI: EC: GPE=0x01, ports=0x66, 0x62
[   16.102777] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.102796] PCI: Probing PCI hardware (bus 00)
[   16.103234] PCI quirk: region 8000-80ff claimed by vt82c586 ACPI
[   16.103245] PCI quirk: region 8080-808f claimed by vt82c686 SMB
[   16.103682] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.107486] ACPI: PCI Interrupt Link [LNKA] (IRQs *9 11 12)
[   16.107718] ACPI: PCI Interrupt Link [LNKB] (IRQs 9 *11 12)
[   16.107938] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 11 12)
[   16.108164] ACPI: PCI Interrupt Link [LNKD] (IRQs 9 *11 12)
[   16.108463] ACPI: Power Resource [PLPC] (on)
[   16.108482] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.108532] pnp: PnP ACPI init
[   16.108568] ACPI: bus type pnp registered
[   16.114536] pnp: PnP ACPI: found 11 devices
[   16.114547] ACPI: ACPI bus type pnp unregistered
[   16.114559] PnPBIOS: Disabled by ACPI PNP
[   16.114743] PCI: Using ACPI for IRQ routing
[   16.114751] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.116499] NET: Registered protocol family 8
[   16.116507] NET: Registered protocol family 20
[   16.116749] pnp: 00:05: iomem range 0x0-0x9ffff could not be reserved
[   16.116758] pnp: 00:05: iomem range 0xdc000-0xdffff has been reserved
[   16.116766] pnp: 00:05: iomem range 0xe0000-0xfffff could not be reserved
[   16.116775] pnp: 00:05: iomem range 0xfffe0000-0xffffffff could not be reserved
[   16.116792] pnp: 00:06: ioport range 0x4d0-0x4d1 has been reserved
[   16.116799] pnp: 00:06: ioport range 0x220-0x22f has been reserved
[   16.116806] pnp: 00:06: ioport range 0x388-0x38b has been reserved
[   16.116814] pnp: 00:06: ioport range 0x8000-0x808f could not be reserved
[   16.116822] pnp: 00:06: ioport range 0x9050-0x9051 has been reserved
[   16.119175] Time: tsc clocksource has been installed.
[   16.147684] PCI: Bridge: 0000:00:01.0
[   16.147689]   IO window: disabled.
[   16.147697]   MEM window: f4100000-f57fffff
[   16.147705]   PREFETCH window: 28000000-280fffff
[   16.147714] PCI: Bus 2, cardbus bridge: 0000:00:0b.0
[   16.147721]   IO window: 00001800-000018ff
[   16.147729]   IO window: 00001c00-00001cff
[   16.147736]   PREFETCH window: 20000000-23ffffff
[   16.147743]   MEM window: 24000000-27ffffff
[   16.147767] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   16.148415] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   16.148425] PCI: setting IRQ 11 as level-triggered
[   16.148434] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   16.148483] NET: Registered protocol family 2
[   16.187244] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   16.187364] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   16.188135] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   16.188897] TCP: Hash tables configured (established 16384 bind 16384)
[   16.188907] TCP reno registered
[   16.199661] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   16.875799]  it is
[   17.746922] Freeing initrd memory: 7081k freed
[   17.747400] Simple Boot Flag at 0x36 set to 0x1
[   17.748171] audit: initializing netlink socket (disabled)
[   17.748221] audit(1199746733.488:1): initialized
[   17.754689] VFS: Disk quotas dquot_6.5.1
[   17.754934] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.755319] io scheduler noop registered
[   17.755327] io scheduler anticipatory registered
[   17.755335] io scheduler deadline registered
[   17.755400] io scheduler cfq registered (default)
[   17.755441] PCI: VIA PCI bridge detected. Disabling DAC.
[   17.755450] PCI: Disabling Via external APIC routing
[   17.755493] Boot video device is 0000:01:00.0
[   17.755974] isapnp: Scanning for PnP cards...
[   18.110581] isapnp: No Plug & Play device found
[   18.192778] Real Time Clock Driver v1.12ac
[   18.193045] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.196553] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.197177] input: Macintosh mouse button emulation as /class/input/input0
[   18.197395] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   18.207600] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.207622] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.208153] mice: PS/2 mouse device common for all mice
[   18.208471] EISA: Probing bus 0 at eisa.0
[   18.208495] Cannot allocate resource for EISA slot 1
[   18.208543] Cannot allocate resource for EISA slot 8
[   18.208548] EISA: Detected 0 cards.
[   18.208849] TCP cubic registered
[   18.208900] NET: Registered protocol family 1
[   18.208982] Using IPI No-Shortcut mode
[   18.209416]   Magic number: 8:271:1007
[   18.209437]   hash matches device ttye6
[   18.209711]   hash matches device 00:09
[   18.210829] Freeing unused kernel memory: 364k freed
[   18.341083] input: AT Translated Set 2 keyboard as /class/input/input1
[   19.796920] AppArmor: AppArmor initialized<5>audit(1199746735.488:2):  type=1505 info="AppArmor initialized" pid=1161
[   19.822392] fuse init (API version 7.8)
[   19.840230] Failure registering capabilities with primary security module.
[   19.879357] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    4.756000] Marking TSC unstable due to: possible TSC halt in C2.
[    4.760000] Time: acpi_pm clocksource has been installed.
[    4.944000] ACPI: Thermal Zone [THRM] (52 C)
[    6.636000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    6.636000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    6.640000] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[    6.640000] VP_IDE: chipset revision 16
[    6.640000] VP_IDE: not 100% native mode: will probe irqs later
[    6.640000] VP_IDE: VIA vt82c686a (rev 22) IDE UDMA66 controller on pci0000:00:07.1
[    6.640000]     ide0: BM-DMA at 0x1420-0x1427, BIOS settings: hda:DMA, hdb:pio
[    6.640000]     ide1: BM-DMA at 0x1428-0x142f, BIOS settings: hdc:DMA, hdd:pio
[    6.640000] Probing IDE interface ide0...
[    6.688000] usbcore: registered new interface driver usbfs
[    6.688000] usbcore: registered new interface driver hub
[    6.688000] usbcore: registered new device driver usb
[    6.692000] USB Universal Host Controller Interface driver v3.0
[    7.076000] hda: TOSHIBA MK2017GAP, ATA DISK drive
[    7.120000] Floppy drive(s): fd0 is 1.44M
[    7.172000] FDC 0 is a post-1991 82077
[    7.748000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    7.748000] Probing IDE interface ide1...
[    8.612000] hdc: TOSHIBA DVD-ROM SD-C2502, ATAPI CD/DVD-ROM drive
[    9.300000] ide1 at 0x170-0x177,0x376 on irq 15
[    9.324000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    9.324000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    9.324000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    9.324000] uhci_hcd 0000:00:07.2: irq 11, io base 0x00001400
[    9.328000] usb usb1: configuration #1 chosen from 1 choice
[    9.328000] hub 1-0:1.0: USB hub found
[    9.328000] hub 1-0:1.0: 2 ports detected
[    9.332000] SCSI subsystem initialized
[    9.356000] libata version 2.21 loaded.
[    9.456000] hda: max request size: 128KiB
[    9.672000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    9.704000] hda: 39070080 sectors (20003 MB), CHS=38760/16/63, UDMA(33)
[    9.704000] hda: cache flushes not supported
[    9.704000]  hda: hda1 hda3 hda4
[    9.780000] hdc: ATAPI 24X DVD-ROM drive, 128kB Cache, UDMA(33)
[    9.780000] Uniform CD-ROM driver Revision: 3.20
[    9.852000] usb 1-1: configuration #1 chosen from 1 choice
[    9.984000] usbcore: registered new interface driver hiddev
[   10.000000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input2
[   10.000000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:07.2-1
[   10.000000] usbcore: registered new interface driver usbhid
[   10.000000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   10.276000] EXT3-fs: INFO: recovery required on readonly filesystem.
[   10.276000] EXT3-fs: write access will be enabled during recovery.
[   14.676000] kjournald starting.  Commit interval 5 seconds
[   14.676000] EXT3-fs: hda3: orphan cleanup on readonly fs
[   14.676000] ext3_orphan_cleanup: deleting unreferenced inode 505775
[   14.676000] EXT3-fs: hda3: 1 orphan inode deleted
[   14.676000] EXT3-fs: recovery complete.
[   14.760000] EXT3-fs: mounted filesystem with ordered data mode.
[   31.372000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   31.464000] Netfilter messages via NETLINK v0.30.
[   31.484000] nf_conntrack version 0.5.0 (2495 buckets, 19960 max)
[   36.436000] parport_pc: VIA 686A/8231 detected
[   36.436000] parport_pc: probing current configuration
[   36.436000] parport_pc: Current parallel port base: 0x378
[   36.436000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   36.536000] parport_pc: VIA parallel port: io=0x378, irq=7
[   36.776000] Linux agpgart interface v0.102 (c) Dave Jones
[   36.808000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.852000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.888000] agpgart: Detected VIA Apollo ProMedia/PLE133Ta chipset
[   36.892000] agpgart: AGP aperture is 64M @ 0xf8000000
[   37.180000] vt596_smbus 0000:00:07.4: SMBUS: Error: Host SMBus controller not enabled! - upgrade BIOS or use force=1
[   37.412000] via686a 0000:00:07.4: base address not set - upgrade BIOS or use force_addr=0xaddr
[   37.420000] Yenta: CardBus bridge found at 0000:00:0b.0 [0e11:b103]
[   37.420000] Yenta: Enabling burst memory read transactions
[   37.420000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   37.420000] Yenta: Routing CardBus interrupts to PCI
[   37.420000] Yenta TI: socket 0000:00:0b.0, mfunc 0x00001002, devctl 0x64
[   37.652000] Yenta: ISA IRQ mask 0x0018, PCI irq 11
[   37.652000] Socket status: 30000010
[   38.288000] pccard: PCMCIA card inserted into slot 0
[   38.736000] Synaptics Touchpad, model: 1, fw: 4.6, id: 0xf42a1, caps: 0x80471b/0x0
[   38.772000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   39.116000] input: PC Speaker as /class/input/input4
[   39.560000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[   39.560000] PCI: setting IRQ 9 as level-triggered
[   39.560000] ACPI: PCI Interrupt 0000:00:07.5[C] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[   39.560000] PCI: Setting latency timer of device 0000:00:07.5 to 64
[   40.108000] cs: IO port probe 0x100-0x3af: clean.
[   40.112000] cs: IO port probe 0x3e0-0x4ff: clean.
[   40.112000] cs: IO port probe 0x820-0x8ff: clean.
[   40.116000] cs: IO port probe 0xc00-0xcf7: clean.
[   40.116000] cs: IO port probe 0xa00-0xaff: clean.
[   40.116000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   40.120000] pcmcia: registering new device pcmcia0.0
[   40.484000] eth0: NE2000 (DL10022 rev 30): io 0x300, irq 3, hw_addr 00:50:BA:7B:2A:94
[   41.476000] lp0: using parport0 (interrupt-driven).
[   42.224000] EXT3 FS on hda3, internal journal
[   47.636000] ACPI: AC Adapter [ACAD] (on-line)
[   47.752000] ACPI: Battery Slot [BAT1] (battery present)
[   47.808000] No dock devices found.
[   47.932000] input: Power Button (FF) as /class/input/input5
[   47.932000] ACPI: Power Button (FF) [PWRF]
[   47.952000] input: Power Button (CM) as /class/input/input6
[   47.952000] ACPI: Power Button (CM) [PWRB]
[   47.964000] input: Sleep Button (CM) as /class/input/input7
[   47.964000] ACPI: Sleep Button (CM) [SLPB]
[   48.540000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   53.000000] NET: Registered protocol family 10
[   53.000000] lo: Disabled Privacy Extensions
[   53.752000] eth0: found link beat
[   53.752000] eth0: autonegotiation complete: 100baseT-FD selected
[   54.636000] Failure registering capabilities with primary security module.
[   56.120000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   56.120000] apm: overridden by ACPI.
[   60.308000] Bluetooth: Core ver 2.11
[   60.308000] NET: Registered protocol family 31
[   60.308000] Bluetooth: HCI device and connection manager initialized
[   60.308000] Bluetooth: HCI socket layer initialized
[   60.340000] Bluetooth: L2CAP ver 2.8
[   60.340000] Bluetooth: L2CAP socket layer initialized
[   60.372000] Bluetooth: RFCOMM socket layer initialized
[   60.372000] Bluetooth: RFCOMM TTY layer initialized
[   60.372000] Bluetooth: RFCOMM ver 1.8
[   60.688000] ppdev: user-space parallel port driver
[   61.756000] audit(1199739593.012:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5575 profile="/usr/sbin/cupsd"
[   66.348000] NET: Registered protocol family 17
[   81.724000] eth0: no IPv6 routers present
[  295.692000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[  295.952000] usb 1-2: configuration #1 chosen from 1 choice
[  297.656000] usbcore: registered new interface driver libusual
[  297.984000] Initializing USB Mass Storage driver...
[  297.992000] scsi0 : SCSI emulation for USB Mass Storage devices
[  297.992000] usb-storage: device found at 3
[  297.992000] usb-storage: waiting for device to settle before scanning
[  297.992000] usbcore: registered new interface driver usb-storage
[  297.996000] USB Mass Storage support registered.
[  303.000000] usb-storage: device scan complete
[  303.004000] scsi 0:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[  303.132000] sd 0:0:0:0: [sda] 1001472 512-byte hardware sectors (513 MB)
[  303.136000] sd 0:0:0:0: [sda] Write Protect is off
[  303.136000] sd 0:0:0:0: [sda] Mode Sense: 0b 00 00 08
[  303.136000] sd 0:0:0:0: [sda] Assuming drive cache: write through
[  303.152000] sd 0:0:0:0: [sda] 1001472 512-byte hardware sectors (513 MB)
[  303.156000] sd 0:0:0:0: [sda] Write Protect is off
[  303.156000] sd 0:0:0:0: [sda] Mode Sense: 0b 00 00 08
[  303.156000] sd 0:0:0:0: [sda] Assuming drive cache: write through
[  303.156000]  sda: sda1
[  303.164000] sd 0:0:0:0: [sda] Attached SCSI removable disk
[  303.200000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  427.004000] usb 1-2: USB disconnect, address 3
[  427.244000] usb 1-2: new full speed USB device using uhci_hcd and address 4
[  427.368000] usb 1-2: device descriptor read/64, error -71
[  440.852000] usb 1-2: new full speed USB device using uhci_hcd and address 5
[  441.020000] usb 1-2: configuration #3 chosen from 1 choice
[  441.748000] cdc_acm 1-2:3.1: ttyACM0: USB ACM device
[  441.756000] cdc_acm 1-2:3.3: ttyACM1: USB ACM device
[  441.760000] usbcore: registered new interface driver cdc_acm
[  441.760000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
[  442.576000] cdc_ether: probe of 1-2:3.8 failed with error -71
[  442.576000] usbcore: registered new interface driver cdc_ether
[  830.468000] usb 1-2: USB disconnect, address 5
[  833.732000] usb 1-2: new full speed USB device using uhci_hcd and address 6
[  833.896000] usb 1-2: configuration #3 chosen from 1 choice
[  833.904000] cdc_acm 1-2:3.1: ttyACM0: USB ACM device
[  833.908000] cdc_acm 1-2:3.3: ttyACM1: USB ACM device
[  833.924000] usb0: register 'cdc_ether' at usb-0000:00:07.2-2, CDC Ethernet Device, 02:80:37:16:03:00 
```

thanx again!

---

### Post by gmaniac on 2008-01-07
cat /proc/bus/usb/devices
...
Manufacturer=Sony Ericsson
S:  Product=Sony Ericsson K800
dmesg
....
[  833.904000] cdc_acm 1-2:3.1: ttyACM0: USB ACM device

So the kernel sees your phone just fine.
Test the connection after this and if it says failed  then maybe 
someone else has an idea...

---

### Post by eumetaxas on 2008-01-08
The kernel sees my phone. But the connection keeps failing!
I do not know if it is a general thing with usb devises on my pc. I had a similar problem with a usb bluetooth. the kernel was able to see the device but never managed to get it work. Thankfully my external drive and pda are connecting properly. 

Thanks for your help!

---

### Post by sthlmmats on 2008-01-08
My W850 does not work either. Is it possible to use Multisync on W850 with the USB cable? When I test the connection, I always get "Connection failed". I have tested Wammu without any problem to get my Calender and addressbook so I know that the USB cable is working. In both cases I connect to /dev/ttyACM0. Is it possible to get more information why the connection fails? 
Does Multisync use SyncML?

T:  Bus=02 Lev=02 Prnt=03 Port=02 Cnt=02 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=02(comm.) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0fce ProdID=d038 Rev= 0.00
S:  Manufacturer=Sony Ericsson
S:  Product=Sony Ericsson W850
S:  SerialNumber=(serial number)
C:* #Ifs=10 Cfg#= 3 Atr=80 MxPwr=500mA
I:* If#= 0 Alt= 0 #EPs= 0 Cls=02(comm.) Sub=08 Prot=00 Driver=(none)
I:* If#= 1 Alt= 0 #EPs= 1 Cls=02(comm.) Sub=02 Prot=01 Driver=cdc_acm
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=16ms
I:* If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:* If#= 3 Alt= 0 #EPs= 1 Cls=02(comm.) Sub=02 Prot=01 Driver=cdc_acm
E:  Ad=83(I) Atr=03(Int.) MxPS=  16 Ivl=16ms
I:* If#= 4 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
E:  Ad=04(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=84(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:* If#= 5 Alt= 0 #EPs= 0 Cls=02(comm.) Sub=0b Prot=00 Driver=(none)
I:* If#= 6 Alt= 0 #EPs= 0 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)
I:  If#= 6 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)
E:  Ad=05(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=85(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:* If#= 7 Alt= 0 #EPs= 1 Cls=02(comm.) Sub=09 Prot=01 Driver=(none)
E:  Ad=86(I) Atr=03(Int.) MxPS=  16 Ivl=16ms
I:* If#= 8 Alt= 0 #EPs= 1 Cls=02(comm.) Sub=06 Prot=00 Driver=cdc_ether
E:  Ad=87(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 9 Alt= 0 #EPs= 0 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
I:* If#= 9 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
E:  Ad=08(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=88(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:  If#= 9 Alt= 2 #EPs= 2 Cls=0a(data ) Sub=00 Prot=ff Driver=cdc_ether
E:  Ad=08(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=88(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms

[12163.936000] usb 2-4.3: new full speed USB device using ehci_hcd and address 6
[12164.056000] usb 2-4.3: configuration #3 chosen from 1 choice
[12164.244000] cdc_acm 2-4.3:3.1: ttyACM0: USB ACM device
[12164.252000] cdc_acm 2-4.3:3.3: ttyACM1: USB ACM device
[12164.252000] usbcore: registered new interface driver cdc_acm
[12164.252000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
[12164.296000] usb0: register 'cdc_ether' at usb-0000:00:0b.1-4.3, CDC Ethernet Device, 02:80:37:02:03:00

---

### Post by esanchez on 2008-01-09
dude you are the man!
Excellent how to..
I was able to syncrhonize my SonyEricsson W300i with Evolution in Gutsy Gibbon in
just about 5 minutes.

thanks...!! \\:D/

regards,
 -eduardo s.m.

---

### Post by strungoutfan78 on 2008-01-15
this worked absolutely flawlessly with my w580i!  thanks so much!:guitar:

---

### Post by zeusalmighty on 2008-01-21
Wow, that was soooooooo, simple!!! I though I was going to be at it for hours! Under 5 minutes and it's setup! Sony-ericsson official software takes longer to install...thanks for this great How-To!

---

### Post by eumetaxas on 2008-01-23
guess that i am the only one who didn't make it out yet!

---

### Post by hoogland on 2008-01-26
what worked for me with the K550i was using the evolution2.x and irmc-sync plugins.

when configuring the plugins make sure to add the xml version line. That made the difference for me between the evolution calendar/tasks syncing or giving an error!

$ msynctool --configure <groupname> 1

[B]<?xml version="1.0"?>
[/B]<config>
<address_path>default</address_path>
<calendar_path>default</calendar_path>
<tasks_path>default</tasks_path>
</config>

---

### Post by jamyskis on 2008-01-27
Don't worry - I'm not getting this either. I have a T650i and have tried all the steps listed here. My phone works fine with Wammu, dmesg lists my phone as an ACM device and when I enter /dev/ttyACM0 in Multisync and test the connection it at least pauses to think before saying connection failed.

> T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 18 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=02(comm.) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0fce ProdID=d073 Rev= 0.00
S:  Manufacturer=Sony Ericsson
S:  Product=Sony Ericsson T650
S:  SerialNumber=3579660126402650

Any suggestions anyone?

---

### Post by Claus7 on 2008-03-19
Hello,

same problem with k800i as well. Yet KMobileTools worked very nice when I chose the right port, ttyACM1 that was. This program is focused on transfering sms and catalogue rather than calendar and tasks. It was very nice that it worked because in Dapper wammu isn't available. 

EDIT1: I just came across this: I did exactly the same, yet I have connected my phone to a different port.
[http://ubuntuforums.org/showthread.php?t=232781&highlight=k800&page=2](http://ubuntuforums.org/showthread.php?t=232781&highlight=k800&page=2)

EDIT2: > **Flavian said:**
> ...
It's funny though, cause the only think that hindered me from syncing was the right USB Port name... what does /dev/ttyACM0 mean btw? Can someone explain to me why /dev/ttyS0 as given by default does not work and is the wrong one?...

The ttyACM# refers to the usb serial ports of one's system. The ttyACM0 refers to the first usb port and so on. A link about this is:
[http://bund.com.au/~foo/linux/mobilephone.html](http://bund.com.au/~foo/linux/mobilephone.html) 
and:
[http://www.linfo.org/serial_port.html](http://www.linfo.org/serial_port.html)
[http://www.pcmag.com/encyclopedia_term/0,2542,t=serial+port&i=51137,00.asp](http://www.pcmag.com/encyclopedia_term/0,2542,t=serial+port&i=51137,00.asp)

Regards!

---

### Post by MarilenCorciovei on 2008-03-22
I was able to syncronize my K550 using the method described [here]("http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/t630-phone-sync"), maybe it helps.

---

### Post by felipeim on 2008-03-24
GREAT!!! Thank you Aetherius.

Sony Ericsson PC Suite was the only reason why I'm still using Windows.

Now with Evolution+MultiSync I can format Windows and use only Debian (this tutorial works great on Debian Etch 4.0).

---

### Post by Orkun Sensebat on 2008-03-25
i have exactly the same problem!
how to get this done with a usb dongle? wammu works but has lots of bugs and does not support proper syncing. with usb i can sync and backup the evolution part but my mobile is being ignored(which is actually the whole deal anyway).

do i still have to use that ir plugin? i can select cable but it seems to be more like a serial cable support. how can this work with usb? i think without proper plugin it does not even try to establish a connection. i was wondering why there is no error message. come on not so many people have bluetooth - or a laptop at all.

---

### Post by Orkun Sensebat on 2008-03-25
as it seems to be "multisync" which is version 0.82 seems to support only irda, bt and serial connections(there is simply no usb plugin).

[http://www.kenny-d.com/2007/09/04/sync-sony-ericsson-w810i-to-evolution/](http://www.kenny-d.com/2007/09/04/sync-sony-ericsson-w810i-to-evolution/) perfectly describes how to connect a sony ericsson k800i or k750i via usb. the packages are simply installable via apt with hardy heron. dont get the multisyncs mixed up - you are looking for multisync0.90 - which is completely different than 0.82. i simply followed his steps with multisync0.90 - which is really just a gui to those commands he enters

add those plugins. some further hints:
- remember to be root. or make sure your usb device in /dev has proper rights(is owned by you i.e.)
- the possible connection types are 2 and 5 for bluetooth and usb.
- some further reading: [http://libsyncml.opensync.org/wiki/obex-guide](http://libsyncml.opensync.org/wiki/obex-guide)

---

### Post by stuoolong on 2008-04-24
Hi all

I have managed to sync my Sony Ericsson z610i with evolution, using multisync and bluetooth. basically using the above guide. I had to have evolution as the first device and the phone as the second, it wouldn't work the other way round.

:lolflag:

---

### Post by antid0te on 2008-04-26
Hello, this tutorial is great, but unfortunately it isn't work on my laptop sync to K800i. On IRmc device, Bluetooth option cannot be selected though it detected properly on my laptop :(

here's my dmesg: 
```

t0m@griffin:~$ dmesg | grep Blue
[   48.712503] Bluetooth: Core ver 2.11
[   48.713199] Bluetooth: HCI device and connection manager initialized
[   48.713206] Bluetooth: HCI socket layer initialized
[   48.751169] Bluetooth: L2CAP ver 2.9
[   48.751177] Bluetooth: L2CAP socket layer initialized
[   48.826276] Bluetooth: RFCOMM socket layer initialized
[   48.826297] Bluetooth: RFCOMM TTY layer initialized
[   48.826301] Bluetooth: RFCOMM ver 1.8
[10939.999897] Bluetooth: HCI USB driver ver 2.9
t0m@griffin:~$ 
```

any help? or it's just a bug?

---

### Post by pivot@pivpoint.no on 2008-06-01
Helo

I tried this multisync, and I managed to connect to my SE phone through bluetooth and the multisync. I also downloaded the backup extension for multisync, because I want a backup before I try to sync. Lots of important stuff on it now, and I've ditched windows on my laptop too now. So I have no windows, and must rely on multisync. The backup seems to work fine. It reads "Events" and then "contacts". When I look into the config of the Backup plugin it only lists all my contacts. Not my calendar items. Why is that? I've check that it's suppose to "sync" calendar too in this job.... Any suggestions?

---

### Post by pivot@pivpoint.no on 2008-06-01
Btw. The IrMc plugin is set as second (and connected with the phone), and the backup module as first plugin. backup destination also set of course...

---

### Post by pivot@pivpoint.no on 2008-06-02
ok, i now set a new event for later this evening. then tried backing up once more. this time it backed up the new event. even though there are other events both before this event and after it only backed up this one. might this be because all those events are created before i paired the computer and phone? or maybe that they contain some kind of outlook 2007 info in them, from the days i used windows (seems like ages ago, but it's actually just 1,5 weeks snce i deleted windows)

---

### Post by The Rocker on 2008-07-07
OK I'm trying this with my Sony W600i phone and I can't get Multisync to recognize my connetion via USB. :(  If I connect the phone in File Transfer mode, Hardy does detect it and shows me all the files on the phone which I can transfer all day long.  But when I try to set up the sync pair in Multisync, and I enter ttyACM0, or ACM1, or whatever... and test the connection, it fails.  What gives?  My laptop doesn't have an infrared port so this isn't an option.

---

### Post by tgyorgyi on 2008-07-18
Same for Sony Ericcson K510i - connection is only successful if I put the phone as first plugin and Evolution as second.

---

