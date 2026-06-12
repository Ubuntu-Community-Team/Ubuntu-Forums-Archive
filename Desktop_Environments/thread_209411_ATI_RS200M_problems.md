---
title: "ATI RS200M problems"
date: 2006-07-05
forum: Desktop Environments
---

### Post by Bezdomny on 2006-07-05
It isn't really a problem just more annoying than anything else. Has anyone else suffered graphic corruption on dialogue buttons? 

The ATI is in a compaq presario 2529EA, set to 128MB shared on the 1GB mem, and more often than not when dialogues are on the screen the button images are corrupt, you can still see the text and when you move the mouse over them they clear. Everything else works fine, no corruption anywhere.

Any ideas? Fixes? Anyone having similar problems?

---

### Post by kvonb on 2006-07-05
Sounds like you are running the stock ATI driver, if you are feeling brave, and know how to back up your complete system BEFORE you start, I can help guide you through the installation "trial by fire" :)

Regards,  KEv :)

---

### Post by Bezdomny on 2006-07-05
Thanks Kev, I guess by full backup you don't mean full re-install? Been there, done that after installing the ATI drivers from the LXF mag DVD. It managed to sort of half install and glxinfo reported I lost direct rendering, which I have no, even with the button poo. So, I would like to walk the coals and find the cold grass at the end :-)  fire away my good man, one re-install is as good as another! 

Steve.

---

### Post by kvonb on 2006-07-06
OK, but I must warn you before you do anything:

This process could leave your system inoperable, I take NO responsibility for any damage you may incur, even if your house burns down and your dog gets eaten by an escaped lion!

This is a rough script that I wrote to simplify and automate the install and setup process of downloading and installing the fglrx drivers from the repositories and get 3d working.

It doesn't make any backups of config files or libs, so please don't scream at me if it does something you don't like, it is NOT malicious in any way but I advise that you read the script before running it to see what it will do.

Print these instructions if you are able, it will make it easier later.

First make sure that the Universe and Multiverse repositories are enabled in Synaptic (MENU -> SYSTEM -> ADMINISTRATION -> SYNAPTIC PACKAGE MANAGER, Settings -> Repositories, click add and select all the boxes)

Download the attached file to your home folder (~/), click on it to open the gzip and extract it to your home folder (~/).

Right click on the extracted ati-install.sh file and check properties to make sure it is executable. If not, just tick all the "executable" boxes then OK.

Open a term and run the script like so:

./ati-install.sh

First It resets your xorg.conf file to a clean default, if asked, choose "ati" as the driver, and choose the defaults for everything else.

It will now go off and download first the driver, then a lib file.  If any of these fail, stop the script (ctrl-c) and start it again.

When the downloads are complete and mucking about has stopped, a gedit window will pop up, 
look for the following section and copy/paste to make it look the same:

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
        Option	    "UseInternalAGPGART" "no"
EndSection

Save and exit gedit, then another one will pop up, add the following lines to the end of the file (if they are not already there):

	agpgart
	fglrx
	dri

Save and exit gedit.

Once the script has finished you must now reboot.

When successfully back in X  (if no X, see below for instructions on how to restore) open a term and type in:

fglrxinfo

You should now be told that you have ATI not MESA.

If not, bang head on desk and fetch a very large hammer :)


Recovery:
If you just want to get X back to your original config, type the following in a term:

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.stuffed
sudo cp /etc/X11/xorg.conf.before-script /etc/X11.xorg.conf

Hope you have joy!  Let me know how you went.

Regards,  Kev :)

---

### Post by Bezdomny on 2006-07-07
Thanks for that Kev, well worth the effort but I did manage to break it, so now there's a dent in my desk and slackware where Ubuntu used to be :-)

When it installed and I rebooted, the gdm error screen appeared telling my that no device was found. I vi'd the config and had to change fglrx back to ati in devices. That got me in but I had lost direct rendering and more screen poo than before. 

Running fglrxinfo gave some compaint about Free86x DRI (or similar) on display 0:0 missing. I messed around with the xorg.conf files, changing the order of devices/screens and gave up. Finally solved by installing Slackware. That probably won't last too long either, I'm new to linux (about a month) and I like to push big red buttons that say "don't push". I have a feeling I'll be breaking that too, and soon.

So thanks for the effort, maybe I'll try again, your script is in the vault :-)

Oh, incidently, I tried to install the ati drivers from Linux Format magazine DVD and when choosing to build for distro it complained about being unsupported for every one of them. Didn't notice that last time. 

Thanks again Kev.

Steve.

---

### Post by kvonb on 2006-07-07
Sorry to hear that!

I hope I'm not to blame for you switching to Slackwear?

