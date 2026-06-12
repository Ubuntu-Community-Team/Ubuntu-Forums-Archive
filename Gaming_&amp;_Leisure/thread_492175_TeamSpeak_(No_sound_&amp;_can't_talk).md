---
title: "TeamSpeak (No sound &amp; can't talk)"
date: 2007-07-04
forum: Gaming &amp; Leisure
---

### Post by Incarnadine on 2007-07-04
I downloaded TeamSpeak from the add/remove list and I don't get any sound nor can I talk. I have my mic set on "Push To Talk" and when I press my caps lock down the green light doesn't even light up. I checked to see if maybe my mic or speakers were muted in TS or my Volume Control, but everything was set-up right. Maybe it's a problem with my mixer? I checked to see what mixer TS was set-up for and only seen oss/dev/dsp. Where is the ALSA mixer? Do I have to add that somehow? Any advice or help would be great. Thanks.

---

### Post by Haz13r on 2007-07-04
Yea i had the same exact problem.  I cant hear anybody or even talk to anyone.  Although i installed it a different way by installing it from the Website.  goteamspeak.com.

---

### Post by Insomn1a on 2007-07-04
if your using a USB headset, click on other in the TS options, and type /dev/dsp1



that fixed my problem.

---

### Post by Incarnadine on 2007-07-04
No I'm not using a USB headset. I am running TS on my laptop and the microphone and speakers are intergrated in the laptop. I know my mic and speakers work fine because I can record my voice and listen to music. It just doesn't work for TS. I have no clue what's wrong here.

---

### Post by Insomn1a on 2007-07-04
is your operation system currently using the OSS drivers? or ALSA?

---

### Post by Incarnadine on 2007-07-04
It is using ALSA. I checked the supported mixers in TS and I only saw oss/dev/dsp. Where is the ALSA? Should I add this somehow?

---

### Post by Insomn1a on 2007-07-04
i remember seeing a thread on linux-gamers.net about running TS with alsa, ill start looking and edit this thread with the link.

---

### Post by splintercellguy on 2007-07-05
Solution: use the alsa-oss wrapper.

sudo apt-get install alsa-oss

aoss ./TeamSpeak

---

### Post by Incarnadine on 2007-07-05
Ok I installed alsa-oss, but I don't know what you mean with "aoss ./TeamSpeak". I don't understand that. Maybe that's why my problem isn't fixed.

---

### Post by Insomn1a on 2007-07-05
go to accessories then go to terminal



type aoss ./teamspeak

---

### Post by Incarnadine on 2007-07-07
I typed that in the terminal, but this is my result.

incarn@Incarnadine:~$ aoss ./teamspeak
exec: 13: ./teamspeak: not found

---

### Post by splintercellguy on 2007-07-07
Well, you would do that in the directory where TS is installed, or alternative supply the full path.

---

### Post by Incarnadine on 2007-07-09
I don't exactly understand what you mean. Are you talking about typing in the whole directory and then the command? If so then I already tried that and got nothing as a result. It didn't register as a proper command. Could you give me a example of what you mean?

---

### Post by Delirious on 2007-07-09
I have a similar problem except i can hear but not speak, when i hold down the button to talk it llights up and others can hear themselves through my speakers but cant hear me.

I tried that aoss ./TeamSpeak and it didnt work.

Tried that wrapper for alsa and it said i already had the latest.

I have no idea what else to try

---

### Post by Haz13r on 2007-07-10
Well, if anyone finds a solution to this, please PM me.

---

### Post by Incarnadine on 2007-07-10
Delirious it sounds like you have the wrong capture input checked in your volume control. Go into your volume control and then click on the "Switches" tab. Then check your  "Microphone Capture". That should solve your problem. Post back on the forum and let me know if everything went ok. Good luck.

---

### Post by Quasimodo316 on 2007-07-10
I just right click on the shortcut, add to panel then edit the properties of the panel to be 'aoss teamspeak'.  It seems to work ok (as long as aoss supports your card).

---

### Post by Praill on 2008-01-13
I had this same problem. Incarnadine is on the right track, but isn't explaining very well. What I had to do is double click the speaker icon on the main bar by the time. This brings up your volume and sound devices settings. 

I had to click on Edit-->Preferences and then check all the unchecked options. Then go over to the recording tab and turn both devices on. Then go over to the Options tab and set to mic.

I also set my teamspeak sound driver device to /dev/audio and ran the teamspeak executable through the aoss wrapper by typing ```
 aoss teamspeak 
``` in a terminal.

---

### Post by marmiteOlz on 2008-01-14
ok i had the same / similar problem   i could hear but no one could hear me
i double clicked the volume button on the sys tray
on edit-preferences i clicked on  the analogue source check box
then selected  mic and for me it worked
mine was using alsa as default when i checked
 hope it helps

---

### Post by asipi on 2008-01-29
u need a full hardware duplex soundcard in either to teamspeak to get it work (e.g. SB Live!) nowadays integrated 'soundcards' are not the proper hw to use it.
unfortunatelly TS uses the old oss interface for streaming and capture sound data and that is obsolote.
the new teamspeak 3.0 platform will use alsa, but it has not finished yet.

---

### Post by Sugi on 2008-10-21
Sorry to breath life to this old thread.

I installed TeamSpeak through their website, but I was having issuess with audio.  Thanks to this thread.  Everything is working.


wget
[ftp://213.202.254.114/teamspeak/releases/ts2_client_rc2_2032.tar.bz2](ftp://213.202.254.114/teamspeak/releases/ts2_client_rc2_2032.tar.bz2)
cd /home/USR/Desktop
tar -jxf ts2_client_rc2_2032.tar.bz2
cd ts2_client_rc2_2032
sudo chmod 755 setup.sh
sudo ./setup.sh
sudo apt-get install alsa-oss
aoss /opt/teamSpeak2RC2/TeamSpeak
(^to run TeamSpeak)

**Note: I ran TeamSpeak after having Opera and Wine open. So with the aoss command I can use audio with TeamSpeak and having working audio with Opera and Wine.

Specs:
Ubuntu Hardy Heron
TeamSpeak Linux Client 2.0.32.60
Audio Mic Slot Logitech

Sugi

---

