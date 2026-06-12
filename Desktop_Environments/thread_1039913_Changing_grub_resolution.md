---
title: "Changing grub resolution"
date: 2009-01-15
forum: Desktop Environments
---

### Post by mreynolds on 2009-01-15
Hello all. I was searching for a list of the vga= values available to use to change grub's resolution. I found the following thread here at the ubuntu forums;

[http://ubuntuforums.org/showthread.php?t=127134](http://ubuntuforums.org/showthread.php?t=127134)

Sadly, the consensus in that thread is that it's impossible to change the resolution of the grub menu. :confused: I wanted to provide the following table of available resolutions, and the value to enter to get them for future searchers. I tried to post to the original thread, but it's to old and has been closed or something. Anyway, here is a table of resolutions that grub supports.
```

                +-------+-------+--------+---------+---------+
                |640x480|800x600|1024x768|1280x1024|1600x1200|
+---------------+-------+-------+--------+---------+---------+
|256    (8 bit) |  769  |  771  |  773   |   775   |   796   |
|32,768 (15 bit)|  784  |  787  |  790   |   793   |   797   |
|65,536 (16 bit)|  785  |  788  |  791   |   794   |   798   |
|16.8M  (24 bit)|  786  |  789  |  792   |   795   |   799   |
+---------------+-------+-------+--------+---------+---------+

```

Add one of the 3 digit values from the table above to the kernel line in an entry;

EX: kernel /vmlinuz ro root=/dev/sda2 vga=799

Your grub menu will now be 1600x1200, using 24bit color.

I was hoping the code tags would display the table in a nice monospace font so it looks nice in the post, but they don't. If you copy the table as is and paste it into a text file with a monospace font, it will line up properly and look pretty. I usually paste the table as a comment right into my grub.conf for future reference.

cheers :guitar:

The link provided in the post mentioned lists the same table as above ;) Mine is slightly more ascii-prettified though

---

### Post by jpkotta on 2009-01-15
I've never heard of changing the resolution of Grub.  It's probably impossible, but I won't say it is for sure.  Those vga= parameters are for the kernel, the kernel is not running when Grub is (Grub's *raison d'être* is to load the kernel).

You can make grub look nicer with a background.  See [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

BTW, code blocks show up as monospaced for me -- your table looks fine.  If it doesn't look right for you, you should look at the font settings for your browser.

---

