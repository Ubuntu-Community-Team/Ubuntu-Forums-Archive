---
title: "Could I have 2 versions installed?"
date: 2009-03-24
forum: General Help
---

### Post by Poalman on 2009-03-24
I was recently trying to install the new style scrobbler plugin for rhythm box, following these instructions [http://blog.blackdown.de/2007/05/19/lastfm-for-rhythmbox-new-style/]("http://blog.blackdown.de/2007/05/19/lastfm-for-rhythmbox-new-style/") and after completing the steps on the website nothing was happening, even after restarts the plugin wasn't showing up.

I couldn't work out why I couldn't install the plugin, so I tried to re-install rhythmbox. So I hit in sudo apt-get remove rhythmbox and it takes off 16Mb, but I noticed that typing rhythmbox into the terminal still brings up rhythmbox exactly as normal, no changes.

So I was thinking I must somehow have 2 independent versions running, and the second gets recognised by packet manager, not by 'rhythmbox' on the command line, and is probably getting this plugin.

So I was wondering how would I go about removing this other version, if this is what is in fact happening.

Thanks for any help :)

Poalman.

---

### Post by Tews on 2009-03-24
There are several ways I can think of,

1. Go to Synaptic Package Manager, do a search for
   Rythmbox and mark it for complete removal. 
   This should do the trick

2. ```
sudo apt-get purge rythmbox
```  

3. Go to the Add/Remove section and mark it for
   removal.

Good Luck!

---

### Post by Poalman on 2009-03-24
Hey Tews,

I tried all three different methods in different orders but still 'rhythmbox' brings up the app just as it always has.

I marked rhythmbox for complete removal, the purge command and there's 1 rhythmbox in Add/Remove and it comes up unticked after purging.

Very confusing :P

---

### Post by Poalman on 2009-03-25
Is there a way to find out what script the bash commands point to?
This might give a better idea of what and where this second version is.

---

