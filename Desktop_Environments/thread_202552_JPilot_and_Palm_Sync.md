---
title: "JPilot and Palm Sync"
date: 2006-06-23
forum: Desktop Environments
---

### Post by carl13 on 2006-06-23
From what I have read, syncing in dapper can be tricky. However, I am just trying to sync my PalmOne Zire31 with JPilot. From what I have read, JPilot is working for others. 

Under preferences - settings - I have tried setting the port as /dev/ttyUSB1 and /dev/ttyUSB0. However neither work. When I hit snyc on my Palm and sync on the sync button in JPilot, nothing happens and my Palm will eventually time out. 

I have made sure that gnome pilot is not running when I try this.  

Is there anything else that I can try differently?

---

### Post by Paerez on 2006-06-23
I have it set to /dev/pilot and I think I also had to add some palm pilot udev rules. Google for palm pilot udev to get it to set the palm to /dev/pilot. The only trick I have to sync mine is I have to press the palm's sync button BEFORE jpilot's button.

---

### Post by carl13 on 2006-06-23
thanks for the reply but I am still stuck

here is what i have done:

created this file : /etc/udev/rules.d/10-custom.rules

added this rule : BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"

made sure to hit my pilot's hot sync before the jpilot hotsync

tried using /dev/pilot, /dev/ttyUSB0, and /dev/ttyUSB1 in jpilot settings

here is my dmesg output:

