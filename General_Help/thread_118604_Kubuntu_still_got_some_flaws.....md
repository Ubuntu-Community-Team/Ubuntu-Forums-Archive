---
title: "Kubuntu still got some flaws...."
date: 2006-01-17
forum: General Help
---

### Post by pelle.k on 2006-01-17
Thats it, i'm trying another distro on our "household" computer. I'll definitly be back for the kubuntu dapper release, but this isn't going anywhere at the momemt...

KDE 3.4.2 had som bugs with administrator mode and system settings. I upgraded to KDE and it seems it almost took care of those problems.
But still, some things is giving me a headache. Some apps never show up on the menus after installation. (like superkaramba for example).
Kicker crashes quite regurarly, Klauncher cant talk to panel.

User & Groups behaves really strange. Sometimes i can create a user, but when i try to login with it, nothing is correctly setup.

I've noticed i can sometimes use administrator mode with the wrong password.

Printing doesn't work well with a multi user setup. I've given them access to all possible groups but nah...

I created a reiserfs partition and mounted it under /media/files. The idea was that this partition should be accessible for all users to read and write, what the hell they want. You can't mount reiserfs, with umask options.
I created a group for all users to belong to, and chgrp:ed /media/files to that group with sticky bit set. But even though new files in there, inherit group owner, the default umask for creating stuff is 755 so other user cant delete what i puit there.
I really don't want to change default umask for any user.

So I created a fat32 (the horror) partition, with umask 000 :|
Should i really have to create a fat32 partition to share files with others? lame...

I will keep Kubuntu 5.10 on my laptop though... ( I haven't got a printer setup there, no other susers than me, and it hasn't broken on me yet so... i'm holding my breath.)

---

### Post by pelle.k on 2006-01-20
Hello again.
Time for an update...

All it took was a few days of abscence, then i realized kubuntu rulez :)
Seriously. Judging from allmost all reviews of openSUSE 10, it should  be good. I soon realized i'm too used to ubuntu and debian in general i guess, so i couldn't stand it. Don't take me wrong, openSUSE is a nice distro, but i found it to messy. YAST is pretty cool, but those times it didn't work i really didn't know what to do...

This I have chosen to keep KDE 3.4.3, as it seems more stable.
Printing now works well with all users. The last time i had accidently moved the usb connector on the printer out of position with my foot, under the table! I ought to put my feet i'm my mouth the next time i make such an attack on printing in KDE ;)

I still have some minor problems with "users & gruops" though, but that is easiely corrected with groupmod, and usermod...

All in all, a multiuser setup is a bit tricky compared to a default single user setup, but this time i've got it right and it works great :)

---

### Post by quasar on 2006-01-29
Hey guys,

    okay maybe you can help me since you've observed problems with KDE's Users and Groups GUI.

    I'm trying to set up a cvs repository on my local machine and for that purpose thought I would go and create a new group, called cvs. That seems to have worked. I did this with the KDE G&U GUI.

    Still with the same GUI, I went and added myself to the newly created group. KDE reports that my username is in that group, and inspection of /etc/group verifies (or does it?) that I'm indeed in that group.

    Problem is, now when I go to a shell window and go 'groups', the new group is not listed! My primary group is still the one named like my username, and I have a whole bunch of secondary groups that Breezy set up for me upon installation, but... the cvs group is just not in the list!

    If I go newgrp cvs I get a new shell and my primary group is now 'cvs'... yay! Useless. Besides, how can it appear now as my primary group, when a second ago it wasn't even listed as a secondary one?

    All I can say is that I'm very confused... any help, even pointers to other posts, will be huge help. Thanks a lot in advance.

     Cheers,

       QUASAR

---

### Post by TrinitronX on 2006-01-29
I've noticed that Kicker has been crashing semi-regularly whenever I restart or shutdown.

---

