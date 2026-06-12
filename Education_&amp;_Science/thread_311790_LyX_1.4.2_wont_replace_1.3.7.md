---
title: "LyX 1.4.2 wont replace 1.3.7"
date: 2006-12-03
forum: Education &amp; Science
---

### Post by Campitor on 2006-12-03
Hello all:

 I have LyX 1.3.7 installed on my dapper machine. I downloaded LyX-1.4.2 from here: [http://wiki.lyx.org/LyX/Download]("http://wiki.lyx.org/LyX/Download") and installed it using gdebi.  The program installed Ok, but now I have two versions of LyX coexisting on my machine. If I select LyX from the menu, or type lyx from a terminal, I get version 1.3.7 starting. To get the new version I have to manually type
```
 /usr/local/bin/lyx 
```I cannot uninstall lyx-qt because it depends on lyx-common which is used by the new version.  Do I just have to live with both version, or is there a way of getting rid of the 1.3.7 version?

thanks for your help

Camp

---

### Post by kleeman on 2006-12-03
I suggest you use the 1.4.3 version as there are several important bugfixes. The deb on that page is a checkinstall one so will have no dependencies and you can nuke the lyx-common. By default the compiled from source version puts things in /usr/local/bin. 

BTW compiling lyx from source is not hard and then you can put things where you like using the configure command.

---

### Post by Campitor on 2006-12-04
Thanks kleeman:

  I will install the 1.4.3. version this afternoon.  I was a little scared about the lack of dependencies from that one.  So 1.4.3. doesn't depend on lyx-common? Does it have all that it needs in the same deb? I never heard of a checkinstall deb, so I really don't know what it is.

One more question...I saw in version 1.4.2 (and I'm asuming is also in 1.4.3) that you can export your file in version 1.3.x ...does this mean that they are not compatible?  I'm working on my thesis, and I wouldn't want to have issues with compatibility. If the new features in 1.4.x are worth it, I can spend a day or two figuring out if everything works on the new version. Any info would be great.  Thanks

I love LyX...work on it everyday!!!!

Camp

---

### Post by kleeman on 2006-12-04
The checkinstall deb is produced by someone compiling lyx from source. Instead of doing "sudo make install" they install it as a deb using "sudo checkinstall". This then produces a standalone deb file and installs it on the system. They have then put this deb up on the lyx wiki.

Checkinstall debs have NO dependencies at all, so are frowned on by packagers because  they are therefore hard to maintain using apt. This is usually not a problem as long as you remember if you upgrade using apt that you have checkinstall debs on your system. The checkinstall lyx deb will be just as good as a regular dapper lyx deb (I speak from experience here).

There are compatibility issues between lyx files from the 1.3 version and the 1.4 version. So if you read the 1.3 file in 1.4 all is fine however if you then save it on 1.4 you can't read the saved file on 1.3.

The 1.4.3 version is better feature wise than 1.3.7 but is perhaps a little slower when you scroll through the file. Perhaps to be totally safe with a thesis ;-) you should copy your 1.3.7 version lyx file to a new location and test it with 1.4.3. If things do not work out you can then uninstall 1.4.3 and reinstall 1.3.7 and use the old backup lyx file again.

Hope this helps. Let me know if you have any problems or questions.

---

### Post by harishg on 2006-12-30
I had the same problem on dapper and tried to use the deb versions i found through google.But it broke so many things and I had to revert back to old version.I updated to edgy to use Lyx 1.4.

---

