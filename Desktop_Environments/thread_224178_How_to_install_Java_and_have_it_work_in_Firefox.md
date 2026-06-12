---
title: "How to install Java and have it work in Firefox"
date: 2006-07-27
forum: Desktop Environments
---

### Post by simuser on 2006-07-27
So I installed Ubuntu 6 on the computer. Accessed the internet and opened a site that required java. 
I attemepted to follow the install procedure on the java site, but had no luck.
Can someone tell me how to install it?
I don't even know what information I can provide that will help you help me.

---

### Post by Dubbayoo on 2006-07-27
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

---

### Post by Tiribulus on 2006-07-27
I did what this guide says and after the password it tells me that it can't find the package. It shouldn't matter that I'm running KDE right? I tried a couple others and they installed. Thanks for the help.
>>>--Tiribulus->:D

---

### Post by Tiribulus on 2006-07-27
Actually it can't find Azuerus either and Bittornado says it installed and it's nowhere to be found. I do really need to get java working which is the topic of this thread. Any help would be greatly appreciated. These guides, while I'm sure they took a lot of work and at one time were maybe more accurate, are not helping.
Thanks again,
>>>--Tiribulus->

---

### Post by mlind on 2006-07-27
Did you configure update-alternatives for java?

---

### Post by Tiribulus on 2006-07-27
How do I know which "option corresponds to J2SE"  ?
Thanks,
>>>--Tiribulus->

---

### Post by Tiribulus on 2006-07-27
Both said they were using that option for java and neither one worked. It still wants me to install the "missing plug-in" . I don't mean to be a pain here, but you wouldn't think this should be this troublesome.
Thanks gain
>>>--Tiribulus->

---

### Post by Sef on 2006-07-27
Here's the easy way to install java:

[Easy Java Install]("https://help.ubuntu.com/community/Java")

You will need to enable multiverse in the repositories. If you haven't done that, [click here.]("https://help.ubuntu.com/community/Repositories/Ubuntu#what")

---

### Post by Tiribulus on 2006-07-27
Ok, I've done the repositories thing three times and each time it tells me the channel info is out of date, click reload to update it. I do that it looks like something happened, I go back in and the two "verse" options are still unchecked. No sign of Java in add remove programs even when I search for it. I had high hopes for this, but my patience is frankly wearing thin. I also tried integrating it with synaptic and it did the same thing. Out of date, reload, no java. Any insight would be greatly appreciated. It shouldn't be a hoop jumping festival to get something as basic as Java to work.
Thanks again,
>>>-Tiribulus->

---

### Post by mlind on 2006-07-28
> **Tiribulus said:**
> Ok, I've done the repositories thing three times and each time it tells me the channel info is out of date, click reload to update it. I do that it looks like something happened, I go back in and the two "verse" options are still unchecked. No sign of Java in add remove programs even when I search for it. I had high hopes for this, but my patience is frankly wearing thin. I also tried integrating it with synaptic and it did the same thing. Out of date, reload, no java. Any insight would be greatly appreciated. It shouldn't be a hoop jumping festival to get something as basic as Java to work.
Thanks again,
>>>-Tiribulus->

It really should be that hard.. Have you enabled **multiverse** repository succesfully? Make sure it's included on /etc/apt/sources.list.

---

### Post by Tiribulus on 2006-07-28
This is what I have in that file:

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


>>>--Tiribulus->

---

### Post by Tiribulus on 2006-07-28
I see them listed there, but don't know if that means they should be available or if the syntax is maybe incorrect or what. I should say that I consider myself maybe a notch above beginner and a notch below intermediate. I've been using Suse (KDE/Webmin) for about 4 years for various utilitarian type things (web/file/mail servers) and it was a major pain at times to get things working how I wanted as well. I'm hoping that Ubuntu will be easier and it does show promise. Maybe I'm missing something really obvious. I have no experience whatsoever with Debian and how it does it's installs. I've been used to RPM's and a few manual installs here and there. I probably just need to get accustomed to the way it does things.
>>>--Tiribulus->:D

