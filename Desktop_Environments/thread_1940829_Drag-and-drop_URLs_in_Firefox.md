---
title: "Drag-and-drop URLs in Firefox"
date: 2012-03-14
forum: Desktop Environments
---

### Post by thundre on 2012-03-14
I often drag links from one tab to another tab on the firefox tab-bar.  It used to cause them to load in the other tab, until I upgraded to 11.10.

For a while, there was a 5-second delay, when Ubuntu's application bar seemed to be doing something.  If I waited until the drag icon changed before releasing, it worked.  Now everything locks up for 30 seconds or so.  I can't switch applications or workspaces until it clears.

Is this a known bug?  

My best workaround so far is:

right click on link
select "copy link location"
click on second tab
select entire old URL with a double-click
ctrl-v to paste
enter

Anybody have a fix, info on what's happening behind the panel, or a shorter workaround?  I don't want to create a new tab each time because I like to keep a history.

Ubuntu 11.10, Firefox 10.0.2.

---

### Post by sp-1070 on 2012-03-15
did you try reinstalling firefox ?

---

### Post by lovinglinux on 2012-03-15
First try Firefox in sage mode from terminal:

```
firefox -safe-mode
```


I f the problem doesn't occur in safe mode, then is probably an extension causing this. You will need to find each one.

If the problem persists in safe mode, then try to optimize your databases:

[http://www.webgapps.org/tutorials/firefox/optimization/database-optimization](http://www.webgapps.org/tutorials/firefox/optimization/database-optimization)

If optimization doesn't solve your problem, try a clean profile. You can create a clean profile for testing using the profile manager:

```
firefox -P
```

---

### Post by thundre on 2012-03-16
Yes, sp-1070, I have been through a few Firefox versions since I upgraded Ubuntu to 11.10.  My employer follows the security bulletins carefully, and I get blocked by the proxy if I'm not up-to-date.

> **lovinglinux said:**
> First try Firefox in sage mode from terminal:

```
firefox -safe-mode
```I f the problem doesn't occur in safe mode, then is probably an extension causing this. You will need to find each one.

If the problem persists in safe mode, then try to optimize your databases:

[http://www.webgapps.org/tutorials/firefox/optimization/database-optimization](http://www.webgapps.org/tutorials/firefox/optimization/database-optimization)

If optimization doesn't solve your problem, try a clean profile. You can create a clean profile for testing using the profile manager:

```
firefox -P
```
The problem persists in safe-mode.  IMHO this is not a Firefox problem, because **nothing **that Firefox does should prevent me from activating the Ubuntu task-bar, or other application windows.  

*edit*:
I just tried a fresh profile, and nothing was different.

---

### Post by thundre on 2012-03-19
I just tested Google Chrome (from the current google-chrome-stable 17.0.963.79-r125985).  It does the same thing, but it showed some diagnostic output when I closed it.
```

[5007:5007:2238850040:ERROR:x11_util.cc(951)] X Error detected: serial 62576, error_code 10 (BadAccess (attempt to access private resource denied)), request_code 140, minor_code 1 (X_ShmAttach)
[5007:5007:2238854269:ERROR:x11_util.cc(951)] X Error detected: serial 62577, error_code 148 (BadShmSeg (invalid shared segment parameter)), request_code 140, minor_code 3 (X_ShmPutImage)
[5007:5007:2238857365:ERROR:x11_util.cc(951)] X Error detected: serial 62595, error_code 148 (BadShmSeg (invalid shared segment parameter)), request_code 140, minor_code 2 (X_ShmDetach)
```Re-testing did not produce the same output, so perhaps it is irrelevant.

Since it appears other people are not having this problem, I fear my solution has to be a "clean install" of Ubuntu.  :(

**edit:**  I just tested a different user account, and there was no problem.  So it appears I have a bad setting in some configuration file (but probably not Firefox or Chrome).

---

### Post by lovinglinux on 2012-03-20
> **thundre said:**
> I just tested Google Chrome (from the current google-chrome-stable 17.0.963.79-r125985).  It does the same thing, but it showed some diagnostic output when I closed it.
```

[5007:5007:2238850040:ERROR:x11_util.cc(951)] X Error detected: serial 62576, error_code 10 (BadAccess (attempt to access private resource denied)), request_code 140, minor_code 1 (X_ShmAttach)
[5007:5007:2238854269:ERROR:x11_util.cc(951)] X Error detected: serial 62577, error_code 148 (BadShmSeg (invalid shared segment parameter)), request_code 140, minor_code 3 (X_ShmPutImage)
[5007:5007:2238857365:ERROR:x11_util.cc(951)] X Error detected: serial 62595, error_code 148 (BadShmSeg (invalid shared segment parameter)), request_code 140, minor_code 2 (X_ShmDetach)
```Re-testing did not produce the same output, so perhaps it is irrelevant.

Since it appears other people are not having this problem, I fear my solution has to be a "clean install" of Ubuntu.  :(

**edit:**  I just tested a different user account, and there was no problem.  So it appears I have a bad setting in some configuration file (but probably not Firefox or Chrome).

Probably a gnome settings then. The easiest way would be to wipe your settings. However I would suggest making a backup, wiping the settings and then restoring only the things you need, always testing to see if the problem persists.

---

### Post by thundre on 2012-03-20
> **lovinglinux said:**
> Probably a gnome settings then. The easiest way would be to wipe your settings. However I would suggest making a backup, wiping the settings and then restoring only the things you need, always testing to see if the problem persists.
Good suggestion, I did this to my home directory while logged in as another user:
```
su thundre
mkdir bad
mv .* bad
```
Then I moved back stuff that I was sure wasn't causing the problem, re-testing at every stage.  Here's what's left:

```
.adobe/
.amazonmp3/
.aptitude/
.bash_history
.bash_logout
.bashrc
.bluefish/
.bouml
.boumlrc
.cache/
.calc_history
.compiz/
.compiz-1/
.config/
.dbus/
.debtags/
.DesktopApplication1/
.dmrc
.ecryptfs@
.esd_auth
.fontconfig/
.gconf/
.gconfd/
.gksu.lock
.gnome2/
.gnome2_private/
.gnupg/
.goutputstream-GB5FBW
.gpsdrive/
.gstreamer-0.10/
.gtk-bookmarks
.hplip/
.ICEauthority
.icedtea/
.icons/
.java/
.juniper_networks/
.lesshst
.libreoffice/
.local/
.m2/
.macromedia/
.matlab/
.metacity/
.mission-control/
.mplayer/
.mysql_history
.nbprofiler/
.netbeans/
.nvidia-settings-rc
.openoffice.org/
.openoffice.org2/
.org.eclipse.epp.usagedata.recording.userId
.pdfedit/
.pki/
.printer-groups.xml
.Private@
.profile
.pulse/
.pulse-cookie
.qt/
.recently-used
.recently-used.xbel.5SDZ2U
.recently-used.xbel.EWLS5U
.recently-used.xbel.L8X02U
.recently-used.xbel.NEQWXU
.recently-used.xbel.RX5V2U
.shotwell/
.subversion/
.sudo_as_admin_successful
.swt/
.synaptic/
.themes/
.thumbnails/
.update-manager-core/
.update-notifier/
.usbcreator.log
.VirtualBox/
.visualvm/
.wgetrc
.wgetrc~
.wine/
.Xauthority
.Xresources
.Xresources~
.xsession-errors
.xsession-errors.old
```

---

### Post by lovinglinux on 2012-03-22
> **thundre said:**
> Good suggestion, I did this to my home directory while logged in as another user:
```
su thundre
mkdir bad
mv .* bad
```
Then I moved back stuff that I was sure wasn't causing the problem, re-testing at every stage.  Here's what's left:

```
.adobe/
.amazonmp3/
.aptitude/
.bash_history
.bash_logout
.bashrc
.bluefish/
.bouml
.boumlrc
.cache/
.calc_history
.compiz/
.compiz-1/
.config/
.dbus/
.debtags/
.DesktopApplication1/
.dmrc
.ecryptfs@
.esd_auth
.fontconfig/
.gconf/
.gconfd/
.gksu.lock
.gnome2/
.gnome2_private/
.gnupg/
.goutputstream-GB5FBW
.gpsdrive/
.gstreamer-0.10/
.gtk-bookmarks
.hplip/
.ICEauthority
.icedtea/
.icons/
.java/
.juniper_networks/
.lesshst
.libreoffice/
.local/
.m2/
.macromedia/
.matlab/
.metacity/
.mission-control/
.mplayer/
.mysql_history
.nbprofiler/
.netbeans/
.nvidia-settings-rc
.openoffice.org/
.openoffice.org2/
.org.eclipse.epp.usagedata.recording.userId
.pdfedit/
.pki/
.printer-groups.xml
.Private@
.profile
.pulse/
.pulse-cookie
.qt/
.recently-used
.recently-used.xbel.5SDZ2U
.recently-used.xbel.EWLS5U
.recently-used.xbel.L8X02U
.recently-used.xbel.NEQWXU
.recently-used.xbel.RX5V2U
.shotwell/
.subversion/
.sudo_as_admin_successful
.swt/
.synaptic/
.themes/
.thumbnails/
.update-manager-core/
.update-notifier/
.usbcreator.log
.VirtualBox/
.visualvm/
.wgetrc
.wgetrc~
.wine/
.Xauthority
.Xresources
.Xresources~
.xsession-errors
.xsession-errors.old
```

You can probably copy these too:

```
.amazonmp3/
.aptitude/
.bash_history
.bashrc
.gnupg/
.mplayer/
.mysql_history
.netbeans/
.openoffice.org/
.openoffice.org2/
.shotwell/
.subversion/
.VirtualBox/
.visualvm/
.wgetrc
.wine/

```

If I would bet, I would say the problem is in nvidia or compiz settings.

---

### Post by thundre on 2012-04-16
It happened again.  I did some more testing, but connected via my home connection instead of through the office proxy, and there was no problem.

VPNed to the office (vpnc) and turned on the proxy, and BANG! it's back.

Disconnected vpnc, un-set the Firefox proxy, and it's working great.

My employer is fairly paranoid about security and blocks many sites at the proxy.  Does the action of dragging a link from Firefox cause some kind of network query?  Often it's not even out of the window when the freeze happens, just dragging it around within the same window for 2 seconds will cause the problem.

The links themselves are perfectly fine, as long as I take the time to copy, switch tabs, select, paste, Enter.

---

### Post by lovinglinux on 2012-04-16
> **thundre said:**
> It happened again.  I did some more testing, but connected via my home connection instead of through the office proxy, and there was no problem.

VPNed to the office (vpnc) and turned on the proxy, and BANG! it's back.

Disconnected vpnc, un-set the Firefox proxy, and it's working great.

My employer is fairly paranoid about security and blocks many sites at the proxy.  Does the action of dragging a link from Firefox cause some kind of network query?  Often it's not even out of the window when the freeze happens, just dragging it around within the same window for 2 seconds will cause the problem.

The links themselves are perfectly fine, as long as I take the time to copy, switch tabs, select, paste, Enter.

I am not sure, but I guess it could be an attempt to update the favicon.

---

### Post by thundre on 2012-04-16
> **lovinglinux said:**
> I am not sure, but I guess it could be an attempt to update the favicon.
Hmmm, could be.  I installed wireshark to see what was happening.   The freeze time is up to 60 seconds now.  When I start dragging the link, wireshark stops updating.  When it finally unfreezes, I see:

```
3    11.223779    172.31.136.99    128.29.154.114    DNS    62    Standard query A ubuntuforums.org
4    11.241988    128.29.154.114    172.31.136.99    DNS    78    Standard query response A 91.189.94.12
5    11.242429    172.31.136.99    91.189.94.12    TCP    60    55521 > http [SYN] Seq=0 Win=13720 Len=0 MSS=1372 SACK_PERM=1 TSval=21001274 TSecr=0 WS=128
6    14.248029    172.31.136.99    91.189.94.12    TCP    60    55521 > http [SYN] Seq=0 Win=13720 Len=0 MSS=1372 SACK_PERM=1 TSval=21002026 TSecr=0 WS=128
7    20.256219    172.31.136.99    91.189.94.12    TCP    60    55521 > http [SYN] Seq=0 Win=13720 Len=0 MSS=1372 SACK_PERM=1 TSval=21003528 TSecr=0 WS=128
8    32.288230    172.31.136.99    91.189.94.12    TCP    60    55521 > http [SYN] Seq=0 Win=13720 Len=0 MSS=1372 SACK_PERM=1 TSval=21006536 TSecr=0 WS=128
```3-4 are a DNS query and response, which shouldn't happen, because I have network.prefetch-next set to false.  The IP address belongs to canonical.com because I was using the ubunuforums.org page to test.

5-8 are http connections which attempt to bypass the proxy to go to that host (and get the favicon?).  It looks like they're timing out.  The first seems to be immediately when I start dragging, then 3 seconds, 9 seconds, 21 seconds.  Of course the company firewall is not allowing this direct connection to happen, so there is no response.

At this point I think it's a Firefox problem, but why is the entire Ubuntu desktop becoming unresponsive just because Firefox has a problem?

New info:  Because Firefox appeared to ignore the Ubuntu proxy pref, I was only setting the Firefox proxy pref.  Setting the Ubuntu proxy pref to the same thing eliminates the problem.

---

### Post by lovinglinux on 2012-04-16
Good to know. I think you should report this as a bug.

I think is not Firefox fault, but an Unity fault. I guess when you drag the link, Unity is doing something with it, otherwise it wouldn't be necessary to use the Ubuntu proxy settings.

---

### Post by thundre on 2012-04-17
Reported as Ayatana Design bug #983866 on Launchpad.

---

