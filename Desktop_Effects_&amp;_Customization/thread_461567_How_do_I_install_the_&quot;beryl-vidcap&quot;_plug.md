---
title: "How do I install the &quot;beryl-vidcap&quot; plugin on Fesity?"
date: 2007-06-01
forum: Desktop Effects &amp; Customization
---

### Post by diablo75 on 2007-06-01
I'm looking for a deb file.  I'm not a developer.  Just someone who really really needs to make some screencasts at high quality of beryl in action, if at all possible.

I've been using xvidcap, which is good, but not as good as I wish.

---

### Post by ernz on 2007-06-04
Hi diablo75! I found your post looking for the same thing. Unfortunately I didn't find any nice and fluffy .deb installer, I would have preferred this myself also, but I did manage to get it to work in the end. This may be a bit of a backwards way of doing things, but as I said, it worked for me. At time of writing this all keys and sources were valid. Credit goes to author(s) of [http://doc.gwos.org/index.php/HowToInstallBeryl](http://doc.gwos.org/index.php/HowToInstallBeryl) as this is an adapted tutorial based on theirs.

I am assuming you have beryl up and running already (if not, go [_here_]("http://doc.gwos.org/index.php/HowToInstallBeryl"))

[SIZE="4"]**_How *I* installed the 'beryl-vidcap' plugin on Feisty_**[/SIZE]

**1. Add sources** 
Enter this into a terminal window:
```
 sudo gedit /etc/apt/sources.list
```

Add this line to the bottom of the file:
```
deb http://download.tuxfamily.org/myberyl/shame/debian-sid/beryl-svn/relatively-stable/ ./
```
Save and close the file.

**2. Add the Key (I do have my reasons for doing it this way)**
Fire up a new text editor window, something like gedit for example. Paste in all of the following code EXACTLY how it is shown:

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.6 (GNU/Linux)

mQGiBEWW9UARBACMtiONcrI2Qt3oWu7QgUzo9ES07rRvmrmpVo GgNvmkK6bxqDxY
kQ/xIGmY/9q81vBvmGDL1Dl04PDROKTKpeedHX0NeJTGDXjo0rcsbPiV4Me RIky/
2LAcQRo8t9zTfkhVHWDkkSxC4UV8ibbyM1d3g0m7FAnyQgPwtO OBsBKkXwCgn+kn
ckSEuO3VA8Tr+wTqpPTv+x0D/3LmK1Wclv4vlS9+ntyqHAiO5sFP1nPgxihLQ78B
pB/eQbei/6ldZIH8aCQhYlKUZZ/G71misx6fe9OfXQ52puORAn1wyQfRp34GTObI
4ffl2rR6Ux+Tuo7DqYsTNdaPAO73ck9FY/0VOD9RpkvVxph1wYlR7LfZI+QeoYgW
x1HXA/0SnHTUQlLDJpTp6HPp7pAKX5d3nL2R6w+wvowgnZW9GGew9rT8 bKhkQEa1
n0ixcbjbEED6eS6ip7AbhxcS4AzLoV/ZtRcaZG1r8z82itewPeatmphCcG3DFA7j
UqsmiuFBspY0DDWYXUH+KEEdz06PkqSt/+cCJBKvcJPpRt5Y87Qmc2hhbWUgKGJl
cnlsIHJlcG9zaXRvcnkpIDxzaGFtZUBzaWR1eD6IYAQTEQIAIA UCRZb1QAIbAwYL
CQgHAwIEFQIIAwQWAgMBAh4BAheAAAoJEHPmsPqkKmz1zcUAmw US0qLcC1FXMFXp
ICMulpzAtrs+AJ0fVSHox9RWhJ0QCR7xNxaIP1Ovh7kCDQRFlv VIEAgAqG6f+PXq
swQI8KgoEsyU9N6QmtD75dOJhCAb1bK3jbwRZHqS9eWAqbQB3/7HNVfH+SifzGb9
Lsd7KT8FS8uk8olKKvtpu/RUsiVXE7tJ8/u8VB3KIZYacan1xBa6PlQC2pXv4xJr
CQC2Z8el0Tu/g8l7o1G9dsavoHoVE55dxwIp+Mb2hxXqW/29qAn9zEuTXzwDCjYG
rPPaN3w8T7/GLIh70w0f5WCTz4ob1Aa3o/76S4fUrPP2M7vJgW5cSGS6FJHs6qR2
pBY5NSqgOnE7YP0SG7t1AWwRdr+q8oXktq0NFwGnU+Kl4UVX+x 3mWXtrPMkCzYXu
w54HtRVy9dj0AwADBQgAo0CU3hgttCmvCCMNz/pIjBTS3pqnWIhP15oFVEBTQRBQ
kvr7/sIGDN8Xkbl3zYXIOItW1p8Es0X3jJ1p/6zGP2hyvb39oULzUSAzlTvi4hxL
xoLs7CdytiWmhQ5DWMX4w9+uJIlQ2UaYkw2L9KyJjRdmo4fKrO UmbQ+FZ5bZYZ9C
Mfa3/s1NvhMYSXWoEXs7SO/n8VhI1UDRGqB9gGsV/uqYDV4dtjMCrWTDfZ2TrgIC
nS/t5NWUy2mE2GBDRBdztrYmt7Rx1QrmoEu078agRWF3nQu6jhB5Q qwQCJXiGCBj
4l75D/9XpehO1auyzR7fT0m8fMBjf01XT98ifkIeV4hJBBgRAgAJBQJF lvVIAhsM
AAoJEHPmsPqkKmz1lmAAn19AdGOiK+oqtOvy1UMmR+MZnGXeAJ 4tQ46Occ+Vl7n6
hr05MWkxwSg0Zw==
=PIoM
-----END PGP PUBLIC KEY BLOCK-----
```
Save the file somewhere you will remember it as 'myberyl.key' and close the file.

Now go to [System > Administration > Software Sources] and open the 'Authentication' tab. Import the 'myberyl.key' file and close that window.

**3. Update Repository Package Lists**
In a terminal window, enter the following:
```
sudo apt-get update
```
This will update the package listings, which include the 'beryl-plugins-vidcap' you are after ;)
After updating you may be prompted by the update manager. IGNORE this message. Installing the updates will upgrade you to the SVN version of beryl, which isn't as stable.

**4. Install the Plugins Package**
Again, in a terminal window enter:
```
sudo apt-get install beryl-plugins-shame
```
The vidcap plugin you require is now installed. 

**5. Cleaning up**
Enter this into a terminal window:
```
 sudo gedit /etc/apt/sources.list
