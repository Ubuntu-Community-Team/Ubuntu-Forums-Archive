---
title: "[SOLVED] How do I find my Mobile Phone's /dev/ path"
date: 2008-12-07
forum: General Help
---

### Post by KenBW2 on 2008-12-07
I'm trying to use one of a few applications (Gnome Phone Manager, BitPim, Kmobiletools) to sync up with or just get info from my Sony Ericsson mobile phone via USB connection.
All the apps ask for the path where my phone is (usually giving /dev/ttyxx as an example).
How do I find this path?

PS: am i to put my phone in "File Transfer Mode" or "Phone Mode"?

---

### Post by change_mode on 2008-12-07
My mobile is mounted to /media/disk

It should be in /media, like CDs and DVDs.

---

### Post by KenBW2 on 2008-12-07
I'm not asking about the memory card - that mounts to /media/PHONE CARD. I'm looking for the path the above apps are asking for

---

### Post by ndefontenay on 2008-12-07
Hi.

I have had the same probably recently.

You should find what you want in this thread:

[http://ubuntuforums.org/showthread.php?t=997426](http://ubuntuforums.org/showthread.php?t=997426)

I'm planning to do an how to of this. It seems there's very few knowledge on that.

Wammu worked well for me. It could retrieve my contact but pretty much every other features were not supported.

Phone manager was a bit crappy. There's still some way to go but I'm happy enough to be able to synch my cellphone.

Try plugging your cellphone at the back of your computer rather than in the front. Wammu should propose the device to you rather than you telling him where it is.

Nico

---

### Post by change_mode on 2008-12-07
> **KenBW2 said:**
> I'm not asking about the memory card - that mounts to /media/PHONE CARD. I'm looking for the path the above apps are asking for

When I connect my mobile, both the memory card and the phone memory are mounted there. The card is in an extra folder. Sorry if it didn't help for you.

---

### Post by KenBW2 on 2008-12-07
Thanks for the help, got it working with Wammu :). Tried putting the /dev/ path into bitpim with no luck, but that's less of a priority now.
Again, thanks.

---

