---
title: "Compiz in Ubuntu 9.04"
date: 2009-04-23
forum: Desktop Environments
---

### Post by charleskw on 2009-04-23
So Compiz was automatically installed with Ubuntu 9.04, however I can't seem to find the Compiz manager. I looked around on the package manager and there isn't anything left for compiz to install.

---

### Post by Darkshade on 2009-04-23
sudo apt-get install compizconfig-settings-manager

After the installation you should have it in your preferences menu. You can also run it with "ccsm".


I recommend you to install the package "fusion-icon" too. It'll add an icon to your notification area which allows you to choose between compiz and  emerald or metacity with just one click.

---

### Post by andddlay on 2009-04-25
> **Darkshade said:**
> sudo apt-get install compizconfig-settings-manager

After the installation you should have it in your preferences menu. You can also run it with "ccsm".


I recommend you to install the package "fusion-icon" too. It'll add an icon to your notification area which allows you to choose between compiz and  emerald or metacity with just one click.

Thank you so much Darkshade!  I was a bit disappointed after upgrading to Jaunty Jackalope and finding Compiz not working.  Installing fusion-icon from the synaptic did the trick, though.  

Thanks again!!!!!!!!

---

### Post by gcbzzzz on 2009-04-25
> **Darkshade said:**
> sudo apt-get install compizconfig-settings-manager

After the installation you should have it in your preferences menu. You can also run it with "ccsm".


I recommend you to install the package "fusion-icon" too. It'll add an icon to your notification area which allows you to choose between compiz and  emerald or metacity with just one click.

There's no such package in 9.04

```
E: Couldn't find package compizconfig-settings-manager
```

---

### Post by foxy123 on 2009-04-25
> **gcbzzzz said:**
> There's no such package in 9.04

```
E: Couldn't find package compizconfig-settings-manager
```

have you got universe repos enabled?

---

### Post by dobhar on 2009-04-25
Thanks DarkShade...that worked for me...  :)

---

### Post by dobhar on 2009-04-25
Hi foxy123...I don't want to hijack charleskw's thread but I have a couple quick questions if you don't mind.  I have JJ 9.04 installed on a Dell Latitude D20 Lappy and the wireless (BCM4311) worked after updating the drivers...I also installed JJ 9.04 on a Dell Latitude D610 but I can't get the wireless to work and it's using the BCM4306 Wireless card like yours (Listed in your signature)...Did you have any issue gettng Wireless to work? Did you have to do anything and if so can you point me in direction that will help me get it to work?

---

### Post by foxy123 on 2009-04-25
> **dobhar said:**
> Hi foxy123...I don't want to hijack charleskw's thread but I have a couple quick questions if you don't mind.  I have JJ 9.04 installed on a Dell Latitude D20 Lappy and the wireless (BCM4311) worked after updating the drivers...I also installed JJ 9.04 on a Dell Latitude D610 but I can't get the wireless to work and it's using the BCM4306 Wireless card like yours (Listed in your signature)...Did you have any issue gettng Wireless to work? Did you have to do anything and if so can you point me in direction that will help me get it to work?

there are a few threads on that topic. you'd be better off posting there or post a new one. It's really not a good idea to hijack a thread.

---

### Post by arunkumar.kariyil on 2009-06-04
> **foxy123 said:**
> have you got universe repos enabled?

hi could you please tell me what is universe repos and how do i enble it...

~Arun

---

### Post by sartic on 2009-06-04
Is it possibly to disable compiz for explicit program? Google Earth and Firefox get side effects when compiz running?

---

### Post by Archernix on 2009-06-13
Should have done this before i got awn

---

### Post by bhp0528 on 2009-07-15
> **Darkshade said:**
> sudo apt-get install compizconfig-settings-manager

After the installation you should have it in your preferences menu. You can also run it with "ccsm".


Bang! Works great.

One question though. In the past you could go to [B]Preferences > Appearance
> Visual Effects (Tab)[/B] and then choose the **Custom** bubble. Is that a different configure utility?

---

### Post by Narcolepsy06 on 2009-07-15
> **gcbzzzz said:**
> There's no such package in 9.04

```
E: Couldn't find package compizconfig-settings-manager
```

I found it on my Ubuntu 9.04. 

```

$aptitude search compiz
i   compiz                          - OpenGL window and compositing manager     
i   compiz-core                     - OpenGL window and compositing manager     
p   compiz-dev                      - OpenGL window and compositing manager - de
p   compiz-fusion-bcop              - Compiz option code generator              
i   compiz-fusion-plugins-extra     - Collection of extra plugins from OpenCompo
i   compiz-fusion-plugins-main      - Collection of plugins from OpenCompositing
p   compiz-fusion-plugins-unsupport - Compiz Fusion plugins - "unsupported" coll
i   compiz-gnome                    - OpenGL window and compositing manager - GN
p   compiz-kde                      - OpenGL window and compositing manager - KD
i   compiz-plugins                  - OpenGL window and compositing manager - pl
i   compiz-wrapper                  - OpenGL window and compositing manager, wra
i   compizconfig-backend-gconf      - Settings library for plugins - OpenComposi
p   compizconfig-backend-kconfig    - KConfig Settings library for plugins - Ope
**p   compizconfig-settings-manager   - Compiz configuration settings** manager     
v   gcompizthemer                   -                                           
i   libcompizconfig0                - Settings library for plugins - OpenComposi
p   libcompizconfig0-dev            - Development file for plugin settings - Ope
p   python-compizconfig             - Compiz configuration system bindings     
```

What version of the kernel do you have?  
What about trying: 
```
 $sudo aptitude update 
```

---

### Post by darkknight045 on 2009-07-15
> **sartic said:**
> Is it possibly to disable compiz for explicit program? Google Earth and Firefox get side effects when compiz running?

You could create a script that does these things, you'd want it to go something like the following:

```
#!bin/bash
#
#
killall compiz*
firefox
compiz*
#This script should be run in terminal, it will keep the terminal 
#open and when you close FF it will restart compiz.
```

This is my poor attempt at bash scripting, but this file *should* do what you intend, if someone knows a more savvy way to control compiz via the CLI by all means provide some constructive criticism.

---

### Post by gnuvistawouldbecool on 2009-07-15
> **darkknight045 said:**
> You could create a script that does these things, you'd want it to go something like the following:


This is my poor attempt at bash scripting, but this file *should* do what you intend, if someone knows a more savvy way to control compiz via the CLI by all means provide some constructive criticism.

I'd say more along the lines of modifying it to:

```
#!bin/bash
#
#
metacity --replace
firefox
compiz --replace
#This script should be run in terminal, it will keep the terminal 
#open and when you close FF it will restart compiz.
```

Killing compiz without a replacement wm will likely remove the titlebars of your windows that are open, and other nasty problems.

---

### Post by lavezarez on 2009-08-01
thanks, darkshade! worked just as you described for me :D

---

### Post by harecanada on 2009-08-01
Hey Darkshade,
I installed that fusion-icon and it works to turn off compiz and turn on metacity but if I try to turn compiz back on it just flickers on and on til I have to reboot and it resets itself. Any ideas on how I can handle this?
Thanks,
harecanada

---

