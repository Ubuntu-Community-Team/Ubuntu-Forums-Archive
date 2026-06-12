---
title: "Firefox 3.0.10 update - Firefox broken"
date: 2009-05-01
forum: General Help
---

### Post by StuartN on 2009-05-01
I just accepted the update of Firefox from version 3.0.9 to 3.0.10 that came out today, and all I get when Firefox restarts is a blank window with no menus and no functionality. I completely purged all traces of Firefox and re-installed, but it still doesn't function.

(I installed Epiphany-Gecko in the meantime).

Is anyone else affected by this?

---

### Post by ajaysutton on 2009-05-01
On one Ubuntu machine that I support, after the 3.0.10 upgrade ther title bar with the x in the upper left corner doesn't appear anymore.  I was attributing it to Netbook Remix but perhaps there's an issue with FireFox

---

### Post by Dai Bando on 2009-05-01
I had no problem with my 3.0.10. Did you reboot aftr the download.

---

### Post by Selfish Meme on 2009-05-01
I had an issue after the upgrade as well, it wouldn't start, just have the starting firefox box and then nothing. I tried reinstalling firefox as well no go, luckily it was a test machine and I just wiped it and started again.

About the only things different from standard where

network-manager-vpnc

repositories medibuntu and backports

awn window manager

and some theme changes

---

### Post by DeMus on 2009-05-01
> **StuartN said:**
> I just accepted the update of Firefox from version 3.0.9 to 3.0.10 that came out today, and all I get when Firefox restarts is a blank window with no menus and no functionality. I completely purged all traces of Firefox and re-installed, but it still doesn't function.

(I installed Epiphany-Gecko in the meantime).

Is anyone else affected by this?

3.0.10 works fine for me, no problems what so ever.

---

### Post by StuartN on 2009-05-01
> **Dai Bando said:**
> I had no problem with my 3.0.10. Did you reboot aftr the download.

Yes, a reboot sorted it. This is getting more and more like Windows...

---

### Post by scottuss on 2009-05-01
> **StuartN said:**
> Yes, a reboot sorted it. This is getting more and more like Windows...

At least Ubuntu doesn't automatically restart your machine after updates... ;)

---

### Post by DeMus on 2009-05-01
> **scottuss said:**
> At least Ubuntu doesn't automatically restart your machine after updates... ;)

Not yet.

---

### Post by codeseer on 2009-05-01
> **DeMus said:**
> Not yet.

Meh. I didn't have to restart.

(about that time.. all havoc breaks loose!)

---

