---
title: "Uniting &quot;USB Memory&quot; threads into one"
date: 2011-05-27
forum: Forum Feedback &amp; Help
---

### Post by iluminameluna on 2011-05-27
Is this where I can suggest that three threads, one of which is marked SOLVED, can be joined/united or whatever it's called so that all discussions of the one problem w/ mounting/manipulating USB memory & other external memory can be seen in one place?

The threads I found are:


[URL="http://ubuntuforums.org/showpost.php?p=10867913&postcount=6"]Ubuntu Forums > The Ubuntu Forum Community > Main Support Categories > Desktop Environments
 [ubuntu] USB memory sticks not automounting in Gnome[/URL]

[URL="http://ubuntuforums.org/showpost.php?p=9346350&postcount=9"]Ubuntu Forums > The Ubuntu Forum Community > Main Support Categories > General Help
 [ubuntu] unable to unmount usb drives when not root[/URL]

[URL="http://ubuntuforums.org/showpost.php?p=9346354&postcount=30"]Ubuntu Forums > The Ubuntu Forum Community > Absolute Beginner Talk
 [SOLVED] cannot write to usb - need root permission
[/URL]


I've been asking for help & looking for similar probs w/ this issue & finally found ONE discussion. Then I found another by changing my search criteria, just by chance, & finally another that actually solved my problem.

Pregiopomo should be awarded a medal. His was the most elegant & simple solution to the one problem that suddenly appeared w/ Ubuntu 10.04LTS & that no one would deign touch in any other forum I tried.

Just thought I'd bring it to the attention of you mods ..

---

### Post by coffeecat on 2011-05-27
I notice that one of the packages that Pregiopomo suggests you remove is usbmount. This was probably the problem one. Threads about this come up with monotonous and depressing regularity, so I'm not sure the staff would want to merge the three threads you refer to because there are so many other related ones.

The problem with usbmount is that it is not designed for systems with GUIs and it interferes with the automounting function built in to the desktop version of Ubuntu. Unfortunately, this is not very clear in the package description and I guess people install it because they think it is needed for mounting of USB sticks. It isn't, and people who do install it come to regret having done so.

As far as the other packages are concerned, it's a bad idea to remove usb-creator related packages - if you ever need to create a bootable USB stick, that is. That was not causing a problem. It's also a bad idea to remove hplip if you have a HP printer. I think some of the other packages listed are essential for some situations but I haven't gone through them in detail.

@iluminameluna, I'm glad you found a solution to your problem.

---

