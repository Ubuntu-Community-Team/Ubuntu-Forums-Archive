---
title: "Ubuntu 8.10 beta, and my Dell Inspiron 1720....."
date: 2008-10-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by liviococcia on 2008-10-10
Hello Members
I'm a new user to Ubuntu, or any Linux OS for that matter, but i was always interested in giving it a chance.

It so happend, that i came accross a demo video on YouTube on 'How to install Ubuntu on a Windows computer' yesturday, the demonstrator made it look so simple, so i thought i'd give it a go.

I created the ISO cd after a few failed attemps, then, worked out through the use of this forum, and some risk taking, my partitions for the OS, a 28gig plus 2gig for the SWAP location.

The first install's GRUB app whent wrong somehow i think, although i did do this install unatended, the second try whent great, with no issues.......few!!!

As soon as the system booted up, and connected to the net, i was prompted to get 290 or so updates, they were downloaded and installed before i could say ...WoW!

The i noticed in one of the desktop menu items 'System hardware', or somthing like that. I'd gone to this to see if there were any hardware issues, thinking it's like the Windows 'device manager', there was a recomendation to install a newer Navidia driver, so i did.

So, so far Ubuntu 8.10 beta is running well, but i do have some questions, and in my defense let me just say before i ask them, i will buy some sort or 'help' manual to guide me through this new learning curve.Please see below...

Q1: How do i actually find out how much disk space i have for the partition i created for Ubuntu, i have seen the included 'Disk space analyser', but i do not understand what its graphically telling me, is there a simpler tool or i can use?

Q2 I'm having a small issue with the 'num lock' in the login screen, i find i have to press 'Numlock' once, then press it again, so i can put in my username and password, the keyborad i'm using is a wireless compact laptop type, so the numlock keys are shared with some of the letters, is there a cure for this?

Thanks you Ubuntu creators, and any members for there help.

regards
Livio

---

### Post by bigbrovar on 2008-10-11
first of i would like to point out that Ubuntu 8.10 is not ideal for new users like you. as you can see its says beta. which means that its meant for testers and more of a preview of what is to come. its would not be stable and probably would break a lot. It is strongly advised that you don't install it on a production machine. for a stable version on Ubuntu you should get the Ubuntu 8.04 aka hardy heron which is the current stable release of Ubuntu.

> Q1: How do i actually find out how much disk space i have for the partition i created for Ubuntu, i have seen the included 'Disk space analyser', but i do not understand what its graphically telling me, is there a simpler tool or i can use?