[17179658.080000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179658.308000] usbcore: registered new driver usbserial
[17179658.308000] drivers/usb/serial/usb-serial.c: USB Serial support registered  for generic
[17179658.308000] usbcore: registered new driver usbserial_generic
[17179658.308000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[17179658.308000] drivers/usb/serial/usb-serial.c: USB Serial support registered  for Handspring Visor / Palm OS
[17179658.308000] drivers/usb/serial/usb-serial.c: USB Serial support registered  for Sony Clie 3.5
[17179658.312000] drivers/usb/serial/usb-serial.c: USB Serial support registered  for Sony Clie 5.0
[17179658.312000] visor 1-1:1.0: Handspring Visor / Palm OS converter detected
[17179658.312000] usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
[17179658.312000] usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB1
[17179658.312000] usbcore: registered new driver visor
[17179658.312000] drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS dri ver
[17179659.100000] usb 1-1: USB disconnect, address 2
[17179659.100000] visor ttyUSB0: Handspring Visor / Palm OS converter now discon nected from ttyUSB0
[17179659.100000] visor ttyUSB1: Handspring Visor / Palm OS converter now discon nected from ttyUSB1
[17179659.100000] visor 1-1:1.0: device disconnected
[17179660.096000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[17179660.240000] visor 1-1:1.0: Handspring Visor / Palm OS converter detected
[17179660.240000] usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
[17179660.240000] usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB1
[17179670.724000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).

](*,)

---

### Post by carl13 on 2006-06-24
Does anyone know what I can do or try from here?

---

### Post by carl13 on 2006-06-24
here is the output form when i try to sync with my palm

pi_bind error: /dev/ttyUSB1 No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND

---

### Post by newman on 2006-06-24
I have a Zire71 that I had similar issues with.  I finally did a clean install of ubuntu and all updates, and installed J-Pilot via Synaptic. I left all the default settings alone in J-Pilot.  Then I went to System/Preferences/Removable Drives and Media > PDA's Tab > and checked the box  "Sync Palm devices when connected."  
I now just press the sync button on the Palm cradle first, then I launch J-Pilot and select the sync button (Ctrl-Y).  This seems to work for me.

---

### Post by harnadem on 2006-06-25
[QUOTE=carl13]here is the output form when i try to sync with my palm

pi_bind error: /dev/ttyUSB1 No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND[/QUOTE]

That is the message I receive when I start the sync on jpilot before starting it on my Palm device.  I also had to change the sync rate to 57,600 on both, the palm device and in jpilot.  Then, I start hotsync on my palm device, followed by starting it on jpilot.  The message I receive is that jpilot is doing a slow sync - but it does sync the information correctly.  Now if I can just find a way to make the jpilot calendar show time bars ... :D

---

### Post by pito on 2006-06-28
I had BIG problems to synchronize TE2 after I updated to Draper.

I managed it to synch with pilot-xfer only three times out of maybe hundreds. 
I tried different tricks, nothing helped.

But...after rumors that kernel 2.6.15 is broken regardin udev and usb stuff.

What I did today was that I switched back the kernel from Version 2.6.15 to 2.6.12, and the sync works every time both from command line,pilot-xfer, and via jpilot.

I recovered the old archived manu.lst~ from Breeze and rebooted the OS.
Then I ran "sudo modprobe visor" and I am back in the bussines.

There are unconfirmed infos that the new kernel for Draper 2.6.17 work perfect as well.

Hope it will help others.

/piotr

---

### Post by Paerez on 2006-06-29
OK so last night I got my Z22 to sync with jpilot.

I pretty much just installed jpilot (no udev rules). Then I pointed it to /dev/ttyUSB1. Then I pushed sync on the PALM, waited 1 second, pushed sync on jpilot, and it failed. Then I kept clicking jpilot's sync once per 1.5s or so, and after about two tries my palm made a click noise and started syncing!

So press the palm button, then just keep clicking jpilot's sync button until it goes. It may take 20s, but mine usually gets it within 1-3 tries.

---

### Post by dannemil on 2006-07-13
> **Paerez said:**
> OK so last night I got my Z22 to sync with jpilot.

I pretty much just installed jpilot (no udev rules). Then I pointed it to /dev/ttyUSB1. Then I pushed sync on the PALM, waited 1 second, pushed sync on jpilot, and it failed. Then I kept clicking jpilot's sync once per 1.5s or so, and after about two tries my palm made a click noise and started syncing!

So press the palm button, then just keep clicking jpilot's sync button until it goes. It may take 20s, but mine usually gets it within 1-3 tries.


Yes, that is what happens with mine as well - it will sync after semmingly random numbers of attempts. This is pretty silly - it should just work without us having to jump through hoops like this.:mad:

---

### Post by Paerez on 2006-07-13
I have no clue how I did it, but I got it to sync with evolution, twice. I tried about 10 times since then, but no dice. If you think jpilot was random, evolution was REALLY random. But when I did get it, it was pretty sweet. But now it doesn't work...

I set it to the same as jpilot, and I had to keep killing gnome-pilot.

---

### Post by Pragmatist on 2006-07-17
I'm using a Zire 72 and have it working consistently.  Here is what I do:

1. I use **jpilot** (although I also got it to work with evolution)

2. **_Always_ click HotSync on the Palm _*before*_ clicking in jpilot**

Note: I don't have a cradle, I just use the hotsync program on the Palm. You might want to try this instead of the cradle, at least for testing.

     Note2: This issue of when to press sync is not unique to jpilot.  I used jpilot, the pilot-xfer utility of the pilot suite of programs, and evolution, and the same principle applied.  First press hotsync on the palm, and only then for the program your using to sync with the palm.

3. Make a persistent device node corresponding to your palm.  The key here is to make a "udev" rule.  If you do a search for udev on the forums here, you'll find lots of helpful stuff.  Here is a link I used:

[http://www.ubuntuforums.org/showthread.php?t=168221&highlight=udev](http://www.ubuntuforums.org/showthread.php?t=168221&highlight=udev)

Specifically, here is what I did:

NOTE: This worked for me.  You should follow the steps in the above link.  In particular, you need to run the program **udevinfo** to find out the specifics of your device.  Your SYSFS{product} may not equal "Palm Handheld", for instance.

I typed this in, using an editor (the line staring with BUS is all one line):
> 
# My Zire 72 Palm Pilot

BUS=="usb", SYSFS{product}=="Palm Handheld", KERNEL=="ttyUSB1", NAME="zire72", SYMLINK="usbdevices/zire72" 

I saved this file as **/etc/udev/rules.d/10-local.rules**

The line beginning with # is just a comment and you can put anything here that will be a useful reminder.  In general, you would use this file to put other rules as  necessary.   So, the comment helps to keep the file organized and easy to read.

Then, following the instructions in the above link, I restarted udev so it would register what I did:
```
 sudo /etc/init.d/udev restart
``` 
Then, I went into jpilot and chose **File-->Preferences-->Settings** and set my serial port to:  **/dev/zire72**  and left my serial rate at 57600 (note, according to jpilot, for USB the rate setting doesn't matter).

And thats it!  Now, every time you connect your Palm, the udev rule allows your computer to recognize the Palm and assign it the same device node every time.  Consequently, your settings in jpilot always work.

Good luck and please give feedback especially if it works for you.

---

### Post by Paerez on 2006-07-17
I came up with a simpler way that works with evolution consistently:
[http://www.ubuntuforums.org/showthread.php?t=215644](http://www.ubuntuforums.org/showthread.php?t=215644)
hopefully it works and its not just my luck.

---

### Post by carl13 on 2006-07-22
thanks for all of the replies and help. however, I still can not sync my palm zire 31 with anything in ubuntu. i am not sure why some people can get their palm to sync while others including myself can not. i have followed many suggestions from various posts and nothing has worked. this is very frustrating because at this point i guess i will start booting windows to sync. obviously this is not the end of the world but on the other hand it is not convenient. being able to sync a palm pilot should not take this much effort and in my opinion should work the same or better in ubuntu than it does in windows. ](*,)

---

### Post by palmdoc on 2006-07-22
Well I am also one of those who can't. Still on Windoze till this is fixed...](*,)

---

### Post by Pragmatist on 2006-07-22
It's true, it can be frustrating.  Have you read the wiki devoted entirely to syncing the Zire 31?

[https://help.ubuntu.com/community/PalmZire31HowTo](https://help.ubuntu.com/community/PalmZire31HowTo)

If not, then give that a try.  Either way, we'll be happy to walk you through the different steps and troubleshoot where necessary.

Please do the following:
1.) Open a terminal and type this command in: 
```
**tail  -f  /var/log/messages** 
``` 
2.) Then plug in your Zire

3.) Then paste the contents of your terminal here (If it is too big, you can include it as an attachment.)

---

### Post by carl13 on 2006-07-23
> **Pragmatist said:**
> It's true, it can be frustrating.  Have you read the wiki devoted entirely to syncing the Zire 31?

[https://help.ubuntu.com/community/PalmZire31HowTo](https://help.ubuntu.com/community/PalmZire31HowTo)

If not, then give that a try.  Either way, we'll be happy to walk you through the different steps and troubleshoot where necessary.

Please do the following:
1.) Open a terminal and type this command in: 
```
**tail  -f  /var/log/messages** 
``` 
2.) Then plug in your Zire

