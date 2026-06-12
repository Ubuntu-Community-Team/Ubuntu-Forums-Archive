---
title: "should I delete ~/.nautilus/-files ?"
date: 2009-02-12
forum: Desktop Environments
---

### Post by zika on 2009-02-12
there are (literally) thousands of .XML files in directory ~/.nautilus and ~/.nautilus/metafiles.
since I do not need that kind of history what would happen if I would erase them?
is there a way I could switch off that kind of "journal"?

---

### Post by kaibob on 2009-02-12
Deleting all the files can cause problems. I use the script supplied in the following thread. It deletes all but a few of the files:

[http://ubuntuforums.org/showthread.php?t=671838](http://ubuntuforums.org/showthread.php?t=671838)

---

### Post by zika on 2009-02-13
> **kaibob said:**
> Deleting all the files can cause problems. I use the script supplied in the following thread. It deletes all but a few of the files:
[http://ubuntuforums.org/showthread.php?t=671838](http://ubuntuforums.org/showthread.php?t=671838)
what is the rule? delete all but the yesterday's ones? is there a way to turn-off that journal?

what about ~/.thumbnails? it is even more of them and more space occupied? 
(update: following some other threads I fould a cure for .thumbnails. gconf-editor->desktop->gnome->thumbnails_cache->size=1. and, of course, deleted more than 26000 of them occupying ~600M of space...)

---

### Post by SuperMike on 2009-03-20
+1 to Zika for creating this thread. My thoughts exactly. I mean, with most every other app I have, including Google's website, if I don't want to keep my history, I can click something to clear it. Why wouldn't the guys who made GNOME permit me to clear it, or keep only the most relevant stuff from the previous day?

And if they're not going to do that, then why not encrypt this data?

Here's the deal. I have a friend who sends me gag emails from time to time. Some of the images in them are extremely funny and so I might save the image in a folder on my desktop or something to send to someone else later. Unfortunately, however, some of them are risque and I have no way of validating the ages of the women in them. Often these come in these new demotivator posters. You know what I'm talking about, yes?

Anyway, there's a new set of laws now in the USA and you can be stopped and searched without warrant within a 100 miles of the USA border. And when they see a laptop, they can ask for a password and scan your hard drive. If you want to be belligerent and say, "Sure, here's my password. Oh! It's not working. I wonder why?" they can call a judge and stick you in a jail cell with no chance of bail indefinitely until a judge has found time to deal with your case. Then, they can take a forensic guy to pull out your hard drive, mount it, and scan it. They scan for MD5 hashes, which, as you know, now have been proven by some Japanese scientists to exist for more than one file, even unrelated.

So, once the police hit your .nautilus folder, it's one more way to get into serious trouble all for an innocent gag email a friend sent you. This is why I would like to be able to SAFELY (I'm nervous about a script) clean this .nautilus trace in thumbnails and other XML files, without hurting the OS. And another reason why I worry about the script is that it may grow out of date -- running it eventually might blow up your Nautilus, forcing you to have to create a whole new user profile.

So, GNOME devs -- if you're out there, please consider fixing this issue.

(I'm probably speaking into a vacuum.)

---

### Post by zika on 2009-03-20
when posting I did not have any kind of privacy issue in mind. just pure disk-space ... :) (I know, that makes me boring, but that is what I am ... :))

---

### Post by randywilharm on 2009-09-09
I've never seen such a useful forum in my life.

Everytime I need to solve something, the answer is there.

Been with Ubuntu 2yrs. If my computer could speak it would thank you!

It's so nice not to DEPEND on proprietary software
specifically Microsloth's broken "windows".

Mac users are better off than they are,
but they still need to convert to linux.

THanks again-- getting linux was the best
thing I ever did and it would have been
5 times harder without Ubuntu.

The learning curve was well worth it.

---

