---
title: "Kubuntu sound problem"
date: 2006-09-11
forum: Desktop Environments
---

### Post by rogier.de.groot on 2006-09-11
Ok, I've just installed KUbuntu, installed support for restricted media formats, flash, java, netbeans (unfortunately not in the repository like eclipse is), and using the commandline I've added another user, since I'm not the only one using the system.
Then I log in as the new user. KDE comes up fine, but the volume thing in the systray has a red cross icon over it, and KMix doesn't seem to realise the system has a soundcard. Using the original user account (generated during install) I do have sound, and KMix recognizes my soundcard just fine. WTF?
I also tried using the "System settings" GUI to add another user
account but that account has the same issue.
Anyone know how to fix this? Thanx.

PS.1 Originally I was to lazy to download the KUbuntu install CD so I used the server install CD to get a basic system & apt-got kubuntu-desktop. Had the same problem, so I figured my install method screwed things up (since the server kernel doesn't (?) support sound), downloaded the KUbuntu alternate CD (I needed LVM) and reinstalled.

PS.2 (K/X)Ubuntu ships with 5+ desktop environments, 5+ word processors, 5+ webbrowsers, 5+ mailclients, 5+ just-about-everything but with only one Java IDE, Eclipse, which I intensely dislike, how come NetBeans isn't in the repository too? It's open-source-ish too isn't it?

PS.3 This machine originally had Xubuntu on it, which supposedly is a light-weight window manager. So how come Kubuntu seems faster?

PS.4 Using the system installed from the server install CD (see PS.1) I couldn't get amaroK to play MP3 after installing libxine-extracodecs. Haven't tested the new install yet, but weird.

---

### Post by anllogui on 2006-09-11
Belong the 2 users to the same groups?
I think there is a group called "sound" (I can't check it, because I don't have linux at job). 
When I used Debian, I had this problem. The new user can't access to the sound device because he doesn't belong to the group allowed.

---

### Post by rogier.de.groot on 2006-09-11
The user is in the "users" group, which sounds like a pretty logical group to put users in to me ;) The other user, the one with sound, is in the "admin" group, since he (well, me) is an administrator and should be able to sudo. The other user shouldn't be able to sudo at all - as soon as I figure out how to set up sudo to disallow users from the "users" group anyway. I'll see about that "sound" group idea when I get back home though (no kubuntu @ school either). Thanx for the suggestion.

---

### Post by rogier.de.groot on 2006-09-11
Ok, making the user a member of the "audio" group solves the problem, and adding a couple more usefull groups, like "plugdev" gives it the access it should have. Wish someone had put this in some manual or something...
On one of my PSes, amaroK still doesn't play MP3s. Even though I did everything in the "RestrictedFormats" page. I have solved this problem though, by installing amarok-arts & telling amarok to use arts as it's engine. Not sure if this screws up something else it normally uses xine for.

---

