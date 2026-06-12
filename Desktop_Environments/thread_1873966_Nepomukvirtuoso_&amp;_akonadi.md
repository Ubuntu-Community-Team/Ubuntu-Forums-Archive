---
title: "Nepomuk/virtuoso &amp; akonadi"
date: 2011-11-02
forum: Desktop Environments
---

### Post by jandac2011 on 2011-11-02
I have upgraded to 11.10 Oneiric Ocelot, and it is a huge step back. Compositing stopped working, KMail stopped working, digikam is almost unusable. Except for the problems with compositing, the driving force behind the destruction is the pair nepomuk (aka virtuoso) and akonadi.
In KMail:
I resolved some initial problems, but KMail complains that it does not have rights to write to my inbox. It displays an error message that always stays on top. Clicking it closes the application. I can still read e-mail, but I cannot access some folders with old e-mail. When KMail does not run, akonadi still wants to access my e-mail accounts.
In digikam:
When I move some photos or films to a directory controlled by digikam, they do not show any more. Moving photos and films to that directory is now the only way to enrich my repository, as digikam no longer recognizes my camera, and I have to use gphoto2 to download them. Not recognizing my camera is a separate problem, but invisibility of new items must be related to akonadi or nepomuk. Rebuilding/updating indexes did not work.

Q: What do akonadi and nepomuk actually do? 
A: They work hard. They take almost 100% of 3 of 4 virtual cores of my Intel i3 processor. 
Q: What is it that they work on so hard? 
A: They write. 
Q: What do they write? 
A: They write an error log. 
Q: Why does it take so long to write it? 
A: Because it is long, it takes a lot of space, and it blocks access to disks, otherwise it would not e.g. take several minutes for konqueror to launch.
Q: How big is the log?
A: .kde/share/apps/nepomuk/repository/main/data/virtuosobackend/soprano-virtuoso.log has 571190586755 bytes after letting 3 processes:
/usr/bin/nepomukservicestub nepomukstorage,
/usr/bin/nepomukserver, and
/usr/bin/virtuoso-t +foreground +configfile /tmp/virtuoso_Tw2293.ini +wait
run for one hour. They could go on writing. The size of the file is hard to read as it is, so here it is with commas for more readability: 571,190,586,755 bytes.
Q: Has it happened before?
A: Yes, one year ago, when I installed kubuntu on my present computer. Switching nepomuk desktop search (or so) off helped. At that time, it was akonadi rather than nepomuk* processes that took 99% of two virtual cores, virtuoso took 50% of another one. Also, the error log had akonadi in its name. After one year, nepomuk/virtuoso/akonadi is more efficient in writing the error log (it used to be ca. 400GB).
Q: What is in the log?
A: Top 10 lines:                Tue Nov 01 2011
00:40:50 Reference to page with free remap dp = 1640, remap = 1640
00:40:50 Reference to page with free remap dp = 1271, remap = 1271
00:40:50 Reference to page with free remap dp = 1582, remap = 1582
00:40:50 Reference to page with free remap dp = 1594, remap = 1594
00:40:50 Reference to page with free remap dp = 1539, remap = 1539
00:40:50 Reference to page with free remap dp = 1170, remap = 1170
00:40:50 Reference to page with free remap dp = 1638, remap = 1638
00:40:50 Reference to page with free remap dp = 1274, remap = 1274
Bottom 10 lines:
11:40:32 Reference to page with free remap dp = 1264, remap = 1264
11:40:32 Reference to page with free remap dp = 1264, remap = 1264
11:40:32 Reference to page with free remap dp = 1264, remap = 1264
11:40:32 Reference to page with free remap dp = 1264, remap = 1264
11:40:32 Reference to page with free remap dp = 1264, remap = 1264
11:40:32 Reference to page with free remap dp = 1264, remap = 1264
11:40:32 Reference to page with free remap dp = 1264, remap = 1264
11:40:32 Reference to page with free remap dp = 1264, remap = 1264
11:40:32 Reference to page with free remap dp = 1264, remap = 1264
11:40:32 Reference to page with free remap dp = 1264, remap = 1264
Q: Is there any advantage for using nepomuk/virtuoso/akonadi?
A: Yes. When I killed those 3 processes, I got a terminal bell in xterm again! Finally! Impossible for several years... Finally I hear when new e-mail comes in. This also happened one year ago when I killed those 3 processes (under different names).

