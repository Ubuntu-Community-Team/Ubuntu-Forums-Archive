---
title: "Just got started"
date: 2005-03-28
forum: Desktop Environments
---

### Post by aces170 on 2005-03-28
I just installed Ubuntu 4.10 installation. Few questions ?
1. How do I login in Root ?
2. Mp3's dont work ? How to make them work ?

---

### Post by nemin on 2005-03-28
[QUOTE=aces170]I just installed Ubuntu 4.10 installation. Few questions ?
1. How do I login in Root ?[/QUOTE]
Not, see [http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo).
[QUOTE=aces170]
2. Mp3's dont work ? How to make them work ?[/QUOTE]
What program do you use?

---

### Post by aces170 on 2005-03-28
[QUOTE=nemin]Not, see [http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo).

What program do you use?[/QUOTE]
 I dont know , which programme is installed by default ? I inserted an MP3 and tried to double click on the song, got an unknown error.
Also How do I access my Windows XP partition ? Is there any command ?

---

### Post by Buffalo Soldier on 2005-03-28
[QUOTE=aces170]I just installed Ubuntu 4.10 installation. Few questions ?
1. How do I login in Root ?[/quote]There's no need to create/login into root. For example if you want to edit the */etc/fstab* file using a GUI text editor, just run the command in console **sudo gedit /etc/fstab**. It will then ask for a password, just enter your user password. 

