---
title: "Internet Browsers off the beaten track  Midori Seamonkey..."
date: 2012-04-20
forum: Desktop Environments
---

### Post by shantiq on 2012-04-20
and maybe some of you know others too......



encountered problems recently with Opera [since the Flash update] and was getting white screens freezing the entire machine



so looking around i found lightning flash [Midori ]("http://beginlinux.com/appsm/midori/midori-web-browser")  much faster and pared down  it is in the repo



Also [Seamonkey]("http://www.seamonkey-project.org/releases/")


Now this one is not basic and seems ok too

Only problem is the one in the repos does not work on recent Ubuntu versions.  it is far too old

But SeaMonkey 2.8 can be[ downloaded ]("http://www.seamonkey-project.org/releases/")as a tar.bz2 in many languages

So i found i had to do this to get it started


Unpack to home folder then

```
sudo mv seamonkey /usr/local
```Right click on desktop to create a launcher [if on Oneiric ]("http://ubuntuforums.org/showpost.php?p=11420857&postcount=2")  enter Seamonkey in properties  then command is

```
/usr/local/seamonkey/seamonkey
```Then to go to the net and find a logo  or use 



[IMG]http://1.bp.blogspot.com/-oHGvVeRtxHM/TuYtFTzXzCI/AAAAAAAAAlI/6J_QxJSOXoA/s1600/seamonkey-logo-original.png[/IMG]

Right-click on your launcher /properties/click on image and find where you stored logo

=================================


Any others one should be aware of??

---

### Post by kohoutek1 on 2012-04-20
I could not get Midori to open after downloading from the repos.

---

### Post by shantiq on 2012-04-20
maybe look again:KS:KS

it did that for me yesterday too


click on the add + sign on left hand side

[ATTACH]216336[/ATTACH]   once installed and ignore message 


or try and install from software centre  [unless did that already]

---

### Post by maureenc on 2012-04-23
Hi Shantiq...

