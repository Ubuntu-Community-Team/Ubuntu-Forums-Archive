---
title: "Ubuntu is being a bitch"
date: 2009-04-28
forum: General Help
---

### Post by joshaman on 2009-04-28
Firefox and Ubuntu are running slow.  Lot of HDD thrashing, low-memory symptoms, and programs stop responding a lot.  Everything is sluggish.  I only use it for web browsing, torrents and videos.  It was not as slow when I first installed 8.10.  It cannot multi-task.  I can't decompress a file while using any other program simultaneously.  I'm using the repository version of 7zip, does someone know of a better utility to unRAR files?

But I guess my main problem is Firefox - it freezes, stops responding.

I have a 3.0 GHz dual-core Intel and 2 GB RAM.

What can I do?  I usually have Transmission and firefox open, along with the movie player.

---

### Post by 3Miro on 2009-04-28
I can unrar files by right clicking on them. Make sure you have installed Ark from Add/Remove.

I have not installed Jaunty yet, so I cannot really help, but from me it runs fine from the CD. Have you properly installed all the drivers and such (System -> Admin -> Hardware Manager).

---

### Post by joshaman on 2009-04-28
Thanks, I'm installing Ark now.  I've installed all hardware drivers available which is only one - for my nvidia 8800GT.

I think it's running faster after disabling a few unneccessary startup programs.  Also it could be that I have low disk space a lot - I'm gonna repartition my drive to give more space to Ubuntu.  I actually can't do a clean install because I have a bunch of stuff on the drive and I don't have the space to backup.

---

### Post by joshaman on 2009-04-28
I don't think Ark supports rar files.

---

### Post by 3Miro on 2009-04-28
I am using KDE which is somewhat different, but here is what I got.

When I go to add/remove programs (make sure you list all available programs), I search for RAR. I have listed:

RAR - which probably does what you need it to do

KArchiver - which is a KDE program that does archives, but you probably don't want that one on ubuntu.

X Archive Manager - which is the KArchiver for Gnome (the Ubuntu desktop environment). XAM should integrate with the rest of the system so you can extract rar files with right-click.

For the CPU control, I am not sure. Look around the forum or start a new tread.

---

### Post by marco123 on 2009-04-28
> sudo apt-get install unrar

You can then right click on .rar files and choose "Extract Here" the same as any other archives.

Cheers, Marco.

---

### Post by scottuss on 2009-04-28
Did you do an upgrade from 8.10 or did you do a clean install?

---

### Post by joshaman on 2009-04-28
> **marco123 said:**
> You can then right click on .rar files and choose "Extract Here" the same as any other archives.

Cheers, Marco.

Thanks buddy!

---

### Post by joshaman on 2009-04-28
> **scottuss said:**
> Did you do an upgrade from 8.10 or did you do a clean install?

I upgraded.  I'm now seeing that it might have a lot to do with Transmission 1.51.

---

### Post by scottuss on 2009-04-28
> **joshaman said:**
> I upgraded.  I'm now seeing that it might have a lot to do with Transmission 1.51.

Oh. I was going to say it's usually best to do a clean install. But if you think you've found the problem, that's good :)

---

### Post by Monsieur Gonzalez on 2009-04-28
YOu might want to try Deluge. In my opinion, it is lighter on resources and just works.

---

### Post by joshaman on 2009-04-28
Thanks I'll check out Deluge.

Turning off AHCI seems to speed things up.  AHCI may have been slowing down Ubuntu.  I have the ICH9 controller.

I wish it wouldn't freeze so often.  If anyone has any other suggestions I'll try them.

---

### Post by zeex on 2009-04-28
> **joshaman said:**
> 
But I guess my main problem is Firefox - it freezes, stops responding, is JUST SLOW and slow to load.


Hi, 

I had the same problem with Firefox but now anymore. Now I use Epiphany web browser. Really awesome in very sense, better fonts than firefox and it doesn't hogs CPU and it is highly customizable  Try it. I don't use firefox anymore in Linux.

It uses firefox engine (epiphany-gecko) or Apple safari engine (epiphany-webkit) use whatever you want.

---

### Post by Monsieur Gonzalez on 2009-04-28
I also have the ICH9 controller (Gigabyte GA-G33M-S2) and have AHCI active in BIOS. No problems with that. Do you get any errors (for instance, in dmesg log). Deactivating AHCI solves the problem?

---

### Post by Barmaleychik on 2009-04-28
My 9.04 also too slow and Firefox is a disaster. What is transmission and how can I get rid of it? 

Will it solve the problem?

---

### Post by Monsieur Gonzalez on 2009-04-28
Well, Transmission is a torrent client, it doesn't do anything unless you're using it, but I doubt you do, since you don't know what it is. Try to find out what's eating your resources, or if you're getting errors.

---

### Post by joshaman on 2009-04-28
> **Monsieur Gonzalez said:**
> I also have the ICH9 controller (Gigabyte GA-G33M-S2) and have AHCI active in BIOS. No problems with that. Do you get any errors (for instance, in dmesg log). Deactivating AHCI solves the problem?

Well it only speeds things up a little.  There's hardly a difference.  It's entirely a matter of system responsiveness.  For instance, when I close firefox, the window doesn't close for about 3 seconds.  I'm going to try a clean install tomorrow.

---

### Post by holodila on 2009-04-28
Jaunty was waaaay too slow at first, but now that Tracker stopped indexing everything seems OK. Just when I watch a video fullscreen and than a notification pops up I get black screen for 2-3 seconds, which is really annoying. I'm thinking about moving to gentoo ;)

---

### Post by Monsieur Gonzalez on 2009-04-28
Before doing a clean install, you might want to make sure it's not user related. Just try Firefox with a different user (create a test one if you're the only user). When upgrading, I've had to "purge" my desktop settings (though I'm on KDE and KDE has changed a lot between releases lately).

It would only take 5 minutes, so might be worth trying.

---

