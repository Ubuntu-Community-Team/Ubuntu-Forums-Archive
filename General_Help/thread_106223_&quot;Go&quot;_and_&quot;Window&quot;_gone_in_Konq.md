---
title: "&quot;Go&quot; and &quot;Window&quot; gone in Konqueror 3.5?"
date: 2005-12-20
forum: General Help
---

### Post by bigblop on 2005-12-20
I have installed kubuntu-KDE but when I open konqueror the topmost menu no longer contains "Go" and "Window" what happend to the menu options, they are there in Hoary and I used them often...

---

### Post by MartinG on 2005-12-20
I think it's been "simplified" for us :-( 

The key file is called konqueror.rc or konq-kubuntu.rc, but I don't know which copy is used when Konqueror starts up!  So, I checked all the files with these names (use locate - 
~/.kde/share/apps/konqueror/, /usr/share/apps/konqueror/, /usr/share/kubuntu-default-settings/kde-profile/default/share/apps/konqueror/) and found which one had the "old" menus.  I then used this to overwrite ALL the others.  It's VERY crude, but it worked.

---

### Post by Sanne on 2005-12-20
That one bit me too. Here's an official instruction from the Kubuntu FAQ, [How do I change Konqueror back to the default KDE profiles?]("http://www.kubuntu.org/faq.php#konqueror").

After you restored the old behaviour, you can make a custom profile which gets saved in ~/.kde/share/apps/konqueror/profiles under the name you gave it, so you can backup and restore your preferred profile easier.

You can then specify which profile gets used at startup by starting Konqueror with the command
```
konqueror --profile your_profile_name
```
Disclaimer: I'm using Konqueror on Ubuntu, not Kubuntu, so there may be Kubuntu specialities I don't know about.

---

### Post by bigblop on 2005-12-20
Just did what the link you pasted instructed but it does still look the same is it necessary to restart ubunut?

---

### Post by Sanne on 2005-12-20
[QUOTE=bigblop]is it necessary to restart ubunut?[/QUOTE]
I didn't need to, but in Kubuntu it may be different. Does it look exactly the same, or do you now get the view profile entries under settings in the menu? I have 
```
Settings
  Load View Profile
  Save View Profile
  Configure View Profiles
```

---

