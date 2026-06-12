---
title: "Can Permissions Bollix Java Runtime Environment?"
date: 2008-12-15
forum: General Help
---

### Post by psuliin on 2008-12-15
I recently had a system glitch that disabled my $HOME/.dmrc directory.  I managed to get my home directory back under my ownership with 644 privileges, and went on about my business.  Then a couple of days later (today) I noticed that a website that required Java wasn't running right.  

I checked Firefox's preferences and "Enable Java" is checked.  My Java Runtime Environment is installed - and it was working a week or so ago when I visited this same website.  However I went back to my firefox and java directories (the former is in my /usr/lib directory and the latter in my home directory) and noticed that the ownership of the directories is different: $HOME/java is owned by me (as it should be since I changed the ownership of my home directory back to myself recently), but /usr/lib/firefox-3.0.4 is owned by root.

The normal process of enabling Java involved placing a link to my JRE (in $HOME/java) in my firefox folder.  Did changing ownership of that $HOME/java folder while leaving my firefox folder with root break that link?

---

