---
title: "Can anyone lend a hand?"
date: 2009-04-05
forum: General Help
---

### Post by Lori700698 on 2009-04-05
Dipstick here deleted my etc files for Citadel and Webcit in my haste to clean up a bad upgrade. Are these files kept somewhere where I can make a copy?

Thank YOU!

---

### Post by wolfen69 on 2009-04-05
if those files were deleted, you are probably up a creek without a paddle.

and next time, backup your files and do a clean install. you'll be much happier with the results.

---

### Post by Lori700698 on 2009-04-05
I thought I was covered, but the nightly back up I thought was happening on my server is not, the file is empty.  I do not want to reinstall, I've spent months configuring it. I could have swore at one time I saw a list of files here on Ubuntu that I could open up and copy.

---

### Post by Lori700698 on 2009-04-06
FYI, this was VERY fixable, took less than 1/2 hour!

```
sudo apt-get -y --purge remove package name && sudo apt-get -y install package name
```

OR

To see the actual name of what you need to remove
```
sudo dpkg --list |grep -i package name
```

To remove package
```
sudo dpkg -r package name
```

Then to remove configs.
 ```
sudo dpkg --purge package name
```

The second option worked better for me because I had errors from dependencies that needed removed too.  So I had to take my time and read the out-put and delete the dependencies then did the -r and --purge a couple times to get it all removed with no errors.

Did a re-install
```
sudo apt-get install package name
```

And life was all good again, I have my mail server back!  After all of the playing around I've done with my Ubunta machines I can't remember everything and I forgot this simple rule of removing unwanted packages, I was so busy looking for a copy of the etc files that I deleted in my haste I didn't think to do a full remove & purge.

Thanks All
Lori

---

