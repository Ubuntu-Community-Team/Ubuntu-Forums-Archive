---
title: "Trevino Repository on Gutsy?"
date: 2007-09-22
forum: Desktop Effects &amp; Customization
---

### Post by Martje_001 on 2007-09-22
Hi,
Does somebody know how to add all the plugins / effects from the Trevino Repository to Gutsy? Thank you!

---

### Post by hyperair on 2007-09-22
Nope, not Gutsy. It just won't work. Besides you already have the Compiz Fusion packages in Gutsy.

---

### Post by petit.padavoine on 2007-09-22
> **hyperair said:**
> Besides you already have the Compiz Fusion packages in Gutsy.

yes, but not the latest & greatest git version.

As for getting the bleeding edge on Gutsy, you'll have to compile from source i think.

---

### Post by FuturePilot on 2007-09-22
I hope he makes a repo for Gutsy, because he added in a custom hack so you can use the --use-copy option which helps for the black window bug. I know Nvidia fixed that bug with their latest driver, but us Nvidia legacy people are stuck with that bug for now. The CF in Gutsy doesn't have the --use-copy available.

---

### Post by Martje_001 on 2007-09-23
Allright.. I think I use the Gutsy repos then..

---

### Post by hyperair on 2007-09-23
I remember there was an opencompositing.org thread on how to remove the black window bug. I tried it, and I've never seen a black window bug since. I'm using the 9639 driver. Also... when Gutsy is released, Trevino will probably make a repo for it. He did for Feisty shortly after it was released.

---

### Post by hyperair on 2007-11-08
Well now that Gutsy has been released, I still don't see a Trevino repository! =(

---

### Post by djrobthaman on 2007-11-09
Yeah, when's that gonna happen?  Impatiently waiting for a gutsy repo from trevino :)

---

### Post by hyperair on 2007-11-09
Same here. Has Trevino gone on holiday? On a side note, is there an APT repository I can get to install the latest stable?

---

### Post by nikoPSK on 2007-11-13
that sucks, anyone know a way i can install 0.6.0. as an update? (add it to my repos???)

---

### Post by hyperair on 2007-11-14
Nope none so far. I've been searching Google. I reckon it is possible to compile debs for the stable from source. I'll try it out when my CPU has free time, and upload the debs if I succeed =)

---

### Post by nikoPSK on 2007-11-14
> **hyperair said:**
> Nope none so far. I've been searching Google. I reckon it is possible to compile debs for the stable from source. I'll try it out when my CPU has free time, and upload the debs if I succeed =)

That'd be wonderful!

---

### Post by hyperair on 2007-11-24
I'd like to mention that Compiz Fusion 0.6.2 stable has been backported to Gutsy! I've just tried it out today, and it works great. ^^

Looks like I gotta delete the debs I created.

---

### Post by Götz on 2007-11-29
Where is Treviño gutsy repo??

Anybody knows why he hasn't made a gutsy repo?

---

### Post by hyperair on 2007-11-29
No idea. But one thing's for certain, it's not easy to build from GIT. There are these libx11-xcb dependencies, and Gutsy doesn't have them.

---

### Post by nikoPSK on 2007-11-29
that's way too bad, but other places have other things. I like the repository of shame;)

---

### Post by Radon on 2007-11-29
Don't worry, I guess he just wants to show us how dependant we are on his contribution to the community [-X :)

---

### Post by nikoPSK on 2007-11-29
not really, I think hes lazy (j/k) ;). He's helped us alot, but I do hope for a gutsy repo.

---

### Post by Götz on 2007-11-30
> **nikoPSK said:**
> that's way too bad, but other places have other things. I like the repository of shame;)

Isn't the repository of shame for Debian?

Can I use it also for Gutsy without problems?

---

### Post by nikoPSK on 2007-11-30
ubuntu is built on debian. And debs are debian too. So.....

---

### Post by hyperair on 2007-11-30
They may and may not work. You could always try them out. Then come back and tell us how it goes. =P

