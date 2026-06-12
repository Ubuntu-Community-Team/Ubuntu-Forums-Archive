---
title: "Headphone switch in jaunty"
date: 2009-05-04
forum: General Help
---

### Post by kboy on 2009-05-04
hi
i don't have a headphone switch in the volume control, it means that the headphones on my laptop and the speakers work at the same time.

I didn't have this problem with ubuntu 8.10. I really hope there is a solution to the problem because the many threads i've seen on the subject didn't have a solution,

thanks

---

### Post by kboy on 2009-05-16
anyone?????
i've posted it a while ago but still have not found an answer

---

### Post by Tipped OuT on 2009-05-16
Have you tried adding the head phone volume control? There's some option to select other volume controls, I'm not on Linux ATM, so try to see for yourself. :p

---

### Post by kboy on 2009-05-16
I don't have a problem with the headphone volume control, the headphone work fine, the problem is they work together with the speakers.
when i mute the speakers so does the headphone mute with them.

I need the switch that will control which device i am using at the moment.

---

### Post by Tipped OuT on 2009-05-16
Oh, same problem here. Can't do any thing about it I guess, I already asked this question in these forums a long time ago and no answer. I'm lucky though, because my headphones has it's own little volume control (not on the computer, I mean physically), so I can have my head phones volume set to max, but still controll how loud it is through the physical volume control.

---

### Post by kboy on 2009-05-19
Is there really no solution???

---

### Post by kboy on 2009-06-12
anyone??????????????

---

### Post by mharrison on 2009-06-12
Not sure if this is valid or not, but a quick Google search yielded
[http://vaioubuntu.wordpress.com/2009/01/03/headphones-detection-auto-switch-off-laptop-speakers/](http://vaioubuntu.wordpress.com/2009/01/03/headphones-detection-auto-switch-off-laptop-speakers/)

HTH

---

### Post by trivialpackets on 2009-06-12
Seriously?  I'm pretty sure my ubuntu has controls separated out.  I am not at my ubuntu now, so I can't tell you the wording, but when I click on the volume applet, it brings up a little slider.  On that screen, there is a button that if you click it you can control it individually.  Not perfect, but I believe it works, and was there as of this morning!  Hope that helps and I'm not just crazy.

---

### Post by kboy on 2009-06-12
> **mharrison said:**
> Not sure if this is valid or not, but a quick Google search yielded
[http://vaioubuntu.wordpress.com/2009/01/03/headphones-detection-auto-switch-off-laptop-speakers/](http://vaioubuntu.wordpress.com/2009/01/03/headphones-detection-auto-switch-off-laptop-speakers/)

HTH

it didn't work, I didn't even this file, so i created one, rebooted and nothing changed. 

The volume of the front controls the front and the headphones, and the same with the headphones volume which controls both the headphones and the front speaker.

---

### Post by Chronon on 2009-06-12
Hardware specific, maybe?  I am using Jaunty (UNR) on my EeePC 1000HE and it works as expected -- plugging in headphones mutes the speakers.  It also works on my desktop machine (running Jaunty) with the front headphone jack.

---

### Post by kboy on 2009-06-12
I have an MSI PR600 Laptop' but i dont think it's a hardware related problem. previous version of Ubunut never had this problem.

---

### Post by muctadir on 2009-06-12
kboy..
sorry for jumping into your thread. i am facing the same problem. plugging in headphones does not mute the speakers. i guess this is not only my problem, many of us having the same problem. if any one knows or finds out the solution, must post it.
thank you.......

---

### Post by kboy on 2009-06-14
where is the solution????
I've tried more than a dozen of different solution, all of which are for ubunutu gusty, non of them worked!!!

What to do???????

---

### Post by stolenfat on 2009-06-18
im getting the same problem bum chow!

---

### Post by kboy on 2009-06-19
I'm sorry to bounce this thread again, but i'm still in hope that someone with a solution will see it!!

---

### Post by yoasif on 2009-06-19
> **kboy said:**
> I'm sorry to bounce this thread again, but i'm still in hope that someone with a solution will see it!!install gnome-xchat, connect to irc.freenode.net -- join #alsa and ask for help.

---

### Post by muctadir on 2009-06-20
if someone have the solution, please post it here.......

---

### Post by ShepHeard on 2009-07-05
Sorry - no solution, just the same problem. 

I remember I had the same problem when I first installed 8.10, but can't remember what I did/installed to fix it.

I'm running 9.04 on an HP Compaq nx6325. 

If I boot the machine up with the headphones plugged in, then the sound plays only through the speakers. However, when I unplug them it doesn't switch back.

I'm getting tired of everyone hearing my conversations on Skype, or having to reboot each time I want to make a call...

Come on guys - there must be a solution somewhere...

---

### Post by Drk Guy on 2009-07-05
I've read somewhere that only the latest Alsa drivers solve your issue, as the ones shipped with Jaunty are outdated, so follow this instructions:

1. Update ALSA
 For some odd reason, the phonon-gstreamer backend didnt work until i updated ALSA compiling it from source (?), so i'll teach you how to do that:
 
 1.1 Check the links
 Fire up your favorite note-taking app and copy-paste the download links that appear in [www.alsa-project.org](www.alsa-project.org) for:
 - Alsa driver
 - Alsa lib
 - Alsa tools
 
 1.2 Download Stuff
 Now, fire up a console, and create a special directory for those files, then:
 
Code:
wget <link>
As of today (4th of July), the latest version is 1.0.20, so i'll post steps for those:
 
Code:
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)
Code:
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2)
Code:
wget [ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.20.tar.bz2)
1.3 Extract the archives
 Now that you have those on a folder, do as follows:
 