### Post by jespdj on 2009-05-01
Look at this thread: [CAREFUL: Firefox 3.0.10 upgrade may not complete fully!](http://ubuntuforums.org/showthread.php?t=1142171)

I did not have any problems with the 3.0.10 update on my laptop (64-bit 9.04) and my netbook (UNR 9.04).

Try deleting your ~/.mozilla/firefox directory (this will reset Firefox settings to defaults and might de-activate plugins!).

---

### Post by codeseer on 2009-05-01
> **jespdj said:**
> Look at this thread: [CAREFUL: Firefox 3.0.10 upgrade may not complete fully!](http://ubuntuforums.org/showthread.php?t=1142171)

I did not have any problems with the 3.0.10 update on my laptop (64-bit 9.04) and my netbook (UNR 9.04).

Try deleting your ~/.mozilla/firefox directory (this will reset Firefox settings to defaults and might de-activate plugins!).

I'd just rename the entire .mozilla directory and try firing it up. Have you also tried starting it with 'firefox-3.0'?

---

### Post by nm4m on 2009-05-01
Firefox 3.0.10 is broke here.  Tried all the standard stuff, rebooting, deleting .mozilla, chown in the .mozilla folder, uninstalling reinstalling firefox and flash.  No joy.  Still looking.

Dave
NM4M

---

### Post by codeseer on 2009-05-01
> **nm4m said:**
> Firefox 3.0.10 is broke here.  Tried all the standard stuff, rebooting, deleting .mozilla, chown in the .mozilla folder, uninstalling reinstalling firefox and flash.  No joy.  Still looking.

Dave
NM4M

Define broken.

---

### Post by Yellow Pasque on 2009-05-01
> **nm4m said:**
> Firefox 3.0.10 is broke here.  Tried all the standard stuff, rebooting, deleting .mozilla, chown in the .mozilla folder, uninstalling reinstalling firefox and flash.  No joy.  Still looking.

Dave
NM4M
Start firefox from the terminal. Any helpful error output?

---

### Post by nm4m on 2009-05-02
That was pretty vague.  Screen comes up blank.  I did find that clicking on it opens menus all the way across the desktop.  Follows that standard File, Edit, and so on.

Opening it in a terminal does not offer any clues.  

Opening it in -safe-mode gives the same results.

Dave
NM4M

---

### Post by nm4m on 2009-05-05
There have been some issues, but none of the solutions have yet worked for me.  

[https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/360923](https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/360923)

Dave
NM4M

---

### Post by netwarriorwy on 2009-05-05
Hi!

I have a Jaunty fresh install on my laptop. 

The first thing i did was to update it...it updated the firefox and some other things. I didnt have to reboot, as a matter of fact I'm using firefox 3.0.10 right now with no problems.

:-\" Maybe you need to update your system.

---

### Post by nm4m on 2009-05-05
Thanks for the reply.  No it has been updated, rebooted, uninstalled, reinstalled purged.  If I click on the frame I get menus in locations I wouldn't expect.  None of the fixes that I have found documented so far, has made a difference.

Dave
NM4M

---

### Post by codeseer on 2009-05-05
> **nm4m said:**
> Thanks for the reply.  No it has been updated, rebooted, uninstalled, reinstalled purged.  If I click on the frame I get menus in locations I wouldn't expect.  None of the fixes that I have found documented so far, has made a difference.

Dave
NM4M

Can you get to the extensions window? If so, try disabling the Ubuntu Firefox Modifications.

I'll get back to you on instructions for manually doing it.

---

### Post by codeseer on 2009-05-05
Manually removing the Ubuntu Firefox Modifications from a Firefox profile:

[LIST=1]
[*]Go to ~/.mozilla/firefox/<YourProfileName>/.
[*]Open extensions.rdf in a text editor.
[*]Find and remove the entry for Ubuntu Firefox Modifications, using backspace to eliminate any remaining whitespace. You want to get everything, including the tags, between the <RDF:Description></RDF:Description> tags.
[/LIST]

The block to remove should look like this:

```

<RDF:Description RDF:about="rdf:#$SBU6c1"
                   NS1:id="{ec8030f7-c20a-464f-9b0e-13a3a9e97384}"
                   NS1:minVersion="3.0"
                   NS1:maxVersion="3.0.*" />
  <RDF:Description RDF:about="urn:mozilla:item:ubufox@ubuntu.com"
                   NS1:installLocation="app-global"
                   NS1:version="0.6"
                   NS1:iconURL="chrome://ubufox/content/ubuntulogo32.png"
                   NS1:name="Ubuntu Firefox Modifications"
                   NS1:description="Ubuntu configuration defaults and apt support for firefox extensions/plugins."
                   NS1:creator="Canonical Ltd.">
    <NS1:type NC:parseType="Integer">2</NS1:type>
    <NS1:contributor>Alexander Sack &lt;asac@ubuntu.com&gt;</NS1:contributor>
    <NS1:contributor>Sasa Bodiroza &lt;jazzva@gmail.com&gt;</NS1:contributor>
    <NS1:contributor>Daniel Abramov &lt;ex@vingrad.ru&gt;</NS1:contributor>
    <NS1:contributor>Arzhel Younsi &lt;xionox@gmail.com&gt;</NS1:contributor>
    <NS1:contributor>Saïvann Carignan &lt;oxmosys@gmail.com&gt;</NS1:contributor>
    <NS1:targetApplication RDF:resource="rdf:#$7CU6c1"/>
  </RDF:Description>

```

I believe that it can be removed from the system by removing 'firefox-3.0-branding' and 'ubufox'.

---

### Post by nm4m on 2009-05-05
No, even when I open it in safe mode things don't display.  I can work my way to the add-on window, but it too is blank.  If I post this screen shot correctly, maybe this will give folks an idea.

In the shot, I have clicked on the left side of the screen, and thus have the file menu open.  This occurs when clicking anywhere on the left side of the screen.  It is like the menu header for the window, takes up the whole window.  Any subsequent windows (such as the add-on window, also come up blank.

Dave 
NM4M

---

### Post by codeseer on 2009-05-05
Wow. That's like non-existent.

Have you tried setting up a local install and seeing if it still occurs?

Have you tried a different user account?

Have you tried running it under 'sudo'?

What's the output of this:

```

ls -al /usr/bin/fire*

ls -al /usr/lib/firefox-3.0.10/fire*

```

---

### Post by nm4m on 2009-05-05
Thanks for the info, good stuff.

It should be noted that I have wiped out the ./mozilla directory at times.  I have a backup in another location.

Here is the file.  I could not find Ubuntu Firefox Modifications in the file.

Dave
NM4M

```
<?xml version="1.0"?>
<RDF:RDF xmlns:NS1="http://www.mozilla.org/2004/em-rdf#"
         xmlns:NC="http://home.netscape.com/NC-rdf#"
         xmlns:RDF="http://www.w3.org/1999/02/22-rdf-syntax-ns#">
  <RDF:Description RDF:about="rdf:#$+hYIR3"
                   NS1:id="{ec8030f7-c20a-464f-9b0e-13a3a9e97384}"
                   NS1:minVersion="3.0.10"
                   NS1:maxVersion="3.0.10" />
  <RDF:Seq RDF:about="urn:mozilla:item:root">
    <RDF:li RDF:resource="urn:mozilla:item:{972ce4c6-7e08-4474-a285-3208198ce6fd}"/>
    <RDF:li RDF:resource="urn:mozilla:item:langpack-en-GB@firefox-3.0.ubuntu.com"/>
    <RDF:li RDF:resource="urn:mozilla:item:langpack-en-GB@xulrunner-1.9.ubuntu.com"/>
  </RDF:Seq>
  <RDF:Description RDF:about="urn:mozilla:item:langpack-en-GB@firefox-3.0.ubuntu.com"
                   NS1:installLocation="app-global"
                   NS1:version="3.0.7"
                   NS1:name="Firefox (en-GB)"
                   NS1:creator="http://translations.launchpad.net">
    <NS1:type NC:parseType="Integer">8</NS1:type>
    <NS1:targetApplication RDF:resource="rdf:#$MhYIR3"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mozilla:item:langpack-en-GB@xulrunner-1.9.ubuntu.com"
                   NS1:installLocation="gre-global"
                   NS1:version="1.9.0.8"
                   NS1:name="Xulrunner (en-GB)"
                   NS1:creator="http://translations.launchpad.net">
    <NS1:type NC:parseType="Integer">8</NS1:type>
    <NS1:targetApplication RDF:resource="rdf:#$6iYIR3"/>
  </RDF:Description>
  <RDF:Description RDF:about="rdf:#$MhYIR3"
                   NS1:id="{ec8030f7-c20a-464f-9b0e-13a3a9e97384}"
                   NS1:minVersion="3.0"
                   NS1:maxVersion="3.0.*" />
  <RDF:Description RDF:about="urn:mozilla:item:{972ce4c6-7e08-4474-a285-3208198ce6fd}"
                   NS1:installLocation="gre-global"
                   NS1:version="3.0.10"
                   NS1:internalName="classic/1.0"
                   NS1:locked="true"
                   NS1:appManaged="true"
                   NS1:name="Default"
                   NS1:description="The default theme."
                   NS1:creator="Mozilla"
                   NS1:contributor="Mozilla Contributors">
    <NS1:type NC:parseType="Integer">4</NS1:type>
    <NS1:targetApplication RDF:resource="rdf:#$+hYIR3"/>
  </RDF:Description>
  <RDF:Description RDF:about="rdf:#$6iYIR3"
                   NS1:id="toolkit@mozilla.org"
                   NS1:minVersion="1.9"
                   NS1:maxVersion="1.9.0.*" />
</RDF:RDF>
```

---

### Post by nm4m on 2009-05-05
> **codeseer said:**
> Wow. That's like non-existent.

Have you tried setting up a local install and seeing if it still occurs?

Have you tried a different user account?

Have you tried running it under 'sudo'?

What's the output of this:

```

ls -al /usr/bin/fire*

ls -al /usr/lib/firefox-3.0.10/fire*

```

I have not yet tried the local install.  I was hoping to stay within Ubuntu's structure so updates went well.  But I have downloaded and un-tarred a firefox load.  I just need to look up the directions on how to install it.

Same response under another account.

Same response opening firefox from a terminal using sudo

I have un-installed and re-installed so much from apt that the below may be butchered.  But the response from Firefox all along has been the same.

```
david@gimli:~$ ls -al /usr/bin/fire*
lrwxrwxrwx 1 root root 11 2009-05-02 21:27 /usr/bin/firefox -> firefox-3.0
lrwxrwxrwx 1 root root 32 2009-05-02 21:27 /usr/bin/firefox-3.0 -> ../lib/firefox-3.0.10/firefox.sh
lrwxrwxrwx 1 root root 34 2009-05-02 16:01 /usr/bin/firefox-3.5 -> ../lib/firefox-3.5b4pre/firefox.sh
david@gimli:~$ ls -al /usr/lib/firefox-3.0.10/fire*
-rwxr-xr-x 1 root root 39376 2009-04-25 19:42 /usr/lib/firefox-3.0.10/firefox
lrwxrwxrwx 1 root root     7 2009-05-02 21:27 /usr/lib/firefox-3.0.10/firefox-3.0 -> firefox
-rw-r--r-- 1 root root   456 2009-04-25 19:41 /usr/lib/firefox-3.0.10/firefox-3.0-restart-required.update-notifier
-rwxr-xr-x 1 root root  4006 2009-04-25 19:41 /usr/lib/firefox-3.0.10/firefox.sh
david@gimli:~$ 

```

I appreciate the help.  Been tinkering and using Linux for a long time and not seen this one before.  

Dave 
NM4M

---

### Post by codeseer on 2009-05-05
That is quite strange. You aren't having any issues from any other programs? Do you have an AppArmor profile for Firefox?

---

### Post by nm4m on 2009-05-05
I have never used AppArmor.  I backed up my directory, and wiped out .mozilla and I have been letting each successive install of firefox do there on thing.  Whenever I have done an sudo apt-get purge firefox(I think it was 3.0) I also wiped out the directory .mozilla.

The only extensions I had used before was forecast fox, download them all, and adblock.

Dave 
NM4M

---

### Post by codeseer on 2009-05-05
I saw you installed the beta at one point. I have had a few people get things messed up by doing that, but it was mainly just permissions and linking related. Your permissions and linking looks good.

Have you added another repository for Firefox to the sources list?

---

### Post by nm4m on 2009-05-05
Sources list

```
david@gimli:~$ sudo cat /etc/apt/sources.list
[sudo] password for david: 
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

deb http://archive.ubuntu.com/ubuntu jaunty universe multiverse
deb-src http://archive.ubuntu.com/ubuntu jaunty universe multiverse
david@gimli:~$ 

```

Dave
NM4M

---

### Post by nm4m on 2009-05-05
I know I had more sources prior to the upgrade (ubuntu media, and one for adobe flash or such, and not sure what else) but the upgrade said it was updating the sources list.

Dave
NM4M

---

### Post by nm4m on 2009-05-05
Yes, interestingly enough the beta runs fine.  Should I just move on to that and forget about 3.0.10?  I was just trying to stay with the flow of what Ubuntu is doing.  Do not want to cause down stream update issues.

Dave
NM4M

---

### Post by nm4m on 2009-05-05
Just noticed, that in the beta, all though websites view fine, if I try to work with importing bookmarks or opening a local file, then I can not view any of the files in the dialog window.  I can view the directories on the left side, but the right side is a pinkish square, much like I get with 3.0.10.

Starting to wonder if it is related to gnome.

Dave
NM4M

---

### Post by codeseer on 2009-05-05
Maybe you could try uninstalling 3.0.10, removing .mozilla, then install 3.0.9 and upgrade to 3.0.10. You should be able to get the older version off the mozilla site.

If the beta works for you though, you may be better off just using that until another update comes out and see if it fixes the issue then.

---

### Post by codeseer on 2009-05-05
> **nm4m said:**
> Just noticed, that in the beta, all though websites view fine, if I try to work with importing bookmarks or opening a local file, then I can not view any of the files in the dialog window.  I can view the directories on the left side, but the right side is a pinkish square, much like I get with 3.0.10.

Starting to wonder if it is related to gnome.

Dave
NM4M

Yeah, I was wondering that, but I figured since you're not having any problems with anything else... Could be a gconf issue, but that usually gives errors.

---

### Post by nm4m on 2009-05-05
> **codeseer said:**
> Maybe you could try uninstalling 3.0.10, removing .mozilla, then install 3.0.9 and upgrade to 3.0.10. You should be able to get the older version off the mozilla site.

If the beta works for you though, you may be better off just using that until another update comes out and see if it fixes the issue then.

To do this I would do the following?
sudo apt-get purge firefox-3.0 
rm -rf .mozilla
sudo apt-get install firefox 3.0.9 <<how do I tell it to install 3.0.9??>>

This is the part I have had problems with.  

Dave
NM4M

---

### Post by codeseer on 2009-05-05
> **nm4m said:**
> To do this I would do the following?
sudo apt-get purge firefox-3.0 
rm -rf .mozilla
sudo apt-get install firefox 3.0.9 <<how do I tell it to install 3.0.9??>>

This is the part I have had problems with.  

Dave
NM4M

What would be easier as a final attempt, from looking at it on my VirtualBox, would be to remove firefox by removing the following packages:

[LIST=1]
[*]firefox
[*]ubufox
[*]firefox-3.0
[*]firefox-3.0-branding
[/LIST]

If you have any other firefox packages, remove them also. In Synaptic, you can search 'firefox', then quick search 'firefox' to narrow the list down and then look for green squares. Rename the .mozilla folder as well.

After this, reload the repositories and install the 'firefox' package.

---

### Post by nm4m on 2009-05-05
I am uninstalling everything with synaptic.  When I look at items that come up with firefox, that have green boxes, one that wants to uninstall a lot of important things is xulrunner-1.9.  I can remove xulrunner-1.9.1 but not 1.9.  So I will have to leave that one.  Will let you know what I find out.  Thanks.

Dave
NM4M

---

### Post by stchman on 2009-05-05
> **StuartN said:**
> I just accepted the update of Firefox from version 3.0.9 to 3.0.10 that came out today, and all I get when Firefox restarts is a blank window with no menus and no functionality. I completely purged all traces of Firefox and re-installed, but it still doesn't function.

(I installed Epiphany-Gecko in the meantime).

Is anyone else affected by this?

Firefox 3.0.10 works perfectly on all (5) of my machines.

---

### Post by nm4m on 2009-05-05
No joy.  No change.  I removed everything except xulrunner, which would have taken gnome with it.

Screen shots and log below.

Dave
NM4M

```
(Reading database ... 124407 files and directories currently installed.)
Removing firefox ...
(Reading database ... 124404 files and directories currently installed.)
Removing firefox-3.0-gnome-support ...
(Reading database ... 124400 files and directories currently installed.)
Removing firefox-3.0 ...
Purging configuration files for firefox-3.0 ...
(Reading database ... 124310 files and directories currently installed.)
Removing firefox-3.0-branding ...
(Reading database ... 124289 files and directories currently installed.)
Removing firefox-3.5 ...
Purging configuration files for firefox-3.5 ...
(Reading database ... 124210 files and directories currently installed.)
Removing firefox-3.5-branding ...
Removing flashplugin-nonfree ...
(Reading database ... 124186 files and directories currently installed.)
Removing flashplugin-installer ...
Purging configuration files for flashplugin-installer ...
Removing mozilla-plugin-vlc ...
dpkg - warning: while removing mozilla-plugin-vlc, directory `/usr/lib/mozilla-firefox/plugins' not empty so not removed.
dpkg - warning: while removing mozilla-plugin-vlc, directory `/usr/lib/mozilla-firefox' not empty so not removed.
Removing totem-mozilla ...


david@gimli:~$ rm -rf .mozilla/
rm: cannot remove `.mozilla/firefox/2plhencm.default/Cache/_CACHE_001_': Permission denied
rm: cannot remove `.mozilla/firefox/2plhencm.default/Cache/_CACHE_002_': Permission denied
rm: cannot remove `.mozilla/firefox/2plhencm.default/Cache/A89F4DBCd01': Permission denied
rm: cannot remove `.mozilla/firefox/2plhencm.default/Cache/_CACHE_MAP_': Permission denied
rm: cannot remove `.mozilla/firefox/2plhencm.default/Cache/9808D2F4d01': Permission denied
rm: cannot remove `.mozilla/firefox/2plhencm.default/Cache/_CACHE_003_': Permission denied
david@gimli:~$ sudo rm -rf .mozilla/
[sudo] password for david: 
david@gimli:~$ ls -a .mozilla
ls: cannot access .mozilla: No such file or directory
david@gimli:~$ 


david@gimli:~$ sudo apt-get update
Hit http://packages.medibuntu.org jaunty Release.gpg
Ign http://packages.medibuntu.org jaunty/free Translation-en_US                           
Hit http://us.archive.ubuntu.com jaunty Release.gpg                                       
Hit http://archive.ubuntu.com jaunty Release.gpg                                           
Ign http://archive.ubuntu.com jaunty/universe Translation-en_US                            
Hit http://security.ubuntu.com jaunty-security Release.gpg                                 
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US                      
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US                
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US                        
Hit http://packages.medibuntu.org jaunty Release                                           
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_US                          
Hit http://archive.ubuntu.com jaunty Release                                              
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US                 
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US               
Hit http://security.ubuntu.com jaunty-security Release                                    
Hit http://packages.medibuntu.org jaunty/free Packages                                    
Hit http://archive.ubuntu.com jaunty/universe Packages               
Hit http://security.ubuntu.com jaunty-security/main Packages         
Hit http://packages.medibuntu.org jaunty/non-free Packages           
Hit http://archive.ubuntu.com jaunty/multiverse Packages             
Hit http://archive.ubuntu.com jaunty/universe Sources                
Hit http://archive.ubuntu.com jaunty/multiverse Sources              
Hit http://security.ubuntu.com jaunty-security/restricted Packages   
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty Release
Hit http://us.archive.ubuntu.com jaunty-updates Release
Hit http://us.archive.ubuntu.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Reading package lists... Done
david@gimli:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
david@gimli:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xulrunner-1.9.1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox-3.0 firefox-3.0-branding
Suggested packages:
  ubufox firefox-3.0-gnome-support latex-xft-fonts
The following NEW packages will be installed:
  firefox firefox-3.0 firefox-3.0-branding
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1176kB of archives.
After this operation, 4080kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package firefox-3.0-branding.
(Reading database ... 124151 files and directories currently installed.)
Unpacking firefox-3.0-branding (from .../firefox-3.0-branding_3.0.10+nobinonly-0ubuntu0.9.04.1_amd64.deb) ...
Selecting previously deselected package firefox-3.0.
Unpacking firefox-3.0 (from .../firefox-3.0_3.0.10+nobinonly-0ubuntu0.9.04.1_amd64.deb) ...
Selecting previously deselected package firefox.
Unpacking firefox (from .../firefox_3.0.10+nobinonly-0ubuntu0.9.04.1_all.deb) ...
Setting up firefox-3.0-branding (3.0.10+nobinonly-0ubuntu0.9.04.1) ...
Setting up firefox-3.0 (3.0.10+nobinonly-0ubuntu0.9.04.1) ...
Please restart all running instances of firefox-3.0, or you will experience problems.

Setting up firefox (3.0.10+nobinonly-0ubuntu0.9.04.1) ...
david@gimli:~$ 

Get the Import Wizard window, Import Settigns and Data - blank
Clicked on the left side of it, and the window disappeared, replaced by an empty firefox window, titleded, "404:File Not Found - Mozilla Firefox
Close this window and a full window opens asking, "Do you want Firefox to save your tabs for the next time it starts?"
Typed Q to quit, had to peek at another box to figure out what I needed to hit.
```

---

### Post by codeseer on 2009-05-05
I'd just use the beta or a local install for now.

---

### Post by nm4m on 2009-05-05
Ok, thanks for the support.  I'll dig up some install instructions.

Dave 
NM4M

---

### Post by nm4m on 2009-05-05
I can't catch a break, but it has been one of those years.....

Leaving a follow-up, as it seems others are experiencing some of these problems.

Installed firefox via this page;
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

A very well done page.  Install worked well.  Problem is the loose nut behind the keyboard did not try it out before installing flash.  More notes on those issues below.

Now firefox opens, can see the screen (meaning it fixed the most obvious problem I had before), but it does not connect to the Internet.  It does not see any domains.  It opens local pages fine.

Installed flash based on a link found in the Ubuntu forums;
[http://sneerwell.blogspot.com/2009/05/install-64-bit-flash-player-plugin-for.html]("http://sneerwell.blogspot.com/2009/05/install-64-bit-flash-player-plugin-for.html")

When I opened it in a terminal, received the following;
```
david@gimli:~$ firefox
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
LoadPlugin: failed to initialize shared library /home/david/.mozilla/plugins/libflashplayer.so [/home/david/.mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so [/usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so: wrong ELF class: ELFCLASS64]

```

Which leads to a bunch of the error messages noted above and here;
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/369123]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/369123")

This is why I hate to wander far from the apt-get path.  I often seem to run into problems, and broken software, with no simple way of untangling the mess. 

Time for a backup, install 9.04 32bit, see if that is less headaches, if not, then back to 8.10.

Good day, and thanks again for all the help.

Dave 
NM4M

---

### Post by codeseer on 2009-05-06
The ELFCLASS64 is a common bug being observed with the ia32-libs; it's a recent occurrence, few weeks since the last update, and you can try downgrading the ia32-libs to fix it. I think you may have just discovered what the real issue is with that bug. It would seem that those using non-repository 32-bit applications on Ubuntu 64-bit Jaunty are getting those errors.

Here's the report I first encountered:

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/369498](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/369498)

---

### Post by nm4m on 2009-05-06
Yea, tired of fighting the 64 bit battle.  There was a time when I was younger, loved digging into this stuff, and I had to have the latest and greatest.  Now I just want it to work.

Last night downloaded new ISOs will get those burned at some point.  Had picked up a USB HD for backups and have been moving files around.  Today I notice that file browser windows periodically open for these drives for no particular reason.  May be because I had the windows open for the last few days moving things around, that I didn't notice it.  No big deal, just annoying when you don't expect it.

I'll roll back to 9.04/32 and give that a try.  I keep the /home on a separate drive so it is easier to install.  Last time it was a bit of a struggle as to add the /home I had to do complete manual partitioning.  In other distros I used in the past, you could auto partition one drive, then mount another as /home.  Hopefully this has gotten a bit simpler this go round.

Have a good day

Dave
NM4M

---

### Post by codeseer on 2009-05-06
I'm hanging with the 64-bit because I have 4 GB of RAM; but, I'm not sitting foot on Jaunty grounds until more is fixed.

---

### Post by Yellow Pasque on 2009-05-06
nm4m, you installed a 32-bit firefox, which is why you got all the ELFCLASS errors.

---

### Post by codeseer on 2009-05-06
> **Temüjin said:**
> nm4m, you installed a 32-bit firefox, which is why you got all the ELFCLASS errors.

You mean the beta he installed?

---

### Post by nm4m on 2009-05-06
Ok.  If I grab the 64 bit do I go through the same install process as before and write over everything, or do I need to do some thing to remove what I just installed?  It wasn't dpkg or apt so I'm not completely sure how to remove everything.

Dave 
NM4M

---

### Post by nm4m on 2009-05-06
Ok, that wasn't as obvious as I thought it would be.  Instead I will figure out how to un-install the 64 bit flash.

Dave
NM4M

---

### Post by nm4m on 2009-05-06
I am finding tons of stuff on 64 bit flash and java, but nothing on 64 bit firefox.  So it must be something obvious I am overlooking.  Where do I get 64 bit firefox?  All my searches tell me about 32 bit firefox.  Even googling, install "64-bit" firefox ubuntu.  I all kinds of information about various plugins, but nothing about the actual 64 bit firefox.  That may have been part of my problem from the start.  How do you get a 64 bit copy of firefox?

Dave 
NM4M

---

### Post by codeseer on 2009-05-06
> **nm4m said:**
> Ok, that wasn't as obvious as I thought it would be.  Instead I will figure out how to un-install the 64 bit flash.

Dave
NM4M

```

sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

```

---

### Post by codeseer on 2009-05-06
> **nm4m said:**
> I am finding tons of stuff on 64 bit flash and java, but nothing on 64 bit firefox.  So it must be something obvious I am overlooking.  Where do I get 64 bit firefox?  All my searches tell me about 32 bit firefox.  Even googling, install "64-bit" firefox ubuntu.  I all kinds of information about various plugins, but nothing about the actual 64 bit firefox.  That may have been part of my problem from the start.  How do you get a 64 bit copy of firefox?

Dave 
NM4M

Firefox from the repository is 64-bit if you are running Ubuntu 64-bit. I think he was talking about the beta version you installed possibly being 32-bit and messing up the 64-bit install.

See (Firefox):Help->About Mozilla Firefox

---

### Post by nm4m on 2009-05-07
Performed the flash uninstall. Was still getting the same stuff with firefox.  Said heck with it and did a new install.  Didn't even try to get my home drive mounted.  Grub generated an error message, but otherwise all went well.  Firefox is working fine now (32-bit installation).

Now to get all the good stuff working again, and get that extra drive mounted so I can copy my email over.

Thanks again.

Dave 
NM4M

---

### Post by codeseer on 2009-05-07
Sorry it had to come to that; sometimes it does though. I'm having a rough time trying to track down an issue on my machine at the moment that may lead to that. I'm always glad to help out; if you need anything else, feel free to hit me up.

---

### Post by nm4m on 2009-05-07
Understand.  The grub issue turned out to be much bigger.  Didn't realize at the time that I was in live cd mode.  Just finished up my second re-install.  ;)

The second time around I did the partitioning manually and set me second drive as /home.  So far after initial install, Firefox works.  I had copied my .mozilla directory without the -R so it did not copy back as needed.  So will have to deal with that manually.

Now to see if the update kills firefox again.  And it works after the update.  Good news.  Now see how adding in all the pluggins and getting everything else working goes.  Take care and good luck with your issues.

Dave
NM4M

---

### Post by lucidmyth on 2009-05-17
Dear Ubuntu fans,

Unfortunately, today (after an update) I am hit with the exact same issue as nm4m.
Firefox gives me the blank screen, menu's don't work and often if the page loads at all you cannot click any buttons.

Running Firefox 3.0.10
Ubuntu 8.10 / x86_64 

I wish there was a button to undo the update...........

---

### Post by nm4m on 2009-05-17
I know what you mean.  Everything worked except Firefox.  The shocker for me was when the 3.5 beta worked.  You will also note, at times file system dialog boxes will come up blank too.  

Just out of curiosity, click on the left side of the window.  Make sure and have the window sized very small.  If menus come up it is the same thing.

A couple of questions;
Are you running 32 bit or 64 bit on the system before the upgrade?
What video card do you have?

Dave 
NM4M

---

