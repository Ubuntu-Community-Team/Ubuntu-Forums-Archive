---
title: "Running Virtualbox Seamless mode on boot"
date: 2010-06-30
forum: Desktop Environments
---

### Post by darkenvy6 on 2010-06-30
Essentially the title says it all. I have windows 7 installed and have no problems with virtual mode but how would I go about having the computer boot into ubuntu (KDE) then boot the virtual machine only to follow with seamless mode? I don't care if I can see the process work, by that I mean the booting of windows. Oh please don't ask why I would want this, I love linux but the world lives in windows not wine :P

Any Ideas? We need to be creative.

---

### Post by ©TriMoon® on 2010-06-30
I guess the simplest way would be to have KDM to auto login to your default user, and then start virtualbox from the users startup script ;)
I'm sure there are other ways but this is IMHO the least intrusive to your linux setup...

---

### Post by cpmman on 2010-06-30
_***[Wubi]("http://wubi-installer.org/")***_

---

### Post by darkenvy6 on 2010-06-30
Eeew Wubi! lol. I want to reside in linux as it's confortable here and I have never found windows to ever be stable after 6 months. Linux stays stable forever even after system-addons.


Oh TriMoon, yea that could work but if I start virtualbox from the user scripts or any scripts it would just start the main window. The overview window that shows all your virtual images and allows you to start then via that gui application. The second issue would be automating the switch from regular mode to seamless mode automaticly. If there is an automation program that would move and click mouse clicks after .bmp checks then it would work. I found one of these for windows, it uses images to reconize if a particular image is up. Weird but it worked like a charm. Also not the way linux should be utilized :P

---

### Post by 3Miro on 2010-06-30
```
VirtualBox --machine=MyWindows7
```

I cannot remember if it is -machine or --machine. In place of MyWindows7 give the name of the machine that you want to start. You can also download the VirtalBox manual from their web-page to see more details on their programs.

```
man VirtualBox
```
or
```
VirtualBox --help
```
should give you information for all the options that you can use to start a machine.

---

### Post by darkenvy6 on 2010-07-02
I will try this when I get home! Thats lovely that this script exists but now what about part two? Now we have to be able to have virtualbox enter seamless mode the moment windows finishes booting. (The seamless mode button IS grayed until windows boots to desktop)

---

