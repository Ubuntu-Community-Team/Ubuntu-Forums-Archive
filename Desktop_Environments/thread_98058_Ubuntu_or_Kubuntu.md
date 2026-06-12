---
title: "Ubuntu or Kubuntu?"
date: 2005-12-02
forum: Desktop Environments
---

### Post by boomerian on 2005-12-02
:confused: Have an aged but functional Celeron 400MHZ desktop with 192MEG of RAM. My son, an avid KDE Linux proponent, built my wife and me a newer,faster desktop running XP. D-Link wireless router and Linksys WMP54G (version 2) wireless adapter for the Celeron machine.
I am eager to install Ubuntu, but have the following questions:
- Do I need to uninstall Windows (unactivated, unauthorized 30-day copy of XP from the purchased CD that accompanied the newer machine) prior to installing Ubuntu? I only use the XP copy in this manner in order to get the wireless adapter up and running, with WEP.
- How do I install the NDISWrapper, since I have read that, though Ubuntu should recognize and work with the WMP54G version 4 chipset, it apparently does not with versions 1 or 2? (I have copied the ndiswrapper files to floppy disk.)
- Should I be concerned about my 192MEG of memory, as far as Gnome is concerned (having read that Gnome needs 256MEG or more)? If so, would Kubuntu be more 'economical' from a memory requirements standpoint instead?
As I have said, I am very much looking forward to getting started with and learning as much as I can about Ubuntu. Thanks in advance for any guidance that any of you can provide. Cheers!

---

### Post by Ampersand on 2005-12-02
You won't need to uninstall Windows. If you want to be able to dual boot then you'll have to create a seperate partition to install Ubuntu on, but if you want to only have ubuntu on there, you can just install over windows.

There's a howto for using the ndis wrapper in the networking forum, should come up in a search.

Start off by trying Gnome. If it runs slowly, it might be worth trying xfce (from Synaptic).

---

### Post by prawdapunk on 2005-12-02
For this computer configuration I instruct you Xubuntu.

I must install ubuntu with option *server* and next:
[HTML]apt-get install xubuntu-desktop[/HTML]

Because your Procesor is very low and 
> (having read that Gnome needs 256MEG or more)

No Gnome act with 128 mb ram, but without spoofs and very slow, but it act ;)

---

### Post by GeneralZod on 2005-12-02
Another xfce vote here, or you could try to pick up another stick of RAM off of eBay - RAM for old desktops seems to be dirt-cheap, nowadays :)

Edit:

Also, there may or may not be some odd issues with floppy disks in Breezy - a USB pen or CD-RW might be a slightly less troublesome option.

---

### Post by meborc on 2005-12-02
i would not suggest a SERVER install for a person who is new to linux... if you run a SERVER install, it will only install packages required to run the machine, there will be no graphical interface, no programs, no nothing... even if the machine is slow and old, a normal install would be my recommendation... and if that doesn't work... well you can always reinstall :D ...

my suggestion is to install ubuntu normally... if it is too slow (GNOME doesn't apeel to you), try to find instructions here on this forum, how to change to XFCE... but try to do it normally in the beginning...

as for installing, just cose BOOT FROM CD in your BIOS and then in the ubuntu install partitioning section chose to erase all existing data (ofcourse i believe you have copied all documents and other important stuff for you to a safe place on the net or on discs)

happy adventure :rolleyes:

---

### Post by Zeroedout on 2005-12-02
Anybody remember the name of the meta package that would install a minimal desktop? I remember reading it would only grab XFCE and a few other low memory items. I looked through the repos, but am drawing a blank, and i know this would be great for boomerian's situation.

---

### Post by meborc on 2005-12-02
i would also recommend [[COLOR="DarkRed"]this post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=90954")... read the whole thind before doing smth... i tried it also, but found it too timeconsumeing afterwards to install all the stuff i use :D ... and i also have 40GB of hard drive, so i'm not very worried :D

EDIT: dam*n that wasn't the post i wanted to show, but it has smth similar... i can't find the real one anymore... too old i guess

---

### Post by boomerian on 2005-12-02
Thank you all for prompt and thoughtful replies!
To Meborc, this is simply (I hope) a workstation install, and I do not intend to use this old machine as a server (If I understand what you're advising against), and yes, I have backed up all old files (both important and probably much that is unimportant).
I will read as much as I can prior to the install, but this is truly a secondary machine, for my use while my wife is on the newer, faster XP machine, and primarily for my web-browsing, tinkering, and learning more about Linux. Just the same, I'd like to make the most of it and get it humming to the extent possible.
As for additional memory, my limit would be 256MEG, according to the specs, as this is an older eMachine and only has two slots. My biggest concern was getting the wireless adapter to work...:cool:

---

