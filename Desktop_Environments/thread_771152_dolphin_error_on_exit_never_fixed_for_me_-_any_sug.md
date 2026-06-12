---
title: "dolphin error on exit never fixed for me - any suggs?"
date: 2008-04-27
forum: Desktop Environments
---

### Post by nowshining on 2008-04-27
[CENTER][/CENTER]"Unable to save bookmarks in /home/nowshining/.kde/share/apps/d3lphin/bookmarks.xml. Reported error was: Permission denied. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive"

This was suppose to be fixed about 6months ago and I got as far as I know of this post - all updates - checked/installed yesterday/hours ago, and this still comes up.

 Yes I tried sudo chown -R username:username pathtofolder however it works fine up till I do a sudo dolphin and it does it again, I tried deleting it, etc..and it stil continues.

Anyone out there know what I could try to hopefully fix this problem?

---

### Post by wandalalakers on 2008-04-28
If this fixes your problem, please give me a "thank you".

I think I might have fixed this problem, at least temporarily.
I went to a desktop that wasn't having this problem and right clicked on the d3lphin folder in the location below:

/home/username/.kde/share/apps/d3lphin

Desktop with 8.04 doesn't have this problem.
I used it to see what was different.

Access permissions
owner: can view & modify content
group: forbidden
others: forbidden

Ownership
user: username
group: username

On the pc with the error it has

Ownership
user: root
group: root

I changed both the user and group to my username but when I did, it said "username" group doesn't exist.  It does exist on this pc so I tried.

Ownership
user: username
group: root
and click apply changes to all subfolders and their contents.

This might just be a temporary fix and the error might pop up again later or upon reboot.

---

### Post by lodravah on 2008-04-28
You could do a clean install. I know this isn't an option for many, but I find that if my system becomes somewhat unstable or slightly buggy, I just do a reinstall. Personally I keep my box as free of all files (DL's, mp3's, *.doc's etc.) so that I can reinstall at any point in time without having to copy files.

Just a suggestion, mate :)

---

### Post by nowshining on 2008-04-28
> **pcdoctor said:**
> If this fixes your problem, please give me a "thank you".

I think I might have fixed this problem, at least temporarily.
I went to a desktop that wasn't having this problem and right clicked on the d3lphin folder in the location below:

/home/username/.kde/share/apps/d3lphin

Desktop with 8.04 doesn't have this problem.
I used it to see what was different.

Access permissions
owner: can view & modify content
group: forbidden
others: forbidden

Ownership
user: username
group: username

On the pc with the error it has

Ownership
user: root
group: root

I changed both the user and group to my username but when I did, it said "username" group doesn't exist.  It does exist on this pc so I tried.

Ownership
user: username
group: root
and click apply changes to all subfolders and their contents.

This might just be a temporary fix and the error might pop up again later or upon reboot.

hmmm i haven't looked into that folder afterawhile, but the permissions on the folder was the same as the fixed one, and still no change, by the way

sudo chown -R username:username pathtofolder

is the CLI way to change owner/group access. :)

i've even tried deleting the folder still no avail..

>  
You could do a clean install. I know this isn't an option for many, but I find that if my system becomes somewhat unstable or slightly buggy, I just do a reinstall. Personally I keep my box as free of all files (DL's, mp3's, *.doc's etc.) so that I can reinstall at any point in time without having to copy files.

Just a suggestion, mate 


na! I won't re-install over something as simple as this when everything else so far works okay/fine.

By the way you could create anoter partition and move your /home folder to it so if you do install you won't lose anything or get another HD and backup to it. :)

---

### Post by Xiong Chiamiov on 2008-04-29
It works until you sudo dolphin, yes?

Sudo is really only meant for command-line stuff; when launching GUI apps use kdesudo instead (or gtksudo if you prefer).

EDIT: Hey, Oildale!  I'm from Taft, btw.  We tend to make Oildale the brunt of our jokes, but I hear that we are the ones who get it from everyone else.  Oh well. :)

---

### Post by nowshining on 2008-04-29
> **Xiong Chiamiov said:**
> It works until you sudo dolphin, yes?

Sudo is really only meant for command-line stuff; when launching GUI apps use kdesudo instead (or gtksudo if you prefer).

EDIT: Hey, Oildale!  I'm from Taft, btw.  We tend to make Oildale the brunt of our jokes, but I hear that we are the ones who get it from everyone else.  Oh well. :)

wow now your the closest i've seen on the net to me, I mean via alive and chatting, lolz Yes we are are Oildalians over here. ;) or however you spell it.

I know using kdesu works but then again it looks ugly :/ and of course the settings are all off than what I have.

---

### Post by Xiong Chiamiov on 2008-04-29
Dolphin should look the same whether you kdesudo or just plain sudo it, right?

When you launch it as root, it'll use settings for a different user (root), so yeah, it'll look different (which is probably a good idea).  But what I'm not saying to use that for normal use, just when you need to have a root file manager window open.  Is that what you understood me to be saying?

---

### Post by nowshining on 2008-04-29
sudo opens dolphin with my prefs, and yeah I kind of know about the look thing, it's a bug in kde, altho after updating glib and pango some such as synaptic look fine now in the theme I chose.altho ksystemlog doesn't. Altho the progress bars in some pango programs look grey and take the color of the windows background color which I have set for win2k color. and I attached the following screenshots of what using each look like and of course I unmaxed the windows for a smaller file size.

gksudodolphin.png  (56.9 KB)
kdesudodolphin.png (56.7 KB)
kdesudolphin.png (56.9 KB)
sudodolphin.png (25.2 KB)

---

### Post by ricardisimo on 2008-05-31
I get this during regular, non-superuser sessions. It's quite annoying. Does resetting the permissions on my Home folder actually help? Any ideas appreciated.

---

### Post by Xiong Chiamiov on 2008-05-31
> **ricardisimo said:**
> I get this during regular, non-superuser sessions. It's quite annoying. Does resetting the permissions on my Home folder actually help? Any ideas appreciated.
When you run dolphin as root once, it will save the bookmarks file when you exit, resetting the permissions on it to be owned by root.  You don't need to change the permissions on the whole home folder, just that file (~/.kde/share/apps/d3lphin/bookmarks.xml).  To prevent that from happening, use kdesudo instead when launching graphical apps.

---

### Post by ricardisimo on 2008-06-01
I know all about gksudo with graphical apps from my Ubuntu comp. What I'm talking about is just launching dolphin regularly (via the panel launcher or whatever), using it and then exiting... then I get the error message.

I'm assuming you're not suggesting I run dolphin in root all the time. That would be somewhat silly.

---

### Post by Xiong Chiamiov on 2008-06-01
What I was trying to say was that the error will come up whether or not you're launching dolphin as root.  In fact, the error will actually only come up when you *aren't* launching as root, since that's when you won't have sufficient permissions.

The problem is caused by improperly launching dolphin once, and it will continue to give you problems until you fix the permissions.

From the phrasing on your post, it seemed that you hadn't yet tried resetting the permissions on the bookmarks file.  Therefore, I was suggesting that you do so.  If you follow good sudo-ing procedures, then you won't have to deal with it again.

---

