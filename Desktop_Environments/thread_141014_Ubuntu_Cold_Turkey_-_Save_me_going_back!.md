---
title: "Ubuntu Cold Turkey - Save me going back!"
date: 2006-03-07
forum: Desktop Environments
---

### Post by SAGuy on 2006-03-07
Hello,

This last weekend end I ended my relationship with MS Windows cold turkey but alas I am having 2 problems that are making me want to revisit this decision.

1) My "add applications" does not work. It seems to start to install the particular program and then just stop and not have installed it. I mentioned this on another thread and a few other people are having the same problem. Is there a solution or do I have to reinstall Ubuntu (not this all over again)

2) I upgraded to Firefox 1.5 and have found it to be quite unstable (admittedly with 10 tabs open but I had more than that open when I was using XP and there were no probs)

Any help would be appreciated. As a South African you can understand why I am very keen to continue using Ubuntu! ;) 

Kind Regards,

SAGuy

---

### Post by evilgold on 2006-03-07
What are you using to add applications? Have you tried using synaptic, or apt-get?
Also what program(s)
 are you trying to install, not all programs show up on the gnome menu automatically.

As for firefox, I havnt found it unstable, but you could always downgrade to 1.07 or try an alternative browser like epiphany or konqueror.

---

### Post by superm1 on 2006-03-07
Did you do an expert install?  If so, /etc/sudoers isn't set up the same way as the "regular" install.  That would probably be why your Add Applications (which normally runs with gksudo) isn't working.

How did you go about getting FF 1.5?  a deb, a mozilla.org d/l, etc?

---

### Post by SAGuy on 2006-03-08
superm1,

How would I know if I did an expert install? Is it possible to totally reinstall Ubuntu on my Ubuntu partition - then I can make sure that I use the correct install. Would I have to format something.

---

### Post by SAGuy on 2006-03-08
I am using the Add Application button that appears in the Applications menu bar. I have tried that Synaptics Package manager and that does seem to work although I don't know how to really use that to add full applications. The thing is that I really like the way the "Add Applications" allows you to choose which program and then puts it directly into your toolbar (well it is supposed to anyway!)

---

### Post by WelterPelter on 2006-03-08
[QUOTE=SAGuy]I am using the Add Application button that appears in the Applications menu bar. I have tried that Synaptics Package manager and that does seem to work although I don't know how to really use that to add full applications. The thing is that I really like the way the "Add Applications" allows you to choose which program and then puts it directly into your toolbar (well it is supposed to anyway!)[/QUOTE]

Synaptic will do exactly the same thing. Simply select a package (it will say "Mark for Installation"). Then go to the toolbar and select "Apply." That will do the trick. Once the package is installed, you will see it in your toolbar (although you may have to search for which heading it's under). 

Don't give up. I know how frustrating this can be at first. If you stick it out, you'll be happy you did. :-D

---

### Post by az on 2006-03-08
How did you install firefox 1.5?  My thought is that may have borked your package system.

What happens when you type

sudo apt-get -f install

from a terminal?  Show the output.

---

### Post by bailout on 2006-03-08
Your firefox problem is easily solved. Install Opera :D

---

### Post by SAGuy on 2006-03-12
Sorry for the late response but was away.

I think you may be onto something. The output of the sudo apt-get -f install is:

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

Also another thing, Ubuntu today told me that there were some upgrade available and when I clicked install the same thing happened as before. It just stops half-way through.

Any ideas?

Could I just reinstall Ubuntu (I've only had it for 1 week anyway) over the old one? Do I need to format then?

---

