---
title: "Walkthrough: Getting bluetooth headsets/speakers to work with Ubuntu"
date: 2009-10-23
forum: Desktop Environments
---

### Post by flyguy97 on 2009-10-23
All,

Currently the biggest problem facing bluetooth users is to get linux to recognize your device. I had major issues trying to get my Sony MBS-100 speakers working with Ubuntu. Here is a breakdown of how I was able to conquer the beast.

1. You will need to add some repositories for Blueman pulseaudio updates. Issue the following commands from a command line:

```

sudo sh -c "echo 'deb http://ppa.launchpad.net/blueman/ppa/ubuntu jaunty main' >> /etc/apt/sources.list"
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 951DC1E2
sudo sh -c "echo 'deb http://ppa.launchpad.net/themuso/ppa/ubuntu jaunty main' >> /etc/apt/sources.list"
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B88A1AA8

```
2. Update and install package updates through apt-get by issuing the following commands:

```

sudo apt-get update
sudo apt-get upgrade

```
3. Install some needed packages to get everything working.

```

sudo apt-get install blueman pulseaudio-module-bluetooth pavucontrol flashplugin-nonfree-extrasound

```
4. Restart your computer
5. Now you will have to pair your device and connect to its audio sink service, all that is fairly intuitive to do through blueman so I will not cover the finer points. (Blueman is the bluetooth icon in your system tray, Blueman has replaced the Gnome default bluetooth manager, bluez-gnome)
6. Select your device in the Blueman main screen and go to the device menu and select Connect: Audio Sink, everything should be working now.
7. If everything worked all right you will be able to activate your bluetooth speaker/headset from now on by right-clicking the bluetooth icon on your system tray and selecting Recent Connections.

Cheers,
Jason

---

### Post by Luciano Pinto on 2010-03-26
Heya all! I'm still a newbie in ubuntu, trying to make my way up and I needed a little help on the subject of this topic.

First of all, I'm currently using Karmic 64 bits and wasn't able to install **flashplugin-nonfree-extrasound** as, apparently, there isn't a 64-bits version available. Is there a way round it?

Additionally, I need help with something else. My first intention with this thread was to be able to use the speakers and mic of my notebook as my 'headset'. In other words, I want to be able to connect my mobile phone with my computer and put through it any calls I might receive.

I know it might be stretching too much, but I intend to build an application capable of doing that. What I need to know is if I'm able to send these voice packages from the mobile to the computer via Bluetooth, to be treated by the application.

Any hints you might give me would be most appreciated.

Thanks all in advance.

Luciano

---

