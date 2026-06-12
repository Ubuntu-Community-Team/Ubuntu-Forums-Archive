---
title: "Flash Video Problems in Jaunty"
date: 2009-04-24
forum: General Help
---

### Post by FFGANDALF on 2009-04-24
I've been trying to watch some videos online(mostly Hulu and other sites)
Hulu Doesn't appear to load at all, and the only site I found that I could get streaming to work at all stutters about every five seconds.

None of this happened before I upgraded to Jaunty.

---

### Post by RichardLinx on 2009-04-24
Do Youtube videos work fine? If they don't then this fix seems to work quite well:

```
sudo aptitude purge flashplugin-nonfree
```
```
sudo aptitude install flashplugin-nonfree
```

You might also be missing some of the required codecs to play the videos on Hulu (Not 100% sure since I don't use Hulu and it's a bit hard to check on dialup)

If that is the case you can fix it by running the command:
```
sudo apt-get install ubuntu-restricted-extras
```

Good luck! And in the future don't be to afraid to try a simple search. I'm sure the answer is already out there.;)

---

### Post by Kinger23 on 2009-04-24
to add to this, when I go to the Adobe flash site and open the .deb file to upgrade Flash, I get a message stating that "only one pkg manager can run at a time" and i need to choose b/t aptitude and synaptic. 

Can't figure out who to do this.


Any advice?

[COLOR="Red"]Update:
Figured it out, which isn't saying much lol. One of the things that was screwing me up was that when I punched "flash" into the search slot of Synaptec, nothing was coming up. Once I opened Quick Search and ran "flash" it cam up and I selected the Flash Plug-In Installer and every thing was good to go.[/COLOR]

---

### Post by bc90021 on 2009-04-24
You could also try:

sudo aptitude purge flashplugin-installer

Restart Firefox, and go to a site that has Flash.

FF will prompt you to "Install Missing Plugins" - follow the prompts.

---

### Post by CRIMPS on 2009-04-24
yeah, I had the same problem.  My Jaunty update just finished.  When I load a page that needs flash I am prompted to install missing pluggins.  However, they show as being installed already.

So, I took RichardLinx' advice and just reinstalled the Flash Pluggin.  This seemed to do the work.

Strange, but it worked.  

Thanks
Z

---

### Post by FFGANDALF on 2009-04-25
thanks for the ideas so far. Unfortunately none of them have solved my problem. If it helps one of the sites that doesn't work(besides hulu) is youtube.

---

### Post by binary10 on 2009-04-25
I had the same problem - but like as above I completely removed (purged) the  flashplugin-installer and installed.

Here's a grep of /var/log/dpkg.log of mine broken and that got mine working..

jsecx25:~/$ grep flash /var/log/dpkg.log | grep -e remove -e ' install ' -e ' purge '
2009-04-24 23:24:47 install flashplugin-installer <none> 10.0.22.87ubuntu2
2009-04-25 01:08:37 remove flashplugin-nonfree 10.0.22.87ubuntu2 10.0.22.87ubuntu2
2009-04-25 01:08:37 remove flashplugin-installer 10.0.22.87ubuntu2 10.0.22.87ubuntu2
2009-04-25 01:08:38 purge flashplugin-installer 10.0.22.87ubuntu2 10.0.22.87ubuntu2
2009-04-25 01:09:18 install flashplugin-installer <none> 10.0.22.87ubuntu2
2009-04-25 01:09:19 install flashplugin-nonfree <none> 10.0.22.87ubuntu2
jsecx25:~/$

---

