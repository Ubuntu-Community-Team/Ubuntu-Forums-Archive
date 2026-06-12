---
title: "Calendar, Mail and Browser which integrate well with Gnome"
date: 2005-12-30
forum: Desktop Environments
---

### Post by Nailor on 2005-12-30
I'm having a problem with daily software I use. Normally, I use Firefox to browse the web, Thunderbird to read mails and Sunbird to keep my calendar organized. The problem is that any of these is not really well integrated to Gnome dekstop enviroinment.

Neither is any of these capable to use some sort of keychain software, for example Revelation. And neither do these work well together. Evolution is one solution, but it's too corporate-oriented software and too bloated. The two major things that made me to consider using Evolution were good integration with Gnome Calendar (the one in panel) and Beagle capabilities to search through the mails.

So, any suggestions for calendar, mail and browsing? If you ever have used Mac OS X, the way the things are done there is the one I'm searching (and I'm not getting a Mac :). Three different softwares, every one of them simple enough with all the necessary features and good integration with desktop system.

- Jyrki

---

### Post by magnusbb on 2005-12-30
My solution would be Epiphany or Galeon (they're going to merge soon, though) for perfect integration with GNOME. But, I have to say, that Firefox works great here. Apart from its memory consumption, it integrates well.

Alternatives to Evolution that fits into GNOME... well, I can't think of any. There's one called Sylpheed ([http://sylpheed.good-day.net/en/](http://sylpheed.good-day.net/en/)) which uses the GTK+ toolkit, but I don't know anything else about it. I've heard it is decent, though.

---

### Post by Nailor on 2005-12-30
[QUOTE=magnusbb]My solution would be Epiphany or Galeon (they're going to merge soon, though) for perfect integration with GNOME. But, I have to say, that Firefox works great here. Apart from its memory consumption, it integrates well.
[/QUOTE]

Well, Firefox integrates quite well, but I'd like to see a possibility to use Gnome Keyring/Revelation/whatever with it as with all. I guess it's a no go anyway, at least for a few versions.

One thing with Sunbird/any other calendar software would be nice to have: the integration with Gnome Calendar so that I could see my appointments etc. clicking the clock in panel. Maybe I should start figuring out how to make extensions to Sunbird and hack it to work with the Gnome Calendar :)

---

### Post by simohell on 2005-12-30
If you want Firefox and Thunderbird to look a bit more gnomish, you can quite easily install gnome themes to both of them. The themes should be in the pages where links in the programs point to (Firefox: Tools --> Themes -->Get More Themes). You can also check out [http://www.deviantart.com](http://www.deviantart.com).

I don't like evolution I have to say. It is a bit too much like Outlook. What I would like is a simple but customisable calendar software, but SunBird isn't quite there yet. I've been trying to use it, but nowdays I mostly rely on my mobile phone to keep me up to date with alarms and reminders and the good old paper version for the rest.

---

### Post by simohell on 2005-12-30
[QUOTE=Nailor]
One thing with Sunbird/any other calendar software would be nice to have: the integration with Gnome Calendar so that I could see my appointments etc. clicking the clock in panel. Maybe I should start figuring out how to make extensions to Sunbird and hack it to work with the Gnome Calendar :)[/QUOTE]

This is something I would really like to see happening.

---

### Post by Bou on 2005-12-30
[QUOTE=Nailor]One thing with Sunbird/any other calendar software would be nice to have: the integration with Gnome Calendar[/QUOTE]

If this could be done, I would drop Evolution in favour of Sunbird, too.

BTW is it anywhere to be found in the repos, or it has to be compiled?

---

### Post by Nailor on 2005-12-30
[QUOTE=Bou]If this could be done, I would drop Evolution in favour of Sunbird, too.

BTW is it anywhere to be found in the repos, or it has to be compiled?[/QUOTE]

I untarred the tar package available from mozilla.org to /opt/sunbird and made symlinks (ln -s) to /usr/bin. Works out of the box just fine.

---

### Post by Bou on 2005-12-30
Thanks a bunch.

---

### Post by foolosophy on 2006-02-21
Do you know how can I tweak Gnome's context menu option "Send to.."? From it I used to send attachments through Evolution. But I migrated to Sylpheed, because it uses only 10% RAM compared to Evo. To attach something to Sylpheed one can use the command "sylpheed --attach X". Is it possible to integrate somehow?

---

