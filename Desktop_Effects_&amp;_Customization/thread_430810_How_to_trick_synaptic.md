---
title: "How to trick synaptic?"
date: 2007-05-02
forum: Desktop Effects &amp; Customization
---

### Post by Muppeteer on 2007-05-02
I'm having a problem with 0.3 version of Beryl and i've deleted the 0.3 files from /var/cache/apt/archives but how do i trick synaptic into thinking it's no longer there? It's not letting me install the 0.2.1 or 2.0 version...

I'm pretty sure there's a simple explaination but i can't think of it :)

---

### Post by scanez on 2007-05-02
What do you mean "trick"? What happens when you try to install beryl? Do you still have the repositories for the 0.3 version listed in your sources.list?

---

### Post by Muppeteer on 2007-05-02
Sorry i should have been more clear...

I can't install beryl 2.1 or 2.0. Everytime i click on Emerald to force an install of either version it always reverts back to 3.0. So i removed the deb files but synaptic still thinks the 3.0 files are there. Yes i took out the beryl info from the repos, but 3.0 must be in the feisty repos or something. 

So basically i just need synaptic to forget 3.0 is available and let me install an earilier version...

---

### Post by rolf-c on 2007-05-02
After you edit your Synaptic sources, be sure to click the reload button.

There are no Beryl 3.x repos in Feisty.  Only 0.2.0 and 0.2.1 exist in Feisty.  beryl-project.org does not list any 3.0 edition of Beryl, either.  Not sure where you are finding a 3.0 version but it's not Feisty and it's not beryl-project.

[http://www.beryl-project.org/releases.php](http://www.beryl-project.org/releases.php)

---

### Post by Muppeteer on 2007-05-02
Ya i got it, they were on the same repos as kiba dock :mad: 

Thanks :)

---

