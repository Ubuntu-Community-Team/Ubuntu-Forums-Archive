---
title: "Kde-dialogs in OO.o"
date: 2005-05-16
forum: Desktop Environments
---

### Post by vicks on 2005-05-16
Damn, when i try to make my open office use kde in dialogs, the dialogs keep crashing.  ](*,) I once saw a post about it on the forums but i just can't find it. Anyone knows if there's a workaround?

---

### Post by philipacamaniac on 2005-05-16
I had the same problem, and to fix it, I just moved to OpenOffice.org2, which not only has working KDE dialogues, but uses crystal, and has a KDE look and feel. It seemed to be a little peppier in the speed department, too. Of course, it is a beta, so don't do this in a mission critical production environment.

---

### Post by vicks on 2005-05-16
Ok, i tried that, and it lokks great. Writer hangs when i try to open files though, which makes it a little unpractical  ;-)

---

### Post by philipacamaniac on 2005-05-16
Really? What document format are you opening? I've been able to open old sxw's and Microsoft doc's without problems.

Can you create new documents and open them without problem?

---

### Post by vicks on 2005-05-16
It's when i open swx (created in 1.1) it crashes. Haven't done any extensive testing to be honest, i got so tired of it all that i got rid of 2.0 on the spot. Maybe it was a bit too hasty decision ;)

---

### Post by SanderAnt on 2005-05-16
Liz Young posted this on the mailing list a while back. Works for me  :
It seems I cannot live without the kdefilepicker in OO.o anymore.  Thanks to
the hackers who spoiled me with that ;-).

Here are the changes I made to Kubuntu Hoary to get it working.

-- edit /etc/openoffice/openoffice.conf to read:
export OOO_FORCE_DESKTOP=kde

-- edit ~/.kde/share/config/kdeglobals
add this section (to prevent crashing):
[Development]
AutoCheckAccelerators=false

<http://bugs.kde.org/show_bug.cgi?id=100849>

-- in OO.o Tools>Options>General>Open/Save dialogs:
clear the checkbox next to "Use Openoffice.org dialogs"

---

### Post by vicks on 2005-05-17
Well, will you look at that! It worked, thanks! What did the edit exactly do? Is there any drawbacks?

---

### Post by SanderAnt on 2005-05-18
I'm not sure about any other implications besides the OOo open dialogue. It seems that this is fixed in some version of KDE as per the bug report.

I too would like to start using 2.0, but I can't until the spellchecker works.

---

