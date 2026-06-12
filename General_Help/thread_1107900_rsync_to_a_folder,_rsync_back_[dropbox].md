---
title: "rsync to a folder, rsync back [dropbox]"
date: 2009-03-27
forum: General Help
---

### Post by tdrusk on 2009-03-27
I recently signed up for dropbox, which allows you to store files on the internet for easy access. It creates a folder in the home directory called "Dropbox". Any files added to that are added to the internet.

I want to write an rsync script to A) backup my computer B) sync back from the Dropbox server to my computer. I want it to first backup my computer, then backup my Dropbox. The problem is, if I backup my computer first and use --delete command it will delete the files that I have recently added to my Dropbox from another computer. If I back up my Dropbox first, I do not intend on using the --delete paramer, but it would add stuff that I deleted from my computer since the last backup. 

I hope my problem makes sense. Any way to make this work?

EDIT: I just discovered Unison. I am checking that out to see if it suits my needs.

---

