---
title: "Sound Failures in Hardy Heron"
date: 2009-01-31
forum: General Help
---

### Post by bigbrovar on 2009-01-31
I get this problem on ubuntu hardy heron where My sound will suddenly stop working and will only work again with a system restart. i cant seem to recreate the problem .. and AFAIK never use to happen before although a friend of mine always experience it on his laptop. it can be really frustrating and even embarrassed me once when i was to play an audio file for my Boss at work
also when this happens i find it hard to do a proper restart not that the system would freeze or anything.. but clicking the restart button just doesnt work unless i do a hard restart or i kill x and start from gdm .All of these problems are post Hardy Heron installation. i would really appreciate if someone can help with this

---

### Post by bigbrovar on 2009-01-31
i was able to track the problem to pulse audio failing ..  [http://jeffreystedfast.blogspot.com/2008/07/more-pulseaudio-problems.html](http://jeffreystedfast.blogspot.com/2008/07/more-pulseaudio-problems.html)

the only way out after this happens is to reboot the system which is just unacceptable with linux.. i mean linux should just work and even if it doesnt one should be able to fix the problem with out having to restart. NO Application should even hold the system to ransom. (when Pulse audio crashes and this happens most gnome apps would freeze because of their inability to use sound.. you wont even be able to logout) pulse Audio is NOT ripe for prime time.. and shiping it is a IMHO a big mistake for any distro that target the average joe. i am yet to see the advantages it has over alsa.. so why ship it .. look at network manager 0.7 everybody was happy with it. why it was a major improvement, and the advantages it has over 0.6 are obvious for all to see. Not so with Pulse Audio .. some of the biggest problems with ubuntu desktop is Pulse related and that is just not acceptable.

---

