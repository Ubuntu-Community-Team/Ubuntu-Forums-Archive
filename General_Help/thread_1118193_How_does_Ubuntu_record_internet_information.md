---
title: "How does Ubuntu record internet information?"
date: 2009-04-06
forum: General Help
---

### Post by Warpster on 2009-04-06
I'm kind of a privacy freak, and I don't especially enjoy that things are stored and hidden in every nook and cranny these days.

I know that Windows has index.dat files when one uses IE; do Ubuntu and Firefox share this same type of relationship? Or is Firefox info solely stored in Firefox itself?

Thanks for reading this, and I hope someone replies.):P

---

### Post by foxmulder881 on 2009-04-06
Simple answer. If you're that paranoid, just set Firefox to clear your cache, cookies, history etc. when you exit.

---

### Post by polkadotteapot on 2009-04-06
Also go to the firefox add-ons bit. There is a whole world of little things you can do depending on your particular privacy concern.

For example Ghostery tells me that Google Analytics is running on this page (why?). And I have a tidy little program that deletes all the LS cookies and DOMs without me having to stop scripts.

And there's carbon offsetting, inexplicably.

---

### Post by TheLions on 2009-04-06
> **Warpster said:**
> I'm kind of a privacy freak, and I don't especially enjoy that things are stored and hidden in every nook and cranny these days.

I know that Windows has index.dat files when one uses IE; do Ubuntu and Firefox share this same type of relationship? Or is Firefox info solely stored in Firefox itself?

Thanks for reading this, and I hope someone replies.):P

it's stored in /home/{username}/.mozilla/firefox/{random alphanumeric name}

pres Ctrl+H to show hidden files):P

---

### Post by kanikilu on 2009-04-06
Also, the new Firefox 3.1 beta (so presumably the final version will have this as well) includes a "Privacy Mode" option, so you won't have to use any add-ons or manually clean up the cache/cookies/etc.

---

### Post by Warpster on 2009-04-06
> **TheLions said:**
> it's stored in /home/{username}/.mozilla/firefox/{random alphanumeric name}

pres Ctrl+H to show hidden files):P


I'm sorry, but what does one put in the {Random alphanumerical name}?

---

### Post by mb_webguy on 2009-04-06
> **Warpster said:**
> I'm sorry, but what does one put in the {Random alphanumerical name}?

You don't put anything in it.  That's the folder containing your profile, which includes your settings, themes, extensions, passwords, cookies, and browsing history, among other things.  This is also where the browser cache is located.

In general, it's not a good idea to make changes to the contents of this directory directly unless you're absolutely sure of what you're doing.  Everything here can be controlled through Firefox itself, or through various extensions.

---

### Post by 3Miro on 2009-04-06
I personally use stealther, nice add-on and it makes sure crap doesn't enter the cookies and/or history.

Everything else is in files somewhere, people are concerned about privacy and since Linux is Open Source, there is no way things could be "hidden" as in the case of windows.

---

### Post by Warpster on 2009-04-06
> **mb_webguy said:**
> You don't put anything in it.  That's the folder containing your profile, which includes your settings, themes, extensions, passwords, cookies, and browsing history, among other things.  This is also where the browser cache is located.

In general, it's not a good idea to make changes to the contents of this directory directly unless you're absolutely sure of what you're doing.  Everything here can be controlled through Firefox itself, or through various extensions.

Ah, I see. Thank you.

---

### Post by mb_webguy on 2009-04-06
If you're really concerned about your privacy, you have numerous options, depending on your level of paranoia.  Your first step, which I would advise to everyone, is to install the Adblock Plus extension, which blocks various advertising images, cookies, and flash ads, which could be used to track your web browsing activity.  Various other extensions are available to increase your privacy and/or security, particularly ones involving Tor (see below).

You can either manually clear your private data (under Tools->Clear Private Data), or set Firefox to automatically clear it on exit (under Edit->Preferences->Privacy->Private Data->Always clear my private data when I close Firefox).  This is really only good for preventing other people who might use your computer from seeing what you've been up to, and not to prevent anyone who might want to monitor your online activity.

Another thing you might consider is installing [IPBlock]("http://ubuntuforums.org/showthread.php?t=530183").  This is a program that allows you to apply IP blocklists to all of your internet activities.  This would prevent connections to government or corporate hosts that might monitor things like bittorrent uploads or web browsing behavior.

Similarly, you could install [Tor]("https://help.ubuntu.com/community/TOR"), which anonymizes your online activity and makes it extremely difficult for anyone to monitor.

---

