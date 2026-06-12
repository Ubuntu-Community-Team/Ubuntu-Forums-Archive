---
title: "Adobe Air apps work in nome but not in KDE 4"
date: 2009-02-04
forum: Desktop Environments
---

### Post by rosslaird on 2009-02-04
Air apps work perfectly under gnome. But with kde4, they seem to load and then yield an empty frame where the app is supposed to be. Anyone else experince this?

---

### Post by DarkAdmiral on 2009-02-28
> **rosslaird said:**
> Air apps work perfectly under gnome. But with kde4, they seem to load and then yield an empty frame where the app is supposed to be. Anyone else experince this?

yes same here. I think the error message gives the reason:

./feedalizr
Unknown desktop manager, only Gnome and KDE are supported

kde4 seems not supported yet :(

---

### Post by dropvision on 2009-05-12
I can confirm this as well. Unfortunately, it took me all night working on a brand new Kubuntu machine to figure out that it was KDE 4, not my own tired mind, that was causing my AIR apps not to work.

My initial thought was that it was the window manager, but that's not it. When I load up KDE and then run metacity --replace, the same thing occurs. So KWin isn't the problem.

I think what's happening is it can't get kwallet to open - TweetDeck, for example, launches the keyring "Allow this application?" dialog box when you fire it up in GNOME. When you launch it in KDE, it comes up blank.

Is there something we can prepend to the command line here to get it to use the GNOME keyring for the time being?

---

### Post by fccoelho on 2009-05-15
I have the same problem. It seems to really be a problem with the wallet since the only built-in (simple) storage air apps have (apart from the more complex sql api) is an encrypted store. I have written a very simple Air app and it fail at the exact point where it tries to write to the store. 

Now the question really is: Why it can't open the kwallet in KDE   but can open the gnome equivalent one? this seems like an issue that should be taken to the kde4 dev community, IMO.

---

### Post by felipero on 2009-05-15
Some AIR applications need the KWallet enabled to work. If you don't want kwallet boring you, just set an empty password for it.

hope this help

---

### Post by dropvision on 2009-05-16
> **fccoelho said:**
> this seems like an issue that should be taken to the kde4 dev community, IMO.

I'm not too sure about that. As I said, AIR apps run perfectly under (at least some) other distros (Sabayon Linux for me runs them just as well as under GNOME.) So I really think this must be distro-specific.

> **felipero said:**
> Some AIR applications need the KWallet enabled to work. If you don't want kwallet boring you, just set an empty password for it.

hope this help

Are you opening up kwalletmanager and blanking out a specific password or are you changing the password for the entire wallet/keyring to blank?

I still can't seem to get this to work.

---

### Post by rameshvr on 2010-01-03
same issue.
I tried running TweetDeck with KWallet running.. 
no way.. it throws the same error..

---

### Post by adpads on 2010-01-15
For what it's worth, I'm having the same issue in Fedora 12 and in Ubuntu Karmic - Adobe AIR apps launch fine in GNOME but not in KDE 4.3.4. 
Here is what seems to be the state of the art on the Fedora forums as to answers: [http://forums.fedoraforum.org/showthread.php?t=225614](http://forums.fedoraforum.org/showthread.php?t=225614)
- in a word, they haven't gotten anywhere either..

I'm much obliged to anyone who can suggest a fix to this problem.

---

### Post by frenchrh on 2010-06-26
The issue here is Adobe Air's local store (called ELS, I think) and it needing local access, so you need to have you KWallet (in KDE) or Gnome keyring working right.  

If  you launch an Air App, like the NYTimes Reader, and it just gives a blank box, then it failed to open the local store.  

This Adobe page discusses how to configure the keyring or wallet correctly

[http://kb2.adobe.com/cps/492/cpsid_49267.html](http://kb2.adobe.com/cps/492/cpsid_49267.html)

Now I have Adobe Air/Times Reader working on my Open Suse 11.2 64bit with KDE 4.4.4, and its cool.

---

### Post by nicoduck on 2011-06-15
Hi,

I just found out: TweetDeck and Adobe AIR uses the program "kfmclient" to open the URLs.
kfmclient is not installed per default in Kubuntu, but included in the packet "konqueror". You need to install konqueror, which brings kfmclient, it's not available separately. kfmclient honours the default browser (in my case firefox) and opens the link.

Nico

---

