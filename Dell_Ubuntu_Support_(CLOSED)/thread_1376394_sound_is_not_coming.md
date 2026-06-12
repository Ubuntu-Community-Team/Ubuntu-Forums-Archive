---
title: "sound is not coming"
date: 2010-01-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by renjumace on 2010-01-09
i have installed ubuntu in my dell inspiron 1525 laptop. earlier i had problems with the video as it was not playing but i managed to fix it. but the sound is still a problem. no sound is coming while a movie is played or music is played. please see me through this problem...

---

### Post by renjumace on 2010-01-09
please anybody give a reply... i am in urgent need...

---

### Post by mikewhatever on 2010-01-09
Which version of Ubuntu did you install?
I suggest starting with the first stages of the [Comprehensive Sound Solution]("http://ubuntuforums.org/showthread.php?t=205449") thread. Find out if your sound card is recognized, if the module is loaded, etc.

---

### Post by renjumace on 2010-01-12
> **mikewhatever said:**
> Which version of Ubuntu did you install?
I suggest starting with the first stages of the [Comprehensive Sound Solution]("http://ubuntuforums.org/showthread.php?t=205449") thread. Find out if your sound card is recognized, if the module is loaded, etc.

man i tried the comprehensive sound solution as u said. but there is a problem when i try out the step 3 in the solution thread. my chipset is ICH8, but after searching intel provides drivers upto chipset ICH7, as upto it was only listed there. hence i could figure out that there was no driver for my chipset. but as i said earlier that i am using dell inspiron 1525 and this model is supported by dell for ubuntu. so is there a way that i could overcome by problem? i had another guy replying to one of my other thread about the same problem but his solution also didnt work. please help me out man... thanks for ur time.

---

### Post by garvinrick4 on 2010-01-12
[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][SIZE=4][B]This has worked for me on three installs 
[/B][/SIZE][/SIZE][/FONT][/COLOR]


[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][SIZE=4]**Part A: Common instructions (Hardy, Intrepid, Jaunty & Karmic)**[/SIZE]
*All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.*

1. Backup (and then delete) your previous configuration files: [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ rm -r ~/.pulse ~/.asound* [/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo rm /etc/asound.conf[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#ff0000]**Warning:**[/COLOR][COLOR=#ff0000] As always, use caution when removing files on your system. Any typos can potentially cause data loss.[/COLOR]
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Don't worry if some of these files did not exist on your system.[/COLOR]


2. Ensure you have the necessary PulseAudio libraries and configuration utilities installed:[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000] [FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio[/SIZE][/FONT][/COLOR] [[COLOR=#444444][FONT=Verdana, Arial, Tahoma][SIZE=2]_3_[/SIZE][/FONT][/COLOR]]("https://bugs.launchpad.net/bugs/192888")[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]. Ensure the evil "libflashsupport" library is [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]**not**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2] installed: [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks![/COLOR]

4. (Karmic users - please skip this step, it's not necessary). Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.[/COLOR]

5. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:[/COLOR][/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ pulseaudio & pavucontrol[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]6. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a common bug in Intrepid and Jaunty):[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ alsamixer [COLOR=#0000ff]-Dhw[/COLOR][/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer.[/COLOR]

7. Continue to **Part B** if you are running Hardy Heron (8.04), or **Part C** if you are running Intrepid Ibex (8.10). If you are running Karmic Koala (9.10) or Jaunty Jackalope (9.04), you're finished - log out and back in for changes to take effect![/SIZE][/FONT][/COLOR]


[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]You now have to Reboot to take effect.
[/SIZE][/FONT][/COLOR]

---

### Post by mikewhatever on 2010-01-12
> **renjumace said:**
> man i tried the comprehensive sound solution as u said. but there is a problem when i try out the step 3 in the solution thread. my chipset is ICH8, but after searching intel provides drivers upto chipset ICH7, as upto it was only listed there. hence i could figure out that there was no driver for my chipset. but as i said earlier that i am using dell inspiron 1525 and this model is supported by dell for ubuntu. so is there a way that i could overcome by problem? i had another guy replying to one of my other thread about the same problem but his solution also didnt work. please help me out man... thanks for ur time.

Can you post the outputs of the following:

lspci -v

lsmod | grep snd

Edit: If you haven't yet solved this, take a look at this fix.
[http://www.ubuntumini.com/2009/11/fix-audio-on-dell-vostro-a90.html](http://www.ubuntumini.com/2009/11/fix-audio-on-dell-vostro-a90.html)

---

### Post by renjumace on 2010-01-15
man i solved the the problem. I had this switch IEC958 present in the menu when i typed alsamixer in the terminal.Though i enableld all other volume options by going into the preferences list, i didnt care about the switch. And after that when i enabled the switch the sound came. Sorry to all for this silly problem and really appreciate all ur replies and the time u guys spent. I will also make an effort to tell all the inspiron guys about this step if they have a problem with the sound. 

Cheers to all.......

---

