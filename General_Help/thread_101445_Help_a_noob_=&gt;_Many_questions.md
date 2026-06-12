---
title: "Help a noob =&gt; Many questions"
date: 2005-12-09
forum: General Help
---

### Post by essell25 on 2005-12-09
I would like to do the following with my ubuntu computer, but i'm a novice :P I tried searching the forums but didn't find anything useful.

[LIST]
[*][COLOR="Red"]My video card presently only has 640X400 in the display size selection screen. What should i do to, at least, get 800X600 (on my tv & on comp screen | looking for 1024X768 tough) My card is ATI 3D Rage II with video & s-video out.[/COLOR]
[*][COLOR="Silver"]I would like to share files between my WinXP Home computer and Ubuntu computer... Installed samba..??[/COLOR] 
[COLOR="Silver"]Smb.conf is read only and i cant change it back (checkboxes are grey).. what can i do?[/COLOR]
[*][COLOR="Silver"]I Tried to install Xmms1 ... Is it compatible with Ubuntu? and if yes how do i install it?[/COLOR] 
How do i install skins?
[*]I have an HP USB Internet keyboard that i got with another computer, but ubuntu doesnt seemk to recognize it.
[*]Share printer with a WinXP computer? (printer connected to winXP one)
[/LIST]

I will delete problems from this list when i fix them.

---

### Post by Specialsauce on 2005-12-09
[QUOTE=essell25][LIST]
[*]I Tried to install Xmms1 ... Is it compatible with Ubuntu? and if yes how do i install it?
[/LIST]
[/QUOTE]
what format is the package? I would advise you to use the repositories to install what you need.

---

### Post by Kobra on 2005-12-09
For your network sharing, I would say use a program called Samba.  I think it takes a spot of configuring, so I'll let someone else do that one

---

### Post by WanderingStar on 2005-12-09
I'm not going to touch the resolution one - xorg.conf is scary to me...

To install XMMS go to System->Administration->Synaptic.  Search in Synaptic for XMMS.  Click the square to install.  You may need all the repositories enabled so see here: [https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29]("https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29")

To share files with a Windows machine you need to install Samba.  Once you do that the relevent file is /etc/samba/smb.conf.  You will need to edit that to your  liking.  Its not too bad, and a good guide is here: [https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29]("https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29").  If you run into troubles with that, post here.  We will help you out, I'm sure. That said, I've attached my smb.conf that works for me - its pretty wide open however (the relevent machines are firewalled off from the internet).

```
[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
	obey pam restrictions = yes
	socket options = TCP_NODELAY
	encrypt passwords = true
	passdb backend = tdbsam guest
	passwd program = /usr/bin/passwd %u
	dns proxy = no
	netbios name = Laptop
	invalid users = root
	default = global
	workgroup = WORKGROUP
	os level = 20
	auto services = global
	security = share
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000

#[homes]
#	create mask = 0700
#	directory mask = 0700
#	comment = Home Directories
#	writable = no
#	public = yes

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

[Downloads]
	public = yes
	path = /home/jeff/Torrent Downloads

[CdRom]
	public = yes
	path = /media/cdrom
[Music]
	public = yes
	path = /home/jeff/Music
[Firefox]
	public = yes
	path = /home/jeff/Downloads
```

---

### Post by aclaunch on 2005-12-09
Question 3 first: yes xmms is compatible with Ubuntu. You should be able to install it via Synaptic (System-> Admin-> Synaptic).

Question 2: also via Synaptic install Samba. This is a connectivity protocol so you can access Windows boxes and vice versa. If you only want to do stuff from Linux to Windows, just enable sharing on the appropriate directory in Windows and you are good to go.

Question 1: have you tried changing the resolution via System-> Preferences-> Screen (or something similar)? That's the easy way. If that doesn't work post back and we can do the more complicated way.

Good Luck
Alan

---

### Post by essell25 on 2005-12-09
for question 1 the only choice ion the dropdown menu is 640X400...


Thx for samba help and mmx

---

### Post by Qrk on 2005-12-09
What X.org driver are you using? Have you tried downloading the drivers from ati, and switching to them with

```
sudo dpkg-reconfigure xserver-xorg
```
??

Ubuntu doesn't include closed source drivers; so you could very easily have a mistake there. This forum has a ton of information about Ati cards, as they are a common problem.

---

### Post by aclaunch on 2005-12-09
You could reconfigure xorg.conf with "sudo dpkg --reconfigure xserver-xorg". When you get to the screen resolution section make sure several resolutions are checked other than 640 X 480.

Alan

Edit: Dang, too slow with typing.

