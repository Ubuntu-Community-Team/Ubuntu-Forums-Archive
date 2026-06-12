---
title: "can't start up - out of disk space??"
date: 2006-01-24
forum: Desktop Environments
---

### Post by hellohenry on 2006-01-24
hey I just installed the file linked on the 'beginners' forum with all the different programs, and it was fine, I checked a few programs including Azureus, the gimp paintshop one, etc and they worked ok. I then restarted the computer since Firefox wasn't working properly (presumably because of the plugins I downloaded, I thought) only to find I couldn't log in anymore. it said that there wasn't enough diskspace to write to the administration folder for the user login, or words to that effect. I tried logging in with my other username and it didn't work either. can anybody help? can I fix it if I burn a boot cd on my friends computer?
thanks a lot
henry

---

### Post by dcstar on 2006-01-24
[QUOTE=hellohenry]hey I just installed the file linked on the 'beginners' forum with all the different programs, and it was fine, I checked a few programs including Azureus, the gimp paintshop one, etc and they worked ok. I then restarted the computer since Firefox wasn't working properly (presumably because of the plugins I downloaded, I thought) only to find I couldn't log in anymore. it said that there wasn't enough diskspace to write to the administration folder for the user login, or words to that effect. I tried logging in with my other username and it didn't work either. can anybody help? can I fix it if I burn a boot cd on my friends computer?
thanks a lot
henry[/QUOTE]
Select the "recovery mode" boot option, and then try and log in with your root password.

Then delete everything in your /tmp directory and use the "reboot" command.

That may give you enough disk space to boot up normally, then you may have to manually uninstall packages to free up more space.

---