3.) Then paste the contents of your terminal here (If it is too big, you can include it as an attachment.)

thanks for your reply and willingness help

here is my output from typing the above command

Jul 23 22:22:40 bbox kernel: [17179976.932000] usb 1-2: new full speed USB device using uhci_hcd and address 6
Jul 23 22:22:40 bbox kernel: [17179977.076000] visor 1-2:1.0: Handspring Visor / Palm OS converter detected
Jul 23 22:22:40 bbox kernel: [17179977.076000] usb 1-2: Handspring Visor / Palm OS converter now attached to ttyUSB0
Jul 23 22:22:40 bbox kernel: [17179977.076000] usb 1-2: Handspring Visor / Palm OS converter now attached to ttyUSB1

---

### Post by timczer on 2006-07-23
I have a Sony clie, and I sync with J-pilot without having to do anything extra.  I have serial port set to /dev/ttyUSB0.  I don't have to use any udev rules.  I use a direct cable connection, not a cradle.  I start the sync from j-pilot first, and when it says to hit the sync button on the palm, I do so and it syncs.  

Maybe try doing it that way.  Hit sync in j-pilot first, when it says hit sync button on palm, do that and see what happens.

---

### Post by Pragmatist on 2006-07-24
> **carl13 said:**
> thanks for your reply and willingness help

here is my output from typing the above command

Jul 23 22:22:40 bbox kernel: [17179976.932000] usb 1-2: new full speed USB device using uhci_hcd and address 6
Jul 23 22:22:40 bbox kernel: [17179977.076000] visor 1-2:1.0: Handspring Visor / Palm OS converter detected
Jul 23 22:22:40 bbox kernel: [17179977.076000] usb 1-2: Handspring Visor / Palm OS converter now attached to ttyUSB0
Jul 23 22:22:40 bbox kernel: [17179977.076000] usb 1-2: Handspring Visor / Palm OS converter now attached to ttyUSB1

Well, just to state the obvious, your system is seeing a Palm device :)

For testing purposes, please install the **pilot-link** package.
 Use  **synaptic **to install it. You can get into synaptic by:
Using menus: System-->Administration-->Synaptic Package Manager
Or, using a terminal just type: synaptic

Once in synaptic use the search feature to find the pilot-link package.
Then click the box to the left of the package and select "Mark for Installation".  Then click the Apply button.

Then, go to a terminal and follow the steps in the previous post and note the device file.  In your last post the file was:

>  Jul 23 22:22:40 bbox kernel: [17179977.076000] usb 1-2: Handspring Visor / Palm OS converter now attached to ttyUSB0
Jul 23 22:22:40 bbox kernel: [17179977.076000] usb 1-2: Handspring Visor / Palm OS converter now attached to **ttyUSB1** 
Note that there are two files mentioned: ttyUSB0 and ttyUSB1.  Always take the higher numbered file, in this case ttyUSB1 (it will also invariably be odd; ttyUSB1, ttyUSB3, ttyUSB5, etc...)

Then, go into a terminal and type this (but ***don't hit enter***):

```
pilot-xfer -p /dev/ttyUSB1 -l
``` 
Note: I'm using /dev/ttyUSB1  but you should use whatever you find in the previous step.  (Also, **-l**  is a dash followed by a lower-case L  which stands for list).

The above command (which is mainly used for transfering info to and from a Palm Pilot) does the following:

-l  lists the information only (no transfering)
-p  tells pilot-xfer which port (device file) your Palm Pilot is on.

Now, press **Hotsync** on your palm (use the program in the palm, not the cradle button).

Finally, hit **Enter** and you should see your computer recognizing, and listing information from, your Zire 31 !!!

Summary:
1.) Use tail -f /var/log/messages to discover the device file assigned to your Zire

2.) Run hotsync on your Zire

