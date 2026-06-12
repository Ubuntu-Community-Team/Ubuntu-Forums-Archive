---
title: "Sane Is Making Me Insane - Error During Device I/O"
date: 2012-04-24
forum: Desktop Environments
---

### Post by linux4me on 2012-04-24
I'm having a major problem getting my scanner to work consistently; now it's not working at all.

I'm getting the error:
> sane_start: error during device I/O
when I run simple scan, xsane, or gscan2pdf. 

The scanner is an HP LaserJet M1217nfw MSP running via a wireless network, but the same error occurs when it is installed directly via USB. I have removed and reinstalled the printer multiple times using the instructions on [HP's site]("http://hplipopensource.com/node/333"), which recommend the use of hp-setup and a required plugin that hp-setup installs. I have no errors when I run hp-check, and printing works fine. The printer is detected correctly.

I did a clean install of the printer on an 11.10 machine, and ran into the same error when I use the document feeder (ADF).

However, scanning does not work either via the flatbed or ADF now on any of the three machines I've tried it with. Although it was working previously before I did something that appears to have broken it permanently, I have tried on three different machines, two running 12.04, and one running 11.10. At first I thought it was something with my wireless router, but as I said, a trial with it installed via USB produced the same problems.

The odd thing is that the scanner was working for single sheets up until yesterday when I had to do a huge (~500) page scanning job using the document feeder. Since then, nothing but trouble.

Does anyone have any idea how to get this thing working? There's nothing in my print queue, but it seems like something has taken the scanner down completely now.

The more I think about it, the more it sounds like a problem with the printer itself. My current plan is to set up a Windows machine :frown: to see if it works that way. I feel dirty just thinking about that...

---

### Post by RichardCain on 2012-04-24
I had a similar problem with an Epsom Workforce 545 recently.  I tried running several scanning programs with no success.

Then I tried:
```
sudo xsane
```
in a terminal and, despite issuing apocalyptic warnings, everything worked fine.  After that one time with sudo, xsane opens normally through the menu with no problems.

EDIT:  This worked for the flatbed; I didn't try with the ADF.

---

### Post by agillator on 2012-04-24
You said you followed HP's instructions, but there are actually a couple of different possibiities. First, are you using HPLIP? I assume so if you went to HP to get instructions. But this is important. Second, how did you install HPLIP, from an HP installation program you downloaded or from Ubuntu's package? 

The gist of where I am going: Ubuntu's package does not work correctly, especially for scanning, for some reason. If you used that, purge it, download the installation program from the HP site and install it. My experience has been that will fix most HP printing/scanning problems. If you have already done this, then we'll see what else we can find for you. However, a number of people have had problems (including yours truly) and that solved the problem slick as a whistle. Let me know if you want detailed instructions.

---

### Post by linux4me on 2012-04-25
> **RichardCain said:**
> I had a similar problem with an Epsom Workforce 545 recently.  I tried running several scanning programs with no success.

Then I tried:
```
sudo xsane
```
in a terminal and, despite issuing apocalyptic warnings, everything worked fine.  After that one time with sudo, xsane opens normally through the menu with no problems.

EDIT:  This worked for the flatbed; I didn't try with the ADF.

This sounds like a permissions issue. I know that with this HP, my user has to be added to the lp and lpadmin groups, which requires a reboot before it takes effect if the user is added to the groups during the installation. That may be why sudo worked for you?

I gave sudo a try with Simple Scan and still got the same error:

> sane_start: error during device I/O

---

### Post by linux4me on 2012-04-25
> **agillator said:**
> You said you followed HP's instructions, but there are actually a couple of different possibiities. First, are you using HPLIP? I assume so if you went to HP to get instructions. But this is important. Second, how did you install HPLIP, from an HP installation program you downloaded or from Ubuntu's package? 

The gist of where I am going: Ubuntu's package does not work correctly, especially for scanning, for some reason. If you used that, purge it, download the installation program from the HP site and install it. My experience has been that will fix most HP printing/scanning problems. If you have already done this, then we'll see what else we can find for you. However, a number of people have had problems (including yours truly) and that solved the problem slick as a whistle. Let me know if you want detailed instructions.

Yes, I am using HPLIP, and I did use the version in the Ubuntu repositories.

As per your suggestion, I removed the installed printer via System Settings, then ran:
```
sudo apt-get purge hplip
```

Next, I went to [HP's site]("http://hplipopensource.com/hplip-web/gethplip.html") and downloaded their HPLIP shell-installation script and ran it in automatic mode as they recommend.

The installation went fine--saying it was successful--until the very end, when I got the following error message:
> error: Unable to lock /home/<my user name>/.hplip/hp-systray.lock. Is hp-systray already running?

I suspect that's because hp-systray was still running from the previous installation, and doesn't represent a problem. I was able to print a test page successfully, and the scanner works for single pages in Simple Scan--though I may not have scanned enough to get the I/O error--but I still get the I/O error when using the document feeder. Sometimes, the error occurs after only one page, sometimes I am able to scan four or more pages successfully before getting the error, but I still get the same error in Simple Scan and:
> INFO - gscan2pdf: sane_start: Error during device I/O
in gscan2pdf while running it in debug mode.

With HP's version of HPLIP, I am getting the HP systray and a pop-up message of something along the lines of "beginning scan" and "scan completed" for each page, even after the I/O error. The printer goes through the remaining pages popping up status messages even after they have failed to show up in Simple Scan and gscan2pdf. 

An additional issue which may or may not be related, is that in gscan2pdf, although it seems to be scanning the pages up until the time I get the I/O error, none of the pages show up in the UI. I tried doing a single page in gscan2pdf in the "flatbed" mode, and get the I/O error there immediately.

Just to make sure it isn't a permissions issue, though since it's intermittent I don't see how it could be, I tried both Simple Scan and gscan2pdf again using sudo and I still get the I/O error.

---

### Post by linux4me on 2012-04-25
It looks like the printer and the network connection are not the problem. I was pretty sure about the latter since I was still getting the errors while connected via USB, but to make sure the printer wasn't the issue, I got hold of Winblows Vista machine, installed HP's drivers and scanner software, and gave the thing a thorough test. 

There was one occasion when it gave me an error about connecting to the scanner when using it wirelessly, but it only happened once (maybe interference?) and I've run about 200 sheets through the document feeder after that without any more problems.

So, I'm currently thinking it's an issue with libsane, and still loving Linux after having to suffer through my time on that Vista machine.

---

### Post by agillator on 2012-04-25
I think you are right, sane is the problem for some reason. This I haven't run into before. You might try purging sane and xsane and then reinstalling. I certainly haven't had any trouble with them but who knows.

---

### Post by linux4me on 2012-04-26
I hate to admit this, but I have a scanning job I really need to get done, so I resorted to trying to finish it using the Windoze machine. Although it took longer to manifest, it seems like there is an I/O problem with it, too. I get frequent "cannot communicate with the printer" errors using HP's own Scan To software. I also had quite a few paper jams in the document feeder, which are interesting because the paper I am scanning is practically new HP paper...

Well, the printer is still under warranty so I called HP Support and spent a whopping 3+ hours on the phone with a really helpful support tech who finally gave up and is sending me a new (refurbished) printer. 

So maybe it's not sane after all. There appears to be an actual issue with the printer involving connection as well as the problem with the document feeder itself. I may still try purging sane/xsane and reinstalling just to see if that helps on the Ubuntu end.

Thanks for taking the time to reply. I really appreciate it.

---

### Post by agillator on 2012-04-26
I'm glad tech support treated you well. I will be curious if the replacement solves the problem. The fact that they spent that much time with you and then agreed it might be the printer is impressive. Another reason to stick with HP.

---

### Post by linux4me on 2012-04-26
> **agillator said:**
> I'm glad tech support treated you well. I will be curious if the replacement solves the problem. The fact that they spent that much time with you and then agreed it might be the printer is impressive. Another reason to stick with HP.

The guy I spoke with did treat me well. He wasn't following a script, was knowledgeable, and really put forth an effort. I did some Ubuntu proselytizing while we were waiting for Vista to reboot multiple times, and I think he's going to download and try 12.04. ;)

I'm curious to see if the replacement printer does the trick, too. I will post back either way. It's not due here until 5/3, so it will be a while...

---

### Post by linux4me on 2012-05-03
I got the new (refurbished) printer yesterday and set it up using HPLIP from the HP site. 

It scans now using the automatic document feeder without any paper jams or errors in both Simple Scan and Gscan2pdf. I didn't do a massive scanning job to really torture-test it, but it did scan seven pages without any errors, which is much better than the previous printer. I still don't get any visible documents with Gscan2pdf, but that may be another issue (maybe even a user issue).

Looks like it was the printer after all.

---

### Post by agillator on 2012-05-04
Great. I was afraid we were going to have to go the 'get a bigger hammer' approach. That's always so messy!

---