---

### Post by essell25 on 2005-12-09
for proprietary drivers it says that i need to run it in super-user...

---

### Post by tabinin on 2005-12-09
[QUOTE=essell25]for proprietary drivers it says that i need to run it in super-user...[/QUOTE]

When you get that message, you need to start the command with sudo.  For example, to edit your smb.conf, do this:

```
sudo gedit /etc/smb.conf
```

sudo allows a permitted user to execute a command as the superuser

gedit is a Gnome text editor

your smb.conf (Samba configuration file) resides in the /etc/ directory

---

### Post by essell25 on 2005-12-09
thx for the smb.conf  but for the ati.run file it says that i need to run it in super user.

---

### Post by tabinin on 2005-12-10
[QUOTE=essell25]thx for the smb.conf  but for the ati.run file it says that i need to run it in super user.[/QUOTE]

so add "sudo" in front of the command to run.  For example:

```
sudo ./ati-driver-installer-8.20.8.run
```


edit:
See [this thread]("http://ubuntuforums.org/showthread.php?t=101124") for an nice conversation about "sudo" and how it works

---

### Post by essell25 on 2005-12-11
everytime i try a sudo command it asks me for a password.... but then i cannot type anything.  The screen doesnt freeze, the terminal just doesnt let me input the password.

Help

:S

---

### Post by wounded on 2005-12-11
When you are asked for a password for sudo, from a terminal, you do not see any indicators that you are typing. No asterisks, x's, or anything but you are typing. Is that what is throwing you off?

when it says Password: just type your password in and hit enter and it will work.

---

### Post by infoseeker on 2005-12-11
The key entries aren't displayed....just enter the password and press enter.

oops....double entry  :)

---

### Post by essell25 on 2005-12-11
ok so the proprietary drivers didn't work... there was a problem with xwindow or something... anyhoo  what log should i post up here for you guys?

---

### Post by essell25 on 2005-12-13
--- removed because somebody finally helped me after  3 days ----

sorry to the people that would've answered but didn't login or something...

and thanks to peteyp666 and brynjarh

---

### Post by peteyp666 on 2005-12-13
Well I'll be glad to see you go if you're gonna act like that but anyway, what happened after you tried this?

[QUOTE=Qrk]What X.org driver are you using? Have you tried downloading the drivers from ati, and switching to them with

```
sudo dpkg-reconfigure xserver-xorg
```
??

Ubuntu doesn't include closed source drivers; so you could very easily have a mistake there. This forum has a ton of information about Ati cards, as they are a common problem.[/QUOTE]

When you installed, did you mark off more resolutions then just 640x480 or did you just enter next for each one?

---

### Post by brynjarh on 2005-12-13
[QUOTE=essell25]My video card presently only has 640X400 in the display size selection screen. What should i do to, at least, get 800X600 (on my tv & on comp screen | looking for 1024X768 tough) My card is ATI 3D Rage II with video & s-video out.[/QUOTE]
Make sure you are using the right driver for your ATI card that comes with Ubuntu, maybe Ubuntu put a generic driver on instead of a ATI specific one?

One problem with checking if you are using the right driver for your card is that where the hell can you read what drivers are for what cards?? Maybe someone else here can answer that here though I doubt it.

Another problem with it is how can one change a driver? There is no default GUI tool to do that so I guess one could do it manually by editing the xorg.conf file by doing ```
sudo gedit /etc/X11/xorg.conf
``` and find a device section that seams to be talking about your graphic card (should be approximately at line 64) and change the line "Driver "name-of-some-driver"" to "Driver "name-of-the-driver-you-want". This is not enough though, you must also make sure that the driver is available on your Ubuntu system, I have no idea how one can find out what drivers are available other then just using the dpkg-reconfigure method and choosing your driver from the list that will be shown to you there.

By doing this some tools that want to edit xorg.conf automatically will not work until you do some more manual work to allow them to do it, so another way to edit the xorg.conf file which does not mess up this is to run ```
sudo dpkg-reconfigure xserver-xorg --default-priority
``` but that will require you do answer a bunch of other questions that have nothing to do with what you want to do, I recommend not skipping the --default-priority line since if you don't do that you will get even more questions that have nothing to do with that you want to do.

You must also make sure that the xorg.conf file lists the resolutions you want, there will be 6 places in the file you must change, if you use "sudo dpkg-reconfigure xserver-xorg --default-priority" you will only have to define them once.

You must also remember to restart x-window-system after you have changed the xorg.conf file, again you can not do this in the default GUI as far as I know so now you have to write at the command line "sudo /etc/init.d/gdm restart", but be sure to save everything you want saved before doing this, this will most definitely close down all your software running on top of X.

