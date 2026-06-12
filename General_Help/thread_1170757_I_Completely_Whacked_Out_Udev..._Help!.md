---
title: "I Completely Whacked Out Udev... Help!"
date: 2009-05-26
forum: General Help
---

### Post by s3MA00RRNY on 2009-05-26
Hello Everyone,

I managed to wreck my Jaunty system. The dev directory is completely messed up in my system and in my initramfs. Steps I took to get it this way...


[LIST=1]
[*]Installed udev script from the article found here: [http://www.debian-administration.org/article/Booting_Debian_in_14_seconds](http://www.debian-administration.org/article/Booting_Debian_in_14_seconds)
[*]Restarted
[*]Most everything stopped working, touchpad, mouse, GNOME Terminal.
[*]Switched to another terminal (Ctrl+Alt+Whatev) and replaced the evil udev with the old one.
[*]Rebooted
[*]Still had problems, so I reinstalled udev, which in turn messed up my initramfs.
[*]I could still chroot through initramfs, by mounting /dev/sda1, so I tried to delete the entire dev folder (STUPID), and manually started udev, which seemed to regenerate it.
[*]Tried to merge the dev folder off a Ubuntu Intrepid CD. It threw several "permissions can not be kept" errors.
[*]Rebooted and tried to recreate initramfs.
[*]Joy and rupture, now I can't do ANYTHING, because every dev in my initramfs is gone except for the ttys and a few others.
[/LIST]
Whenever I tried to recreate initramfs, it threw an error but continued anyway: "/tmp/mkinitramfs-*/lib/udev/rules.d" does not exist. That has to be a lie. And "/tmp/mkinitramfs-*/*/udev.conf". That could be true because I currently do not have a udev.conf (because I deleted it) in my /etc/udev. I have no clue how to get it back.

I've only been using Ubuntu for a few months, but I learned fast. So I'm a newb based on time, but not experience. Still, this one has me stumped.

Edit: Forgot to mention, my entire disk directory was missing from the start, which is why initramfs wouldn't work. (No UUIDs)

---

### Post by s3MA00RRNY on 2009-05-26
bump.

---

### Post by s3MA00RRNY on 2009-05-26
bump2.

---

### Post by s3MA00RRNY on 2009-05-26
I really need help! I'm starting to go into shock from using Windows Vista!

---

### Post by s3MA00RRNY on 2009-05-26
I guess no one is smart enough to figure it out. :(

---

### Post by s3MA00RRNY on 2009-05-27
I guess I'll just have to go back to Windows.

---

### Post by s3MA00RRNY on 2009-05-27
bump.

---

### Post by deadlockedgamer on 2009-05-27
One you used debian instructions two you need to be patient for responses and three for all I know the script you executed was intentionally malicious code since ubuntu does not get that boot time and quick boot times are a main focus of the project.

---

### Post by s3MA00RRNY on 2009-05-27
Sorry about all the bumps. I just didn't want my question to get lost amongst everything else. I was getting impatient. 

My home directory still exists (and is not corrupted), so even if it was malicious, it didn't kill that. I *could *reinstall the system, but I just did that to reorganize my partition layout. I don't want to have to do it all over again, even though it was pretty simple.

I need someone to explain how I repair my system without an initramfs. I can chroot with the Live CD (if I kill gdm) but nothing works properly.

---

### Post by albinootje on 2009-05-27
> **pcdude2143 said:**
> I managed to wreck my Jaunty system. 
I suggest to go for a separate /home partition, make backups, and reinstall.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by s3MA00RRNY on 2009-05-27
How would I go about making a markings list without access to Synaptic? I already have one, but it's old.

---

### Post by albinootje on 2009-05-27
> **pcdude2143 said:**
> How would I go about making a markings list without access to Synaptic? I already have one, but it's old.

```

$ dpkg --help|grep selections
  --get-selections [<pattern> ...] Get list of selections to stdout.
  --set-selections                 Set package selections from stdin.
  --clear-selections               Deselect every non-essential package.

```

---

### Post by s3MA00RRNY on 2009-05-27
Thanks, that's great. Off I go to reinstall.

---

### Post by deadlockedgamer on 2009-05-27
Tell us how it goes and glad you found help however for future reference I would recommend not saying anything that could sound like you like windows way better especially vista since ubuntu users are truly fanatical about there os and it being the best. Good luck and good day;)

---

### Post by s3MA00RRNY on 2009-06-07
I'm back. It went so smooth! The only hiccup I had was not related to Ubuntu. Sometimes my computer will freeze completely (no flashing CAPS LOCK). Also, when I exit a high graphics game, it's so slow I have to log out. That probably has something to do with my 80C GPU temp.

Yeah, you're right. I probably shouldn't have said those things about going back to Windows. I was just trying to scare other fanatics into answering my question. ("How dare you insult Linux!")

I am such a fanatic that I converted my grandmother and my Ubuntu stickers are coming in the mail soon. I peeled my Windows sticker off and shrunk its partition down to 25 GB. Recently it mysteriously BROKE ITSELF, so I probably never get around to fixing it. Ubuntu all the way!

---

