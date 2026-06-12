---
title: "Please help, I'm in way over my head here..."
date: 2009-06-25
forum: General Help
---

### Post by TheStabe on 2009-06-25
I had no idea what I was getting into when I tried Linux for the first time yesterday. Basically, I'm lost. I have plenty of problems and questions, but the first thing I'd like solved is why my internet connection is so bad. My 1.2mb/s download speed went to 30kb/s, and my web browsing is very, very slow. I can't imagine what the problem is here- but I doubt it's supposed to be this way. In fact, regular desktop stuff is a bit sluggish too. My specs:

Pentium 4 HT 3.2Ghz
ATI Radeon HD4670
2Gb RAM

And I'm using 9.04.

One more thing, If you tell me a code of some sort, I will have absolutely no ideo on what to do with it. For now, I just want my internet fixed...

Thank you in advance for your help, I hope I can adjust to Linux.

---

### Post by Therion on 2009-06-25
Clarify one thing for me...  Did you install Ubuntu to your hard drive, or are you running it from the LiveCD?

---

### Post by philcamlin on 2009-06-25
live cd = extreme slow 


if its on your hard drive thats a different ball game :D

---

### Post by TheStabe on 2009-06-25
I installed it (thanks for quick reply).

---

### Post by philcamlin on 2009-06-25
sudo apt-get update 

sudo apt-get upgrade 

try those and let it do its thing it should be better after that :popcorn:

---

### Post by Therion on 2009-06-25
Okay, so it's a fresh install. Gotcha.

Have you checked for updates?  S'okay if you don't know how, but I need to know if you've done this or not.

---

### Post by mk1w86 on 2009-06-25
Is your computer connected to the internet through wireless?  I have had problems with a wireless belkin USB stick where the download speed has been incredibly slow (around 30kbps like you say) but that was with Ubuntu 8.04, I have since installed 9.04 and it seems ok so far.

---

### Post by TheStabe on 2009-06-25
I did download a bunch of updates (accidentally). At 30kp/s :P It took awhile.

Yes it is wireless, and yes this is 9.04.

---

### Post by Therion on 2009-06-25
That's okay.  We're going to go back and check for more.

You have a panel at the top of your screen and menus at the top left:  **Applications, Places, System.**

Click on System/Administration and then Software Sources and then Ubuntu Software tab.  You should have some check boxes.  Put a tic in all the boxes except the one at the bottom indicating source code.  Do NOT check that box.

Now, click on "OK", and on "Reload" when prompted.

Go back to System/Administration and now click on the Update Manager and check for more updates.  Install any remaining updates.

It should look like this when you're done: [Picture](http://web2.justhost.com/~buranen1/wp-content/uploads/2007/10/screenshot-software-sources1.png)

---

### Post by philcamlin on 2009-06-25
haha me and this other guy are on the same page :D

---

### Post by TheStabe on 2009-06-25
That did nothing- there were no more updates availible.

---

### Post by donkyhotay on 2009-06-25
> **TheStabe said:**
> One more thing, If you tell me a code of some sort, I will have absolutely no ideo on what to do with it. For now, I just want my internet fixed...

copy/pasting terminal commands is often easier then using the GUI so don't complain if people tell you to do so. Iprobably don't believe me (many people fresh from windows don't) but as an example, say you need to install build-essential at some point to fix this issue (you don't need to yet it's just an example). Using the GUI the instructions are

Goto "system > administration > synaptic package manager"
click 'reload'
click the search button
type in "build-essential"
click on the white box next to 'build-essential' and select 'mark for installation'
click apply

On the other hand the exact same process can be done by copying/pasting the following commands into the terminal
```

sudo apt-get update
sudo apt-get install build-essential

```
Honestly which is simpler for someone to do? Especially someone just learning how to use linux? Using the GUI has 6 steps, using the CLI has 2 steps which you just copy/paste so you don't have to worry about mistyping anything. And just for future reference since you don't know where to copy/paste these types of commands too. If you ever are told to copy/paste something into the CLI (sometimes referred to as the terminal) just go to 'applications > accessories > terminal' and the window that appears is the one you want to copy/paste those types of commands into.

---

### Post by pbpersson on 2009-06-25
> **TheStabe said:**
> I had no idea what I was getting into when I tried Linux for the first time yesterday. 

I hope I can adjust to Linux.

You have stepped through the looking glass into a brave new world.

The first rule of thumb is to forget most of what you learned in Windows because it probably will not apply here.

There are no drive letters, applications are not installed in "Program Files" and there is no such thing as an EXE file.

Welcome to Linux!  :)

---

### Post by TheStabe on 2009-06-25
Okay. What about my bad internet speeds?:confused:

---

