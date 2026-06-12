---
title: "Backup files (*~) visible on Xfce/Xubuntu desktop."
date: 2012-11-27
forum: Desktop Environments
---

### Post by Pandanus on 2012-11-27
Hello Forum,

this is a rather minor and cosmetic issue, but annoying nonetheless. General backup files, ending in a tilde (~) are visible on my Desktop (Xubuntu 12.04). E.g. if I have 'example.txt' on the Desktop to take notes or whatever, and edit it with gedit, any save will automatically create a backup file 'example.txt~' which in Thunar is only visible in my ~/Desktop folder if 'show hidden files' is switched on (this is as expected); however, they are always visible on the Desktop itself, and come complete with an ugly 'paper-roll' thumbnail. I have had a look around, but apparently this isn't a common issue. Is that somehow a problem with my install? And, of course, perhaps someone would have a suggestions for how to hide the backup files. 

Many Thanks.
Pandanus

---

### Post by LewisTM on 2012-11-27
I think your install is fine. You might want to file a bug. Xfdesktop and Thunar file display should be consistent. In addition, Xfdesktop cannot be set to show hidden files. 
One day Thunar will be used for managing the desktop but in the meantime we have to use xfdesktop. 

That being said, you should ask yourself the bigger question: Do you really need automatic file backups? This feature can be turned off in gedit. It's not even present in leafpad, Xubuntu's default text editor. For serious file version control, you can use bzr, git, svn, etc. For the casual, a [Dropbox]("http://db.tt/nI4sWDHJ") account keeps 30 days of file versions for free.

Cheers!

---

### Post by SlugSlug on 2012-11-27
You could try clicking the desktop (wallpaper) and press ctrl +h

---

### Post by rai4shu2 on 2012-11-27
Interesting use case. I think most people don't see that because they put documents into their ~/Documents folder rather than their ~/Desktop folder. The thing is, if I were to put all my documents on the Desktop, it would soon get cluttered and be a huge distraction in every other thing I do. Maybe it's just me, but I like to use ~/Desktop as a temporary folder, if at all.

---

### Post by Pandanus on 2012-11-27
First of all thanks to everyone for their answers.

@rai4shu2 Well, I also keep most of my documents somewhere else, not in ~/Desktop, but sometimes it is quite handy to just click on the Desktop, and generate a new text file to take notes of something, or leave it there to not forget about an idea. Anyway, different people will use the Desktop differently, and in my opinion one should have the possibility to have documents on it, and be able to work on them.

@LewisTM Thanks a lot Lewis, I learned two new things here! I had no idea that Thunar isn't managing the desktop, but I am new to Xfce; however, I also never thought about just disabling the backups, despite using gedit for quite a while now - the problem just never occurred in Ubuntu. That solved my problem! (though not the more general issue, perhaps I'll file a bug report, but is anything going to happen if the idea is to use Thunar at some point anyway?)

Thanks again
Pandanus

---

