---
title: "Wine crashes on audio tab"
date: 2006-04-03
forum: Gaming &amp; Leisure
---

### Post by Mortuis on 2006-04-03
Hey, I'm running Ubuntu 5.10 on a Thinkpad T23.

I am having a problem getting sound to work in Wine.  When I run winecfg and click on the audio tab, the window closes.  Below is what I type and the resulting (what I assume is an) error message.

> john@uriel:~$ winecfg
Creating link /home/john/.kde/socket-uriel.
can't create mcop directory
john@uriel:~$

I've browsed the forum and noticed that people have had this problem before, but it was fixed when they upgraded Wine.  I just ran apt-get upgrade and noticed Wine get upgraded to the latest version, but I am still having the same exact problem.

Can anyone help direct me to figure out how to fix this?  I'm new to Linux so I'm not sure how one goes about troubleshooting the problem.  My sound works, I can play audio files and run games in Cedega, so I think the problem is probably my Wine setup, but I'm not sure how to locate the files and look around for sound settings.

---

### Post by jkeyes0 on 2006-04-03
I had a similar problem, running wine 0.9.6, and I updated to 0.9.10 from winehq, (google it, not sure of the address) by downloading and building the source, then installing from there. I haven't had the problem since.

---

### Post by Mortuis on 2006-04-03
When you built the app, did you just overwrite your current Wine install or did you uninstall Wine first?

Did you have to reinstall your Wine applications after installing the binarys?

---

### Post by goatflyer on 2006-04-03
You don't buld anything, wine distributes ubuntu-compatible .deb files.

Just be sure your sources.list contains 
```

## wine
deb http://wine.sourceforge.net/apt/ binary/

```

run synaptic update and wine will upgrade fine, no uninstall required.

Be sure to re-run winecfg after every update in case any new fields were added.

---

### Post by Mortuis on 2006-04-04
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ is in my sources.list, and I ran synaptic, but I only see a package for 0.9.11.  How do I get synaptic to show me the 0.9.10 package?

---

### Post by Toxicity999 on 2006-04-04
Well I'm on windows right now here at school but simply in one of the toolbar sections theres a 'Force Version...' option open that up after highlighting WINE then choose the version you wish to download. Fairly easy, you may also want to 'lock version' so you dont get buggered with a constant upgrade prompt. (just follow WINE releases as so when the version after 11 comes out you can unlock and try it out!) Good luck with that.

---

### Post by YokoZar on 2006-04-04
[QUOTE=Mortuis]deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ is in my sources.list, and I ran synaptic, but I only see a package for 0.9.11.  How do I get synaptic to show me the 0.9.10 package?[/QUOTE]
It won't, since 0.9.10 is no longer in the repository as it's out of date.

You'll have to download and install it by hand by following the instructions at the bottom of this page:

[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

---

### Post by Mortuis on 2006-04-05
Problem solved, I had a moment of clarity and did
mkdir /home/john/.kde/socket-uriel.
problem is solved, and very obvious looking in retrospect.

Thanks for the help.

---

### Post by Toxicity999 on 2006-04-05
Ah, sorry I was thinking on the level of how most Repos. are run, I forgot entirely about Wine cleaning theirs up so much.

---

