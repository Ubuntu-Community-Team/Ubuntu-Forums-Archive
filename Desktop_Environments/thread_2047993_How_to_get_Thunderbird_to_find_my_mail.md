---
title: "How to get Thunderbird to find my mail"
date: 2012-08-25
forum: Desktop Environments
---

### Post by andycivil on 2012-08-25
My old computer crashed and we got a new one and installed Ubuntu 12.04. I restored my mail backup to .thunderbird and started it, but it tries to create a new profile. A new profile appeared in my .thunderbird directory. I edited the profiles.ini file to point to the old 'restored' profile, but it STILL refuses to come up with my existing email account.

---

### Post by user333 on 2012-08-25
Try [Tools] -> [Import...]

I'm not sure if that is what you need, but you can give it a try.

---

### Post by andycivil on 2012-08-26
No, "Import..." only imports from other programs, not from a backup. (The next screen where you get a choice of installed mail programs to import from is blank, because there are no other mail programs installed.) Thanks for the thought, anyone else?

P.S. I'm super angry with Thunderbird right now, because what I want to do is just create a blank account, find out where the folders are, move the old mail in, set up the server settings, and go from there. But it won't let me create a blank account - it INSISTS that it works. But I don't have an email account where I'm willing for it to fetch mail at this point.

---

### Post by oldfred on 2012-08-26
I regularly copy my XXXXX.default from one computer to another. Since I always copy to the same place I do not even have to update my profile.ini.

But on a new install I have to start Thunderbird once to create the profile.ini and the new XXXX.default. I then just edit profile.ini to my old XXXX.default & it works. 

I also have a long path in my profile.ini as I have it in a shared NTFS partition and use it from XP and multiple installs of Ubuntu. Same with Firefox.

new 
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by andycivil on 2012-08-27
Thanks Old Fred, I know that's how it's SUPPOSED to work. You know, I found that some of my mail was corrupted, and I'm going to assume that this problem was specific to me, perhaps my profile was also corrupted in some way and that's why Thunderbird wouldn't accept it.

I fixed my problem by creating a dummy email account just so that I could make Thunderbird happy enough to create an INBOX for me - then I copied my old mail in there. It was a kludge, but at least I have my mail back now. I'm going to mark the thread solved, in any case.

---

