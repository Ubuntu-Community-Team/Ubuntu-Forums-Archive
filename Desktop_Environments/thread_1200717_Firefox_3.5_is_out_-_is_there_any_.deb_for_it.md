---
title: "Firefox 3.5 is out - is there any .deb for it?"
date: 2009-06-30
forum: Desktop Environments
---

### Post by udippel on 2009-06-30
[Uhh. Subject says all.]

---

### Post by cieplak32 on 2009-06-30
```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main 
deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
```

---

### Post by dentaku65 on 2009-06-30
> **cieplak32 said:**
> ```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main 
deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
```

No, it seems rc2 only in these repos...

---

### Post by udippel on 2009-06-30
Yes. Hmm. Not quite:

$ sudo apt-get update 
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages [7579B]
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources [2244B]
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ apt-cache show firefox-3.5
Package: firefox-3.5
Source: firefox-3.5
Priority: optional
Section: web
Installed-Size: 3600
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Architecture: amd64
Version: 3.5~rc2+nobinonly-0ubuntu2~umd1~jaunty

All this is not what I want.

Any better solution?

---

### Post by asmoore82 on 2009-06-30
```
sudo apt-get install firefox-3.5
```

---

### Post by xak on 2009-06-30
> **asmoore82 said:**
> ```
sudo apt-get install firefox-3.5
```

But that command will install the RC2 package:

> **udippel said:**
> 
Version: 3.5~**rc2**+nobinonly-0ubuntu2~umd1~jaunty


Where is the final!! :-k

---

### Post by torusturtle on 2009-06-30
> **dentaku65 said:**
> No, it seems rc2 only in these repos...

I guess you have to wait at least a day so that the maintainers can update the ppa.

---

### Post by EmEyKeYwAy on 2009-06-30
Same problem here.

---

### Post by traxxas on 2009-06-30
According to [asac]("http://www.asoftsite.org/s9y/"), one of the maintainers of the Daily PPA, we should see 3.5 builds soon.  I'm watching the Security PPA now while running rc2 from daily.

---

### Post by dentaku65 on 2009-06-30
> **traxxas said:**
> According to [asac]("http://www.asoftsite.org/s9y/"), one of the maintainers of the Daily PPA, we should see 3.5 builds soon.  I'm watching the Security PPA now while running rc2 from daily.

Good point Traxxas!

---

### Post by traxxas on 2009-06-30
[fta's PPA]("https://launchpad.net/~fta/+archive/ppa") has builds of 3.5 that just finished, I'm running them now.

---

### Post by jrolland on 2009-06-30
Thanks for all the responses. I have two questions.

1) I am using Intrepid. Will Firefox 3.5 be made available to Intrepid users "by default", that is, without adding any repositories?

2) If I use the mozilla-daily-build repository, will I constantly be nagged to update on a daily basis? I only want Firefox 3.5 and its official updates.

Thanks in advance for any assistance you can provide.

---

