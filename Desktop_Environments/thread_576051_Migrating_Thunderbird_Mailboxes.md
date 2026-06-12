---
title: "Migrating Thunderbird Mailboxes"
date: 2007-10-14
forum: Desktop Environments
---

### Post by alpinegroove on 2007-10-14
I am just starting out with Ubuntu 7.10 which I am using on a Compaq Athlon 2.08gh. 
I have never used Linux before.
My Windows XP is no longer available, but I have a cd with the XP Thuderbird files that I copied from: C:\Documents and Settings\user\Application Data\Thunderbird
This folder contains all my mailboxes and other TB info.

From what I read on the site, I understand that I need to copy my XP Thunderbird folder into either of the following: 

/home/desktop/.mozilla-thunderbird
/home/desktop/.thunderbird

My user name under Ubuntu is "desktop."
But these folders do not exist in my Ubundu. Am I supposed to create one of them and then copy my XP folder into it?
Do I have to include the "." before mozilla or thunderbird?
I tried to create such a folder and copy all my TB folder into it. Nothing happened. What next?
Starting to fear that my messages cannot be migrated...
Thank you!

---

### Post by aysiu on 2007-10-14
The folders *may* exist, but the . means they are hidden. If you view hidden files and still can't see them, you can create them, and the . is necessary.

It's definitely /home/*username*/.mozilla-thunderbird

Make sure that the folders and files directly underneath ~/.mozilla-thunderbird are your profile folder (usually a mix of numbers and letters) and profiles.ini (possibly also appreg).

There should be only one profile folder; otherwise, it may be using a newly created one instead of the one you copied from XP.

---

### Post by alpinegroove on 2007-10-14
yes, they were hidden. i came back to report that i had solved it. thanks anyway. every little step is taking me 2 hours with this new os.

---

### Post by alpinegroove on 2007-10-14
It turns out it is not solved yet.
After migrating Firefox's setting, I am now having problems with TB again.
All of a sudden, when I try to run TB, I get the following message:
TB is already running, but is not responding. To open a new window, you must first close the exiting TB process, or restart your system.

The only way to bypass this, is to delete everything in the TB folder. They it recreates its folders and starts, but of course without my mailboxes.
Whenever I replace the contents of the folder with my own files, I get the message above.
help please...

---

### Post by aysiu on 2007-10-14
Instead of deleting the Thunderbird folder, close the error message and press Alt-F2. In the Run dialogue box type ```
killall thunderbird-bin
``` Then try to launch Thunderbird again.

---

### Post by duppydrew on 2007-10-19
worked fine for me

---

### Post by TeaSwigger on 2007-10-19
Hello and welcome,

You'll get it. If you still have any problems, this article might apply:
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
noting the parts about "prefs.js" - I had to change the paths in this file from old windows paths to the current linux paths.

> **alpinegroove said:**
> every little step is taking me 2 hours with this new os.

Yeah it might for a while, it was for me, but then it was once like that for windows. It's great to get off the windows gravy train though, and moreover this is an amazing system. Hang in there :)

---

### Post by deinonychus on 2007-10-20
I had a similar problem migrating my Thunderbird inbox from an XP install to my new Feisty install. When I would delete the default TB profile folder and paste in my old one, I would get the same error message you discuss above. 

What finally worked was to open the default TB inbox folder within the .mozilla-thunderbird folder ( it was titled something like nhap3cd2.default)  and delete the contents, and paste in the contents of my old one. I left the profile.ini file that was also in the the .mozilla-thunderbird folder alone. Then, when I restarted TB, I had my mail, folders, and account settings migrated. The only problem was that my folder names were changed from their original titles to gibberish, but their contents were undisturbed and it was fairly simple to retitle them. 

Hope this helps.

---