### Post by Therion on 2009-06-25
First off, reboot.  Seriously.

Second, after a reboot open Firefox.

Then go to System/Administration/System Monitor.

Click on the "Processes" tab.  

Look for the "Firefox" process.  How much CPU usage is it sucking up?

Do you see any other process that appears to be sucking up an unusual amount of your CPU or system memory?

---

### Post by amityak on 2009-06-25
how about telling us which kind of wlan are you using?

type into the terminal the following commands

lspci

which lists all your hardware devices (installed or not doesnt matter)

try to read this list and get familiar with your machine, try to locate your wireless network card, post this list here.

if your card is a usb stick so type into the terminal

lsusb

this command stands for LIST USB or LIST PCI
i recommend to read about commands before typing them in
you can read about every command by typing 'man' (manual) before the command

here:

man lspci

or

man lsusb



good luck

---

### Post by mk1w86 on 2009-06-25
You can also use

```
dmesg
```

to see what the OS is doing with your hardware. :)

---

### Post by sloggerkhan on 2009-06-25
Can you post complete info on your wireless dongle?

(The easiest way to verify if the wireless is responsible is to connect to your modem/router via ethernet cable and see if your speeeds change.)

I very much suspect the wireless dongle. If that proves to be the case through speed comparison, first try looking under system > administration > hardware drivers. If nothing shows up there, try using ndiswrapper + ndisgtk to install the windows driver for your wireless card. It may work better than the current driver.

---

### Post by TheStabe on 2009-06-25
Here goes:

Firefox is sucking up 1% of my CPU.

"Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI"

I'm starting to not like this OS :P

---

### Post by surfed on 2009-06-25
check if internet is slow with wired so we can isolate the issue.

---

### Post by DeMus on 2009-06-25
> **TheStabe said:**
> Here goes:

Firefox is sucking up 1% of my CPU.

"Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI"

I'm starting to not like this OS :P

Don't do that. remember how it  took you to get familiar with Windows? Now don't expect to get to learn Linux in a day. It will take some time, but take that time, you will love it. Just as I do. I started a little over a year ago and never touched Windows again (except at work where I can not convince them to make the step).
Try to read a lot about Linux, there are plenty of websites and don't be afraid to do something. As a "simple" user you can not do anything wrong. That's the strength of Linux. If you want to set something, install something, delete something you need administrator (in Linux called root) rights. Without you can only use the computer.

Oh yes, and where will you find such a community to help you? In a Windows forum? Forget it.

---

### Post by Megrimn on 2009-06-25
> **pbpersson said:**
> 

The first rule of thumb is to forget most of what you learned in Windows because it probably will not apply here.
That's a lie.  And a good way to discourage the new user.  What you should have said is that you need to be open-minded.  Many of the functions are the same.  Windows just has more hang-ups :P

> **pbpersson said:**
> There are no drive letters
uh, yeah, there are. sda and sdb are 2 examples.

> **pbpersson said:**
> there is no such thing as an EXE file

yeah, if you don't use WINE.

---

### Post by TheStabe on 2009-06-25
Ok guys, I fixed it. It was definitely the card- I switched it out and am now DLing at 1MB/s. Thanks for your help; now that I'm not infuriated I can start learning this thing :D

---

### Post by pbpersson on 2009-06-25
> **Megrimn said:**
> That's a lie.  And a good way to discourage the new user.  What you should have said is that you need to be open-minded.  Many of the functions are the same.

Well....for instance:

1.  No drive letters like C:, D:, E:, F:, etc
2.  You do not type "\" between directories
3.  No control panel
4.  Typically no virus scanner
5.  No need to use install CD's and CD keys
6.  No Internet Explorer
7.  No MS Office
8.  No Wordpad
9.  No notepad
10. No registry
11. No network neighborhood
12. No Windows genuine advantage
13. No Nero to burn CDs
14. No need to buy software, it is all free
15. All software from any company is typically installed from one screen
16. All updates for ALL software are usually downloaded automatically
17. No Internet Information Server
18. No Visual Studio
19. No Windows Task manager

Need I go on?  :)

All these things exist in Ubuntu BUT they have different names and they are located in different places.  That is what I meant.

It is like moving from a model T Ford with a manual crank engine from 1930 to a new all-electric car in the 21st century.  It has an accelerator pedal and a steering wheel but it is a new and better reality.

---

### Post by Megrimn on 2009-06-25
> **pbpersson said:**
> Well....for instance...



All these things exist in Ubuntu BUT they have different names and they are located in different places.  That is what I meant....



Yeah, well, the tone of your earlier post isn't exactly what a frustrated new user needs to hear.  

@TheStabe:
you may have skinned your knee diving into the pool, but you can still swim, I'm sure :)

---

