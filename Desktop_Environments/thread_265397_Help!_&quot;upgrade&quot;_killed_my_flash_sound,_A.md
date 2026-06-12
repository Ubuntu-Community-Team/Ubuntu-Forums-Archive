---
title: "Help! &quot;upgrade&quot; killed my flash sound, ATI drivers,  AND my usb mouse!"
date: 2006-09-25
forum: Desktop Environments
---

### Post by ogami1972 on 2006-09-25
So... I just had to have cinelerra. I just had to get it no matter what. so, I used the sources list [here]("http://www.daniweb.com/blogs/showentry.php?entryid=769#comments")

Since, I have lost flash sound, my USB remote mouse, and my abiltiy to install ATI proprietary drivers ( the steps work fine like always, but no results).
I know this was a true noob error, but i'm really hoping I can fix it...

---

### Post by BorgHunter on 2006-09-25
Did you try restoring your old sources.list, then updating apt and running an upgrade?

---

### Post by ogami1972 on 2006-09-26
hmmmm...no, not yet. So far
a. amarok/xine plays, just no 'internet' sound (youtube (i'm missing lonelygirl15 episodes!), google, badgerbadgerbadger all dead). This occurs in all browsers. Have tried downgrading flash-plugin, to no effect. alsa-oss already installed, firefoxrc already modified. "sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1" results in "ln: creating symbolic link `/usr/lib/libesd.so.1' to `/usr/lib/libesd.so.0': File exists" Preferred Browser : swiftfox
b. USB mouse must be unplugged/plugged to be recognized (appears to be sporadic at this point- may be fixed).
c. NO fixes for ati drivers have worked, proprietary or otherwise. X currently set to 'fglrx' manually; results in 'mesa' issue (which, granted, is better than an X crash).

](*,) 
Keep in mind: 6 hours ago, I had a system that has been 'up' since 6.06 was released, with EVERYTHING working properly, including all problems listed above. I have been producing and recording multi-track audio ( and probably stll can),playing all the cool games like cube and tremulous and bzflag, watching all internet media <flash8, editing vids with avidemux, and generally laughing at windows users with that "oh, you silly little man" laugh i reserve for people i pity.

[Here]("http://www.daniweb.com/blogs/showentry.php?entryid=769#comments") is the sources.list i used. avoid at all costs.
[URL="http://pastebin.com/794545"]
Here[/URL] is the pastebin from my upgrade detailing the changes. 

Pity me. I am going to bed now. I am sad. 
p.s. any help is , of course, appreciated.

:KS  edit: tested suggestion above- thank you, but it did not work. Although my mouse worked properly after reboot ( maybe subsequential and inexplicable at this point). However, during reboot, i recalled what should have been #4 from the list above.
4. Usplash is no longer functioning (no great loss). Still shows as installed and listed in GRUB line.

---

### Post by WalmartSniperLX on 2006-09-26
try ctrl+alt+backspace and log back in 

I dont have 100% assurance this will help but give it a try :D

---

### Post by ogami1972 on 2006-09-26
unforunately not, but thank you. I'll be happy to join your movement once i am done beating my head on this keyboard.
I can never sleep when I have a problem like this.
HEY ALL YOU EMPLOYERS OUT THERE! DIG IT: i may not have the certificates, but i stay 'til the job is done ( i was refused an IT position based on my lack of discernible qualifications. Doesn't all this work count?)
anyway... updated Automatix and tried selecting "swiftfox plugins" and "mplayer FF", and so on and etc. (anything that looked related). This resulted in some potentially significant upgrades, but after a reboot, same as it ever was. :evil: 
Thanks anyway, Arnieboy.
I accessed 'about: plugins' in swiftfox; all seems well...um..ooookkk- went to check that swiftfox was 'saying' the same version of flashplugin-nonfree that I had (after all this, who can be sure?); fastest way to find which version of flash i was using I could think of was "apt-get install"; expected to see "already installed"- instead it is currently installing (?)- will be back with updates...:-k

edit: no luck. am off to bed for real now.
edit2: read about reported and experienced flash problems tried to install from macromedia directly. no luck. wah wah wah.

---

### Post by ogami1972 on 2006-09-26
UPDATE: flash and usb mouse now working. ATI drivers next on the bench. Here's what I did:

Here's what i did:
I discovered I had a package called 'libflash-mozplugin', and , what's more, the version of flash i call '.068' was giving an 'installation failed' notice during installation/upgrade.

1. remove libflash-mozplugin (i used synaptic- remember to right click and choose "complete removal" so as to remove any leftover config files!)

2.remove "flashplugin-nonfree"

3. reboot ( some steps maybe unecessary, but this is EXACTLY how i did it).

4 In synaptic , go 'settings>>properties' and select 'show package properties in main window'. apply. you should now see tabs 'description', 'common', 'dependencies', etc.

5. search or whatever to find and select 'flashplugin-nonfree'. go 'package>>force version...' and select the ".o63' version ( if you do not see an .063 version, let me know and i will send you my sources.list).

6. Install. Reboot ( again, probably unecessary)

7. In synaptic, search or whatever to find and select flashplugin-nonfree'.
 go 'package>>lock version'. Keep it locked and watch these forums until you hear '.068' flash is working.

8. Open firefox and enjoy the latest lonelygirl15 video!:D

(above copy/pasted from another post i replied too re: flash)

Usb problem
Where is 'hotplug'? Nowhere in my cache...
1. installed usbmgr

2 reboots and all is well. off to address ATI problems. Good Luck to both of us!

edit-usb mouse not working again...believe this to be kernel related ( discovered i am somehow using a mepis kernel- sneaky bugger must have slipped in....)

edit ok- ati drivers working, usplash is back, flash working, but still no usb mouse. HELP!

---

### Post by rlozano on 2006-10-18
this might help...

i have noticed that the default edgy ATI driver is actually causing the USB to die, not just the mouse. try pulling out your mouse from the USB port and plug it again. if you have an optical mouse, you will notice that it will not light up anymore...

i suggest that you upgrade your ATI driver to binary drive fglrx. this will solve the problem of the dying mouse/USB.

hope this helps...

---

### Post by cevans on 2006-11-10
In the future, you should be careful about using sources.lists that you find in unofficial places. This particular list was nearly gauranteed to cause serious damage to your installation.

---

