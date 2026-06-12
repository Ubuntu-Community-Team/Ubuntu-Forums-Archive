---
title: "Trying to upgrade Evolution ended in trouble!"
date: 2009-03-07
forum: General Help
---

### Post by drorata on 2009-03-07
Dear ubuntu fellows,

I was trying to immigrate from Thunderbird to Evolution, but realized that I need a newer version then the one installed in 8.04. So I followed these [instruction]("http://ubuntuforums.org/showpost.php?p=5802161&postcount=2"):
> 
1-Make a backup of your current sources.list
**sudo cp /etc/apt/sources.list /etc/apt/sources.backup**
2-Change your software sources from hardy to intrepid
**sudo sed -i 's/hardy/intrepid/g' /etc/apt/sources.list**
3-Update your package lists
**sudo apt-get update**
4-Install [the new] evolution (do not install any other software from Intrepid, seriously)
**sudo apt-get install evolution evolution-exchange evolution-plugins**
5-Restore your original sources.list file
**sudo cp /etc/apt/sources.backup /etc/apt/sources.list**
6-Update your package lists
**sudo apt-get update**
7-Check to see if problem persists (who knows it may have been evolution all along)


I managed to upgrade the Evolution, but many other things (seems like all are GNOME related) messed up.

I tried to undo the harm, by following:
```
sudo apt-get install evolution=2.22.3.1-0ubuntu1 evolution-exchange=2.22.3-0ubuntu2 evolution-plugins=2.22.3.1-0ubuntu1
```
as suggested by in the same post, and this was the result:

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
  evolution: Depends: evolution-common (= 2.22.3.1-0ubuntu1) but 2.24.3-0ubuntu1 is to be installed
             Depends: evolution-data-server (>= 2.21.92) but it is not going to be installed
E: Broken packages

```

At this point I realized that I'm in trouble.
These are the problems I spotted so far:
[LIST]
[*]After reboot I get the following message:
```
There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.
The Settings Daemon restarted too many times.
GNOME will still try to restart the Settings Daemon next time you log in.
```
[*]In order to have internet connection I have to restart the network manager and the networking
```
sudo /etc/dbus-1/event.d/25NetworkManager restart
```
```
sudo /etc/init.d/networking restart
```
[*]The "Screen Resolution" tool looks different now, and I don't have the option of "use previous settings" when I change display features.
[*]Speller in FireFox doesn't offer correction (just mark misspellings)
[*]After clicking the "Shut Down" and canceling it two icons of the "Power Manager" appears in the system try.
[/LIST]

These are the problems I found so far, I'm afraid many more are hidden somewhere.

*Please help me*... I really can't afford re-installing the whole system right now.

*PLEASE...*

---

### Post by dcstar on 2009-03-07
> **drorata said:**
> Dear ubuntu fellows,

I was trying to immigrate from Thunderbird to Evolution, but realized that I need a newer version then the one installed in 8.04. So I followed these [instruction]("http://ubuntuforums.org/showpost.php?p=5802161&postcount=2"):
........
*Please help me*... I really can't afford re-installing the whole system right now.

*PLEASE...*

Later versions of Evolution **CANNOT** be used in an earlier Ubuntu version because they have many dependencies that cannot be met (whoever provided those instructions should be shot - slowly!)

You will not find backported versions of Evolution for an Ubuntu release because it is generally too hard to achieve as they use features that are unavailable in the earlier Ubuntu.

You are right that your Gnome is now messed up, you have mixed in incompatible 8.10 packages into your 8.04 system.

---

