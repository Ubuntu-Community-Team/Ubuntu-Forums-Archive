---
title: "Accidentaly deleted desktop folder"
date: 2011-07-02
forum: Desktop Environments
---

### Post by TheStefan12345 on 2011-07-02
On my Lubuntu desktop, I accidentaly deleted Desktop folder, and now I can't put anything on my desktop, and nothing is on my desktop. What should I do?


Another thing: While Googling I found out that Lubuntu should show me my home folder if I deleted desktop, but that didn't happen.

I need it today because I wont have network tomorrow. Please
Thanks in advance.

---

### Post by SteveDee on 2011-07-02
> **TheStefan12345 said:**
> On my Lubuntu desktop, I accidentaly deleted Desktop folder, and now I can't put anything on my desktop, and nothing is on my desktop....

Have you tried going to the trash can and recovering it?

If that does not work try opening the file manager (PcManFM), going to your user home folder (e.g. /home/steve) and then creating a new folder called "Desktop"

---

### Post by TheStefan12345 on 2011-07-02
> **SteveDee said:**
> Have you tried going to the trash can and recovering it?

If that does not work try opening the file manager (PcManFM), going to your user home folder (e.g. /home/steve) and then creating a new folder called "Desktop"

Making folder desktop didn't work. I use Lubuntu in serbian so the folder was named &#1056;&#1072;&#1076;&#1085;&#1072; &#1055;&#1086;&#1074;&#1088;&#1096;&#1080;&#1085;&#1072;, but that's probably not important.  Afterall, I tried to copy&paste some folder to desktop (on desktop) and it said that I can't paste it there (/home/username/lator/) because it doesn't exist. Indeed, it doesn't exist.

Yes, and about recovering, no, I tried it before.

And why &#8222;lator&#8220; as desktop?

---

### Post by SteveDee on 2011-07-02
> **TheStefan12345 said:**
> ...I use Lubuntu in serbian so the folder was named &#1056;&#1072;&#1076;&#1085;&#1072; &#1055;&#1086;&#1074;&#1088;&#1096;, but that's probably not important.

The actual destop folder name may be very important, as the system my be looking for an exact match.
What about the rubbish bin, did you look in there for the deleted folder? (open PcManFM, "Rubbish" or the Serbian alternative should be listed in the left pane or side bar).

---

### Post by TheStefan12345 on 2011-07-02
> **SteveDee said:**
> The actual destop folder name may be very important, as the system my be looking for an exact match.
What about the rubbish bin, did you look in there for the deleted folder? (open PcManFM, "Rubbish" or the Serbian alternative should be listed in the left pane or side bar).

Yes, I did. I made a massive clean-up, and I then deleted everything from wastebasket. I made 2 directories: Radna Površ and Radna Površina (in cyrillic) because both can be „dektops“. None of them worked.

---

### Post by SteveDee on 2011-07-02
> **TheStefan12345 said:**
> ...both can be „dektops“. None of them worked.

You could try creating a 2nd user account, which I would expect to include a desktop folder. This should help confirm the exact spelling of "desktop" which you could then try with your main account.

---

### Post by TheStefan12345 on 2011-07-02
> **SteveDee said:**
> You could try creating a 2nd user account, which I would expect to include a desktop folder. This should help confirm the exact spelling of "desktop" which you could then try with your main account.

I did that (now), renamed to Radna povr&#353;ina (not Radna Povr&#353;ina) and still it doesn't work, it is still /home/biljana/lator

And logged out.

---

### Post by TheStefan12345 on 2011-07-02
Since Bosnian and Croatian are really similar to Serbian (they just add „j“ in some words) I will change to croatian. Lubuntu will ask me to rename my folders, and I will agree, and since desktop is now written well, it is logical to me that it will automaticaly recognize the desktop folder.

---

### Post by TheStefan12345 on 2011-07-02
> **TheStefan12345 said:**
> Since Bosnian and Croatian are really similar to Serbian (they just add „j“ in some words) I will change to croatian. Lubuntu will ask me to rename my folders, and I will agree, and since desktop is now written well, it is logical to me that it will automaticaly recognize the desktop folder.

Hmmmmmmmmmmmm....

Weird. He didn't ask me to change name of folders. Weird...

---

### Post by TheStefan12345 on 2011-07-02
Edit ~/.config/user-dirs ???

Where says desktop type the location of desktop folder you want


That is the solution

---

### Post by SteveDee on 2011-07-02
There is a bit more info here: [http://wiki.lxde.org/en/PCManFM](http://wiki.lxde.org/en/PCManFM)
...which may helps others with a similar problem.

---

