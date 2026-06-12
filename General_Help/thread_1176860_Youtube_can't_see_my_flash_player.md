---
title: "Youtube can't see my flash player"
date: 2009-06-02
forum: General Help
---

### Post by t0p on 2009-06-02
I've been using Youtube for a long time now without flash problems.  But now it's gone weird.  Instead of seeing the videos I want to play, I'm getting this message:

> Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. 

Thing is, I haven't turned off Javascript and I have the latest **flashplugin-nonfree** in the repos.  This is happening on my desktop that runs Hardy, and on my Eee PC - I've just installed Jaunty NetBook Remix on the Eee, so I *know* that it's got brand-new flash etc.

I don't know what to do to fix this problem.  Any ideas?  I don't have any problem playing flash videos on other sites, like Megavideo and Novamov.

---

### Post by JGreenidge on 2009-06-02
> **t0p said:**
> I've been using Youtube for a long time now without flash problems.  But now it's gone weird.  Instead of seeing the videos I want to play, I'm getting this message:



Thing is, I haven't turned off Javascript and I have the latest **flashplugin-nonfree** in the repos.  This is happening on my desktop that runs Hardy, and on my Eee PC - I've just installed Jaunty NetBook Remix on the Eee, so I *know* that it's got brand-new flash etc.

I don't know what to do to fix this problem.  Any ideas?  I don't have any problem playing flash videos on other sites, like Megavideo and Novamov.

I echo this, after running all over the web for a solution!

---

### Post by TheForumTroll on 2009-06-02
What browser are you using? Firefox? Did you try a newer version?

I have only seen this on Windows machines using Norton or some other software with adblocking functionality. Do you perhaps use adblock?

---

### Post by Chronon on 2009-06-02
Works fine on my EeePC.  I thought I was seeing the same, but I had forgotten to whitelist youtube and ytimg.

---

### Post by t0p on 2009-06-03
On my Eee PC I'm using Firefox 3.0.10 on Ubuntu NBR Jaunty.  I'm not near to my desktop machine so I can't check that machine's browser version, but it's Firefox on Hardy, and as my updates etc are all up to date I assume that's also Firefox 3.0.10.

I haven't got any adblocker on my Eee PC.  The only add-ons I've got on this machine's browser are User Agent Switcher, Greasemonkey, CustomizeGoogle, Tor Button, FireGPG and gspace.  I've tried using Youtube with all add-ons disabled and it makes no difference.

When I first noticed this happening on my Hardy desktop machine, it didn't happen consistently with every video I wanted to watch.  Some vids would play okay, while others would display the notice about javascript/flash.  But now it seems to happen with every video, on both the desktop computer and my Eee PC.

---

### Post by t0p on 2009-06-03
Grr, now Youtube vids are playing - I've just watched 3 vids.  Happy happy, right?  *Wrong!!* - cos later on I'll get that stupid javascript/flash message again.

If anyone knows what's going on/how to fix it for good... please post.

---

### Post by spcwingo on 2009-06-03
I too have had nothing but heartache with the flash from the repos.  You can try uninstalling flash then reinstalling like this:

```
sudo apt-get remove flashplugin-nonfree
```

Then going to the adobe site and downloading the tar.gz version.  Extract that and open nautilus as root:

```
gksu nautilus
```

Now copy the extracted libflashplayer.so to /usr/lib/firefox-addons/plugins and restart Firefox.  Alternately, you can try the .deb from the Adobe site, but personally I've never had much luck with it.

---

### Post by kendoori on 2009-06-06
Last bit worked for me. Prior to this Hulu wasn't working, and now it is.

---