3.) Run the pilot-xfer program in a terminal to list info on your Zire using this invocation (pilot-xfer -p /dev/[I]your-device-filename -l)

[/I]You won't have to do this each time.  We are only doing this now for testing purposes.

---

### Post by jethro10 on 2006-07-24
I too have no problems BUT have to press the cradle button first. aparently this create the device in the file system for the Jpilot to see. So I do cradle (to activate the port)->click SYNC on Jpilot  (seems to get it to try to sync)-> Press cradle again (now it all goes ok).

I wonder if this was your original problem and all this messing around has made it worse.

Jeff

---

### Post by carl13 on 2006-07-24
> **Pragmatist said:**
> 
Summary:
1.) Use tail -f /var/log/messages to discover the device file assigned to your Zire

2.) Run hotsync on your Zire

3.) Run the pilot-xfer program in a terminal to list info on your Zire using this invocation (pilot-xfer -p /dev/[I]your-device-filename -l)

[/I]You won't have to do this each time.  We are only doing this now for testing purposes.

here is my output:

carl@bbox:~$ pilot-xfer -p /dev/ttyUSB1 -l

   The device /dev/ttyUSB1 does not exist..
   Possible solution:

        mknod /dev/ttyUSB1 c <major> <minor>

   Unable to bind to port: /dev/ttyUSB1
   Please use --help for more information

_______________________

not sure what is going on here
one command (tail -f /var/log/messages) will recognize that my palm is there but the other (pilot-xfer -p /dev/ttyUSB1 -l) will not

i googled that above error message and came accross this [ link]("http://www.die.net/doc/linux/HOWTO/mini/Handspring-Visor-2.html") which seemed to address a similar issue

---

### Post by Pragmatist on 2006-07-25
> **carl13 said:**
> here is my output:

carl@bbox:~$ pilot-xfer -p /dev/ttyUSB1 -l

   The device /dev/ttyUSB1 does not exist..
   Possible solution:

        mknod /dev/ttyUSB1 c <major> <minor>

   Unable to bind to port: /dev/ttyUSB1
   Please use --help for more information

Did you press hotsync on your Zire before running the pilot-xfer command?

If so, then try this:

When your in the terminal and you've run **tail -f /var/log/messages **you see that your computer is recognizing it as /dev/ttyUSB1

Keep this terminal window open and open another (hint: if your using gnome-terminal, you can just press CTRL-SHIFT-T)

Use this new window to type in the above pilot-xfer command, but make sure that the first terminal window (running the tail -f command) states that your Zire is connected.  

To see what is going on, watch the terminal and turn off your zire.  Then turn on your zire.  You should see that /var/log/messages states that it is disconnected when you turn off the zire and that it is connected at ttyUSB1 when you turn it back on.

If your zire is disconnected then the error message you got is normal (it doesn't see the device anymore because it is "disconnected").  Note: even though your USB cable still "connects" the device, the Zire will still register as disconnected if it is turned off, or sometimes if you just started and then stopped a hotsync.)

The purpose of using the pilot-xfer utility is just to demonstrate to you that Linux can sync with your Zire.  Also, it is a good way to understand what is going on without getting caught up in individual programs like evolution and jpilot and kpilot etc...etc...

Once this works, we'll move onto getting you setup with whatever program you want to use.

---

### Post by carl13 on 2006-07-25
> **Pragmatist said:**
> 
If your zire is disconnected then the error message you got is normal (it doesn't see the device anymore because it is "disconnected").  Note: even though your USB cable still "connects" the device, the Zire will still register as disconnected if it is turned off, or sometimes if you just started and then stopped a hotsync.)


I used "tail -f /var/log/messages" and it showed that my palm was connected. I even turned it off and it showed that it was disconnected and then turned it back on and it showed that it was connected. In a seperate terminal window, i hit hot sync (while still showing connected in the first terminal window) then used "pilot-xfer -p /dev/ttyUSB1 -l" and got the same message as before. :confused: It does not make sense because my palm is connected but for some reason software like pilot-xfer is not able to detect it.

---

### Post by Pragmatist on 2006-07-25
> **carl13 said:**
> I used "tail -f /var/log/messages" and it showed that my palm was connected. I even turned it off and it showed that it was disconnected and then turned it back on and it showed that it was connected. In a seperate terminal window, i hit hot sync (while still showing connected in the first terminal window) then used "pilot-xfer -p /dev/ttyUSB1 -l" and got the same message as before. :confused: It does not make sense because my palm is connected but for some reason software like pilot-xfer is not able to detect it.

Great!  So, you can see your device connecting and disconnecting.  When I used pilot-xfer  not 5 minutes ago, I had the same error message as you did.  However, it usually work when you run the program a second time.

There is no doubt in my mind that you will get pilot-xfer to work.  There is this annoying timing issue though.  Here is the basic principle:

[I][B]Always hit hotsync on the palm _first_!

[/B][/I]After that, you may need to run pilot-xfer more than one time in succession.  This also applies with jpilot.  Sometimes I have to press jpilot's hotsync button twice.

So, the order is:
1.) Press hotsync on Palm
2.) Press hotsync in software (or run pilot-xfer)
3.) Press hotsync in software a second time (or run-pilot-xfer a second time)

