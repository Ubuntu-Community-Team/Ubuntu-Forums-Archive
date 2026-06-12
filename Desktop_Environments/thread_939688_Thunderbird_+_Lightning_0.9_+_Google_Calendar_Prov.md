---
title: "Thunderbird + Lightning 0.9 + Google Calendar Provider - No write support"
date: 2008-10-06
forum: Desktop Environments
---

### Post by enigma_0Z on 2008-10-06
Back on Hardy, in order to maintain consistency, I've installed Lightning myself and kept it up to date because the development cycle for Lightning seems to be much quicker.

To that end, I also kept up to date with the Google Calendar provider for Lightning...

I recently updated to Hardy and went through the same process (including installing libstdc++5 for lightning to work in the first place). Now, I'm at a point where Lightning works, and I can read from my Google calendar, but I can't read any reminder info, and I can't write anything to the calendar.

I'm just about to install Thunderbird from Mozilla's site instead of Ubuntu's, unless someone has a better idea.

--update--

In the interim, I've posted a bug and downgraded to lightning 0.8 and the appropriate google provider version.

See launchpad bug: [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/278853](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/278853)

---

### Post by iosonofabio on 2008-10-16
Same issue, the solution is here:

[http://forums.mozillazine.org/viewtopic.php?f=46&t=876295](http://forums.mozillazine.org/viewtopic.php?f=46&t=876295)

i.e. you have to install libstdc++5 package. The lastest version now is libstdc++6, so I personally downloaded both versions.

---

### Post by enigma_0Z on 2008-10-16
Found that before posting this thread. installed libstdc++5 and it *got lightning to run* but it doesn't really function at all. See this bug: [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/278853](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/278853)

---

