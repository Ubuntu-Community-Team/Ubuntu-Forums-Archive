---
title: "recommended way of re-installing Ubuntu?"
date: 2009-06-01
forum: General Help
---

### Post by OrganizedFellow on 2009-06-01
My computer freezes WAY too often.
It all started when I upgraded to Jaunty.

Strange, it always freezes when I am using Firefox. I started using Opera a few days ago, and have noticed it does NOT freeze! Weird!
All brand-new hardware, less than 10 months old.

I assume I have many 'broken' things, still a newb here :|


I'd like to re-install.
If so, I need to backup my ~/home/ directory, right?!
I know it contains lots of hidden folders, which contain config files for my installed apps.
What if I want to start over and do a fresh install and reconfigure everything - I just backup bookmarks, personal files, etc. Right?
What if I want to start over and do a fresh install but NOT reconfigure everything - I just backup the partcular hidden folders in home?


How could I conclude Firefox is the culprit?
Either way, I'd like to start fresh, get rid of all the clutter.

---

### Post by DeMus on 2009-06-01
> **OrganizedFellow said:**
> My computer freezes WAY too often.
It all started when I upgraded to Jaunty.

Strange, it always freezes when I am using Firefox. I started using Opera a few days ago, and have noticed it does NOT freeze! Weird!
All brand-new hardware, less than 10 months old.

I assume I have many 'broken' things, still a newb here :|


I'd like to re-install.
If so, I need to backup my ~/home/ directory, right?!
I know it contains lots of hidden folders, which contain config files for my installed apps.
What if I want to start over and do a fresh install and reconfigure everything - I just backup bookmarks, personal files, etc. Right?
What if I want to start over and do a fresh install but NOT reconfigure everything - I just backup the partcular hidden folders in home?


How could I conclude Firefox is the culprit?
Either way, I'd like to start fresh, get rid of all the clutter.

When you really want to do a re-install of Jaunty you have to back-up all your personal data, like documents, pictures, movies, e-mail, bookmarks, etc.
Settings for programs are not needed since they will be be renewed anyway.
In Nautilus press ctrl-h to also see hidden files and folders.

About Firefox: in Firefox first go to organize bookmarks and export them to a html file. The latest releases keep bookmarks stored in a database like file which is not readable with a text-editor.
The html file with the exported bookmarks is the file you need to back-up.
Don't back-up anything else, since it might be the cause of your problems.

Re-install Jaunty fresh from scratch and place your personal data back to your home folder. Make sure your home folder is new as well, don't keep anything behind. In other words make a new disk for /home and format it. It's the only way to get rid of all old things.

Good luck.

---

### Post by OrganizedFellow on 2009-06-01
@DeMus thank you! I really can't live without Tomboy Notes, and found it at:
/home/organizedfellow/.tomboy

In addition to my bookmarks.html file (as you mentioned) and personal files, this seems pretty straight forward!

:)

I really should wait for tomorrow to do this, but ADHD ... gotta do it now, before I procrastinate, hahaha.

Thanks Again!

---

### Post by OrganizedFellow on 2009-06-01
So I successfully reinstalled last night.
Launched Firefox, was about to go to their Addons/Plug-ins pages ... FREEZE!!!

grrr

Downloaded, checked md5sum of iso, burned, installed. Same thing.

Then tried my luck with Kubuntu.
I am using Konquerer at the moment, but it still froze earlier.

HOW can I possibly find the problem?!
It's not software like I thought. All hardware is properly plugged in and recognized.
I need to take a can of air to the insides, just a little bit of dust.

Maybe that's it?

---

