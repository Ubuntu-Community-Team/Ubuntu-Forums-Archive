---
title: "Can't start up firefox..."
date: 2005-08-18
forum: Desktop Environments
---

### Post by YourSurrogateGod on 2005-08-18
Ok, I'll admit that I've messed with the installation of firefox because I figured that it would be better to simply go over to standard mozilla (there are a few small features that I prefer in just mozilla.) I went back and reinstalled firefox, fixed all of the broken packages and I still can' get firefox to start up. Whenever I click on the icon, it simply has small bar show up at the bottom stating that firefox is being started, but in the end, you don't see the browser window. What's going on?

---

### Post by buldir on 2005-08-18
Might be a permissions or a profile problem.  Can you run Firefox as root?  Backup your bookmarks and anything else you want.  You can always uninstall (complete removal) Firefox via Synaptic.  Then find any Firefox directories/files that might remain and remove them.  Remove /home/user_name/.mozilla.  Now, reinstall Firefox via synaptic...see what happens.

---

### Post by YourSurrogateGod on 2005-08-18
[QUOTE=buldir]Might be a permissions or a profile problem.  Can you run Firefox as root?  Backup your bookmarks and anything else you want.  You can always uninstall (complete removal) Firefox via Synaptic.  Then find any Firefox directories/files that might remain and remove them.  Remove /home/user_name/.mozilla.  Now, reinstall Firefox via synaptic...see what happens.[/QUOTE]
This is kinda off-topic, but why does the mozilla folder have a period before it?

---

### Post by Lambert on 2005-08-18
Anything with a . before the name is a hidden folder/directory.

---

### Post by YourSurrogateGod on 2005-08-18
[QUOTE=Lambert]Anything with a . before the name is a hidden folder/directory.[/QUOTE]
Thanks.

---

### Post by YourSurrogateGod on 2005-08-20
Weird, after rebooting my box, firefox worked... oh well.

---

### Post by jouni on 2005-08-22
[QUOTE=YourSurrogateGod]Whenever I click on the icon, it simply has small bar show up at the bottom stating that firefox is being started, but in the end, you don't see the browser window. What's going on?[/QUOTE]

I'm having a similar problem. I'm trying out Ubuntu using the live cd (I currently have Debian sarge on my hard drive), and while it certainly looks good, I don't want to lose my bookmarks, stored passwords, etc. when installing Ubuntu. I tried copying over my .mozilla directory from the hard drive into the home folder that I get when running the live cd, but then Firefox won't start. Upgrading Firefox to 1.0.6 didn't help. Is there a way to get debugging information from Firefox?

Perhaps another option is to create a new Firefox profile and somehow migrate the contents of the old one. I wonder if there is a tool for that? I moved my .mozilla folder out of the way, started Firefox and clicked on File/Import. Firefox starts up an "Import Wizard", but it just says "Import Preferences, Bookmarks, History, Passwords and other data from:" (and a large empty space below that), and nothing happens when I click on Next.

---

### Post by YourSurrogateGod on 2005-08-22
[QUOTE=jouni]I'm having a similar problem. I'm trying out Ubuntu using the live cd (I currently have Debian sarge on my hard drive), and while it certainly looks good, I don't want to lose my bookmarks, stored passwords, etc. when installing Ubuntu. I tried copying over my .mozilla directory from the hard drive into the home folder that I get when running the live cd, but then Firefox won't start. Upgrading Firefox to 1.0.6 didn't help. Is there a way to get debugging information from Firefox?

Perhaps another option is to create a new Firefox profile and somehow migrate the contents of the old one. I wonder if there is a tool for that? I moved my .mozilla folder out of the way, started Firefox and clicked on File/Import. Firefox starts up an "Import Wizard", but it just says "Import Preferences, Bookmarks, History, Passwords and other data from:" (and a large empty space below that), and nothing happens when I click on Next.[/QUOTE]
Well, like I said, I simply rebooted and everything worked fine. Other than that, I'm not sure what other type of advice I could give you. You could tinker around with the .Mozilla folder and try to get your bookmarks to a safer directory before simply reinstalling everything (which will inevitably overwrite everything that was previously there.)

---

### Post by 5-HT on 2005-08-22
[QUOTE=jouni]I'm having a similar problem. I'm trying out Ubuntu using the live cd (I currently have Debian sarge on my hard drive), and while it certainly looks good, I don't want to lose my bookmarks, stored passwords, etc. when installing Ubuntu. I tried copying over my .mozilla directory from the hard drive into the home folder that I get when running the live cd, but then Firefox won't start. Upgrading Firefox to 1.0.6 didn't help. Is there a way to get debugging information from Firefox?

Perhaps another option is to create a new Firefox profile and somehow migrate the contents of the old one. I wonder if there is a tool for that? I moved my .mozilla folder out of the way, started Firefox and clicked on File/Import. Firefox starts up an "Import Wizard", but it just says "Import Preferences, Bookmarks, History, Passwords and other data from:" (and a large empty space below that), and nothing happens when I click on Next.[/QUOTE]

It shouldn't be a problem to simply migrate your existing profile for use in Ubuntu.

As you said, I can see two options available (make sure you have a backup of your existing profile just in case).

One option would be to simply copy over specific files from your existing profile, and overwrite them into the new  one (not sure on which files these are, I simply just copy over "bookmarks", but for cookies/passwords etc..a quick search on the firefox forum should yield some results).

Another option would be to simply copy over your entire existing profile into the ~/.mozilla/firefox/ directory.

The problem here is that you need to let firefox know to use that profile instead of the default one.

The Firefox website has a walk-through for this: 
[http://www.mozilla.org/support/firefox/profile#backup](http://www.mozilla.org/support/firefox/profile#backup)

That walk-through also describes how to use a profile in a directory other than ~/.mozilla/firefox/  so all of the recommendations may not be necessary.

Possibly just modifying the "Path=" in "profiles.ini" to point to the profile you'd like to use may be enough.

Hope this helps.

---

### Post by jouni on 2005-09-03
[QUOTE=5-HT]One option would be to simply copy over specific files from your existing profile, and overwrite them into the new  one (not sure on which files these are, I simply just copy over "bookmarks", but for cookies/passwords etc..a quick search on the firefox forum should yield some results).[/QUOTE]

Just in case someone is searching for this later: [http://kb.mozillazine.org/Profile_Folder](http://kb.mozillazine.org/Profile_Folder) has a list of the files in the profile folder.

> Another option would be to simply copy over your entire existing profile into the ~/.mozilla/firefox/ directory.

Thanks for the link, but this by itself didn't help, since the old profile was somehow incompatible with the new Firefox. But browsing the Firefox forums lead me to the instructions at [http://kb.mozillazine.org/Standard_diagnostic](http://kb.mozillazine.org/Standard_diagnostic), which helped: I started Firefox in safe mode and uninstalled all extensions, and now I have a working profile with all my old bookmarks, cookies and stored passwords.

---