### Post by lovinglinux on 2009-06-30
For instructions on how to install Firefox 3.5 or upgrade the 3.0.11 version, check the [color=#CC0000]**Firefox Alternatives & Newer Versions**[/color] section of the [**[color=#CC0000]Firefox optimization and troubleshooting thread[/color]**](http://ubuntuforums.org/showthread.php?t=1193567).

For a list of other threads talking about the same subject, visit [http://ubuntuforums.org/showthread.php?t=1200781](http://ubuntuforums.org/showthread.php?t=1200781)

---

### Post by QCompson on 2009-06-30
> **traxxas said:**
> [fta's PPA]("https://launchpad.net/~fta/+archive/ppa") has builds of 3.5 that just finished, I'm running them now.

Thanks, that worked for me.

IMO Mozilla should just provide an ubuntu deb for the new version until it gets updated in the repos.  People want to try it as soon as it's released; adding sources and dealing with frustrating pubkey issues is always annoying.

---

### Post by udippel on 2009-07-01
> **QCompson said:**
> 
IMO Mozilla should just provide an ubuntu deb for the new version until it gets updated in the repos.  People want to try it as soon as it's released; adding sources and dealing with frustrating pubkey issues is always annoying.

Seconded.

And to lovinglinux: Yes, I also kind of love Linux! But two links, one making fun about the number of links, and one with a thousand lines and dozens of topics and links, from where one moves to other links, uses the command line, and adds this here and there, and edits yet another file: No, that's not much of a help. 

Plus, now we have Firefox 3.5 under different repositories, and even me, though loving Linux, would rather have an 'official' version, instead of pondering how many different versions we have available!

Yes, I'd wish Mozilla offered a .deb, and then dpkg - i Firefox-3.5 would solve a good part of the problems. 
Even easier (and this is my suggestion to Launchpad): When I add a new repository, maybe specific to Firefox 3.5, the next update/upgrade will upgrade to the newer version.
You may call this a 'tag' then. One adds a repository, 'update', and the latest version is bumped to the one in that repository.

Over.

---

### Post by lovinglinux on 2009-07-01
> **udippel said:**
> Seconded.

And to lovinglinux: Yes, I also kind of love Linux! But two links, one making fun about the number of links, and one with a thousand lines and dozens of topics and links, from where one moves to other links, uses the command line, and adds this here and there, and edits yet another file: No, that's not much of a help. 

Plus, now we have Firefox 3.5 under different repositories, and even me, though loving Linux, would rather have an 'official' version, instead of pondering how many different versions we have available!

Yes, I'd wish Mozilla offered a .deb, and then dpkg - i Firefox-3.5 would solve a good part of the problems. 
Even easier (and this is my suggestion to Launchpad): When I add a new repository, maybe specific to Firefox 3.5, the next update/upgrade will upgrade to the newer version.
You may call this a 'tag' then. One adds a repository, 'update', and the latest version is bumped to the one in that repository.

Over.

I have changed the tutorial, recommending only [Ubuntuzilla](http://ubuntuforums.org/showthread.php?t=1193567). It's not complicated and works like a charm. The script is installed via deb file, then all you have to do is run a command and answer some questions. It will download the Firefox deb from Mozilla site, install it in ~/opt/firefox  and make the necessary changes, including backing up your profiles. It also easy to remove it. I've done it and installed twice just for testing. It works great.

If you have time to read my tutorial, you find very useful information. There are several topics because I'm trying to organize information about common issues regarding Firefox, that are posted regularly on the forums.

I'm sorry if you find it too long, but that was the best I could do.

---

### Post by Lety on 2009-07-01
Today I've done a clean install from [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) 
with ```
sudo apt-get install firefox-3.5
```
The build is Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1) Gecko/20090630 Ubuntu/9.04 (jaunty) Shiretoko/3.5.
Is this a final one?
As the name of the main window is Shiretoko :)
How can I rename to 'Firefox' ?
What is suprising: I deleted Firefox 3 profile and then uninstalled FF 3.0 with --purge .
Freshly installed FF 3.5 started with a clean profile, but the Fast Dial plugin, which has been just installed took my old Fast Dial links from somewhere ;)

---

### Post by jlacroix on 2009-07-01
I tried to install the firefox-3.5 package on my Kubuntu box from the repos and it wants to install a bunch of Gnome crap. The Firefox 3.0 package doesn't do that. I don't want any Gnome BS on my machine. Any way around that? It wants to install things like Synaptic, Gnome App Install, and a bunch of others. I just want the browser.

---

### Post by udippel on 2009-07-03
I have the same here: Shiretoko, and no idea which version it actually is.
And it installed another two packages, one of them pretty large (forgot the name).

So in the end, after some rather arrogant pondering in this thread and elsewhere, there is no answer after all?

---

### Post by Justin Trouble on 2009-07-03
> **jlacroix said:**
> I tried to install the firefox-3.5 package on my Kubuntu box from the repos and it wants to install a bunch of Gnome crap. The Firefox 3.0 package doesn't do that. I don't want any Gnome BS on my machine. Any way around that? It wants to install things like Synaptic, Gnome App Install, and a bunch of others. I just want the browser.

It's because Firefox has a recommend for Ubufox, which in turn requires a load of GNOME stuff.

Install on the command line with:
```
sudo apt-get--no-install-recommends install firefox-3.5
```

---

### Post by utkjamie on 2009-07-03
> **udippel said:**
> I have the same here: Shiretoko, and no idea which version it actually is.
And it installed another two packages, one of them pretty large (forgot the name).

So in the end, after some rather arrogant pondering in this thread and elsewhere, there is no answer after all?

Same question. I'm running 3.5 and it's showing up as Shiretoko. Some web sites tell me that my browser is not supported and that I should try using Internet Explorer or Firefox. Hrm.

---

### Post by picopir8 on 2009-07-03
Installing the useragent switcher pluging for firefox should allow you to have it actually report "firefox" or ie or whatever you want it to report to websites.

---

### Post by Sukotto on 2009-07-04
I just downloaded Firefox 3.5 extracted it placed it in my apps folder the created a launcher for it. the old version is still on my computer but I just user the launcher icon to the 3.5 I dl. Thats what worked for me 'till 3.5 final it the repositories.

---

### Post by jlacroix on 2009-07-04
> **Justin Trouble said:**
> It's because Firefox has a recommend for Ubufox, which in turn requires a load of GNOME stuff.

Install on the command line with:
```
sudo apt-get--no-install-recommends install firefox-3.5
```

Thank you, I will try that the next time I have to install it. I just find it strange that when I install Firefox 3.0 on Kubuntu it doesn't automatically install all of the other things.

---

### Post by JoeNZ on 2009-07-05
Ubuntuzilla is the answer. Very easy to use. Follow the instructions and you'll be sweet as.
I tried all the tips that people gave in the forums to no avail. That was until I came across Ubuntuzilla.
Good luck.

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by jlacroix on 2009-07-06
I just received updates today for Firefox, and it still says "Shiretoko" while I'm running it, so I don't think it's the final version yet. Also, links in email messages in Thunderbird don't automatically open Firefox. Any ideas?

---

### Post by lovinglinux on 2009-07-06
> **jlacroix said:**
> I just received updates today for Firefox, and it still says "Shiretoko" while I'm running it, so I don't think it's the final version yet. Also, links in email messages in Thunderbird don't automatically open Firefox. Any ideas?

It's the final version, I just installed to check it, although it won't be branded Firefox, because is not the official Firefox package. Which means Firefox 3.0.11 probably won't be updated to 3.5 in Jaunty, but you still can run this version using the Shiretoko brand.

If you don't like the Shiretoko name then uninstall it and and install the official Firefox 3.5 from Mozilla.

The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT). I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

