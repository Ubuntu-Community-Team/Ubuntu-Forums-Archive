---
title: "Reading files needed to boot.. &amp; bash: command not found"
date: 2009-04-07
forum: General Help
---

### Post by LindaLou on 2009-04-07
[COLOR="Black"][COLOR="Black"]I am unable to access my laptop. The following is the scenario that preceded my difficulty.

I received a video via email (gmail). It was from a trusted "emailer" - a news report. Clicked to open (Totem)and it responded slowly. The image froze but I could hear sound. The sound was too low. I pressed the volume control and nothing happened. The image finally displayed on Totem and then froze. Video started playing but was buffering. Sound still low and then the screen went gray. I tried to do a force quite by clicking the X in Totem top right hand corner - no response. Tried using the application Force to Quit - nothing. The image continued to play, buffering and then the volume went up. 
I had Thunderbird open and my gmail via Firefox (latest version 3.0.8).  I was unable to have either program respond - I tried to close via Xing out and also doing a right click to choose Close.
I waited for the video to end and was able to close the application. The screen/Totem application was still gray.
I closed Gmail. This took  a few more seconds than normal. 
I closed TBird. This took a few more seconds than normal. 
I left the laptop for about 5 minutes. Came back and opened an OoCalc application that I wanted to work on. The document grayed out when opening. It remained this way for several seconds. I clicked the X and the Force to Quit window appeared. I clicked Force to Quit. This took several seconds to complete.
I left the laptop for 5 minutes and attempted TBird. It was very slow in opening.
I clicked on the OoCalc again and it did the exact same as previously described.
Throughout this entire time, from the video to the last attempt of the OoCalc document the hard drive light remained fully on. The system monitor showed no real peaks in the processor. Nothing out of the ordinary.
I decided to shut down the laptop and click the Shut Down. This took approximate 6 minutes to shut down. I could move the mouse pointer. When the shutdown started to "happen" it was if someone was using an erasure and slowing removing the screen, line by line, starting at the top of the screen. Every file on the desktop was disappearing, line by line. This took about 5+ minutes. 
The screen remained now, with only the Heron image and background color.
It finally shut down after another 3+ minutes.
I waited about 5 minutes and turned the laptop on.
Grub showed up and I thought I was ok.
Ubuntu screen showed up with the loading bar, sweeping the orange back and forth. Normal. However, it never stopped the back and forth motion and I knew there was trouble.
The screen went black and the following appeared:

"*Reading files needed to boot.."

This remained on the screen for approximately 15 minutes. I knew there was more trouble because on March 20, I had this [Reading files needed to boot..] and all files loaded with no problems.(no idea what caused this as the laptop and all programs were working normally.)

The hard drive light is on and steady.

The screen now says"Setting Preliminary keymap [OK]

After about 3+ minutes more information was displayed. Please note that I was unable to make note of all information that was displayed. Hopefully what I do have here will be of help and someone out there will be able to assist me in getting my laptop back in business:

