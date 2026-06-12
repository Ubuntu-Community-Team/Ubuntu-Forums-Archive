---
title: "Requires installation of untrusted packages"
date: 2012-06-04
forum: Desktop Environments
---

### Post by JasonFWard on 2012-06-04
My system says it needs to update.

When I run the update it barfs saying "Requires installation of untrusted packages"

I also noticed when looking at what its "updating" that its actually attempting to install the entire KDE desktop system.  Which is strange as I've never had KDE anywhere near this computer.

What can I do?

---

### Post by JasonFWard on 2012-06-05
Hello?

Anyone?

---

### Post by zombifier25 on 2012-06-05
Did you add any PPA recently?

---

### Post by prismctg on 2012-06-05
Try this : [http://www.webupd8.org/2010/05/automatically-import-all-missing.html]("http://www.webupd8.org/2010/05/automatically-import-all-missing.html")

---

### Post by oldos2er on 2012-06-05
> **JasonFWard said:**
> What can I do?

Run ```
sudo apt-get update
``` in a terminal and post the output here.

---

### Post by JasonFWard on 2012-06-05
> **zombifier25 said:**
> Did you add any PPA recently?Not in many weeks.

> **prismctg said:**
> Try this : [http://www.webupd8.org/2010/05/automatically-import-all-missing.html]("http://www.webupd8.org/2010/05/automatically-import-all-missing.html")I'm not sure how this is relevant, I'm not trying to add a PPA, nor have I added one recently.

> **oldos2er said:**
> Run ```
sudo apt-get update
``` in a terminal and post the output here.Thanks, rather long so I put [here](http://pastebin.com/FVEiUNjH)

I thought my [APT Sources](http://pastebin.com/mKTfxaVt) might be relevant also.

---

### Post by oldos2er on 2012-06-05
You can use code tags to contain any large terminal output in your posts, [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

Is there nothing after "Reading package lists" ? Usually if you're missing a gpg key you'll see a NO_PUBKEY warning followed by the repository that's missing its key.

---

### Post by JasonFWard on 2012-06-06
What you see is what I get I'm afriad.

However, I ran the update again last night and this time it worked.

:confused:

I'm also going to look into why so much of KDE is installed on my system.

---

### Post by zombifier25 on 2012-06-06
You may have installed some KDE apps, which uses a lot of really tiny libraries. The overall size is rather small.

---