---

### Post by drbillbailey on 2006-07-28
Here are the steps that worked for me:

Download Java from [www.java.com](www.java.com)

cd ~/Desktop

sudo ./jre-1_5_0_06-linux-i586.bin

sudo mkdir /usr/java

sudo mv jre1.5.0_06/ /usr/java/

sudo chown -R root:root /usr/java/jre1.5.0_06/

sudo ln -fs /usr/java/jre1.5.0_06/bin/java /usr/bin/java

sudo ln -fs /usr/java/jre1.5.0_06/bin/java_vm /usr/bin/java_vm

sudo ln -fs /usr/java/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so

Exit all browser sessions, go back into firefox.  Enjoy!

---

### Post by Uncle Spellbinder on 2006-07-28
I used [**AUTOMATIX**]("http://ubuntuforums.org/showthread.php?t=177646") and got all the necessary Firefox plugins. 

Generated: Fri Jul 28 2006 10:16:38 GMT-0400 (EDT)
User Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.5) Gecko/20060727 Ubuntu/dapper-security Firefox/1.5.0.5
Build ID: 2006072714

Installed Plugins: (8)
- Google VLC multimedia plugin 1.0
- Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
- Java(TM) Plug-in 1.5.0_06-b05
- mplayerplug-in 3.17
- QuickTime Plug-in 6.0
- RealPlayer 9
- Shockwave Flash
- Windows Media Player Plugin

---

### Post by srunni on 2006-07-28
I had some problems installing the plugins, sort of like you have. I kept running the installation script, and it didn't work. The problem was that I was installing to /usr/lib/firefox/plugins,and I needed to install to /home/[user]/.mozilla/plugins . Some scripts give you the choice of where you want to install to. If you have the choice, then install to /home/[user]/.mozilla/plugins . Otherwise, let it install to wherever it wants to, then go there and copy all the files in the plugins folder and put them in /home/[user]/.mozilla/plugins. That should solve the problem.

---

### Post by Tiribulus on 2006-07-28
Thanks guys for your attention,

@ drbillbailey:
It tells me command not found on the first command once I'm in the desktop folder even though a dir tells me that it's there and the name is correct.

@ Uncle Spellbinder:
Did everything as instructed, all commands said they ran. No Automatix in system tools and says command not found from the prompt.

@ srunni:
Only file in the /usr/lib/firefox/plugins dir is libunixprintplugin.so . 

I don't think God wants me to run Ubuntu:sad: 

>>>--Tiribulus->

---

### Post by Tiribulus on 2006-07-29
Do you guys have any idea why this might be happeneing? I should add that this is a P4 3ghz with a gig of memory and it runs everything fine usually.
>>>-Tiribulus->

---

### Post by Uncle Spellbinder on 2006-07-29
> **Tiribulus said:**
> 
@ Uncle Spellbinder:
Did everything as instructed, all commands said they ran. No Automatix in system tools and says command not found from the prompt.

Hmmmmmmm.  Did you try the install directions from the proper link? It should work.  :-k 

[**AUTOMATIX for Ubuntu (Xubuntu) Dapper**]("http://ubuntuforums.org/showthread.php?t=190025")

[**AUTOMATIX for Kubuntu  Dapper**]("http://ubuntuforums.org/showthread.php?t=203294")

---

### Post by Tiribulus on 2006-07-29
A little later I'll put the Ubuntu drive back in and double check, but as far as I remember I did exactly what it said. even copied and pasted the lines into the file and the commands into the terminal. It looked like everything worked, but It doesn't show up anywhere. I'm typing this from my Suse drive(I do it this way obviously so I can just swap the drives in and out). I'll put the Ubuntu drive in later and check again. Ths is getting very frustrating. I've been in this business long enough to know it's probably something on my end. If all these guys get this stuff working it must work. I'm not one of these "I'm having issues so it must suck" people.
>>>--Tiribulus->:D

---

