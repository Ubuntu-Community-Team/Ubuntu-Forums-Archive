---
title: "Installed dictionaries not showing up in Evolution"
date: 2006-03-24
forum: Desktop Environments
---

### Post by achim_59 on 2006-03-24
I recently upgraded from "Hoary" to "Breezy" and added a number of new packages while I was at it. For the most part everything worked well, but then I noticed that when I wrote emails in German almost everything was marked as misspelled. (This was also the case for OpenOffice.org Writer.) I checked the composer preferences and found that only the English dictionaries were listed. Next step was to check the installed language support in Synaptic and sure enough, the German dictionary and package material is all there (I've listed it all below). I did notice that Synaptic complained about certain "Hoary" directories not being there, but that didn't happen last time and I didN't take note of the exact error message (Woops! The price of impatience, I guess).

Next I checked System>Administration>Language Selector. There I noticed that German was not selcted (neither translations nor writing aids). Never one to dally, I promptly selected them. As I recall there was bit of installation work that took place, then I rechecked the composer preferences in Evolution... the German (and Spanish) dictionaries were there! I selected them and all seemed to be well with the world again. (OpenOffice.org Writer was also fixed so that I could write German documents, too.)

A week later I shut the machine down. (Went away a couple of days to CeBIT.) When I restarted, the spell checking problem with Evolution was back. (Oddly enough OOo Writer is fine!) Once again only the English dictionaries are available. I've done all the checks described above and nothing seems to be wrong. The only difference is that Synaptic no longer complains about the missing "Hoary" files. Incidently... yes I did do the second reboot when I did the upgrade, so if anybody's thinking that might be the problem, then I'll have to disappoint you... a shame it isn't that simple, huh?

The language/dictionary packages I have installed are:
libmyspell3c2 (1:3.1-14)
myspell-de-at,ch,de (all 3 versions are 20030222-7)
aspell-de (0.50.2-2) ... not sure if that one is relevant
language.pack-de + base (20051011) also not sure if that is relevant

I have searched all other posts for "Evolution" + "Dictionary" and this particular problem doesn't seem to appear. It suggests to me that I'm doing something wrong, but I cannot figure out what it is. Anybody have any ideas?

Achim

](*,)   <-- This little fellow displays how I feel about this problem.

---

### Post by achim_59 on 2006-03-29
Some additional information... The warning messages from Synaptic are back! Here's what it says:

W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)

I'm not certain what the term "stat" means in this context, but it doesn't seem particularly relevant to the issue... If anybody thinks otherwise, please let me know.

Achim

---

### Post by dcstar on 2006-03-30
[QUOTE=achim_59]Some additional information... The warning messages from Synaptic are back! Here's what it says:

W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) **hoary**-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_**hoary**-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) **hoary**-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_**hoary**-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)

I'm not certain what the term "stat" means in this context, but it doesn't seem particularly relevant to the issue... If anybody thinks otherwise, please let me know.

Achim[/QUOTE]
You must go into Synaptic and manually change all your Repository entries from Hoary to Breezy.

---

### Post by achim_59 on 2006-03-30
[QUOTE=dcstar]You must go into Synaptic and manually change all your Repository entries from Hoary to Breezy.[/QUOTE]

Thanks for the tip. I did that and Synaptic is happy now. ;) 

However it hasn't helped to solve my problem. Infact I've reinstalled a number of packages, but that acheived zilch. I've been scouring the Ubuntu forums for most of an entire day (though I really should be doing other things) and still found nothing that's really relevant. Last night I went through the gconf files in my home folder. The only one that seemed relevant was ~/.gconf/GNOME/Spell/%gconf.xml. Trouble is that the entries are difficult to interpret, since the values are all integers. Here's a sample:
<entry name="language3" mtime="1142324369" type="int" value="18">
        </entry>
Note the *type* and *value* attributes. I wonder if the order of the *entry* elements is significant...:-k 

Maybe I should rephrase my initial question question: Where does evolution get the information about what dictionaries are available? Can I edit that information directly (assuming I can understand it)?

Achim

---

### Post by onehotcutey on 2007-09-18
Was this problem ever solved?  I am experiencing something very similar on Gutsy.

---

### Post by achim_59 on 2007-09-18
Sorry to disapoint you but the problem was never solved. Yours is the first reply I've had in over a year now. Personally I have simply put up with a lot of red underlines in my German texts... I didn't turn spell checking off, because I still want it on when I send messages in English. 

I am hoping the problem goes away when I upgrade to feisty which impressed me no end when I installed it on an old laptop. I am not altogether up to date with the world of Ubuntu, because I have been working away from home and spent the last 18 months mostly underway. I will try once again to get behind the cause of the problem.

Can you tell me precisely what your particular problem is? How did it arise? Does it involve the Evolution mail client and organiser? Which versions of Evolution and dictionary packages? That sort of thing might give me an insight into what's going on.

One other thing... did you do an upgrade of your existing system? I will not do that again, because I had several other problems when I did. Nex time I'll just do some backups and re-install from scratch. I have a sneaking suspicion that the upgrade is at the root of my problem.

Achim.  :???:  :-k

---