One more crucial point:  Make sure that the gpilot daemon (gpilotd) is NOT running.  the gpilot software is the default on Ubuntu.  However, I find that it is spotty (although if your dead set on using your zire with evolution, then, as far as I know, you'll need to work with gpilotd). Many people prefer jpilot anyway.

To check if gpilot is running, do this:
```
ps -ef |grep gpilot
``` 
If you get anything (other than the one line showing your running the grep command), then you need to kill it.  Here is how:
```
sudo kill *<processID>*
``` 
For example, lets say you get this (note, I'm making this example up):
> username   **23059** 12964  0 19:48 pts/0    00:00:00 gpilotd To kill this made up example, you'd type this:
```
sudo kill -9 23059
``` 
Note, the process id is the first number (in bold in the example above).  There are other ways to kill processes (the killall command, or the above command without sudo and/or without the -9).  However, the one I'm giving you should always work.

Finally, if you really want to avoid gpilot, just use synaptic to find the gpilot packages (I think there are two) and uninstall them. You can always reinstall them later.

---

### Post by cafonso on 2006-09-20
> **newman said:**
> I have a Zire71 that I had similar issues with.  I finally did a clean install of ubuntu and all updates, and installed J-Pilot via Synaptic. I left all the default settings alone in J-Pilot.  Then I went to System/Preferences/Removable Drives and Media > PDA's Tab > and checked the box  "Sync Palm devices when connected."  
I now just press the sync button on the Palm cradle first, then I launch J-Pilot and select the sync button (Ctrl-Y).  This seems to work for me.

Using dapper with latest updates to date. I just apt-get-installed jpilot and did what newman did, using a Tungsten E. Works fine.

---

### Post by tute666 on 2006-11-21
> **Paerez said:**
> I have it set to /dev/pilot and I think I also had to add some palm pilot udev rules. Google for palm pilot udev to get it to set the palm to /dev/pilot. The only trick I have to sync mine is I have to press the palm's sync button BEFORE jpilot's button.

good god man.  it works, let me bear your children!
finally it works.  this has been quite vexing, worst part of my ubuntu experience.

Also, i believe that replacing pilot-link with coldsync resolves the problem of jpilot not recognising the /dev/pilot link

---

### Post by jlh on 2006-12-03
I run Dapper, and have jpilot installed to sync with my Treo 650.  I find the sync process totally unpredictable.  Some times it works like a charm, and that may continue for a couple weeks.  Other times, it is totally useless; no sync, and I can't tell why not.  Some times a reboot of the computer straightens everything out.  Some times a soft reset of the Treo fixes things. 

I have no idea what accounts for this.  Can anyone suggest how to troubleshoot jpilot and a Treo.   It's very frustrating not knowing whether I'll be able to sync - or not.  

I ran jpilot on Suse 9.3 with much more consistency than I have in Dapper.

---

### Post by jfl on 2006-12-05
Just started to try Palm syncing on Dapper; didn't get very far yet, but I found something strange (for me).
When I start Jpilot and try to sync, I loose my network connection !!!??? It is a wired ethernet... 

JF

---

### Post by megamania on 2006-12-06
> **jfl said:**
> Just started to try Palm syncing on Dapper; didn't get very far yet, but I found something strange (for me).
When I start Jpilot and try to sync, I loose my network connection !!!??? It is a wired ethernet... 

I know that Dapper is LTS, but it is known to have problems with Palm syncing.

If you can upgrade to Edgy, in my opinion that's the easiest thing to do in order to have functional palm syncing.

---

### Post by jonrkc on 2007-01-20
Using Dapper 6.06, no trouble till sometime after Dec. 28 (my last sync).  Couldn't get it to work and spent two hours last night and one this morning searching for answers.  Finally found that by repeatedly pushing the device sync button and then the JPilot button it eventually worked.  It must be an issue with timing.  Wait too long: nothing.  Press too soon: nothing.  Exactly right timing: it works.

This was not the case last month, when it had been working perfectly on the first try for several months at least.  But at least this is a way I found to make it work, although it's time-consuming and may cause swearing (at least here).

---

### Post by jlh on 2007-01-20
I find the same thing.  Click the Treo.  Pause a second - or so.  Click on jPilot.  Click the Treo again.  Maybe it works fine.  Too little or too much time between the sequence of clicks, and nothing happens.

I also seem to have better success if I sync right after I boot, before I've launched a lot of other applications.

Sometimes, however, nothing helps.  I just can't sync, even if I try to adjust the pause after the first Treo click.  I shut down the computer, and try again the next day, right after the boot. Usually that works.

All-in-all, frustrating.  Not ready for prime time.  SuSe was much better on this than Ubuntu.

---

### Post by fdimmling on 2007-01-21
I had problems to sync my Palm Tungsten E with Jpilot in the early days of dapper too. The following solved it permanently:

I created a file 10-visor.rules in /etc/udev/rules.d containing only the line

BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", MODE="666", SYMLINK="pilot", RUN="/bin/su - fd -c '/usr/bin/jpilot -s'"

You have to replace the fd in the RUN=... entry by your own user id!!!

To sync start jpilot first, then connect the Palm and press the Sync (Star) Button on your Palm. Syncing starts. It works reliably for more than half a year now.

Friedrich

---

### Post by jlh on 2007-01-21
fdimmling,

I'm not exactly a newbie, but I'm not geeky either.  So, I have a couple probably dumb questions:

1.  I'm syncing a Treo 650.  Do I have to change "Palm Handheld*" to something else?

2.  Where to I get the "user id" that I substitute for "fd"?

Thanks.

---

### Post by fdimmling on 2007-01-22
> **jlh said:**
> fdimmling,

I'm not exactly a newbie, but I'm not geeky either.  So, I have a couple probably dumb questions:

1.  I'm syncing a Treo 650.  Do I have to change "Palm Handheld*" to something else?

2.  Where to I get the "user id" that I substitute for "fd"?

Thanks.


Hi, AFAIK there are no dumb questions,

there should be no need to adapt the "Palm Handheld*" entry. The user id is your login name, that is what you type in to log into your system, it is also the name of your home directory, i.e. my home directory is /home/fd . In a terminal window you get it by typing

cd
pwd

You have to create the file as root, otherwise you are not allowed to write it into /etc/udev/rules.d. To create it you have to open a terminal and type 

sudo gedit /etc/udev/rules.d/10-visor.rules

Good luck

Friedrich

---

### Post by jlh on 2007-01-22
Ok.  That I understand.  A couple more questions:

1.  I substitute my computer user login name even though the Treo itself uses a slightly different name when it syncs?  In other words, I don't worry about the name used in the sync?

2.  Is there a space after the "-" that precedes "fd"?  But not, say, before "s"?

Thanks again.

---

### Post by fdimmling on 2007-01-22
> **jlh said:**
> Ok.  That I understand.  A couple more questions:

1.  I substitute my computer user login name even though the Treo itself uses a slightly different name when it syncs?  In other words, I don't worry about the name used in the sync?

2.  Is there a space after the "-" that precedes "fd"?  But not, say, before "s"?


Absolutely correct. "su - fd" means: execute the following command as user fd, while -s is the option "sync" passed to jpilot. The user name on the Treo does not matter in this context, it will be cared for in the dialog between Palm and JPilot after establishing the connection. 
BTW you have to set the device for syncing in the JPilot preferences to /dev/pilot. The udev rule is triggered as soon as a Palm device is seen by the kernel, it maps the chosen USB device to /dev/pilot and starts the syncing process of jpilot.

Friedrich

---

### Post by carl13 on 2007-01-22
I started this thread and finally gave up on getting my palm to sync. I have not used Linux for quite some time since and just recently installed Edgy. I then installed JPilot, clicked sync on my Palm, and then clicked sync on JPilot, and it worked!

---

### Post by pennygov on 2007-01-24
Thank you fdimling - your suggestion to create the rules file actually worked!!!

I had posted a new thread earlier today for help because I had tried everything except that to no avail. I didn't have much hope left but made the file and ... beep ... it worked flawlessly! 

I have a Sony Clie SJ22 running kernel 2.6.15-27-386 with the KDE evironment in case there's another poor person out there looking for help. (and it sounds like there are a lot of them)

Thanks again!

---

### Post by jlh on 2007-01-31
fd,

I've created your script, and yes, indeed, it works.  I'll say it's a little strange.  I always seems to get a bind_error message first.  But that's of no moment because pressing the handheld sync once or twice anyway results in a successful sync.  

Thanks much.

---

### Post by fdimmling on 2007-01-31
> **jlh said:**
> fd,

I've created your script, and yes, indeed, it works.  I'll say it's a little strange.  I always seems to get a bind_error message first.  But that's of no moment because pressing the handheld sync once or twice anyway results in a successful sync.  


It is indeed a bit strange. AFAIK it is a problem of timing. The USB connection is established at the moment you press the button on the Palm. After the kernel sees the device the node /dev/pilot is created dynamically and then the jpilot syncing is started and tries to connect to the Palm. If somewhere the chain of communication is not yet ready you get an error message, but later on when everybody is on its place, you can start the syncing. Maybe I am wrong with this interpretation but from what I could find out reading myriads of posts on this subject it should be something like that. On my machine the timing seems to work for the first try but I have heard before from other people that they have to press the sync button twice or so. But it seems to work anyway.

Friedrich

---

### Post by jlh on 2007-01-31
Maybe I'm not quite doing it quite right.  Assume I launch jpilot.  Should I then push the sync button on the treo without first clicking sync on jpilot, and just wait?

I've tried first by clicking sync on jpilot, and then on the treo.  I've also tried the reverse order.  My experience is that I get the error message either way, but soon thereafter another click or two on the Treo accomplishes the sync.

---

### Post by fdimmling on 2007-01-31
> **jlh said:**
> Maybe I'm not quite doing it quite right.  Assume I launch jpilot.  Should I then push the sync button on the treo without first clicking sync on jpilot, and just wait?


You should _only_ press the sync button on the Palm, because the start of the sync process on the side of jpilot is performed by the jpilot -s command in the udev rule. This rule is triggered as soon as the pilot is recognized by the kernel and /dev/pilot has been created. With respect to jpilot the only thing you have to do is to start the program prior to pressing the Palms syn button.

Friedrich

---

### Post by jlh on 2007-02-02
Frederich

Yep.  Your rule works.  It seems to take two clicks on the Treo.  The first generates an error, with a "press the sync button" message, and doing so promptly launches the sync.  

Thanks much for the help.  I'm delighted to have this feature running consistently in dapper.

---

### Post by herbster on 2007-03-02
How strange, I have gotten JPilot AND the gnome pilot to work, but there seems to be something goofy with my Address book (contacts) database. This is what I get when I sync with JPilot:

```
 Syncing on device /dev/ttyUSB1
 Press the HotSync button now
****************************************
Username is "Bobby Gill"
User ID is 19674
lastSyncPC = 1283812151
This PC = 1283812151
Doing a fast sync.
sync_categories: Unable to open file: AddressDB
Syncing AddressDB
fast_sync_application: Unable to open file: AddressDB
Syncing ToDoDB
Syncing MemoDB
Fetching 'Saved Preferences' (Creator ID 'psys')... OK
Finished.
```

Everything is lovely except for my contacts, they don't sync at all! :(

---

### Post by Pragmatist on 2007-03-03
This is just a shot in the dark, but what happens if you backup your current AddressDB files and then remove them from the $HOME/.jpilot  directory.  Perhaps jpilot will create a new directory.  If it doesn't work you can always put the old copies back.

Another thing to check is the permissions on the AddressDB files in $HOME/.jpilot

---

### Post by trents on 2007-03-07
On my old Handspring Visor I got Jpilot to hotsync (I'm just doing backups, not syncing with Evolution, etc.) successfully by changing the port ID in File>Preferences>Settings to /dev/ttyUSB1 and then clicking on the Jpilot "Hotsync" button followed by TWO punches of the cradle button. Don't know why it takes two but it works every time. Now I'm wondering how to backup my Bible search software that's stored on the Visor's add on memory card.

Steve

---

### Post by trents on 2007-03-29
Got my Palm Z22 to sync with Jpilot on Edgy just fine. Port setting needs to be /dev/tttyUSB1 and like others have said, press the palm's hotsync button (or icon) first then after a couple of seconds click on Jpilot's hotsync button. One other thing, did you guys install pilot-link? I think this file may be necessary from what I have read. You can install it from Snyaptic.

Steve

---

### Post by jal on 2007-04-05
Thank you fdimmling, 
Your suggestion for the rules.d file worked perfectly. :) ;)

I had been manually syncing my clie sj22 by starting the pda sync and the starting the jpilot sync.

---

### Post by DonnieP on 2007-05-01
For anyone on Feisty, be aware that you have to use usb: in place of /dev/ttyUSB1 .

---

### Post by jlh on 2007-10-27
I've had my treo 650 syncing fine on jpilot using the rule file suggested in this post for more than a year.  I was running Dapper, but did a clean install of Gusty last night.  Now I can't sync.  

How do I figure out the device path to use in jpilot.  I was using /dev/pilot, but that doesn't work.  

I'd be grateful for any help.  :(

---

### Post by Pragmatist on 2007-10-27
Try using this instead **usb:  **That is 3 letters and a [B]: 

[/B]I don't remember why I did that, but it works! :)  I think it has something to do with a change in the way devices are handled.  I used the above method after switching from dapper to feisty.

---

### Post by jlh on 2007-10-27
Yes, that works.  Thanks.

Note as that "usb:" means just that - no backslash anymore. :)