---

### Post by Götz on 2007-12-01
Now I'm using this Compiz Fusion repository for Gutsy, I recoment it!

[http://kwatrow.nl/repo](http://kwatrow.nl/repo)

---

### Post by exactopposite on 2007-12-01
> **Götz said:**
> Now I'm using this Compiz Fusion repository for Gutsy, I recoment it!

[http://kwatrow.nl/repo](http://kwatrow.nl/repo)

thanks for this

---

### Post by SunnyRabbiera on 2007-12-01
> **nikoPSK said:**
> ubuntu is built on debian. And debs are debian too. So.....

woa wait, you have to be careful here as this can bork your system.
never assume anything

---

### Post by hyperair on 2007-12-01
Hmm.. Is this safe?

---

### Post by nikoPSK on 2007-12-01
> **SunnyRabbiera said:**
> woa wait, you have to be careful here as this can bork your system.
never assume anything
hmm, okay. Well, I didn't have any problems with the repo of shame....

---

### Post by Gourgi on 2007-12-03
> **nikoPSK said:**
> hmm, okay. Well, I didn't have any problems with the repo of shame....

i just installed compiz & extra plugins 
everythings goes fine so far 
:)

---

### Post by imoatama on 2007-12-06
nikoPSK: What shame repo did you use? Sid Lenny or Etch & Stable/Unstable? What version of compiz did it upgrade to?

---

### Post by nikoPSK on 2007-12-07
0,6,0, I don't use it anymore though....

---

### Post by hyperair on 2007-12-09
I just compiled some Compiz Fusion debs using Trevino's makefusiondebs script! =P Who's willing to test them out for me?

I'm uploading them to mediafire.com right now, so be patient. I'll post the link when I'm done. The file is called fusiondebs.tar.bz2, and the MD5 checksum is: 8d62cd5a95e1b83a2400b85bb2ea257b

EDIT: Link is here: [http://www.mediafire.com/?81hk09e9j0o](http://www.mediafire.com/?81hk09e9j0o)
EDIT: I'm currently using the debs I've made. Works fine. I'm also looking for a place I can use to host an APT repository. Currently I'm hosting on localhost, but I can't keep my computer on all the time so I can't post the link here for people to use. If anybody can recommend me a place where I can host the debs I will be grateful. On a side note Trevino's makefusiondebs script doesn't provide for creation of sources so I can't figure out how to do a deb-src on the repo.

---

### Post by djrobthaman on 2008-02-14
> **Götz said:**
> Now I'm using this Compiz Fusion repository for Gutsy, I recoment it!

[http://kwatrow.nl/repo](http://kwatrow.nl/repo)

I tried using this one yesterday, upgraded to all the new packages and compiz slapped me in the face.  All my windows borders disappeared and none of the compiz decorations worked.  (Funnily enough, the avant dock I have seemed to work after executing compiz --replace)

I have seen in a how-to a while back talking about switching from trevino's repo to aramanth's where they said you had to fully uninstall all files associated with the previous compiz (sudo apt-get purge compiz* or something like that) before installing the files from the new repo.  Do I need to do that?

I notice a couple of you earlier posters say that the repos work fine for you.  Did you have to something like that to get it working?

---

### Post by ThaRabbit on 2008-03-13
> **djrobthaman said:**
> I tried using this one yesterday, upgraded to all the new packages and compiz slapped me in the face.  All my windows borders disappeared and none of the compiz decorations worked.  (Funnily enough, the avant dock I have seemed to work after executing compiz --replace)

I have seen in a how-to a while back talking about switching from trevino's repo to aramanth's where they said you had to fully uninstall all files associated with the previous compiz (sudo apt-get purge compiz* or something like that) before installing the files from the new repo.  Do I need to do that?

I notice a couple of you earlier posters say that the repos work fine for you.  Did you have to something like that to get it working?

Could be emerald not playing nice with the newer (non ubuntu 7.10 tested) compiz...

---

