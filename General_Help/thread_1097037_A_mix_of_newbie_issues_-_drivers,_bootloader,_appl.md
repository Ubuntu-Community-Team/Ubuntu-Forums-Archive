---
title: "A mix of newbie issues - drivers, bootloader, applications"
date: 2009-03-15
forum: General Help
---

### Post by ungua on 2009-03-15
Last week I received a Dell M1530 with Vista, which I deleted in favour of XP and Ubuntu. I have been using several versions of OpenSuse (KDE) since 2004 but without ever acquiring a good understanding of the Linux-world, since I mostly used it as uninformed as people usually use Windows. My conversion to Ubuntu is due to peer pressure :) and there are some issues I need help to get solved, and some comments at the end of the post.

*Proprietory drivers*

Dell offers notebooks with Ubuntu preinstalled, which unfortunately was no option with mine. The Dell-homepage offers driver downloads for Vista 32, -64 and for the BIOS, but not for Ubuntu. I assume the download of proprietory drivers such as for the NVidia graphics is the newest and best available software, equivalent to what Dell sells?

*Boot loader*

OpenSuse came with a fancy visual bootloader whose options I could change in Yast. Ubuntu has some DOS-style bootloader, that after an initial update even contains two different kernel versions. Altogether, there are 4 or 5 options to start some Ubuntu and under "other operating systems" I can choose XP. How do I (1) change options and their hierarchy, (2) can I simply delete the older kernel editions and (3) can I get a more visual appealing boot loader? I typed both "GRUB" and "LILO" into the programme installation tool, but got no results. It is enough with a coloured background making me and other users distinguish the screen from some BIOS-messages, displaying the options "Ubuntu" and "XP". I never used the failsafe-option and I don't need a line telling users there are other OS, people get that.

Connected: Restart-options - I cannot just click on the red button, walk away and the computer restarts directly into Windows? Available now are "Log Out, Suspend, Hibernate, Restart [no further options], Shut down".

*Single-click modus*

Can I change to a single-click-modus different from XP and more like in OpenSuse to open files after one click. It's a stupid passage issue, but it happens I click on an icon and stare at the screen waiting for something to happen. That, of course, never happens unless i doubleclick. :)

*KNotes vs. Tomboy*

I used KNotes a lot, Tomboy seems to be the GNOME-"twin", but more advanced. One simple sheet of "paper" without any options is more than enough for me, can I install KDE-applications on GNOME, too? I see that a lot of them are offered in the program tool. Though, I digg the GNOME-tetris, even cleaner than KSirtet. =8^) But why can't I delete all the other games except for Tetris (it's called a "package", well?)?

*Java & Firefox*

To log in to my bank I need Java. I tried to install it, but it didn't work in the first round. Now I installed a plugin called "Icedtea"-plugin for JRE-like software. Unfortunately, my bank's site seems to be down, and I can't test it. But I see that Java and Firefox have been a troublesome issue in Ubuntu before, if you guys know a good tutorial, can you let me know about it? :)

*System monitor*

Very nice application, but how do I make it display GPU, CPU and HDD temperatures? I didn't find anything about that in its options.

Apart from that I really like the layout, it's simple and clean and my initial annoyance of not finding things I am looking for will go over fast. Three comments: I already got confirmed that "AMD64" in the downloaded image's name and in some presentations and documents online is bogus and means both Intel and AMD processors. But I don't get why it should be called "AMD" then. In addition I have to remark the strange Norwegian in the installation screen, it's better in the actual installation, but are there competing translations? One last comment is rather serious, since it took a lot of time and triggered an internet research: The partitioning options during install were stupid altogether. The guided one offered me to resize my XP-partition considerably, leaving the unpartitioned space untouched. The next one offered to delete XP, still leaving the rest untouched. Manually, I could leave the XP-partition as it was and could install Ubuntu into the free space. But doing that comes not natural for first time users, especially if your partition program crashes the first time, leaves you no options at all the second time and allows you to work with it first at the third try (when a download of OpenSuse 11 x64 was soon to be finished on my old notebook). The partitioning recommendations in the Ubuntu installation guide still talk about very old machines or servers with 256MB RAM etc, which left me quite insecure about how much space to choose for the available partitions. I ended up with 4GB-swap (as much as RAM) and put the rest in one partition.

Best regards
Ungua

---

### Post by LegendofTom on 2009-03-15
The proprietary driver provided is the most recent Nvidia has to offer.  Also, KDE applications can be install in Gnome, just with a bunch of other stuff required to run.  Look in the Add/Remove for Java.

---

### Post by ungua on 2009-03-15
Thank you for your answer, good to know about the KDE applications. As for Java, I did exactly that. I installed Sun Java proprietory first, with no success, than rAn An instAllAtion oF whAt AppEARS TO BE AN open source VARIANT.

AND NOW I CAN'T WRITE SMALL CONSONANTS, THEY ARE UNDERLINED AND I CAN'T CONTINUE WRITING. WHAT IS THIS ABOUT??? THAT'S WHY I USE CAPITAL LETTERS.

---

### Post by ungua on 2009-03-16
The keyboard issue is due to some small app changing my keyboard to "RAW Code", whatever that is. And it seems I get my questions answered at linuxquestions instead, since my post in this forum here disappeared in a stream of others. Thank you guys anyway!

Regards
Ungua

---

