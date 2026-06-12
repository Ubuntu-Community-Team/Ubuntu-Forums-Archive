---
title: "Evolution is a mess - beagle plugins for Thunderbird?"
date: 2006-07-18
forum: Desktop Environments
---

### Post by matthias_k on 2006-07-18
I tried very hard to like Evolution, because I think the integration into the GNOME desktop was very well done (sending E-Mails through deskbar, cool! showing my appointments in the calendar applet, cool! indexing my contacts in beagle, cool!).

However, all this great integration is worth nothing if the integrated  application just plain sucks. And Evolution sucks big time. On day one it crashed three times on me, I found numerous bugs, key parts of the application don't work as expected (the app isn't even smart enough to open a browser for me when I click a hyperlink...). The so called "smart and learning" junk mails controls are a joke. I junk-clicked away like 20 mails from the same sender, but the filter still doesn't get that I consider this sender a spammer. It's funny: when I tried Evolution for the first time like 2 or 3 years ago, it felt as alpha back then as it feels today...

But enough rants, here's the question:
Has anyone managed to integrate Thunderbird with the desktop as has been done with Evolution? In particular, I want to manage my addressbook in Thunderbird from now on, but this would mean I can't search my contacts with beagle or deskbar anymore.

Any hints? Thunderbird rocks!

---

### Post by jordilin on 2006-07-18
If I'm not wrong you'll not be able to search through thunderbird by means of beagle. Thunderbird is not pointed out as a supported app in the beagle main page at [http://beagle-project.org/Supported_Filetypes](http://beagle-project.org/Supported_Filetypes) One of the reasons is that beagle searches through your home directory and does not include hidden folders (those that begin with a dot), and thunderbird emails and contacts are stored within a hidden folder.

---

### Post by iTrendsNET on 2006-07-18
> **jordilin said:**
> If I'm not wrong you'll not be able to search through thunderbird by means of beagle. Thunderbird is not pointed out as a supported app in the beagle main page at [http://beagle-project.org/Supported_Filetypes](http://beagle-project.org/Supported_Filetypes) **One of the reasons is that beagle searches through your home directory and does not include hidden folders (those that begin with a dot)**, and thunderbird emails and contacts are stored within a hidden folder.

I am not sure the above is correct.  Evolution stores mail in a sub-directory of the hidden holder ( .evolution ) in your home directory.  No?  

I have seen various guides as to how to use Beagle to index Thunderbird mail.  Some options are shown here:  

[http://www.antezeta.com/beagle-fedora.html](http://www.antezeta.com/beagle-fedora.html)

I believe there are also posts in Ubuntu Forums on this.  In my opinion, indexing Thunderbird mail should not be too difficult for you to set up using the options in the above link.

Good luck!

---

### Post by jordilin on 2006-07-18
> **iTrendsNET said:**
> I am not sure the above is correct.  Evolution stores mail in a sub-directory of the hidden holder ( .evolution ) in your home directory.  No?  
Good luck!
Yes, that's right, but the folder .evolution, somehow is integrated(supported) in the beagle code. In any case, I'm not sure a 100%. Let's see if someone else has a solution to integrate beagle into thunderbird. Perhaps is a missing feature that will be integrated in a near future.

---

### Post by jordilin on 2006-07-18
> **jordilin said:**
> Perhaps is a missing feature that will be integrated in a near future.
In fact, it will be in a near future. See the following link [http://beagle-project.org/ThunderbirdBackend](http://beagle-project.org/ThunderbirdBackend). It seems that it is a work in progress.

---

### Post by kkubasik on 2006-08-11
Good news! The Thunderbird backend for beagle is no longer a work in progress! It has been committed to CVS, and will be included in the 0.2.8 release of beagle (coming soon!).

---

### Post by matthias_k on 2006-08-11
> **kkubasik said:**
> Good news! The Thunderbird backend for beagle is no longer a work in progress! It has been committed to CVS, and will be included in the 0.2.8 release of beagle (coming soon!).
Uh thank god, thanks for the news!

I hate Evo more with every day I use it. (Does anyone else get random crashes on exit? Or when you do as simple of a task as clicking "new email"?)

Back to TB it is. :)

---

### Post by Dec on 2006-08-12
Did you try this:

[http://www.ubuntuforums.org/showpost.php?p=1351272&postcount=14](http://www.ubuntuforums.org/showpost.php?p=1351272&postcount=14)

---