Is it possible to purge akonadi/nepomuk/virtuoso from Kubuntu to make it work again? I love the terminal bell, but I need my digikam database more.

---

### Post by jandac2011 on 2011-11-02
Actually, it looks like regaining the terminal bell may have nothing to do with nepomuk/virtuoso/akonadi. When I log in now, I have to wait several minutes for plasma-desktop (or so) to bring up my desktop. The "top" command shows the status of plasma-desktop as D (uninterruptible  sleep). I run the command in a text terminal (Ctrl-Alt-F1), and that may trigger the bell. What causes the plasma-desktop to sleep is still a mystery.

---

### Post by ankspo71 on 2011-11-03
Hi,
I haven't used Kubuntu in a few months, but nepomuk, virtuoso, akonadi, and strigi are parts of a 'semantic desktop'. These processes allow us to tag, comment, rate?, files and folders, and be able to find files and folders by name, content, tags, comments, and ratings etc. The tagging, commenting and rating integrates into the right side panel of dolphin. If you don't use that panel then you can safely disable desktop features (nepomuk) in systemsettings  > dekstop search. 

It's also very important to tell strigi to stop indexing certain files that are too large or have unindexable (human-unreadable) content (even images and music files are unindexable, but strigi can collect the metadata... which most image viewers and audio players already do). In fact, try to restrict the indexing to mainly documents. You can do that in systemsettings > dekstop search.

If you still have problems with these processes then you could try disabling a few of the krunner plugins that might invoke these processes too. Press Alt+F2 then click on the small settings icon next to the run dialog box.

You might also want to try installing kubuntu-low-fat-settings.

Here's some info on nepomuk, virtuoso, akonadi, and strigi
[http://thomasmcguire.wordpress.com/2009/10/03/akonadi-nepomuk-and-strigi-explained/](http://thomasmcguire.wordpress.com/2009/10/03/akonadi-nepomuk-and-strigi-explained/)
[http://nepomuk.kde.org/node/2](http://nepomuk.kde.org/node/2)
[http://semanticweb.org/wiki/Semantic_Desktop](http://semanticweb.org/wiki/Semantic_Desktop)

Hope this helps

---

### Post by jandac2011 on 2011-11-06
This helps indeed. Thanks a lot.

I have already switched off Nepomuk semantic desktop, and those 3 processes do not try to steal 3/4 of my virtual cores. I still have a hardware bell in xterm, which I like very much. I didn't know that there is so much hidden under Alt-F2 even though I use it to invoke commands - mostly xterm. It seems to me a crazy idea to put configuration of so many processes there instead of putting them into System Settings, i.e. the KDE Control Center. That configuration is not well explained (About and Author is not enough).

Now I know why digikam does not see my new photos. Digikam has been damaged by introduction of a new library that conflicts with gphoto2 library, so digikam cannot recognize my camera, and I have to use a standalone console program gphoto2 to transfer my photos from the camera. As it is a console program, nepomuk does not see a change in the directory. What a wonderful idea it was to disable gphoto2 library and introduce nepomuk at the same time!!! I don't need nepomuk, I need digikam and (to lesser extent) kmail. Some KDE developers do not realize that people treat Linux as a working system, not a hobby. I know Gnome people are even worse (replacing configurable gdm [now gdm2.2] with inconfigurable windows-inspired, security disaster greeter while damaging gdm2.2 to prevent people from using it, imposing Unity on people etc.), but this is not a competition to win.

---

### Post by searchfgold6789 on 2011-11-06
I would check your hard disk and also do a memcheck, just in case. I never use Nepomuk; purge it?

---

### Post by jandac2011 on 2011-11-08
> **searchfgold6789 said:**
> I would check your hard disk and also do a memcheck, just in case. I never use Nepomuk; purge it?
Smart shows a healthy disk, and it is periodically checked at startup. Purging nepomuk would be great, but it looks like it would break digikam.

---

