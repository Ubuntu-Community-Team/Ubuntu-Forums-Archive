---
title: "Ubuntu 10.4 LTS &amp; Quantum GIS (QGIS) 1.4 (Ubuntu version)"
date: 2010-05-03
forum: Education &amp; Science
---

### Post by badaveil on 2010-05-03
[img]http://lh6.ggpht.com/_yJ5Rhn3UxL4/S-ATHUeIhqI/AAAAAAAADEE/EgtzpCkjl9c/s800/Screenshot-2.png[/img]

I have installed both OS and GIS in my pc and they integrate well. This is good news for GIS users who want probably the most user-friendly open source GIS...QGIS!:D

---

### Post by Herman on 2010-05-03
That's good news, badaveil, I have been waiting for Quantum GIS to be installable in 10.04 for a long time now.
The last time I checked it looked as if there was a repository there for it in [https://launchpad.net/~qgis]("https://launchpad.net/%7Eqgis")  and I found another page off that for 'unstable, which led me to one of the most convoluted, inside-out and back to front set of instructions for how to add a repository I have ever seen in my life. No matter how hard I tried I wasn't able to get it, and  I wasted hours and hours of my precious time. It was extremely frustrating, it seemed as if it was there, and yet I just wasn't able to get it.

This time I am looking again in [qgis-stable]("https://launchpad.net/%7Eqgis/+archive/stable") and in                                            [qgis-unstable]("https://launchpad.net/%7Eqgis/+archive/unstable") but I can only find quantum gis for earlier versions of Ubuntu.

Ah, okay, finally I have found it, but it took a separate internet search to do that, for some reason I wasn't able to get there from their main page.
Quantum GIS for 10.04 is here, [https://launchpad.net/~ubuntugis/+archive/ubuntugis-unstable?field.series_filter=lucid]("https://launchpad.net/%7Eubuntugis/+archive/ubuntugis-unstable?field.series_filter=lucid")

Now for the complicated part ... understanding their hopelessly complicated instructions! :confused:

It's only thanks to your thread, sir, in previous versions of Ubuntu that I have ever been able to use Quantum GIS at all. 
I will try to figure it out again, but I might need help. :)

---

### Post by Herman on 2010-05-03
**1) Here are the official instructions,**
> **Adding the PPA to Ubuntu 9.10 (Karmic) and later**

             If you're using the most recent version of Ubuntu (or any version  from       Ubuntu 9.10 onwards), you can add a PPA to your system with a  single       line in your terminal.     
> **Step 1:** On the PPA's overview page, look for the       heading that reads *Adding this PPA to your system*. Make a  note       of the PPA's location, which looks like:     
             ppa:gwibber-daily/ppa
**And here is what I did,**
Okay, so I copy:  **ppa:ubuntugis/ubuntugis-unstable **to my system's software sources?

So I went 'System'- 'Administration' - 'Software Sources', and clicked the tab for 'other software'.
Then I pressed the 'add' button down in the lower left-hand corner and up popped a dialog for the apt line, and I pasted in:  **ppa:ubuntugis/ubuntugis-unstable **and my 'add source' button became active, so I clicked it. 

All seems good so far. 

**2) Here are the official instructions,**
> **Step 2:** Open a terminal and enter:     
             sudo add-apt-repository ppa:user/ppa-name     
             Replace ppa:user/ppa-name with the PPA's location  that you       noted above.**And here's what I did,**
```
herman@tsunami-lynx:~$ sudo add-apt-repository ppa:ubuntugis/ubuntugis-unstable
[sudo] password for herman: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 6B827C12C2D425E227EDCA75089EBE08314DF160
gpg: requesting key 314DF160 from hkp server keyserver.ubuntu.com
[COLOR=Red][B]gpg: key 314DF160: "Launchpad ubuntugis-stable" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1[/B][/COLOR]

```** It seems like it's not working.**
> Your system will now fetch the PPA's key. This enables your Ubuntu       system to verify that the packages in the PPA have not been  interfered       with since they were built.     **I tried again,**
```
herman@tsunami-lynx:~$ sudo add-apt-repository ppa:ubuntugis/ubuntugis-unstable
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 6B827C12C2D425E227EDCA75089EBE08314DF160
gpg: requesting key 314DF160 from hkp server keyserver.ubuntu.com
[COLOR=Red][B]gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error[/B][/COLOR]

``` **It still seems like it's not working.**
What an I doing wrong?  :confused:

