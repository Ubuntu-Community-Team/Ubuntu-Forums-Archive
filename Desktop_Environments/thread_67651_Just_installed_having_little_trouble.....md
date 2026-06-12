---
title: "Just installed having little trouble...."
date: 2005-09-20
forum: Desktop Environments
---

### Post by mitchelliscious on 2005-09-20
hey guys-
i just want to say first off thanks.  I mean i read all your answere's on how to install ubuntu and shrink the windows partition and all and i got it working and i couldn't be happier.  I want to start using ubuntu more but i need some help

1. I have all my music installed on an externam hard drive.  I opened rythem box music player and it shows all my files there so i know it reads it but when i say to open my music folder's and files nothing happens, it goes back to the main music player screen shwoing no files.  The files are .MP3, .WAV

2. I downloaded the mozilla thunderbird email desktop.  However i opened it and i'm so used to windows just clicking install and it starting,  but i really have no idea how to install thunderbird? any suggestions?


3.  I would like to know what is best linux firewall/ virus scanner.  I would also like to find any programs that work with ubuntu that get rid of spyware

4.  also what replaces aim on linux?


Thanks- any suggestions please feel free to say
-mitch

---

### Post by aysiu on 2005-09-20
[QUOTE=mitchelliscious]
1. I have all my music installed on an externam hard drive.  I opened rythem box music player and it shows all my files there so i know it reads it but when i say to open my music folder's and files nothing happens, it goes back to the main music player screen shwoing no files.  The files are .MP3, .WAV[/quote] Ubuntu doesn't come supporting proprietary formats. You have to enable that support.

[http://www.frankandjacq.com/ubuntuguide/5.04/#extrarepositories](http://www.frankandjacq.com/ubuntuguide/5.04/#extrarepositories)
[http://www.frankandjacq.com/ubuntuguide/5.04/#codecs](http://www.frankandjacq.com/ubuntuguide/5.04/#codecs)

> 
2. I downloaded the mozilla thunderbird email desktop.  However i opened it and i'm so used to windows just clicking install and it starting,  but i really have no idea how to install thunderbird? any suggestions? See how [this tutorial](http://www.psychocats.net/essays/winuxinstall.php) tells you how to install Blender? Same principle. Just do it for Thunderbird.

> 
3.  I would like to know what is best linux firewall/ virus scanner.  I would also like to find any programs that work with ubuntu that get rid of spyware You don't need to worry about viruses or spyware in Linux. There is, however, an anti-virus program called clamav, and two firewall programs called firestarter and guarddog. All of those can be installed through [Synaptic](http://www.psychocats.net/essays/winuxinstall.php).

> 
4.  also what replaces aim on linux? [GAIM](http://gaim.sourceforge.net/)--it should already be installed.

P.S. If you're using the new Breezy preview, you may need to change all the *hoary* references in your sources.list to *breezy* (except the backports--those can stay *hoary*).

---

### Post by mitchelliscious on 2005-09-20
alright installing codecs pack so i can play MP3's and this happens

root@ubuntu:/home/mitch# sudo apt-get install gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd gstreamer0.8-caca
  gstreamer0.8-festival gstreamer0.8-jack gstreamer0.8-mad gstreamer0.8-mikmod
  gstreamer0.8-mpeg2dec gstreamer0.8-sid gstreamer0.8-swfdec jackd
  liba52-0.7.4 libid3tag0 libjack0.80.0-0 libmad0 libmikmod2 libmpeg2-4
  libsidplay1 libsndfile1 libswfdec0.3
Suggested packages:
  qjackctl jack-tools meterbridge libjackasyn0 sidplay-base xsidplay
The following NEW packages will be installed:
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd gstreamer0.8-caca
  gstreamer0.8-festival gstreamer0.8-jack gstreamer0.8-mad gstreamer0.8-mikmod
  gstreamer0.8-mpeg2dec gstreamer0.8-plugins gstreamer0.8-sid
  gstreamer0.8-swfdec jackd liba52-0.7.4 libid3tag0 libjack0.80.0-0 libmad0
  libmikmod2 libmpeg2-4 libsidplay1 libsndfile1 libswfdec0.3
0 upgraded, 22 newly installed, 0 to remove and 2 not upgraded.
Need to get 1249kB of archives.
After unpacking 3764kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.
root@ubuntu:/home/mitch#


I tried Capital Y. y, yes, Yes what else is there to type it says abort no matter what i put in

---

### Post by Xian on 2005-09-20
[QUOTE=mitchelliscious]Do you want to continue [Y/n]?[/QUOTE]
When you get to this step just hit your Enter key.
The default response is Yes so this should serve as confirmation.

---

### Post by mitchelliscious on 2005-09-20
Yes i hit enter after i hit yes and it automativly goes to abort

---

### Post by Xian on 2005-09-20
No, I mean hit Enter without selecting 'Y'.
Just hit the Enter key and don't type anything else.

---

### Post by az on 2005-09-21
That is *so* weird.

Do you otherwise have any keybord issues?



Waitaminute!  root@ubuntu?  You are logged in as root?  Why?

---

### Post by mitchelliscious on 2005-09-21
I don't know i went to system tools... root terminal, put in my password and there came a white box with that showing the first thing... i put in the commands and what not so i could change the codex so i could play my mp's and it wouldnt let me say yes.  I dont know if its cause im logged in as root but i don't know how to change it.  My keyboard has been working fine.  The only thing i wish was working better was my mouse.  i have the logitech mx1000 and the scrolling does not work on ubuntu can i download any programs that will work with linux for setting up the mouse buttons

---

### Post by az on 2005-09-21
I dunno.

You can always try:

sudo apt-get install -y gstreamer0.8-plugins

so that it does not ask you the yes or no questions..

---

### Post by mitchelliscious on 2005-09-21
mitch@ubuntu:~$ sudo apt-get install gstreamer0.8-plugins
Password:

found regular terminal not root terminal.  However when i put this in it asks for my password and i type and nothing shows up i can not type anything for my password.  Which terminal should i use to input codes the regular terminal or root terminal?

---

### Post by matthew on 2005-09-21
[QUOTE=mitchelliscious]mitch@ubuntu:~$ sudo apt-get install gstreamer0.8-plugins
Password:

found regular terminal not root terminal.  However when i put this in it asks for my password and i type and nothing shows up i can not type anything for my password.  Which terminal should i use to input codes the regular terminal or root terminal?[/QUOTE]
When you type a password in the terminal nothing will appear on the screen. This is so that if someone were standing behind you they could not see your password. It doesn't even print ****'s so that no one can see the password's length. I know it can be a bit confusing the first time you see that, but you really can type your password even though nothing is appearing on the screen. Type it slowly and carefully and hit <enter> and it should work.

---

### Post by mitchelliscious on 2005-09-21
alright installed that now when i go in to rythembox i try to open my folder and it says this is not an audio stream and it says the file path then it says .m4a for all of my media?

---

