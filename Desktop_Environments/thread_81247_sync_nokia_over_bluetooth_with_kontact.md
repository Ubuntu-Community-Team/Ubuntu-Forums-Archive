---
title: "sync nokia over bluetooth with kontact?"
date: 2005-10-24
forum: Desktop Environments
---

### Post by ianikeev on 2005-10-24
Hi everybody,

The other question is whether there is a step-by-step description (or not step-by-step) of how to do the subj. I haven't had luck with evolution and multisync so far. Is it at all possible? If yes, then how? Kandy seems to only recongnize those phones connected via cable. I have a Nokia 6600 and it's pretty loaded with info already, but installing windows only for that seems kind of pathetic, not counting the dact that Nokia Suite is plain ugly and i'd have to use Outlook (horrifying).

Best,
Igor

---

### Post by ltmon on 2005-10-24
It can work, but it's not easy.

I would start at [http://kde-bluetooth.sourceforge.net](http://kde-bluetooth.sourceforge.net) as they have fairly good docs.... but it's far from a step-by-step.

Also this thread: [http://ubuntuforums.org/showthread.php?t=39478](http://ubuntuforums.org/showthread.php?t=39478)

L.

---

### Post by ianikeev on 2005-10-24
Thanks a lot! ¨Step-by-step¨ was not a requirement :-)

Igor

---

### Post by ianikeev on 2005-10-24
Ahem, I can now easily send the files from my desktop to the Nokia. On the other hand, when I try to find the device from the konnector it doesn find it. Why? kbtobexclient has no problem with it.

---

### Post by ltmon on 2005-10-24
I'm not sure about nokia internals, as I use a SonyEricsson.

I think the SE uses the "IRMCSync" protocol to sync calendar/addresses, which multisynk can handle.

Your Nokia may use SyncML instead, which I am not as sure about.  I know that the program "kitchensync" has syncml support, but it's a pretty buggy program.  I also found this: [http://www.borowka.net/~maciek/ksyncml/](http://www.borowka.net/~maciek/ksyncml/)

Sorry I can't test any of this out for you, but I don't have a syncml phone.

L.

---

### Post by wish on 2005-12-10
Did any one ever get this working?

---

### Post by justinlawrence on 2008-02-13
i'm keen to get this working as well and am happy to test stuff for anyone. i've installed kandy, but am not sure what to put as the /dev for the bluetooth connection. does anyone know what the device might be?

---