**EDIT: Oops - Hey it worked!**
I ignored the apparent error messages and went into Synaptic Package Manager regardless, run 'reload', and searched for qgis and it was found!

Now I have Quantum GIS 1.4.0-Enceladus open and ready for me so start work!  :)

Thank you, for letting me know it's available at last, badaveil, and I hope I wasn't bothering you here. Sorry if I annoyed you. That turned out to be a lot easier than I thought.

---

### Post by Herman on 2010-05-03
:D After doing this on one more computer, I found that we can skip step 2, it seems as if the key must be getting added automatically.

---

### Post by badaveil on 2010-05-03
You should have just asked me how?:


1. Copy everything below then go to accessories/gedit text editor and save as "qgis publickey"

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESgc8TwEEANnh7UAVSnJoE8fyLMss5VUuG+1Bw5W2XWEyxuOCfMMAnJq4FY7YOjaFwX37
KdPTy5/+NVqegazUbB3WV8d21aRhN977HXYztt/1Ft73m30FLbZC3vRwaMg5oaWQ/XAy9ONY
8QND/ahhSNf3d8wyrfAlG2RLaUeASDXqMBOU2fKVABEBAAG0GkxhdW5jaHBhZCB1YnVudHVn
aXMtc3RhYmxliLYEEwECACAFAkoHPE8CGwMGCwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAKCRAI
nr4IMU3xYG3iA/0dnVOYqpLayEgzmlJ6mwJnVKcL+tGRfNsKQTHe77skFBcO/YyLez29HJJJ
S0xGtkZ+bUEQ3mdKnV/jGK4ygeSouItfz3fM3/PvVbZMbARUTzOdIR/Hv8GUyVhY3dPR8NEy
w0Op41kCOuxZBVU985IQHDDQe6Fw1q6IFjOES0NMjQ==
=gZdQ
-----END PGP PUBLIC KEY BLOCK-----

2. Go to  file system/etc/apt/sources.list enter administrator password/authentication/import key file (search for that qgis public key you saved)

3. Now select sources.list/other software/add/type "deb [http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu](http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu) lucid main"

4. Now select sources.list/other software/add/type " main 
deb-src [http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu](http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu) lucid main"

5. Select close. You will told you are out-of-date, select yes (I think) and all necessary files will be downloaded to the pc.

6. Go to system/administration/synaptic package manager/type "qgis" under quick search/select qgis(if this file along with 5 other related files are not there, you did not go step 1-5 properly)right-click qgis/select mark for installation/select apply. When the status box of qgis and 3 other related files turn green, you have succeeded!

7. Go to main menu/science/quantum gis/plugin/fetch python plugin/repositories/add 3rd party repositories. All plugins will download.

8.In the QGIS Python Plugin Installer, select plugins/select not installed plugin of your choice/install/upgrade plugin. Repeat and select other not installed plugins of your choice.

9.Go to main menu/science/quantum gis/plugin/fetch plugin/select plugin of your choice to enable it.

10.In the QGIS Python Plugin Installer, select options/tick "check for updates on startup/select "once a day". Because of this, when new plugins are available or upgradeable, it will be made known in the lower QGIS panel.

THE END

---

### Post by FiReSTaRT on 2010-05-06
That's great news. I use it for work and I also wanna continue testing certain plugins for it. The DL pages need to be more clear as the Lucid option wasn't visible, so I figured I'd have to compile from source. Quick googling of this thread helped me get it done the easy way.

---

### Post by badaveil on 2010-05-06
> **FiReSTaRT said:**
> That's great news. I use it for work and I also wanna continue testing certain plugins for it. The DL pages need to be more clear as the Lucid option wasn't visible, so I figured I'd have to compile from source. Quick googling of this thread helped me get it done the easy way.

I noticed qgis.org even that its deb and deb-src command lines ready long before the official 10.4 LTS came out but the source codes were available only after the official launch of Lucid.

---