you best bet is to install a tool called gparted from synaptic (synaptics is under **system/administration/synaptics** search for gparted. right to install then apply . once install you can launch the program by going to **systems/adminitration/partition editor** when you open the tool it would display the state of your hard drive and the amoun to mem allocated the linux partition is ext3 and swap while the windows should be ntfs and or fat32.
another way of knowing the among of partition your ubuntu filesystem has is to go to computer under places then click on filesystem you should see the size of your ubuntu filesystem below the the folder.although this will not include the size of your swap partition.

> Q2 I'm having a small issue with the 'num lock' in the login screen, i find i have to press 'Numlock' once, then press it again, so i can put in my username and password, the keyborad i'm using is a wireless compact laptop type, so the numlock keys are shared with some of the letters, is there a cure for this?

Thanks you Ubuntu creators, and any members for there help.
am sorry i cant help u on that i have no experience with wireless keyboards.but like i said the version on ubuntu u have is unstable and meant for testing purpose perhaps you could wait till oct 30 when the final stable version is released or better still grab a copy of the current version.

---

### Post by PinkFloyd102489 on 2008-10-11
I have a 1720 also and I dont see how you have one that has Numlock shared on another key. Numlock on mine is a dedicated key, in the normal place on a standard keyboard.

---

### Post by liviococcia on 2008-10-12
Thanks bigbrovar for your help, i did realise the 8.10 was a beta, and befor i installed the beta version i installed the 8.04 version first, which for somereason wasn't working for me when it came to restarting the computer (maybe a driver or Grub issue at the time), and before you ask, i did format the hard drive partition again before installing 8.10 beta on the same space.

The keyboard 'Numlock' issue is related to using my wireless 'Trust media center' keyboard, it's a small issue, and what i find i need to do when the login screen appears is press 'numlock' twice on it, on the actual Dell laptop the keyboard is a 'full' layout type, as 'Pinkfloyd' correctly says so the problem doesn't happen.

Bigbrovar, i wan't to stick with the 8.10 version for now, but i will upgrade to the next stable version as you've advised (you've metioned it's only a couple of weeks away 30th Oct), but when it arrives, will i be able to upgrade it while in the Ubuntu OS itself, or is it a case of doing the whole process of partitioning the hardrive (OS space & Swap) again, as if it had never been installed?

Thanks for all your help, i'm gonna see if there's such a thing as an instruction book, like 'Ubuntu for Dummies'.

regards

---

### Post by PinkFloyd102489 on 2008-10-12
> **liviococcia said:**
> 
Thanks for all your help, i'm gonna see if there's such a thing as an instruction book, like 'Ubuntu for Dummies'.


There is but I didnt find it very helpful. :P

---

### Post by liviococcia on 2008-10-12
Thanks PinkFloyd, do any members have recommendations regarding an 'easy-to-follow' 'paper' manual on Ubuntu, that i can buy in the UK (or webstore for Uk sales), something for the absolute beginner.

regs

---

### Post by freddybob on 2008-10-12
an easy way to see your available disk space is to open a terminal and type: df

---

### Post by andybleaden on 2008-10-13
Hi..interesting post and well done for sticking with the ubuntu system.

I have found this how to guide very helpful in the past

[https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

If you are using GDM you can use numlockx:

    *

      Install numlockx using apt-get, aptitude or Synaptic
    *

      In Hardy and Gutsy, edit /etc/gdm/Init/Default. For older versions of ubuntu edit /etc/X11/gdm/Init/Default instead.
          o

            Find the line

            exit 0

          o

            Add the following code above that line

            if [ -x /usr/bin/numlockx ]; then
              /usr/bin/numlockx on
            fi

Hope that helps

---

### Post by liviococcia on 2008-10-13
Thanks for your help Freddybob, i'll give your instruction a go,i just want to mention that the package 'Gparted' which was suggested was just perfect also, thanks for that.

Also Andy. thank you for pointing me to the 'numblock' help page link, can i assume that if i change the 'on' part of the instruction to 'off', that this would then mean 'numblock' would then not be turned on when Ubuntu loaded at the login screen?
 
Just to back-track a little, i found the book 'Ubuntu for Non-Geeks' on Amozon.uk's website, and i've read other customers reviews, has anyone used it?, i think it also comes with a DVD.

I've also setup the Evolution email cient, i can send and receive emails, but for some reason amy emails that have images in them are not shown, even though i've changed the setting in 'preferences' to allow them to be downloaded, i have searched the forum and found info regarding this, but no cure to the problem, seems it has something to do with websites not allowing Evolution access rights to them.

regards

---

### Post by andybleaden on 2008-10-14
I have had a lookat a few books..not all of them very good..that one was helpful..whether it is good for when the internet is down and you are goosed...hmmm

As for the num lock I think you are right...try and see and let us know!

Re evolution...My kde mail....kontact never shows images straight away...you have to ask for them to be shown inline etc..saves the nasties being downloaded

---

### Post by andybleaden on 2008-10-14
by the way ...how have you found dell support?

---

### Post by liviococcia on 2008-10-16
Actually..... now you mention it Andy, i've encountered a bit of a problem with the Dell, and was going to start a new thread requesting some help from members.

As i've mentioned, the Dell model is an Inspiron 1720, mine has the built in webcam and mic, now i do a lot of Skype-ing, i use Skype as one of my main telephone numbers, and do a lot of video calling, so i downloaded the Skype Ubuntu version form the Skype website and installed it.

The problem i'm getting is the settings on the Audio side of things, double clicking on the volume icon opens the sound controls, but no matter how i set things i can not un-mute any of the capture controls, so i have no sound capturing, and on the Audio sound side of things, i'm using headphones but the sound is not balanced equally, more audio is coming out of the left than on the right.

Andy, do you or any members, who have a Dell know the way to correct the setup?

Otherwise, running Ubuntu 8.10 beta on the Dell is really fast, i'm mean like lighting,

I did note using LogMein through Firefox was really bad the refresh rate was so slow, again must be something to do with the settings, as i did notice the desktop quality i was remoting to was very high, so this is another problem, but with the Firefox LogMeIn plugin maybe?, Firefox is very fast when using it normally though.

Again, any help would be very grateful.

regards

---

### Post by andybleaden on 2008-10-17
There is a dedicated dell linux forum by the way here where I posted a message on a similar topic

[http://www.dellcommunity.com/supportforums/board?board.id=sw_linux](http://www.dellcommunity.com/supportforums/board?board.id=sw_linux)

I had similar issues yesterday with a new Inspiron 530 that came with ubuntu installed.

 

Had to do some major editing to get the sound working using the ALSA sound drivers and alsamixer commands. Advanced Linux

 

ALSA = the Advanced Linux Sound Architecture

 

I have Kubuntu running on my pc so forgive any mention of KDE stuff . In your konsole/terminal type :

 

sudo alsamixer

 

then your password

 

You will then see a basic sound mixer showing the status of all sound-related
devices. Check which ones have MM under, then select them one by one and press M key
to unmute them.

 

You can also increase the levels up and down with your arrow buttons

 

I have also just found an excellent guide to ALSA here:

 

[http://www.debianhelp.co.uk/sound.htm](http://www.debianhelp.co.uk/sound.htm)

---