I love Seamonkey and run it on an ancient recycled Easynote.... It has just about everything from briliant Cookie management (so that I can keep things like Quanterve and all of the other annoying market research cookie out.... It has neat colour tabs so I know where I am.... It is really fast and cnfigurable.... Can use Greasemonkey, scripts... everything you could want really and you can even change the background colour of all pages so that you have a nice restful surf without the hideous white glare!

My only problem is that I can't get it to install properly on Ubuntu 11.10 on my Toshiba AC100.... As you say, it isn't available anymore through the repositories and I have not succeeded with the TAR.GZ... When I try to run it I get the message "failed to execute child process "usr/local/seamonkey/seamonkey" (No such file or directory).

Any ideas?


Another rapid and very neat browser is Arora (Not Aurora Firefox).

It has third party cookie manage,ent and adblock as standard and can run some user scripts.... It has a good feel to it but unfortunately doesn't seem to be being supported anymore.... SO no upgrades.... I shall keep it on the Netbook though simply because I like tit so much.

Midori is BRILLIANT.... I've have it on my dekstop for years.... It has colour tabs and can use Greasemonkey emulation and user scripts.... Has aneat "vieing panel so you can see what is going on with cookies etc.... It also has the wonderful Speedial page which is great.... Only problem is that my version 0.4.2 doesn't allow me to block thirdp-party cookies.... And I am not able to upgrade via the Midori Launchpas PPA...

I have been trying for weeks.... I know the 0.4.4 is there for Oeneiric but however hard I try I am told that I already have the latest version.... Really frustrating.... because I did downlad it originally via the ppa... I currently have 0.4.0-2build0.1.... I tried "downgrading the 0.4.0-2 Oeneric  and then trying to upgrade again.... Didn't work and now I don't even get that version to chose from...

There is also something new that looks intersting called QUPZILLA but I had problems with that as well!

I think these issues may lie with the fact that the Ubuntu was loaded via NVIDIA flash bootloader using the "ubuntu-11.10-preinstalled-desktop-armel+ac100" image.... Maybe I will never be able to upgrade on it?  

Anyway.... If you manage to get Qupzilla installed, I'd be interested.... Also if you know what I have done wrong with Seamonkey!

Cheers,
Mo

---

### Post by wacky_sung on 2012-04-23
I still prefer to use Google Chrome which is the most secure browser while Chrome update from Ubuntu repo is way too slow and behind the patch release date and time.

---

### Post by shantiq on 2012-04-23
Mo   it looks as if you forgot the first forward slash  :KS [assuming you have placed the seamonkey folder in /usr/local which i am sure you have]


so try   again with    ```
/usr/local/seamonkey/seamonkey
```
will definitely check [QUPZILLA ]("http://www.qupzilla.com/download")and Arora.  Thanx for those tips

Qupzilla started up fine here

and > sudo apt-get install arora good too



Wacky   my problem with Google anything [and yes their browser IS excellent ] is they work Hand in Hand with CIA etc... and all your data is passed around [alledgedly] and i am no criminal but like my privacy or at least a chance/illusion:KS of privacy;   i still use Googlemail as i have too many things tied into it;   but do not wish to use their excellent browser 

**Linux for me is Latin for off-the-beaten-track**  and i aim for the non-corporate software whenever given the choice 

[IMG]http://img838.imageshack.us/img838/5745/smilie33.png[/IMG]

---

### Post by maureenc on 2012-04-23
Hi Shantiq,
I have since moved it to /usr/share which is where Midori sits....

Tried it again with the first slash and:
```

```mo@mo-laptop:~$ sudo /usr/share/seamonkey/seamonkey
/usr/share/seamonkey/seamonkey-bin: 1: Syntax error: "(" unexpected
```

```

Which is what I had the past few times I tried...

I know It is something simple?
Mo

I did put the above in code tags so not sure why it didn't work

---

### Post by shantiq on 2012-04-23
sorry MO  this is is in  a launcher on desktop right?   and the line   > /usr/local/seamonkey/seamonkey
  in command


what is the whole message you are getting?


unexpected....  what?


This is what i see when i right-click on launcher and choose properties

[ATTACH]216478[/ATTACH]

---

### Post by maureenc on 2012-04-24
Hi Shantiq,

I've deleted the whole lot and started from scratch three times now and still won't launch......Although launcher is now on Desktop rather than in top toolbar..... 

My launcher"properties" are exactly the same except that mine show 29 bytes.... But we won't squabble over that, will we!

I notice, however, that the other launchers don't have the full location, just the name "Midori %U" but I don't know what that means.... Doesn't work when I use that location instead anyway.

Permission is set for me and as executable.....

When you extracted yours from the TAR did you just do "extract here" from right click? That's what I did....

At least it's not giving an error anymore... Just not doing anything!

The reason I can't get any ppa updates or new software from those repositories is that work seems to have come to a stop on Ubuntu's Armel Deb dream.... Nothing is going into the repositories for this device anymore so my 0.4.2 version of Midori will be the last and Qupzilla will never make it at all!

Arch Linux has stopped developement on the AC100 too I think but there may be so work for other Nvidia/Tegra chips along the line that can be hacked.... I am hopeful....

I could try going for Precise but not sure I would be any better off and it takes so much effort to get something that resembles a working system up and running with so little info available..... 

Shame.... The Toshiba AC100 is a neat device.....and very cheap!

---

### Post by RichardCain on 2012-04-24
Hi Shantiq,

If you really like Seamonkey, then you'd be better installing it from the [Ubuntuzilla PPA]("http://www.ubuntuupdates.org/ppa/ubuntuzilla?dist=all") as it will keep it up to date.  However it is very much Mozilla's second best browser and doesn't receive the same amount of care and attention that Firefox does.

Personally, I use Firefox [speeded up]("http://www.ubuntugeek.com/speed-up-firefox-web-browser.html") (I like to the live bookmarks) and Chrome for work ('cos it's just so fast).  I've also heard of security issues with Midori, so wouldn't recommend that.

EDIT:  If you're looking for alternatives, you might find some inspiration [here]("http://en.wikipedia.org/wiki/List_of_web_browsers").

---

### Post by shantiq on 2012-04-26
thank you Richard for all this excellent info


the route i showed worked fine on Oneiric but failed on Pangolin

The PPA you showed here works on Pangolin

---

### Post by vasa1 on 2012-04-26
> **shantiq said:**
> ...
Also [Seamonkey]("http://www.seamonkey-project.org/releases/")
...
Only problem is the one in the repos does not work on recent Ubuntu versions.  it is far too old

But SeaMonkey 2.8 can be[ downloaded ]("http://www.seamonkey-project.org/releases/")as a tar.bz2 in many languages

So i found i had to do this to get it started

Unpack to home folder then
```
sudo mv seamonkey /usr/local
```Right click on desktop to create a launcher [if on Oneiric ]("http://ubuntuforums.org/showpost.php?p=11420857&postcount=2")  enter Seamonkey in properties  then command is
```
/usr/local/seamonkey/seamonkey
```Then to go to the net and find a logo  ...
...

Hey, Shantiq, I really want to thank you for posting this! I'm now on 12.04 and was having trouble running Seamonkey from my home folder. Now, I've followed your instructions to the dot and got it working from /usr/local/seamonkey/.

I just want to add a couple of things... To stick it in the Unity Launcher, I added alacarte (MainMenu) from the USC and that allowed me to make a launcher in 12.04 (Unity 3D). Then I started Seamonkey via the Dash and once it was running, I locked it to Unity's launcher on the left.

The other point is that we can find a bunch of icons here and I went with:
/usr/local/seamonkey/chrome/icons/default.png

Once again, a big thank you :)