### Post by BigBaka on 2010-05-25
Hey thanks for this. 

I used to use QGIS in Intrepid, but have now upgraded to Lucid. Alas, although I got QGIS to work using your instructions, I found it very unstable and also unable to load MrSid raster files, which basically made it unusable. When I was running QGIS on Intrepid I loaded the stable repository, and then made some modifications that I saw somewhere on a forum to allow MrSid files into an upgraded 1.4.0 edition, that was extremely stable and worked well. 

Alas, I can't find the repositories for the stable 1.0.2 version. Do you have any info on where they are, and / or allowing MrSid files to be read in QGIS.

Regards,
BB

---

### Post by badaveil on 2010-05-25
> **BigBaka said:**
> Hey thanks for this. 

I used to use QGIS in Intrepid, but have now upgraded to Lucid. Alas, although I got QGIS to work using your instructions, I found it very unstable and also unable to load MrSid raster files, which basically made it unusable. When I was running QGIS on Intrepid I loaded the stable repository, and then made some modifications that I saw somewhere on a forum to allow MrSid files into an upgraded 1.4.0 edition, that was extremely stable and worked well. 

Alas, I can't find the repositories for the stable 1.0.2 version. Do you have any info on where they are, and / or allowing MrSid files to be read in QGIS.

Regards,
BB

Try [http://www.softpedia.com/get/Science-CAD/Quantum-GIS.shtml](http://www.softpedia.com/get/Science-CAD/Quantum-GIS.shtml)

---

### Post by BigBaka on 2010-05-25
> **badaveil said:**
> Try [http://www.softpedia.com/get/Science-CAD/Quantum-GIS.shtml](http://www.softpedia.com/get/Science-CAD/Quantum-GIS.shtml)

Hmmm, that link doesn't seem to be working. [www.softpedia.com](www.softpedia.com) keeps directing me to [http://w3.mict.go.th/](http://w3.mict.go.th/) which then fails to load.

---

### Post by badaveil on 2010-05-25
Try [http://www.softpedia.com/progDownload/Quantum-GIS-Download-76638.html]("http://www.softpedia.com/progDownload/Quantum-GIS-Download-76638.html")

---

### Post by BigBaka on 2010-05-26
Same thing as before, being redirected to some thai website that doesn't load? Is that just me or does the same thing happen to you?

---

### Post by BigBaka on 2010-08-19
Hey, that link is finally working. But actually today I've just installed the latest version of QGIS 1.5 Tethys. Alas, the MrSID file format is still not accepted on an Ubuntu system. :(  Please post if you find a solution.

Regards,
BB

---

### Post by Herman on 2010-08-19
:D Hello badaveil,

Mine is upgraded automatically to Tethys too.
 I followed your instructions in steps numbered 7, 8, 9 and 10 from [post # 5]("http://ubuntuforums.org/showpost.php?p=9230809&postcount=5"), some time ago and now I have **92 plugins** available. **Wow!**
> 7. Go to main menu/science/quantum gis/plugin/fetch python  plugin/repositories/add 3rd party repositories. All plugins will  download.

8.In the QGIS Python Plugin Installer,  select plugins/select not installed plugin of your  choice/install/upgrade plugin. Repeat and select other not installed  plugins of your choice.

9.Go to main menu/science/quantum gis/plugin/fetch plugin/select plugin of your choice to enable it.

10.In the QGIS Python Plugin Installer,  select options/tick "check for updates on startup/select "once a day".  Because of this, when new plugins are available or upgradeable, it will  be made known in the lower QGIS panel.Thanks for your great advice again! :)

---

### Post by BigBaka on 2010-08-20
After much suffering I have finally managed to get QGIS 1.5.0 Tethys up and running on Ubuntu 10.4 Lucid LTS fully integrated with MrSID file formats. The Ubuntu GIS guys have a tutorial on how to do it here
[http://trac.osgeo.org/ubuntugis/wiki/TutorialMrSid](http://trac.osgeo.org/ubuntugis/wiki/TutorialMrSid)

---

### Post by cespinal on 2010-08-20
I'm very glad there are GIS users around the community. I have used arcGIS a little a couple of years ago and now I'm retaking it since I found a job that will require some GIS skills... kind of a dream come true since I always wanted to work hard with GIS and never found a real opportunity to do so. 

I have found using open source GIS a little painful, something always comes up during the installations.

---

### Post by Herman on 2010-08-20
I used to find qgis difficult to install too for some reason, but not this time. 
Give it a try, you might be in for a pleasant surprise! :)

My job involves GPS and GIS  work too. In an effort to be helpful, I have been adding random information quietly in another thread. Some of it pertains to getting started with Quantum GIS, some is about using Tango GPS and some is about Google Earth, here it is in case anybody is curious, [usb gps on ubuntu. how to, maybe...]("http://ubuntuforums.org/showthread.php?t=1430516")

Regards, Herman :)

PS @ BigBaka, thanks for sharing, I don't have any MrSID files yet, but if I do get any I'll know where to look up how to use them.

---

### Post by badaveil on 2010-08-20
> **cespinal said:**
> I'm very glad there are GIS users around the community. I have used arcGIS a little a couple of years ago and now I'm retaking it since I found a job that will require some GIS skills... kind of a dream come true since I always wanted to work hard with GIS and never found a real opportunity to do so. 

I have found using open source GIS a little painful, something always comes up during the installations.

At the time of writing, QGIS 1.4 was the latest version, now, 1.5 version is. Friends and me who see how the 1.5 performs agree it is impressively fast in zooming in and out as against 1.4. Installing the windows version is chicken feed for a GUI-man like me though installing the Ubuntu version isn't that difficult once you copy and paste the appropriate script which I got advised from a QGIS forumer.

---

### Post by cespinal on 2010-08-20
Can you help me on this?It seems I cannot download qgis directly from the repositories....

---

### Post by cespinal on 2010-08-20
> **Herman said:**
> I used to find qgis difficult to install too for some reason, but not this time. 
Give it a try, you might be in for a pleasant surprise! :)

My job involves GPS and GIS  work too. In an effort to be helpful, I have been adding random information quietly in another thread. Some of it pertains to getting started with Quantum GIS, some is about using Tango GPS and some is about Google Earth, here it is in case anybody is curious, [usb gps on ubuntu. how to, maybe...]("http://ubuntuforums.org/showthread.php?t=1430516")

Regards, Herman :)

PS @ BigBaka, thanks for sharing, I don't have any MrSID files yet, but if I do get any I'll know where to look up how to use them.

Hi Hernan... as far as I am aware, I will be working with database management and georeferencing streams of satellite imagery...I know is not a very hard thing to do but I can't wait to get my hands on that!!!! :D

---

### Post by badaveil on 2010-08-20
> **cespinal said:**
> Can you help me on this?It seems I cannot download qgis directly from the repositories....

Glad to ;)


