---
title: "Help Me! Tinkering With .deb Packages!"
date: 2005-12-19
forum: General Help
---

### Post by Rev. Nathan on 2005-12-19
Oh, crap. I just ran into the biggest trouble. I wanted to try KMobileTools, which required updated versions of some lib packages. So from us.debian.org, I downloaded the packages, and two installed fine. Ignoring the last one, I tried to install KMobileTools, but failed. Ignoring the packages I installed, I later in the day tried to download a .deb update of totem, which ran into install conflicts as well. But it installed regardless!

Now opening up Syaptic, I see all three packages I downloaded today are broken! What's worse, is when I try to remove any of them, I'd remove my entire computer!

[IMG]http://www.bigrevmedia.com/coronets/Screenshot-Synaptic%20Package%20Manager%20.png[/IMG]
[IMG]http://www.bigrevmedia.com/coronets/Screenshot-synaptic.png[/IMG]

This is ultimately annoying; I'm 'frozen'. I can't upgrade my system whatsoever, now. Is there a way to backtrack to a time before? I'm willing to give up any modifications I did after these installs.

Help?

---

### Post by shakin on 2005-12-19
You can downgrade those packages to the normal Ubuntu versions by going to Package -> Force Version. The Ubuntu versions will be marked as such. Downgrading the the proper version is definitely the way to go. You can compile KMobileTools from source (install using checkinstall) to build it agains your library versions.

---

### Post by Rev. Nathan on 2005-12-19
[QUOTE=shakin]You can downgrade those packages to the normal Ubuntu versions by going to Package -> Force Version. The Ubuntu versions will be marked as such. Downgrading the the proper version is definitely the way to go. You can compile KMobileTools from source (install using checkinstall) to build it agains your library versions.[/QUOTE]
I just checked that, and again it wants to uninstall a bunch of things, as seen in that error message in the first post. Is there another solution?

Also, I could never find anywhere or anyone to teach me to compile and install source tarballs; is there a tutorial where I can learn it?

---

### Post by Rev. Nathan on 2005-12-19
Can anyone help me? Is there a way to just backtrack to an earlier date or something simple?

---

### Post by Rev. Nathan on 2005-12-19
Damn, if no one can help me, should I just reformat? I'll do that if I don't get an answer by Midnight / 8:00AM UTC

---

### Post by nekr0z on 2006-04-30
Sorry for offtopic, but shakin, if you please, tell me how to install kmobiletools so that the goddamn thing works! I nearly gave up now...

---

### Post by Ramses de Norre on 2006-04-30
Can you download the needed lib's from [here]("http://packages.ubuntu.com/breezy/") and install them with dpkg?

---

### Post by nekr0z on 2006-04-30
[QUOTE=Ramses de Norre]Can you download the needed lib's from [here]("http://packages.ubuntu.com/breezy/") and install them with dpkg?[/QUOTE]
I suppose, the answer is NO, since all the listed files are also in repositories, and the repositories are of a little (honestly: of no) help here.

---

### Post by Ramses de Norre on 2006-04-30
[QUOTE=nekr0z]I suppose, the answer is NO, since all the listed files are also in repositories, and the repositories are of a little (honestly: of no) help here.[/QUOTE]
It was a sugestion for the topic starter. 
He should be able to replace the debian libraries with the original ubuntu ones.

---

### Post by nekr0z on 2006-04-30
[QUOTE=Ramses de Norre]It was a sugestion for the topic starter. 
He should be able to replace the debian libraries with the original ubuntu ones.[/QUOTE]
First: hey, that message was dated December. I suppose he has already managed the problem.
Second: I still don't see the way it can help. The most annoying thing about the *.deb system is that the dependencies are on packages, not on libraries. There could be the same library in another ubuntu package, or even in the same package with different name, and the whole thing comes to crash.

For example, let us say there is a program "*coolprog*" that needs a library "*nicelib*". This library is included in the package "*finelibs*". That's in Debian.

In Ubuntu there's no *coolprog* in repositories, and there's no *finelibs* as well. But there's a *nicelib* included in another package, say, "*libniceandstuff*". You try to install a *coolprog.deb*, and it says there's an unsolvable dependency. Then you force it to install with dpkg -f. And the thing WORKS, because you have *nicelib* installed in your system.

But the PACKAGE *finelibs* is not installed (and it is actually NOT NEEDED, since you have the necessary LIBRARY already). The stupid apt-get wants only *finelibs* and nothing else, and refuses to do anything at all until you uninstall the *coolprog*...

---

### Post by Ramses de Norre on 2006-04-30
I should have watched the dates.. sorry.

---

