---
title: "Firefox Crashes - What Can You Do?"
date: 2008-08-14
forum: Desktop Environments
---

### Post by NickWilsdon on 2008-08-14
I'm getting repeated crashes with latest FF 3.0.1 on Ubuntu 8.04. I've upgraded everything in package manager and removed all extensions from FF. Still happening. 

I've also installed Bonager and forced a file check

Is there any way of finding out what is causing these crashes?

TIA

Nick

---

### Post by mrsudo on 2008-08-15
does it crash on sites involving flash?  this is a common problem

---

### Post by fuzin on 2008-08-15
I have same problem on my stacionary machine, on laptop is working nicely. 

All WebBrowses crashes. I have kde, so also qonquer crashes. 

And usualy is when i browse some flash content. 

How can i fix this ?

I have adobe non-free flash installed.

---

### Post by hackboy on 2008-08-15
Just Goto Add Or Remove Programs And Install opera..That Will Work Excellent

---

### Post by blartish on 2008-08-15
My Firefox 3 on Ubuntu 8.04 64-bit crashes when I click on occasional website links that open new windows. After about 10 seconds the screen goes gray, i am then obliged to "Force Quit".

Sometimes it also doesn't seem to register that a link has been clicked on and it is impossible to navigate away from the page (except with back-button).

---

### Post by penol700 on 2008-08-15
try getswiftfox.com, i had the same problems and this fixed all of them.. i can even watch youtube clips in fullscreen without any lag!:)

---

### Post by silkstone on 2008-08-15
How does it crash? Does it hang and have to be killed, or does it just shut down unexpectedly?

---

### Post by kelean on 2008-08-15
I have been having the same type of problem with firefox.  Mine just closes for no reason.  If i start it with the cli and it closes I get a segmentation fault.  I have been having the same problem with opera.  Some times after it closes it will not start.  I get the seg fault error.  I have to reboot it order to start the program.

---

### Post by pietjanjaap on 2008-08-15
On a different forum somebody had also such a problem on a website, but other people went to the site and had no problems.
He was installing flash(and other things), but he removed it, but problem was still there.

He is starting over with installing, and following a website how to install codecs etc.
On 1 of these how to site's you can find wat you have to install after installation of ubuntu.

Search forums, ubuntu howto sites etc.


