---
title: "Dolphin not searching tags or ratings"
date: 2022-02-26
forum: Desktop Environments
---

### Post by Deanobats on 2022-02-26
I may have solved this one already, but I'm not sure how or why, so I would appreciate some help in understanding why what I've done works.

I've been using Dolphin to add ratings to files and also created some tags which I have added to some files. If the files are located under the home directory, then searching by tag or rating worked fine, but for a mounted USB drive, the search box would not show searching for ratings and searches for tags only showed up for files under home, although searching for file names on the USB drive did work. I checked baloofilerc and sure enough, the usb drive was set to be excluded from search (though this would not explain WHY file search for names still worked, but hey).

Anyway.. I removed the exclusion for the mounted USB drive. Now I can search by ratings on the USB drive (at least the option to appears), but it still only returns files in the home directory, the same for any tags. I did get it to work by enabling 'index file content', so now I can get search returns on the mounted USB drive.

So my questions are:

Why did I get filename search returns on the USB drive when baloofilerc set it to be excluded?
Why did Dolphin return searches for tags and ratings from home directories when 'index file content' was off, and why did it need to be on to return the same searches from a USB drive?

As I said, it all works, but I also don't understand why.

---