[COLOR="Black"][1085.260232 atal.00:exception EMask OxO SAct OxO SErr OxO action Ox2 frozen
[1085.250306 [COLOR="DarkRed"]I was unable to note all information other than[/COLOR] DRDY frozen
*Preparing restricted Drivers [OK]
*Setting system clocks [OK]
*Starting basic Networking [OK]
*Starting kernel event manager [OK]
*Loading kernel event manager [OK]
*Loading hardware drivers [OK]
*Loading kernel module [OK]
*Setting kernel variable [OK]
*Activating Swap [OK]
*Checking root file system fsk 1.40.0 (13-Mar-2008) /dev/sda1:clean 19 blocked
*Checking file system fsck 1.40.8 (13-Mar-2008)
*[1332.331861] ata1.00:exception Emask OxO SAct OxO SErr OxO action Ox2 frozen
*[1332.331954] ata1.00:cmd e8/00:00:2f:25:67/00:00:00:00:00/e5 tag O dma 131072 in
[1332.332049]ata1.00:status: [DRY]
*Mounting local filesystems
*Activiating Swapfile swap
$Mounting securityFs on /sys/kernel/security:done 
*Loading AppArmor profiles:done
*Checking minimum space in /tmp
*Skipping firewall: ufw (not 
*Configuring network interface
*Saving VESA state
*Loading ACPI modules
*Starting ACPI services
*Starting System log daemon
*Doing Wacon setup
*Starting kernel llog daemon
*Starting System message buss dbug[/COLOR]
[COLOR="DarkRed"]I was unable to get the rest. Then the screen went black and the following appeared:
[/COLOR]
Trying to resume from /dev/disk/by-uuid/5945F9d6-f40c-4429-92e6-d380392ee037
Loading 
kinit: No resume image doing normal boot
Ubuntu 8.04.2 laptop tty1
laptop login: [COLOR="DarkRed"]here it typed my login and hit the enter key. nothing happened for several minutes. Then a bright blue screen appeared with a window with the following:[/COLOR]
"Failed to start X Server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X xerver output to diagnose the problem?" 
[COLOR="DarkRed"]There was a choice of Yes or NO. I chose Yes and the following appeared in another blue screen with white window:[/COLOR]
WARNING: Could not retrieve EDID because get-edid is not installed (1).
WARNING: Could not retrieve PCI IDs because discover is not installed (1) debconf:DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable"
[COLOR="DarkRed"]Here there was an OK and I clicked on it. A new blue screen with the white window and the following message:[/COLOR]
"The X Server is now disabled. Restart GDM when it is configured correctly."
There was an OK and I clicked on it and the screen went black with the following information:
kinit:name_to_dev_t(/dev/disk/by_uuid/5945fd6-f40c-4429-92e6-d380392ee037)-sda5(8,5)
kinit:No resume image doing normal boot...
Ubuntu 8.04.2 laptop tty1
Laptop login:here I entered my usual login name
Password:
Login timed out after 60 seconds
Ubuntu 8.04.2 laptop tty1
laptop login: here I entered my usual login name
Password: here I entered my usual password

This is the response:
Linux laptop 2.6.24-23 generic #1 SMP Mon Jan 26 01:04:16 UTC 2009 x84_64 Kernel direct mapping tables up to 100000000 @ 8000-d00
The programs included with Ubuntu system are free software: the exact distribution terms for each program are described in the individual files in /usr/share/doc/copyright
Ubunty comes with absolutely no warranty, to the extent permitted by applicable law.
To access official Ubuntu documentation please visit:[http://help.ubuntu.com](http://help.ubuntu.com)
linda@laptop:~$mygirl
bash:mygirl.command not found }[COLOR="DarkRed"](mygirl is my password)[/COLOR]

And that is where I stand. The laptop is with the black screen with the last line bash:mygirl.command not found

The hard drive light has finally stopped "glowing".

I am at a complete loss as to what has happened and what to do. I will leave my laptop on overnite as I am not sure if doing a hard shut down is the answer or not.[/COLOR]
[/COLOR] Installed with Ubuntu 8.04, 64 bit. Any info that is required that I may have left out, I'll be glad to supply if I have.

---

### Post by GeeZor on 2009-04-07
Sounds like Xserver has gone down for some reason. 
Indeed, i think you are in trouble.

consider re-installing your X server / reconfigure your X server

On Ubuntu machines, this might help editing/configuring /etc/X11/xorg.conf:
```
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg


```

Or
```

sudo dpkg-reconfigure xserver-xorg

```

might wanna try that using all the defaults and without the -phigh if the command fails..

als, you could look for old files config files. If your not comfortable with the commandline, try this:
```
sudo apt-get install mc
```
That will install Midnight Commander which will help yo through the commandline barier..
```
mc
```
and browse to the /etc/X11 folder and see if there ary any old config files left. 
xorg.conf is used by the X server, after it fails it usualy lets you u know why. If you cold post that output that would clarify a lot!

Hope this helps.

---

### Post by DeMus on 2009-04-07
It looks like you have become the victim of a virus or some other nasty stuf. I know it should be impossible because of all the safety build into the Linux system. If you were using Windows it would be 100% sure.
What else could have distroyed your system files that way?

Maybe somebody else has an idea how to bring this computer back to life.

I know re-installing is not an answer you want to hear but I would consider it. Be sure to back up your files first, all of them. Use the live cd to approach your installation and make sure you have all of your important files, inclusing the hidden one, the ones you so easy forget. (like I did once). If you have so many problems just at once, then something is terribly wrong. Did you contact the sende of the e-mail?
Btw, how did you manage to write down all what happened so accurately with a non responsive computer?
I hope you will get help soon, other than my re-install idea.

---

### Post by LindaLou on 2009-04-07
GeeZor, thanks for your response. Since I have never comes up against anything even closely related to this, I am asking you to do some clarification for me. (sob!) When you say 
> On Ubuntu machines, this might help editing/configuring /etc/X11/xorg.conf:
are you saying that I should enter code as in the terminal? If so, I am completely in the dark as to access the terminal from the current black screen telling me that the bash command is not found! 
If you would take some pity on me and provide your explanations in some more details, I would be more that grateful to give this a go.
In about 15 minutes from now, (Current time is 1943 GMT) I am heading home now as my work day is over and will be back bright and early to tackle this. As mentioned, I am going to leave the laptop on since I really don't see any other choice at this time.
I am running Ubuntu 8.04 100%. When I installed Ubuntu last year, it was to rid myself of Windows.

---

### Post by LindaLou on 2009-04-07
Thanks for the reply DeMus. I am 100% Ubuntu. No MS Windows. I guess the adrenialine was flowing and I just started power writing when I saw the computer going through it's paces. I don't think it's a virus. Must be something else. Maybe my number came up and I will have to trundle threw some Ubuntu learning the hard way, rather than just reading about it in the forum.

---

### Post by GeeZor on 2009-04-07
LindaLou, 

Try Alt-F1 through 6 to switch to your first/second/third tty (tty1-6) terminals. maybe you can login to one of those.. (although i think not since bash can't be loaded)

If your real problem is that the /bin/bash file can't be found, you really have a problem i am afraid.. if that is the case, chances are your hard drive is not "mounted(loaded as a local resource)" correctly, which indicates serious issues..
If that is the case, best thing to do is find a local "guru" since Holland is just to far away for me to come and take a look for ya ;)

Or..  sit down at try troubleshooting it your self

Restart your computer, if needed using the restart button...
When Grub comes up, try other kernels if possible.. 

If that fails,
reboot your machine...
start your normal kernel in the GRUB boot screen..
Look carefully at what happes.
If the screen goes to some graphical mode, try switching to ALT-F1 or ALT-F2 or something.. try to gather as much info as possible as to identify where things start to go wrong/report errors...

When you do manage to get a login prompt and successfully login.. 

try the mc thing i mentioned before, just to help you through the file browsing/manipulation part. it provides a "graphical interface" on the commandline for just just such needs. 

```

dmesg

```
provides the messages produces at startup and will reveal any errors (if you manage to get this far!!!)

I will check up on this in about 11/12 hours from now, when my day start bright and early..

best wishes for now!

---

### Post by LindaLou on 2009-04-08
Thanks GeeZor, for your advice. I am waiting for some feed back from a "guru". I'm 3 hours ahead so I am going to do some web and forum searching while I wait. There was a forum post a while back that was somewhat similar to my situation and the fellow resolved it. Unfortunately, I book marked the page on my lap top sooo...
I *_really_* would like to know why this happened. I have a basic Ubuntu, really. Nothing added other than TBird. And I use it for basic applications for work which include OoWord documents, OoCalc, emailing thru TBird and Gmail. I visit the same web sites - news, newsletters, Ubuntu Forum and that's it. I just don't have time to visit any other sites. 
The unfortunate part of all this is that I had scheduled to backup my documents needed for tax purposes and regrettably was not able to do this. ](*,):( Those are the only documents that I am really concerned about. All the other documents for work can be replaced, eventually, so I'm not sweating over them, not really.
So, enjoy your Spring day in Holland. :grin:(Hope that Spring is blooming there!) and I will be back on this post later on today.

---

### Post by DeMus on 2009-04-08
> **LindaLou said:**
> Thanks for the reply DeMus. I am 100% Ubuntu. No MS Windows. I guess the adrenialine was flowing and I just started power writing when I saw the computer going through it's paces. I don't think it's a virus. Must be something else. Maybe my number came up and I will have to trundle threw some Ubuntu learning the hard way, rather than just reading about it in the forum.

I know, but when you start to read your original post it sure looks like a virus attack. Happily, until now, there are no Linux viruses, so either you found the first one or you have different problems.
But it happened after you opened your friend's e-mail with the attachment? Did you contact your friend and ask him/her about it? Did it come from a Linux machine also, or does your friend still use MS? I ask this to try to find out if another Linux was damaged also by it. 
As Geezor suggested try to find a local Linux guru in Lelystad to help you. There must be somebody there in de polder.
Success.

---

### Post by DeMus on 2009-04-08
> **LindaLou said:**
> 
The unfortunate part of all this is that I had scheduled to backup my documents needed for tax purposes and regrettably was not able to do this. ](*,):( Those are the only documents that I am really concerned about. All the other documents for work can be replaced, eventually, so I'm not sweating over them, not really.

Can you boot from your live CD and copy the files over to a back-up?
This way, whatever happens, you still have your files.

---

### Post by GeeZor on 2009-04-08
Dear LindaLou,

Best thing indeed is to use a live cd to copy all your files (if the real problem is not your harddrive..)

Did you manage to make any of the tests?
and what where the results or is your machine still in the same 'state' ?

GeeZor

---

### Post by LindaLou on 2009-04-08
UPDATE:I hope that the following answers the questions from all forum members involved in my dilemma. I think I must file a bug due to the following:

Last nite I shutdown my laptop. I did so by using the on/off button (hard shutdown). I figured why not, haven't got much more to loose. The response was so quick that I was unable to note any of it other than "This Network is shutting down....." Shut down was rapid and painless. Thank goodness. I gave the laptop a pat good nite and packed it away.

This morning, on the office PC, I reviewed the posts here, searched the web for more info and awaited further info from my computer guru (3 hours behind me time wise). I was convinced that I was not up against any sort of catastrophic failure and no virus was involved.

After answering the guru's questions, basically what was I doing prior to. I turned on the laptop and the following occurred:

1.  Grub Loading Stage 1.5.... 
2.  Ubuntu loading screen appears. The loading bar sweeps back and forth and stops on the left for loading.
3.  Login Screen appears and I login.
4.  Password Screen. I enter the password.
5.  Hard driving is working away.
6.  After 3 minutes from the time Grub started loading the entire desktop appears as it was yesterday. Unbelievable!!!!
7.  The hard drive is on and steady.
8.  I'm plugged into the internet and use the Update Manager to check for updates as the office PC had some installed this morning.
9.  7 updates to install for a total of 26.8MB.
10. I click Install.
11. After 25 minutes the installs are complete.  The hard drive is glowing steady. This usually takes no time at all as we have super fast internet.
12. Some of the installs require a restart and I do so.
13. Restart complete after 7 minutes. A long time.
14. I get a Error message - see attached.  I had this error msg before when I first installed Ubuntu (nearly 1 year ago) and never had any problems with anything missing. Maybe this time will be different. I will be checking and if anything is "missing" I will add to the post.
15. I click to open FireFox. Nothing. Try again and I am told that FF is running. Hmmmm. I don't see FF - it is not in the tray or on the screen. I switch desktops back and forth and try FF again, this time with success. Sloooooooooow load.
16. Click to get into Gmail. Sloooooooooooow and the hard drive light is steady.
17. Get into Gmail and the screen goes transparent gray. After about 30 seconds it reverts back to normal. The hard drive is steady. Try to open an email and the screen goes transparent gray.
18. I force to quit. FF closes.
19. I attempt the same procedure - open FF and then gmail -  3 times in an attempt to open emails, but to no avail.
21. I open ThunderBird. Slow response but it opens.
22. I go to a OoWord document that was not being used yesterday and click to open. Slooooooooooow response. And what does open is a OoCalc document that I had worked on yesterday and saved/closed long before my problems occurred. The OoCalc documents opens after I complete the process of recovery. Strange since the document was saved with no issues yesterday.
23. Now the OoWord doc that I wanted to open, opens. It fades to transparent gray and stays that way for 10 seconds. I make a few minor typing changes  as a test and save the document. It takes about 25 seconds for a response but I am able to save the document with the minor test changes.
24. I repeat the FF attempts 3 more times and finally am able to open and respond to emails.
25. TBird working fine.



Everything is responding very slowly. Even typing. It's like Ubuntu is playing catch up with my typing speed. I type, Ubuntu doesn't enter text, I continue to type and then Ubuntu wakes up and catches up with what I have typed.

For me, I have no explanation. Not being savy on the guts of what makes computer operating systems work, I await replies to this posting as well as info from my furu.

Some back history: On Friday,March 20 I was working away on on OoCalc doc. I had FF open with 2 or 3 tabs - Gmail, Google Search page and BBC news page. I was referring to some paperwork on my desk. Out of the corner of my eye I saw the computer screen change and I turned to see the laptop shutting down. What the hell??!! It went into restart and after saying Grub loading... the screen went to "Reading files needed to boot...
And then file names and locations went scrolling down the screen. Then the Login/Password screen came up and Ubuntu loaded the desktop. Strange.
The following Monday, March 23, this occurrence repeated itself. I was in the throws of an OoWord document. FF open with nearly identical tabs open plus Ubuntu Forum.

Nothing else occurred until yesterday.

Oo has been slowing down for months. Yes, I am using the older version 2.4 and if I could find the extra time in the day to upgrade I would. FF is know to consume the processor but...I honestly don't think these attributed to the mess that I was looking at yesterday.

I have always kept my laptop up to date with whatever installs are available. ThunderBird with Lightning 0.7 addon, (have not been able to upgrade. always get the error that I can't install the upgrade 0.9 because it is not compatible with my Tbird build type Linux_x86_64-gee3), Gnucash, VLC are the only additions I have made to Ubuntu and there are not additional dependencies. I have only FoxClocks and Portuguese Language addons in FF. I clean up the cookies in FF as well as private date,browsing history, cache, cookies, etc, on a near daily basis. I don't download unnecessary documents to my computer, I surf safely selectively. 

I will contact the person that sent me the video. It is a family member who is computer savvy, uses Windows, keeps her computer as safe as MS possible (i.e. firewall, virus protection, etc) and doesn't accept or forward emails from strangers. Yes, I know, no one *intends* to forward "bad" emails so I will address this with her. 

It is all too disturbing for me and as I type this I am thinking of when the next occurrence will happen and why. That's the question I want answered - why did this happen??  In the meantime, I am heading across the street to the office supply store and purchasing some CD's and putting my near irreplacable documents on CD's.  

Waiting for you replies and thank you all for your interest and info. I know this is lengthy, but I am hoping that I am not alone out there and hopefully someone else will benefit from all of our postings.

Back in a bit with CD's:p;)

---

### Post by DeMus on 2009-04-08
Okay, the computer works terribly slow, but it is working. With that I mean everything is working? All programs?

Did you open the system monitor to see if there is a program or process which eats all the CPU power?
In the View menu of system monitor choose All processes to make sure you also see the system ones.

Sorry for not being able to help you any further. I wish I could.

---

### Post by LindaLou on 2009-04-08
DeMus,

Everything is working - programs and I have sound when I play music. When I open the system monitor it tells me that everything is sleeping and at 0% CPU usage. Weird since FF is running right now and it is showing 0%. It always says Sleeping and 0%. 

I am going to do some google searching and Ubuntu forum searching again to see if there are others who have run up against this strange occurrence.   Itis pretty disturbing and I hope to find my answer to "why".

Thanks for you support and continued inquiries.

---

### Post by LindaLou on 2009-04-09
UPDATE: Last night when I shut my laptop down it, nothing compared to before happened. Although, it took 3 minutes for the desktop to "disappear" and a took a total of 4 minutes to complete this process. A long time. The screen with Ubuntu loading bar never did appear.

This morning, start was normal but slow. 4 minutes to complete the task.
FF is not cooperating all that well, meaning that each web page, Ubuntu forum, Gmail, care2.com, Google web search page, took between 5 - 10 seconds to load and when they did the screen went transparent gray. Each web page, each viewing of emails had the hard drive running steady.  

TBird is a bit sluggish but nothing compared to FF. 

I am going to post my experience (trying to put a positive curve on this) in launchpad.

My office PC has Ubuntu 8.04 installed from the same CD I received. I ordered the CD from Ubuntu website and had it delivered via postal service. The PC is performing normally.

---

### Post by mitso on 2009-04-10
Hi LindaLou,

Have you tried the ArsTechnica.com forum ?
They have a linux branch in their forum and a group of very sharp guys. Hope they can help.

I'm still messing around with K3B.

---

### Post by LindaLou on 2009-04-10
Update:Day 3. After a useful day with the laptop I am back to square one. Today I turned it on and it was slow nearly 4 minutes to load into the desktop. Programs were sluggish - Tbird, OoCalc and System Monitor. 
FF took 3 times to open.

When I hovered my mouse of the System Monitor it said system monitor said 100% use of processor. When I looked at the All Processes only 3 were indicated as working - xorg, compiz real, and gnome system monitor. None were more than a few percentages.

The sytem became unresponsive.

I did a hard shut down after the laptop being on for over an hour.

At the time of this writing, I turned it back on and the following is occurring:

1.  Grub loading 1.5
Went to Ubuntu load window and then went black screen
2.  listing series of numbers and errors. These numbers start at 91.878484 and are at 1539.6348 and climbing
3. the descriptions are repeated and are either ata1.00:exception Emask 0x0 SAct 0X0 SErr action 0x2 frozen 
or this description  ata1.00:cmd c/8/00:08:f7:03:7e/00:00:00:00:00/e5 tag0 dma 4096 i
or this description ata1.00: statusÇ {DRDY}
chow: changing word ownership of /var/run/policykit:read-only file system
chmod: changing permission of /var/run/policykit:read-only file system
more numbers now starting at 1652.845260 and climbing
5. *saving VESA state...
*/etc/rc2.d/s05vbesave: 58:cannot create/VAR /lib/acpi-support/vbestate:Read-only file system
*OK
*loading ACPI modules...
*starting ACPI services...
acpid:can't open socket /var/run/acpid.socket:Read-only file system
*Staring system log daemon...

6. Then the screen went back to 3198.339780 ata1.0: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

7. Then:
chown Changing ownership of /var/log/mail.warn :Read-only file system
Same sentence except: /var/log/user.log :Read-only fle system
Same sentence except: /var/log/daemon.log:Read-only file system
Same sentence except: /var/log/messages :Read-only file system
Same sentence except: /var/log/debug :Read-only file system
Same sentence except: /var/log/auth.log :Read-only file system
Same sentence except: /var/log/mail.err :Read-only file system
syslog
mail.log
kern.log
1pr.log
mail.info

*Doing Wacom setup... OK
*Starting kernel log daemon...OK

chown: Changing ownership of /var/run/klogd :Read-only file system
mkmkfifo:cannot create fifo/var/run/klogd/kmsg :Read-only file system
Start-stop-daemon:unable to open pid file /var/run/klogd/kmsgpipe.pid for writing:Rread only file system (read-only file system) [failed]
starting system message bus dbus
4485.262848 ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Failed to start message bus: Failed to bind socket "/var/run/dbus/system_bus_socket" :Read-only file system
*Starting Avahi mDNS /DNS-SD Daemon avahi-daemon
4632.359800 exception Emask 0x0  (and so on as stated above)
Time out reached while waiting for return value could not receive return value from daemon process.
Failed
*Starting Common unix Printing System :cupsd
5015.387581 ata1.00: exception Emask (and so on as stated above)
cupsd: Child exited with status 1!
/etc/rc2.d/S20hotkey-setup: line 58:/var/run/hotkey-setup:Read-only file system
*Starting powernowd... OK
*Starting DHCP D-Bus daemon dhcdbd
dhcdbd; dbus_svc_init failed:org.freedesktop.Dbus.Error.FileNotFound Failed to connect to socket /var/run/dbus/system_bus_socket:No such file or directory dhcdbd Failed to initialise D-Busservice   OK *can't start hardware extraction layer-please ensure dbus is running
*Starting Bluetooth... OK
6078.672347 same as above noted
these numbers continue until it reaches 62 series ini numbers
*Starting GNOME Display Manager..

At this point an hour or so has passed and I figure with the failures displayed, I have nothing more to lose by shutting down the laptop. 

Mitso, I will check out the Ars site you mentioned. Hopefully there will be someone there with insight.

---

### Post by DeMus on 2009-04-11
Hello Linda Lou,

I'm not totally sure but:
> 2.  listing series of numbers and errors. These numbers start at 91.878484 and are at 1539.6348 and climbing
3. the descriptions are repeated and are either ata1.00:exception Emask 0x0 SAct 0X0 SErr action 0x2 frozen 
or this description  ata1.00:cmd c/8/00:08:f7:03:7e/00:00:00:00:00/e5 tag0 dma 4096 i
could indicate a bad disk.

Please have a look here:
[http://ubuntu-snippets.blogspot.com/2008/12/gsmartcontrol-hard-disk-health-checker.html]("http://ubuntu-snippets.blogspot.com/2008/12/gsmartcontrol-hard-disk-health-checker.html"), download and run the program gsmartcontrol. First do a simple test and if that results in no errors do the extended test. This will also do a surface check of your harddisk.

Should you have errors here it is obvious: you need another hard disk.
Should the test give no errors I am afraid you will have to re-install Ubuntu since all the errors you get are not normal, nor is the slow response you get from your machine. There is definitely something wrong in your installation.

I just did the simple test and after 1 minute I get no errors. Now I am running the extended test which takes a bout 2 hours (on my machine). Try it please. It takes a long time but then you know more about the status of your hard disks.

Edit: also the extended test showed no errors, which made me happy.

Good luck.

---

### Post by LindaLou on 2009-04-15
Well, from my guru analysis, it seems that the HDD is pretty much cooked. I am ordering an new, faster HDD. 
I am going to get into Recovery Mode today, just for the heck of it and see where I can go. Will post any findings.
Thanks to all for the input. Greatly appreciated.:p

---

### Post by LindaLou on 2009-05-08
3 weeks later! Ugghhh.  Apparently, the HDD is fine. It is the connection of the HDD to the motherboard. While awaiting the technician to show up, the laptop is have a good cleaning.  When will I have it back on my lap? hoping for next week.  I'll post here when I do have the laptop back.  Ahhhhhh Brasil!

---

### Post by LindaLou on 2009-05-13
UPDATE: Well, my laptop is back in my hands, with the original HDD and motherboard. That's fine.  

I'm a bit perplexed: I have Windows XP. Strange. No Ubuntu. The HP tech said that the Hard Drive was restored to factory specs. 

I'm curious as to how this is possible since I did not partition Ubuntu when I installed it, nearly a  year ago.  I chose to wipe Windows out completely.

I will be installing Ubuntu this afternoon. With all the updates that have been applied over the past year, I'm not looking forward to the time involved, even with great high speed internet.  Thinking of doing the updates in parcels.

If anyone has ever experienced this scenario - Have the HDD restored to Windows - I would like to hear about it.  

I will update this when I have the laptop back with Ubuntu.

Thanks for all the tips, advise and consultations along the way.:)

---

### Post by dandnsmith on 2009-05-13
They obviously restored using an image of the HDD as originally supplied - whether this is done using a 'hidden partition', or the image is held elsewhere is really immaterial.
It is a standard technique, used by the tech support, who don't want to 'waste time' sorting out an unknown situation.

BTW would you know if they had swapped in a new HDD?

---

### Post by LindaLou on 2009-05-27
Without going into a rant regarding the country men/service of where I am living, suffice it to say that I have once again been recognized as a foreigner.

My laptop has indeed the original HDD. Because I know have Windows XP Basic installed(never heard of this Basic before I moved here), I used Belarc, downloaded the application and it showed the HDD the identification numbers/letters matched the previous Belarc diagnosis of 2 years ago. 

I do not have any of the XP CDs that came with my laptop.  When I installed Ubuntu last year I was so thrilled to be rid of MS I did a cleansing and threw all of them in the trash.  

The "tech", and I use this term loosely, was in deed not interested in wasting his time, as  you so rightly stated dandnsmith. On the bottom of the laptop is a MS sticker with the MS code.  This gets the install of Windows that was originally installed on the laptop. In my case I now have Windows XP Basic - NOT what I had orignially. I had Win XP Home loaded, as per normal in North America.  

But that isn't the point because if there was no problem with the HDD why wipe it and put on XP?  The tech said the problem was with the connection of the HDD to the motherboard. In this case, with the proper repair, the laptop should have fired up with Ubuntu and the HDD would not have Win XP Basic installed.

Long story shortened, I miss home!! and I'm upgrading to Win XP Pro and partition the HDD for Ubuntu 8.04.  I am partitioning this time around with Ubuntu because there are 3 applications that I require with MS OP for business.  I tried and tried to find replacements or to simply live without or work around these programs but it was rather difficult this past year.  And, I never did get my wireless working - never was able to hook up with the neighbors free wireless zone.

My thanks to all of you that participated in this event of mine and for all your help, and input!! The Ubuntu forum/community is by far the most welcoming and helpful I have ever been involved with!!!  My hat off to all!!  =D> I'm sure I will be posting for help will I set up my laptop with Ubuntu, again! 

Kind Regards.

---