Copy paste the following commands in a terminal line by line then  press ENTER after each line script was done:

sudo add-apt-repository ppa:jef-norbit/qgis-unstable-ubuntugis-jef
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install qgis

---

### Post by cespinal on 2010-08-20
The following packages have unmet dependencies:
  qgis: Depends: libgdal1-1.7.0 but it is not installable
        Depends: libgeos-c1 (>= 3.2.2) but 3.1.0-1 is to be installed
        Depends: libqgis1.5.0 but it is not going to be installed
        Depends: libqt4-svg (>= 4:4.5.3) but it is not going to be installed
        Depends: libqwt5-qt4 but it is not going to be installed
        Recommends: qgis-plugin-grass but it is not going to be installed
        Recommends: python-qgis but it is not going to be installed


Seems I'm falling in a dependency hell

---

### Post by badaveil on 2010-08-20
I had assumed that you hadn't any QGIS or part of QGIS installed and you didn't tell me either but an advise given prior to the script was "Just uninstall your version of qgis (if you have one on your ubuntu)".

I just followed through and everything works fine so I can't answer why it didn't work for you. I'm not a programmer:( so can't advise terminal wise but my best advise is for you to be a member of QGIS Forum and the QGIS user mailing list of which response from the latter is quicker. Have you been to [http://www.qgis.org/wiki/Download#Ubuntu]("http://www.qgis.org/wiki/Download#Ubuntu")?

---

### Post by Herman on 2010-08-20
It seems like there's a little problem of some kind in the repositories, so maybe wait a while and try again later.

I have a spare fresh new Ubuntu installation I am using for GRUB2 experiments to update my website, so I tried the same commands and I received the same error message.
Then I tried running through the commands most of us use to install software for playing music in case there might be something we need in that repository,  [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683") and I got even more error messages about packages not being available.

Finally I tried the steps we posted in the first page of this thread and it worked. I don't know why. I think my clumsy way of blundering into it in post #3 doesn't differ substantially from the way badaveil most eloquently summed it up in post#4, just that I used the GUI more. Unless I was just lucky and something in the repositories was fixed at the same time I tried again.
I guess the moral of the story is to just keep trying and you will succeed.

---

### Post by badaveil on 2010-08-20
QGIS site [http://www.qgis.org/wiki/Download#Ubuntu]("http://www.qgis.org/wiki/Download#Ubuntu") recommends:

**Ubuntu**
 *Release*
Current packages available for jaunty, karmic, lucid and maverick from

sudo apt-get install add-apt-repository 
sudo add-apt-repository ppa:ubuntugis/ubuntugis-unstable
sudo aptitude install qgis

---

### Post by cespinal on 2010-09-03
> **badaveil said:**
> QGIS site [http://www.qgis.org/wiki/Download#Ubuntu]("http://www.qgis.org/wiki/Download#Ubuntu") recommends:

**Ubuntu**
 *Release*
Current packages available for jaunty, karmic, lucid and maverick from

sudo apt-get install add-apt-repository 
sudo add-apt-repository ppa:ubuntugis/ubuntugis-unstable
sudo aptitude install qgis

Followed your recommendation. Here is the output when I try to install Qgis from the repos. 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  qgis: Depends: libgdal1-1.7.0 but it is not installable
        Depends: libgeos-c1 (>= 3.2.2) but 3.1.0-1 is to be installed
        Depends: libqgis1.5.0 but it is not going to be installed
        Depends: libqt4-svg (>= 4:4.5.3) but it is not going to be installed
        Depends: libqwt5-qt4 but it is not going to be installed
        Recommends: qgis-plugin-grass but it is not going to be installed
        Recommends: python-qgis but it is not going to be installed
E: Broken packages
```

I'm really in need of giving QGIS a try...

---

### Post by badaveil on 2010-09-03
cespinal,

I see from the output the last line state "E: Broken packages"

From my understanding, you have to fix broken packages first before you can even think of installing a related application. 

So what I can advise is to go to the Synaptic Package Manager then under Edit, select Fix broken packages.

If it got fixed, the status menu bar will state so. Only then repeat the earlier step.

If it still persist, under Synaptic, search QGIS and do a total removal of all related QGIS files then repeat the recommended QGIS download steps

If that still persist, do a total removal of all related QGIS files then repeat download following J.Norbit's repos.

If that still persist, I've run out of options:(

---

### Post by cespinal on 2010-09-03
Sorry...tried every one of your suggestions. 

The funny thing is that I haver never installed qgis...let alone had any qgis installation on my system.

---

### Post by badaveil on 2010-09-03
Then the final advice I can give is for you to subcribe to QGIS user mailing list at [http://lists.osgeo.org/mailman/listinfo/qgis-user]("http://lists.osgeo.org/mailman/listinfo/qgis-user")

Make a query, mention you tried to install QGIS based on :

sudo apt-get install add-apt-repository 
sudo add-apt-repository ppa:ubuntugis/ubuntugis-unstable
sudo aptitude install qgis

and your output was:


Code:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  qgis: Depends: libgdal1-1.7.0 but it is not installable
        Depends: libgeos-c1 (>= 3.2.2) but 3.1.0-1 is to be installed
        Depends: libqgis1.5.0 but it is not going to be installed
        Depends: libqt4-svg (>= 4:4.5.3) but it is not going to be installed
        Depends: libqwt5-qt4 but it is not going to be installed
        Recommends: qgis-plugin-grass but it is not going to be installed
        Recommends: python-qgis but it is not going to be installed
E: Broken packages

Ask for help.

Based on my experience, you should get a reply less than 24 hours.

Best of luck!):P

---