---

### Post by premodern on 2007-10-27
> **Pragmatist said:**
> Try using this instead **usb:  **That is 3 letters and a [B]: 

[/B]I don't remember why I did that, but it works! :)  I think it has something to do with a change in the way devices are handled.  I used the above method after switching from dapper to feisty.

Thanks man ! I have installed Gutsy and I was trying to hot sync my Tunsgten E2 for hours ! This just did it !

---

### Post by kolinab on 2007-10-28
Wonderful. I had read this thread but somehow didn't believe the fix would work for me. Duh. 

"usb:" works. Thanks a bunch!

---

### Post by emale07 on 2007-10-30
very grateful for the help, citizens.

---

### Post by davidreedernst on 2007-11-05
Well, waaa!  I want to be all excited about how easily using "usb:" makes the whole process.  Unfortunately, ever since upgrading to Gutsy, I've been unable to sync.  Here's the rundown:

When I press the (soft) hotsync button on my palm, the computer notices.  I get new /dev/ entries like this:

 crw-rw-r-- 1 root   dialout 254,   8 2007-11-05 19:35 usbdev1.3_ep00
 crw-rw-r-- 1 root   dialout 254,  10 2007-11-05 19:35 usbdev1.3_ep01
 crw-rw-r-- 1 root   dialout 254,  12 2007-11-05 19:35 usbdev1.3_ep02
 crw-rw-r-- 1 root   dialout 254,   9 2007-11-05 19:35 usbdev1.3_ep81
 crw-rw-r-- 1 root   dialout 254,  11 2007-11-05 19:35 usbdev1.3_ep82

