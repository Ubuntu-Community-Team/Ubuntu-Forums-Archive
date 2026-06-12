---
title: "Drive not mounting, what does this mean?"
date: 2009-02-22
forum: General Help
---

### Post by SanctusMessor on 2009-02-22
I hope to god this isn't another FAIL drive. I had an external fail on me about a year ago. I had a question though about a program I was using as well. I tried to access my Vista drive through my Ubuntu drive (I have 3 drives in the tower) and originally I could not access the Vista drive. So I forced into it via command and the following is what I get when I try to access it 

[IMG]http://i95.photobucket.com/albums/l147/lyricaray/poop.jpg[/IMG]

That program is "Wake Up On Standby" and one of the things it can do is shutdown the computer on a timer which is perfect for me because every so often I need to run torrents, this past time was for Zeitgeist Addendum, and I cant have the internet bogged down when other people need the computer. So I let it run over night and have WOSB shut down the computer at 7am. Though I think it closes it with a shutdown -s -f or something along the lines, I was wondering if a force shutdown could have caused the issue I am having with the vista drive.

---

### Post by pytheas22 on 2009-02-23
An unclean shutdown could have caused issues on your drive, but it doesn't necessarily mean the drive is failing.

The solution, as the dialog box explains, is to boot to Windows and type 'chkdsk /f' in a terminal, then reboot (into Windows) twice.  This will force Windows to check itself for problems and fix them if necessary.  When it's done, reboot back into Ubuntu and try mounting the Vista partition again.

If you continue to have problems, don't force-mount it; that only runs the risk of making it worse.

---

