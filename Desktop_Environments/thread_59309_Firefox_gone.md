---
title: "Firefox gone"
date: 2005-08-23
forum: Desktop Environments
---

### Post by pekko on 2005-08-23
I installed Ubuntu 5.04 on Saturday. Everything went well until yesterday. I installed more programs according the instructions in ubuntuguide.org. After that I installed all updates Synaptic had found. During update I got an error regarding firefox-gnome-support. After reboot Synaptic indicated that firefox-gnome-support was broken, I re-installed it and thought everything was fine.

Then the problems with Firefox began. Firefox started and everything looked normal until the first click. I found out that anything but opening a new window would stall Firefox. If I opened new window, I could use that window without problems.

I tried to remove and re-install Firefox and that seemed to help but the problem came back soon. Today I gave it another shot and removed Firefox again. When trying to re-install I couldn't find firefox from Synaptic's list anymore. I also tried to install Firefox from console, no success.

```
pekko@musta:~$ sudo apt-get install firefox
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
pekko@musta:~$
pekko@musta:~$
```

I have no idea what's wrong, help anybody?

---

### Post by KingBahamut on 2005-08-23
Sure you dont have Synaptic open in another workspace somewhere or minimized?

---

### Post by pekko on 2005-08-23
Actually, yes I did.

Now I get a different error:
```

pekko@musta:~$ sudo apt-get install firefox
Password:
Reading package lists... Done
Building dependency tree... Done
Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package firefox has no installation candidate
pekko@musta:~$
```

I have added all extra repositories recommended in ubuntuguide.org.

I'm pretty sure something went wrong during synaptic update. Wish I had saved the output and the error message.

---

### Post by KingBahamut on 2005-08-23
apt-get remove mozilla-firefox
apt-get install mozilla-firefox

---

### Post by pekko on 2005-08-23
No luck:

```
pekko@musta:~$ sudo apt-get remove mozilla-firefox
Reading package lists... Done
Building dependency tree... Done
Package mozilla-firefox is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
pekko@musta:~$ sudo apt-get install mozilla-firefox
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-firefox: Depends: firefox but it is not installable
E: Broken packages
pekko@musta:~$
```

---

### Post by pekko on 2005-08-23
I already managed to hang Mozilla Browser also, but at least I found the reason. Mozilla and Firefox seem not to like my ISP's home page. Url is [http://www.welho.com](http://www.welho.com) if someone is interested. Homepage recognises Welho customers and uses different homepage for them, so I'm not sure if it's possible to recreate the problem if you are not a Welho customer. I'll mail their tech support in order to solve the problem.

Bad news is that I still can't re-install Firefox. Is anybody else having this problem or is this inside my box only?

---

### Post by bwana on 2005-08-25
Same for me. Have used firefox for six months - keeping it updated with synaptic. After strange firefox crashes I tried to revert to a previous version. It didnt work. I dont know what happened but when now try to attempt to re-install firefox I get into exactly the same situation as you.
Did firefox dissapear from the repositories all of a sudden? what is going on here?

---

### Post by Isulgar on 2005-08-25
I had the same problem as you guys but now it seems fixed. I did a "sudo apt-get install mozilla-firefox" and it was downloaded and installed perfectly.

Once again a happy firefox user.   \\:D/

---

