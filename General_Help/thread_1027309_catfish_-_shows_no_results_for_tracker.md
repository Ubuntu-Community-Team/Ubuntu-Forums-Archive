---
title: "catfish - shows no results for tracker"
date: 2009-01-01
forum: General Help
---

### Post by jackmetal on 2009-01-01
I decided to try a front-end to Tracker, but it shows no results.  Results for a search done within tracker work fine, but nothing shows up for the same search in catfish.  

I've selected 'tracker' as the Search method, tried selecting different file types, folders, searches for text and filenames that show up correctly in tracker, but nothing ever shows up in catfish (unless of course, I change the search method to find or locate, etc...)  :-)

Is there a config file or anything I should be doing to configure it other than just installing via the repository and selecting the Search method when catfish comes up?

Thanks!!

---

### Post by jackmetal on 2009-01-02
Oh well..   

I guess it's a bug.  I'll try to contact the author and check.

Tried everything, but still only get results from selecting everything 'except' tracker as the back-end.

I'm sure the Tracker group will make their front-end better with time and maybe there won't be a need for a third-party front-end to it in the future.  Until then......

Have a great New Year!!

---

### Post by jackmetal on 2009-01-04
-bump

Any ideas at all?  Catfish looks like it might be a decent front-end for tracker, if I can figure out why it never shows any findings.

---

### Post by ugkbunb on 2009-02-28
I have had this problem as well with xubuntu and now arch > <

---

### Post by afoglia on 2011-01-11
I'm sorry to see catfish abandoned, I liked it when I used it in the past.  But I knew enough to figure out the problem.  Here's a patch file that should get your catfish working.  Apply it to catfish.py in /usr/share/catfish.  (I wouldn't recommend patching distribution installed files, but this is the easiest for now.)  I plan on passing this to both the original developers and the debian maintainers, but I don't expect any luck getting it in.

I just noticed someone made a similar patch a year ago, but even though the fix is supposedly committed, the version in the universe repo hasn't changed.  [https://bugs.launchpad.net/ubuntu/+source/catfish/+bug/518549]("https://bugs.launchpad.net/ubuntu/+source/catfish/+bug/518549")

This weekend, I'll figure out how to make a deb package with this patch, plus some other changes.

---

### Post by dez93_2000 on 2011-09-10
tried it but it made no difference. Code used looked like it worked:

root@me-desktop:/usr/share/catfish# patch /usr/share/catfish/catfish.py /home/me/Downloads/catfish.tracker_parsing.patch.txt

patching file /usr/share/catfish/catfish.py

root@me-desktop:/usr/share/catfish# 



Any ideas?
Cheers

p.s. using locate i get "fatal error search was aborted" almost instantly. don't know if it did this before or is related. Trying to search an ntfs drive which tracker searches without problems.

Dez

---