What is Sudo?[list]
[*] [http://www.ubuntulinux.org/support/documentation/faq/root/talkback/1099896833](http://www.ubuntulinux.org/support/documentation/faq/root/talkback/1099896833)
[*] [http://www.courtesan.com/sudo/](http://www.courtesan.com/sudo/)[/list]

Give sudo a try for a few days. But if you're still uncomfortable and prefer the old ways of root. Fear not, here's how: [http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root)

> 2. Mp3's dont work ? How to make them work ?Try following the instructions here: **[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)** if that doesn't work, what went wrong? any error message?

---

### Post by nemin on 2005-03-28
[QUOTE=aces170]
Also How do I access my Windows XP partition ? Is there any command ?[/QUOTE][http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

### Post by aces170 on 2005-03-29
[QUOTE=nemin][http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)[/QUOTE]
 Thanx a lot guys. One last query :
Buffalo soldier has given a link to the guide, and in that guide a command is given to install multimedia codecs. My question is the MP3 codec bundled or do I need to serately download it ? If yes any one can provide a link ? ( I am a total newbie.)

---

### Post by aces170 on 2005-03-30
[QUOTE=aces170]Thanx a lot guys. One last query :
Buffalo soldier has given a link to the guide, and in that guide a command is given to install multimedia codecs. My question is the MP3 codec bundled or do I need to serately download it ? If yes any one can provide a link ? ( I am a total newbie.)[/QUOTE]
 Ok, I tried the command to install w32 codecs, but it didnt install. Can anyone provide me a link to download the same ?

---

### Post by ubuntu_demon on 2005-03-30
[QUOTE=aces170]Ok, I tried the command to install w32 codecs, but it didnt install. Can anyone provide me a link to download the same ?[/QUOTE]
 First you have to edit your /etc/apt/sources.list an howto for this is here :

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

But I wouldn't use the latest line (the one with warty-backports) of the sources.list. Because hoary (the next release of Ubuntu) is arriving soon.

---

### Post by aces170 on 2005-03-30
[QUOTE=demon666_nl]First you have to edit your /etc/apt/sources.list an howto for this is here :

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

But I wouldn't use the latest line (the one with warty-backports) of the sources.list. Because hoary (the next release of Ubuntu) is arriving soon.[/QUOTE]
 Now I am really confused. Please understand I dont understand the terminoligies am a Newbie. So to play Mp3s now, i have to do the following ?

1. Write the foll command line:
 $ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
$ sudo gedit /etc/apt/sources.list
2. And then write the install command for w32 codecs /

OR, 
could I just download XMMS player and install that ?

---

### Post by ubuntu_demon on 2005-03-30
[QUOTE=aces170]Now I am really confused. Please understand I dont understand the terminoligies am a Newbie. So to play Mp3s now, i have to do the following ?

1. Write the foll command line:
 $ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
$ sudo gedit /etc/apt/sources.list
2. And then write the install command for w32 codecs /

OR, 
could I just download XMMS player and install that ?[/QUOTE]
 yes you are right

1) edit your sources.list like they explain at ubuntuguide.org (but don't use the backports because you want to upgrade to hoary in a couple of days/weeks)

$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
$ sudo gedit /etc/apt/sources.list

2)
$ sudo apt-get update
$ sudo apt-get install w32codecs xmms

I think [www.ubuntuguide.org](www.ubuntuguide.org) is rather clear. Please read it. There's a lot of help there.

I think w32codecs are in multiverse so you have to just uncomment those lines. But since you have to edit your sources.list you could also uncomment universe (because a lot of software is stored there) and add marillat (because that place has for example stuff to play dvd's).


PS don't type the $ because it stands for the prompt :)

---

### Post by hashimoto on 2005-03-30
The first command makes a back-up copy of the original sources.list file. This is a text file telling your system where to find software packages in the internet.
The second one opens a "notepad" called gedit so that you can edit the file sources.list There you add the extra repositories (that is: extra places to get software packages)
Then with command "sudo apt-get update" you tell your system to find out what new software packages are available (according to the edited sources.list).
With command "sudo apt-get install packagename" you install software named "packagename"

After editing the sources.list you should be able to install XMMS, too. The command would be "sudo apt-get install xmms"

Hope this explains something!

---

### Post by aces170 on 2005-03-30
[QUOTE=hashimoto]The first command makes a back-up copy of the original sources.list file. This is a text file telling your system where to find software packages in the internet.
The second one opens a "notepad" called gedit so that you can edit the file sources.list There you add the extra repositories (that is: extra places to get software packages)
Then with command "sudo apt-get update" you tell your system to find out what new software packages are available (according to the edited sources.list).
With command "sudo apt-get install packagename" you install software named "packagename"

After editing the sources.list you should be able to install XMMS, too. The command would be "sudo apt-get install xmms"

Hope this explains something![/QUOTE]
 Thanx Guys, So this does make things clear. Am at work will try and get back after work.

---

### Post by ubuntu_demon on 2005-03-30
no problem :)

---

### Post by aces170 on 2005-03-31
[QUOTE=demon666_nl]no problem :)[/QUOTE]
 Allrite One more question :

1. I have Linux Installed on my 40 GB hdd, and Windows on the other 120gb HDD. I wanna shift the 40gb HDD on my other comp. Is it possible to install Windows on that ?

---

### Post by bored2k on 2005-03-31
[QUOTE=aces170]Allrite One more question :

1. I have Linux Installed on my 40 GB hdd, and Windows on the other 120gb HDD. I wanna shift the 40gb HDD on my other comp. Is it possible to install Windows on that ?[/QUOTE]
 Windows on a 40gb and Ubie on 120gb? sure why not .
If you use a clone application dont expect it to auto detect the change in grub loader

---

### Post by aces170 on 2005-03-31
[QUOTE=bored2k]Windows on a 40gb and Ubie on 120gb? sure why not .
If you use a clone application dont expect it to auto detect the change in grub loader[/QUOTE]
No what i meant was :

I have 2 comps ones a old P2  400 mhz lying around, and ones an A64 which I use. I gathered that Linux would work on an old comp like a P2, but just in case it doest I have 10gb partion on the 40gb HDD where I would like to install Win98. Also Ubuntu wont have any probs with the hardware changes like Windows XP ?

Also I dont have net at home so can you guys help me.  ( Whatever is mentioned on the Unofficial guide kindly ignore as I will be printing out the whole page. )

1. Would PDF files open in Ubuntu ? if not where can I download the app ? and How do I install it ?
2. Will Divx, and Xvid codec movies run on XMMS ? If no where can I download and How do I install the codecs?
3. This is a toughie. How do I install my AGP drivers for a Radeon 9800 pro. I crashed the comp twice while doing it .

---

### Post by ubuntu_demon on 2005-03-31
[QUOTE=aces170]No what i meant was :

I have 2 comps ones a old P2  400 mhz lying around, and ones an A64 which I use. I gathered that Linux would work on an old comp like a P2, but just in case it doest I have 10gb partion on the 40gb HDD where I would like to install Win98. Also Ubuntu wont have any probs with the hardware changes like Windows XP ?

Also I dont have net at home so can you guys help me.  ( Whatever is mentioned on the Unofficial guide kindly ignore as I will be printing out the whole page. )

1. Would PDF files open in Ubuntu ? if not where can I download the app ? and How do I install it ?
2. Will Divx, and Xvid codec movies run on XMMS ? If no where can I download and How do I install the codecs?
3. This is a toughie. How do I install my AGP drivers for a Radeon 9800 pro. I crashed the comp twice while doing it .[/QUOTE]
 What you should do is just put the 40 gb in the P2-400 and install Ubuntu on it. Don't switch the hardrives just do a clean install because that's a lot faster than trying to get Ubuntu alive again. No windows 98 that's really ugly and not necessary. Ubuntu has to have at least 32 mb(could be 64 for hoary I'm not entirely sure).

Also install the hoary release candidate. It's almost finished. I think you'll manage. If you have problems with hoary we can help you. If your screen suddenly doesn't work anymore do "sudo dpkg-reconfigure xserver-xorg" but I doubt it's necessary because hoary will get released next week most likely!

If you think Ubuntu is not fast enough upgrade your memory to 512 mb or try beatrix (based on Ubuntu) [http://www.watsky.net](http://www.watsky.net) this distribution is capable of installing most Ubuntu packages according to the website.

1 mentioned in ubuntuguide
2 install w32codecs and totem-xine. don't use xmms for movies. (w32codecs come from marillat)

sudo apt-get install w32codecs
sudo apt-get install totem-xine

3

[http://ubuntulinux.org/wiki/BinaryDriverHowto](http://ubuntulinux.org/wiki/BinaryDriverHowto)

---