And /var/log/messages says things like 

Nov  5 20:34:25 kernel: usb 1-2: new full speed USB device using ohci_hcd and address 8
Nov  5 20:34:25 kernel: usb 1-2: configuration #1 chosen from 1 choice
Nov  5 20:35:25 kernel: usb 1-2: USB disconnect, address 8

That last "disconnect" message appears when the palm disconnects, either time-out or when I click cancel.  The /dev/ files disappear then too, so I have no doubt that the computer is aware of the connected palm trying to sync.  

However, when I try to sync, it looks like this:  

$ pilot-xfer -p usb: -l

   Listening for incoming connection on usb:... 

It looks like that whether I've done hotsync first, or after, or multiple times, including every combination of before and after that I could think of.  Then I tried them all with jpilot as well, also going before, after, and multiple.  And I've tried this pointing pilot-xfer at those /dev/ files mentioned above too.  As root and as a mere mortal.  No dice..  

All the same hardware worked when I was running Breezy before the upgrade, so really don't think there's an issue there.  I'm feeling stumped.  Any ideas anyone?

---

### Post by esbGutsy on 2007-11-15
I greatly appreciate it! :)
Now syncing the Zire72 to Gutsy via USB using JPilot

[COLOR="Blue"]**Note** killed the gpilotd process.  unsure if it was necessary..[/COLOR]

