---
title: "vostro v131 problem with upgrade to 11.10"
date: 2011-12-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wgarider on 2011-12-11
My v131 came pre-installed with 11.04 and I was hoping to do an in-place upgrade to 11.10 but get an error "authentication failed - authenticating the upgrade failed. There may be a problem with the network or with the server"
My network seems to be just fine and if it's the server, it's been out for several days now. Anyone else run into this?

Alternatively I downloaded an ISO and used startup disk creator to make a bootable usb stick. On boot, I chose F12, picked USB, and get an error that there's nothing it can boot from. Another thread here suggested I used the USB2 port - did that, same error.

At this point I'm good with 11.04 but would really like to upgrade someday........

---

### Post by wgarider on 2012-01-01
no responses......anyone have any thoughts or ideas on how I might overcome this issue?

---

### Post by mrfeely on 2012-01-08
I just tried to upgrade my Vostro v131 and ran into the same problem.  I was able to get it to work by mounting the ISO as a drive, as described on the [OneiricUpgrades]("https://help.ubuntu.com/community/OneiricUpgrades#Upgrading_Using_the_Alternate_CD.2BAC8-DVD") page.

I did have to decline to update from network sources during the install, to avoid [bug #874508]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/874508").

---

### Post by wgarider on 2012-01-11
Thanks! So you upgraded using the alternate CD? 'preciate the help!

---

### Post by wgarider on 2012-01-11
Hi - I followed the instructions at the link you posted....upgrade seems to have gone ok but now the brightness and keyboard shortcuts don't work. Did you have that issue? Any ideas how to restore those functions?

---

### Post by stefanb21487 on 2012-03-25
This isn't in direct response to your upgrade issues. I just installed 11.10 on my product had the hard keys at the top and if so how were they programmed. Also, was there any specific software utilities that came with your laptop.

Thanks,
SB

---

