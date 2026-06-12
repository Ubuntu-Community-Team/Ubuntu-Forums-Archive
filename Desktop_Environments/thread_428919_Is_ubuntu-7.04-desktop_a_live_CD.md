---
title: "Is ubuntu-7.04-desktop a live CD?"
date: 2007-04-30
forum: Desktop Environments
---

### Post by gcaubu on 2007-04-30
Can it be installed on hard disc permanently and will not go nothing after rebooting?

---

### Post by blamecanada on 2007-04-30
It's a live CD, but there is an install option, so it can do both.

---

### Post by az on 2007-04-30
There used to be two Ubuntu cds.  The install cd and the live cd.  Before the Dapper LTS release, the live-cd installer was developed which became the default, preferred method of installing Ubuntu on a Desktop.  The legacy installer is still available on the "alternate" cd  as well as the "server" cd.

The live cd with installer was renamed "desktop" cd and it permitted Canonical to save some money by only producing and shipping one cd through Shipit.  It is also faster.  It takes on average twenty minutes to install using the live (desktop) cd as opposed to an hour using the classic installer.

Both installers are very safe.

---

### Post by LuisGMarine on 2007-04-30
Also I would like to add that I think this idea was a very smart one.  The live CD allows you to see if you computer works or doesn't work with Linux.  If you pop in the live CD and things are working properly, you might need to do some search on your hardware and Linux compatibility before you go ahead and do a full system install.

In a sense, this allows you to test the system before you install it to the hard drive.  Think of it like a test run.  So before I go around installing Ubuntu on peoples desktop, I pop in the live CD, make sure everything is working properly and then go ahead with the system install.  Has saved me from FUBARING peoples computers.

---

### Post by Flopmouth_Fish on 2007-04-30
A live CD means that I can boot from the CD and run the OS without installing it, correct?  If so, when I turn on my PC with the Ubuntu CD in the drive, will it give me the option to boot Ubuntu or Windows?  Also, does the live CD version have all the functionality of a full installation to the hard drive?

Finally, what is the easiest way to burn the ISO files to a CD?  I went to the downloads section on the Ubuntu website and read the "burning iso file howto", but I found it somewhat unclear.  When I click the download button, I am given the option of opening the file (WinRAR is the default) or saving it to the disk.  I assume I should save it, but will I then need a special program (such as the one shown in the "burning iso file howto"), or can I just burn it directly to a CD?

Just for reference, my PC is a custom-build with an Athlon64, DFI motherboard, 1GB of RAM, and a 250GB SATA HD, running XP Pro.  I am looking to install Ubuntu 7.04.

Lastly, I am sorry if I have hijacked this thread; I just did a search for "live cd" and I figured that my post is kinda related.  Thanks in advance for all help!

---

### Post by airtonix on 2007-05-01
you need a program that will burn superimpose the contents of teh ISO file onto the face of the disc......(sorry if already knew what an ISO was)

i came across this problem in windows, they all want you too pay to learn how to breath.

ok found two opensource pieces of software you can use under windows to burn an ISO onto a blank cd....

+ infrarecorder : [http://www.osalt.com/infrarecorder](http://www.osalt.com/infrarecorder)
+ cdrdao : [http://www.osalt.com/cdrdao](http://www.osalt.com/cdrdao)

---

### Post by SikEnCide on 2007-05-01
> **Flopmouth_Fish said:**
> A live CD means that I can boot from the CD and run the OS without installing it, correct?  If so, when I turn on my PC with the Ubuntu CD in the drive, will it give me the option to boot Ubuntu or Windows?  Also, does the live CD version have all the functionality of a full installation to the hard drive?

Finally, what is the easiest way to burn the ISO files to a CD?  I went to the downloads section on the Ubuntu website and read the "burning iso file howto", but I found it somewhat unclear.  When I click the download button, I am given the option of opening the file (WinRAR is the default) or saving it to the disk.  I assume I should save it, but will I then need a special program (such as the one shown in the "burning iso file howto"), or can I just burn it directly to a CD?

Just for reference, my PC is a custom-build with an Athlon64, DFI motherboard, 1GB of RAM, and a 250GB SATA HD, running XP Pro.  I am looking to install Ubuntu 7.04.

Lastly, I am sorry if I have hijacked this thread; I just did a search for "live cd" and I figured that my post is kinda related.  Thanks in advance for all help!


Use the previous mentioned software for burning the ISO.

Yes you boot from the cd and it gives you choices to boot from cd or boot from hard drive, so if you restart you system you will get ubuntu's menu and if you want to use your xp then boot from hard drive.

Yes as far as i know you basically have all the functionality with the cd as actually having it installed. Except for installing other programs and such that would need to use a hard drive.

I suggest you invest some money and buy partition magic(or find some open source partitioning program), and give ubuntu some drive space and do an actual install.  im running a laptop with a 120 gb hd and i gave ubuntu 10 gb with a 2 gb swap space and it runs perfect. i gave the other space to xp.. upon boot grub comes up and i have a choice of what i want to boot into. the grub setup is all done automatically when you install ubuntu.

---

### Post by Flopmouth_Fish on 2007-05-01
> **airtonix said:**
> you need a program that will burn superimpose the contents of teh ISO file onto the face of the disc......(sorry if already knew what an ISO was)

i came across this problem in windows, they all want you too pay to learn how to breath.

ok found two opensource pieces of software you can use under windows to burn an ISO onto a blank cd....

+ infrarecorder : [http://www.osalt.com/infrarecorder](http://www.osalt.com/infrarecorder)
+ cdrdao : [http://www.osalt.com/cdrdao](http://www.osalt.com/cdrdao)

OK.  I am downloading the ISO right now off of the Ubuntu website.  I'll then download and install the infrarecorderand use that to burn the CD.  Wish me luck!

---

### Post by SikEnCide on 2007-05-01
let us know how everything goes... also a note... BURN AT 4X or the slowest your burner will go

---

### Post by Flopmouth_Fish on 2007-05-01
> **SikEnCide said:**
> let us know how everything goes... also a note... BURN AT 4X or the slowest your burner will go

Oops; I burned it at the preset speed in InfraRecorder; the burn went at about 20x.  I'm about to reboot my computer and try the live CD.

---

### Post by SikEnCide on 2007-05-02
well if it works it works.. its just a precation i take when burning IS?O's. sometimes they dont like to be burned at higher speeds.

---

### Post by Flopmouth_Fish on 2007-05-02
I just tried the Live CD, and I'm pretty impressed.  I'm going to do a bit of searching for compatibility with my hardware (especially the wireless adapter), and then give the full installation a shot this weekend, when I have some more time.

---

### Post by SikEnCide on 2007-05-02
try looking here

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

---

### Post by Flopmouth_Fish on 2007-05-02
> **SikEnCide said:**
> try looking here

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

According to that list, my card (D-Link DWL-G122 Rev. A2)...

> works well in Breezy with ndiswrapper (the one provided in synaptic), with the drivers provided on the CD

I then went on the ndiswrapper site, and found a link to this page:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I hope that the installation will be straightforward; command lines scare me :-? 

One more question: I have a single partition on my hard drive with a Windows XP install which I don't want to mess up.  I think I remember reading that the Ubuntu installer will allow me to repartition my drive; is this correct?  Or do I need to use a third-party program?

Thanks to all who have helped answer my questions!

---

### Post by SikEnCide on 2007-05-02
To tell the truth, im not too sure. I used third party software. Partition Magic, because i have a copy of it and ive used it many times before so i know it works...  Maybe one of the Ubuntu guru's can help with this...

I have only been using Ubuntu for a few months now.

---

