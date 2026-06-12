---
title: "&quot;optimize&quot; synaptic for dialup?"
date: 2009-04-07
forum: General Help
---

### Post by sir_cheats_a_lot on 2009-04-07
There is one thing that has always bugged me about package managers well.. GUI ones at least.  when you mark a package and its dependencies, it almost always tries downloading all the files at once.    now on a broadband connection this wouldn't be considered an issue at all.  unfortunately, however, not everyone gets that luxury. 

  Since there is such a large number of folks out there with no other option but a dialup connection, i'd like to know if there is a way to force synaptic(or any graphical package manager for that matter) to download ONE file at a time?  suppose worst comes to worst i could go back to basics, and use apt from the command line *shudders*.

 other recent issues with my phone line has only magnified this annoyance then usual.  there is so much line noise right now im getting sub-dialup connect speeds.  all week the best i've managed was 21120 bps.  now imagine my pain as i download a 10MB update consisting of 4 files splitting an average download speed of 2.4 kb/s.  ](*,)

---

### Post by sir_cheats_a_lot on 2009-04-07
hmm... there seems to be a new one in the repos i haven't seen before.  "gnome-apt".  sadly it seems to do the same thing. :(

---

### Post by lisati on 2009-04-07
You might want to talk to your phone company about the quality of the line.
 A year or two back I was getting noise on my phone line, which affected both ADSL and dial-up. One time it was so bad it knocked out my phone service for a few days but I was still able to sporadically get a connection via ADSL - a call from my mobile to the phone company revealed that water had got into the underground cable near my place, and the phone company were working on drying it out. They were even good enough to temporarily divert my landline to my mobile at no charge.

---

### Post by robert shearer on 2009-04-07
If you have access to an adsl connected computer at another location (friends, library, internet cafe) you might want to investigate these applications for downloading there and transfering, on a usb flashdrive, to your computer.

aptoncd (in the repos but needs an ubuntu machine at the other location)

Keryx from here...
[http://keryx.betaserver.org/](http://keryx.betaserver.org/)
This is designed for updating dial-up users from other machines and works on various o/s.

---

### Post by sir_cheats_a_lot on 2009-04-07
> **lisati said:**
> You might want to talk to your phone company about the quality of the line.
 a call from my mobile to the phone company revealed that water had got into the underground cable near my place, and the phone company were working on drying it out.

Our line is only a year old. coincidently, it too is an underground line. i kinda figured that was our likely culprit, but at the moment can't afford to have them come out here for that.

> **robert shearer said:**
> f you have access to an adsl connected computer at another location (friends, library, internet cafe) you might want to investigate these applications for downloading there and transfering, on a usb flashdrive, to your computer.

aptoncd (in the repos but needs an ubuntu machine at the other location)

Keryx from here...
[http://keryx.betaserver.org/](http://keryx.betaserver.org/)
This is designed for updating dial-up users from other machines and works on various o/s. 

yeah i use keryx for my larger downloads(50+ MB), and it works great, when i do have access to someone's DSL connection...which is rare.   was looking more for a way to tweak a package manager to properly utilize my lack of bandwidth for those files i otherwise shouldn't need to go elsewhere to get.(basically anything under 50MB)

---

### Post by sir_cheats_a_lot on 2009-10-06
well, well... it appears that the line to the new box isn't the new line, but rather what was left from when the old line got tore down by the logging company when they came and got the trees a few years ago.  appearently the new phone line runs from the road to the old box, and the old line runs from the old box to the new box.
  bah... such half-***ed work.  I suppose it should be expected from AT&T though, especially after what they did with my brother's DSL the day he DID have service.  in THAT instance they not only hooked up everything backwords(and i had to go fix it), but they also forgot to close the phone box up when they were done, and send a message to the main office to turn the service on for over a week.   I guess i'll have to re-run the cable myself, which i really don't know what i'm doing, since no one else in the house seems to care. 
   the guy from AT&T tried explainning how to do it to my dad. i assume he was drunk durring this process, because he claims not to remember now, even though mom remembers them talking about it.   Anyone else ever have to deal with this?  meh.. don't even know where to begin this project.

---

