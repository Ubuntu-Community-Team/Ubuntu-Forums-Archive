---
title: "Loosing creation date when copying files"
date: 2015-09-07
forum: Desktop Environments
---

### Post by mahavishnu on 2015-09-07
When I move files to my Ubuntu PC (e.g. pictures from SD card to HD), the ´Date modified´ "updates" to the current date & time.

Is there a way to keep the original date? Because I didn't modify them, I only MOVED them.

I don't believe this is happening !!!  Copying has nothing to do with creation !!!!

Creation date is an important metadata of files.  It may be a backup, a directory reorganization, anything!

Please CORRECT this.

---

### Post by mahavishnu on 2015-09-07
The 'date modified' of a file seems in nautilus to be updated whenever that file is rewritten, not only when the content is changed. So if I move a file between discs, its date modified gets updated. I find this really unhelpful. An extreme example is that in switching over to Ubuntu, I created an archive disc for all the data files on my old PC - they now all share the same date modified, making it impossible to distinguish between older and newer versions of similar files.

Is there any way to change the rules for 'date modified', or to access a 'content modified' field instead?

---

### Post by coffeecat on 2015-09-07
Let's get one thing clear to start with. 

> **mahavishnu said:**
> 
Please CORRECT this.

The forum members, staff included, are all volunteers, mostly ordinary users. Making peremptory demands of the forum membership to do things outside of their control won't get you anywhere.

Having said that, I agree with you - changing the modification date is data corruption in my view. However, I haven't see this behaviour for many years now, and I cannot reproduce it now. Using the file manager to copy a file from an SD card to my hard drive in Ubuntu preserves the modification date. There was a bug in Nautilus way back in 2008 which did this, but it has long since been fixed, so my first question is: which version of Ubuntu are you using? Also:

What is the filesystem on the SD card?
How are you mounting the SD card?
When you refer to your HD, do you mean a folder within your Ubuntu OS, or a separate partition for data? If the latter, what filesystem does this have, and how are you mounting it?

---

### Post by mahavishnu on 2015-09-07
sorry, coffeecat. The "Please CORRECT this" if for the serious bug related.
Copying a file is not creating a new file with a new "date created" information.

All file dates from the pictures I copy from my SD card are changed to the date the copy takes place. Thats a catastrophical bug from my perspective because for me its important to see when the picture has been taken. Thats the only way to Sort pictures withoud the need of a full blown picture manager that reads the exif -information. In the windows world copying a file means copy. Changing the time stamps means loosing the ability to see when the picture has been made original. I dont understand why that is not an option ? 

I managed to get the things solved with Grsync, but with any file manager (nautilus, nemo, gnome comander) misses the date created.

I didn't mean any peremptory demand. Sorry one more time.

---

### Post by coffeecat on 2015-09-07
Did you not understand from my post that this should not be happening? In fact it doesn't happen if you use a supported version of Ubuntu. So - what version of Ubuntu are you using? And what about the other questions I asked?

---