---

### Post by shantiq on 2012-04-26
> **maureenc said:**
> Hi Shantiq,

I've deleted the whole lot and started from scratch three times now and still won't launch......Although launcher is now on Desktop rather than in top toolbar..... 

My launcher"properties" are exactly the same except that mine show 29 bytes.... But we won't squabble over that, will we!

I notice, however, that the other launchers don't have the full location, just the name "Midori %U" but I don't know what that means.... Doesn't work when I use that location instead anyway.

Permission is set for me and as executable.....

When you extracted yours from the TAR did you just do "extract here" from right click? That's what I did....

At least it's not giving an error anymore... Just not doing anything!

The reason I can't get any ppa updates or new software from those repositories is that work seems to have come to a stop on Ubuntu's Armel Deb dream.... Nothing is going into the repositories for this device anymore so my 0.4.2 version of Midori will be the last and Qupzilla will never make it at all!

Arch Linux has stopped developement on the AC100 too I think but there may be so work for other Nvidia/Tegra chips along the line that can be hacked.... I am hopeful....

I could try going for Precise but not sure I would be any better off and it takes so much effort to get something that resembles a working system up and running with so little info available..... 

Shame.... The Toshiba AC100 is a neat device.....and very cheap!


ok Maureen lets start absolutely from scratch

when you see > "Midori %U" that means you installed that one through the normal way [repository]


since here we are going from tar that does not apply/work

so let me break it down

1.   first the [**download**]("http://download.mozilla.org/?product=seamonkey-2.9&os=linux&lang=en-GBhttp://download.mozilla.org/?product=seamonkey-2.9&os=linux&lang=en-GB") of the tar; i pick the british one here but of course take the one you need


2. open it and unpack to  to home folder   it will be named seamonkey by default

Once it is safely in home folder


3.  ```
sudo mv seamonkey /usr/local
```     [or where you wish it to be]

4.  again create [**launcher**]("http://ubuntuforums.org/showpost.php?p=11420857&postcount=2") method is good for most recent versions of ubuntu


5.  ```
/usr/local/seamonkey/seamonkey 
```   in command in launcher


this time  :KS:KS:KS:KS  



 ** PS**   thank you Vasa for feedback

---

### Post by maureenc on 2012-04-26
Hi again Shantiq...

Thank you for explaining about the %U bit.... One less mystery in my Ubuntu world is always welcome!

I am currently on my fourth "starting from scratch" with Seamonkey.... He/She and I are becoming quite close friends... We may not yet understand one another.... But we have hopes... Well, one of us does.

I note that your link is to the 2.9 beta version?  I have been downloading the 2.8 version in the assumption that it  would be safer to do so?

Apart from the bit about using Nautilus Script Manager to create the Launcher, I did everything as per your instructions.... I then used the Main Menu option under Applications > Other > to create a new launcher with the same properties as yours.... I didn't think that would make any difference.... I think that is the way that Vasal did it too?

I have now downloaded the Nautilus Script Manager and will try to get to grips with it tomorrow.... At the moment it just sits there with nothing in the display telling me that scripts must first be installed in /usr/share/nautilus/scripts... But not how to get a script into it.... Am I supposed to use Gedit? Anyway.... Will check that out tomorrow... I don't think it is the cause of the problem.

The "desktop configuration file (application/x-desktop) with the seamonkey logo is exactly the same as yours.... apart from the number of bytes being 277.

But.... I don't think any of that makes any difference because... From everything I have read so far I believe I should be able to double click on the /usr/local/seamonkey/seamonkey shell file and it should run? It asks me if I want to run in terminal, display or run.... But when I select Run...nothing happens.... Which is what is wrong.... but why..... I have the right permission... I am the owner and it is set to execute.... But it doesn't.... No matter how much I plead and cajole.... Nada... Niet... Nothing....

