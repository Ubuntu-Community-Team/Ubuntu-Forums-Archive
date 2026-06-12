---
title: "tracker-indexer taking up 100% cpu"
date: 2009-04-02
forum: General Help
---

### Post by keithclark on 2009-04-02
tracker-indexer seems to be taking up 100% of my cpu time no matter how long I leave my laptop running.  This causes my laptop to run extremely hot.

Is there a way to either solve this or should can I just uninstall it?

Thanks,

Keith

---

### Post by Sidewinder1 on 2009-04-02
I took a quick gander but couldn't find it. I know there is a way to stop the tracker. Do a search on this forum for Nautilus tracker and I'm sure that you'll find it. Keep in mind that future searches of your drive will take longer but that's a small price to pay for freeing up your processor.
HTH
Side

PS this'll also work as a 'bump' for someone who can give you more specific instructions. :-)

---

### Post by binbash on 2009-04-02
Are you using ubuntu jaunty?If so this is a known bug

---

### Post by keithclark on 2009-04-02
> **binbash said:**
> Are you using ubuntu jaunty?If so this is a known bug

Yes, I'm using 9.04 Beta.  Sorry, I should have mentioned that in my original post.

Thanks for the information.  Appreciated.

Keith

---

### Post by pylorns on 2009-04-25
I just updated to 9.04 non-beta and I'm having this problem.

---

### Post by Didius Falco on 2009-04-26
> **pylorns said:**
> I just updated to 9.04 non-beta and I'm having this problem.

What are your settings in Tracker Indexer Preferences?

---

### Post by wyclif on 2009-04-28
Similar problem here, running 9.04 and Tracker keeps the indexing pop-up from closing.  Annoying.

---

### Post by Charlie91 on 2009-04-30
I have the same problem here.  What I do is to kill three processes (tracker, trackerd and tracker-indexer) using the System-Monitor.  It solves the problem.

How can I automatically kill (or to stop from starting in the first place) these processes?  Which file to edit?:confused:

---

### Post by Wartender on 2009-04-30
i'm having the same problem... except that today this appeared (see picture)
and if i hit ok it just pops up again... over and over and over...
gonna kill the processes for now, anyone know what to do?

---

### Post by DavidTangye on 2009-05-01
There are many posts here all repeating your issue. For a solution see the launchpad bug reports, in this case [this one is good]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/346912") and there are many duplicate reports there too.
I can recommend you search before posting issues, especially [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu), as your answers are often already there, and it saves these forums being filled with 10,000 'me too' issues.

---

### Post by Charlie91 on 2009-05-02
I went to that link and the following was taken from there (tell me is this okay to do?):

[COLOR="RoyalBlue"][Milan wrote on 2009-04-26: (permalink)]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/346912/comments/51")
A few informations to stop these scared comments: :-)
- unchecking 'Enable indexing' in System->Preferences->Search & indexing should be sufficient to stop trackerd, at least after restarting your session if it's hanging

- you can prevent trackerd from starting by going to System->Preferences->Startup Applications, and unchecking the Tracker daemon

- you can always stop trackerd using Alt+F2 and then typing 'killall trackerd', or 'killall trackerd -9' if it's not quitting

- you can completely remove Tracker from your system by removing the tracker package, without any risk for your system

- Tracker was actually installed by default in previous versions, which explains why it may be installed in your box without you doing anything for that. But note that it has always been *disabled* by default.

- there is no 'trackerd' executable in your path, it's in /usr/lib/tracker/trackerd since it's not meant to be started manually

But apart from that, Tracker is a great tool! And, see, it's not so malicious than you may think...[/COLOR]

I'm actually using a non-Ubuntu computer now, but I'll reboot and fix it... :popcorn:

---

