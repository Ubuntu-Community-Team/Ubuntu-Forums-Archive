---
title: "What should I clean out in Ubuntu in laptop for sale?"
date: 2009-01-21
forum: General Help
---

### Post by friendofpugs on 2009-01-21
Hi All!

Sorry to be a drag, but I couldn't find any recommendations searching through the forums. Here's the situation: I'm selling my old laptop on eBay (Dell XPS 1210) and I want to clean out any personal details that might linger in Ubuntu 8.04 LTS. What things should I look for? Or, should I just reinstall Ubuntu to cover everything up? I've got the computer running great, wifi, temp. sensors, etc., and I'd hate to take the time to reinstall to wipe it clean. I'm wondering what are the top three or four things you'd do to clean up your Ubuntu laptop, short of reinstalling the OS, before giving it away to a total stranger. I'd think Linux would be quite adept at this sort of thing, multiple users, etc. 

Thanks for any recommendations you have.;)

---

### Post by trentscott4 on 2009-01-21
Do a reinstall.  The amount of time it would take to ensure all your files/personal data was whiped will be 10x that of a simple reinstall.

Or, you could just run a low level format utility like Darik's Boot and Nuke (dban.org) on the drive and sell it without a working OS.

---

### Post by stefangr1 on 2009-01-21
The safest way would be to use the live cd to erease your disk completely with the build-in command:

shred -vfz -n 1 /dev/hda

which will overwrite your disk with zero's, and then do a fresh reinstall.

If there's not much to hide you can just erase your passwords from firefox and the personal files from your home directory, and maybe reset your user password.

---

### Post by hangfire on 2009-01-21
> **friendofpugs said:**
> Hi All!

Sorry to be a drag, but I couldn't find any recommendations searching through the forums. Here's the situation: I'm selling my old laptop on eBay (Dell XPS 1210) and I want to clean out any personal details that might linger in Ubuntu 8.04 LTS. What things should I look for? Or, should I just reinstall Ubuntu to cover everything up? I've got the computer running great, wifi, temp. sensors, etc., and I'd hate to take the time to reinstall to wipe it clean. I'm wondering what are the top three or four things you'd do to clean up your Ubuntu laptop, short of reinstalling the OS, before giving it away to a total stranger. I'd think Linux would be quite adept at this sort of thing, multiple users, etc. 

Thanks for any recommendations you have.;)

It may be too late, but if user data is kept in the (for instance) /home partition, it is easy to nuke that & Swap partitions only, and leave the O/S install alone.

I also vote for Derek's Boot and Nuke for a complete system wipe, followed by a reinstall.

I suggest against just formatting the drive. I have freeware data recovery tools that will easily recover all typical file formats in all contiguous data files. Chances are good that most of your user files are contiguous (no gaps in the sectors) and that the new O/S install will simply overlay the old, leaving your user data still on disk (albeit the directory structure destroyed by the format).

-HF

---

### Post by friendofpugs on 2009-01-21
> **hangfire said:**
> It may be too late, but if user data is kept in the (for instance) /home partition, it is easy to nuke that & Swap partitions only, and leave the O/S install alone.

How would I go about doing this? I really don't have anything sensitive on the laptop, I just used it for school, writing papers, surfing the net, some web design, not much else.

---