The script is very "dirty" as it doesn't do any checks or backups.

I used the script on a fresh install of 6.06, after I'd done all the updates.  I'm not sure where it went wrong, did it download the driver AND the libGL.so.1.2 file successfully?

I can e-mail you my copy of the lib file if you feel like trying again.

I would suggest that nobody download and use that script until I've done some more work on it (I don't know off hand how to remove it myself).

I am waiting for a new mainboard that I bought on e-bay, when that arrives I will perform another fresh install and play around with the script, I should look into making it interactive or at least more user friendly.

For posterity purposes, here are my system specs:

AMD XP2000+ CPU
ECS K7S5A mainboard
512 megs DDR400 ram
Generic ATI 9200SE AGP video
onboard sound
3com 3C905C network card
80gig Seagate HDD (master on primary)
LG DVD re-writer (master on secondary)
PS/2 mouse
Ps/2 keyboard
Sony G500 screen

Regards,  Kev :)

---

### Post by Bezdomny on 2006-07-07
Kev, I don't think it was the script, using the ATI drivers off the LXF DVD did the same thing earlier this week. I did have a look at the script before I ran it and it seemed relatively straightfoward, download, install, default configure and user finish. Thanks for the effort.

I still have Ubuntu on the server so the move to slack was based on a "whats all this about then" nosey on google. Being new to Linux I guess you have to try a few before you find one that suits. I must say though, it got to 2am last night and I had finally got kde up, had a quick click and went to bed. Haven't looked at it properly yet but from what I saw, I do prefer gnome and Ubuntu seemed easier? Or better to say, friendlier? I'll probably end up flattening the laptop again and installing Ubuntu, it's been on and off more times that I can remember (and thats just this week!) :-) One day I might actually manage to get netbeans/anjuta/eclipse running and do some *real* work ;-)

Thanks again Kev, much appreciated.


Oh and specs:

Compaq Presario 2529EA /DVD/CDRW
1GB RAM
ATI RS200M (IGP 345 methinks)
Netgear WG511v2 Wireless (Marvel)
80GB HDD
15" LCD 1024*768
LOUD FAN!

and oh, oh before I forget: this is why another distro change
[http://www.tuxmachines.org/node/8031](http://www.tuxmachines.org/node/8031)   :-)

---

### Post by art on 2006-07-07
I think your graphics card is not supported by the fglrx driver, that's why it doesn't work and no matter how you install it it wont work. Mine is not supported as well, and I use the radeon driver, which is an open source, and has almost all the features of the propriatery driver.

---

### Post by kvonb on 2006-07-08
I tried the script on a clean install this afternoon and it worked perfectly for me.

I'm inclined to agree with art, you can check on ATI's website, there is a readme that lists the supported cards, I'm too lazy to do it myself :D.

I wish I could offer you some more help, I know how frustrating it is, I spent months trying to get my 9200 working with Cedega and Battlefield 1942!

I ditched the card several times, but eventually got it to fly.

I like the ATIs for 2 reasons, 1 they seem to give me a crisper, clearer pic than nvidia, and 2 they are about half the price so that is a good incentive for me :D.

Check ATI's website every so often, you might find a new driver will support it.  When it does, I will be happy to help you get it up and running.

All the best....Kev :)

---

### Post by Bezdomny on 2006-07-10
Thanks for the effort, as I said I went through the script and it seemed fine. I was trying to upgrade to get rid of screen poo on the buttons in Ubuntu, slackware didn't help things much with fighting over getting wireless to work and some other problems, so now the laptop has Kubuntu installed (probably the only one I hadn't tried up till then). No screen poo! Whey! Result! The laptop is only used for developing, I need it to cart around to customers etc so games level support isn't needed (until I get bored! :-) ) I'll keep looking on ATI though, but I won't hold my breath for drivers, it's an older machine now. 

Thanks again for the lendeth of hand. Now I can get some *real* work done, instead of fighing with it! ;-)

Steve.

---

### Post by afterxleep on 2006-07-11
Actually I have the same problem with corrupt graphics on buttons, and I'm on a IGP 320, wich is not supported by ati fglrx driver, and will not work.

By default, ubuntu installed the ati driver wich provides 2d acceleration only.  I  changed my system to use the radeon driver, in order to get some sort of 3D support, and see if that was the problem.

I have some sort of 3D support now, or at least direct rendering (DRM) working, but the problem with buttons is still there.   Any ideas?.

---

### Post by afterxleep on 2006-07-11
Actually the problem is not with your card.  Seems an issue with most ati's and the Default 'Human' theme from Ubuntu.  

Change to say, 'Clearlooks' theme and problem vanished.

---

