---
title: "Question re:  Firefox Bookmarks"
date: 2006-08-14
forum: Desktop Environments
---

### Post by djross95 on 2006-08-14
Hi, I'm relatively new to Ubuntu, so bear with me.........     :-)

I'm trying to copy my Firefox "bookmarks.html" file from a previous distro over to my newly installed copy of Dapper so that I don't have to add all my sites manually.  Unile all other versions of Linux I have used, Ubuntu does not place the FF directory in the home folder.  This, of course, means that I cannot simply copy over my file without sufficient permissions.  

How can I do this?  Is there an equivalent to the "File Manger--Super User" that I have seen in other Linux distros?  I'd rather not use the command line, but if that's the only way to do it, then I'm game.

Thanks in advance for your help!     DR

---

### Post by timetunnel on 2006-08-14
> Ubuntu does not place the FF directory in the home folder
Of course it does, but only the files that are user dependant. That's where the bookmarks are. It's all in a hidden directory. IIRC it should all be in /home/username/.mozilla/firefox (I'm not at my Linux box right now, therefore it might be slightly different. But it *is* there somewhere)
In order to see hidden files and folders in the Nautilus file manager, press CTRL-H.

---

### Post by djross95 on 2006-08-14
Oops, I missed it the first time around.  Sorry, and thanks for the quick reply---I'm good to go!     DR

---

### Post by baka_rob on 2006-08-14
Have you tried to import the .html file?  If you open firefox and go to Bookmarks -> Manage Bookmarks... and then in the resulting window go to File -> Import..., you should be presented with an import wizard.  Then you just need to navigate to and pick your .html file, and it should import the entries within it for you.  Does this work for you?

---

### Post by djross95 on 2006-08-14
Thanks to all for the feedback.  I was able to copy over the bookmarks file and I'm all set.  For some reason I missed the hidden FF directory the first time around, likely because I hadn't launched the program yet.  One of Linux's little quirks that I'm learning day by day!    DR

---

### Post by shakyone on 2006-08-14
I'm not a big Google fan, but I would swear by the "Google Browser Sync" Plugin for Firefox.  My life has become so much easier between work, two home computers and portable firefox.  It completely alleviates the hassle you describe here.
"http://www.google.com/tools/firefox/index.html"

Shaky

---

