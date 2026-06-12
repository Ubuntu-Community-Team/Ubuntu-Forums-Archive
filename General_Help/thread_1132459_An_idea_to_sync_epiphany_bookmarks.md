---
title: "An idea to sync epiphany bookmarks"
date: 2009-04-21
forum: General Help
---

### Post by Psyphre on 2009-04-21
Hi,

Ive just started using Dropbox, which as an amazing file syncing service. Its cross platform and open source.

This thread isnt about convincing you to use dropbox, so I'll link you a video tour for those interested:
**Preview**
[https://www.getdropbox.com/screencast#screencast](https://www.getdropbox.com/screencast#screencast)

If you want to get extra space when you sign up please feel free to use my referal link:
**Link**
[https://www.getdropbox.com/referrals/NTk1Njg2Mzk](https://www.getdropbox.com/referrals/NTk1Njg2Mzk)


When I used it to sync files between my laptop and desktop I had an idea; what about using it to sync my bookmarks for epiphany (or firefox, or any other browser)? Unfortunately I havent been completely successful, so I thought I'd share what I've done so far and see if others can come up with an idea to make it work. I'm sure this would be extremely useful for many people.

I have 2 computers. One is called 'A', the other is called 'B'.
Dropbox is the bridge between the two (its essentally an online server which stores files). Of course it doesnt have to be dropbox, could be a network drive or something.

I moved the bookmark file to drop box and created symbolic links to the .gnome2/epiphany/  folder on each computer. So something like this:

**A** <----------------------------------> Dropbox <------------------------------------> **B**

Now I opened up epiphany on computer B and VOILA! I had all of computer A's bookmarks. I was exstatic,   but that soon faded when i discovered a problem. When epiphany makes a new bookmark it deletes the symbolic link and just makes its own bookmark file in its place. Of course with no link, the dropbox doesnt get updated and therefore neither does computer B.

This is the only problem stopping it from working. 

Any ideas?

---

### Post by Psyphre on 2009-04-22
bump?

---

