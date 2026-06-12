---
title: "Removing unused dependancies? Ontv's deps."
date: 2006-09-28
forum: Desktop Environments
---

### Post by Neobuntu on 2006-09-28
Well, I had a nice clean Kubuntu install and noticed the TV guide type "ontv" program was installable via Adept. Yet It also brought MANY gnome dependantcies and libs.

I had hoped it would work anyway with Kubuntu. It doesn't. It seems it may be for the Gnome panel.

I could remove ontv easy enough but how to I remove the long list of other dependancies to brought with it? They are listed in the details of "ontv" and I think those are what I saw installed.

Am I screwed? Do I have to delete them one by one and hope somthing else doesn't use them (cause they may have been some already installed?)

I don't want to install the full Gnome now; because I want upgrades to go faster. How do I reverse this ontv install; back to where I was?

---

### Post by Neobuntu on 2006-09-28
Please tell me there is a time saving way to remove all the dependances that Adept just installed. There are 30 of them.

I don't think any will be missed.

Can I copy thier names, edit them and paste them in an apt-get remove command? Is that the best way?

---

### Post by aysiu on 2006-09-28
1. Next time use *aptitude* instead of Adept:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

2. Install *deborphan* to isolate and remove "orphaned" dependencies. There's a graphical frontend called *gtkorphan*, but since you don't want Gnome libs...

---

### Post by Neobuntu on 2006-09-28
Thank you very much.

Yes I have heard aptitude many have advantages in this area but I don't know why. I'll read that link next.

I don't mind having minimal Gnome libraies to run Gnome programs (which most work) but this test dindn't work (I think) and it added other; extra Gnome stuff I hadn't needed before.

I just figure if I keep it lean (now that I favor KDE,) the upgrades will go faster and smoother. SSL just updated now.

Thanks again. 

Please, if anyone can add more, please do so.

---

### Post by Neobuntu on 2006-09-28
All right. does this mean one can ```
sudo apt-get remove ontv
``` knowing this will leave those 30 problem dependances and then just ```
sudo aptitude update
``````
sudo aptitude install ontv
``` again (but with aptitude now) and then ```
sudo aptitude remove ontv
``` and it will also then remove my 30 unused dependances with it? Because now, I did install (and then removed) with Aptitude. Plus will this also leave any of those 30 ontv dependancies that might (by chance) be used by some past package I don't know about (AKA they were already an install dependacy of another past package install.)

Sounds logical and makes sense to me. What's the verdict? If true, this is an easy fix and good to know.

It didn't work.

OK so until I remove dependacies left from apt-get install; with gtkorphan manually, aptitude skips over the install of them (there there already) and therefore also, will NOT neatly remove what it (Aptitude) did not install (dang it.)

---

### Post by aysiu on 2006-09-28
No. In order for the removal in *aptitude* to work, you have to **update** and **install** with *aptitude* first.

```
sudo aptitude update
sudo aptitude install ontv
``` and then later ```
sudo aptitude remove ontv
``` What you need to do right now is ```
sudo aptitude update
sudo aptitude install gtkorphan
gtkorphan
``` and then remove the stranded libs. If you want, too, you can do ```
sudo aptitude remove gtkorphan
```

---

### Post by Neobuntu on 2006-09-28
Yes, update was implied (in my head :P) I did it first and as you said my idea did not work anyway.

Also I had already followed your advice (thank you) and got gtkorphan (dpendences accepted) and it's great.

I'm a little shy about what it's telling me and which are OK to remove but I'm getting there.

Hey, why doesn't Adept, Synaptic, or the others use Aptitude (or it's methods) to remove unused dependancies with the main package you are removing (if it leaves one used by something else?)

---

### Post by aysiu on 2006-09-28
I don't know why. Adept and Synaptic are front-ends for *apt-get*. People have asked numerous times why they don't have *aptitude*'s functionality.

Rumor has it the Ubuntu developers are working on something called SMART Package Manager. Not sure what that does exactly.

---

### Post by Neobuntu on 2006-09-28
Cool. That is the way.

You've been exeeding patient and helpful and I thank you Aysiu.

---

### Post by aysiu on 2006-09-28
You're welcome. Go and do likewise.

---

