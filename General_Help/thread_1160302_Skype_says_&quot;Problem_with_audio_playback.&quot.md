---
title: "Skype says &quot;Problem with audio playback.&quot;"
date: 2009-05-15
forum: General Help
---

### Post by bhishan on 2009-05-15
Hi, I have a Dell inspiron 1525. I recently installed Skype. In Skype, when I use the Skype Test Call, it says "Problem with audio playback". What does this mean? I have inbuilt microphone in my laptop.

---

### Post by HOLY COW on 2009-05-15
> **bhishan said:**
> Hi, I have a Dell inspiron 1525. I recently installed Skype. In Skype, when I use the Skype Test Call, it says "Problem with audio playback". What does this mean? I have inbuilt microphone in my laptop.

Have you done the setup of your audio capture device in skype ?

Either way change your audio playback device to pulse, see if that works? (worked for me)

I am not on my ubuntu machine right now so cant help you with details. Hope it helped !

---

### Post by kiridude on 2009-05-16
I also am trying to set up skype on a dell inspiron 1521 for my wife, but can't get the mic to work. 

Holy cow, the sound works perfectly set to pulse, but the microphone does not. Any further suggestions?

---

### Post by HOLY COW on 2009-05-16
> **kiridude said:**
> I also am trying to set up skype on a dell inspiron 1521 for my wife, but can't get the mic to work. 

Holy cow, the sound works perfectly set to pulse, but the microphone does not. Any further suggestions?

OK, try setting all your audio options to > Pulse < it should work.

IF that does not work then just change the > audio input settings while keeping the others on Pulse < it should work too.

Hope it helps.

---

### Post by tacantara on 2009-05-16
Welcome to the "Skype/Microphone Dilemma Club."  Have you checked the microphone using Sound Recorder?  If you can't record your voice on that app, then the issue should be fixable by tweaking some settings.  I received some excellent advice on adjusting the microphone on this thread:  [http://ubuntuforums.org/showthread.php?t=1073884](http://ubuntuforums.org/showthread.php?t=1073884)
 
If the suggested fixes in that thread don't work for you, try checking out the recommended fixes on this thread:  [http://ubuntuforums.org/showthread.php?t=1153117](http://ubuntuforums.org/showthread.php?t=1153117).  Although this fix involves a KDE audio mixer, it will also work in GNOME.
 
Once you've applied the fixes, test your mic in Sound Recorder.  If you can record your voice, you should be able to talk in Skype.  Go to the Skype Options menu (Ctrl+o). Select Sound Devices from the left pane, and set everything to Default Device. Make sure the "Allow Skype to automatically adjust my mixer levels" box is unchecked.
 
Good luck!  :)

---

### Post by kiridude on 2009-05-16
Thanks for your replies guys.

I got skype working now by setting all the settings to "pulse" and enabling "capture" and "+50db" Mic" in "volume control." It may be my imagination, but I think the mic is louder like this. It is also important to go to the "Recording" tab to un-mute the mic settings as it seems that they are muted by default (?).

PHEW! what a hassle! Skype has not tried hard enough and I will be researching alternatives such as ekiga, gizmo, etc. PLUS not being open source, who knows what eavesdropping agreements they may have...

I am a paying customer for skype by the way...

---

### Post by bhishan on 2009-05-19
Heres a solution that worked for me. Use the following commands in terminal:

killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo rm /etc/X11/Xsession.d/70pulseaudio

As you can see this method uninstalls pulseaudio and installs esound instead.

---

### Post by d3ngar on 2009-05-19
Tacantra's first link solved everything for me.

It seems that audio capture is muted by default. You have to make this available in Audio Control by selecting Preferences > Capture.
This 'unlocks' a new tab in which you can turn up the capture volume, but be careful of too much and also switch of the audio playback to avoid feedback..

---

### Post by Morpholinux on 2010-01-03
hi Bhishan..
I am thinking in doing what you said, but your reply was some months ago...
that still works??
..
I've tried Ekiga before...ummh unfortunately not everybody have an account..

While trying Skype beta 1.0.3.0.0.93 (on my Sony Vaio vgn-nr220fe)
....first...I could not make or receive any calls...(click on the "start call" green button but immediately finished..saying something like --problem with audio playback-- )

So...I Changed my sound devices:
"default"--> "pulse" 
like Kiridude suggested
thanks Kiridude

Now I can make the calls, but Skype works very slowly..... well; more like If a say something, appears 5 minutes later in the Mac of my sister ...I am able to see her with no problems...but cannot listen to her.....
also I can make the call to the "skype test call"..but I cannot hear a thing..
uhhmmm and If I want to "end call" with somebody...Skype does not allow it..so I have to kill the process in the terminal with top
besides that....skype uses a lot of cpu 57->84% ...that's normal?

well I am not an expert on 
computers...
skype
or
Ubuntu..

but I think every daily problem in our life have a solution or more than one.....
so...can I have a more..faster conversation?...and listen to everybody else?
it's the problem Ubuntu vs Mac?..
...
Haven't tried anything yet with another Ubuntu user...

or with windows users...
I will tell you later...


ps.
btw...I think I heard something...that looks like Skype but it's free like Ekiga ...I was dreaming?

2nd ps. If I have some mistakes in my english...well sorry it is not my native language.....

---

### Post by Morpholinux on 2010-01-03
again me...sorry need email notification and I dunno how to change that...but by doing a new reply and changing the option on the notification type...

---

### Post by kiridude on 2010-01-04
Morpholinux, as a first step I would suggest you update to the latest version of skype (2.1.0.47...from their website), and also the latest version of Ubuntu (although this is not as important).

If you do not know how to install from the site, post back.

I found that all my problems with skype were solved in their new release.

---

### Post by Morpholinux on 2010-01-16
Hi....Yep...I installed skype from the synaptic package manager...
...
have problems with my sound....
and then realize was not the version you said
after..I uninstalled (completely)
and go to  [http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)
for Ubuntu 8.10+ 32.bit did work!!

both video and sound have very good quality...

thanks!!

---

### Post by kingm on 2010-07-24
As well as changing all to pulse, you may need to turn off Skype's automatic level setting. I found it reset the microphone volume so low that it appeared to be not working.
(10.04 on Inspiron 1525)

> **kiridude said:**
> I also am trying to set up skype on a dell inspiron 1521 for my wife, but can't get the mic to work. 

Holy cow, the sound works perfectly set to pulse, but the microphone does not. Any further suggestions?

---