Code:
tar xvjf <filename>
for each file, that will extract them to an almost-usable state, if you're lazy enough to write down the complete filename (as i do ) you can just write down "alsa-l" and push TAB (If you're using bash, if you dont know what the hell is bash, just push it, idk about other shells) so the filename of the alsa lib package will be auto-completed, so you dont have to write it down, do it again for each of the three files, those commands will generate three different folders with similar names to the ones of the compressed files.
 
 1.4 Compile
 Now i'll only explain this once ¬¬ (Hey, i'm volunteering my time ), cd into alsa-driver folder (remember the Tab thingy? it works for *virtually* anything...) and run this:
 
Code:
 sudo apt-get -y install build-essential ncurses-dev gettext xmlto linux-headers-`uname-r`
 (That wasn't actually *compiling* the program, this was the easy part, installing the dependancies  now do this:
 
Code:
 ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
 (The hda-intel thingy is for ppl using realtek integrated HD audio, that can also be re-branded as nVidia HD audio, Intel HD audio, Ati.... it doesnt matter if you compile it or not if you dont have one of those AFAIK, but if you have one, DO IT ...ot (4chan?), After it is complete, just run 
Code:
 make && sudo make compile
 It will ask you for your password (If you aren't on sudo'ers file, you're out of luck), insert it and let it run, after it is done, run this 
Code:
 cd ../ && cd alsa-utils-1.0.20
 (Remember, this guide is done as of 4th of July, filenames could change with version changes, so you might get an error or two, but you should be able to fix it by now if you have some brains), after that, just copy-paste this into console [code] ./configure && make && sudo make install [/install]
 
 1.5 Reboot (You might want to do this AFTER step 2, to save time)

They were copied from another tutorial of mine (Too lazy to adpat to this specific case xD)

Hope this works for you guys, bump me up if it does (PM) ;)

---

### Post by ShepHeard on 2009-07-06
Cheers Drk Guy,

I tried this, but still no joy for me - still not switching off the speakers when the headphones are plugged in...

Any further ideas?

---

### Post by ShepHeard on 2009-07-06
Actually - now,, having done the above I get the old 

> "Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'"

when I try to test the mic in System/Prefs/Sound

This is depressingly similar to my experiences with 8.10. Has anything changed?


[EDIT] I've got my own thread on this [here]("http://ubuntuforums.org/showthread.php?t=1205190") where I'll log my progress... If I have any...

---

### Post by Student Driver on 2009-07-24
I came to fix a skipping MP3 issue, and found this thread:

[http://ubuntuforums.org/showthread.php?p=7670920](http://ubuntuforums.org/showthread.php?p=7670920)

I followed post #13, and removed pulseaudio.  Once I did that, my skipping and headphone jack issues went away.

There's another link to a possible fix for the headphone jack over here:

[http://ubuntuforums.org/showthread.php?t=780029](http://ubuntuforums.org/showthread.php?t=780029)

---

### Post by ShepHeard on 2009-07-25
@Student Driver: This is something I tried while going through exactly the same problems with 8.10. The problem is that Pulse Audio is very deeply (and badly) integrated with Ubuntu, and so I'd worry about simply removing it. 

Anyway, I've found the solution: Start again with Kubuntu. It doesn't use Pulse Audio.

---