Uninstall Shiretoko from terminal [see footnote] or synaptic:

```
sudo apt-get remove firefox-3.5
```

Then follow the method 1 of that tutorial and you will have the original Firefox 3.5 in no time.

Keep in mind that Shiretoko stores user profiles in the folder ~/.mozilla/firefox-3.5 instead of ~/.mozilla/firefox, so you might want to copy the profile from Shiretoko if you did important changes to it while using Shiretoko.

---

### Post by Justin Trouble on 2009-07-06
> **jlacroix said:**
> I just received updates today for Firefox, and it still says "Shiretoko" while I'm running it, so I don't think it's the final version yet. Also, links in email messages in Thunderbird don't automatically open Firefox. Any ideas?

It is the final version, but it will never receive the official Firefox branding.
See my post here: [http://ubuntuforums.org/showpost.php?p=7564802&postcount=81](http://ubuntuforums.org/showpost.php?p=7564802&postcount=81)

---

### Post by jlacroix on 2009-07-06
Thanks. I tried the Ubuntuzilla package, and while it worked, it gave me an extremely ugly looking Firefox. My KDE theme wouldn't shine through, and instead all the widgets look like old Windows 98. This is strange because the way that Kubuntu is set up is to make it look like the rest of the OS...

---

### Post by KWhistle on 2009-07-12
Tried installing it from synaptic, but nothing really worked... I'd either get the beta version, or the daily build, not the stable 3.5.  Eventually found the following instructions that worked for me.  Ridiculously cumbersome, I know, but it worked:

1. Download the tar file from Firefox.com web site.

2. Extract to /home/username/.mozilla/firefox .  I did owerwrite on everything, so that 3.0 doesn't pop up all of the sudden.

3. Open terminal and enter these commands (this to maintain the shortcuts):
cd /usr/bin

sudo  ln -s /home/username/.mozilla/firefox/firefox

---

### Post by lovinglinux on 2009-07-12
> **KWhistle said:**
> Tried installing it from synaptic, but nothing really worked... I'd either get the beta version, or the daily build, not the stable 3.5.  Eventually found the following instructions that worked for me.  Ridiculously cumbersome, I know, but it worked:

1. Download the tar file from Firefox.com web site.

2. Extract to /home/username/.mozilla/firefox .  I did owerwrite on everything, so that 3.0 doesn't pop up all of the sudden.

3. Open terminal and enter these commands (this to maintain the shortcuts):
cd /usr/bin

sudo  ln -s /home/username/.mozilla/firefox/firefox

IMO, that's is not a good idea. You are mixing the installation files with the profile folders, since ~/.mozilla/firefox is the folder where firefox stores profiles.

Follow method #1 from the "Install Other Version" section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). It will save Firefox binaries in /opt/firefox and create the necessary links, without messing with the profile folder.

---

### Post by deepclutch on 2009-07-18
As of Now ,Only Swiftfox .deb is available to be the latest.but ,java/flash plugins you have to resolve.
[http://getswiftfox.com/deb.htm](http://getswiftfox.com/deb.htm)
[http://www.fishbowl42.com/archive/debian/](http://www.fishbowl42.com/archive/debian/)

---