---

### Post by davidreedernst on 2007-11-15
> **davidreedernst said:**
> Well, waaa!  I want to be all excited about how easily using "usb:" makes the whole process.  Unfortunately, ever since upgrading to Gutsy, I've been unable to sync.  Here's the rundown:


Well, never got this to work, but this worked flawlessly for me:

[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

Hope that's helpful to others!

---

### Post by jal on 2007-11-16
This thread has been extremely helpful to me in trying to sync my Sony clie under gutsy,  had success thanks to the link davidreedernst posted:

[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

I needed to modprobe visor and set up the udev rule.
I set the jpilot device to "/dev/pilot".
jpilot synced fine. Well, so far. 
I need to press sync on the pda, then hit the sync in jpilot.

---

### Post by DJ_Peng on 2007-11-28
That worked for me once, it worked twice, but the third time I tried to sync my Sony Clie (PEG-SJ20) with J-Pilot the software refused to see that the PDA was syncing and some very calendar data I had already put on my PDA got wiped from my PDA. Is there a trick I'm missing to get J-Pilot syncing consistently?

---

### Post by darkazurka on 2007-12-19
Trents: I got a Palm Z22 too.
When I do 1. Hit the sync button on the Palm z22. 2. Press the synchronise key (after some seconds) in the program J-Pilot it gives me this error:
```
Syncing on device /dev/ttyUSB1
 Press the HotSync button now
****************************************
pi_bind error: /dev/ttyUSB1 No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished
```

---

### Post by DJ_Peng on 2007-12-19
I usually hit the sync button in J-pilot and then on my PDA. It gives an initial error but when I hit the button on the PDA it works fine and I get everything synced up.

---

### Post by darkazurka on 2007-12-20
I found a solution from this thread to sync my palm z22 device: [http://ubuntuforums.org/showthread.php?t=418979](http://ubuntuforums.org/showthread.php?t=418979)

trents: Your 3# post helped me to sync my Palm Z22 . The lines I followed to get it to work were:
> If I open terminal and issue the command "sudo modprobe visor" before attempting the hotsync then J-pilot is able to locate the palm device. I then tap the hotsync button on my Palm Z22 screen and then I mouse click on J-pilot's hotsync button.

very helpful (!!), after I set the device in preferences to /dev/ttyUSB1
I had also installed a program in synaptic called "pilot-link". I don't know if that helped the situation, but I think it did help.

---

