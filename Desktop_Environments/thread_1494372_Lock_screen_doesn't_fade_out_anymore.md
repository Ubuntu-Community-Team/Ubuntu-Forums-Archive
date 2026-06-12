---
title: "Lock screen doesn't fade out anymore?"
date: 2010-05-26
forum: Desktop Environments
---

### Post by MusicMan374 on 2010-05-26
I am currently using Ubuntu 10.04 Lucid Lynx 64-bit. I installed several updates today so it might be a bug related to that, but now when I click lock screen, it no longer fades to black like it used to, it instantly goes to black. Not a MAJOR issue but I did like the fade better. Any way to get it back, terminal command or anything? Thanks!

---

### Post by beruic on 2010-05-27
I have the same issue. Both with compiz on and off.
Also 64 bit.

---

### Post by MusicMan374 on 2010-05-27
I just confirmed on my netbook, since it hadn't been updated yet, that it was an update. I didn't read the details but there was a gnome-screensaver update that probably changed it, but I don't know if this is a mistake side effect or if it was one of the points of the update to disable the fadeout. Before the group of around 50 updates the lock screen faded, now it doesn't, exactly what happened to my desktop. Not sure whether or not I should submit a bug report?

Edit: Also this is not confined to 64-bit, as I have the UNE installed on my netbook. I really didn't like the UNE windowing system though so I login with gnome on it, because compiz can't run correctly on the UNE environment. But there is no 64-bit UNE so this is 32 bit, same issue. I suppose there was no point to installing the UNE if I'm still gonna use gnome but whatever I guess, don't want to reinstall.

---

### Post by imbjr on 2010-05-29
> **MusicMan374 said:**
> I just confirmed on my netbook, since it hadn't been updated yet, that it was an update. I didn't read the details but there was a gnome-screensaver update that probably changed it, but I don't know if this is a mistake side effect or if it was one of the points of the update to disable the fadeout. Before the group of around 50 updates the lock screen faded, now it doesn't, exactly what happened to my desktop. Not sure whether or not I should submit a bug report?

Edit: Also this is not confined to 64-bit, as I have the UNE installed on my netbook. I really didn't like the UNE windowing system though so I login with gnome on it, because compiz can't run correctly on the UNE environment. But there is no 64-bit UNE so this is 32 bit, same issue. I suppose there was no point to installing the UNE if I'm still gonna use gnome but whatever I guess, don't want to reinstall.

I can confirm that this this not just 64-bit and I do recall there being a screensaver update recently.

---

### Post by MusicMan374 on 2010-05-29
It seems it is just the gnome-screensaver as well. I installed xubuntu 64-bit on my netbook, and since it runs xfce and a different screen saver it still fades out. But In the xfce screensaver, I can configure the fadeout options. Is there any place to do this in gnome? Or did the update break the functionality? I did confirm it started happening right after the gnome-screensaver update that came out this week. I also do not know if this was intended. If it was unintended, and there is no place to configure the screensaver options, I can submit a bug report on launchpad, but otherwise I don't know how to fix it. I'm on vacation at the moment visiting family so I won't have a chance to screw around with gnome until late sunday night or monday afternoon. Maybe I am missing something.

---

### Post by SabreWolfy on 2010-06-08
Confirmed in Lucid 32-bit. Why the change? I thought the fade-out looked quite nice :)

---

### Post by MusicMan374 on 2010-06-08
Yeah, I know, I don't know what's goin on there, I'll post a bug report on launchpad and post the URL. I don't think it's right, probably unintended, the fade out was a nice effect.

---

### Post by MusicMan374 on 2010-06-08
[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/591500](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/591500)

You can go there to confirm the bug and comment.

---

### Post by Nandox7 on 2010-06-09
As the Fade on lock was disabled on the last update the workaround is to force the install of the older version. :)

sudo apt-get install --reinstall gnome-screensaver=2.30.0-0ubuntu1

---

### Post by Nandox7 on 2010-07-06
As I wanted my fade effect back I ended creating a patch for the screensaver deb.
It's attached on the bug mentioned before in case anyone is interested, as it won't make it on the package itself due to some ...... reasons. :D

---

