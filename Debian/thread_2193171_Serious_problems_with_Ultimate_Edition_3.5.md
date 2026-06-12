---
title: "Serious problems with Ultimate Edition 3.5"
date: 2013-12-11
forum: Debian
---

### Post by nef1312 on 2013-12-11
Before installing Ultimate Edition 3.5.2, I ran Mint 12 on my computer, which has an I5 cpu and Nvidia graphics card GTX 550 ti. Mint 12 was excellent but, as it is built on Ubuntu 11.10, support came to an end.

I had planned to install Ubuntu 12.04.3 but, because the live version created a second, "[unknown]("http://ubuntuforums.org/showthread.php?t=2191788&p=12864950#post12864950")," monitor superimposed over a properly recognized monitor, I gave up on the idea. I decided, instead, to install Ultimate Edition 3.5.2, which is based on Ubuntu 12.04. The only good thing about the choice is that it was easy, after adding the ubuntu-x-swat/x-updates ppa, to install the Nvidia 331.20 driver through Jockey.

I hope, without having to start from scratch with a new Distro, to make Ultimate Edition (which uses KDE, which I liked and relied upon after I added it to Mint 12, as the primary DE) functional, rather than a buggy, prone to freeze up OS that it is on my machine.

Please note that, after the initial installation, my first attempt to improve things was to upgrade KDE to its latest version by adding the kubuntu backport ppa and running apt-get upgrade. The latest version of KDE did nothing to improve matters. 

I tried switching to compize instead of kwin, to manage the windows. This did nothing for me. I also tried switching the version of OpenGL to 3.1 from 2.0, which seemed, for a while, to improve things before problems set back in.

The next thing I tried was to use Unity. While listed in the DM as existing, it booted nowhere and I was left with a machine which booted to a blank screen with a rotating pointer. That was fixed by booting into repair and, from there, dropping to command line where I uninstalled Unity, which left me booting into a cairo-dock interface, from which I was able to get back to KDE. I then reinstalled Unity. I again tried Unity but it was not fully functional. For example, it was not possible to set hide launcher without losing it entirely. This could not be done with either Ubuntu Tweak or Unsettings - and I have used both programs before on a machine on which I installed Ubuntu. Moreover, Myunity, while I installed, does not run at all, leaving an error message that it is incompatible with Ultimate Edition 3.5.

I tried installing and using Cinnamon, which required a package change related to bluetooth in order to be installed. I do not particularly like Cinnamon but thought it would be more functional than Unity or KDE. I was able to get rid of some of the undesired extra programs which, in KDE, fail to show up at all in Autostart but which clearly do start up on login. So, there was some benefit to it.

I am trying to avoid having to start from scratch. My first thought is to install a new kernel, e.g. 3.11 or 3.12, in the hope that it will make the computer more "Ubuntu-like." Alternatively or in addition, I might fully purge all of the DE's and then reinstall KDE, which I had installed and was using on computer when I had Mint 12. Any suggestions - other than to install another OS - would be welcome.

---

### Post by nef1312 on 2013-12-13
Nevermind. I solved my problem by uninstalling Ultimate Edition.

---

### Post by nef1312 on 2013-12-13
I have solved the problem.

---

### Post by mörgæs on 2013-12-13
Good, please mark the thread solved using 'thread tools'.

---