In the folder there is also a "seamonkey-bin" which is also executable ("executable (application/X-executable)

I've just extracted the 2.9 folder and that doesn't run the seamonkey/seamonkey either....

I'm beginning to think this is yet another quirk of the Armel installation... Plus I am not running under Unity but using Gnome Session-Fallback.... But that shouldn't make any difference?

Thank you for your patience Shantiq

---

### Post by shantiq on 2012-04-27
ha well it might be the Armel thing

i too run on Gnome Session-Fallback since i LOathe U-know what


Best of luck with it all.   No doubt it will become clear at some point :KS:KS:KS

---

### Post by shantiq on 2012-04-27
faster route as indicated earlier on for SEAMONKEY    this worked on Precise when the other route would not


```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29

```


CLICK ENTER


THEN ENTER THIS


>  echo -e "\ndeb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main" | sudo tee -a /etc/apt/sources.list > /dev/null


==> get the [**deb**]("http://heanet.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/pool/main/s/seamonkey-mozilla-build/seamonkey-mozilla-build_2.9-0ubuntu1_amd64.deb")

save the file to Downloads


```
cd Downloads

```




```
sudo dpkg -i seamonkey-mozilla-build_2.9-0ubuntu1_amd64.deb

```

---

### Post by maureenc on 2012-04-28
Hi Shantiq,

I tried that one yesterday and various other DEB downloads but get the same response when I try to install them "ERROR - WRONG ARCHITECTURE"

Problem is that this is not AMD64 or 386 or any of the normal ones but the NVIDIA TEGRA chip which is a completely different kettle of fish.

These links will give you some idea of what we have been trying to do:

[http://www.tabletroms.com/forums/ac100-rom-development/1920-experiment-linux-ubuntu-more-firmware-2-2-toshiba-ac100-intersolar-22.html](http://www.tabletroms.com/forums/ac100-rom-development/1920-experiment-linux-ubuntu-more-firmware-2-2-toshiba-ac100-intersolar-22.html)

[https://wiki.ubuntu.com/ARM/TEGRA/AC100](https://wiki.ubuntu.com/ARM/TEGRA/AC100)

But Ubuntu has lost interest in the AC100 now so there has been no build work for months now....Meaning that the software that was already in the repos last year is all that we have/will have....

There is an old version of Seamonkey that I could install but it is 2.0.13 and full of bugs for which I will never be able to get any patches!

I could try installing Precise on here but from other AC100  forums it sounds as though it doesn't work as well as 11.10.... Video doesn't work at all and I doubt I would be much better off......Besides it has been such a difficult "birth" getting this far with the Tegra.

I think I will have to leave my "experminenting" as it stands and use this little machine as it stands now.... Most things work .... pretty fast.... It cost me very little to have a fully functioning "laptop" with all mod cons.... And it is so small and light that it fits easily into a handbag!

On the other hand there is some work being done on Puppy Linux still that may be interesting.... If I can face it, that is!

Cheers Shantiq,
Mo

---

### Post by shantiq on 2012-04-28
now you talking

> Problem is that this is not AMD64 or 386 or any of the normal ones but  the NVIDIA TEGRA chip which is a completely different kettle of fish:KS:KS:KS

---

### Post by vasa1 on 2012-05-02
Just want to mention that I could update Seamonkey to 2.9.1 via the browser's internal update mechanism and so the update was a differential (delta) and small, less that 1 MB. That's great. My other browsers, Firefox and Chrome, **installed via ppas**, require downloading the full version whenever an update is available.

---

### Post by shantiq on 2012-05-02
yes Vasa   the "MOnkey"   is really quite a kicker

It is really growing on me and find myself there more and more:KS

---

### Post by jimwg on 2012-10-03
> **shantiq said:**
> and maybe some of you know others too......



encountered problems recently with Opera [since the Flash update] and was getting white screens freezing the entire machine



so looking around i found lightning flash [Midori ]("http://beginlinux.com/appsm/midori/midori-web-browser")  much faster and pared down  it is in the repo



Also [Seamonkey]("http://www.seamonkey-project.org/releases/")


Now this one is not basic and seems ok too

Only problem is the one in the repos does not work on recent Ubuntu versions.  it is far too old

But SeaMonkey 2.8 can be[ downloaded ]("http://www.seamonkey-project.org/releases/")as a tar.bz2 in many languages

So i found i had to do this to get it started


Unpack to home folder then

```
sudo mv seamonkey /usr/local
```Right click on desktop to create a launcher [if on Oneiric ]("http://ubuntuforums.org/showpost.php?p=11420857&postcount=2")  enter Seamonkey in properties  then command is

```
/usr/local/seamonkey/seamonkey
```Then to go to the net and find a logo  or use 



[IMG]http://1.bp.blogspot.com/-oHGvVeRtxHM/TuYtFTzXzCI/AAAAAAAAAlI/6J_QxJSOXoA/s1600/seamonkey-logo-original.png[/IMG]

Right-click on your launcher /properties/click on image and find where you stored logo

=================================


Thanks to your advice I installed SM 2.12.1 on my flash drive's Mint Maya! One thing -- how can I get Seamonkey listed on the Internet submenu of XFCE's main Menu? Thanks a million!

---

