---
title: "Nautilus [Create date] bulk rename issue"
date: 2019-03-23
forum: Desktop Environments
---

### Post by stefanita1201 on 2019-03-23
I have been searching for a terminal rename command for renaming multiple photo files and I manage to find one, but the process was so tricky and long. But shortly after I discovered that I have Nautilus bulk rename included in F2 command when I selected multiple files, and I was so glad. Until I dug a little deeper under the surface.

Unfortunately the rename command allows you to append the filename with usual numbers (well done!) and whatever other free text. However, on metadata type of appending doesn't work.

I used the terminal to check exiftool metada for all files that I intended to rename, and the data was there.

And I tried to add it in Nautilus again, and for the *somefilename.ext *I got the output *somefilename[Create date].ext* instead of expected format *somefilename.timeHours.Minutes.Seconds.ext*.

And then I returned back to terminal. Unfortunately "exiftool '-filename<CreateDate' -d %H.%M.%S%%-c.%%le -r *.ext" which worked beautifully deleted as well my custom previous name, giving me only the output *H.M.S.ext*.

I tried some "for" command, but I got stuck. I am not such an advanced linux-user.

So, in the end, I wonder why the so beautiful F2 command in Nautilus doesn't add automatically the metadata date numbers? Is it me (most likely), or is any one out there who can shade a bit of light in my darkness?

Digging didn't help (I ended up in a forum with only three lines which confused me more).

Thank you in advance for your time!
 
I am using the latest Ubuntu 18.10 updated and nautilus 3.26.4.

---

