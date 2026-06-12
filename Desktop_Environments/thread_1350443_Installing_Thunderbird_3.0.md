---
title: "Installing Thunderbird 3.0"
date: 2009-12-09
forum: Desktop Environments
---

### Post by CarlosinFL on 2009-12-09
Recently Thunderbird 3.0 for Linux was released and sadly Ubuntu is still using 2.x for good reason. I would like to know if I would have any problems downloaded the .bz2 file and using Thunderbird alone rather than a version that was packaged and installed from 'apt-get'?

I downloaded the file and extracted it. I can run / launch Thunderbird but my questions is where do I place the 'thunderbird' folder? Where would it go if I had installed 3.0 from my package manager? Can I simply move it there...where ever that is?

---

### Post by ikt on 2009-12-09
Should be able to install from the ppa:

[http://ubuntuforums.org/showthread.php?t=1214872](http://ubuntuforums.org/showthread.php?t=1214872)

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

### Post by wojox on 2009-12-09
Move it to your /opt directory. That's where I install applications from outside the repo's.

---

### Post by CarlosinFL on 2009-12-09
So I just add the following to the end of my sources.list?

```
ppa:ubuntu-mozilla-daily/ppa
```

---

### Post by adaucourt on 2009-12-09
> **Carlwill said:**
> Recently Thunderbird 3.0 for Linux was released and sadly Ubuntu is still using 2.x for good reason. I would like to know if I would have any problems downloaded the .bz2 file and using Thunderbird alone rather than a version that was packaged and installed from 'apt-get'?

I downloaded the file and extracted it. I can run / launch Thunderbird but my questions is where do I place the 'thunderbird' folder? Where would it go if I had installed 3.0 from my package manager? Can I simply move it there...where ever that is?

Usually in /etc/yourprogramname... some people prefer /opt/yourprogramname
Here is some documentation:
[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

---

### Post by LuisGMarine on 2009-12-09
add this to your sources.list

```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main 
```

Then you should be able to install it though apt-get, this command will update your sources and install thunderbird:

```
sudo apt-get update && sudo apt-get install mozilla-thunderbird

```

Even better .. after you add that to your sources.list and run the update command, you can even install it though the Ubuntu Software Center which is located by going to **Applications > Ubuntu Software Center**

Hope this helps! :popcorn:

---

### Post by CarlosinFL on 2009-12-09
> **LuisGMarine said:**
> add this to your sources.list

```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main 
```

Then you should be able to install it though apt-get, this command will update your sources and install thunderbird:

```
sudo apt-get update && sudo apt-get install mozilla-thunderbird

```

Even better .. after you add that to your sources.list and run the update command, you can even install it though the Ubuntu Software Center which is located by going to **Applications > Ubuntu Software Center**

Hope this helps! :popcorn:

I get the following when I try to do an update:

```
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE

```

---

### Post by gastly on 2009-12-09
I use mozilla builds of Thunderbird and it's not much of a difference really, that you use one from the repositories or from mozilla. Just that, you cannot automatically upgrade to a new version when it comes out, if you're using the mozilla builds (since it does not integrate with the package manager).

To 'properly' install Thunderbird from a tar.bz2 archive, you need to extract it in the **/opt** directory.

You can also use the ppa's as mentioned above, but here's what I do to install thunderbird on my system (yes, I don't like the ppa's :P):

[color=blue]**If you plan on using *only* the mozilla builds from now on, you can follow the following steps:**[/color]

**1. Extract Thunderbird to /opt**

Open up a terminal, 'cd' to the folder where you've downloaded the thunderbird package and type this:
```
sudo tar -jxf thunderbird-3.0.tar.bz2 -C /opt/
```

**2. Integrate it with the system**

Remove the 'old' thunderbird:

```
sudo apt-get remove thunderbird
```

and add a symlink in /usr/bin:

```

cd /usr/bin
sudo ln -s /opt/thunderbird/thunderbird

```

That's it. You can now use Thunderbird installed from the archive normally. The disadvantage of this method is that it will not upgrade to a newer version automatically, and you will always need to download the new version from mozilla and extract it in /opt.

I use this method and I've never had any problems with it :)

---

### Post by gastly on 2009-12-09
> **Carlwill said:**
> I get the following when I try to do an update:

```
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE

```

Geez, ppl write so fast lol, anyways.
Enter this command if you're getting the error:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key EF4186FE247510BE
```

and then run ```
sudo apt-get update
```

---

### Post by LuisGMarine on 2009-12-09
> **gastly said:**
> Geez, ppl write so fast lol, anyways.
Enter this command if you're getting the error:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key EF4186FE247510BE
```

and then run ```
sudo apt-get update
```

darn it beat me to the punch!

---

### Post by CarlosinFL on 2009-12-09
Thanks!

---

### Post by LuisGMarine on 2009-12-09
If this fixed your issue, please mark this thread as "Solved".  Thank you and best of luck.

---

### Post by ratcheer on 2009-12-09
I am confused (which is nothing new).

I added the mozilla-daily source. Now, when I run Update Manager, it offers to upgrade Firefox, which is already up-to-date, but not Thunderbird. What did I do wrong?

This is what I added:
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main

---

### Post by LuisGMarine on 2009-12-09
> **ratcheer said:**
> I am confused (which is nothing new).

I added the mozilla-daily source. Now, when I run Update Manager, it offers to upgrade Firefox, which is already up-to-date, but not Thunderbird. What did I do wrong?

This is what I added:
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main

Are you sure that thunderbird isn't already at 3.0?

---

### Post by khelben1979 on 2009-12-09
I have just installed Thunderbird 3.0 myself over here and I'm wondering how I can import my mail inbox which is stored locally on the harddrive with the old Thunderbird 2.

Shall I just manually copy over all the files from the old client to the new one? I was surprised that the import option did not include the possibility to import mail from the old Thunderbird (I guess I have missed something?)

---

### Post by gatorbrit on 2009-12-09
I updated the sources.list and ran the update and got the following

```
sudo apt-get install mozilla-thunderbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mozilla-thunderbird is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

But I am still running thunderbird 2.0 - not sure why it is not upgrading to  3.0


Any ideas?  Is it because I am running 64 bit ubuntu?

---

### Post by ratcheer on 2009-12-09
> **ratcheer said:**
> I am confused (which is nothing new).

I added the mozilla-daily source. Now, when I run Update Manager, it offers to upgrade Firefox, which is already up-to-date, but not Thunderbird. What did I do wrong?

This is what I added:
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main

Ok, I re-did the above, then specifically told it to install mozilla-thunderbird. On one hand, it was successful, but what it did was to reinstall 2.0.0.23.

So, I still need to know how to install or upgrade to Thunderbird 3.0.

Thanks,
Tim

---

### Post by gatorbrit on 2009-12-09
> **ratcheer said:**
> Ok, I re-did the above, then specifically told it to install mozilla-thunderbird. On one hand, it was successful, but what it did was to reinstall 2.0.0.23.

So, I still need to know how to install or upgrade to Thunderbird 3.0.

Thanks,
Tim

Are you running 64 bit ubuntu?

---

### Post by solitaire on 2009-12-09
> **gatorbrit said:**
> I updated the sources.list and ran the update and got the following

```
sudo apt-get install mozilla-thunderbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mozilla-thunderbird is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```But I am still running thunderbird 2.0 - not sure why it is not upgrading to  3.0


Any ideas?  Is it because I am running 64 bit ubuntu?

Thunderbird 3 is listed as a separate program (so you keep both) 
try:
```
sudo apt-get install thunderbird-3.0
```

---

### Post by ratcheer on 2009-12-09
> **gatorbrit said:**
> Are you running 64 bit ubuntu?

No, it is 32-bit.

Tim

---

### Post by ratcheer on 2009-12-09
> **solitaire said:**
> Thunderbird 3 is listed as a separate program (so you keep both) 
try:
```
sudo apt-get install thunderbird-3.0
```

Thanks, that resolves my question.

Tim

---

### Post by gatorbrit on 2009-12-09
> **solitaire said:**
> Thunderbird 3 is listed as a separate program (so you keep both) 
try:
```
sudo apt-get install thunderbird-3.0
```


Ah ha!   That worked!

---

### Post by LuisGMarine on 2009-12-10
lol I'm so dumb sometimes, I should of searched for packages and pin pointed the exact command instead of just giving you the general 'mozilla-thunderbird', which has worked in the past for me.  

Anyhow, glad you got it running, I'm about to install this puppy myself.):P

---

### Post by thuerrschmidt on 2009-12-13
The easiest way to install Thunderbird 3.0 in Karmic is by using the [Mozilla Beta PPA ]("https://launchpad.net/~micahg/+archive/mozilla-beta"). As of today it has Shredder RC3, which is by all practical means identical to the final Thunderbird 3 release.

The build from this PPA will integrate better into your Ubuntu and look much nicer than Mozilla's own. Plus, unlink the [Mozilla Daily Build PPA]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa"), you'll only get milestone releases, not daily updates.

---

### Post by timzak on 2009-12-13
Any issues with installing the Lightning extension with either the Mozilla or the PPA versions?  Is one better than the other for using with Lightning?  I'd like to try out Tbird3 but need to have calendar integration.

---

### Post by Lety on 2009-12-14
Could somebody tell is this the same version as Thunderbird 3 Final ?
```
Version: 3.0.1~hg20091209r4510+nobinonly-0ubuntu1~umd1~jaunty
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.7pre) Gecko/20091209 Shredder/3.0.1pre

```

Installed from here through apt-get :
```
http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu
```

---

### Post by ivotron on 2009-12-14
> **timzak said:**
> Any issues with installing the Lightning extension with either the Mozilla or the PPA versions?  Is one better than the other for using with Lightning?  I'd like to try out Tbird3 but need to have calendar integration.

I've been using TB3 with Lighting and GData provider since the alpha 2 and haven't experienced any issue with it.

---

### Post by jamesisin on 2009-12-14
Is there no repo for the final version then?

---

### Post by kmand on 2009-12-14
Using the apt-get approach how do you get a lighting extension compatible with the thunderbird-3.0

I've been building them in concert, but I would prefer to get updates of thunderbird-3.x and lightning automatically with apt-get.

---

### Post by Jr.Muffin on 2009-12-14
> **jamesisin said:**
> Is there no repo for the final version then?

The best way to install Thunderbird 3 (in my opinion) is [using Ubuntuzilla]("http://www.learningubuntu.com/software/how-install-thunderbird-3-right-way").[URL="http://www.learningubuntu.com/software/how-install-thunderbird-3-right-way"]
[/URL]

---

### Post by Domainbug on 2009-12-15
A silly question from a newbie.

Where do I find this command window in order to enter command lines for the purpose of installing TB 3 into Ubuntu V 9.10

Any help appreciated.
Lee

---

### Post by bofphile on 2009-12-15
Does anybody has a solution for the font's problem when using Thunderbird 3 from Ubuntuzilla ? 
I know that Thunderbird 3 from the Mozilla ppa does not suffer from this problem but I would prefer to have the latest stable version of Thunderbird (no daily build) and do not want to update Firefox as well when using this ppa.
Thanks.

---

### Post by Jr.Muffin on 2009-12-15
> **Domainbug said:**
> A silly question from a newbie.

Where do I find this command window in order to enter command lines for the purpose of installing TB 3 into Ubuntu V 9.10

Any help appreciated.
Lee

Go to the "Accessories" menu inside "Applications" and open up the "Terminal program". Paste in the commands in there, and press Enter.

---

### Post by Domainbug on 2009-12-15
Many thanks Jr Muffin.

Lee

---

### Post by Defiant Rat on 2009-12-15
> **Jr.Muffin said:**
> The best way to install Thunderbird 3 (in my opinion) is [using Ubuntuzilla]("http://www.learningubuntu.com/software/how-install-thunderbird-3-right-way").[URL="http://www.learningubuntu.com/software/how-install-thunderbird-3-right-way"]
[/URL]

+1

I used Ubuntuzilla to install the latest version of Thunderbird and everything worked fine :D

---

### Post by jamesisin on 2009-12-16
> **Jr.Muffin said:**
> The best way to install Thunderbird 3 (in my opinion) is [using Ubuntuzilla]("http://www.learningubuntu.com/software/how-install-thunderbird-3-right-way").[URL="http://www.learningubuntu.com/software/how-install-thunderbird-3-right-way"]
[/URL]

Well, that sounds mighty interesting.  Think I'll give that a roll.

---

### Post by sojusnik on 2009-12-19
@ bofphile

I'm experiencing the same problem and looking for a solution too.

---

### Post by Domainbug on 2009-12-19
[jamesisin]("http://ubuntuforums.org/member.php?u=612780")

That Unbuntuzilla script work a treat. Absolutely magic, Many many thanks and have a great Christmas.

Lee

---

### Post by michael37 on 2009-12-21
> **kmand said:**
> Using the apt-get approach how do you get a lighting extension compatible with the thunderbird-3.0

I've been building them in concert, but I would prefer to get updates of thunderbird-3.x and lightning automatically with apt-get.

There is no lightning-extention .deb available today compatible with thunderbird-3.x.

I posted a workaround [thread="1360488"]here[/thread]. Works well for 32-bit.  

[s]There is no 64-bit lightning compatible with thunderbird-3.x at all.[/s]

---

### Post by Benchrest on 2009-12-21
Ok, I have Thunderbird 3 installed as a separate program in /opt/thunderbird/
Now I would like to copy my mail, settings address book from .mozilla-thunderbird from TB2 but I am not sure where to copy to. There is no import function (unbelievable).

---

### Post by michael37 on 2009-12-22
> **Benchrest said:**
> Ok, I have Thunderbird 3 installed as a separate program in /opt/thunderbird/
Now I would like to copy my mail, settings address book from .mozilla-thunderbird from TB2 but I am not sure where to copy to. There is no import function (unbelievable).

That's because you don't need any import.  TB3 reads TB2 files natively.

```
cd ~
cp -a .mozilla-thunderbird .thunderbird
ln -s .thunderbird .thunderbird-3.0

```

---

### Post by michael37 on 2009-12-22
> **michael37 said:**
> There is no lightning-extention .deb available today compatible with thunderbird-3.x.

I posted a workaround [thread="1360488"]here[/thread]. Works well for 32-bit.  

[s]There is no 64-bit lightning compatible with thunderbird-3.x at all.[/s]

So, there is a working **64-bit** solution.  I just tested it. Works GREAT.

Advanced users and experts only.  If you need more info, read the following two links:
[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)
[https://help.ubuntu.com/community/ThunderbirdLightning](https://help.ubuntu.com/community/ThunderbirdLightning)

[LIST]
[*]Enable mozilla-daily repository
[*]Install or upgrade thunderbird-3.0 and thunderbird-3.0-gnome-support packages.  This will install 3.0.1pre version (argh, but it works).
[*]Do not upgrade other packages, esp Firefox, to daily builds
[*]Disable mozilla-daily repository.
[*]Download lightning.xpi and gdata-provider.xpi from "2009-12-03 - lightning 1.0pre x86_64 linux" folder.  See [https://help.ubuntu.com/community/ThunderbirdLightning#Lightning%20for%20Thunderbird%203.0](https://help.ubuntu.com/community/ThunderbirdLightning#Lightning%20for%20Thunderbird%203.0).
[*]Start Thunderbird 3 from Applicatios->Internet->Shredder 3 Mail/News
[*]Install extensions via Tools->Add-ons
[/LIST]

---

### Post by Benchrest on 2009-12-22
> **michael37 said:**
> That's because you don't need any import.  TB3 reads TB2 files natively.

```
cd ~
cp -a .mozilla-thunderbird .thunderbird
ln -s .thunderbird .thunderbird-3.0

```

I guess I was not clear enough. TB3 does not find TB2 profile automatically. Nor does the import function recognise it. So I was left with not knowing where TB3 needed the information copied to. I since have found in the profiles where I can point to the existing profile by changing the file address. But before that I created a profile and then looked to see where TB3 stored it. Where as TB2 uses .mozilla-thunderbird , tb3 uses .thunderbird Still having a few problems but I think I see what I need to do. Not being a command line person, not sure what your commands were for.

---

### Post by ratcheer on 2009-12-22
> **Benchrest said:**
> I guess I was not clear enough. TB3 does not find TB2 profile automatically. 

?? 

It found mine.

Tim

---

### Post by Benchrest on 2009-12-22
> **ratcheer said:**
> ?? 

It found mine.

Tim

Thanks Tim, That tells me I screwed something up:) . I think I will start over. It doesn't take that long to install it and it will clear up another error I made. That is exactly what I needed to know that it should find the existing tb2 profile, mail address list etc. I don't need to jump through hoops to make it work.

---

### Post by Wollombi on 2009-12-22
If you want it from a PPA, then do the following:

1. If Thunderbird is installed:
```
sudo apt-get remove thunderbird
```

2. Add the Mozilla daily PPA:
```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
```

3. Install Thunderbird 3:
```
sudo apt-get install thunderbird-3.0
```

4. Enjoy


Alternatively, if you just want to download the tar file from Mozilla and install it manually, then you can do the following:

1. download the file
2. at the command line navigate to the folder you downloaded to
3. run the following:
```

sudo tar -jxvf thunderbird-3.0.tar.bz2 -C /opt

```
4. You can now launch it at the command line with the command /opt/thunderbird/thunderbird and/or you can create a launcher (in the menu, on the desktop, or wherever else) that executes the same command.

---

### Post by michael37 on 2009-12-22
> **Wollombi said:**
> If you want it from a PPA, then do the following:

2. Add the Mozilla daily PPA:
```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
```


And after you finish, go to System->Software Sources and uncheck ubuntu-mozilla-daily.  It has a good chance of messing up your Firefox.

---