And then you can always go with the linux drivers ATI makes instead of the free software drivers but "rumors say it's unreliable" and how does one install them? You probably have to read some further long instructions and hope it will work. I recommend trying to get Ubuntu working before starting to add 3rd party stuff on it.

The second thing you can do is check your xorg.conf file monitor settings, for example when I install Ubuntu I just get 640x480 resolution (like you) so I have to manually tell Ubuntu that my monitor has 30-96 horizontal sync rate and 48-120 vertical refresh rate by adding...
```

        HorizSync       30-96
        VertRefresh     48-120

```
..to the monitor section of the xorg.conf file, apparently it is not enough to tell xorg what resolution you want since it will ignore it for some reason, so to set your HorizSync and VertRefresh to the right value look in your monitors manual, if you threw it away you will have to google it up and if the monitor is old and unsupported it's most likely that the information will only be found in well hidden places on the web, but let's hope not. You can also use "sudo dpkg-reconfigure xserver-xorg --default-priority" to change this.

You obviously are not familiar with Ubuntu so I recommend you check out [http://help.ubuntu.com/starterguide/C/index.html](http://help.ubuntu.com/starterguide/C/index.html) which you may or may not be aware of.

---

### Post by essell25 on 2005-12-13
when i installed the generic driver, the screen turned blue then there was a error message 
> Xwindow display error. Please restore backup.

also i contacted atri and they answered that Rage II isn't supported for linux by ati anymore they just keep the windows drivers as backup : they just spport newer cards. They said that they didn't do anything to support that card on linux.  Do you guys know third party drivers for ati cards?

---

### Post by essell25 on 2005-12-13
[QUOTE=peteyp666]
When you installed, did you mark off more resolutions then just 640x480 or did you just enter next for each one?[/QUOTE]

i changed the horiz and vert refresh like brynjarh said and chose all resolutions from 640.. to 1024.. still got 400X640

> Another problem with it is how can one change a driver? There is no default GUI tool to do that so I guess one could do it manually by editing the xorg.conf file

tried with all twelve drivers that the ati package installed... they all did pretty much the same thing : not work


thx again

---

### Post by essell25 on 2005-12-18
4 days and no help... 8 days since first post...




[SIZE="6"][COLOR="Black"]
peteyp666? I don't like you either.

A special THX to _**[COLOR="Red"]tabinin[/COLOR]**_ because he followed the problem and tried to help.. because he's the kind of guy that this section needs.

Normal thanks to infoseeker, brynjarh, wounded, Specialsauce, Kobra, WanderingStar,Qrk and aclaunch
[/COLOR][/SIZE]

You guys just helped for the easy stuff...

now everything works... not with ubuntu : with Mandrake. For you noobs out there... you need custom  drivers made by third parties for rage (except 128 ) and fire gl cards...

Your community sucks... At least the Mandrake community helped me!




so long suckaz!

P.S. : You guys can freeze my account, change my posts wutever i dont give a rat's ass.
P.S. #2 : And don't talk about my attitude... just admit it : you guys suck... you only know what the tutorials say ... you don't even try to test the problem or even google the problem for that matter... you don't go on the hardware makers site... you all just suck

example : quote from ati

> Linux drivers are only supported for RADEON 8500 Series and newer

But noooo you noobs tell me to install and use the drivers... FOR NOTHING!!

omfg i'm soo pissed st you idiots

---

### Post by peteyp666 on 2005-12-19
[QUOTE=essell25]
peteyp666? I don't like you either.
...
now everything works... not with ubuntu : with Mandrake. For you noobs out there... you need custom  drivers made by third parties for rage (except 128 ) and fire gl cards...

Your community sucks... At least the Mandrake community helped me!




so long suckaz!

P.S. : You guys can freeze my account, change my posts wutever i dont give a rat's ass.
P.S. #2 : And don't talk about my attitude... just admit it : you guys suck... you only know what the tutorials say ... you don't even try to test the problem or even google the problem for that matter... you don't go on the hardware makers site... you all just suck

example : quote from ati



But noooo you noobs tell me to install and use the drivers... FOR NOTHING!!

omfg i'm soo pissed st you idiots[/QUOTE]
I never said I didn't like you, but at least you know about your crappy attitude.  I don't have an ATI card so I couldn't test the problem and I'm sure google works for you as well.  Your experience with linux seemed new and I was trying to make sure you didn't skip something in the installation.  I am glad you solved your problem and hopefully other people will read this thread and learn from your experience.

---

