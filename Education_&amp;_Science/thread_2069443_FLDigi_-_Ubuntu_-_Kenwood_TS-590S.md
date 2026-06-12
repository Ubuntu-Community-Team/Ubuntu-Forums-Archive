---
title: "FLDigi - Ubuntu - Kenwood TS-590S"
date: 2012-10-10
forum: Education &amp; Science
---

### Post by tm-hart on 2012-10-10
[COLOR="Blue"]**SETUP NOTES FOR FLDigi and the  KENWOOD TS-590S **[/COLOR]

[COLOR="Blue"]Summary[/COLOR]: The Kenwood TS-590S and FLDigi software form a solid partnership after installation and setup.  Transmission and reception tests with CW, BPSK-31 and RTTY-45 have been successful using a standard USB cable to connect the computer and transceiver. 

[COLOR="Blue"]Recommendation[/COLOR]:  G3NRW has an excellent Kenwood TS-590S web site.  His discussions of audio card, software and hardware issues are very helpful.  Refer to:
[http://homepage.ntlworld.com/wadei/HOWTO_TS-590S_with_SDR_IQ.pdf](http://homepage.ntlworld.com/wadei/HOWTO_TS-590S_with_SDR_IQ.pdf)

	**Part I. Transceiver settings:**

The TS-590S default MENU CONFIGURATION settings should work with FLDigi.  However, personal preferences might call for some changes. 

	**Part II. FLDigi setup and CONFIGURATION menu settings:**

Copy the RigCAT file “TS-590S.xml” to the “.fldigi/rigs” folder in the HOME directory.  When FLDigi first starts, it will load the file and make a number of program settings.  “TS-590S.xml” is available on-line:
 [http://www.w1hkj.com/download.html](http://www.w1hkj.com/download.html) 

On first use, FLDigi launches an Install Wizard to simplify the setup process.

Top Line Menu checks:

The following settings work on my system; use them as starting points and make changes as needed.

RIG – HARDWARE PTT: Check the  “PTT tone on right audio channel”. 

RIG – RigCAT:  Check the “Use RigCAT” box.
	
	Verify the following:
		Rig description file: TS-590S.xml
		Device: /dev/ttyUSB0
		Baud rate: 115200
		Stopbits: 1
		Check TRS/CTS flow control
		Check CAT command for PTT
		Check DTR +12 v
		“Initialize” if changes are made.

AUDIO – DEVICES: 
	
	Verify the following:
		Check PortAudio
		Select USB Audio CODEC for “Capture”
		Select USB Audio CODEC  for “Playback”

AUDIO – RIGHT CHANNEL:
	
	Verify the following:
		Check “Reverse Left/Right audio channels”

	[B]Part III. Operating System Settings:
[/B]
A number of on-line postings advise making certain changes to the “/etc/group” file for FLDigi use.
Edit /etc/group file to add yourself to the group for two lines: (1) “dialout:x:20:” and (2) “tty:x:5:”.  Assume that your login name is “username”; make these edits:
		dialout:x:20:username
		tty:x:5:username

Then, save the file, log out and log back in.  Instead of logging out-in, rebooting the computer  and logging in will also reset your permissions.

It is easy to install FLDigi via Synaptic. Then, start the program from either a terminal prompt by typing “fldigi”or from Dash Home.  For future convenience, consider locking FLDigi to the Launcher.

	**Part IV. Odds and ends:**

To determine sound card information, use the “aplay -l” command.  For example:

   $ aplay -l

   **** List of PLAYBACK Hardware Devices ****

     card 0: Generic [HD-Audio Generic], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]

     Subdevices: 1/1

     Subdevice #0: subdevice #0

   $ 



The top line menu choice “Configure – Colors & Fonts” allows customization of screen appearance.  A variety of colors for the receive and transmit panels are available along with various fonts.  I like the Arial font size 22. My received text is black while transmitted text is green.

RigCAT file “TS-590S.xml” from the FLDigi download web site runs my transceiver.  I edited the file and changed the <BAUDRATE> field to “115,200” and the <STOPBITS> field to “1” to accommodate the USB cable connecting computer to TS-590S.

Run digital modes on VFO-A of the TS-590S for full CAT  functionality.  VFO-B will send / receive  and display the transceiver. frequency.  However, VFO-B may not accept commands from the computer to change frequency.

The “Signal Range (dB)” slider on lower left of the FLDigi main screen is helpful in setting input signal strength.  By increasing or decreasing the setting, incidental noise can be minimized.  In general, there should be good contrast between background and signal streams .

It is easy to rename and rewrite the MACRO buttons on the FLDigi screen.  The manual explains the options.  Some macros examples:

Macro to change frequency:
	<QSY:7070>

Macro to clear receive panel:
	<CLRRX>

Macro to clear transmit panel:
	<CLRTX>

Macros to change modes to CW, PSK or RTTY (45.45/170):
	<MODEM:CW>
	<MODEM:BPSK31>
	<MODEM:RTTY>

On the WATERFALL-DISPLAY menu, un-check the “Always show audio frequencies” option to display RF frequencies on the waterfall instead of audio frequencies.  

When RigCAT is running, the name of the control file will appear above the VFO frequency panel on the upper left of the screen.  When it is not working, the tag ”Enter Xcvr Freq.” will appear. 

[COLOR="Blue"]**Personal note:**[/COLOR] My thanks and congratulations go to Dave Frees / W1HKJ and his team for their efforts in creating FLDigi.  This is an excellent program that is a boon to the community.

---