[http://computertip.googlepages.com/ubuntulinux](http://computertip.googlepages.com/ubuntulinux)
[http://onlyubuntu.blogspot.com/](http://onlyubuntu.blogspot.com/)
[http://www.ubuntu-unleashed.com/](http://www.ubuntu-unleashed.com/)
[http://www.ubuntu1501.com/](http://www.ubuntu1501.com/)
[http://www.tuxmachines.org/](http://www.tuxmachines.org/)
[http://polishlinux.org/howtos/truecrypt-howto/](http://polishlinux.org/howtos/truecrypt-howto/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)
[http://ubuntu-tutorials.com/](http://ubuntu-tutorials.com/)
[http://www.ubuntux.org/](http://www.ubuntux.org/)
[http://www.debuntu.org/how-to-instal...lvm-filesystem](http://www.debuntu.org/how-to-instal...lvm-filesystem)




[http://www.linuxalt.com/](http://www.linuxalt.com/)
[http://www.openinhoud.nl/zoeken](http://www.openinhoud.nl/zoeken)
[http://www.osalt.com/](http://www.osalt.com/)
[http://linuxappfinder.com/alternatives?page=1](http://linuxappfinder.com/alternatives?page=1)

the best:
[http://damen.dommel.be/Ubuntu.html](http://damen.dommel.be/Ubuntu.html)

the gimp - very good photoshop
gfslicer - splitter joiner
Q7z+7z - archiver
hellanzb - downloaden nzb van usenet
kget - download program
Inkscape Vector Graphics Editor
Klibido - to look in usenet groups and nzb download
dvdfab in wine - the only thing i can't find in linux.
quickpar in wine
k3b writing/burning dvd's
gmount iso - to mount iso file
KNetLoad Network Monitor - you network activity in a grafic

---

### Post by Anzan on 2008-08-17
I used to use Epiphany in Gnome because it crashed much less. 

In Fluxbox Firefox has never crashed for me or several other people that I know.

---

### Post by NickWilsdon on 2008-08-18
Hi everyone - thanks for the replies 

@mrsudo 

Yes I read that after I had posted. I removed the flash extension and for a little while it seemed stable again. Then I got a crash. I've read that it's a good idea to install the Adobe 10 module so will be trying that next. It definitely seems like something on the page crashes it. 

@fuzin

Yes seems we should dump the nonfree and get the adobe10 installed. 

@hackboy

I didn't know Opera did a release - cool. I like my FF plugins but Opera have a very good core browser.

@penol700

Thanks, trying SwiftFox too for my CPU. Will let you know.

@silkstone

Can get either. Sometimes it's grays out and needs to be shut down (waited 30 mins on one occasion so definitely not recovering itself). Usually though it just crashes. Halfway through a forum post :mad:

@kelean

I'll check this on the CLI, not done that. Maybe we have the same problem.

---

### Post by NickWilsdon on 2008-08-18
@fuzin

Just installed Flash 10 player. Here are the instructions:

```
# sudo apt-get remove flashplugin-nonfree
# cd /tmp
# wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz
# tar -zxvf flashplayer10_install_linux_070208.tar.gz
# cd install_flash_player_10_linux
# ./flashplayer-installer

(Enter, yes, no)
```

HTH - I've just tried it and will report back here.

---

### Post by billgoldberg on 2008-08-18
> **NickWilsdon said:**
> I'm getting repeated crashes with latest FF 3.0.1 on Ubuntu 8.04. I've upgraded everything in package manager and removed all extensions from FF. Still happening. 

I've also installed Bonager and forced a file check

Is there any way of finding out what is causing these crashes?

TIA

Nick

If your browser crashes on flash sites, switch to ALSA instead of using PulseAudio

[link]("http://linuxowns.wordpress.com/2008/05/07/hardy-sound-problems-2/")

Or use the new flash player:

[link]("http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/").

---

### Post by NickWilsdon on 2008-08-20
Thanks Bill - but it looks like this is a bigger problem than just Firefox. I now get segmentation fault errors on Opera, Swiftfox and FF. I also get crashes on other windows, including the package manager. I'll open another thread on this. 

Thx

---

### Post by acy76 on 2008-08-20
I would suggest you start by running a memory test on the machine, as this could be a hardware error (possibly caused by bad RAM). 

This can be done easily by rebooting and hitting 'ESC' when prompted, prior to Grub loading. Then, select memory test as the boot option instead of the Ubuntu kernel. Memtest will begin running automatically. Leave the test running for at least one complete pass (one pass is composed of several individual tests), longer if time allows. Any errors listed on the screen should be cause for concern - a healthy system will produce none.

It is worth noting that Memtest can detect errors that are caused by other hardware issues, not necessarily RAM. If you do encounter errors, try removing all but one stick of RAM and re-running the test to see if the errors return. Try this with each stick individually to find the bad one.

---

### Post by tombo465 on 2008-08-20
i had a similar problem . i could navigate to about 3 websites then it would slow down to the point of not being able to keep up with my typing (thats realy sloooow) i ended up switching over to seamonkey and have not had any problem since .

---

### Post by HandleWithCare on 2008-08-21
I'm having quite a similar problem. Sometimes when I try to view a site like [http://collegerama.tudelft.nl/mediasite/Viewer/?peid=b42173c4-27b4-4dfa-af02-6c8ca9995987]("http://collegerama.tudelft.nl/mediasite/Viewer/?peid=b42173c4-27b4-4dfa-af02-6c8ca9995987") firefox just shuts down. Then I can restart normaly but when restoring session it crashes immidiatly on the same page. The weird thing is, it happen quite rarely, for instance, youtube runs perfect...

---

### Post by neymac on 2008-09-25
I had the same problems with Firefox 3.01 and flash-player 10.
When opened some sites FF crashes.
Then I changed to Slackware 12.1 to keep working, and although konqueror 3.5.9 using flash player 9 did not crash, I notice some errors messages in file ~/.xsession-errors complaining about flash player when I opened the pages that crashed FF 3.01 in Ubuntu 8.04.
After find out that there was an update in Ubuntu for Firefox 3.0.2, I did the update and now FF3.02 works fine with flash_ player_10 plugin  untill now.

---

### Post by simtaalo on 2008-09-25
ive had no crashes since running the FF 3.02 update. hope it carries on

---

