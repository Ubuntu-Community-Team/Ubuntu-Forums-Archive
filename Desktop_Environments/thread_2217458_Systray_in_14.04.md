---
title: "Systray in 14.04"
date: 2014-04-17
forum: Desktop Environments
---

### Post by RudolfMDLT on 2014-04-17
Hi Folks, 

Has any one found a patch or fix to get the systray white list back in 14.04? I use davmail to sync Thunderbird with exchange and I can't setup davmail becuase the ampplication starts up minimised! :confused:

Thanks for any help or a point in the right direction (such as forcing an application to show it self in the systray :popcorn:) 

Regards,

Rudolf

---

### Post by slickymaster on 2014-04-17
[Unity Global Menu Can Now Be Disabled For Individual Applications [Ubuntu 14.04 Trusty Tahr]]("http://www.adminreseau.fr/unity-global-menu-can-now-be-disabled-for-individual-applications-ubuntu-14-04-trusty-tahr/")

---

### Post by mc4man on 2014-04-17
There are 2 ways, both require a unity source rebuild which is best done via a ppa.
(unity builds are quite large now due to precompiled headers & may fail on one of the boatload of tests, though you can try locally if inclined.

One way is just to hard code whatever apps you wish, fairly simple edit unity source > panel/PanelTray.cpp at or around line 33 - 
Ex. - orig.
> const std::array<std::string, 2> WHITELIST {{ "JavaEmbeddedFrame", "Wine" }};
adding 3 apps, note blue
```
const std::array<std::string, [COLOR="#0000CD"]5[/COLOR]> WHITELIST {{ "JavaEmbeddedFrame", "Wine", "Vlc", "Smplayer", "Audacious" }};

```

There is also a global systray patch, I'm currently testing it here, seems ok . In this case the systray is enabled for all apps that use & are set to use in apps config if needed.
As far as a ppa this one should have a trusty build in due course..
[https://launchpad.net/~timekiller/+archive/unity-systrayfix](https://launchpad.net/~timekiller/+archive/unity-systrayfix)

Again if inclined patch line adjusted for trusty attached
(I have a build in a ppa but I also change the expo launcher icon to work with 1x4 workspaces instead of the default 2x2

---

### Post by adrian-ambroziak on 2014-04-21
[https://launchpad.net/~timekiller/+a...ity-systrayfix]("https://launchpad.net/~timekiller/+archive/unity-systrayfix") still doesn't work. Checked it.

---

### Post by jwadamson on 2014-04-22
I'm hoping timekiller updates the ppa it soon. Then I plan to sit on Trusty at least until next LTS if not the one after.

---

### Post by z-raj on 2014-04-22
Hi,

try this:

```

sudo apt-add-repository ppa:gurqn/systray-trusty
sudo apt-get update
sudo apt-get upgrade

```

then logoff and logon again.

---

### Post by RudolfMDLT on 2014-04-23
Thanks guys! 

Appreciate it!

Regards,

Rudolf

---

### Post by Scoobin on 2014-04-23
Hey RudolfMDLT, what solution did you use? Can anyone confirm z-raj's PPA works?

---

### Post by jwadamson on 2014-04-23
So timekiller ppa now has trusty listed. I applied that on my secondary computer, but the tray icons did not show up (checked after reboot). 

I don't have time until later today/tomorrow to see if it is fixed or try ppa:gurqn/systray-trusty. If I get something working I'll post back here with my results (hopefully).

So I removed timekiller and added gurqn and I got my systray apps back. If it wasn't for the fact that I have a couple corporate apps that the only interface is via systray I probably wouldn't have even bothered.

---

### Post by z-raj on 2014-04-23
But there is any problem. I can not see Empathy and Printing systray icon :-(

---

### Post by z-raj on 2014-04-23
Any Idea?

---

### Post by Scoobin on 2014-04-23
Thanks guys. I am waiting to see if I can get this functionality for a particular app before I  upgrade from 13.10 -> 14.04. Looks like it's probably safe for me to  upgrade and use gurqn PPA.

> **z-raj said:**
> But there is any problem. I can not see Empathy and Printing systray icon [IMG]http://ubuntuforums.org/images/smilies/icon_sad.gif[/IMG]

I don't use Emapthy a whole lot but check your settings for both apps... You may have to enable the try icon like you do in Pidgin. Otherwise, Pidgin is a decent alternative if you don't find a way (I think I was reading Pidgin now has Unity indicator support).

EDIT: I guess you're aware that Empathy also uses the Unity messaging indicator? (the email icon)

---

### Post by z-raj on 2014-04-24
Empathy uses thme similar icon like Pidgin (green point). Thats a pitty about printing icon what missing in systray.

---

### Post by epictete on 2014-04-24
ppa:timekiller/unity-systrayfix doesn't work in 14.04.

But ppa:gurqn/systray-trusty works perfectly.

Thank you so much!

---

### Post by peshooo on 2014-04-24
ppa:gurqn/systray-trusty doesn't work for me - Xubuntu upgraded to 14.04 :(

---

### Post by chico3 on 2014-04-29
I can confirm that 

```
sudo apt-add-repository ppa:gurqn/systray-trusty
sudo apt-get update
sudo apt-get upgrade
```
is working in Ubuntu 14.04 LTS - I can now see the Davmail and google chrome systray icon

---

### Post by kanhiya on 2014-05-05
Gurqn, First of all thanks for the systray fix. Please provide a fix for Unity Drag and Drop , application icons, on desktop also. It was working well with 12.04 and with 14.04, i got  error while copying and it is a known old age bug. [https://bugs.launchpad.net/unity/+bug/1241972](https://bugs.launchpad.net/unity/+bug/1241972) , please, many first time users will get benefit from it.

---

### Post by mrnatelantz on 2014-05-22
This worked for me! Thanks dude!!!!!

---

### Post by david-treumann on 2014-09-13
I had to temporarily set the pin-priority to 1000 for the installation. Afterwards I reduced it to 600 again.

Package: *
Pin: release o=LP-PPA-gurqn-systray-trusty
Pin-Priority: **1000**

---

### Post by phanhan on 2014-09-15
follow me, timekiller ppa now has trusty listed. 
I applied that on my secondary computer, but the tray icons did not show up (checked after reboot).
Ads: Vinahost là doanh nghi&#7879;p hàng &#273;&#7847;u Vi&#7879;t Nam chuyên kinh doanh các l&#297;nh v&#7921;c  D&#7883;ch V&#7909; [ Thuê ch&#7893; &#273;&#7863;t máy ch&#7911;](http://vinahost.vn/cho-dat-may-chu.html) và [ thuê máy ch&#7911; &#7843;o](http://vinahost.vn/gioi-thieu-cong-nghe-cloud.html) và [ Hosting doanh nghi&#7879;p](http://vinahost.vn/hosting.php) và [ tên mi&#7873;n qu&#7889;c t&#7871;](http://vinahost.vn/vndomain.php) và [ d&#7883;ch v&#7909; email hosting](http://vinahost.vn/email-hosting.html) t&#7889;t nh&#7845;t hi&#7879;n nay.

---

### Post by sethj3 on 2014-09-26
> **z-raj said:**
> Hi,

try this:

```

sudo apt-add-repository ppa:gurqn/systray-trusty
sudo apt-get update
sudo apt-get upgrade

```

then logoff and logon again.

This upgrades the Unity package. How will that affect future updates to Unity from upstream? My first though is it would either break it or the update would replace this package and I'd have to preform the upgrade again, but I'm not sure.

---

### Post by armid on 2014-11-11
Hi. Please tell me how I can remove this repo [http://dl.dropbox.com/u/16833006/Selection_003.png](http://dl.dropbox.com/u/16833006/Selection_003.png) and revert all changes (from this repository) in Ubuntu?

---

### Post by mc4man on 2014-11-11
> **armid said:**
> Hi. Please tell me how I can remove this repo [http://dl.dropbox.com/u/16833006/Selection_003.png](http://dl.dropbox.com/u/16833006/Selection_003.png) and revert all changes (from this repository) in Ubuntu?

Open up your source like in the screenshot, highlight the ppa entry & click on the delete button
In this case that ppa has no utopic packages so nothing was installed for **utopic**

(in the case where a ppa did have builds for your release you'd use ppa-purge

---

### Post by armid on 2014-11-11
> (in the case where a ppa did have builds for your release you'd use ppa-purge
You mean - sudo ppa-purge ppa:repository to remove?

---

### Post by mc4man on 2014-11-11
> **armid said:**
> You mean - sudo ppa-purge ppa:repository to remove?

If you are on 14.10 then you have no packages from that ppa, so just remove the entry from your sources.

To double ck. - 
```
apt-cache policy unity
```

---

### Post by armid on 2014-11-12
> **mc4man said:**
> If you are on 14.10 then you have no packages from that ppa, so just remove the entry from your sources.

And what I need to do if the package got utopic was same days ago, and then author remove them. In this case this package may be installed on my pc?

> 
apt-cache policy unity
```
unity:
  Installed: 7.3.1+14.10.20141016-0ubuntu1
  Candidate: 7.3.1+14.10.20141016-0ubuntu1
  Version table:
 *** 7.3.1+14.10.20141016-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ utopic/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by adrian-ambroziak on 2015-04-21
Doesn't work anymore. Timekiller ppa also. They changed unity once again.

---

### Post by callen92 on 2015-04-23
Not working for me either. There was a Unity update this month that cancelled out the PPA fix

---

### Post by mikini on 2015-05-07
> **callen92 said:**
> Not working for me either. There was a Unity update this month that cancelled out the PPA fix

Gurqn has also marked the "Unity with systray" ppas as "no longer - maintained" (see [https://launchpad.net/~gurqn/+archive/ubuntu/systray-utopic](https://launchpad.net/~gurqn/+archive/ubuntu/systray-utopic)), so I didn't want to go that way.

However, I had the same specific problem as the original poster with inaccessible davmail tray icon. I solved it by using the platform independent package of davmail. Somehow this enables davmail to show a tray icon.

I'm running davmail 4.6.1 ([http://sourceforge.net/projects/davmail/files/davmail/4.6.1/davmail-4.6.1-2343.zip/download](http://sourceforge.net/projects/davmail/files/davmail/4.6.1/davmail-4.6.1-2343.zip/download)) with tray icon on Ubuntu 14.10 (utopic).

Mikkel

---

### Post by Lopatin_Egor on 2015-05-07
Hello,
May be it will be helpful for someone. You may downgrade Unity version and dependent applications and hold them updating with apt-mark hold. Original post from author is here: [https://askubuntu.com/questions/612912/how-to-re-enable-the-systray-indicator-panel-after-latest-updates/616545#616545](https://askubuntu.com/questions/612912/how-to-re-enable-the-systray-indicator-panel-after-latest-updates/616545#616545)

```

sudo apt-get -s purge unity unity-services libunity-core-6.0-9

sudo apt-get install unity=7.2.4+14.04.20141217-0ubuntu1-systray-ppa1 libunity-core-6.0-9=7.2.4+14.04.20141217-0ubuntu1-systray-ppa1 unity-services=7.2.4+14.04.20141217-0ubuntu1-systray-ppa1

sudo apt-mark hold unity unity-services libunity-core-6.0-9

```

From the author:
> 
Be warned: doing this may break things in the future, and you may miss  out on important security updates.  Personally, though, to get a  functional systemtray back, it's a risk I'm willing to take.


---

### Post by callen92 on 2015-05-12
Thanks for the replies. What I ended up doing was use the whitelist patch from the Arch Linux version of Unity with the source code, build the unity packages, and then install them. If there is a need for this, it would be possible to automate a process to apply the patch to current and future versions of Unity and upload the fixed debs to a PPA. In theory, the PPA would be self-maintaining.

---

### Post by temenchat on 2015-06-12
> **adrian-ambroziak said:**
> Doesn't work anymore. Timekiller ppa also. They changed unity once again.

Mine too.. I am unable to systray-whitelist anymore in the last few days. I don't understand, what's the point of removing systray while there are a lot of users still use it heavily

---

### Post by CantankRus on 2015-06-12
> **temenchat said:**
> Mine too.. I am unable to systray-whitelist anymore in the last few days. I don't understand, what's the point of removing systray while there are a lot of users still use it heavily
See [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2280775&p=13297076#post13297076")

---

### Post by zish on 2015-07-08
> **mikini said:**
> Gurqn has also marked the "Unity with systray" ppas as "no longer - maintained" (see [https://launchpad.net/~gurqn/+archive/ubuntu/systray-utopic](https://launchpad.net/~gurqn/+archive/ubuntu/systray-utopic)), so I didn't want to go that way.

However, I had the same specific problem as the original poster with inaccessible davmail tray icon. I solved it by using the platform independent package of davmail. Somehow this enables davmail to show a tray icon.

I'm running davmail 4.6.1 ([http://sourceforge.net/projects/davmail/files/davmail/4.6.1/davmail-4.6.1-2343.zip/download](http://sourceforge.net/projects/davmail/files/davmail/4.6.1/davmail-4.6.1-2343.zip/download)) with tray icon on Ubuntu 14.10 (utopic).

Mikkel

Based on Mikkel's post, I decided to check out the differences between "/usr/bin/davmail" from the .deb packaged and "davmail.sh" from the platform-independent .zip. It turns out that the .deb installed script adds "/usr/share/java/swt.jar" to the CLASSPATH. DavMail will use SWT if it's available. It reverts to AWT if it can't use SWT.

I got the .deb version to display the System Tray icon by removing "/usr/share/java.swt" from the the "exec" line in "/usr/bin/davmail".
**The line now looks like:**
```
exec java -Xmx512M -Dsun.net.inetaddr.ttl=60 -cp /usr/share/davmail/davmail.jar:$CLASSPATH davmail.DavGateway "$@"
```

---

