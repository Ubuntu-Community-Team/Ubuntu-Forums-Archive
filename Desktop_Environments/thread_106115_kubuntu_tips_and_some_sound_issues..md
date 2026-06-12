---
title: "kubuntu tips and some sound issues."
date: 2005-12-19
forum: Desktop Environments
---

### Post by PsychoTrauma on 2005-12-19
I have been a gnome user for a long time and have been wanting to experiment with kde lately. I have done a fresh install of kubuntu and updated kde and amarok to their latest versions. I was wondering if some kde users could tell me some things they usually do after a fresh install to make things more personal. I also seem to be having trouble playing multiple sounds at once after system bells go off. An example is I will be listening to amarok and i'll minimize a window and the the system bell will take over and block amarok from playing. I used to set up dmixing to solve problems like this on gnome but since breezy is supposed to be already set up like that i'm not sure what my next step should be. I have a turtle beach catalina sound card and it is using the ICE1724 driver.

---

### Post by jobezone on 2005-12-19
Tip #1: Install the **yakuake** package. Run it, and by pressing F12, you can drop down or hide it (terminal window). It's pretty cool, and simillar to quake's terminal screen)

---

### Post by PsychoTrauma on 2005-12-19
[QUOTE=jobezone]Tip #1: Install the **yakuake** package. Run it, and by pressing F12, you can drop down or hide it (terminal window). It's pretty cool, and simillar to quake's terminal screen)[/QUOTE]

Thank you for the tip I gave the program a try and it seems very useful.

(error I get from amarok = ) [GStreamer Error] ALSA device "default" is already in use by another program.

---

### Post by ltmon on 2005-12-20
[QUOTE=PsychoTrauma]Thank you for the tip I gave the program a try and it seems very useful.

(error I get from amarok = ) [GStreamer Error] ALSA device "default" is already in use by another program.[/QUOTE]

Try turning of artsd.  As far as I can tell it screws up nearly everything.

(Note: this is from memory... it may be a little off)
1. Go to KMenu->System Settings
2. Click on "Sound and Multimedia"
3. Click on the "Enable the Sound System" check box (to disable it)
4. Click on "Apply"

5. Optional: If you still want notification sounds keep going, otherwise you're done
6. Click on "Notifications", and one one of the advanced tabs you can tell it to use an external sound player.  "mplayer" is excellent for this (if you have it installed).  Any other command line media player should work.

Hope it works.

L.

---

### Post by PsychoTrauma on 2005-12-20
[QUOTE=ltmon]Try turning of artsd.  As far as I can tell it screws up nearly everything.

(Note: this is from memory... it may be a little off)
1. Go to KMenu->System Settings
2. Click on "Sound and Multimedia"
3. Click on the "Enable the Sound System" check box (to disable it)
4. Click on "Apply"

5. Optional: If you still want notification sounds keep going, otherwise you're done
6. Click on "Notifications", and one one of the advanced tabs you can tell it to use an external sound player.  "mplayer" is excellent for this (if you have it installed).  Any other command line media player should work.

Hope it works.

L.[/QUOTE]

Thank you for the help, I have been turning the sound system off already but I wanted a way to keep both which you provided. I will give it a try asap with a couple different apps and see how it goes since I don't have mplayer installed. I guess I should have looked in the advanced options. :cool:

---

### Post by ace2005 on 2005-12-20
Well i would say use arts:

Go into Synaptic and do a search fo gstreamer and install the output plugins like "gstreamer0.8-alsa" and you may also want to install some of the codecs.

And then in Amarok go into Settings > Configure Amarok > Engine

Choose Gstreamer as the engine and the output plugin as "artsdsink"

Then go into Kcontrol > Sound and Multimedia > Sound System

Enable the sound system, set "Auto-suspend if idle after" to 1 second, then in the hardware tab choose the audio device of you're choice (i use ALSA)

Apply the changes and music should work in Amarok and KDE

Tip: Install Xine to play videos, i've found it is better than mplayer

Edit: installing  "amarok-arts" and choosing that as the engine may also work but i haven't tested it

i use Juk because some of the songs in my collection don't have names and so i used File > New > Playlist from Folder (Ctrl + D). Everything in the folder and its subfolders you select will be added to the playlist, this helps when all the songs are in the right folders but they're all neamed something like Track2.mp3 Then i have a list of albums down the left side. You have to not show it where you're collection is when it first starts and then add the folders one by one

---

