---
title: "usplash"
date: 2009-03-31
forum: General Help
---

### Post by laloruelas on 2009-03-31
I have a minor problem, usplash will only show up for about three seconds, then before the progress bar it switches to a text-based boot. My system still boots into gdm fine, but this is really annoying. how could i fix this

---

### Post by dcstar on 2009-03-31
> **laloruelas said:**
> I have a minor problem, usplash will only show up for about three seconds, then before the progress bar it switches to a text-based boot. My system still boots into gdm fine, but this is really annoying. how could i fix this

```
sudo update-initramfs -k all -u
```

---

### Post by laloruelas on 2009-04-01
that didn't work :(

---

### Post by coffeecat on 2009-04-01
Which version of Ubuntu are you using? It helps if you provide more information. There's an issue with Hardy (8.04) - but only Hardy - where you lose the usplash if you've reformatted the swap partition. Have you reformatted the swap partition?

If you are using Hardy, look at my posts #5 and #10 (for fstab) in this thread:

[http://ubuntuforums.org/showthread.php?t=857565](http://ubuntuforums.org/showthread.php?t=857565)

---

### Post by James_Lochhead on 2009-04-01
If you upgrade to Jaunty when it comes out (could even do it now - it is beta tho) you won't have this problem, Plymouth has replaced USplash.

---

### Post by maheshasolkar on 2009-04-01
> **laloruelas said:**
> I have a minor problem, usplash will only show up for about three seconds, then before the progress bar it switches to a text-based boot. My system still boots into gdm fine, but this is really annoying. how could i fix this

This looks similar to Launchpad bug #206878

  [https://bugs.launchpad.net/bugs/206878](https://bugs.launchpad.net/bugs/206878)

You should try the solution mentioned there:

[LIST=1]
[*] Make sure you have the initramfs-tools update
[*] ```
sudo blkid
```
[*] Check that swap line UUID from /etc/fstab matches swap UUID from step 2, if not change fstab.
[*] Check that the UUID in /etc/initramfs-tools/conf.d/resume matches the swap UUID from step 2, if not change resume file.
[*] ```
sudo update-initramfs -u
```
[*]Restart
[/LIST]

---

### Post by laloruelas on 2009-04-01
i'm using the jaunty beta, but this has not been working since ibex :(  i installed splashy in ibex and then uninstantiated it and got usplash again. now it only shows for a few seconds and it shows itself completely during shutdown. Don't think i have changed my swap partition recently

---

### Post by coffeecat on 2009-04-02
> **laloruelas said:**
> i'm using the jaunty beta

<snip>

Don't think i have changed my swap partition recently

As far as I am aware the problem with changing swap UUID and disappearing usplash is only a Hardy one.

---

### Post by emptybox on 2009-04-28
I upgraded from Intrepid to Jaunty today, and initially lost the uSplash screen (text only), but that was because I was using a custom one that obviously wasn't compatible with Jaunty.

I changed back to the default one in Startup-Manager, and the uSplash returned. :)

Also if you had installed the Smooth uSplash in Intrepid, then you'll have to uninstall that, as it doesn't work yet in Jaunty.

---

