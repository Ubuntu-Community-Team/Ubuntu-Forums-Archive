---
title: "Going from Unity to XFCE (now back to Unity) broke laptop sound"
date: 2015-11-14
forum: Desktop Environments
---

### Post by Russell_Sinclair on 2015-11-14
Hi All! (first post!)

I'm running a Dell XPS L702x with Ubuntu 15.10 (really like it). I tried to switch to XFCE and it completely hosed the previously working sound. Now when I boot, the sound device shows "Dummy Device". When I "alsa force-reload", the Built-in audio is recognized but with a red circle with line through it.

I've purged/reinstalled pulseaudio and alsa, but to no avail. I've purged all xubuntu references and the sound just will not work.

Is there anyway I can simply reset the audio settings without having to completely reinstall Ubuntu?

I'm happy to follow troubleshooting steps, as I'm actually fairly Unix literate.

Thanks in Advance....

---

### Post by QDR06VV9 on 2015-11-14
[COLOR=#333333][FONT=Verdana]Go into Xfce Settings Editor -> xfce4-mixer -> sound-card and click 'reset'.
If that don't work Log Out and Log in should be there now.
And more info 
[/FONT][/COLOR]http://askubuntu.com/questions/397819/ubuntu-13-10-and-xfce4-no-sound-at-all

---

### Post by Russell_Sinclair on 2015-11-14
I realise I should put 'Unity" in the thread title, as I've switched back to unity because I couldn't get xfce to give me anything other than a solid black screen.

XFCE/Xubuntu-desktop has been completely purged from my system because I couldn't get it working at all.

---

### Post by QDR06VV9 on 2015-11-14
Good to know, so see if this gets you sorted out 
```
[COLOR=#111111][FONT=Consolas]gsettings set com.canonical.indicator.sound visible true[/FONT][/COLOR]
```

---

### Post by Russell_Sinclair on 2015-11-14
> **runrickus said:**
> Good to know, so see if this gets you sorted out 
```
[COLOR=#111111][FONT=Consolas]gsettings set com.canonical.indicator.sound visible true[/FONT][/COLOR]
```

Ran that, no output.

Only getting dummy-output in devices :(

I really appreciate the assistance.

---

### Post by QDR06VV9 on 2015-11-14
Huumm?? What is the output of

```
[COLOR=#333333][FONT=UbuntuMono]sudo aplay -l[/FONT][/COLOR]
```

---

### Post by coffeecat on 2015-11-14
> **Russell_Sinclair said:**
> I realise I should put 'Unity" in the thread title, as I've switched back to unity because I couldn't get xfce to give me anything other than a solid black screen.

We don't have a Unity prefix for some reason (there never seemed to be a need for one) but I've edited your thread title to reflect the situation for you - hopefully.

Good luck finding a solution.

---

### Post by Russell_Sinclair on 2015-11-14
> **runrickus said:**
> Huumm?? What is the output of

```
[COLOR=#333333][FONT=UbuntuMono]sudo aplay -l[/FONT][/COLOR]
```


```
rsinclair@bender:~$ sudo aplay -l**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC665 Analog [ALC665 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC665 Digital [ALC665 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Russell_Sinclair on 2015-11-14
> **coffeecat said:**
> We don't have a Unity prefix for some reason (there never seemed to be a need for one) but I've edited your thread title to reflect the situation for you - hopefully.

Good luck finding a solution.

Thanks Coffee cat!

*Gives Mocha Cappacino*

---

### Post by QDR06VV9 on 2015-11-14
Lets see if things got muted,  in the terminal type
```
alsamixer
```
Make sure all volume sliders are not muted and reading a volume level  if they are you can use the arrow keys to move selections right or left.
I attached a screenshot to help.

---

### Post by Russell_Sinclair on 2015-11-14
Every seems OK - see attached

---

### Post by QDR06VV9 on 2015-11-14
With that same window open select F6 and change the card to another other than PCM
Then check for sound.

---

### Post by Russell_Sinclair on 2015-11-14
> **runrickus said:**
> With that same window open select F6 and change the card to another other than PCM
Then check for sound.

No go, (see attached)

[ATTACH=CONFIG]265568[/ATTACH]

FWIW, when I boot from the live CD, it would normally show SPDIF sound and Laptop speakers in the sound other than just "dummy output"

---

### Post by QDR06VV9 on 2015-11-14
Wow it uninstalled more than just XFCE.
Once again in the terminal
```
[COLOR=#111111][FONT=Consolas]sudo apt-get install alsa-base* indicator-sound* libcanberra-pulse* osspd* osspd-pulseaudio* pulseaudio* pulseaudio-module-bluetooth* 
pulseaudio-module-x11* unity-control-center* unity-control-center-signon* webaccounts-extension-common* xul-ext-webaccounts*
[/FONT][/COLOR]
```
it may or may not say some of those are already installed.
Then reboot.
Fingers crossed.

---

### Post by Russell_Sinclair on 2015-11-14
> **runrickus said:**
> Wow it uninstalled more than just XFCE.
Once again in the terminal
```
[COLOR=#111111][FONT=Consolas]sudo apt-get install alsa-base* indicator-sound* libcanberra-pulse* osspd* osspd-pulseaudio* pulseaudio* pulseaudio-module-bluetooth* 
pulseaudio-module-x11* unity-control-center* unity-control-center-signon* webaccounts-extension-common* xul-ext-webaccounts*
[/FONT][/COLOR]
```
it may or may not say some of those are already installed.
Then reboot.
Fingers crossed.

```

rsinclair@bender:~$ sudo apt-get install alsa-base* indicator-sound* libcanberra-pulse* osspd* osspd-pulseaudio* pulseaudio* pulseaudio-module-bluetooth* pulseaudio-module-x11* unity-control-center* unity-control-center-signon* webaccounts-extension-common* xul-ext-webaccounts*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'alsa-base' for regex 'alsa-base*'
Note, selecting 'indicator-sound-gtk2' for regex 'indicator-sound*'
Note, selecting 'indicator-sound' for regex 'indicator-sound*'
Note, selecting 'libcanberra-pulse-dbg' for regex 'libcanberra-pulse*'
Note, selecting 'libcanberra-pulse' for regex 'libcanberra-pulse*'
Note, selecting 'libossp-uuid-perl' for regex 'osspd*'
Note, selecting 'krosspython' for regex 'osspd*'
Note, selecting 'libossp-sa-dev' for regex 'osspd*'
Note, selecting 'libossp-uuid11' for regex 'osspd*'
Note, selecting 'libossp-uuid16' for regex 'osspd*'
Note, selecting 'osspd-backend' for regex 'osspd*'
Note, selecting 'osspd-alsa' for regex 'osspd*'
Note, selecting 'libossp-uuid-dev' for regex 'osspd*'
Note, selecting 'osspd-dbg' for regex 'osspd*'
Note, selecting 'osspd' for regex 'osspd*'
Note, selecting 'osspd-pulseaudio' for regex 'osspd*'
Note, selecting 'libossp-sa12' for regex 'osspd*'
Note, selecting 'osspd-pulseaudio' for regex 'osspd-pulseaudio*'
Note, selecting 'projectm-pulseaudio' for regex 'pulseaudio*'
Note, selecting 'pulseaudio' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-trust-store-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-gconf' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-zeroconf' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-gconf-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-x11-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-bluetooth-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-lirc-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-utils-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-raop-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-x11' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-jack-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-esound-compat' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-jack' for regex 'pulseaudio*'
Note, selecting 'liquidsoap-plugin-pulseaudio' for regex 'pulseaudio*'
Note, selecting 'gstreamer0.10-pulseaudio' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-trust-store' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-utils' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-equalizer' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-raop' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-droid' for regex 'pulseaudio*'
Note, selecting 'gstreamer1.0-pulseaudio' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-zeroconf-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-bluetooth' for regex 'pulseaudio*'
Note, selecting 'libsdl1.2debian-pulseaudio' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-lirc' for regex 'pulseaudio*'
Note, selecting 'osspd-pulseaudio' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-droid-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-esound-compat-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-bluetooth-dbg' for regex 'pulseaudio-module-bluetooth*'
Note, selecting 'pulseaudio-module-bluetooth' for regex 'pulseaudio-module-bluetooth*'
Note, selecting 'pulseaudio-module-x11-dbg' for regex 'pulseaudio-module-x11*'
Note, selecting 'pulseaudio-module-x11' for regex 'pulseaudio-module-x11*'
Note, selecting 'unity-control-center-signon' for regex 'unity-control-center*'
Note, selecting 'unity-control-center-dev' for regex 'unity-control-center*'
Note, selecting 'libunity-control-center-dev' for regex 'unity-control-center*'
Note, selecting 'libunity-control-center1' for regex 'unity-control-center*'
Note, selecting 'unity-control-center-datetime' for regex 'unity-control-center*'
Note, selecting 'unity-control-center' for regex 'unity-control-center*'
Note, selecting 'unity-control-center-signon-autopilot' for regex 'unity-control-center*'
Note, selecting 'unity-control-center' instead of 'unity-control-center-datetime'
Note, selecting 'unity-control-center-signon' for regex 'unity-control-center-signon*'
Note, selecting 'unity-control-center-signon-autopilot' for regex 'unity-control-center-signon*'
E: Unable to locate package webaccounts-extension-common*
E: Couldn't find any package by regex 'webaccounts-extension-common*'
E: Unable to locate package xul-ext-webaccounts*
E: Couldn't find any package by regex 'xul-ext-webaccounts*'
rsinclair@bender:~$ 



```

I removed the two things it couldn't find, and I'm runnign the command now.

---

### Post by QDR06VV9 on 2015-11-14
Thats my bad
Try this instead
```
sudo apt-get install alsa-base* indicator-sound* libcanberra-pulse* osspd* osspd-pulseaudio* pulseaudio* pulseaudio-module-bluetooth* 
pulseaudio-module-x11* unity-control-center* 
```

---

### Post by Russell_Sinclair on 2015-11-14
OK, we are getting better.

When I boot, I still get "dummy device" but, if I do an alsa force-reload things are recognised.

Now, I just need to get it to a state where I don't have to do that on every boot.

---

### Post by Russell_Sinclair on 2015-11-14
> **runrickus said:**
> Thats my bad
Try this instead
```
sudo apt-get install alsa-base* indicator-sound* libcanberra-pulse* osspd* osspd-pulseaudio* pulseaudio* pulseaudio-module-bluetooth* 
pulseaudio-module-x11* unity-control-center* 
```

```

rsinclair@bender:~$ sudo apt-get install alsa-base* indicator-sound* libcanberra-pulse* osspd* osspd-pulseaudio* pulseaudio* pulseaudio-module-bluetooth* pulseaudio-module-x11* unity-control-center*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'alsa-base' for regex 'alsa-base*'
Note, selecting 'indicator-sound-gtk2' for regex 'indicator-sound*'
Note, selecting 'indicator-sound' for regex 'indicator-sound*'
Note, selecting 'libcanberra-pulse-dbg' for regex 'libcanberra-pulse*'
Note, selecting 'libcanberra-pulse' for regex 'libcanberra-pulse*'
Note, selecting 'libossp-uuid-perl' for regex 'osspd*'
Note, selecting 'krosspython' for regex 'osspd*'
Note, selecting 'libossp-sa-dev' for regex 'osspd*'
Note, selecting 'libossp-uuid11' for regex 'osspd*'
Note, selecting 'libossp-uuid16' for regex 'osspd*'
Note, selecting 'osspd-backend' for regex 'osspd*'
Note, selecting 'osspd-alsa' for regex 'osspd*'
Note, selecting 'libossp-uuid-dev' for regex 'osspd*'
Note, selecting 'osspd-dbg' for regex 'osspd*'
Note, selecting 'osspd' for regex 'osspd*'
Note, selecting 'osspd-pulseaudio' for regex 'osspd*'
Note, selecting 'libossp-sa12' for regex 'osspd*'
Note, selecting 'osspd-pulseaudio' for regex 'osspd-pulseaudio*'
Note, selecting 'projectm-pulseaudio' for regex 'pulseaudio*'
Note, selecting 'pulseaudio' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-trust-store-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-gconf' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-zeroconf' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-gconf-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-x11-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-bluetooth-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-lirc-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-utils-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-raop-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-x11' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-jack-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-esound-compat' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-jack' for regex 'pulseaudio*'
Note, selecting 'liquidsoap-plugin-pulseaudio' for regex 'pulseaudio*'
Note, selecting 'gstreamer0.10-pulseaudio' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-trust-store' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-utils' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-equalizer' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-raop' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-droid' for regex 'pulseaudio*'
Note, selecting 'gstreamer1.0-pulseaudio' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-zeroconf-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-bluetooth' for regex 'pulseaudio*'
Note, selecting 'libsdl1.2debian-pulseaudio' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-lirc' for regex 'pulseaudio*'
Note, selecting 'osspd-pulseaudio' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-droid-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-esound-compat-dbg' for regex 'pulseaudio*'
Note, selecting 'pulseaudio-module-bluetooth-dbg' for regex 'pulseaudio-module-bluetooth*'
Note, selecting 'pulseaudio-module-bluetooth' for regex 'pulseaudio-module-bluetooth*'
Note, selecting 'pulseaudio-module-x11-dbg' for regex 'pulseaudio-module-x11*'
Note, selecting 'pulseaudio-module-x11' for regex 'pulseaudio-module-x11*'
Note, selecting 'unity-control-center-signon' for regex 'unity-control-center*'
Note, selecting 'unity-control-center-dev' for regex 'unity-control-center*'
Note, selecting 'libunity-control-center-dev' for regex 'unity-control-center*'
Note, selecting 'libunity-control-center1' for regex 'unity-control-center*'
Note, selecting 'unity-control-center-datetime' for regex 'unity-control-center*'
Note, selecting 'unity-control-center' for regex 'unity-control-center*'
Note, selecting 'unity-control-center-signon-autopilot' for regex 'unity-control-center*'
Note, selecting 'unity-control-center' instead of 'unity-control-center-datetime'
alsa-base is already the newest version.
gstreamer0.10-pulseaudio is already the newest version.
gstreamer1.0-pulseaudio is already the newest version.
indicator-sound is already the newest version.
libcanberra-pulse is already the newest version.
libcanberra-pulse-dbg is already the newest version.
libunity-control-center-dev is already the newest version.
libunity-control-center1 is already the newest version.
pulseaudio is already the newest version.
pulseaudio-dbg is already the newest version.
pulseaudio-esound-compat is already the newest version.
pulseaudio-esound-compat-dbg is already the newest version.
pulseaudio-module-bluetooth is already the newest version.
pulseaudio-module-bluetooth-dbg is already the newest version.
pulseaudio-module-droid is already the newest version.
pulseaudio-module-droid-dbg is already the newest version.
pulseaudio-module-gconf is already the newest version.
pulseaudio-module-gconf-dbg is already the newest version.
pulseaudio-module-jack is already the newest version.
pulseaudio-module-jack-dbg is already the newest version.
pulseaudio-module-lirc is already the newest version.
pulseaudio-module-lirc-dbg is already the newest version.
pulseaudio-module-raop is already the newest version.
pulseaudio-module-raop-dbg is already the newest version.
pulseaudio-module-trust-store is already the newest version.
pulseaudio-module-trust-store-dbg is already the newest version.
pulseaudio-module-x11 is already the newest version.
pulseaudio-module-x11-dbg is already the newest version.
pulseaudio-module-zeroconf is already the newest version.
pulseaudio-module-zeroconf-dbg is already the newest version.
pulseaudio-utils is already the newest version.
pulseaudio-utils-dbg is already the newest version.
unity-control-center is already the newest version.
unity-control-center-dev is already the newest version.
unity-control-center-signon is already the newest version.
indicator-sound-gtk2 is already the newest version.
krosspython is already the newest version.
libossp-sa-dev is already the newest version.
libossp-sa12 is already the newest version.
libossp-uuid-dev is already the newest version.
libossp-uuid-perl is already the newest version.
libossp-uuid16 is already the newest version.
liquidsoap-plugin-pulseaudio is already the newest version.
osspd is already the newest version.
osspd-alsa is already the newest version.
osspd-dbg is already the newest version.
osspd-pulseaudio is already the newest version.
projectm-pulseaudio is already the newest version.
unity-control-center-signon-autopilot is already the newest version.
pulseaudio-equalizer is already the newest version.
The following packages were automatically installed and are no longer required:
  apturl-common checkbox-ng checkbox-ng-service libblas-dev liblinear-dev liblinear-tools liblinear1 libsnack-oss libsox-fmt-mp3 libsvm-tools ndiff nmap
  plainbox-provider-checkbox plainbox-provider-resource-generic plainbox-secure-policy python3-checkbox-ng python3-checkbox-support python3-jinja2
  python3-plainbox python3-pycurl python3-pyparsing python3-software-properties python3-xlsxwriter software-properties-common tcl-snack-doc
  unattended-upgrades
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by QDR06VV9 on 2015-11-14
What is in this file(Paste back the content)
```
gedit /etc/default/speech-dispatcher
```

---

### Post by Russell_Sinclair on 2015-11-14
> **runrickus said:**
> What is in this file(Paste back the content)
```
gedit/etc/default/speech-dispatcher
```

```

# Defaults for the speech-dispatcher initscript, from speech-dispatcher


# Set to yes to start system wide Speech Dispatcher
RUN=no
```

---

### Post by QDR06VV9 on 2015-11-14
Ok Good
Now let do this
```
sudo [COLOR=#111111][FONT=Consolas]rm ~/.pulse-cookie[/FONT][/COLOR]
```
And 
```
sudo [COLOR=#111111][FONT=Consolas]rm -rf ~/.config/pulse[/FONT][/COLOR]
```
Now Reboot and this time hopefully all should be good.

---

### Post by Russell_Sinclair on 2015-11-14
> **runrickus said:**
> Ok Good
Now let do this
```
sudo [COLOR=#111111][FONT=Consolas]rm ~/.pulse-cookie[/FONT][/COLOR]
```
And 
```
sudo [COLOR=#111111][FONT=Consolas]rm -rf ~/.config/pulse[/FONT][/COLOR]
```
Now Reboot and this time hopefully all should be good.

Peformed both of those steps, and when I rebooted I got the following 
[ATTACH=CONFIG]265569[/ATTACH]

I've not yet done the alsa force-reload, but it still says "dummy output" in sound settings.

---

### Post by Russell_Sinclair on 2015-11-14
For the record, did force reload (stuff recognised), then rebooted, still "dummy output" :(

---

### Post by QDR06VV9 on 2015-11-14
I would have expected an error code to show.
Still not seeing your card?
Hang in there we are getting closer.
what is the output of
```
apt-cache policy [COLOR=#111111][FONT=Consolas]pavucontrol[/FONT][/COLOR]
```

---

### Post by Russell_Sinclair on 2015-11-14
> **runrickus said:**
> I would have expected an error code to show.
Still not seeing your card?
Hang in there we are getting closer.
what is the output of
```
apt-cache policy [COLOR=#111111][FONT=Consolas]pavucontrol[/FONT][/COLOR]
```

```

rsinclair@bender:~$ sudo apt-cache policy pavucontrol
[sudo] password for rsinclair: 
pavucontrol:
  Installed: 3.0-3build1
  Candidate: 3.0-3build1
  Version table:
 *** 3.0-3build1 0
        500 http://ftp.utexas.edu/ubuntu/ wily/universe amd64 Packages
        100 /var/lib/dpkg/status
rsinclair@bender:~$ 

```

---

### Post by QDR06VV9 on 2015-11-14
Go to Menu> Sound and Video> Pulseaudio Volume: So on the top tabs there is one the reads> Configuration click that and below there should be a drop down
I have mine set to> Analog Stereo Duplex
Then just to be sure kill all Pulse Audio
```
pulseaudio -k
```
And see if there is any sound.

---

### Post by Russell_Sinclair on 2015-11-14
> **runrickus said:**
> Go to Menu> Sound and Video> Pulseaudio Volume: So on the top tabs there is one the reads> Configuration click that and below there should be a drop down
I have mine set to> Analog Stereo Duplex
Then just to be sure kill all Pulse Audio
```
pulseaudio -k
```
And see if there is any sound.

OK, I opened it. It says "no cards available for configuration"

I did a sudo alsa force-reload and "Analog Stereo Duplex" is default.

I ran pulseaudio -k and there IS sound.

Have not yet restarted to see if there is sound after reboot.

---

### Post by QDR06VV9 on 2015-11-14
But you still had to run "[COLOR=#000000]alsa force-reload"?

[/COLOR]

---

### Post by Russell_Sinclair on 2015-11-14
For it to show up in the config tab, yes

---

### Post by QDR06VV9 on 2015-11-14
Do you by chance have  hybrid video IE: Intel and Nvidia?

---

### Post by Russell_Sinclair on 2015-11-14
> **runrickus said:**
> Do you by chance have  hybrid video IE: Intel and Nvidia?
As a matter of fact, yes I do

That is why I abandoned Mint. The Nvidia/Intel caused Cinnamon to keep freezing.

---

### Post by Russell_Sinclair on 2015-11-14
FWIW, here is a detailed breakdown of my system
[https://www.dell.com/support/home/us/en/19/product-support/servicetag/17V6RS1/diagnose?ref=3275_previously&rvps=y](https://www.dell.com/support/home/us/en/19/product-support/servicetag/17V6RS1/diagnose?ref=3275_previously&rvps=y)

HDDs are different tho...

Primary is a 256 SSD
Secondary is a 1 TB HDD

---

### Post by QDR06VV9 on 2015-11-14
Sorry maybe you don't know?
What is the output of
```
[COLOR=#111111][FONT=Consolas]lspci | grep VGA[/FONT][/COLOR]
```

---

### Post by Russell_Sinclair on 2015-11-14
> **runrickus said:**
> Sorry maybe you don't know?
What is the output of
```
[COLOR=#111111][FONT=Consolas]lspci | grep VGA[/FONT][/COLOR]
```

I assume that by hybrid, you meant 2 video controllers. Yes I do.

```

rsinclair@bender:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF116M [GeForce GT 555M/635M] (rev a1)
rsinclair@bender:~$ 

```

---

### Post by QDR06VV9 on 2015-11-14
> **Russell_Sinclair said:**
> As a matter of fact, yes I do

That is why I abandoned Mint. The Nvidia/Intel caused Cinnamon to keep freezing.
Well if that is the case then you are bound to have problems with Ubuntu as well, as Mint is built around Ubuntu.

---

### Post by Russell_Sinclair on 2015-11-14
> **runrickus said:**
> Well if that is the case then you are bound to have problems with Ubuntu as well, as Mint is built around Ubuntu.

Yes, but I figured the fact that the most recent Mint was based on Tahir, that Ubuntu would be more up to date. Also, it doesn't lock up like Mint did.

---

### Post by QDR06VV9 on 2015-11-14
Not sure how you installed your video driver on Mint but have a look here.
[http://askubuntu.com/questions/589397/ubuntu-desktop-freezes-sometimes](http://askubuntu.com/questions/589397/ubuntu-desktop-freezes-sometimes)

---

### Post by Russell_Sinclair on 2015-11-14
> **runrickus said:**
> Not sure how you installed your video driver on Mint but have a look here.
[http://askubuntu.com/questions/589397/ubuntu-desktop-freezes-sometimes](http://askubuntu.com/questions/589397/ubuntu-desktop-freezes-sometimes)

I'll dig into that in a bit.

I gather that the dual video is confusing the OS when it tries to find the sound device?

---

### Post by QDR06VV9 on 2015-11-14
It can Yes! Nvidia gives you the HDMI option. And kind of tells all the sound modules what is where.
If anyone else wants to jump in Please Do!

---

### Post by Russell_Sinclair on 2015-11-14
I think it's moot.

I jumped the gun and installed Bumblebee......

The desktop would not load.

I tried purging and rebooting, and it took me back to a 800x600 GUI login which, while it showed my userid, It would not accept my pwd.

I think I'm going to need to reinstall Ubuntu again and reinstall all packages, steam, and games from GoG I downloaded.

I'm really really really frustrated.

---

### Post by Russell_Sinclair on 2015-11-14
Good news
Ubuntu reinstalled, looks like the only thing I lost was Steam.

Bad news
Sound still hosed. 

However, at least I can do the alsa force-reload

---

### Post by Russell_Sinclair on 2015-11-14
Thanks for your help Runrickus, it's very appreciated.

Check your PMs for a thank you....

---

### Post by Russell_Sinclair on 2015-11-14
JANKY SOLUTION!!!!!

Did a search on "Run commands on unity startup" and created an upstart command that runs alsa force-reload when unity starts :)

---

### Post by QDR06VV9 on 2015-11-14
Thank You for your message!;)
I will do some research on this and post back any relevant news!
Kind Regards

---

### Post by QDR06VV9 on 2015-11-16
@ Russell_Sinclair I have found a link that might have some bearing on your problem, It shows some sucess. 
[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)
The only down side is I have no personal experience with this but a few in this forum have had luck with this method.
Just to be sure have a good back-up in place.
Best of Luck and Regards

---

