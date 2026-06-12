---
title: "OpenOffice update problem"
date: 2009-01-30
forum: General Help
---

### Post by arepaking on 2009-01-30
Hello experts,
I am running the update manager and I am receiving the following message:
```

W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
```

Does anyone knows how to get this missing public key? 

I am using the following Source to keep my OpenOffice up-to-date:
[http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu)

Thanks in advance for your help,
AK

---

### Post by Mr Tim on 2009-01-30
I had a similar problem and had a friend help me out. Then I did a partial upgrade which removed openoffice and I'm having trouble getting it back. :(
I don't know if the problems are related, but I just thought I should perhaps warn you.

---

### Post by arepaking on 2009-01-30
Does anyone has an entry in the Authentication tab (Software Source) for Launchpad OpenOffice? I don't know if I delete that one by mistake or there is no authentication key for OO.

I am attaching a screenshot so you can help me figure it out if I am missing a key.

Thanks in advance,
AK

---

### Post by Mr Tim on 2009-01-30
The key can be found Here:
[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x60D11217247D1CFF](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x60D11217247D1CFF)
Copy the contents into an empty text file, then add the key file in the authorisation tab with the "import key file" button.
Like I said before, this killed my installation of OpenOffice (I think the repository may be broken), so be careful.

---

### Post by Aearenda on 2009-01-30
The PPA seems to contain an unfinished build of the latest version. It's best to hold off upgrading until the dependency problems go away.

Look at [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa) - note that the build status is not yet ticked for the i10n package.

EDIT - it is done now, but there are still 8 packages with a failed build, so keep waiting!

EDIT2: The missing dependency dictionaries-common is now done, upgrades for Intrepid should work. Hardy is still building as I write.

---

### Post by arepaking on 2009-01-30
Ok, I fixed the issue with the PPA key. The message is not displayed anymore. Thanks guys.

Now, when I click on the Update Manager I can see some pending OpenOffice updates by they are like disabled ( gray color ) and cannot be marked. If I do this via terminal I get the following results:

```
 sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-math
  openoffice.org-style-human openoffice.org-writer python-uno
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
```

Do you think this could be related to the PPA that still under development? I read in other forums that running: ```
apt-get dist-upgrade
``` could fix any packages that are being kept back. Is this true? 

I thought that command supposed to be used to go from a distro to another (hardy to intrepid). Please correct me if I am wrong.

Thanks in advance,
AK

---

### Post by Aearenda on 2009-01-30
Running apt-get dist-upgrade with the PPA in its present incomplete state will remove large parts of OpenOffice **and not replace them**. Just wait until Update Manager is willing to do the upgrade without warnings.

Using 'dist-upgrade' allows apt-get to remove packages that clash with new or updated ones - it isn't just for full version upgrades, but needs to be used with care. Now is not the time to try it!

If you want to get rid of the upgrade marker in the notification area, you can lock the present versions of OpenOffice 3 in Synaptic, but then you'll need to watch the PPA page to know when to unlock it again.

EDIT: I just looked at the PPA page, and the i10n package build is finished. However, apt-get update then apt-get upgrade still wants to hold back large parts of OpenOffice, so I still suggest waiting until the repository is sorted out. The page is showing that 8 packages have a failed build status.

---

### Post by arepaking on 2009-01-30
> **Aearenda said:**
> Running apt-get dist-upgrade with the PPA in its present incomplete state will remove large parts of OpenOffice **and not replace them**. Just wait until Update Manager is willing to do the upgrade without warnings.

Using 'dist-upgrade' allows apt-get to remove packages that clash with new or updated ones - it isn't just for full version upgrades, but needs to be used with care. Now is not the time to try it!

If you want to get rid of the upgrade marker in the notification area, you can lock the present versions of OpenOffice 3 in Synaptic, but then you'll need to watch the PPA page to know when to unlock it again.

EDIT: I just looked at the PPA page, and the i10n package build is finished. However, apt-get update then apt-get upgrade still wants to hold back large parts of OpenOffice, so I still suggest waiting until the repository is sorted out. The page is showing that 8 packages have a failed build status.

Thanks again Aearenda!
Unfortunately I read your post too late. I ran distro-upgrade and I notice that it removed OpenOffice writer :(  Do you think when everything sorts out I will get Writer back?

---

### Post by Aearenda on 2009-01-30
I *think* you will be able to get it back when the PPA is sorted out, by re-installing the openoffice.org meta-package which depends on all the rest. 

I'll add here I'm not connected in any way with the PPA or OOo 3 - I just encountered the same issue myself and somehow didn't fall over the edge of the precipice!

---

### Post by sunny_nwho on 2009-01-30
Yes let us hope this thing gets rectified soon

---

### Post by Aearenda on 2009-01-30
Best not to stress about it. If you desperately need OOo now, and you have encountered the partial removal problem, you can remove all the version 3 packages and then reinstall 2.4 from the standard repository, or you can download the 'raw' deb version from OOo's website, or you may find the rc1 debs are still in your apt's cache. Any of these may end up making your system less stable, and it'll be less work to wait, but it may not be quick. Remember we're depending on volunteers for all this!

---

### Post by sunny_nwho on 2009-01-30
Thanks a lot for the message..yes i absolutely agree with you and kudos to all the voluteers!!

---

### Post by Aearenda on 2009-01-31
My system is now happy to proceed with the entire update - the difference is that the 'dictionaries-common' package was built in the PPA - I'll post an edit with the outcome soon...

EDIT: It's done, it works (or at least, the upgrade works, Writer opens docs, YMMV).

I suggest those on Intrepid who had OOo removed earlier now try adding it back (after 'sudo apt-get update' or hitting the 'reload' button in Synaptic).
Hardy packages are not done yet.

---

### Post by arepaking on 2009-01-31
Hi guys,
My system is updating properly as we speak. It seems that finally everything sorted out. After the installation I will manually try to install back Writer.

Have a nice weekend!

---

