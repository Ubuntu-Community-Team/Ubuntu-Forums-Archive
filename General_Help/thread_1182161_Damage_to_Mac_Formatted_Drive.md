---
title: "Damage to Mac Formatted Drive"
date: 2009-06-08
forum: General Help
---

### Post by CosmicSunset on 2009-06-08
I have an external USB hard drive that was formatted on a mac.  I took it to a friend's house and connected it to his computer running Ubuntu.  The drive seemed to work ok but was pretty slow (his USB controller may not be version 2.0).
 
 We moved the drive to a computer running Windows XP with MacDrive 7 and the transfer rate improved but weird things started happening like Windows saying it couldn't copy a file that we had just dragged and dropped because the file couldn't be found.  After a while of trying to use the drive like this it started acting like it was read only and Windows started giving us permissions errors.

Now when I connect the drive to a Windows Vista computer with MacDrive 7 more strange errors occur.  Sometimes a folder that has files in it will appear empty.  Other times the files show up but when I try to copy them I get a "file not found" error.

The drive had previously worked fine with both Windows Vista and Windows XP with MacDrive 7 so I'm wondering if Ubuntu did something to the drive that could be causing this problem.  There was a small amount of data on the drive that wasn't backed up and I'd like to retrieve it if possible.

Kris

---

### Post by coffeecat on 2009-06-08
> **CosmicSunset said:**
> I'm wondering if Ubuntu did something to the drive that could be causing this problem.

I think that's unlikely because I found through trial and error that Ubuntu cannot write to (only read) the journalled version of HFS+, the Mac filesystem, which is most likely what your drive was formatted with. If you format a drive in the MacOS Disk Utility app, it defaults to the journalled version of HFS+. If you choose the unjournalled version, however, Ubuntu can write to it.

Have you tried connecting the drive to a Mac to see what that makes of it? One possible cause of what you're seeing is a physically failing drive, so you'll want to backup that data as soon as you can. If I was in your postition, I would use a Mac to do that, not Windows - or Linux - because it's a Mac filesystem.

---

