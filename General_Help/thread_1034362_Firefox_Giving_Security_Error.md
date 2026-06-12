---
title: "Firefox Giving Security Error"
date: 2009-01-08
forum: General Help
---

### Post by jskandhari on 2009-01-08
When ever i start my Firefox in Ubuntu it Gives me this error
[COLOR="Red"]Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.[/COLOR]

whereas my hardisk has sufficient space and all the permisions:confused:

---

### Post by fooman on 2009-01-08
if it were me,  i would first close firefox if it is open. * then back up your bookmarks*....then delete the hidden .mozilla folder that contains your profile.

open your home folder  > places > home folder

in the toolbar, click view and put a check next to "show hidden files"

find the .mozilla folder....right click on it and choose "move to trash"

reopen firefox and all should be good (you will have to reinstall any plugins you had before).

---

### Post by jskandhari on 2009-01-08
It worked thanksz... but there must be a way i mean editing some text or so.. instead of re-creating the prof.. or browser app data

---

### Post by PierreDeKat on 2009-01-08
Is this the message?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=90102[/IMG]

Wow, I thought this was purely a [seamonkey bug]("https://bugs.launchpad.net/ubuntu/+source/seamonkey/+bug/290857"), but apparently it's occurring in Firefox as well.

Are you using Intrepid? If so, this bug might be related more to Intrepid, since it occurs in both Firefox and Seamonkey.

I ended up having to use Ubuntuzilla to upgrade my Seamonkey to 1.1.14. That was the only way I could rid myself of this nuisance.

If you continue to have problems, I'm guessing you will have to use [Ubuntuzilla]("http://ubuntuzilla.wiki.sourceforge.net/") to upgrade to a newer version of Firefox.

---

### Post by jskandhari on 2009-01-08
> **PierreDeKat said:**
> Is this the message?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=90102[/IMG]

Wow, I thought this was purely a [seamonkey bug]("https://bugs.launchpad.net/ubuntu/+source/seamonkey/+bug/290857"), but apparently it's occurring in Firefox as well.

Are you using Intrepid? If so, this bug might be related more to Intrepid, since it occurs in both Firefox and Seamonkey.

I ended up having to use Ubuntuzilla to upgrade my Seamonkey to 1.1.14. That was the only way I could rid myself of this nuisance.

If you continue to have problems, I'm guessing you will have to use [Ubuntuzilla]("http://ubuntuzilla.wiki.sourceforge.net/") to upgrade to a newer version of Firefox.
Deleting the mozilla application data folder ".mozilla" ( it is hidden so press ctrl+h first to display hidden folders ) in this way when next time i start the firefox it works perfectly...

The very resson it started coming what i think is my HDD partiton on which Ubuntu was installed was full... ( linking library folders from vista copies them during installation... ) so basically i think it was that....

Now what i what is some log file which has this error still stored in it.. in the app data folder ... so by editing the problm can be solved instead of deleting the whole folder...

---

### Post by Cosmosis on 2009-02-28
I have been using Ubuntu on a netbook for a while without problems, and decided today to take the plunge and dual-boot it on my XP desktop.  Install went fine, but immediately upon booting and installing all 200+ recommended updates, I started getting this security error when trying to open Firefox.  Firefox has never opened at all, either giving me the error, or after uninstalling it and reinstalling it, not opening at all.  I can see a box in the taskbar at the bottom that shows Firefox trying to open, but then it just vanishes and nothing happens.  I looked and no longer have a .mozilla folder anymore (even checking with "show hidden files" activated).  So....anyone else gotten to this point?  I can't get on the web, and I tried installing a different browser, which has it's own problems and won't load.  Sigh.  Never had this much trouble with Ubuntu before!  Anyway, any suggestions or help would be appreciated.  Thanks.

---

