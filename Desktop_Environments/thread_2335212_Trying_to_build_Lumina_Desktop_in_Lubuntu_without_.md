---
title: "Trying to build Lumina Desktop in Lubuntu without having a working Lumina.."
date: 2016-08-26
forum: Desktop Environments
---

### Post by madscientist132 on 2016-08-26
I had install lubuntu into an old laptop and all works fine.
Happens that i want to add Lumina Desktop as i think it is what LXDE should have been, and, given that the BSD developers only offers it for 64 bit systems, i had to pull the sources and the dependences and build it in my own. 

The Lumina website, at [https://lumina-desktop.org/get-lumina/?lang=en](https://lumina-desktop.org/get-lumina/?lang=en) , tells this:

> "[h=3]Building Lumina from source on Debian/Ubuntu/Linux Mint[/h]To build the Lumian desktop from source code on any members of the Debian, Ubuntu or Linux Mint distribution (or their derivative distributions) please perform the following steps.
Please note that older versions of Ubuntu (14.04 and earlier) do not ship with modern versions of the Qt 5 libraries. The following instructions should work for Debian 8 and Ubuntu 14.10 and earlier.
1. First, install the required software and build tools. Please note the &#8220;sudo apt-get install build-essential.. command is all one long command. There should be no line breaks between &#8220;build-essential&#8221; and &#8220;pavucontrol&#8221;.


```
sudo apt-get update
sudo apt-get install build-essential git qt5-default qttools5-dev-tools libqt5gui5 qtmultimedia5-dev libqt5multimediawidgets5 libqt5network5 libqt5svg5-dev libqt5x11extras5-dev libxcb-icccm4-dev libxcb-ewmh-dev libxcb-composite0-dev libxcb-damage0-dev libxcb-util0-dev libphonon-dev libxcomposite-dev libxdamage-dev libxrender-dev libxcb-image0-dev libxcb-screensaver0-dev qtdeclarative5-dev fluxbox kde-style-oxygen xscreensaver xbacklight alsa-utils acpi numlockx pavucontrol xterm sysstat

```
Next we need to download the Lumina source code.
```
git clone [https://github.com/trueos/lumina.git](https://github.com/trueos/lumina.git)
```
Our next step is to configure and build Lumina&#8217;s source code.
```
cd lumina
qmake
cd libLumina
make-linux-distro.sh Debian
cd ..
```
Please note, in the above step where we run &#8220;make-linux-distro.sh Debian&#8221; we need to specify Debian, even if we are using a distribution with a different name, such as Ubuntu or Mint.
Finally, we build and install the desktop. These steps will likely take several minutes to complete."

I could do everything except enter to libLumina and run the shell script, since i got none. I thought that it could be some sort of old information and since then that step could be eliminated by further developing, so i proceeded with make and make install and all seemed to go fine without stopping or having to add "make -i". 

But.. when i wanted to log in on Lumina, it doesn't work and goes back to the login screen.

Given this situation, where should look for problems, and, should this problem be known, does exist something i should try for fixing it?

---

