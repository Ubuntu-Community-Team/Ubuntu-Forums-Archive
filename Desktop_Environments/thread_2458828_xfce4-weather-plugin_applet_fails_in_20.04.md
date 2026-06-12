---
title: "xfce4-weather-plugin applet fails in 20.04"
date: 2021-03-04
forum: Desktop Environments
---

### Post by ajgreeny on 2021-03-04
I use the xfce4-weather-plugin applet and have done so for many years.

It has suddenly stopped working in 20.04 and is impossible to set the location in the usual way with a right-click and using Properties from the context menu.

I have tried installing the version from Xubuntu 21.04 (0.11.0-1) but that fails with a dependency problem due to the version of libgdk-pixbuf available in 20.04.
Following a thread in the LinuxMint forum [https://forums.linuxmint.com/viewtopic.php?f=57&t=344110](https://forums.linuxmint.com/viewtopic.php?f=57&t=344110) about using the libweather.so from MX-Linux I tried the version of the plugin direct from MX-Linux and it installed with no problem.
No doubt this will be sorted out soon as it was when I last suffered in this way back in 2016 but I wonder if anyone else has seen this problem and found other ways of solving it without using the MX version.
I have also just downloaded the plugin version 0.10.2.1 from the PPA at [https://launchpad.net/~wasta-linux/+archive/ubuntu/xfce-4-16/+packages](https://launchpad.net/~wasta-linux/+archive/ubuntu/xfce-4-16/+packages) to see if that will install.  I didn't hold out much as it is from Xfce-4.16 but it installed fine and appears to be working fine.


Watch this space!

EDIT.
I have just restored the repository version but then downloaded the version from the PPA for xfce-4.16 at [https://launchpad.net/~bluesabre/+archive/ubuntu/xfce-4.16/+packages](https://launchpad.net/~bluesabre/+archive/ubuntu/xfce-4.16/+packages).
I extracted the libweather.so from the package of that PPA version and replaced the installed version with this 4.16 version.

All is working well at present.

---

### Post by him610 on 2021-03-04
@ajgreeny
I had never used xfce4-weather-plugin applet, but in reading your post, I added it to my panel. I was able to set the location, but the panel indicator shows, "No Data" Was that the same symptom that yours was showing before your fixit?

---

### Post by T6&amp;sfpER35% on 2021-03-04
yea my weather thingy also stopped working last nigth. 
didn't have time to look into it yet , but now i'm glad i stumbled onto this thread lol
will try your fixes once i'm home again.
thanks!

ps. wondering why it suddenly stopped working? could some update broken it? i mean this isn't windows ...=P~

---

### Post by ActionParsnip on 2021-03-05
Sounds like a bug to me. If you report one with your fix it may help the guys resolve the issue. Great share too. Hopefully it'll help others

---

### Post by ajgreeny on 2021-03-05
The problem relates to the API of the applet apparently, but I'm the wrong person to ask about what that really means other than the failure of the applet.

It looks as if there are several  work arounds for this which I've mentioned in my post and I expect it to be solved fully fairly quickly but its still annoying.

@ him610
Yes, that is the exact problem.

---

### Post by Holger_Gehrke on 2021-03-05
> **ajgreeny said:**
> The problem relates to the API of the applet apparently, but I'm the wrong person to ask about what that really means other than the failure of the applet.


Not the API of the plugin but that of the web-service (met.no) it uses to get the data. The new version went online sometime last summer but there was a grace period in which both the old and the new version of the service were available. Seems like that has ended. New versions of the plugin use the new API, so there's no problem beside getting the new version ...

Holger

---

### Post by ajgreeny on 2021-03-05
Thanks for that Holger; it shows how little I know about such details, or even what exactly an API is!

However, as you say, there is no problem in getting the newer version of the ***libweather.so*** file to replace the version in the default package in order to get the applet to work again.

---

### Post by SantaFe on 2021-03-06
For those who don't mind using a DEB from MX-17, this post here: [https://gitlab.xfce.org/panel-plugins/xfce4-weather-plugin/-/issues/27#note_26949](https://gitlab.xfce.org/panel-plugins/xfce4-weather-plugin/-/issues/27#note_26949)  gives you a download link for the plugin from the MX17 repository.  Tried it & I gots weather. ;)

---

### Post by him610 on 2021-03-06
Downloaded xfce4-weather-plugin_0.10.2-1_20.04_amd64.deb from the the link, [https://launchpad.net/~wasta-linux/+archive/ubuntu/xfce-4-16/+packages]("https://launchpad.net/~wasta-linux/+archive/ubuntu/xfce-4-16/+packages") provided in post #1 by ajgreeny
Removed the current installed version of xfce4-weather-plugin.
Installed the downloaded deb file.
Rebooted.
Weather Update indicator in panel now displays information.

@ajgreeny - big thanks:)

---

### Post by ajgreeny on 2021-03-06
As I said in my edit to post #1
> EDIT.
I have just restored the repository version but then downloaded the version from the PPA for xfce-4.16 at [https://launchpad.net/~bluesabre/+ar...4.16/+packages](https://launchpad.net/~bluesabre/+ar...4.16/+packages).
I extracted the libweather.so from the package of that PPA version and replaced the installed version with this 4.16 version.

All is working well at present. 
I still have the repository version of the plugin installed and changed only the libweather.so file that the repo version gives.
This means that should an updated version of the plugin appear in repos I shall get it using normal upgrades rather than having possible problems due to a non-standard version being installed.

At least we all have this useful information available to us again!

---

### Post by T6&amp;sfpER35% on 2021-03-07
[http://repo.linuxliteos.com/linuxlite/pool/main/x/xfce4-weather-plugin/xfce4-weather-plugin_0.11.0-1_amd64.deb](http://repo.linuxliteos.com/linuxlite/pool/main/x/xfce4-weather-plugin/xfce4-weather-plugin_0.11.0-1_amd64.deb)

did it for me

---

### Post by BFG on 2021-03-21
For those who don't want to pollute their systems with other debs or deviate from update path by compiling, 
ajgreeny's post in that thread is very effective. 

[https://gitlab.xfce.org/panel-plugins/xfce4-weather-plugin/-/issues/27](https://gitlab.xfce.org/panel-plugins/xfce4-weather-plugin/-/issues/27)

Edit: Just noticed Post #1 is updated with this.
So just adding that it worked for me on multiple installs.

---

### Post by Sonador on 2021-03-22
This same "bug" also happened in previous 18.04 LTS, what a pity it has happened again. And what more - the bug had been reported before it occurred because the weather applet was showing the warning about ending API...

---

