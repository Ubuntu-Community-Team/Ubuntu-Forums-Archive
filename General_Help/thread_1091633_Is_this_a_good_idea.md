---
title: "Is this a good idea?"
date: 2009-03-09
forum: General Help
---

### Post by dodle on 2009-03-09
If I am using Hardy and can't upgrade to Intrepid, is it a good idea to disable Hardy's repository, and add Intrepid's?  I hope so... because I've already done it.

---

### Post by kostkon on 2009-03-09
Actually, no, it's not necessary. The update manager does all these automatically for you during a distribution upgrade. It replaces the repos with the ones of the new version and also before the start of the upgrade process it disables your 3rd party repos.

---

### Post by Woody1987 on 2009-03-09
open up software sources, got to updates. At the bottom choose normal releases in the drop down box. Intrepid should show up now as an option when updating.

---

### Post by hockeyhead019 on 2009-03-09
is there a reason you can't upgrade? because if you don't know how you just > **Woody1987 said:**
> open up software sources, got to updates. At the bottom choose normal releases in the drop down box. Intrepid should show up now as an option when updating.

this way you avoid having to mess with any software sources which could possible complicate things in the future

---

### Post by dodle on 2009-03-09
I can't upgrade because my laptop won't run intrepid.  

Something has gone wrong.  I can't connect to the internet anymore.  I am on my dad's Windows machine now.  My laptop uses the Broadcom B43 wireless driver.  It worked fine until just a little while ago when I updated network-manager, and I thought that I updated b43-fwcutter.  Now I cannot connect via wireless or lan.  According to Synaptic, b43-fwcutter is not installed, and I Cannot connect to install it.  Does anyone have any advice?

---

### Post by dodle on 2009-03-09
I think that I am going to have to do a re-install.  I guess there is a problem with the newest version of gvfs.

---

### Post by hyper_ch on 2009-03-09
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