```

Go to the line you entered which will look something like:
*deb [http://download.tuxfamily.org/myberyl/shame/debian-sid/beryl-svn/relatively-stable/](http://download.tuxfamily.org/myberyl/shame/debian-sid/beryl-svn/relatively-stable/) ./*

Stick a hash (#) at the start of the line to make it look like:
*#deb [http://download.tuxfamily.org/myberyl/shame/debian-sid/beryl-svn/relatively-stable/](http://download.tuxfamily.org/myberyl/shame/debian-sid/beryl-svn/relatively-stable/) ./*

Commenting this line out will stop the SVN version of beryl being installed, updating will stop the update manager from listing the SVN updates, but you will still retain the plugin functionality you require :)

Finally, in a terminal window, enter the following:
```
sudo apt-get update
```


[B]
Restart X (CTRL + ALT + BACKSPACE) and you're ALL DONE! - Hope this has helped. If you find any mistakes then I am sorry, I was doing this mostly from memory. If you have problems with what I have posted, please post them here and I will help as much as I can.[/B]

*One* last thing. If this works fine and you have the plugin working like I do now, go to 
[Beryl Settings Manager > Extras > Capture] and go to the 'Post-Processing' tab.
Replacing the command there with:
```
seom-filter /tmp/beryl-capture.seom | mencoder - -ovc xvid -xvidencopts bitrate=1200 -o /home/diablo/Desktop/BerylVideo.avi
```
...where 'diablo' is you username and 'mencoder' is already installed - will encode the capture to an **[SIZE="2"]Xvid![/SIZE]** video file...right to your desktop! Nice :D

---

### Post by sp0rk on 2007-06-04
I tried this, and it appears to have installed correctly, but now my Beryl isn't working at all.  The Window Decorator setting is grayed out.  Here's a screenshot:
[IMG]http://sp0rk-tech.net/Goddamnitt.png[/IMG]

If I select Beryl as the WM, it tries to load it and then just reverts back to Metacity.  Any ideas?

---

### Post by ernz on 2007-06-06
Hi sp0rk! I'm not a beryl expert or anything, I just listed what worked for me on two of my machines. Here's what I suggest though:

Check that you have installed:
[LIST]
[*]beryl (+dependancies)
[*]beryl-manager
[*]emerald (+ dependancies)
[*]emerald-themes
[/LIST]

If this doesn't work, re-enable the 
```

deb [http://download.tuxfamily.org/myberyl/shame/debian-sid/beryl-svn/relatively-stable/](http://download.tuxfamily.org/myberyl/shame/debian-sid/beryl-svn/relatively-stable/) ./

```
 repository, and allow the upgrades to be made after you sudo apt-get update. This SHOULD re-install a newer SVN version over the one you have installed, alongside the screenshot plugin. It's less stable, but it's more likely to work.

Tell us how you get on :)

---

