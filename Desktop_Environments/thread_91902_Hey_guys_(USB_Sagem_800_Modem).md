---
title: "Hey guys (USB Sagem 800 Modem)"
date: 2005-11-18
forum: Desktop Environments
---

### Post by {anthrax} on 2005-11-18
I have spent the last 5 days trying multiple distros of linux, and I keep returning to Ubuntu as being my favourite.

My only problem is getting my damn USB sagem 800 modem to work. However everyday I come a step closer to getting it to work, I have a feeling today is the day when I finally get online with Ubuntu :D

Just like to say, love the look of the OS, really nice site layout we have here as well... and damn is this community friendly :)

So there we go, and introduction post... go me :D

---

### Post by ubuntu_demon on 2005-11-18
hi there!
welcome to the club :)

---

### Post by Brunellus on 2005-11-18
yet another tiscali user?

The Sagem USB DSL modem is a *notoriously* troublesome device to get running in Linux.  The easiest alternative would be to junk it and get a modem which speaks real ethernet.

---

### Post by eMuNiX on 2005-11-18
[QUOTE=Brunellus]yet another tiscali user?

The Sagem USB DSL modem is a *notoriously* troublesome device to get running in Linux.  The easiest alternative would be to junk it and get a modem which speaks real ethernet.[/QUOTE]
Yes ditch the USB modem, they all seem to be quite difficult to get working under Linux.  Have a look at eBuyer for ADSL routers (they have some for about £20, these have an integrated ADSL modem, look at something like the Safecom SAMR-4114), they are very easy to configure, will stay permanently connected (even when the PC is off) and will reconnect should your connection drop (BT outage or similar) and connect by Ethernet which often will set itself up.  It also means that it is very easy to share the connection with another PC or MAC.

---

### Post by {anthrax} on 2005-11-18
I want to get the USB modem to work after spending so much time messing with it, I know it can be done.

If after another week all else fails I will buy something else, but I refuse to give up yet lol.

---

### Post by quietglow on 2005-11-18
I completely understand that feeling. I've been working on my IR remote for days. I get paid enough per hour I could have bought 2 dozen IR keyboards (which would also solve the problem) in the time I've spent messing with this damn thing...and yet I keep on.

Linux. Not just an OS, but a hobby too.

---

### Post by lotusleaf on 2005-11-18
[QUOTE={anthrax}]I keep returning to Ubuntu as being my favourite.[/QUOTE]

A wise choice! :) Welcome to the forums! :)

---

### Post by aysiu on 2005-11-18
I don't know why this modem is so popular.
I quick search for "sagem" in the Ubuntu Forums came up with at least these:

[http://www.ubuntuforums.org/showthread.php?t=91602&page=3](http://www.ubuntuforums.org/showthread.php?t=91602&page=3)
[http://www.ubuntuforums.org/showthread.php?t=44459&highlight=sagem](http://www.ubuntuforums.org/showthread.php?t=44459&highlight=sagem)
[http://www.ubuntuforums.org/showthread.php?t=2307&highlight=sagem](http://www.ubuntuforums.org/showthread.php?t=2307&highlight=sagem)
[http://www.ubuntuforums.org/showthread.php?t=62280&highlight=sagem](http://www.ubuntuforums.org/showthread.php?t=62280&highlight=sagem)
[http://www.ubuntuforums.org/showthread.php?t=61827&highlight=sagem](http://www.ubuntuforums.org/showthread.php?t=61827&highlight=sagem)
[http://www.ubuntuforums.org/showthread.php?t=58962&highlight=sagem](http://www.ubuntuforums.org/showthread.php?t=58962&highlight=sagem)
[http://www.ubuntuforums.org/showthread.php?t=56963&highlight=sagem](http://www.ubuntuforums.org/showthread.php?t=56963&highlight=sagem)
[http://www.ubuntuforums.org/showthread.php?t=55677&highlight=sagem](http://www.ubuntuforums.org/showthread.php?t=55677&highlight=sagem)
[http://www.ubuntuforums.org/showthread.php?t=54320&highlight=sagem](http://www.ubuntuforums.org/showthread.php?t=54320&highlight=sagem)
[http://www.ubuntuforums.org/showthread.php?t=50154&highlight=sagem](http://www.ubuntuforums.org/showthread.php?t=50154&highlight=sagem)

---

### Post by {anthrax} on 2005-11-21
Cheers, I hadn't seen one of those forum posts before and that particular one has a method I havn't seen yet. *sigh* back to ubuntu to try and get this stupid modem to work.

---

### Post by GeneralZod on 2005-11-21
[QUOTE={anthrax}]Cheers, I hadn't seen one of those forum posts before and that particular one has a method I havn't seen yet. *sigh* back to ubuntu to try and get this stupid modem to work.[/QUOTE]

If you do get it sorted, could you please let us know how? This seems to be a very common question and is probably Wiki-worthy :)

---

### Post by {anthrax} on 2005-11-21
Ok heres the update. Today I got the ADSL light to come on :D wooooo a pretty light!!

lol only problem is I can't connect to the internet. For example, i open up firefox and type in [www.google.co.uk](www.google.co.uk), it tells me google could not be found.

When I have this thing sorted then I will write a guide on how to get it working. Only problem is I can't remember everything that I have tried lol.

---

### Post by {anthrax} on 2005-11-22
I'm really lost here guys, I don't know what the next step is I should take.

I'm using the Sagem 800 USB modem
ISP: Tiscali

I have finally got the ADSL light to show up, but I can't ping any addresses and can't browse pages on the net.

I think the problem may come from the fact its pppoa instead of pppoe?

How do I set this up?

---

### Post by Pablo_Escobar on 2005-11-22
What kind of Sagem USB 800 is it ??
Is it Sagem F@st 800 ?? Because if it is then maybe I can help - these modems are very popular at Polands main ISP.

---

### Post by kosmic on 2005-11-22
Have you tried to put in etc/resolv.conf the Dns numbers from your ISP ??

---

### Post by {anthrax} on 2005-11-22
Yes Pablo it is the sagem f@st 800, damned annoying thing too :p

---

### Post by Pablo_Escobar on 2005-11-22
[QUOTE={anthrax}]Yes Pablo it is the sagem f@st 800, damned annoying thing too :p[/QUOTE]
Ok, so be patient, today I'll translate the Polish How-to to understandable (I hope :) ) English.
Altough I don't have this USB modem - I hate that ISP, and connect via ethernet, I'll translate the How-To because it's been roled over a 1000 times by the Polish Ubuntu Community :)

Be patient and keep Your fingers crossed for my English translation :)

---

### Post by {anthrax} on 2005-11-22
Well thankyou very much Pablo. I really appreciate this.

lol I too hate tiscali now, however I don't pay for it, so i cant complain :p

If I don't understand parts of your translation, I will PM you or install IRC and chat with you about it. Hopefully we can create an english document we can spread around here so that others can get this damn modem working.

Once again thanks :)

---

### Post by Pablo_Escobar on 2005-11-22
If this how-to will be successfull I'll apply it to wiki.

This is a How-To successfully get Sagem F@st 800 USB going &#61514;
**It&#8217;s based on the Polish How-to and I&#8217;m unable to verify it, so give me feedback if it worked.**

**Step 1.**
We need to get some packages for the kernel that OS is using.
You can find out what kernel You are using by typing in terminal:
```
 uname &#8211;r 
```
When You know what kernel the OS is using go to synaptic search and install appropriate packages:
linux-kernel-headers-<kernel version>_<version>_<arch>.deb
kernel-package_<version>_all.deb
We will also need the sources file :
eagle-usb.tar.gz &#8211; it should be on the CD provided by Your ISP

**Step 2.**
We copy the eagle sources to /usr/src/
```
 cp eagle-usb.tar.gz /usr/src
```
We switch to that directory
```
 cd /usr/src
```
We unpack the sources file
```
 sudo tar -zxvf eagle-usb.tar.gz
```
We create symlink to the headers directory
```
 sudo ln -s linux-headers-<uname -r>
```

**Step 3. Compilation time**
We need to execute a command which will look like this:
```
 sudo make-kpkg --append-to-version=<kernel version> --revision=<package version> modules_image
```
Quick explanation &#8211;
<kernel version> depends on the kernel it can look like this:
-9-386
-9-k7
-9-amd64
Brief explanation : 
If our kernel is : 
2.6.12**-9-386**
We cut the last bit, leaving us with -9-386.
<package version> can be anything You like, but do not use special characters like &#8220;_&#8221;

We should get a nice package called: 
eagle-usb-modules-<uname -r>_2.1.1-2+<package version>_i386.deb

**Step 4. Installation time**
We install the created package by :
```
 sudo dpkg -i eagle-usb-modules-<uname -r>_2.1.1-2+<package version>_i386.deb
```
Now we need 2 additional packages
```
 sudo apt-get install eagle-usb-data eagle-usb-utils
```
In that step we may be asked to insert Ubuntu CD.
After all the installation and hard work one more thing is required:
```
 sudo eagleconfig
```
And follow the instructions given by the config.

**Shortcut :)**
If You&#8217;re using the generic Ubuntu kernel You can try the debs prepared by Polish Ubuntu users. They can be found at:
[http://www.paczki-ubuntu.cba.pl/](http://www.paczki-ubuntu.cba.pl/)

---

### Post by {anthrax} on 2005-11-22
Right I'm going to reinstall Ubuntu so I have a clean slate to work with. You should get the results soon.

---

### Post by {anthrax} on 2005-11-22
I get stuck at step three.

make-kpkg: command not found

What do I need to install to enable this command?

Alternatively how do you use the .deb files?

---

### Post by Pablo_Escobar on 2005-11-22
Did You apt-get: kernel-package and kernel-source ??
You may need also to get build-essentials.

Debs should be easy to install "sudo dpkg -i package.deb"

---

### Post by {anthrax} on 2005-11-22
For the .debs do I need to install all three of them?

I can dpkg -i eagle-usb-modules-2.6.12-9-386_2.1.1-2+20051014-1_i386.deb

but the others return a fatal error.

---

### Post by Pablo_Escobar on 2005-11-22
It's because, other debs are compiled for different architectures (k7, etc).
It seems that You have a Pentium and the 386 deb went ahead :)
Is there any improvement in net access ??

---

### Post by {anthrax} on 2005-11-22
Nope.

For a start the modem doesnt appear under networking and the ADSL light is not on.

I can't remember how I got it to appear under networking before the reinstall...

---

### Post by Pablo_Escobar on 2005-11-22
Did You do 
sudo eagleconfig

and 

Do these commands work ??
stopadsl
eaglectrl -w
startadsl

??

---

### Post by {anthrax} on 2005-11-22
They don't work

eagleconfig doesnt work either.

They did before the reinstall, when I installed my drivers another way.

---

### Post by Pablo_Escobar on 2005-11-22
Hmmmm, then the debs seem to be not working, the only way it seems is to compile the kernel module.
Install build-essentials and try to go ahead with the module.
Remember to remove the installed debs before !!

---

### Post by {anthrax} on 2005-11-22
Ok i can compile the kernel
I have already installed the version of GCC needed as well, so it shouldnt take too long.

How do i uninstall the debs?

---

### Post by Pablo_Escobar on 2005-11-22
Synaptic -> search -> eagle -> remove the installed packages.

---

### Post by {anthrax} on 2005-11-22
Right thats that sorted, currently waiting for it to install itself.

What do I do when its finished?

---

### Post by Pablo_Escobar on 2005-11-22
Just follow the next step in How-to :)

---

### Post by ace2005 on 2005-11-22
I have one of these modems too

I installed the ksernel source off the internet, gcc g++ and just about every other compiler package that was there and i also installed things like make and gmake.

Then i downloaded this:

[http://prdownloads.sourceforge.net/eagle-usb/eagle-usb-2.3.2.tar.bz2?download](http://prdownloads.sourceforge.net/eagle-usb/eagle-usb-2.3.2.tar.bz2?download)

Then i extracted it, went into there in konqeror and pressed F4 and konsole opens up with that dir already selected (i use Kubuntu), Since you're in gnome you might have to use CD to get into the directory

Then i did:

sudo ./configure

**make**

**make install**

when it was finished i did:

**sudo eagleconfig**

Which part in particular are you stuck on?

That was it

---

### Post by {anthrax} on 2005-11-22
I've done all that, installed the eagle-usb drivers and all that.

But now when I try startadsl, it doesn't do anything.

Both my power and ADSL light are on but when I open firefox and try type in [www.google.co.uk](www.google.co.uk), it says the page cannot be found.

What am I missing here?

---

### Post by Pablo_Escobar on 2005-11-22
Huh. One more thing I found in the how-to is this:

edit the file /etc/init.d/eagle-usb
we look for the bit called

# See how we were called.
case "$1" in
start)
$CMDECHO $START_SERVICE_MSG
touch $SYSCONF_FILE
if [ $ASYNCHRONOUS_START == 0 ] ; then

we replace it with

# See how we were called.
case "$1" in
start)
**eaglectrl -d**
$CMDECHO $START_SERVICE_MSG
touch $SYSCONF_FILE
if [ $ASYNCHRONOUS_START == 0 ] ; then 

2. Make sure Your login and paswword are supplied correctly

3. If this doesn't work try with **eagleconfig**  to select other thing : (chap/pap) secure authenthication (or something called like that - I can't verify :( )

4. One other thing - did You **sudo startadsl**  ??

---

### Post by {anthrax} on 2005-11-22
Ok i'll try that, brb in a few minutes with an update :)

---

### Post by {anthrax} on 2005-11-22
Ok I've tried all that, and still had no luck :(

Anybody else got any suggestions?

---

### Post by ace2005 on 2005-11-23
Oh i know this, well i think i do anyway

After you're in KDE open konsole

Type:

"sudo startadsl"

"sudo startadsl -s"

This should make the internet work, i had this problem with SuSE but not with Kubuntu

---

### Post by {anthrax} on 2005-11-23
I have tried that, nothing happens. Starting to lose my patience with this modem now.

---

