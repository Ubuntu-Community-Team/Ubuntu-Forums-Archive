---
title: "help with flash in firefox"
date: 2009-05-27
forum: General Help
---

### Post by searayman on 2009-05-27
I am trying to watch a cycling race at:

[http://www.universalsports.com/mediaPlayer/media.dbml?id=138747&catid=-2&sid=13044&db_oem_id=23000](http://www.universalsports.com/mediaPlayer/media.dbml?id=138747&catid=-2&sid=13044&db_oem_id=23000)

but i don't have flash working properly so it does not work. Please help.

---

### Post by taurus on 2009-05-27
Look in synaptic for flashplugin-nonfree.  Don't forget to restart firefox once you've installed it.

---

### Post by mick222 on 2009-05-27
Is it not also in ubuntu restricted extras.

---

### Post by searayman on 2009-05-27
> **taurus said:**
> Look in synaptic for flashplugin-nonfree.  Don't forget to restart firefox once you've installed it.

that website i posted above does not work still, although i believe i have flash now

any more ideas?

---

### Post by wpshooter on 2009-05-27
> **searayman said:**
> that website i posted above does not work still, although i believe i have flash now

any more ideas?

Go to this website and download and install the TAR version of Flashplayer for Linux.

[http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)

Write back if you need instructions for installing.

---

### Post by searayman on 2009-05-27
> **wpshooter said:**
> Go to this website and download and install the TAR version of Flashplayer for Linux.

[http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)

Write back if you need instructions for installing.

how can i check and uninstall any other version of flash i got?

---

### Post by Bender2k14 on 2009-05-27
> **searayman said:**
> that website i posted above does not work still, although i believe i have flash now

How does it not work?  What does it say?

---

### Post by taurus on 2009-05-27
> **searayman said:**
> how can i check and uninstall any other version of flash i got?

Remove it from synaptic.

---

### Post by searayman on 2009-05-27
> **taurus said:**
> Remove it from synaptic.

i dont know what all the other version are called

---

### Post by taurus on 2009-05-27
What other versions?  

By the way, which release are you running and is it 32bit (i686) or 64bit (x86_64)?

```
uname -m
lsb_release -a
```

---

### Post by Bender2k14 on 2009-05-27
> **searayman said:**
> i dont know what all the other version are called

You can remove all versions of flash by executing the following command:
```
sudo apt-get remove flashplugin-* --purge
```

After that, you can reinstall the flashplugin with the following command:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Newfoundlander on 2009-05-27
Verify that Flash actually has been installed.  Can you watch a video on YouTube?

The first time I went to YouTube, a grey bar appeared at the top of FireFox and asked if I wanted to install the plug-in.  I installed it and Flash automatically worked in both Firefox and Opera.

---

### Post by wpshooter on 2009-05-27
Again, install the complete FlashPlayer from their website and forget about all of these plugins, etc. found in Synaptic, etc. and you will find that once you have installed the complete Flashplayer from their website you will no longer have the problems you are having.

Good luck.

---

### Post by Bender2k14 on 2009-05-27
> **wpshooter said:**
> Again, install the complete FlashPlayer from their website and forget about all of these plugins, etc. found in Synaptic, etc. and you will find that once you have installed the complete Flashplayer from their website you will no longer have the problems you are having

Why are you so quick to recommend not using the package manager?

---

### Post by searayman on 2009-05-27
> **wpshooter said:**
> Go to this website and download and install the TAR version of Flashplayer for Linux.

[http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)

Write back if you need instructions for installing.

need help enterign path to install here is what i type and what it says:

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): usr/lib/mozila

WARNING: /home/mike/Desktop/install_flash_player_10_linux/usr/lib/mozila is not a directory.

---

### Post by searayman on 2009-05-27
ok i have flash just that one website i initialy posted isnt working...

---

### Post by Bender2k14 on 2009-05-27
> **searayman said:**
> ok i have flash just that one website i initialy posted isnt working...

How is it not working?  What is the error message?

---

### Post by searayman on 2009-05-27
> **Bender2k14 said:**
> How is it not working?  What is the error message?

the whoel flash player isnt loading or playign the online video of the bike race

---

### Post by wpshooter on 2009-05-28
> **Bender2k14 said:**
> Why are you so quick to recommend not using the package manager?

Because "in this instance" package manager does not seem to give completely functionality to Flash.  However, normally it is a good idea to install exclusively from Synaptic.

---

### Post by lordbux on 2009-05-28
ok 
from what i can see you need to go through a complete list of steps.

first uninstall the package manager version fully.
```
sudo apt-get install flashplugin-nonfree --purge
```

Second: identify your Distro 
see which one it is.

if you are using HARDY or JAUNTY 
select .deb for ubuntu 8.0+ from the drop down box here
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

then double click and select install. 
CLOSE ALL APPLICATIONS INCLUDING FIREFOX.

or you may install it from
the other tar package.
just make sure that you have closed all the applications and Firefox.

---

### Post by Bender2k14 on 2009-05-28
> **lordbux said:**
> ok 
from what i can see you need to go through a complete list of steps.

first uninstall the package manager version fully.
```
sudo apt-get install flashplugin-nonfree --purge
```

Second: identify your Distro 
see which one it is.

if you are using HARDY or JAUNTY 
select .deb for ubuntu 8.0+ from the drop down box here
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

then double click and select install. 
CLOSE ALL APPLICATIONS INCLUDING FIREFOX.

or you may install it from
the other tar package.
just make sure that you have closed all the applications and Firefox.

What are you talking about? searayman said:

> **searayman said:**
> ok i have flash just that one website i initially posted isnt working...

That means that it is probably something about this specific website and not searayman's flash install in general.

How about this...  someone confirm that they are able to watch a live bike race from that website.  I just tried and it didn't work.  The player seems to load, but the screen stays black and none of the buttons are clickable (although the volume button appears to be clickable, clicking it does nothing).

---

### Post by Bender2k14 on 2009-05-28
The Univseral Sports website says ([here]("http://universalsports.tv/Video_Help.html")) that their video service recently changed (around May 12th) and you might experience problems.  I submitted a "problem report" which included a link to this thread.

---

### Post by Bender2k14 on 2009-05-28
Here is their response:

> We do not support the Linus OS, so I'm unsure of any settings or set up which would allow for the successful viewing using it as the OS.

Thank you,

Les, JumpTV Fan Support

Do we think that their video service should work even if they do not officially support Linux/Ubuntu?

---

### Post by lordbux on 2009-05-31
There reply donot make sence.

as they are not using any preparatory software of there own and not using any special format it does not make sound  that the application can be dependent on the OS.
it should be dependent only on a a third party tool ( FLASH IN THIS CASE).:KS

so it seems its an internal error with any of your settings or there site is having a handshake problem with your browser.

I am sorry abut my previous reply.
anyway i will analyze  there site and try to find a reason. :popcorn:

---

### Post by lordbux on 2009-06-07
it seems the site seems normal..........
as it is using flash it should work fine on Linux as long as you have flash.

it seems that there is some configuration error with your browser, system or and inbuilt factor of the site.

tested the site with 7 distros ..all ran well

if you have cleard the problem then please report

---

### Post by Ed_Ziffel on 2009-06-07
Installed flash from the adobe site on 8.04 lts. Video but no sound.  Did the searches.  Tried at least 5 different suggestions but still no sound.  Music plays, sound scheme tones etc. but no sound with flash.  Others are having the same issues.  

Is there some good old boy or girl out there who knows whats up with this for sure?

---

