---
title: "KDE Lirc (IRKICK)"
date: 2006-05-27
forum: Desktop Environments
---

### Post by jon_benge on 2006-05-27
Hi

I have got lirc setup and functioning fine with my Hauppauge remote control. However IRKICK doesn't load with KDE after a boot. I have to manually start it every time by pointing to the K Menu > Utilities > KDE Lirc Server.

How can I get IRKICK to start automatically?

---

### Post by CitizenKane on 2006-05-28
Not a problem.
First, make sure you have IRKick started. 
Then open Kcontrol ( i.e. systems settings in k menu)

Under "Personal" select KDE components
Click session manager on the left

In the "On Login" box 
select the radio button that says "Restore manually saved session"

Close all normal open apps that you have , do not close IR kick

Then in the k menu select "save session"
And that is it!

Any programs you have open when you click "save session" will be started when you start KDE.  For instance, if you wanted firefox to start when you start KDE you could also have firefox open when you click "save session".  It is really up to you.

BTW
Do you happen to have a link or something for setting up LIRC?  It is something that I have been wanting to do.

---

### Post by jon_benge on 2006-05-28
Funny you should say that, but I've been trying to post my HOWTO over the last couple of days. For whatever reason, it doesn't seem to appear in the HOWTO forum :???: 

I'll post it here as well, just in case it never shows up....

Oh and thanks a bunch for that information. You have solved the final piece to my puzzle :) I've included your information in my HOWTO if you don't mind.

-----------------------------------------------------------------------------------------------

Took me several months to get my Hauppauge remote control working. I've followed several guides and got nowhere. Only now, after combining all the information I have gathered, have I finally got it working! 
Hopefully by the end of this guide, you too will be able to launch and control Kaffeine, Amarok and even Konqueror from the comfort of your arm chair :)

*NOTE: I can only confirm this guide works for the grey remote control that comes with the new Nova-T PCI. If you successfully set up a different remote control using this guide, please post details and help others!*

Okay, let's get to it..


**[SIZE="5"]PART 1: Testing, Testing, 1.2.3[/SIZE]**

We need to find out if the standard Kubuntu kernel has detected your remote control. We can check this by typing the following command into a terminal window.

```
cat /proc/bus/input/devices
```

A load of text will appear. Look for something similar to what is shown below:

```
I: Bus=0001 Vendor=0070 Product=9002 Version=0001
**N: Name="cx88 IR (Hauppauge Nova-T DVB-T"**
P: Phys=pci-0000:01:02.0/ir0
S: Sysfs=/class/input/input3
**H: Handlers=kbd event3**
B: EV=100003
B: KEY=100fc312 214a802 0 0 0 0 18000 41a8 4801 9e1680 7bb80 0 10000000
```

There are two important things to look for here. The **'N:Name'** proves the remote control has been detected properly and the **'H:Handlers'** shows us what *'event number'* our remote control is mapped to. 
You will need to remember the event number later on so keep it in mind. My Hauppuage remote control event number is 3, but yours could be something different.

We are going to test the remote control to make sure everything is working correctly. Type the command below into a terminal and replace *'eventx'* with your event number. So if I were doing this, i'd have to  type *'event3'*.

```
sudo evtest /dev/input/eventx
```

Press some buttons on the remote control. You should see some output in the terminal. This confirms communication with your remote control was received. 

Press Ctrl+C to finish the test.


**[SIZE="5"]PART 2: Installing The Lirc Server[/SIZE]**

We need to install *lirc*, the Linux Infra-Red Receiver. Lirc will handle all of the communication between your remote control and your computer

```
sudo apt-get install lirc
```

Time for another little test! You will need to have **two terminals** open at the same time to perform this test. In the first terminal, type what you see below and replace *'eventx'* with your event number

```
sudo /usr/sbin/lircd -H dev/input -d /dev/input/eventx -n
```

And in the second terminal, type:

```
irw
```

Press some buttons on the remote control and you should see some output in one of the terminals. Once you have finished with this, press CTRL+C to cancel.


**[SIZE="5"]PART 3: Configuration Files[/SIZE]**

You need to download two configuration files and save them to your home folder

[lircd.conf]("http://parker1.co.uk/myth/lircd.conf")

[hardware.conf]("http://parker1.co.uk/myth/hardware.conf")

Open up the hardware.conf configuration file with your favourite text editor and look for the line that starts with:

```
DEVICE="/dev/input/event2"
```.

Change the event number to your own event number (if different).

Once that's completed, you need to move these files to /etc/lirc

```
sudo mv lircd.conf /etc/lirc
```
```
sudo mv hardware.conf /etc/lirc
```


**[SIZE="5"]PART 4: Installing The KDE Lirc Front End, IRKICK[/SIZE]**

The next thing we need to do is install the KDE front end for lirc, called IRKICK.

```
sudo apt-get install kdelirc
```

*NOTE: For this very reason, this guide is for Kubuntu users only. I am not aware of a GNOME front end for Lirc. But if you know of one, this is when you should install it.*


**[SIZE="5"]PART 5: Key Mapping[/SIZE]**

Go to the *K menu*, point to *Utilities* and click on *KDE Lirc Server (IRKICK)*.

If you don't see it there, you may have to wait a couple of seconds, or reboot your computer.

Look over at your taskbar and you will see a little antenna. If your configuration is a success, the antenna will be surrounded by red radiowaves. 

This icon will light up whenever a button is pressed on the remote control. Press a few buttons now to test it for yourself!

All that is left to do now is to configure the buttons on the remote control to perform a specific action. 
Right click the antenna icon in your taskbar and select *configure*. Click the *add* button on the **right hand side** and a wizard will begin and guide you through the rest!


**[SIZE="5"]PART 6: Starting IRKICK Automatically with KDE[/SIZE]**

Make sure you have IRKick started. Then open 'System Setting' in the K Menu. Under 'Personal' select 'KDE components' and click 'Session Manager' on the left. 
In the 'On Login' box select the radio button that says 'Restore manually saved session'. Close all normal applications that you have open but do not close IR kick. Then in the k menu select 'save session' and that is it! 
Any programs you have open when you click 'save session' will be started when you start KDE. For instance, if you wanted Firefox to start when you start KDE, you should have Firefox open when you click 'save session'. It is really up to you. 

Enjoy!

[i]Acknowledgements: 
Thanks to James Muscatt for helping out at [Hauppauge forums]("http://www.hauppauge.co.uk/board/showthread.php?t=7085").
Thanks to the author of [this guide]("http://parker1.co.uk/mythtv_ubuntu2.php") too!
Thanks to CitizenKane for the last part of this tutorial[/i]

---

### Post by CitizenKane on 2006-05-28
I am going to try and go through this as soon as have time, (I am helping people move all this week).  Hopefully I can just get some kind of remote working.  And no problem on adding the little part at the end.  Not that much of a secret. ;)

---

