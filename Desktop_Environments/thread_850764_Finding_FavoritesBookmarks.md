---
title: "Finding Favorites/Bookmarks"
date: 2008-07-05
forum: Desktop Environments
---

### Post by fishergirl on 2008-07-05
I had a computer that I had installed Firefox, which had a ton of bookmarks saved.  That computer 'crashed' cause the video stuff all went out on it, but the hard drive is still ok.  So I bought the stuff to make it into an external hard drive and plugged it into my newly refurbished computer.  I am having problems finding out how to transfer my favorites/bookmarks from that hard drive to either IE or Firefox.  Does anyone know how I find and move this file?
The other issue I have is when I try to install Firefox on the new computer, I can only get Firefox 3, and then I can use it but if I close it and open it again it wont work.  Does anyone know where to get one of the 'old' reliable versions of Firefox or how to fix this issue?
Thanks.
(Sorry if this is a duplicate post from a few days ago, I cant seem to find the place I may have posted before on these issues.)

---

### Post by tamoneya on 2008-07-05
/home/username/.mozilla/firefox/*.default/bookmarks.html

To revert to firefox 2 run the following commands:```
sudo apt-get update
sudo apt-get remove firefox-3.0
sudo apt-get install firefox-2
```

---

### Post by fishergirl on 2008-07-08
Where do I go to enter this info?  Explain this to me like I'm a computer idiot...I am a bit of one.  
Where/how to I put the info for the bookmarks?

---

### Post by tamoneya on 2008-07-08
You should save the file that i mentioned above somewhere that you can find it later.  Then run the commands in the box in terminal: Applications -> accessories -> terminal.  After that just go and replace bookmarks.html.

---

### Post by fishergirl on 2008-07-08
Ok, then do you know how I find the old bookmarks file?  I have looked and searched all through that hard drive with no luck.  But I am not sure what the name would be.  I have done searches for favorites and bookmarks.

---

### Post by tamoneya on 2008-07-08
> **fishergirl said:**
> Ok, then do you know how I find the old bookmarks file?  I have looked and searched all through that hard drive with no luck.  But I am not sure what the name would be.  I have done searches for favorites and bookmarks.

Yes i know where it is.  I  already mentioned it:
/home/username/.mozilla/firefox/*.default/bookmarks.html

Where username is your username and * is a random string.  There should only be one of them anyways but I just dont know what it will be on your computer.  Mine is cj5c4kzw.default.

---

